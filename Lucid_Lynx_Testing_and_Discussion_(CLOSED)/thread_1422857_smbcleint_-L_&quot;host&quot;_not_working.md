---
title: "smbcleint -L &quot;host&quot; not working"
date: 2010-03-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by maestrobwh1 on 2010-03-05
I can browse my samba share with dolphin via network smb://eee-box where eee-box is my host. 

I can also use xsmbrowser to browse and mount my shares.

However, I am experiencing something very odd with smbclient

```
ubuntu@IBM-TP:~$ smbclient -L eee-box
Enter ubuntu's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.0]
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: NT_STATUS_ACCESS_DENIED

```

---

### Post by maestrobwh1 on 2010-03-05
added after doing an hour of searching and finding this 
[http://sidux.com/PNphpBB2-viewtopic-t-14163.html](http://sidux.com/PNphpBB2-viewtopic-t-14163.html)

```
####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
# client ntlmv2 auth = no
# security = share
[B]client lanman auth = Yes
lanman auth = Yes [/B]

```

and now my shares list from my host machine (running karmic) on my guests (running lucid).

---

### Post by DeusEx on 2010-04-18
cheers
works for me as well!
I had the same error after last update or so.

---

