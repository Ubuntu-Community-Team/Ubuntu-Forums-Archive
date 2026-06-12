---
title: "ubuntu partitioning while installing"
date: 2012-12-30
forum: Installation &amp; Upgrades
---

### Post by krksidhu on 2012-12-30
[FONT="Lucida Console"]Hi everybody, just starting out with Ubuntu and I've been reading the documentation and I'm a little confused on the best way to go about partitioning to install Ubuntu. I'm going to be installing the version 12.10 and attempting to dual boot with Windows 8 32bit on a single disk drive on my laptop. I would really prefer not to have to wipe out Windows 8 to do this and it seems like I don't have to but I'm not sure the best way to go about creating the blank partition before I install Ubuntu. 

I'll be working with C drive which currently contains only Windows 8. The main partition is 590gb and I have 150gb free. I'd like to create in that free space.

What would be the best way to go about partitioning for Ubuntu without wiping out Windows 8 and starting all over to be able to dual boot with my set up?

And also I want to know how much of size must be given to each partition while installing ubuntu from that free space 150 GB.

please mention the size by each partition.
like, for example, 
swap --- some GB,
/usr --- some GB, like that.....

Thanking you very much.....

[/FONT]

---

### Post by HomelandSecurity on 2012-12-30
just follow the steps in here

[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)

---

### Post by offgridguy on 2012-12-30
Just reading some of the comments from the above link, not totally trouble free.

Since you have 150 gb free space that you want to install to,  you can choose
the option, install  to free space and the ubuntu installer will do it for you
automatically, including swap.

---

### Post by krksidhu on 2012-12-31
Thank you for you help.... I will be trying them.....

---

### Post by grahammechanical on 2012-12-31
That blog post says this:

> Note that this article does not address dual-booting between Windows 8 and Ubuntu 12.10 on a computer preloaded with Windows 8. Such computers tend to have additional partitions for Windows that you will not create on your own. Not to mention the problem associated with Restricted Boot (Secure Boot).

The blogger is not in the same situation as the original poster.

this might be more useful:

[https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")

Please also read about Ubuntu Secure Remix

[https://help.ubuntu.com/community/UbuntuSecureRemix]("https://help.ubuntu.com/community/UbuntuSecureRemix")

You will need the 12.10 version

[http://sourceforge.net/projects/ubuntu-secured/]("http://sourceforge.net/projects/ubuntu-secured/")


Regards.

---

