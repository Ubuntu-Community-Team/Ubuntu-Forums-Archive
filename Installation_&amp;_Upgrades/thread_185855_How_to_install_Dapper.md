---
title: "How to install Dapper?"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by Zdravko on 2006-06-01
Could you tell me please, how to install Dapper? I already downloaded 
[ubuntu-6.06-desktop-i386.iso]("http://se.releases.ubuntu.com/6.06/ubuntu-6.06-desktop-i386.iso"), 

[LEFT]checked MD5sum - it was OK. 
[/LEFT]
Then I burned it to a CD. After setting the boot options in BIOS, a menu appeared with a counter. 
Unfortunately, when I select "Install or run" it never performs any installaion.
Instead of this it just tries to load the whole OS in RAM!
I thought I downloaded a INSTALL version?

---

### Post by frodon on 2006-06-01
The installer of the desktop CD is graphical and executed through the live CD, that's why it lauchs the live CD first in the RAM to setup the GNOME environment.
The CD which use the text based installer is the alternate CD.
[IMG]http://www.ubuntu.com/testing/dapperrc?action=AttachFile&do=get&target=liveinstall.png[/IMG]

---

### Post by Klaidas on 2006-06-01
When you boot, there is an ion on the desktop "Install" Click it ;)

---

### Post by Zdravko on 2006-06-01
Thank you very much for the help!
Now I have another problem - and I don't want to flood this place - that's why I'll stick to this post.
I have already Windows and Breezy installed and dualboot. Via the Dapper installer I repartitioned the Breezy parts:
/dev/hde1, ntfs, 20GB, boot (untouched - for Windows)
/dev/hde2:extended, 56.33GB -lba (what could it be this?)
/dev/hde5, ntfs, 30GB (untouched - Windows data)

Now here follows the new partitions:
Nr1. ext3 23.44GB (here I want the '/')
Nr2. swap, 512MB
N3. fat32, 2.15GB (for swapping data between OS's)

After applying the changes I get a very confisuing window - where should be the mount point? The listboxes are confisung. Help me.

---

