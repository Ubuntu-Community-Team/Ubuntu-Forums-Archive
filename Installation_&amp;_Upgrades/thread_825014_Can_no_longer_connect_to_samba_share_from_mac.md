---
title: "Can no longer connect to samba share from mac"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by surfer63 on 2008-06-10
One week ago I updated my ubuntu feisty server to gutsy and four days later to hardy. On Gutsy it still worked OK. Since upgrading to Hardy I can no longer connect to my "valid users" share from my apple mac running 10.4.11. I can connect to my read only "guest" shares, but I can't connect to my "valid users" shares. I have my global section and an example of a guest and valid users section of my smb.conf.
Please note that I can connect from a windows XP pc to the valid users shares. I've searched the forum (and google) but I can't find equal problems.


[global]
  workgroup = THUIS
  printcap name = cups
  printing = cups
  security = share
  disable spoolss = Yes
  show add printer wizard = No
  wins support = yes
  domain master = no
  local master = yes
  preferred master = yes
  os level = 65
  name resolve order = wins lmhosts

[rdata]
comment = RO form of big datadisk
path=/data
read only = yes
guest ok = yes
nt acl support = No

[wdata]
comment = RW form of big datadisk
path=/data
writable= yes
guest ok = no
valid users = harryvanderwolf
nt acl support = Yes

Has anyone a clue?

---

### Post by Audiosears on 2008-06-11
surfer,

one issue I ran into with Hardy was that with the new samba package (3.0.28a) included with it, you have to specify a couple of new things for some of their security changes.

I don't know if this would apply to OSX, but it could be that OSX uses encrypted passwords using the lanman part of the password hash in your /etc/samba/smbpasswd file instead of the NT side.  Win98 and NT machines (pre-SP4) connect this way, and NT SP4 / XP and later use the NT hash.  just about everything after win95 uses encrypted passwords instead of plaintext also, and OSX would probably follow suit.

Your /etc/samba/smbpasswd file contains string entries that ddefine the username, userid, and two sets of alphanumerics that represent the lanman hash and the NT hash.  These are the entries that are checked against to authenticate the client.  if you see X's instead of letters and numbers, then the password is not valid and the client will not be able to connect.

I don't see 'encrypt passwords = yes' in your [global] section, but you will probably need that as well as 'lanman auth = yes'.  Take a look at your /etc/samba/smbpasswd file, find the username in question, and see if either of the files look something like this example:

gk:1000:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:3A7F56DC5DB01A34FC389A6FB2954BC0:[U          ]:LCT-46E93487:

gk is the username
1000 is the uid
XXXXXXXXXXXXXXXXXXXXX is the lanman hash (in this case, disabled)
3A7F56... is the NT hash
[U..] is the parameters section (indicates this is a user password)
LCT-... is a hex code for the last time the password was changed

If either side has the X's, try adding those two global options to your /etc/samba/smb.conf file, and run smbpasswd <username> (where <username> is the one you want to connect with), and reset the password.  After editing the smb.conf file you will have to restart samba, easily done using the command

/sbin/service smb restart


Check out this article for more:

[http://www.nabble.com/Side-effect-of-recent-change-to-more-secure-defaults-like-%22lanman-auth-%3D-No%22-intentionally--td12665350.html](http://www.nabble.com/Side-effect-of-recent-change-to-more-secure-defaults-like-%22lanman-auth-%3D-No%22-intentionally--td12665350.html)

---

### Post by surfer63 on 2008-06-12
Thanks a lot Audiosears. 
This solves the problem. I addded the lanman authentification to my smb.conf, restarted samba, recreated my smbpasswd and now it functions again.

---

