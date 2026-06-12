---
title: "New UBUNTU 11.10 server configuration"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by phani247 on 2012-03-01
Hi everyone
[I]Iam working as a server administrator and in my company we are using windows servers,
now we planned to move to UBUNTU 11.10. so i started to build a new server..


DOMAIN Controller : UBUNTU 11.10
Clients : Windows and Ubuntu desktops

after that i installed

DNS
DHCP
SAMBA
NFS
&
NIS


now i am able to join windows machines as a clients to ubuntu domain controller but unfortunately iam unable to join ubuntu desktops as a clients in my domain..

I think i did mistake in the nis client configuration so plz help me in my new server setup

and we want to maintain all user data in centralized location with roaming profiles and home folders give me some info on this

plz help me...
[/I]

---

### Post by dino99 on 2012-03-01
[https://help.ubuntu.com/11.10/serverguide/C/index.html](https://help.ubuntu.com/11.10/serverguide/C/index.html)

---

### Post by phani247 on 2012-03-01
> **dino99 said:**
> [https://help.ubuntu.com/11.10/serverguide/C/index.html](https://help.ubuntu.com/11.10/serverguide/C/index.html)
already i go through that Server guide but iam unable to add the client machine..
can i add ubuntu desktop as a client without LDAP..?
if yes wat r the requirements to add as a client..

---

### Post by MAFoElffen on 2012-03-02
> **phani247 said:**
> already i go through that Server guide but iam unable to add the client machine..
can i add ubuntu desktop as a client without LDAP..?
if yes wat r the requirements to add as a client..
What is your point-to-point that you want really want to end up with?
 - Client access to a Samba share?
 -  Client access to NFS?

Are you trying to do Samba with Active Directory Integration? If so then this might help:
[****ActiveDirectoryWinbindHowto - Community *Ubuntu* Documentation]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cts=1330665930847&ved=0CEMQFjAB&url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FActiveDirectoryWinbindHowto&ei=rFhQT-vaIsXKiAKo6sW0Bg&usg=AFQjCNEJzocSQylJshdcHrP7_U4ypq5ddQ&cad=rja")
[****HOWTO: *Active Directory* Authentication - *Ubuntu* Forums]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=4&cts=1330666100290&ved=0CFYQFjAD&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D91510&ei=rFhQT-vaIsXKiAKo6sW0Bg&usg=AFQjCNFr_y1MDye_GzFj6Hac_Xdx7w51nQ")
Where you can see, those methods use Keberos... OR:
[Samba as a Domain Controller]("https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html")

With Samba, have you configured for users and/or groups yet?

The reason I asked the last question, is that with my experience, Win clients seem to work right out of the Box, while Ubuntu clients needed Samba on the Host to be have 3-4 lines configured first. If so, I'll share one of my server's smb.conf files...

Is that the problem you are having? Or is it with NIS?
[SettingUpNISHowTo - Community *Ubuntu* Documentation]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cts=1330665432697&ved=0CDMQFjAA&url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FSettingUpNISHowTo&ei=0FdQT_exAoOuiQKIo9C1Bg&usg=AFQjCNEsE8mZyRuMRZNlANZyzGtoVoH2ig&cad=rja")

That enough info to research?

---

### Post by phani247 on 2012-03-02
> **MAFoElffen said:**
> What is your point-to-point that you want really want to end up with?
 - Client access to a Samba share?
 -  Client access to NFS?

Are you trying to do Samba with Active Directory Integration? If so then this might help:
[****ActiveDirectoryWinbindHowto - Community *Ubuntu* Documentation]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cts=1330665930847&ved=0CEMQFjAB&url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FActiveDirectoryWinbindHowto&ei=rFhQT-vaIsXKiAKo6sW0Bg&usg=AFQjCNEJzocSQylJshdcHrP7_U4ypq5ddQ&cad=rja")
[****HOWTO: *Active Directory* Authentication - *Ubuntu* Forums]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=4&cts=1330666100290&ved=0CFYQFjAD&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D91510&ei=rFhQT-vaIsXKiAKo6sW0Bg&usg=AFQjCNFr_y1MDye_GzFj6Hac_Xdx7w51nQ")
Where you can see, those methods use Keberos... OR:
[Samba as a Domain Controller]("https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html")

With Samba, have you configured for users and/or groups yet?

The reason I asked the last question, is that with my experience, Win clients seem to work right out of the Box, while Ubuntu clients needed Samba on the Host to be have 3-4 lines configured first. If so, I'll share one of my server's smb.conf files...

Is that the problem you are having? Or is it with NIS?
[SettingUpNISHowTo - Community *Ubuntu* Documentation]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cts=1330665432697&ved=0CDMQFjAA&url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FSettingUpNISHowTo&ei=0FdQT_exAoOuiQKIo9C1Bg&usg=AFQjCNEsE8mZyRuMRZNlANZyzGtoVoH2ig&cad=rja")

That enough info to research?
in my network i have windows as well as ubuntu clients
iam using samba for sharing the resources b/w windows and ubuntu machines as well as domain controller..
nis is using for centralised user authentication...
still iam not created any users 
iam newbie to ubuntu..

---

### Post by phani247 on 2012-03-02
> **phani247 said:**
> in my network i have windows as well as ubuntu clients
iam using samba for sharing the resources b/w windows and ubuntu machines as well as domain controller..
nis is using for centralised user authentication...
still iam not created any users 
iam newbie to ubuntu..


any one help me on this issue plz...

---

### Post by MAFoElffen on 2012-03-03
> **phani247 said:**
> any one help me on this issue plz...
So with the Ubuntu machines, are you getting a user authentication error or an error that says something like "could not read file list, smb:xxxxx?
```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[Share01]
    comment = Samba Server on Server maferr-serv-01
    path = /home
    browsable = yes
    guess ok = yes
    readonly = no
    create mask = 0755

[Share01.5]
    comment = Samba Server on Server maferr-serv-01
    path = /Share01.5
    browsable = yes
    readonly = no
    create mask = 0755

```And this one configure with Samba as a Domain Controller
```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
# 
# \\ Samba as a Domain Controller \\
#  Although it cannot act as an Active Directory Primary Domain 
#  Controller (PDC), a Samba server can be configured to appear as a 
#  Windows NT4-style domain controller.
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
 add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home directory as \\server\username
[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mask = 0700
   directory mask = 0700
   valid users = %S

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   guest ok = yes
   read only = yes
   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[Share01]
    comment = Samba Server on Server maferr-serv-01
    path = /home
    browsable = yes
    guess ok = yes
    readonly = no
    create mask = 0755

[Share01.5]
    comment = Samba Server on Server maferr-serv-01
    path = /Share01.5
    browsable = yes
    readonly = no
    create mask = 0755

```Here's Samba instruction for setting up Active Directory with Kerberos...
[http://wiki.samba.org/index.php/Samba_%26_Active_Directory](http://wiki.samba.org/index.php/Samba_%26_Active_Directory)

There lots of Ubuntu tutorials and directions for Samba/Kerberos.  Not sure about NIS. I don't use NIS. It's been around awhile (understatement) and is crossplatform  (Windows, UNIX and Linux). For example, this quote from Microsoft Tech NET, MS Windows Server 2000:
> Although this article is billed as a primer to Kerberos  authentication, it is a high technical review. Kerberos is an integral  part of Windows 2000 Active Directory implementations, and anyone  planning to deploy and maintain a Windows 2000 enterprise must have a  working knowledge of the principals and administrative issues involved  in this front-line security technology.


 Since many other operating system vendors are also adopting this  MIT-developed authentication protocol, Kerberos Version 5 will  increasingly become a centerpiece of enterprise-level interoperability.  Kerberos provides secure user authentication with an industry standard  that permits interoperability. The Active Directory domain controller  maintains user account and log-in information to support the Kerberos  service.
 

The process of authenticating the identity of users during log-in is  the first step in gaining system access. For local machines that aren't  actively participating in a domain, Windows NT LAN Manager protocol is  still utilized to verify a user's name and password before granting  system access. However, in domain environments, Microsoft has coupled  Active Directory closely with Kerberos. Once access is granted, tickets  that permit specific access to other system resources within the domain  are exchanged.


---

### Post by phani247 on 2012-03-03
thanxs

---

