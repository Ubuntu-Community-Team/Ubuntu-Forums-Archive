---
title: "How do I rescue a messed up installation"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2007-01-10
I am having to access the forum through Windows (yuck) because my Edgy system is corrupted and I can no longer load Firefox.  I tried to repair my install with the installation cd but no luck.  It just tries to install a whole new system.  The documentation says something about typing rescue at the boot prompt, but is not very clear.  When and where does the boot prompt occur?  I tried typing "c" when I got to the Grub page but the commands rescue and rescue mode are not valid.  How exactly do I get my system up and running again without wiping out my whole hard drive?

Bob

---

### Post by meng on 2007-01-10
When you say it is corrupted, can you explain in more detail? Did you notice any other problems besides being unable to load Firefox? Do you have any idea what might have caused this or contributed to it? Had you been messing around with important configuration files?

---

### Post by Baasha on 2007-01-11
Yes, I probably messed it up myself.  I was having a problem with Firefox.  The Firefox Help>About Mozilla Firefox said I had vs 1.5.0.4 installed, but Synaptic said I had vs 2.0.0.1 installed.  I backed up my profile then tried to reinstall with Synaptic.  That didn't work so I went back to Synaptic and did a complete removal including configuration files.  Still no luck, no matter what I did I could not get a 2.0.0.1 version running.

As a last resort I did a "whereis Firefox" in the terminal and then proceeded to manually erase every Firefox file I could find.  Then I reinstalled Firefox from Synaptic.  When I tried to start Firefox it complained about missing configuration files and it wouldn't load.

Is this something I can fix, or would I be better off erasing my hard drive and starting all over?

Bob

---

### Post by meng on 2007-01-11
Are you running Dapper? This site explains how to get Firefox 2 running in Dapper.
[www.psychocats.net/ubuntu](www.psychocats.net/ubuntu)

---

### Post by Baasha on 2007-01-11
No, I am not running Dapper.  I upgraded from Dapper to Edgy by running the iso disc and selecting the upgrade option.

Is it possible the upgrade went wrong?  What is the vs # for Edgy?  I will compare that with what comes up in the Grub menu.

Bob

---

### Post by meng on 2007-01-11
Edgy is 6.10. I suppose anything is possible with an upgrade. Have you got a separate /home partition?
[www.psychocats.net/ubuntu/separatehome](www.psychocats.net/ubuntu/separatehome)
If you have a separate /home partition, your data will be saved if you do a fresh install.

---

### Post by Baasha on 2007-01-11
Thanks Meng,
As far as I can remember I did set up a seperate home partition, so I think I will risk doing a completely fresh install.  Are any other partitions wiped out when doing this?  I set up a seperate Fat32 partition to store my files from Windows so that I could read and write from either operating system.  My actual Windows installation is on another hard drive, but the Fat32 partition is on the same drive as the Ubuntu OS.

Bob

---

### Post by Sef on 2007-01-11
> As far as I can remember I did set up a seperate home partition, so I think I will risk doing a completely fresh install. 

Best to make sure you do have  a separate home partition.  In any case, **back up** your data first.a  There are no 100% guarantees that all will go well.


> Are any other partitions wiped out when doing this?

Swap is also reinstalled.

---

