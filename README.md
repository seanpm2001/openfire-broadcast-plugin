# openfire-broadcast-plugin

<h2>Overview</h2>

<p>
The broadcast plugin broadcasts messages to all users in the system or to specific groups. It's
primarily useful for sending announcements or notifications.
</p>

<h2>Installation</h2>

<p>Copy broadcast.jar into the plugins directory of your Openfire installation. The
plugin will then be automatically deployed. To upgrade to a new version, copy the new
broadcast.jar file over the existing file.</p>

<h2>Configuration</h2>

The broadcast plugin is configured via Openfire system properties. These can
be configured under Server/Server Manager/System Properties:

<ul>
	<li><tt>plugin.broadcast.serviceName</tt> -- the name of the broadcast service. If no value
	is set, the default is "broadcast".</li>
	<li><tt>plugin.broadcast.disableGroupPermissions</tt> -- true to allow any user to
	broadcast a message to a group. When false, only group members or administrators can
	broadcast messages to a group. The default value is false.</li>
	<li><tt>plugin.broadcast.groupMembersAllowed</tt> -- true to also allow group members
	to send broadcast messages to groups they belong to. When false, only administrators can
	send broadcast messages to a group. The default value is true. Note that the property value
	of <tt>plugin.broadcast.disableGroupPermissions</tt> can effectively override this value
	by letting anyone send broadcast messages to groups.</li>
	<li><tt>plugin.broadcast.allowedUsers</tt> -- the comma-delimitted list of users allowed
	to broadcast messages to all connected users at once. When this property isn't set,
	anyone is allowed to broadcast messages to all users. Users should be specified by their
	bare JID (e.g. john@myserver.com)</li>
	<li><tt>plugin.broadcast.all2offline</tt> -- true to deliver broadcast messages sent
	to all@[serviceName].[serverName] to online and offline users. When false or not
	set only online users get the messages as described below.</li>
	<li><tt>plugin.broadcast.messagePrefix</tt> -- Add a prefix for all broadcast
	messages. Set this to "(broadcast)" to prepend "(broadcast)&nbsp;".
	</li>
</ul>

<h2>Using the Plugin</h2>

To send a broadcast message, send a message to all@[serviceName].[serverName] or
[group]@[serviceName].[serverName]. For example, if your server is called foo and the
default service name is being used, a message to all@broadcast.foo would be broadcast to
all users connected to the server. For the group staff, a message to staff@broadcast.foo would
be sent to all users in the group staff that are currently online or offline.

<p>
Note: for maximum compatability between group implementations, it's recommended that you use
lower-case group names in conjunction with the broadcast plugin.
</p>

