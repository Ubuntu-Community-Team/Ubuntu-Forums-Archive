---
title: "samba problems upgrading from feisty to gutsy"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by foresttb on 2007-10-21
hello to the forum.

Upgrading from feisty to gutsy, the only serious problems i had , were with samba server.
I have an ubuntu desktop and an xp laptop.
My ubuntu desktop owns itself a workgroup.

   a)
    Browsing the windows network i cannot see my ubuntu workgroup, 
    Only way to enter to the shared files
    of my ubuntu desktop, is by pressing \\ and its internal ip.
   
   b)
    I cannot print from other computers
    of the windows network (using xp) 
    (using photosmart printer c4280)

here is my smb.conf :
```
[global]
    ; General server settings
    netbios name = forest
    
    workgroup = UBUNTU
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[forest]
path = /home/forest
available = yes
browsable = yes
public = yes
writable = yes

[big boy]
path = /media/big boy
available = yes
browsable = yes
public = yes
writable = yes
```

---

### Post by krymson on 2007-10-22
I also got mysterious samba problems after upgrading from feisty(7.04) to Gibbong(7.10)
My network drives are now inaccessible. I can't access the folders im suppsed to be sharing. 

The share are setup in smb.conf like so:

> 
[global]
	workgroup = MSHOME
	server string = %h server (Samba, Ubuntu)
	dns proxy = no
	security = share
	encrypt passwords = true
	passdb backend = tdbsam
	obey pam restrictions = yes
	invalid users = root
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIXpassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssucccessfully* .

[FatMan]
path = /mnt/FatMan
available = yes
browsable = yes
public = yes
writable = yes


[Chubby]
path = /mnt/FatMan
available = yes
browsable = yes
public = yes
writable = yes


---

### Post by pjhsv on 2007-10-24
I'm getting the same samba woes that seem to have plagued a few people since upgrading to Gutsy.  On Feisty, everything worked 100%, but as soon as I upgraded, I can't connect to my samba shares.  I can see them if I browse workgroup computers, but as soon as I try to connect, it tells me I don't have access.  If I have security=share, it just denies access straight away (I've always had it set as share previously).  If I set it to security=user, it asks for a username/password, but it doesn't matter what I type, it just brings the username/password screen back up.

Interestingly though, I setup a share for my home directory, restarted samba, and it worked straight away.  Perhaps the problem is related to not being able to create a share for a directory outside your home dir? (although, with a symlink to my normal share, I can still connect to it from my home dir)


[public]
comment = Public Folder
path = /home/public/
guest ok = yes
read only = no
create mask = 0777
directory mask = 0777
force user = paul
force group = paul
guest account = paul
case sensitive = no
strict locking = no
msdfs proxy = no

[paul]
comment = Pauls Home Dir
path = /home/paul/
guest ok = yes
read only = no
create mask = 0777
directory mask = 0777
force user = paul
force group = paul
guest account = paul
case sensitive = no
strict locking = no
msdfs proxy = no


\\newton\paul\ works fine
\\newton\public\ doesn't.

Both directories are owned by user "paul" (including all subdirs), and the permissions all seem fine.  I'm completely out of ideas...

paul@newton:/home/public$ smbclient //newton/paul -U paul
Password: 
Domain=[NEWTON] OS=[Unix] Server=[Samba 3.0.26a]
smb: \> exit
paul@newton:/home/public$ smbclient //newton/public -U paul
Password: 
Domain=[NEWTON] OS=[Unix] Server=[Samba 3.0.26a]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

paul@newton:/home/public$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[public]"
Global parameter guest account found in service section!
Processing section "[paul]"
Global parameter guest account found in service section!
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

---

### Post by krymson on 2007-10-28
a few restarts later, i'm back in business. i dunno what the magic number was or why, but things are working now.

---

### Post by pjhsv on 2007-10-28
Your smb.conf is still the same?  And you can connect to both FatMan and Chubby shares ??

..it's still not working for me.

---

### Post by leona on 2007-10-29
After upgrading from Fiesty to Gusty I can no longer print to my network printer (from Gusty to printer connected to a windows 2000 box).
This used to work perfect in Fiesty.
I also can't browse my network.
The mounts I've setup in fstab to connect to network shares on the w2k box however work perfectly.
Bizare!
Any clues?

---

### Post by michaelzap on 2007-10-29
I've also had problems connecting to shared Samba drives on my LAN after installing Gutsy (fresh install but trying the same fstab and samba configs that worked fine on Feisty). I finally was able to mount them using cifs (and an automatic unmount script that I found here in the forums to keep shutdown from hanging for a minute or more), but it's still not 100%. One of these shares doesn't automount on boot, but then does when I type sudo mount -a in the terminal.

I've pretty much decided that there is a problem with Samba in Gutsy and that I'll muddle through like this until a fix arrives via updates.

---

### Post by leona on 2007-10-29
I got it to find my printer but chaning my server name to its ip address, that seemed to work, something is definatly broken, has anyone rasied a bug ticket?

Hum, well that allowed me to 'see' my printer but not print, I then went around pushing buttons (like you do) and found that in the 'Policy' tab of the printer there is a State option, ticked this and it fired into life, how odd.

Can't access file shares with the ip method though, but got the printer printing so that's good :)

---

### Post by homerj742 on 2007-11-04
I'm having similar samba share issues, if anyone has found a fix PLEASE post!

---

### Post by scarboni on 2007-11-06
I am also unable to access my Windows network since upgrading to 7.10. I double-click the "Windows Network" & it knows, in the title bar, the workgroup name, but the screen is blank. Rebooting the same box into Vista & all shares easily accessible. smbclient -N returns nothing.

---

### Post by undfined on 2007-11-06
I renamed the printer's share name, on the Windows Server that hosts our printer, to a simpler name with no spaces (ie, EpsonRX620), installed the CUPS updates that were released this morning, and rebooted.  I used the Server's IP address instead of the hostname too.

This got Samba working for me.

I haven't had any trouble browsing the network though.

---

### Post by tednyc on 2007-11-07
I had the same problem.I was able to resolve it by using the ip address of the Windows box instead of the workstation name. Not sure why this was necessary, but at least I can access the shares on my Windows server (2003). That is, until I swap it to Ubuntu.:)

Still need to test the printer this way.

---

### Post by scarboni on 2007-11-08
Update:  I have booted the machine using the 7.10 64-bit live cd & can see the Windows shares just fine.  Something broke in the upgrade.  Can anyone tell me if there's a way to rebuild, reset, or reconfigure the smb client?  Also, does the /etc/samba/smb.conf file affect the client or is this only relevant when running the server?

I have overwritten the upgraded  /etc/samba/smb.conf file with the one from the livecd & tested nautilus again with no change.  Also smbtree -N still reports nothing.  However I have not rebooted yet so maybe that is needed.  Anyone got any ideas?

---

### Post by drcbrath on 2007-11-09
> **scarboni said:**
> Update:  I have booted the machine using the 7.10 64-bit live cd & can see the Windows shares just fine.  Something broke in the upgrade.  Can anyone tell me if there's a way to rebuild, reset, or reconfigure the smb client?  Also, does the /etc/samba/smb.conf file affect the client or is this only relevant when running the server?

I have overwritten the upgraded  /etc/samba/smb.conf file with the one from the livecd & tested nautilus again with no change.  Also smbtree -N still reports nothing.  However I have not rebooted yet so maybe that is needed.  Anyone got any ideas?


I have had similar trouble accessing my upgraded Gutsy Gibbon from other machines in my home network. I think I have it fixed. I used smbpasswd to set the samba password for my account on the server machine. Then I was able to access my share at '\\SERVERNAME\USERNAME' just like before. BTW, I have another machine still running Feisty, it had the same problem and fix. I do not remember having to set the samba password before Feisty. Perhaps the default setup changed for more security? But I do not have my earlier config files to check.

---

### Post by satx on 2007-11-09
Ran into some problems myself, but installed SMB4K. You can download directly from Applications->Add/Remove->All Available Applications->Smb4k.

Smb4K
A Samba (SMB) share advanced browser for KDE  
Smb4K is a SMB (Windows) share browser for KDE. It uses the Samba software suite to access the SMB shares of the local network neighborhood. Its purpose is to provide a program that's easy to use and has as many features as possible.
Home page: [http://smb4k.berlios.de/](http://smb4k.berlios.de/)

This application is provided by the Ubuntu community.
Smb4K integrates well into the Kubuntu desktop

Works great on Gutsy Gibbon 7.10! Try it, it simplifies and is a great interface. My Samba Config file is:
[global]
    ; General server settings
    netbios name = UBUNTU-VII
    server string = UBUNTU-VII
    workgroup = DOGNET
    interfaces = lo, eth0
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    
    encrypt passwords = true
    smb passwd file = /etc/smbpasswd
    dns proxy = no
    preserve case = yes
    short preserve case = yes
    default case = lower
    
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast
    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.


[UBUNTU]
    path = /home/michael
    browseable = yes
    available = yes
    writable = yes    
    guest ok = no
    public = yes
    create mask = 0664
    directory mask = 0775
    ;force user = michael
    ;force group = michael

---

### Post by satx on 2007-11-09
Also, I notice most of the smb.conf files shown don't have the:

interfaces = lo, eth0

Entry.

On another note, SAMBA does not play well with DHCP. I use a static IP address, and disable Roaming.

 I have a dual boot WIN XP/Ubuntu, 7.10 HP d4650y PC, 4 GB RAM, GeForce 7300, and have an HP Deskjet 952c printer. I am also running WIN XP SP2 under VMWARE in my Ubuntu 7.10.

I am able to share all devices (another HP d4650y on the net w/WIN XP SP2). I can acess the WIN XP partition on by dual boot box, as well as the WIN XP VMWARE device with no issues. No problem w/video, USB, printers, etc. 

I did have to reinstall VMWARE and my virtual XP device, fight with the graphics card, and beat SAMBA with a baseball bat until it worked again. Fortunately, I had several backup smb.conf files. The SMB4K program mentioned above is really neat, and works well. I tried GSAMBAD, but did not like it. 

As to Firefox, I installed the flash player, but still had problems with videos on FoxNews, etc., but installed GreaseMonkey to deal with that. 

SATX

---

### Post by crt667-1 on 2007-11-16
I too am having problems with my samba server after upgrading.

Strange thing is new shares work fine using \\samba\sharename.

I have renamed my existing shares (backups -> backup) and that works, renaming the share back to backups fails again.

The only way I can access my home directory however is with \\ipaddress\sharename

Soooo samba must be saving some information somewhere that is incompatible between the versions and that is obviously not in smb.conf.  Ideas anyone?

-- well actually after renaming my shares and rebooting my win client I can now access my home directory as \\samba\sharename

---

