---
title: "Can not boot to Windows 8 after Ubuntu installation"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by Christopher_Hartford on 2013-10-19
I'm having serious issues here. I don't know what happened, but I cannot boot into Windows 8 no matter what I do. I installed Ubuntu 12.04 and I tried to update it to Ubuntu 12.10 and when I went to boot it up...I got nothing but a black screen. So I downloaded 13.10 from the Ubuntu website and made a flash drive to boot up from. I chose to install 13.10 by removing 12.10 and installing 13.10 overtop of it. Now it will only boot into Ubuntu and Windows is nowhere to be found. I see the option in my GRUB but it says that it can't find the .efi or whatever. I'm not extremely proficient with Linux yet, so if someone could help me out and be as clear as possible...I'd be forever thankful.

[http://paste.ubuntu.com/6266751/](http://paste.ubuntu.com/6266751/)

---

### Post by oldfred on 2013-10-19
Old thread is about a year old and solved, few will look at it.

You have what looks like an Ultrabook with a 32GB SSD and Intel SRT. 
And you now show no Windows install at all.
When installer came up you probably saw no Windows because of the Intel SRT which uses RAID somehow.
I would file this as a bug report but most have just turned off Intel SRT, removed the RAID meta data installed correctly and restarted Intel SRT in Windows without issue. More details in link in my signature.

If you did no make backups you will have to contact vendor and see if you can get a recovery DVD.  Do not explain why, just that drive needs recovery DVD. They may ship it or just charge shipping. Otherwise you will have to purchase a full Windows 8 install.

       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

