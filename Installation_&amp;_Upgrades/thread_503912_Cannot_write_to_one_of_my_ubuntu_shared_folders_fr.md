---
title: "Cannot write to one of my ubuntu shared folders from windows."
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by Groggx on 2007-07-18
I had this posted in the networking forum originally but was not getting any help there.  Thought I would try this forum as it is more of an install issue.

--------------------------------------------------------------------------------

I have created three shared folders on my ubuntu system and can see them and read access all of them Via my xp systems. I have my network setup as a workgroup environment and have set up the three folders so that I can access them them and write to them. Well two of the folders I can write to from windows but the third one called music will not allow me to write to it only read from it. The settings are the same as the other two so I am stumped. I am really new to linux and have not had the time to really dig into the learning of it. I am going away on an extended job and would like to set this up so the wife does not have to worry about windows that I had on this box before crapping out on her. I have the folders set for access with out using a log in as it is just easier to do it that way for the other users in my house and I do not use this machine for anything more that a storage box right now. 
Pasted below is a copy of my smb.conf. If there is something amiss please let me know how to fix this issue. Thanks

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = visions
# server string is the equivalent of the NT Description field
server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
; wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
; wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
; name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
; interfaces = lo eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself. However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
; bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
; syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = share" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
security = share

# You may wish to use password encryption. See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using. 
passdb backend = tdbsam

obey pam restrictions = yes

; guest account = nobody
invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
; unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
; pam password change = no

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
; domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
; logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
; logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
; logon drive = H:
; logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
; logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe. The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
; load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
; printing = bsd
; printcap name = /etc/printcap

# CUPS printing. See also the cupsaddsmb( manpage in the
# cupsys-client package.
; printing = cups
; printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
; printer admin = @lpadmin


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
; include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
# SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
; message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
; domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
; idmap uid = 10000-20000
; idmap gid = 10000-20000
; template shell = /bin/bash

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
comment = Home Directories
browseable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
; valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
writable = yes

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
; create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
; directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
; comment = Network Logon Service
; path = /home/samba/netlogon
; guest ok = yes
; writable = no
; share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
; comment = Users profiles
; path = /home/samba/profiles
; guest ok = no
; browseable = no
; create mask = 0600
; directory mask = 0700

wins support = no
[printers]
comment = All Printers
browseable = no
path = /tmp
printable = yes
public = no
writable = no
create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = yes
guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
; write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
; comment = Samba server's CD-ROM
; writable = no
; locking = no
; path = /cdrom
; public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
# cdrom share is accesed. For this to work /etc/fstab must contain
# an entry like this:
#
# /dev/scd0 /cdrom iso9660 defaults,noauto,ro,user 0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
# is mounted on /cdrom
#
; preexec = /bin/mount /cdrom
; postexec = /bin/umount /cdrom

[acerbackup]
path = /acerbackup
available = yes
browsable = yes
public = yes
writable = yes

[apps+drivers]
path = /apps+drivers
available = yes
browsable = yes
public = yes
writable = yes

[music]
path = /music
available = yes
browsable = yes
public = yes
writable = yes


Here is my fstab
File: /etc/fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=67407fa4-00ab-4df2-a97a-21c8ec2be5bd / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5
UUID=839bdcd6-5db2-4e64-9b4f-f5bdc2001ca9 none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0
/dev/hdc1 /apps+drivers ext3 rw 0 0
/dev/hdd1 /acerbackup ext3 rw 0 0
/dev/hdb1 /music ext3 rw 0 0

---

### Post by silverdulcet on 2007-07-20
Can you open up a terminal window (Applications->Accessories->Terminal)
Navigate to the root directory by typing:
> cd /

Then paste the output of this command when you reply:
```
ls -lad apps+drivers acerbackup music
```

That is assuming your three directories are mounted at / as it appears in your fstab. The output of the command should look something like this:

drwxr-xr-x 2 owner group 4096 2007-07-18 19:22  [COLOR="Blue"]apps+drivers[/COLOR]
drwxr-xr-x 2 owner group 4096 2007-04-29 00:34  [COLOR="Blue"]acerbackup[/COLOR]
drwxr-xr-x 2 owner group 4096 2007-06-28 18:33  [COLOR="Blue"]music[/COLOR]

---

### Post by Groggx on 2007-07-20
storage@storage:~$ cd /
storage@storage:/$ ls -lad apps+drivers acerbackup music
drwxr-xr-x 4 storage storage 4096 2007-07-19 22:43 acerbackup
drwxrwxrwx 5 storage storage 4096 2007-07-20 10:32 apps+drivers
drwxr-xr-x 4 storage storage 4096 2007-07-19 22:43 music
storage@storage:/$ 


Silverducet.
This is what it comes back with.  Thanks for the response.

---

### Post by silverdulcet on 2007-07-20
> storage@storage:~$ cd /
storage@storage:/$ ls -lad apps+drivers acerbackup music
drwxr-xr-x 4 storage storage 4096 2007-07-19 22:43 acerbackup
drwxrwxrwx 5 storage storage 4096 2007-07-20 10:32 apps+drivers
drwxr-xr-x 4 storage storage 4096 2007-07-19 22:43 music
storage@storage:/$ 

Ok, as you've probably noticed the acerbackup and music directories have the same permissions and apps+drivers is different. I have read that sometimes Windows has trouble with a Linux Samba server set to security=share which might explain why you have no problems with reading and writing to acerbackup. Yet you do have problems writing to music even though it has the same permissions set.

First I would try changing the permissions for the music directory to match that of apps+drivers. You would do so by navigating to the root directory as before:
```
cd /
```

Then use this command:
```
sudo chmod 777 music
```
The password should be the same one you use to edit system settings and add shares on your gui desktop.

Now when you type:
```
ls -lad music
```

It should return something like that:
```
drwxrwxrwx 5 storage storage 4096 2007-07-20 10:32 music
```

Finally you need to restart the Samba server to make sure it realizes you've made permission changes to the directory:
```
sudo /etc/init.d/samba restart
```

The password should be the same one you use to edit system settings and add shares on your gui desktop. After you issue the command you should see some output saying that Samba is shutting down and then starting again. Let me know if this works. If it does, you might want to go through the same steps of changing the permissions of acerbackup so that you do not run into any permission troubles in the future.

If you'd like to learn more about what all these directory and file permissions are about this link would be a good start.

[http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)

You can also search the Ubuntu forums for information regarding file permissions and how-to's relating to it. What you have to watch out for is that the linux file system permissions supercede any permissions you set in Samba. Samba is unable to override those. So you always have to make sure that you make the file system permissions you want coincide with the ones you set in Samba.

---

### Post by Groggx on 2007-07-20
Silverdulcet, You Rock...  It is now working.  My wife will not kill me now for having no access to her files for the past 2 weeks.  Thank you greatly.  I will read up on file permissions and will hopefully learn some more stuff.  Kinda use windows at work.  Corporate thing so hard to try any learn 2 complete OS at the same time...LOL  But still fun to try.
Have a good day and many thanks.  This forum rules.

---

