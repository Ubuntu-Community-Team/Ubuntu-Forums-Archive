---
title: "Completely remove ProFTPd from server"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by trymbill on 2007-10-18
I have a problem.  I installed ProFTPd, and it worked fine.  Then I tried using Webmin with ProFTPd and it kinda ****** up my config of ProFTPd.

Now, I try to uninstall ProFTPd and it says that it's unistalled but when I try to install again the same .conf file is there and it doesn't ask me if I want a standalone or inetd version.

I've tried using dpkg -r and dpkg -p and then tried installing again and I got the "Standalone or inetd" window, but I still get this error when I try to start the server:

```
* Starting ftp server proftpd                                                                                                                                 - IPv4 getaddrinfo 'hruturinn' error: No address associated with hostname
 - warning: unable to determine IP address of 'hruturinn'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
```

And here is my proftpd.conf file:

```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                         on

ServerName                      "Debian"
ServerType                      standalone
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                     "-l"

DenyFilter                      \*.*/

# Use this to jail all users in their homes
# DefaultRoot                   ~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShells            off

# Port 21 is the standard FTP port.
Port                            21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress             1.2.3.4

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            proftpd
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd              off

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile                   off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the backend
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend                    mysql
#</IfModule>

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_tls.c>
TLSEngine off
</IfModule>

<IfModule mod_quota.c>
QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
Ratios on
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default.
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User                                ftp
#   Group                               nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias                   anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser on ftp
#   DirFakeGroup on ftp
#
#   RequireValidShell           off
#
#   # Limit the maximum number of anonymous logins
#   MaxClients                  10
#
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin                        welcome.msg
#   DisplayFirstChdir           .message
#
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
#
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask                           022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
#
# </Anonymous>

```

I'm not sure what I'm doing wrong here, but I've been trying to get this up and running again for 2 hours now and I just wanted to work like it used to :)

With hope of getting this fixed with your help,
Magnus

---

### Post by jzlharvey on 2007-10-24
Im in the same boat as well.

Just installed it and accidentally chose inetd rather then standalone.  Would love to start over :/

---

### Post by snozle on 2007-12-21
I too would like to be able to do this, has anyone found a way?

---

### Post by Swerve1000 on 2008-02-08
I have this problem also. Anyone know how to completly delete ProFTPd?

Thanks

---

### Post by acidzfire on 2008-03-22
I know this is an old post, but i figured I'd post a reply in case anyone else with this problem stumbles across it.

Here is what fixed it for me:

run

```
sudo apt-get autoremove proftpd
```

after that there is still a proftpd directory that needs to be removed.

```
sudo rm-rf /etc/proftpd/
```

also make sure the proftpd.conf file is not still in /etc
if it is, delete this too.


Hope this helps!

---

### Post by curVV on 2008-03-28
Hi thanks for reply, but how do i get it to prompt me again for inetd or standalone? i followed your instructions and when i install it again it just goes directly to 
Setting up proftpd (1.3.0-21ubuntu1) ...
ProFTPd is started from inetd/xinetd.

?? :)

---

### Post by varshovi on 2008-06-24
Hey fellas,

This is an issue with all debian based operating systems.
To solve the problem check to see if your proftpd.conf located in /etc/proftpd/ contains the following:

ServerType                      inetd

If so, change it to:

ServerType                      standalone

save the config and then try:

apt-get remove proftpd

if you install it you will again be asked to select inetd or standalone.

Regards.

---

