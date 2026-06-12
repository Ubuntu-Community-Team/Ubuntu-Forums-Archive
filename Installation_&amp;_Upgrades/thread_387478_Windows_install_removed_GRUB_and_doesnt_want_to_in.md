---
title: "Windows install removed GRUB and doesn\t want to install"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by 1002285 on 2007-03-18
What did I ever do to harm you, Bill Gates?

I have a multiboot computer with LinuxMint and Windows XP. I decided to install XP again, because I suspected Dell's own install was not good.

Windows setup said that it was not recommended to install on a partition where there was a Windows install already. Then I deleted the partition and wanted to install on that. Windows setup said that I already had a maximum allowed number of partitions. And it had already managed to wipe out GRUB I think because I cannot boot into my LinuxMint install any more. What can I do now? 

I am now using Mints's LiveCD, formatting the Windows partition to NTFS again and will try to install Windows XP on that then. But how do I get the GRUB back? Do I really need to install LinuxMint again? Installing the OS would not be very time consuming, but I have already installed automatix, made azureus work correctly, etc, so I wouldn't want to start all that over again.

---

### Post by christhemonkey on 2007-03-18
See this howto:
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

or this one:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by 1002285 on 2007-03-18
> **christhemonkey said:**
> See this howto:
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

or this one:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Thanks, I should have looked myself.
But do you think I'll be able to install Windows before that on the NTFS partition, without harming other partitions? Or will it be fine now, when I just choose the right partition from the menu?

---

### Post by christhemonkey on 2007-03-18
I think (you should probs back up before u go further) that you should be fine now just installing onto the NTFS.
You might want a 2nd opinion though.

---

### Post by 1002285 on 2007-03-18
> **christhemonkey said:**
> I think (you should probs back up before u go further) that you should be fine now just installing onto the NTFS.
You might want a 2nd opinion though.

Thank you, one of the instructions worked, too.
(Though the XP install didn't work at all - it was not able to get internet connections to work. May-be it was a very old version of Windows.)

---

