---
title: "Cannot get Win 7 machine to connect to Samba share"
date: 2014-11-06
forum: MINT
---

### Post by Mark_Fish on 2014-11-06
Hi all,

I'm not sure if I've put this thread in the correct section but any help that anyone can give me would be GREATLY appreciated...

I have recently built a Linux Mint machine and I am running it as a NAS/Entertainment centre, it has a RAID 6 array with 2 Partitions created (RaidData and Other) both of which are set up as shares in Samba. There are also 2 users set up on the machine ("generic" and "fish") both of which have had corresponding Samba users created for them and been added to the smbusers file (I will post its contents further below). The machine is running Samba 4.1.6. I'll post the contents of the smb.conf file at the bottom of this post.

I have been able to get the Win 7 machine to connect to the RaidData share with no issues as I have "force user = generic" in the share options. The other share however I have been having endless problems with, I need to set this share up so that only the "fish" user can access it. Originally I was having issues because of the ntlmv2 authentication that win 7 uses but I have added 
    ntlm auth = no
    lanman auth = no
    client ntlmv2 auth = yes
to the Global options and that has (as far as I can tell) solved part of the issue. When trying to connect to the "Other" share it prompts for the password as it should, however when the credentials are entered it gives the error: "Windows cannot access \\newfishnas\other$, You do not have permission to access \\newfishnas\other$. Contact your network administrator to request access.". This error ONLY occurs if I enter the correct password for the "fish" user, if I enter the password incorrectly or enter the "generic" user's credentials it gives the error either incorrect password or you don't have access (like it should) and prompts to re-enter your credentials.

On the actual partition I have set the permissions up so that anyone can access, create, delete, etc files/folders. It looks like the issue has something to do with the actual permissions on the partition as it seems to authenticate the password correctly but then is denied access. The part that really confuses me is if I change the "valid users" in the "Other" share to "generic", it works without issue. The only thing I can think of is that the Partition is mounted as generic which may have something to do with it.

Any help that anyone can give me to try and fix this issue would be great, I've spent about 2 weeks fiddling with settings trying to get this to work but nothing seems to help. It may be something really simple that I overlooked.

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

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = workgroup
    name resolve order = bcast host

# why can't samba work with windows properly? Because that would make it easy.
    ntlm auth = no
    lanman auth = no
    client ntlmv2 auth = yes

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Linux Mint)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
    dns proxy = no

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

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
    server role = standalone server

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;    passdb backend = tdbsam

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
;    map to guest = bad user

########## Domains ###########

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
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

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
;    usershare allow guests = yes
    security = user
    map to guest = bad user
;    encrypt passwords = yes
;    guest ok = yes
    guest account = generic

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
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
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

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
;    guest ok = no
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[Data]
    comment = All Data on the NAS
    path = /media/generic/RaidData
    read only = no
    writeable = yes
    browseable = yes
    guest ok = yes
    public = yes
    force user = generic
;    valid users = generic

[Other$]
    comment = Hidden Stuff
    path = /media/generic/RaidData/Other$
    read only = no
    writeable = yes
    browseable = no
    valid users = fish

Contents of smbusers:

generic = "generic"
fish = "fish"
```

---

### Post by Mark_Fish on 2014-11-06
Below are the results from "testparm -v"

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Data]"
Processing section "[Other$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    dos charset = CP850
    unix charset = UTF-8
    workgroup = WORKGROUP
    realm = 
    netbios name = NEWFISHNAS
    netbios aliases = 
    netbios scope = 
    server string = %h server (Samba, Linux Mint)
    interfaces = 
    bind interfaces only = No
    server role = standalone server
    security = USER
    auth methods = 
    encrypt passwords = Yes
    client schannel = Auto
    server schannel = Auto
    allow trusted domains = Yes
    map to guest = Bad User
    null passwords = No
    obey pam restrictions = Yes
    password server = *
    smb passwd file = /etc/samba/smbpasswd
    private dir = /var/lib/samba/private
    passdb backend = tdbsam
    algorithmic rid base = 1000
    root directory = 
    guest account = generic
    enable privileges = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd chat debug = No
    passwd chat timeout = 2
    check password script = 
    username map = 
    username level = 0
    unix password sync = Yes
    restrict anonymous = 0
    lanman auth = No
    ntlm auth = No
    client NTLMv2 auth = Yes
    client lanman auth = No
    client plaintext auth = No
    client use spnego principal = No
    preload modules = 
    dedicated keytab file = 
    kerberos method = default
    map untrusted to domain = No
    log level = 2
    syslog = 0
    syslog only = No
    log file = /var/log/samba/log.%m
    max log size = 1000
    debug timestamp = Yes
    debug prefix timestamp = No
    debug hires timestamp = Yes
    debug pid = No
    debug uid = No
    debug class = No
    enable core files = Yes
    smb ports = 445, 139
    large readwrite = Yes
    server max protocol = SMB3
    server min protocol = LANMAN1
    client max protocol = NT1
    client min protocol = CORE
    unicode = Yes
    min receivefile size = 0
    read raw = Yes
    write raw = Yes
    disable netbios = No
    reset on zero vc = No
    log writeable files on exit = No
    defer sharing violations = Yes
    nt pipe support = Yes
    nt status support = Yes
    max mux = 50
    max xmit = 16644
    name resolve order = bcast, host
    max ttl = 259200
    max wins ttl = 518400
    min wins ttl = 21600
    time server = No
    unix extensions = Yes
    use spnego = Yes
    client signing = default
    server signing = default
    client use spnego = Yes
    client ldap sasl wrapping = plain
    enable asu support = No
    svcctl list = 
    cldap port = 0
    dgram port = 0
    nbt port = 0
    krb5 port = 0
    kpasswd port = 0
    web port = 0
    rpc big endian = No
    deadtime = 0
    getwd cache = Yes
    keepalive = 300
    lpq cache time = 30
    max smbd processes = 0
    max disk size = 0
    max open files = 16384
    socket options = TCP_NODELAY
    use mmap = Yes
    use ntdb = No
    hostname lookups = No
    name cache timeout = 660
    ctdbd socket = 
    cluster addresses = 
    clustering = No
    ctdb timeout = 0
    ctdb locktime warn threshold = 0
    smb2 max read = 1048576
    smb2 max write = 1048576
    smb2 max trans = 1048576
    smb2 max credits = 8192
    load printers = Yes
    printcap cache time = 750
    printcap name = 
    cups server = 
    cups encrypt = No
    cups connection timeout = 30
    iprint server = 
    disable spoolss = No
    addport command = 
    enumports command = 
    addprinter command = 
    deleteprinter command = 
    show add printer wizard = Yes
    os2 driver map = 
    mangling method = hash2
    mangle prefix = 1
    max stat cache size = 256
    stat cache = Yes
    machine password timeout = 604800
    add user script = 
    rename user script = 
    delete user script = 
    add group script = 
    delete group script = 
    add user to group script = 
    delete user from group script = 
    set primary group script = 
    add machine script = 
    shutdown script = 
    abort shutdown script = 
    username map script = 
    username map cache time = 0
    logon script = 
    logon path = \\%N\%U\profile
    logon drive = 
    logon home = \\%N\%U
    domain logons = No
    init logon delayed hosts = 
    init logon delay = 100
    os level = 20
    lm announce = Auto
    lm interval = 60
    preferred master = No
    local master = Yes
    domain master = Auto
    browse list = Yes
    enhanced browsing = Yes
    dns proxy = No
    wins proxy = No
    wins server = 
    wins support = No
    wins hook = 
    lock spin time = 200
    oplock break wait time = 0
    ldap admin dn = 
    ldap delete dn = No
    ldap group suffix = 
    ldap idmap suffix = 
    ldap machine suffix = 
    ldap passwd sync = no
    ldap replication sleep = 1000
    ldap suffix = 
    ldap ssl = start tls
    ldap ssl ads = No
    ldap deref = auto
    ldap follow referral = Auto
    ldap timeout = 15
    ldap connection timeout = 2
    ldap page size = 1024
    ldap user suffix = 
    ldap debug level = 0
    ldap debug threshold = 10
    eventlog list = 
    add share command = 
    change share command = 
    delete share command = 
    preload = 
    lock directory = /var/run/samba
    state directory = /var/lib/samba
    cache directory = /var/cache/samba
    pid directory = /var/run/samba
    ntp signd socket directory = 
    utmp directory = 
    wtmp directory = 
    utmp = No
    default service = 
    message command = 
    get quota command = 
    set quota command = 
    remote announce = 
    remote browse sync = 
    nbt client socket address = 0.0.0.0
    nmbd bind explicit broadcast = Yes
    homedir map = auto.home
    afs username map = 
    afs token lifetime = 604800
    log nt token command = 
    NIS homedir = No
    registry shares = No
    usershare allow guests = No
    usershare max shares = 100
    usershare owner only = Yes
    usershare path = /var/lib/samba/usershares
    usershare prefix allow list = 
    usershare prefix deny list = 
    usershare template share = 
    async smb echo handler = No
    panic action = /usr/share/samba/panic-action %d
    perfcount module = 
    host msdfs = Yes
    passdb expand explicit = No
    idmap backend = tdb
    idmap cache time = 604800
    idmap negative cache time = 120
    idmap uid = 
    idmap gid = 
    template homedir = /home/%D/%U
    template shell = /bin/false
    winbind separator = \
    winbind cache time = 300
    winbind reconnect delay = 30
    winbind max clients = 200
    winbind enum users = No
    winbind enum groups = No
    winbind use default domain = No
    winbind trusted domains only = No
    winbind nested groups = Yes
    winbind expand groups = 1
    winbind nss info = template
    winbind refresh tickets = No
    winbind offline logon = No
    winbind normalize names = No
    winbind rpc only = No
    create krb5 conf = Yes
    ncalrpc dir = /var/run/samba/ncalrpc
    winbind max domain connections = 1
    winbindd socket directory = 
    winbindd privileged socket directory = 
    winbind sealed pipes = No
    allow dns updates = disabled
    dns forwarder = 
    dns update command = 
    nsupdate command = 
    rndc command = 
    multicast dns register = Yes
    samba kcc command = 
    server services = 
    dcerpc endpoint servers = 
    spn update command = 
    share backend = 
    tls enabled = No
    tls keyfile = 
    tls certfile = 
    tls cafile = 
    tls crlfile = 
    tls dh params file = 
    idmap config * : backend = tdb
    comment = 
    path = 
    username = 
    invalid users = 
    valid users = 
    admin users = 
    read list = 
    write list = 
    force user = 
    force group = 
    read only = Yes
    acl check permissions = Yes
    acl group control = No
    acl map full control = Yes
    acl allow execute always = No
    create mask = 0744
    force create mode = 00
    directory mask = 0755
    force directory mode = 00
    force unknown acl user = No
    inherit permissions = No
    inherit acls = No
    inherit owner = No
    guest only = No
    administrative share = No
    guest ok = No
    only user = No
    hosts allow = 
    hosts deny = 
    allocation roundup size = 1048576
    aio read size = 0
    aio write size = 0
    aio write behind = 
    ea support = No
    nt acl support = Yes
    profile acls = No
    map acl inherit = No
    afs share = No
    smb encrypt = default
    durable handles = Yes
    block size = 1024
    change notify = Yes
    directory name cache size = 100
    kernel change notify = Yes
    max connections = 0
    min print space = 0
    strict allocate = No
    strict sync = No
    sync always = No
    use sendfile = No
    write cache size = 0
    max reported print jobs = 0
    max print jobs = 1000
    printable = No
    print notify backchannel = Yes
    print ok = No
    printing = cups
    cups options = 
    print command = 
    lpq command = %p
    lprm command = 
    lppause command = 
    lpresume command = 
    queuepause command = 
    queueresume command = 
    printer name = 
    use client driver = No
    default devmode = Yes
    force printername = No
    printjob username = %U
    default case = lower
    case sensitive = Auto
    preserve case = Yes
    short preserve case = Yes
    mangling char = ~
    hide dot files = Yes
    hide special files = No
    hide unreadable = No
    hide unwriteable files = No
    delete veto files = No
    veto files = 
    hide files = 
    veto oplock files = 
    map archive = Yes
    map hidden = No
    map system = No
    map readonly = yes
    mangled names = Yes
    store dos attributes = No
    dmapi support = No
    browseable = Yes
    access based share enum = No
    blocking locks = Yes
    csc policy = manual
    fake oplocks = No
    kernel oplocks = No
    kernel share modes = Yes
    locking = Yes
    oplocks = Yes
    level2 oplocks = Yes
    oplock contention limit = 2
    posix locking = Yes
    strict locking = Auto
    dfree cache time = 0
    dfree command = 
    copy = 
    preexec = 
    preexec close = No
    postexec = 
    root preexec = 
    root preexec close = No
    root postexec = 
    available = Yes
    volume = 
    fstype = NTFS
    wide links = No
    follow symlinks = Yes
    dont descend = 
    magic script = 
    magic output = 
    delete readonly = No
    dos filemode = No
    dos filetimes = Yes
    dos filetime resolution = No
    fake directory create times = No
    vfs objects = 
    msdfs root = No
    msdfs proxy = 
    ntvfs handler = 

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Data]
    comment = All Data on the NAS
    path = /media/generic/RaidData
    force user = generic
    read only = No
    guest ok = Yes

[Other$]
    comment = Hidden Stuff
    path = /media/generic/RaidData/Other$
    valid users = fish
    read only = No
    browseable = No


```

---

### Post by slickymaster on 2014-11-06
Hey Mark_Fish, welcome to the forums. I'm moving you're thread to the **Networking & Wireless** sub-forum.

Also, I've edited your first post, adding code tags to it,because output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of 'Code' tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by Morbius1 on 2014-11-06
Run the following command and I think you will see the source of the problem:
```
getfacl -t /media/generic
```
The only user ( other than root ) that can access the folder or anything under it is "generic". This is by design.

The reason your [Data] share works is because the remote user is converted to "generic" and now can get through the road block to the folder under it.

You can do the same thing with the "Other" share. Even though it appears contradictory "valid users" and "force user" can coexist since "valid users" happens at authentication time and "force user" happens after the user is granted access.

---

### Post by Bucky Ball on 2014-11-06
*Thread moved to **MINT**.*

Sorry slickymaster, but moving this to the ***Mint*** forum. 

@OP: Your support request regards Win and Mint, neither of which are supported in the main areas of these forums. While you are more than welcome to post here, please be aware the Mint community is a vibrant one and they have an active forum. As the problem appears to be about not being able to connect from a Win box, perhaps a Win forum may also be of help.

The sub-categories in ***Ubuntu Official Flavours Support*** are for Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, and Mythbuntu.

Good luck. ;)

---

### Post by Mark_Fish on 2014-11-06
> **Morbius1 said:**
> Run the following command and I think you will see the source of the problem:
```
getfacl -t /media/generic
```
The only user ( other than root ) that can access the folder or anything under it is "generic". This is by design.

The reason your [Data] share works is because the remote user is converted to "generic" and now can get through the road block to the folder under it.

You can do the same thing with the "Other" share. Even though it appears contradictory "valid users" and "force user" can coexist since "valid users" happens at authentication time and "force user" happens after the user is granted access.

Hi Morbius,

So what you're saying is I should put the options "valid users = fish" and then "force user = generic" under it in the "other" share? As it will validate if the entered credentials have permission to access the share, then if they do have access, the share is accessed as if you logged in with the generic user's login?

also, thankyou SlickyMaster and Bucky Ball for correcting my post.

I will check if this solution fixes the issue now.

---

### Post by Morbius1 on 2014-11-06
> So what you're saying is I should put the options "valid users = fish"  and then "force user = generic" under it in the "other" share? As it  will validate if the entered credentials have permission to access the  share, then if they do have access, the share is accessed as if you  logged in with the generic user's login?
Correct.

OF course there is a flaw in your overall design. Everyone and your Aunt Tilly can access /media/generic/RaidData and everything under it like /media/generic/RaidData/Other$.

So if some user really wants to access the "Other" share and can't he can always access the shared folder through the "Data" share.

---

### Post by Mark_Fish on 2014-11-06
> **Morbius1 said:**
> Correct.

OF course there is a flaw in your overall design. Everyone and your Aunt Tilly can access /media/generic/RaidData and everything under it like /media/generic/RaidData/Other$.

So if some user really wants to access the "Other" share and can't he can always access the shared folder through the "Data" share.

Yeah, I was doing some testing at some point and changed the path for the "Other" share and forgot to change it back. The actual path for the share is /media/generic/Other.

I've put the changes in that you recommended and now I'm just getting an "access is denied" error every time and it just asks for credentials to be put in again. Not sure if I've done something dumb and not done it correctly.... hmmm

---

### Post by Morbius1 on 2014-11-06
Then "generic" doesn't have Linux access to the /media/generic/Other folder itself.

What are it's permissions:
```
ls -dl /media/generic/Other
```

---

### Post by Mark_Fish on 2014-11-06
I set the permissions so that everyone should be able to read/write to /media/generic/Other through the GUI, unless I need to do it through the terminal?

That command gave me the below output:
```

drwxrwxrwx 20 root root 4096 Oct 26 19:00 /media/generic/Other

```

Edit:
I just tried changing the smbusers file to
```

root = "fish"

```
and commented out the "force user = generic" in smb.conf

Still says I don't have access...

---

### Post by Morbius1 on 2014-11-06
Well that doesn't make any sense does it.

Um ... You did add "fish" to the samba password database right?

As in:
```
sudo smbpasswd -a fish
```

---

### Post by Mark_Fish on 2014-11-06
Yeah, I had already added fish as a samba user.

On a side note, I just tried changing the smbusers file to
 	```


root = "fish"

```


and commented out the "force user = generic" in smb.conf

Still says I don't have access...

---

### Post by Morbius1 on 2014-11-06
post the output of this command please:
```
sudo pdbedit -L | grep fish
```
And you don't want a link between any user and root so undo all of that.

---

### Post by Mark_Fish on 2014-11-06
Output:
```

fish:1002:fish

```

And undone.

---

### Post by Morbius1 on 2014-11-06
Is "fish" the login user name on the Windows box?

And did you make the samba password that "fish" uses the same as the Windows login user named "fish" or is it something different.

---

### Post by Mark_Fish on 2014-11-06
Fish is the username on the windows box, I didn't even think of that. Could that be what's causing the issue?

The samba password for fish is different to the windows one. I've been trying to log into the share with "workgroup\fish".

Would creating a different Samba user altogether and replacing fish with that solve the problem?

EDIT:
Just tried it, same thing...

---

### Post by Morbius1 on 2014-11-06
You can do that or you can make the samba password match the password that fish uses to log into Windows match - exactly.

If you create another user in Mint you would have to remove fish from the samba password database:
```
sudo smbpasswd -x fish
```

---

### Post by Mark_Fish on 2014-11-06
Ok, I've removed the "fish" samba user. I've changed the smb.conf and smbusers files accordingly. Still no luck...

---

### Post by Mark_Fish on 2014-11-06
By the way; when I change the smbusers file, do I have to run
```

sudo /etc/init.d/samba reload

```
or is that only after altering smb.conf?

---

### Post by Morbius1 on 2014-11-06
I don't know why you have an smbusers file but if you want to restart samba - or smbd in this case - it's:
```
sudo service smbd restart
```

---

### Post by Mark_Fish on 2014-11-06
I didn't realize that I didn't need one. Does everything still work as it should if it's blank?

---

### Post by Morbius1 on 2014-11-06
Since I don't have one at all the answer is yes.

---

### Post by Mark_Fish on 2014-11-06
If it helps at all; I can't connect to the share from another linux box either but can access the "Data" share with no issues.

---

### Post by Mark_Fish on 2014-11-06
If it helps at all; I can't access the [Other$] share from a linux box either but I can access the [Data] share with no problems.

I'm completely stumped... It looks like everything should be working now but nope...

There is a Samba user called nasadmin, that is the only "valid user" for the share and the actual permissions on the machine for the directory is set to everyone has read/write access and yet I still get the access is denied error...

---

### Post by Mark_Fish on 2014-11-06
If it helps at all; I can't access the [Other$] share from a linux box either but I can access the [Data] share with no problems.

I'm completely stumped... It looks like everything should be working now but nope...

There is a Samba user called nasadmin, that is the only "valid user" for the share and the actual permissions on the machine for the directory is set to everyone has read/write access and yet I still get the access is denied error...

---

### Post by Mark_Fish on 2014-11-06
If it helps at all; I can't access the [Other$] share from a linux box  either but I can access the [Data] share with no problems.

I'm completely stumped... It looks like everything should be working now but nope...

There is a Samba user called nasadmin, that is the only "valid user" for  the share and the actual permissions on the machine for the directory  is set to everyone has read/write access. Yet I still get the access  is denied error...

---

### Post by Mark_Fish on 2014-11-06
Great... the forum lagged and posted multiple copies...

Can I delete posts?

---

### Post by bab1 on 2014-11-06
> **Mark_Fish said:**
> Great... the forum lagged and posted multiple copies...

Can I delete posts?
No, but you can replace the content with oooops :oops:

[COLOR="#0000FF"]**Edit: **On a more serious note.  I think you are trying to recover from some mis-conceived  ideas from the start.  @Morbius1 and I go way back.  Generally we agree.  But our methods are different.  He is helping you so I won't step in front of him helping you.

I will however give you a different point of view.  I don't believe in hacking the configuration of Samba.  There are proper ways of doing this and there are alternative methods that cover up the ill conceived file system structure and ownership/permissions problem.

I don't think you should nest shares below shares and @Morbius1 has mentioned that.  You need to add Linux and Samba users to your Ubuntu server or you will always be fighting with the guest user using all manner of chmod and chown along with force this or force that.

If you want multiple users (be they mortal or system) you need to use common user groups and ACL's as a last resort.  After all of that is taken care of you can easily set up the Samba sharing.

I will answer to your earlier questions if you still want answers.[/COLOR]

---

### Post by Mark_Fish on 2014-11-06
Hi bab1,

Thanks for your reply. I don't actually have nested shares, I was just testing something temporarily and forgot to change it back. The shares are actually "/media/generic/RaidData" and "/media/generic/Other". As far as I'm aware I have set up the Samba and Linux users correctly.

Ideally I wanted to have the "Other$" share to be locked down on the actual machine aswell so that the Linux user "nasadmin" could only access it but from the looks of it that will overcomplicate things and I will take what I can get...

Any additional help that either you or Morbius could give me would be fantastic!

---

### Post by bab1 on 2014-11-07
> **Mark_Fish said:**
> Hi bab1,

Thanks for your reply. I don't actually have nested shares, I was just testing something temporarily and forgot to change it back. The shares are actually "/media/generic/RaidData" and "/media/generic/Other". As far as I'm aware I have set up the Samba and Linux users correctly.

Ideally I wanted to have the "Other$" share to be locked down on the actual machine aswell so that the Linux user "nasadmin" could only access it but from the looks of it that will overcomplicate things and I will take what I can get...

I don't see that as a complication.  If you want the user to have complete control then you have to configure that,  What is the user *nasadmin* used for?  is that a mortal user ( a human) or a system user (a process or app)?  has this user been added to the Samba users database (via sudo smbpasswd -a).  The smbusers file is not where Samba users reside.  Smbusers is a mapping of Samba user to Windows users with a different username such as```

# linux-user = SMB_name1 SMB_name2 ...

root = administrator admin

nobody = guest pcguest smbguest

bbaggins = Bilbo 

```...the smbpasswd file is encrypted.  It's a .tbd file and you view it with pdbedit.


What are the current ownership and permissions on the 2 directories?  Post the output of these 3 commands> ls -l /media/generic

ls -l /media/generic/RaidData

ls -l /media/generic/Other
... who are the users that will access the shares and for what reason (read only or read and write)?

---

### Post by Mark_Fish on 2014-11-07
I won't be able to reply for the next day and a bit so I'll post the results of what you've asked me to do when I get back. Thanks for the help so far!

---

### Post by Mark_Fish on 2014-11-08
nasadmin is a mortal user, I've set up the machine so that the user "generic" is automatically logged in at startup. I only have the "nasadmin" user created so that the "Other" directory is locked and cannot be accessed by anyone but nasadmin.

So the smbusers file is just for converting usernames for when connecting from windows? If my understanding is correct then that may be what is causing the issue. I'll try deleting the file's contents to see if that has any effect.

Both users (generic and nasadmin) have had Samba users created using "sudo smbpasswd -a".

See below for results of the commands that you asked to be run:
```

generic@NewFishNAS ~ $ ls -l /media/generic
total 8
drwxrwxrwx 20 root    root    4096 Oct 26 19:00 Other
drwxrwxrwx 10 generic generic 4096 Nov  6 23:16 RaidData
generic@NewFishNAS ~ $ ls -l /media/generic/RaidData
total 32
drwxr-xr-x 26 generic generic 4096 Oct 26 13:37 Anime
drwxr-xr-x  4 generic generic 4096 Oct 24 14:09 CloneZilla Backups
-rw-r--r--  1 generic generic 2610 Nov  6 19:56 Forum post
drwxr-xr-x 19 generic generic 4096 Oct 24 13:24 Games
drwxr-xr-x  8 generic generic 4096 Oct 22 18:26 General Data
drwxr-xr-x 74 generic generic 4096 Nov  7 13:44 Movies
drwxr-xr-x 31 generic generic 4096 Oct 26 20:52 Music
drwxr-xr-x 18 generic generic 4096 Oct 10 19:47 TV Series
ls -l /media/generic/Other
total 92
drwxrwxrwx  4 generic generic  4096 Oct 12 14:10 *
drwxrwxrwx  5 generic generic  4096 Oct 12 14:04 *
drwxrwxrwx  3 generic generic  4096 Oct 12 15:16 *
drwxrwxrwx  5 generic generic  4096 Oct 12 14:01 *
drwxrwxrwx  4 generic generic 12288 Oct 12 15:06 *
drwxrwxrwx  3 generic generic  4096 Oct 12 14:02 *
drwxrwxrwx  3 generic generic  4096 Oct 12 15:16 *
drwxrwxrwx  2 generic generic  4096 Oct 22 17:41 *
drwxrwxrwx  2 root    root    16384 Oct 10 00:41 lost+found
drwxrwxrwx 12 generic generic  4096 Oct 22 21:17 Misc
drwxrwxrwx  3 generic generic  4096 Oct 12 15:18 Network Trash Folder
drwxrwxrwx  5 generic generic  4096 Oct 12 14:01 *
drwxrwxrwx  4 generic generic  4096 Oct 12 14:06 *
drwxrwxrwx  3 generic generic  4096 Oct 12 15:16 *
drwxrwxrwx  3 generic generic  4096 Oct 12 15:06 *
drwxrwxrwx 52 generic generic  4096 Oct 26 19:00 *
drwxrwxrwx  3 generic generic  4096 Oct 12 15:16 *

```

(I'd rather not post the actual names of the folders in Other)

EDIT: Clearing the smbusers file did nothing, however now when I try and access the Data share (/media/generic/RaidData) it says "unknown username or password" and prompts for me to enter credentials. Entering workgroup\generic allows me access even though that share has "force user = generic" specified as an option. Weird...

---

### Post by bab1 on 2014-11-08
> **Mark_Fish said:**
> nasadmin is a mortal user.   I've set up the machine so that the user "generic" is automatically logged in at startup. 

Does the user *generic *have an Ubuntu password at all.
> 
I only have the "nasadmin" user created so that the "Other" directory is locked and cannot be accessed by anyone but nasadmin.

This doesn't seem quite right.  The directory is open to all users as shown in red ```
drwxrwx[COLOR="#FF0000"]rwx[/COLOR] 20 root    root    4096 Oct 26 19:00 Other

```
The red is the *others* group which is by definition "all other users on this host"  There is no Samba share authentication at this level based on your posted smb.conf file.  
> 
So the smbusers file is just for converting usernames for when connecting from windows? If my understanding is correct then that may be what is causing the issue. I'll try deleting the file's contents to see if that has any effect.

The smbusers file is used when you need to map a Windows user with a different username to a Linux user.  If the username is the same Linux Windows and Samba then you don't need the file mapping at all.  Just as @morbius has said.
> 
Both users (generic and nasadmin) have had Samba users created using "sudo smbpasswd -a".

Some how I'm missing what you are trying to do here.  The [Data] share with the directory: /media/generic/RaidData is setup as a guest share (any Samba user has access (no authentication))```

[Data]
    comment = All Data on the NAS
    path = /media/generic/RaidData
    read only = no
    writeable = yes
    browseable = yes
[COLOR="#FF0000"]    guest ok = yes[/COLOR]
    public = yes
    force user = generic
;    valid users = generic

```...The *guest ok =yes *means no prompt for access.  The directory that is shared has Linux authorization (permissions) for the user *generic* only.

All users are authenticated as the user nobody which is why you have to use the *force user = generic* parameter.  If you truly want only the user *generic * authenticated get rid of the*_ guest user = ok_* and the *_public = ok_* which is a synonym for guest ok anyway.  In their place uncomment the *valid users = generic*.  This makes the prompt come up and the only Samba user that is authorized is the user *generic*.  The Linux directory permissions authorize the Linux user *generic* to read and write to the directory.  This means the Samba user generic is only authenticated (who are you) and the Linux user generic is authorized (has permissions)>  This is why it's a good habit for the user names to be the same.  It just makes it simpler.  In any case a share that restricts what user should use it should not use the guest parameter. 
[QUOTE]

See below for results of the commands that you asked to be run:
```

generic@NewFishNAS ~ $ ls -l /media/generic
total 8
drwxrwxrwx 20 root    root    4096 Oct 26 19:00 Other
drwxrwxrwx 10 generic generic 4096 Nov  6 23:16 RaidData
generic@NewFishNAS ~ $ ls -l /media/generic/RaidData
total 32
drwxr-xr-x 26 generic generic 4096 Oct 26 13:37 Anime
drwxr-xr-x  4 generic generic 4096 Oct 24 14:09 CloneZilla Backups
-rw-r--r--  1 generic generic 2610 Nov  6 19:56 Forum post
drwxr-xr-x 19 generic generic 4096 Oct 24 13:24 Games
drwxr-xr-x  8 generic generic 4096 Oct 22 18:26 General Data
drwxr-xr-x 74 generic generic 4096 Nov  7 13:44 Movies
drwxr-xr-x 31 generic generic 4096 Oct 26 20:52 Music
drwxr-xr-x 18 generic generic 4096 Oct 10 19:47 TV Series
ls -l /media/generic/Other
total 92
drwxrwxrwx  4 generic generic  4096 Oct 12 14:10 *
drwxrwxrwx  5 generic generic  4096 Oct 12 14:04 *
drwxrwxrwx  3 generic generic  4096 Oct 12 15:16 *
drwxrwxrwx  5 generic generic  4096 Oct 12 14:01 *
drwxrwxrwx  4 generic generic 12288 Oct 12 15:06 *
drwxrwxrwx  3 generic generic  4096 Oct 12 14:02 *
drwxrwxrwx  3 generic generic  4096 Oct 12 15:16 *
drwxrwxrwx  2 generic generic  4096 Oct 22 17:41 *
drwxrwxrwx  2 root    root    16384 Oct 10 00:41 lost+found
drwxrwxrwx 12 generic generic  4096 Oct 22 21:17 Misc
drwxrwxrwx  3 generic generic  4096 Oct 12 15:18 Network Trash Folder
drwxrwxrwx  5 generic generic  4096 Oct 12 14:01 *
drwxrwxrwx  4 generic generic  4096 Oct 12 14:06 *
drwxrwxrwx  3 generic generic  4096 Oct 12 15:16 *
drwxrwxrwx  3 generic generic  4096 Oct 12 15:06 *
drwxrwxrwx 52 generic generic  4096 Oct 26 19:00 *
drwxrwxrwx  3 generic generic  4096 Oct 12 15:16 *

```

(I'd rather not post the actual names of the folders in Other)

The [Other] share doesn't look right either for much the same reasons.  See below in red```
[Other$]
    comment = Hidden Stuff
    path = /media/generic/RaidData/Other$
    read only = no
    writeable = yes
    browseable = no
[COLOR="#FF0000"]    valid users = fish[/COLOR]

```
In this case you have the user *fish *as the only authenticated user and some how that users authentication (user/pass) is not correct.  I see the user in the pdbedit listing so I wonder if the password is incorrect.  IMHO you should do a little house cleaning as all the user and groups are for the user generic on this share.  Why is that.  Have you thought of using a common group for this if you have two users using this share?

---

### Post by Mark_Fish on 2014-11-08
The linux user "generic" does not have a password as it's meant to just be a user that anyone can use. The directory is currently open to all users because I was going to try and fix this connection problem first and then try and lock down the "Other" share. I have exactly the same issue when the permissions aren't "full access" to Others.

The [Data] share is working as it should - from the windows machine the credentials aren't recognized so it defaults to guest. But then the user is forced to generic so that access permissions to files shouldn't be an issue. The [Data] share should be a guest share.

Sorry, I've been changing so many different things so often to try and fix the problem that some of the thing's I've posted are no longer correct. The fish user was another user that I created (it is now deleted and the smb.conf file has been changed accordingly, valid users is now nasadmin instead). I only want nasadmin to be able to access the share.

Did you want me to post the smb.conf as it is now?

---

### Post by Mark_Fish on 2014-11-08
OK... So after messing around with some stuff I have now got the share to work... I checked the permissions of the path all the way from the bottom. It turns out the /media/generic folder has "no access" to users other than root. I've changed the permissions on the /media/generic folder from
```

drwxr-x---+ 2 root root 4096 Nov  8 22:44 generic

```
to:
```

drwxr-xr-x+ 2 root root 4096 Nov  8 22:44 generic

```

I then commented out the "force user = generic" and now the share works. I'm not sure gives the access denied error only when the user is forced to generic... Anyway, it *looks* like the issue is fixed. I'm just going to test everything to make sure it's all working then mark this thread as solved.

Thank you both for all your help, you're both awesome :)

---

