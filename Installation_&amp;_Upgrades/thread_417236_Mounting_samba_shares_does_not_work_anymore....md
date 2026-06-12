---
title: "Mounting samba shares does not work anymore..."
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by StoneDragon on 2007-04-21
I get the following error, if I try to mount a samba share with cifs:

retrying with upper case share name
mount error 6 = No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

The fstab entries  on the client side for the shares have not changed. But the client is also feisty, so I'm not sure, if it's a client or a server problem...
I already reinstalled all samba-stuff (including smb.conf and the passwords) on the server to eliminate risk of having old incompatible entries in smb.conf => did not help.

This is smbclient -L output shows o.k. though:
Domain=[LURCHIE] OS=[Unix] Server=[Samba 3.0.24]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        stuff           Disk      hobbes stuff
        data            Disk      hobbes stuff
        windata         Disk      hobbes stuff
        IPC$            IPC       IPC Service (lurchie server (Samba, Ubuntu))
Domain=[LURCHIE] OS=[Unix] Server=[Samba 3.0.24]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        MIDDLEEARTH          LURCHIE

I appreciate any help. As far as I have seen, many other users are having theses troubles too, but I did not stumble over any solution yet.

---

### Post by spin2cool on 2007-04-21
Try using ip addresses instead of hostnames and see if you can connect:

so instead of //xyz/share, 
try //192.168.1.103/share

---

### Post by StoneDragon on 2007-04-21
> **spin2cool said:**
> Try using ip addresses instead of hostnames and see if you can connect:

so instead of //xyz/share, 
try //192.168.1.103/share

Thanks, but that's sure not the problem, as I use only IP's in my client's fstab...(and the error message would be another, afaik).

---

### Post by stevecs on 2007-04-21
did you check that your shares are available  "available= yes" and browseable "browseable=yes" in your smb.conf file?     In upgrades generally that gets updated to turn both of them off to avoid opening up something that you didn't intend.

---

### Post by StoneDragon on 2007-04-21
Just the standard stuff the same as before:

[data]
comment = hobbes stuff
path = /media/data/
valid users = hobbes
write list = hobbes
max connections = 6
case sensitive = yes
msdfs proxy = no
hosts allow = 192.168.1.0/24

BONK! I just found out! 
just kick away the line
msdfs proxy = no

and it'll work again!

---

### Post by RobMongoose on 2007-04-28
> just kick away the line
msdfs proxy = no

and it'll work again!


Thanks for this.

Got my samba shares working again with Feisty :)

---

### Post by dvessels on 2008-04-20
*Since I'm not quite so technically sharp I have to make sure we're talking the same language. I must therefore speak in simpler, more direct language.* In Ubuntu 8.04 I can't get a "working" network connectiion. Internet works fine, but browsing interior home network, the browser seems unable to load anything below the level where it sees other network machines. It sees Windows workgroup and machines in the workgroup. Does not display shares on shared Windows machines. With Ubuntu7.10 I can browse, copy, move, etc., to heart's content.

Yeah, I know--maybe I should go back--at least until it's all settled. I sure do like some of the nice new features, though!

dried vessels

---

