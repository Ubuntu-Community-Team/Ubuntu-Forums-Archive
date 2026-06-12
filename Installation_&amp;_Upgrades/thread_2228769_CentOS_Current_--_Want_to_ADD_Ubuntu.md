---
title: "CentOS Current -- Want to ADD Ubuntu"
date: 2014-06-09
forum: Installation &amp; Upgrades
---

### Post by jacob38 on 2014-06-09
I tried my hardest to get Ubuntu to work properly before on my server; though, I do not have a DVD drive and it is not configured to boot from USB. So I was unable to get Ubuntu operational on the server before. I now have CentOS 6.5 running on the server but with my limited experience in Linux I need more GUI interface programs, CentOS uses A LOT of terminal work.

Either way, if I download a Ubuntu .iso on the server can I run and install it side-by-side with CentOS? I have CentOS using all the partition space right now, can Ubuntu "steal" some of that space and be able to install or do I need to re-install everything if I were to go that route?

---

### Post by SeijiSensei on 2014-06-09
Most versions of CentOS come with GNOME desktop.  Doesn't yours?

If you want to install Ubuntu as well, you would need to repartition the drive.  The other option is to use a VM like VirtualBox.

In the long run, though, server administration is best handled at the command prompt.  That's just as true for Ubuntu as for any other distribution.  In fact, the server version of Ubuntu comes with no GUI interface at all.

---

### Post by Gyokuro on 2014-06-09
HiDue to that CentOS uses LVM you can resize the space and have a dual boot system but in case your system supports hardware virtualization install your Ubuntu Server in KVM on top of CentOS It's easier, you need less time. However I'm not sure whether you are using Ubuntu server or an Ubuntu desktop product - in case of the server product you have to do the administration via command line or install the desktop parts which you can do on your CentOS installation too.

---

### Post by buzzingrobot on 2014-06-09
If you make the space available, you could, indeed add Ubuntu. But, you would not be able to use it, in any practical sense, to administer CentOS. If you are looking for GUI tools to use to help administer your CentOS server, then you need to install the CentOS GUI. That GUI is Gnome 2, which is installed by default unless someone specifically omits it.  Check the CentoS site -- centos.org -- for how-to's.

Typically, server installs include no GUI tools.  That includes Ubuntu's server installation.

---

