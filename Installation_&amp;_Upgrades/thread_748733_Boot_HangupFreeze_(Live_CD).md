---
title: "Boot Hangup/Freeze (Live CD)"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by cferrell on 2008-04-07
Ok, im very new to Linux, ive been toying around with various distro's live cd's for the past week and want to install Ubuntu. It worked fine last night until I started looking for free ways to resize my partition, as I dont want to pay $ for a commercial application. Needless to say, I tried several demos but none would actually let me do it. I installed one, Acronis, and since then I haven't been able to get my live cds to work. It installed Acronis' OS Selector, which I think is where the problem lies. I've gotten rid of it, and downloaded a small application (fixmbr.exe) to execute that command, as I don't have my windows xp cd with me. Technically, that should have done it from everything ive read, but im still having problems. When booting up Ubuntu, it freezes (and screws up the screen) during the loading screen... I can't get past that point. It must be a general linux problem, as no other distro will boot up either. At one point I got this error and wrote it down:

[B]VFS: Cannot open root device "<NULL>" or unknown-block(104,1)
Please append a correct "root=" boot option; here are the available partitions
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1)[/B]

Now, I know my way around computers, but im new to Linux and command lines, so i've read a little into the problem but am having a difficult time deciphering where to go/ what to do.

Here's my computer:
Intel Pentium D 3.00 ghz
Intel 82801G
1g ram
Realtek Audio
Nvidia geForce 5500 256mb PCI
C: 200gb Maxtor Drive
E: Optiarc DVD RW AD-7170A

---

### Post by Partyboi2 on 2008-04-07
try using noapic as a boot option and see what happens. To do this when you are at the Ubuntu main menu screen press F6 and add ```
noapic
``` to the end of the line then enter to boot.  Also [Gparted]("http://gparted.sourceforge.net/") is a free program that will allow you to resize partitions. When you have ubuntu up and running again you can install it by synaptic package manager or from terminal (Applications>Accessories>Terminal)
```
sudo apt-get install gparted
```

---

### Post by cferrell on 2008-04-07
Still not working. From what i've read its a matter of the root partition not being specified during the boot phase, but how do I fix this? I've read a little bit and tried a couple of things, like adding on **root=/dev/sda1** and **root=/dev/hda1**... The "NULL" is the key part, reporting that there is no root partition. Whats up with this, the live cd worked last night until this partition junk screwed with my bootup, and I desperately want to get this working. Thanks for the heads up on gparted though, I hope it works if I can get this going.

---

