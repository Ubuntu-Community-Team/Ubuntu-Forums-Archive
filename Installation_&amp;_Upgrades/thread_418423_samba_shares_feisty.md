---
title: "samba shares feisty"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by glennph93 on 2007-04-22
Hi

I'm having a problem connecting my mythbox to my fresh install of feisty via samba. When I first setup samba(in feisty) the same way I set up in dapper everything work great. After a reboot it will not connect again?? Here is my myth log when I try to connect.

[PHP]Apr 22 10:40:06 mythtv automount[8021]: >> Error connecting to 192.168.0.10 (Connection refused)
Apr 22 10:40:06 mythtv automount[8021]: >> 8023: Connection to 192.168.0.10 failed
Apr 22 10:40:06 mythtv automount[8021]: >> SMB connection failed
Apr 22 10:40:06 mythtv automount[8021]: mount(generic): failed to mount //192.168.0.10/mythvideos (type smbfs) on /mnt/auto/movies
Apr 22 10:40:06 mythtv automount[8021]: failed to mount /mnt/auto/movies
Apr 22 10:40:06 mythtv automount[8024]: >> Error connecting to 192.168.0.10 (Connection refused)
Apr 22 10:40:06 mythtv automount[8024]: >> 8026: Connection to 192.168.0.10 failed
Apr 22 10:40:06 mythtv automount[8024]: >> SMB connection failed
Apr 22 10:40:06 mythtv automount[8024]: mount(generic): failed to mount //192.168.0.10/mythvideos (type smbfs) on /mnt/auto/movies
Apr 22 10:40:06 mythtv automount[8024]: failed to mount /mnt/auto/movies
Apr 22 10:40:07 mythtv automount[8027]: >> Error connecting to 192.168.0.10 (Connection refused)
Apr 22 10:40:07 mythtv automount[8027]: >> 8029: Connection to 192.168.0.10 failed
Apr 22 10:40:07 mythtv automount[8027]: >> SMB connection failed
Apr 22 10:40:07 mythtv automount[8027]: mount(generic): failed to mount //192.168.0.10/mythvideos (type smbfs) on /mnt/auto/movies
Apr 22 10:40:07 mythtv automount[8027]: failed to mount /mnt/auto/movies[/PHP]


By the way I'm using autofs on myth with the same credentials as before. Here is the share in smb.conf.

[PHP][mythvideos]
path = /media/sdb1/mythvideos
available = yes
browseable = yes
public = yes
writable = yes[/PHP]


I'm at loss any help would be appreciated.

---

### Post by glennph93 on 2007-04-22
After some digging I seen that samba is not listening.  I noticed this when I tried to restart samba it said it wasn't running when it tried to kill it.Also from this log file ( sudo cat /var/log/samba/log.smbd) it seems to not load (PANIC).  PLEASE HELP


[PHP][2007/04/22 19:46:50, 0] smbd/server.c:main(847)
  smbd version 3.0.24 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2007/04/22 19:46:50, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2007/04/22 19:46:50, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2007/04/22 19:46:50, 0] passdb/pdb_interface.c:make_pdb_method_name(174)
  No builtin nor plugin backend for tdbsam guest found
[2007/04/22 19:46:50, 0] lib/util.c:smb_panic(1599)
  PANIC (pid 22732): pdb_get_methods_reload: failed to get pdb methods for backend tdbsam guest
  
[2007/04/22 19:46:50, 0] lib/util.c:log_stack_trace(1706)
  BACKTRACE: 7 stack frames:
   #0 /usr/sbin/smbd(log_stack_trace+0x22) [0x823dd92]
   #1 /usr/sbin/smbd(smb_panic+0x43) [0x823de73]
   #2 /usr/sbin/smbd [0x81fc16a]
   #3 /usr/sbin/smbd(initialize_password_db+0xe) [0x81fc1be]
   #4 /usr/sbin/smbd(main+0x577) [0x82d9ac7]
   #5 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7b98ebc]
   #6 /usr/sbin/smbd [0x808c7f1]
[2007/04/22 19:46:50, 0] lib/util.c:smb_panic(1607)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 22732]
[2007/04/22 19:46:50, 0] lib/util.c:smb_panic(1615)
  smb_panic(): action returned status 0
[2007/04/22 19:46:50, 0] lib/fault.c:dump_core(173)
  dumping core in /var/log/samba/cores/smbd
[/PHP]

---

### Post by glennph93 on 2007-04-23
After hours of looking and digging I found what was wrong, I think. 

The first time I thought it was working it was not (myth showed me what should have been there). So in haste I switched back to my dapper smb.conf (which was working in dapper). This is what was causing smbd to PANIC/crash, this line** passdb backend = tdbsam guest** in dapper smb.conf was the problem it should have been this** passdb backend = tdbsam**. After switching back to the feisty smb.conf it started up and was listening.

The real culprit was on the myth side, now I don't need any credential line in my autofs configuration file and it connects fine (a little worried about security).

I'm posting this in case anyone has the same problem.

Thanks

Feisty is pretty cool.

---

### Post by Galactix on 2007-05-01
Thanks! I stumbled upon this problem this morning when upgrading my fileserver to Feisty. Bluntly copying my Edgy smb.conf.... well it works again!

---

### Post by maphew on 2007-06-20
this happened to me too. I eventually discovered the problem was that when I search & replaced the comments in smb.conf with newline , it saved it as dos-style instead of unix-style text file. In gedit it looked as I expected, but it was gvim that showed the tell-tale ^M instead of a new line.

---

