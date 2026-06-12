---
title: "Replace XP with Ubunty - looking for automated install"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by zank on 2010-10-05
Hi, i have a windows xp desktop machine that i've been using as a fileserver throguh sharing my 4 external usb drives attached to it. I want to replace this sytem with ubuntu (unless theres a different alternative for waht i want to do?). 
the problem is its not a standard install i can just do.

- first, the desktop has no keyboard mouse or monitor connected and i generally used vnc to control it.
- the computer right now is heavily infected with some kind of virus. disabld all my anti virus software, wont allow me to use new ones, etc. 

my only option really is to wipe it clean and this time not xp, i want ubuntu. is there a way to configure an ubuntu install (or find a preconfigured install) to basically boot automatically from cd/usb drive when i restart my computer, do the install with no user intervention, and upon finalization install a vnc server on the install so i can get back in.

please remember this is my first time wiht ubuntu and while i know more than your average user about computers, id ratehr not muck around. i jsut want to be able to download a standard install, put a file on the installation cd or usb drive and let it install itself.

any help doing this?

another note, 4 of my external drives connected via usb are ntfs, and 1 is hfs. can ubuntu read/write to all of these systems? if not out of the box, can i later enable these filesystems somehow?

---

### Post by mörgæs on 2010-10-05
Hi, welcome to the forum.

The present flora of vira on the machine is no problem. Everything will be erased when you install Ubuntu.

I don't think there is an install like you describe. The best option is probably to bring the machine to a friend, where you can borrow mouse, keyboard and screen for a few hours.

Keep as few external connections (especially USB) as possible while installing but remember to have wired internet access.

---

### Post by zank on 2010-10-05
will ubuntu automaticall pick up my ntfs/hfs drives once installed, the way windows and leopard do, or do i have to run complicated mount commands?
as for sharing, is it simple like in xp/leopard where you right click and go into some options?

---

### Post by mörgæs on 2010-10-05
There are lots of guides describing how to access the other file systems. Here is something to get you started:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)

I have never used Apple, so I can not talk from experience. 

Normally I don't like the answer 'just google it', but in this case it is actually a good option.

---

### Post by pricetech on 2010-10-05
As far as sharing, you'll want Samba installed.  In Synaptic search for system-config-samba which will install both Samba and a GUI configuration tool.

---

### Post by spcwingo on 2010-10-05
Have a look-see here:

[http://www.howtoforge.com/ubuntu-home-fileserver]("http://www.howtoforge.com/ubuntu-home-fileserver")

---

### Post by mörgæs on 2010-10-06
> **spcwingo said:**
> Have a look-see here:

[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

Seems like a good tutorial, except that it talks of obsolete Ubuntu releases. Have you tried with 10.04?

---

### Post by spcwingo on 2010-10-06
> **mörgæs said:**
> Seems like a good tutorial, except that it talks of obsolete Ubuntu releases. Have you tried with 10.04?

No, but I don't see anything that would prevent you from doing this with 10.04.

---

