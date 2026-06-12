---
title: "Problems accessing windows partition..."
date: 2005-03-21
forum: Installation &amp; Upgrades
---

### Post by Sabator on 2005-03-21
I regret not doing my reseacrh, to be honest. A friend of mine assured me I'd be able to access my windows partition. Y'see, he wanted me to switch to Linux soon (He recommended Debian, which was very hard to use, afterwards he changed his mind and said Ubuntu was a more user-friendly platform) but my DVD writer was broken. I set it up as a dual boot system, but whenever I select windows XP at startup, it says something about autocheck failing and reboots. I've tried mounting the partion with limited success.

mnt -t ntfs hda2 /mnt/

It says the device does not exist, which I know it does.

How on Earth do I create a dual-boot system, then? I created a Linux partition, and a swap partition, with Partition magic, I installed Debian, a day later I formatted the Linux partition and installed Ubuntu. Someone told me something about Windows XP not working if it wasn't the first OS on disk, which is true, the boot screen lists my two Linux partitions before the two XP partitions. Apparently, I should install Windows after Linux. But, I don't have a Windows XP install disc. Stupid Compaq equipped this computer with "System recovery", which erases the entire disk and installs Windows.

Right now, the data on my windows partition isn't hugely important. What is important, is that I get a dual-boot system up and running.

So, any ideas? :D

---

### Post by bored2k on 2005-03-21
[QUOTE=Sabator]I regret not doing my reseacrh, to be honest. A friend of mine assured me I'd be able to access my windows partition. Y'see, he wanted me to switch to Linux soon (He recommended Debian, which was very hard to use, afterwards he changed his mind and said Ubuntu was a more user-friendly platform) but my DVD writer was broken. I set it up as a dual boot system, but whenever I select windows XP at startup, it says something about autocheck failing and reboots. I've tried mounting the partion with limited success.

mnt -t ntfs hda2 /mnt/

It says the device does not exist, which I know it does.

How on Earth do I create a dual-boot system, then? I created a Linux partition, and a swap partition, with Partition magic, I installed Debian, a day later I formatted the Linux partition and installed Ubuntu. Someone told me something about Windows XP not working if it wasn't the first OS on disk, which is true, the boot screen lists my two Linux partitions before the two XP partitions. Apparently, I should install Windows after Linux. But, I don't have a Windows XP install disc. Stupid Compaq equipped this computer with "System recovery", which erases the entire disk and installs Windows.

Right now, the data on my windows partition isn't hugely important. What is important, is that I get a dual-boot system up and running.

So, any ideas? :D[/QUOTE]
 [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

Welcome to the forums btw .

---

### Post by Sabator on 2005-03-21
I love you.

Have my children.

---

### Post by bored2k on 2005-03-21
[QUOTE=Sabator]I love you.

Have my children.[/QUOTE]
 O_o *shocked* .. Buffering .. [A]bort [R]etry [F]ail .. **F**

---

