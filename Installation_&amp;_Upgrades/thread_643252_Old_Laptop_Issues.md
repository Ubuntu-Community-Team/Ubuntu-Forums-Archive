---
title: "Old Laptop Issues"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by Torginator on 2007-12-17
I am attempting to put a minimal Ubuntu on an old laptop. It's a ThinkPad 750P with a 33MHz 486 CPU, 36MB RAM and a 5GB disk. That should be enough to get a minimal installation right?

What I've done is made a FreeDOS boot diskette, and I can get the contents of the Ubuntu Mini ISO onto a RAM disk, and I can use linld097 to load the image, but it crashes and dumps a lot of text that flies off the screen.

How can I debug this process and get the installation to start? Any tips or pointers are most welcome.

---

### Post by logos34 on 2007-12-17
> **Torginator said:**
> I am attempting to put a minimal Ubuntu on an old laptop. It's a ThinkPad 750P with a 33MHz 486 CPU, 36MB RAM and a 5GB disk. That should be enough to get a minimal installation right?

Not even close.  (Server maybe--wanna run it from command line?)

Think DSL (Damn Small) or Deli linux.

---

### Post by kerry_s on 2007-12-17
try dsl-> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by Torginator on 2007-12-17
A server install and command line is exactly what I want. To start with. There's no reason I shouldn't be able to get X running. Gnome or KDE are another matter entirely, and I'm OK with that.

Now... any tips on debugging the crash, anyone?

---

### Post by logos34 on 2007-12-17
ok, if it's just the text-based installation then you might be able to start that, but you're at the low end of the ram requirements--32 mb is pretty much rock bottom.  Sometimes you can get by with a little less, some machine need a little more.  Depends.  To be honest I've never tried it with those low specs.  I've only seen [this guide]("https://wiki.ubuntu.com/Installation/FromWindows") (but it assumes you at least have an older version of windows--> section 'Windows 95/98/ME (using Loadlin')).

---

### Post by louieb on 2007-12-17
[Installation/LowMemorySystems - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Installation/LowMemorySystems")
On a hoot I followed this guide. On a PII-400 384MB memory. The server alone  uses 19-21 MB. When  I start x and Fluxbox - free shows 31MB used.

Might be better off finding a distro using a 2.4 kernel Some of the older Slackware releases come to mind as something that could  run a pretty decent command line system on that machine.

---

### Post by kerry_s on 2007-12-17
you need to put a boot parameter for the small screen size, since it's below 800x600 you'll always get a crash because it's out of range. save yourself a lot of headaches grab DSL they have already done all the work to function on those low specs. all you have to do is type> dsl xsetup <and hit enter.

---

### Post by Torginator on 2007-12-18
> **logos34 said:**
> I've only seen [this guide]("https://wiki.ubuntu.com/Installation/FromWindows") (but it assumes you at least have an older version of windows--> section 'Windows 95/98/ME (using Loadlin')).

I'm not installing from Windows. I have seen a guide with instructions from DOS, but it's too old as LOADLIN doesn't work with the new large kernels. 32MB is rock bottom, and my 36MB should be enough to at least install and really learn how much pain I'll get from trying to use the machine.

---

### Post by Torginator on 2007-12-18
> **louieb said:**
> [Installation/LowMemorySystems - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Installation/LowMemorySystems")
On a hoot I followed this guide. On a PII-400 384MB memory. The server alone  uses 19-21 MB. When  I start x and Fluxbox - free shows 31MB used.

Might be better off finding a distro using a 2.4 kernel Some of the older Slackware releases come to mind as something that could  run a pretty decent command line system on that machine.

That is an excellent guide. Thanks for that, but my machine has no CD drive. I am not interested in older distributions, as I have installed Debian Woody pretty easily. I want something newer, and Ubuntu documents say it will run on a 486 with 32MB RAM, so I'm up for it.

---

### Post by Torginator on 2007-12-18
> **kerry_s said:**
> you need to put a boot parameter for the small screen size, since it's below 800x600 you'll always get a crash because it's out of range. save yourself a lot of headaches grab DSL they have already done all the work to function on those low specs. all you have to do is type> dsl xsetup <and hit enter.

This is of no help at all. First, I'm using the text mode installer and the Mini ISO image. Second, you have no idea what screen size I have. Third, what is the boot parameter? Fourth, don't assume I haven't tried DSL or that you are answering the question you think I'm asking. I have tried DSL, and it is not at all what I want. I tried to install it, but it was more difficult than Debian, so I gave up. Ubuntu is supposed to work on this machine.

Now, if you could provide a tip like "send console output to the serial port and capture that so we can have a look. add this to your linld command line:"... now THAT would be helpful and get us somewhere. I plan to fully document this procedure so others can benefit from it.

---

### Post by kerry_s on 2007-12-18
> **Torginator said:**
> This is of no help at all. First, I'm using the text mode installer and the Mini ISO image. Second, you have no idea what screen size I have. Third, what is the boot parameter? Fourth, don't assume I haven't tried DSL or that you are answering the question you think I'm asking. I have tried DSL, and it is not at all what I want. I tried to install it, but it was more difficult than Debian, so I gave up. Ubuntu is supposed to work on this machine.

Now, if you could provide a tip like "send console output to the serial port and capture that so we can have a look. add this to your linld command line:"... now THAT would be helpful and get us somewhere. I plan to fully document this procedure so others can benefit from it.

okay, you sound like you got it all under control.

Some specs: 33MHz 486, 36MB RAM (maxed out), 2.88MB floppy, two PC Card
slots (16-bit). No CD-ROM drive. Grayscale 640x480 display. Pen interface
that works like a tablet.

---

### Post by Torginator on 2007-12-26
Dapper Drake installed without a hitch. The netboot files (linux and initrd.gz) work just great both for that version and for Edgy Eft, but Feisty and Gutsy both fail.

Anyone getting crashes just after loading those files might have better luck with the older versions.

Now what about upgrading? Will the machine crash on newer kernels? Does anyone know or should I give it a try?

---

### Post by Torginator on 2007-12-26
My documentation of putting Ubuntu on my ThinkPad 750P:

[http://thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_750P]("http://thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_750P")

I know it's not perfect, so suggestions for improvements would be most welcome.

---

### Post by Craigus on 2007-12-26
> I know it's not perfect

Actually, that's a nice job, IMHO. Thanks for making the effort to make this available for others.

---

