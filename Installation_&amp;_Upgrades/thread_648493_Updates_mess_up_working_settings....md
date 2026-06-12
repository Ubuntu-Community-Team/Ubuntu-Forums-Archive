---
title: "Updates mess up working settings..."
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by *B* on 2007-12-23
As so many others, I have tried to get away from MS, and have tried several different distros before I decided on Ubuntu. My problem is, every time I do any sort of update, it messes up certain things and they dot work. I learned to save a copy of the working config files, but I still cant make things work. Then, all of the sudden, they start working again.... till I update again. I have Ubuntu 7.10, 2.6.22-14 running dual boot with XP Pro on a MSI MS635 (1029) notebook with a Turion 2.2Ghz/2GB Ram/ATI X700 PCIe. Everything loaded fine, and what didnt, I found easy answers for here on the forum. The two things causing me problems after updates are my MS Bluetooth mouse, and Samba that I have setup to see my XP File Server and other XP Boxes.

My mouse works fine, till I update, then, it wont load at startup. I can run the search every time I boot up and force it to find it manually. This is hard on the batteries though. Then, all of the sudden, it will start finding it on its own again and load it at startup. Here is the hcid.conf file:

#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security auto;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	pin_helper /usr/bin/pinwrapper;

	# D-Bus PIN helper
	#dbus_pin_helper;
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;

	# Authentication and Encryption (Security Mode 3)
	#auth enable;
	#encrypt enable;
}

device 00:12:5A:61:2C:42 { name "MS Bluetooth 8000"; 
}


The other problem I have is Samba stops seeing my other XP systems, even thought I havent changed the smb.conf file at all. I found this tutorial here [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+tutorial](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+tutorial)
which helped me get samba setup and working.All my computers have static IP's. The XP boxes have "WINS" enabled, and the IP addresses of my wireless and wired network adapter added and allowed.  After updating, when I click on "Places" and choose "network", it will see the "windows network". It then either wont show the network name (ACMENET)l, or sometimes it will show "ACMENET" and the computers on the network like it sees them ok, but when I click on a computer, it tells me that computer is "unavailable". It even tells me that when I click on my laptop in the list of computers (which is the computer Im on) which I dont understand, it doesnt connect to the computer Im using. Here is my smb.conf:

[global]
    ; General server settings
    netbios name = MSI-Laptop
    server string =
    workgroup = ACMENET
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

[MyFiles]
    path = /media/hda6
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = acme
    force group = acme

Any help at all would be appreciated. Thanks in advance :-)

---

