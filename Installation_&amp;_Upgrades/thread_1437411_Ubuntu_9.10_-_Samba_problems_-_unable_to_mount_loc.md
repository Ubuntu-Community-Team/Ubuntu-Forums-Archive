---
title: "Ubuntu 9.10 - Samba problems - unable to mount location"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by peterv6 on 2010-03-23
I'm running Ubuntu 9.10, and am getting the following error when I attempt to access the HADEN workgroup on my Windows network via Samba:

Unable to mount location - Failed to retrieve share list from server.

I ran the following command: 
```
peterv@MBP17U:~$ findsmb
sh: /usr/bin/nmblookup: not found

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
```

My smb.conf file is listed below, just in case that'd help with debugging:
```

peterv@MBP17U:/etc/samba$ cat -n smb.conf
     1	#
     2	# Sample configuration file for the Samba suite for Debian GNU/Linux.
     3	#
     4	#
     5	# This is the main Samba configuration file. You should read the
     6	# smb.conf(5) manual page in order to understand the options listed
     7	# here. Samba has a huge number of configurable options most of which 
     8	# are not shown in this example
     9	#
    10	# Some options that are often worth tuning have been included as
    11	# commented-out examples in this file.
    12	#  - When such options are commented with ";", the proposed setting
    13	#    differs from the default Samba behaviour
    14	#  - When commented with "#", the proposed setting is the default
    15	#    behaviour of Samba but the option is considered important
    16	#    enough to be mentioned here
    17	#
    18	# NOTE: Whenever you modify this file you should run the command
    19	# "testparm" to check that you have not made any basic syntactic 
    20	# errors. 
    21	# A well-established practice is to name the original file
    22	# "smb.conf.master" and create the "real" config file with
    23	# testparm -s smb.conf.master >smb.conf
    24	# This minimizes the size of the really used smb.conf file
    25	# which, according to the Samba Team, impacts performance
    26	# However, use this with caution if your smb.conf file contains nested
    27	# "include" statements. See Debian bug #483187 for a case
    28	# where using a master file is not a good idea.
    29	#
    30	
    31	#======================= Global Settings =======================
    32	
    33	[global]
    34	
    35	## Browsing/Identification ###
    36	
    37	# Change this to the workgroup/NT-domain name your Samba server will part of
    38	   workgroup = HADEN
    39	
    40	# server string is the equivalent of the NT Description field
    41	   server string = %h server (Samba, Ubuntu)
    42	
    43	# Windows Internet Name Serving Support Section:
    44	# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
    45	#   wins support = no
    46	
    47	# WINS Server - Tells the NMBD components of Samba to be a WINS Client
    48	# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
    49	;   wins server = w.x.y.z
    50	
    51	# This will prevent nmbd to search for NetBIOS names through DNS.
    52	   dns proxy = no
    53	
    54	# What naming service and in what order should we use to resolve host names
    55	# to IP addresses
    56	;   name resolve order = lmhosts host wins bcast
    57	
    58	#### Networking ####
    59	
    60	# The specific set of interfaces / networks to bind to
    61	# This can be either the interface name or an IP address/netmask;
    62	# interface names are normally preferred
    63	;   interfaces = 127.0.0.0/8 eth0
    64	
    65	# Only bind to the named interfaces and/or networks; you must use the
    66	# 'interfaces' option above to use this.
    67	# It is recommended that you enable this feature if your Samba machine is
    68	# not protected by a firewall or is a firewall itself.  However, this
    69	# option cannot handle dynamic or non-broadcast interfaces correctly.
    70	;   bind interfaces only = yes
    71	
    72	
    73	
    74	#### Debugging/Accounting ####
    75	
    76	# This tells Samba to use a separate log file for each machine
    77	# that connects
    78	   log file = /var/log/samba/log.%m
    79	
    80	# Cap the size of the individual log files (in KiB).
    81	   max log size = 1000
    82	
    83	# If you want Samba to only log through syslog then set the following
    84	# parameter to 'yes'.
    85	#   syslog only = no
    86	
    87	# We want Samba to log a minimum amount of information to syslog. Everything
    88	# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
    89	# through syslog you should set the following parameter to something higher.
    90	   syslog = 0
    91	
    92	# Do something sensible when Samba crashes: mail the admin a backtrace
    93	   panic action = /usr/share/samba/panic-action %d
    94	
    95	
    96	####### Authentication #######
    97	
    98	# "security = user" is always a good idea. This will require a Unix account
    99	# in this server for every user accessing the server. See
   100	# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
   101	# in the samba-doc package for details.
   102	#   security = user
   103	
   104	# You may wish to use password encryption.  See the section on
   105	# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   106	   encrypt passwords = true
   107	
   108	# If you are using encrypted passwords, Samba will need to know what
   109	# password database type you are using.  
   110	   passdb backend = tdbsam
   111	
   112	   obey pam restrictions = yes
   113	
   114	# This boolean parameter controls whether Samba attempts to sync the Unix
   115	# password with the SMB password when the encrypted SMB password in the
   116	# passdb is changed.
   117	   unix password sync = yes
   118	
   119	# For Unix password sync to work on a Debian GNU/Linux system, the following
   120	# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
   121	# sending the correct chat script for the passwd program in Debian Sarge).
   122	   passwd program = /usr/bin/passwd %u
   123	   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   124	
   125	# This boolean controls whether PAM will be used for password changes
   126	# when requested by an SMB client instead of the program listed in
   127	# 'passwd program'. The default is 'no'.
   128	   pam password change = yes
   129	
   130	# This option controls how unsuccessful authentication attempts are mapped 
   131	# to anonymous connections
   132	   map to guest = bad user
   133	
   134	########## Domains ###########
   135	
   136	# Is this machine able to authenticate users. Both PDC and BDC
   137	# must have this setting enabled. If you are the BDC you must
   138	# change the 'domain master' setting to no
   139	#
   140	;   domain logons = yes
   141	#
   142	# The following setting only takes effect if 'domain logons' is set
   143	# It specifies the location of the user's profile directory
   144	# from the client point of view)
   145	# The following required a [profiles] share to be setup on the
   146	# samba server (see below)
   147	;   logon path = \\%N\profiles\%U
   148	# Another common choice is storing the profile in the user's home directory
   149	# (this is Samba's default)
   150	#   logon path = \\%N\%U\profile
   151	
   152	# The following setting only takes effect if 'domain logons' is set
   153	# It specifies the location of a user's home directory (from the client
   154	# point of view)
   155	;   logon drive = H:
   156	#   logon home = \\%N\%U
   157	
   158	# The following setting only takes effect if 'domain logons' is set
   159	# It specifies the script to run during logon. The script must be stored
   160	# in the [netlogon] share
   161	# NOTE: Must be store in 'DOS' file format convention
   162	;   logon script = logon.cmd
   163	
   164	# This allows Unix users to be created on the domain controller via the SAMR
   165	# RPC pipe.  The example command creates a user account with a disabled Unix
   166	# password; please adapt to your needs
   167	; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
   168	
   169	# This allows machine accounts to be created on the domain controller via the 
   170	# SAMR RPC pipe.  
   171	# The following assumes a "machines" group exists on the system
   172	; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
   173	
   174	# This allows Unix groups to be created on the domain controller via the SAMR
   175	# RPC pipe.  
   176	; add group script = /usr/sbin/addgroup --force-badname %g
   177	
   178	########## Printing ##########
   179	
   180	# If you want to automatically load your printer list rather
   181	# than setting them up individually then you'll need this
   182	#   load printers = yes
   183	
   184	# lpr(ng) printing. You may wish to override the location of the
   185	# printcap file
   186	;   printing = bsd
   187	;   printcap name = /etc/printcap
   188	
   189	# CUPS printing.  See also the cupsaddsmb(8) manpage in the
   190	# cupsys-client package.
   191	;   printing = cups
   192	;   printcap name = cups
   193	
   194	############ Misc ############
   195	
   196	# Using the following line enables you to customise your configuration
   197	# on a per machine basis. The %m gets replaced with the netbios name
   198	# of the machine that is connecting
   199	;   include = /home/samba/etc/smb.conf.%m
   200	
   201	# Most people will find that this option gives better performance.
   202	# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
   203	# for details
   204	# You may want to add the following on a Linux system:
   205	#         SO_RCVBUF=8192 SO_SNDBUF=8192
   206	#   socket options = TCP_NODELAY
   207	
   208	# The following parameter is useful only if you have the linpopup package
   209	# installed. The samba maintainer and the linpopup maintainer are
   210	# working to ease installation and configuration of linpopup and samba.
   211	;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
   212	
   213	# Domain Master specifies Samba to be the Domain Master Browser. If this
   214	# machine will be configured as a BDC (a secondary logon server), you
   215	# must set this to 'no'; otherwise, the default behavior is recommended.
   216	#   domain master = auto
   217	
   218	# Some defaults for winbind (make sure you're not using the ranges
   219	# for something else.)
   220	;   idmap uid = 10000-20000
   221	;   idmap gid = 10000-20000
   222	;   template shell = /bin/bash
   223	
   224	# The following was the default behaviour in sarge,
   225	# but samba upstream reverted the default because it might induce
   226	# performance issues in large organizations.
   227	# See Debian bug #368251 for some of the consequences of *not*
   228	# having this setting and smb.conf(5) for details.
   229	;   winbind enum groups = yes
   230	;   winbind enum users = yes
   231	
   232	# Setup usershare options to enable non-root users to share folders
   233	# with the net usershare command.
   234	
   235	# Maximum number of usershare. 0 (default) means that usershare is disabled.
   236	;   usershare max shares = 100
   237	
   238	# Allow users who've been granted usershare privileges to create
   239	# public shares, not just authenticated ones
   240	   usershare allow guests = yes
   241	
   242	#======================= Share Definitions =======================
   243	
   244	# Un-comment the following (and tweak the other settings below to suit)
   245	# to enable the default home directory shares.  This will share each
   246	# user's home directory as \\server\username
   247	;[homes]
   248	;   comment = Home Directories
   249	;   browseable = no
   250	
   251	# By default, the home directories are exported read-only. Change the
   252	# next parameter to 'no' if you want to be able to write to them.
   253	;   read only = yes
   254	
   255	# File creation mask is set to 0700 for security reasons. If you want to
   256	# create files with group=rw permissions, set next parameter to 0775.
   257	;   create mask = 0700
   258	
   259	# Directory creation mask is set to 0700 for security reasons. If you want to
   260	# create dirs. with group=rw permissions, set next parameter to 0775.
   261	;   directory mask = 0700
   262	
   263	# By default, \\server\username shares can be connected to by anyone
   264	# with access to the samba server.  Un-comment the following parameter
   265	# to make sure that only "username" can connect to \\server\username
   266	# This might need tweaking when using external authentication schemes
   267	;   valid users = %S
   268	
   269	# Un-comment the following and create the netlogon directory for Domain Logons
   270	# (you need to configure Samba to act as a domain controller too.)
   271	;[netlogon]
   272	;   comment = Network Logon Service
   273	;   path = /home/samba/netlogon
   274	;   guest ok = yes
   275	;   read only = yes
   276	;   share modes = no
   277	
   278	# Un-comment the following and create the profiles directory to store
   279	# users profiles (see the "logon path" option above)
   280	# (you need to configure Samba to act as a domain controller too.)
   281	# The path below should be writable by all users so that their
   282	# profile directory may be created the first time they log on
   283	;[profiles]
   284	;   comment = Users profiles
   285	;   path = /home/samba/profiles
   286	;   guest ok = no
   287	;   browseable = no
   288	;   create mask = 0600
   289	;   directory mask = 0700
   290	
   291	[printers]
   292	   comment = All Printers
   293	   browseable = no
   294	   path = /var/spool/samba
   295	   printable = yes
   296	   guest ok = no
   297	   read only = yes
   298	   create mask = 0700
   299	
   300	# Windows clients look for this share name as a source of downloadable
   301	# printer drivers
   302	[print$]
   303	   comment = Printer Drivers
   304	   path = /var/lib/samba/printers
   305	   browseable = yes
   306	   read only = yes
   307	   guest ok = no
   308	# Uncomment to allow remote administration of Windows print drivers.
   309	# You may need to replace 'lpadmin' with the name of the group your
   310	# admin users are members of.
   311	# Please note that you also need to set appropriate Unix permissions
   312	# to the drivers directory for these users to have write rights in it
   313	;   write list = root, @lpadmin
   314	
   315	# A sample share for sharing your CD-ROM with others.
   316	;[cdrom]
   317	;   comment = Samba server's CD-ROM
   318	;   read only = yes
   319	;   locking = no
   320	;   path = /cdrom
   321	;   guest ok = yes
   322	
   323	# The next two parameters show how to auto-mount a CD-ROM when the
   324	#	cdrom share is accesed. For this to work /etc/fstab must contain
   325	#	an entry like this:
   326	#
   327	#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
   328	#
   329	# The CD-ROM gets unmounted automatically after the connection to the
   330	#
   331	# If you don't want to use auto-mounting/unmounting make sure the CD
   332	#	is mounted on /cdrom
   333	#
   334	;   preexec = /bin/mount /cdrom
   335	;   postexec = /bin/umount /cdrom
   [COLOR="Red"][B]336	[test]
   337	path = /home/peterv/test
   338	available = yes
   339	valid users = peterv
   340	read only = no
   341	browsable = yes
   342	public = yes
   343	writable = yes[/B][/COLOR]


```

The segment hilighted in red at the bottom is what I can see in the Windows network neighborhood.

I've installed Samba version 3.4.0

On my Windows XP machine, I can see the Ubuntu directory and can access files on it.  I just can't access the Windows workgroup from Ubuntu.  Can anyone please help?

---

### Post by blues_edwin on 2010-03-24
[COLOR=Black][windows access ubuntu or linux access ubuntu]

[global]
security = user

[/COLOR][COLOR=Black][test] for easy
path = /home/peterv/test
[/COLOR][COLOR=Black]browsable = yes
[/COLOR] [COLOR=Black]valid users = peterv
writable = yes
[/COLOR][COLOR=Black]
[command line]
# smbpasswd -a [/COLOR][COLOR=Black]peterv[/COLOR][COLOR=Black] (setting peterv password)
# service smb restart (restart samba service)

======================================

[Ubuntu access windows]

1.create a new account on the windows xp to share folder
2.setting password
[/COLOR][COLOR=Black]
Try it! 

mount -t cifs  //ip address/share name -o username=your name,password=your password  /home/xxx/your wnat to mount tmp
[/COLOR][COLOR=Red][COLOR=Black]



[/COLOR] 











 
[/COLOR]

---

