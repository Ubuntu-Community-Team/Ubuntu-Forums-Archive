---
title: "Virtual PC and 8.04 installation issue"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by geekazine on 2008-04-26
I downloaded 8.04 tonight to try out on a Virtual PC connection. I went to install, and I got the message: 

An unrecoverable Processor Error has occurred 

I cannot install or even just load up the disk. The only thing that doesn't give the error is if I do a memory check. 7.10 loads fine. 

I am running XP with Virtual PC 2007. I bumped up the memory to 512. 

I even thought I might have a bad .iso, so I downloaded from another mirror. No change. 

Any thought as to why this is happening?

---

### Post by Jshaw on 2008-04-27
I have run into this problem as well, and while this solution didn't work for me, it did work for others. Try setting it to safe graphics mode and then in advanced options type "noapic nolapic vga=791" without the quotations.

---

### Post by NeonBible on 2008-05-20
I am having this problem too.

I managed to get past the error with &#8220;vga=791 noreplace-paravirt&#8221;

But it just hangs at a black screen for ages.  Is it supposed to do that?

---

### Post by NeonBible on 2008-05-20
I am having this problem too.

I managed to get past the error with “vga=791 noreplace-paravirt”

But it just hangs at a black screen for ages.  Is it supposed to do that?

---

### Post by jtrindle on 2008-05-20
Look here:

[http://arcanecode.wordpress.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/](http://arcanecode.wordpress.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/)

especially in the comments.  My line ended up something like:

noapic nolapic noreplace-paravirt i8042.noloop clock=pit 

I got the install to work.  However, I still had troubles booting directly into the hard drive image, even with the menu.lst edited.

I finally gave up on Virtual PC.  VMWware Server 1.05 worked perfectly out of the box.

[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

---

### Post by NeonBible on 2008-05-21
I found this in the end- [http://blogs.technet.com/seanearp/archive/2008/05/13/installing-ubuntu-8-04-hardy-heron-in-virtual-pc-2007.aspx](http://blogs.technet.com/seanearp/archive/2008/05/13/installing-ubuntu-8-04-hardy-heron-in-virtual-pc-2007.aspx)

Worked for install and booting.  Also getting sound and higher resolution to work.

---

