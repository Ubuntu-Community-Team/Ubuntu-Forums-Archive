---
title: "I turn off the symbolic link protection?"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by kalmarr on 2010-03-27
Hi!
  I have a server UBU 9.04 (file server). I could use to this day, when I upgraded. I can use the file share, but I can&#8217;t use the symbolk links. If I want entry or use I can&#8217;t it.
  I solved the symbolic links to each user's file management.
  
I write the example my share:


  gerorge - user see
  -          private directory
  -          document &#8211; symolic links


  I can see perfect the &#8222;private directory&#8221;, I can&#8217;t see document &#8211; symolic links
  I would like to know I how can use the symbolic links? Posibble, Do I turn off the symbolic link protection?


  I sent the my smb.conf
   
  #======================= Global Settings =======================
  [global]
log file = /share/sysop/log/samba-log.%m
logon drive = y:
  debug timestamp = yes
map to guest = bad user
domain master = yes
encrypt passwords = true
time server = yes
passdb backend = tdbsam
passwd program = /usr/bin/passwd %u
wins support = true
dns proxy = no
netbios name = matrix
server string = Kozpont - SAMBA %v
logon script = U%.bat
unix password sync = yes
local master = yes
workgroup = mshome
logon path = \\matrix\kozponti\
os level = 34
security = user
usershare allow guests = yes
panic action = /usr/share/samba/panic-action %d
preferred master = yes
max log size = 1000
pam password change = yes
log level = 2
domain logons = yes
  [netlogon]
comment = Network Logon Service
path = /share/sysop/netlogon/
public = no
;guest ok = yes
writeable = yes
browseable = no
  [printers]
comment = All Printers
browseable = yes
path = /var/spool/samba
printable = yes
guest ok = yes
read only = yes
create mask = 0700
  [print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = yes
guest ok = no
  [sysop]
browseable = yes
writeable = yes
guest ok = no
valid users = george
path = /share/
create mode = 777
directory mode = 777
  [kozponti]
browseable = yes
writeable = yes
path = /share/sysop/users/%U/
revalidate = yes
comment = &#258;&#347;dv&#258;¶z&#258;¶llek %U! - Saj&#258;&#711;t fi&#258;&#322;k
valid users = george
create mode = 777
directory mode = 777
  ---
  

I am waiting the solution :)



  KALMI

---

### Post by nexist on 2010-04-16
My problem was fixed by [http://ubuntuforums.org/showthread.php?t=1439092](http://ubuntuforums.org/showthread.php?t=1439092)

---

