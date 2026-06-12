---
title: "Ubuntu and MS Virtual PC 2007"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by coder1024 on 2007-05-30
I'm running Windows XP and MS Virtual PC 2007.  I created a new virtual machine, started it, and booted off the Ubuntu installation CD (v7.04 i386).

I selected "start or install Ubuntu" and it seemed to go ok for awhile.  After a bit with the progress bar moving back and forth and eventually filling up, the window for the virtual machine switched to a really wide non-standard size and went black while it continued loading.

Eventually some graphics displayed but they were all distorted and not readable.

I retried this, and this time used the additional options and specified 1024x768x32 hoping that would fix the size and prevent the issue and it didn't work.

I also tried using the Virtual PC 2007 settings, telling it to only use standard resolutions but this didn't work either.

Anyone else able to get Ubuntu v7.04 installed using MS Virtual PC 2007?  Any tricks to getting this to work?

---

### Post by Dryvlyne on 2007-05-30
Hello, I tried setting up Ubuntu on Virtual PC as well just over a month ago and couldn't get it to work. After doing some digging around it appears that no *NIX OS is officially supported via Virtual PC (although some distros do work).

You might want to look into giving VMPlayer a try - [http://www.vmware.com/products/player/](http://www.vmware.com/products/player/). It too allows you to run a virtual machine and is compatible with *NIX OS's (though not 64-bit versions). Once installed check out their VIrtual Appliance marketplace for OS's [here](http://www.vmware.com/vmtn/appliances/directory/cat/45). Unfortunately I only see German versions of Ubuntu Fiesty available at the moment. Although if you know a bit of German you should be able to switch the language to English after installation.

Ultimately I had a spare hard drive around and setup a dual-boot system on my machine. I'm now in the process of trying to use Ubuntu exclusively, but it's nice to still have Windows available just in case I screw something up in Ubuntu and need a quick way to get on the Internet and research an issue or download updated files.

Regards

---

### Post by coder1024 on 2007-05-31
Thanks for the reply.  For now, I've given up on Virtual PC and switched to VMWare's free server product.  Although it seems significantly more heavy weight and is a bit more complicated to use, it actually has a specific option for Ubuntu when you create the virtual machine.  Using VMWare server, I was able to install Ubuntu without any issue and am able to run it fine inside Windows XP.  I prefer Virtual PC as its very light-weight and almost trivial to use in comparison to VMWare, but since it doesn't work, I guess for now its VMWare :-)  Since I was able to get it to work with a fresh machine I opted to do that and do the full install myself rather than using the player with a pre-built machine, although I suppose that could work as well.

For me, dual-booting isn't an option, nor is completely switching to Ubuntu.  My preference is to keep Windows XP as my primary OS, but be able to run Ubuntu at the same time in a window (as is possible with VMWare).  This allows me to run SW which only provides Linux versions and to learn Ubuntu and Linux, and perhaps do some Linux development, while still using Windows as my primary OS.  To each his own of course, but virtualization fits this scenario perfectly.

Anyway, the short version is VMWare works :-)

---

### Post by coder1024 on 2007-05-31
for reference, I noticed someone asked this question over on the Virtual PC MS newsgroup ([http://www.microsoft.com/windowsxp/expertzone/newsgroups/reader.mspx?dg=microsoft.public.virtualpc&lang=en&cr=US](http://www.microsoft.com/windowsxp/expertzone/newsgroups/reader.mspx?dg=microsoft.public.virtualpc&lang=en&cr=US)).

Someone responded with some links which I've pasted below in case this helps.

---

Finally I can help someone with Ubuntu and VPC 2007

After getting help from others, I can finally help someone else, what a 
great feeling…anyway, someone else solved the problem, but here are the 
links.



1.	If you’re trying to install Ubuntu 7.04 and are having trouble with 
the mouse issue, go here:
[http://arcanecode.wordpress.com/2007/05/17/fixing-ubuntu-704-fiesty-fawn-mouse-under-virtual-pc-2007/](http://arcanecode.wordpress.com/2007/05/17/fixing-ubuntu-704-fiesty-fawn-mouse-under-virtual-pc-2007/)

2.	If you’re trying to install Ubuntu 6.06 and are having trouble with 
the 24bit color issue, go here:
[http://haacked.com/archive/2007/05/06/installing-ubuntu-on-virtual-pc-for-windows-lovers.aspx](http://haacked.com/archive/2007/05/06/installing-ubuntu-on-virtual-pc-for-windows-lovers.aspx)

Hope this helps

Chaz

---

