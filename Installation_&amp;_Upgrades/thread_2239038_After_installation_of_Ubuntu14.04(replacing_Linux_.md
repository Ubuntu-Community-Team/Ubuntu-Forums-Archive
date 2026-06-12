---
title: "After installation of Ubuntu14.04(replacing Linux Mint 17)can't see Windows 8 on GRUB"
date: 2014-08-11
forum: Installation &amp; Upgrades
---

### Post by g.voumvoulaki on 2014-08-11
Greetings everyone,

I have a laptop with Windows 8.1 preinstalled on which I installed Linux Mint 17-cinnamon x64 alongside Windows on a new partition I created.
Dual booting worked fine. Because I didn't really like it I decided to try Ubuntu 14.04. I boot it from a live CD and when I got  onto installing it, I selected the option"Replace Linux Mint 17".

After successful installation I stopped seeing GRUB on boot. I looked around on the forum and installed boot-repair following the instructions and selecting "Recommended Repair". Now GRUB does appear on startup but I still don't see Windows as an option.(boot-info report: [http://paste.ubuntu.com/8019660/](http://paste.ubuntu.com/8019660/) )

Any idea how to fix that?Is there a chance I deleted windows when I installed ubuntu?I dont see how that could be though since I had Linux Mint on a different partition so I thought when I chose "Replace Linux Mint"Ubuntu would be installed on that partition..

Any help would be greatly appreciated!

Thanks in advance.

---

### Post by ajgreeny on 2014-08-11
I fear you managed to find what I think is a bug in the installer if you choose to do what you did to replace an existing Linux OS.

You have indeed removed Windows completely when reinstalling the Linux OS.  The only truly safe way to do that is to choose the **Something Else** option at partitioning stage, and replace each specific partition one at a time.

I am sure you will be annoyed at the least, and possibly devastated to hear that, and apart from suggesting that you stop using your hard disk, and now run a live system with testdisk and hope that you can recover your old partitons, I can not really help you further.

Reinstalling Ubuntu is a very quick operation, but I have no idea about Windows 8.1, and if you did not make the restore DVDs you may have difficulty in any case.

I am sorry if this is the last thing you wished to hear, but I wish you very good luck in restoring the machine to what you want.

---

### Post by nerdtron on 2014-08-11
It's not a bug. I'd rather call it "Replace the Current Operating System".

Whatever you call it, choosing that option ("Replace Linux Mint 17") will format the selected hard drive and reinstall Ubuntu. It's just the way the installer works and it's very misleading especially to new users.
If I where you, I'll start to learn using the "**Something Else**' when you install Ubuntu. You'll learn how to repartition your drives there just like how you partition when installing windows. This is the safest way to install Ubuntu on a particular partition so that other OSes will be unharmed.

---

### Post by kansasnoob on 2014-08-11
> **nerdtron said:**
> **[COLOR="#FF0000"]It's not a bug[/COLOR]**. I'd rather call it "Replace the Current Operating System".

Whatever you call it, choosing that option ("Replace Linux Mint 17") will format the selected hard drive and reinstall Ubuntu. It's just the way the installer works and it's very misleading especially to new users.
If I where you, I'll start to learn using the "**Something Else**' when you install Ubuntu. You'll learn how to repartition your drives there just like how you partition when installing windows. This is the safest way to install Ubuntu on a particular partition so that other OSes will be unharmed.

It certainly is a bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by nerdtron on 2014-08-11
Oh there's a bug report to it. So it really is a bug. I thought it was designed to do that in the first place.
I have never used that option before (one time VM test machine only), I just assumed that it will replace all operating systems on the hard drive (I have trust issues on these automated installers). I always use "Something Else" aka manual partitioning whenever I reinstall a Linux OS.

---

