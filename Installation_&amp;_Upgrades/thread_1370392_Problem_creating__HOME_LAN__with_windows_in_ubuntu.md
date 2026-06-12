---
title: "Problem creating  HOME LAN  with windows in ubuntu 9.10"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by durga11 on 2010-01-02
Hi, I am trying to setup a home LAN with a windows system. I had created a LAN in windows system in DHCP,The windows system is showing as LAN connected.I had configured a SAMBA for DHCP. but i am unable to connect, i tried setting samba with static IP,still i am unable to set up LAN with windows

please chk the config settings of my system,


$ sudo vi /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#iface eth0 inet static
#address 169.254.54.11
#netmask 255.255.252.0
#gateway 192.168.1.1   // ?? what should be the gateway IP  to be used for static IP

----------------------------------------------------
$ sudo gedit /etc/samba/smb.conf
[global]
    ; General server settings
    netbios name = durga
   ; server string =
    workgroup = MSHOME    
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
   interfaces = lo, eth0 
   bind interfaces only = true
  
    passdb backend = tdbsam
    security = user
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
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = durga
   


Please let me know if I am wrong in configuring samba for connecting to Windows .

---

### Post by jplemoine on 2010-01-02
Hello, 
I think there is a problem with the IP adress...

Quote :
#iface eth0 inet static
#address 169.254.54.11
#netmask 255.255.252.0
#gateway 192.168.1.1   // ?? what should be the gateway IP  to be used for static IP
End of Quote

the adress begins with 169.254 with can not talk to Network.
It must begins with 192.168.

Check the configuration of DHCP : The DHCP server does not give a valid adress ; So, the device take a private IP adress.

Sorry for my bad english, hope that these informations will be usefull,

Jean-Philippe

---

### Post by durga11 on 2010-01-02
Thanks for the reply,
Can you guide me in setting up a HOME LAN with  windows machine.which one is best ... to give a static IP addres or by DHCP, I failed to setup in both. The configuration I  had done is given above.

---

