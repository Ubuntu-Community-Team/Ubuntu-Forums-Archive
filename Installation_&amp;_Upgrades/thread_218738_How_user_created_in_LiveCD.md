---
title: "How user created in LiveCD?"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by mzoller on 2006-07-19
I am currently trying to adapt a dapper liveCD and need to change some of the defaults for the ubuntu user which is created when the livecd is booted.

* Where is the user added (what script/conffile)?
* Maybe it is just a templated getting copied (in that case where is it?)

Any help apreciated!

Michael

---

### Post by dostl_ba on 2006-07-20
I'm interested in that too.

I simply created a new user which i can login, but in /etc/gdm/gdm-cdd.conf it says user ubuntu should be logged in automatically.

when/where is that file generated? Under the original squashfs-system the file doesnt exist ...

TIA

---

### Post by mzoller on 2006-07-20
> **dostl_ba said:**
> 
I simply created a new user which i can login, but in /etc/gdm/gdm-cdd.conf it says user ubuntu should be logged in automatically.


Well I suppose that would be a workaround I haven't thought of yet. Not as clean as I would have liked - but probably easier as continuing searching for the mysterious "adduser" command. :-k 

> **dostl_ba said:**
> 
when/where is that file generated? Under the original squashfs-system the file doesnt exist ...


:confused: I have looked through all the rc2.d skripts an rc.local and all the other (likely and unlikely) places I could think of. 
I suppose an adduser is easy to overlook though...

BTW I am going to create a Kiosk Browser LiveCD with mozilla an OpenKiosk.

Michael

---

### Post by dostl_ba on 2006-07-20
[https://help.ubuntu.com/community/LiveCDCustomization?highlight=%28livecd%29](https://help.ubuntu.com/community/LiveCDCustomization?highlight=%28livecd%29)

Simply adjust the session and save it. Then tar czf /home/ubuntu, save it and extract it to /etc/skel when customizing the CD.

---

### Post by dostl_ba on 2006-07-20
While this looks like a workaround, im still interested in how the user is created, because i added a system user which runs a server daemon. Now Automatic login doesnt work: gdm wants to login ubuntu, and asks for a password which doesnt exist. (as far as i know).

So some detailed infos on the adduser process are highly appreciated.

---

### Post by dostl_ba on 2006-07-21
Got it:

When chrooted to you new Live CD, look in 

/usr/share/initramfs-tools/scripts/

There you find the init scripts, e.g. casper-bottom/10adduser

I hope i can figure out from here ...

Regards, Sebastian.

---

### Post by mzoller on 2006-07-21
> **dostl_ba said:**
> Got it:
/usr/share/initramfs-tools/scripts/

There you find the init scripts, e.g. casper-bottom/10adduser


](*,) Makes sense now that I read it ... You should add that to the wiki!

Thanks!
Michael

---

### Post by Tasu on 2006-08-19
> **dostl_ba said:**
> Got it:

When chrooted to you new Live CD, look in 

/usr/share/initramfs-tools/scripts/

There you find the init scripts, e.g. casper-bottom/10adduser

I hope i can figure out from here ...

Regards, Sebastian.

Hmmmm! This is not enough! Hmmm! I changed the user in /usr/share/initramfs-tools/scripts/casper and deleted some scripts from /usr/share/initramfs-tools/scripts/casper-bottom/, but the newly generated livecd seems to run the scripts from another position, becuase it always adds the ubuntu user and executes the scripts I deleted, it seems the modifications I've done are not understood by th livecd! Any idea?

---

### Post by olympionex on 2007-01-22
Tasu,

Check out this page:
[https://help.ubuntu.com/community/LiveCDCustomization/6.06](https://help.ubuntu.com/community/LiveCDCustomization/6.06) 

It says that if you change those scripts, you need to rebuild your initramfs in the chroot environment and copy that to /yourlivecddirectory/casper/initrd.gz

Hope that helps

---

### Post by Tasu on 2007-01-23
> **olympionex said:**
> Tasu,

Check out this page:
[https://help.ubuntu.com/community/LiveCDCustomization/6.06](https://help.ubuntu.com/community/LiveCDCustomization/6.06) 



Indeed I know, after some researches I managed to understand that step and I wrote those lines in that wiki page (sorry for not signing my contributions on that wiki!)! ^_^

---

### Post by olympionex on 2007-01-24
Ah, then thank you for figuring it out.

---

### Post by forestbird on 2008-01-13
ty

---

