---
title: "VMware network I can no find anything"
date: 2005-05-19
forum: Installation &amp; Upgrades
---

### Post by mkg on 2005-05-19
Hallo good people, free people,

I just installed vmware on my Kubuntu with the network options, but Windows 98 can not find any of the computers in (windows) network. Option is NUT. Do you have any idea why? 
Windows network is with Win2000 on NTFS partitions and maybe that is the problem, but in this case shared printers have to be present. 

Any suggestions?

 :???:

---

### Post by sfw5000 on 2005-05-19
Have you set up Samba on the linux machine?

---

### Post by mkg on 2005-05-19
[QUOTE=sfw5000]Have you set up Samba on the linux machine?[/QUOTE]

I have main OS Kubuntu 5.04. In VMware I have Windows 98. On Kubuntu 5.04 Samba is set. So, through samba I can find win98, but from Win98 I can not se any computers in windows network, where Kubuntu is attached. 

p.s. From Kubuntu I can find computers in Windows network and I can even print on network printer too.

---

### Post by sfw5000 on 2005-05-19
post the /etc/smb.conf file... i've only done this with XP Pro, so I'm not sure about win98, but usually you have to add samba users on the linux machine and then login to the windows machine using the usernames and passwords you set on the linux machine... also I've found that sometimes win98 (in general not just with sama networking) just doesn't "see" the other computers automatically and you might have to manually add the network locations. Is the win98 computer in the same workgroup as set in the smb.conf file?

---

### Post by mkg on 2005-05-19
[QUOTE=sfw5000]post the /etc/smb.conf file... i've only done this with XP Pro, so I'm not sure about win98, but usually you have to add samba users on the linux machine and then login to the windows machine using the usernames and passwords you set on the linux machine... also I've found that sometimes win98 (in general not just with sama networking) just doesn't "see" the other computers automatically and you might have to manually add the network locations. Is the win98 computer in the same workgroup as set in the smb.conf file?[/QUOTE]

I'm not sure I'll check right now

---

### Post by mkg on 2005-05-19
[QUOTE=mkg]I'm not sure I'll check right now[/QUOTE]


Here it is

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
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

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
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

---

### Post by patrick295767 on 2006-06-27
[QUOTE=mkg]Hallo good people, free people,

I just installed vmware on my Kubuntu with the network options, but Windows 98 can not find any of the computers in (windows) network. Option is NUT. Do you have any idea why? 
Windows network is with Win2000 on NTFS partitions and maybe that is the problem, but in this case shared printers have to be present. 

Any suggestions?

 :???:[/QUOTE]
  
Is it possible to do network with Windows 98SE ??
(I saw that some limitations existed with win 98 se for share folders) 

.?

how ot add network locations ?? 
> post the /etc/smb.conf file... i've only done this with XP Pro, so I'm not sure about win98, but usually you have to add samba users on the linux machine and then login to the windows machine using the usernames and passwords you set on the linux machine... also I've found that sometimes win98 (in general not just with sama networking) just doesn't "see" the other computers automatically and you might have to manually add the network locations. Is the win98 computer in the same workgroup as set in the smb.conf file?

---

