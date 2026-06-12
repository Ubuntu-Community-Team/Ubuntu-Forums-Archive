---
title: "Share printer over samba"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by dmsn on 2008-03-02
Hello I got little problem with my printer shareing over samba. It works with lp blabla.txt to print
but not over samba share. I dont find it when i search from my win xp machine.
I got printer HP Laserjet 1018. Do you know my problem with smb.conf ?

Thanks for help.


root@server:/etc/samba# lpstat -v
device for HP_LaserJet_1018_USB_KP35NSS_HPLIP: hp:/usb/HP_LaserJet_1018?serial=KP35NSS
root@server:/etc/samba#

Here is my smb.conf:

[global]
   security = share
   log file =/var/log/samba.log
   max log size = 1000
   socket options = TCP_NODELAY SO_SNDBUF=32768 SO_RCVBUF=32768
   interfaces = eth1
   printcap name = cups
   printing      = cups


[printers]
  comment      = All printers
  path         = /var/spool/samba
  browseable   = yes
  guest ok     = yes
  writable     = yes
  printable    = yes
  public       = yes
  printer name = HP1018

---

