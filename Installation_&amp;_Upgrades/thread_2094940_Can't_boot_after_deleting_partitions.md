---
title: "Can't boot after deleting partitions"
date: 2012-12-15
forum: Installation &amp; Upgrades
---

### Post by nafihsus on 2012-12-15
:mad: I made a severe mistake by deleting the partitions used by Ubuntu from within Win7, merging them to one and assigning them a new volume letter for Windows, thereby also deleting Grub. Now the system doesn't boot any more and runs into grub rescue mode. When booting 'set' returns

prefix=(hd0,msdos7)/boot/grub
root=hd0, msdos7

which don't exist any more. 'ls' returns
(hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1).

Is there a chance I get to boot Windows (which shouldn't be affected at all) and thereafter fix grub?:mad:

---

### Post by Cheesemill on 2012-12-15
If you boot from your Windows installation CD it will let you repair the Windows boot loader.

It's unlikely you will be able to recover your Ubuntu installation though.

---

### Post by nafihsus on 2012-12-15
I only have a Windows recovery CD which I fear will reinstall Windows. Can I recover grub from a Ubuntu CD?

I deleted linux on purpose because I wanted to reinstall it on a different partition once I have freed up sufficient space on the windows partition by moving all data to the now deleted one.

---

### Post by ibjsb4 on 2012-12-15
Once you reinstall Ubuntu that will also reinstall grub and your system should boot again.

---

### Post by Mark Phelps on 2012-12-15
When you get back booting, go into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  With this, next time, you will have a CD that you can use to repair the Windows boot loader -- so you won't have to worry about using your Restore CD.

---

### Post by darkod on 2012-12-15
You don't need to restore grub, it can't work without the ubuntu partition. What you need is to restore windows bootloader.

You can do that from the ubuntu cd in live mode. Just run in terminal:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

That should install a generic MBR which can boot windows. The first command will print out some warning about the lilo configuration, just ignore it and continue. After that windows should boot as normal, until you decide to install ubuntu again.

PS. There is also a way to boot windows from the grub rescue prompt, make the repair cd and then use that to repair the windows bootloader. But the above solution is quite fast and is working. If you decide to boot windows once to make the rescue cd, boot the ubuntu cd in live mode and post the output of:
```
sudo parted -l
```

---

### Post by nafihsus on 2012-12-15
Solved. Thank you darko - the option with the Live CD worked fine. 
First thing I'll do now is creating a rescue CD for Win. 

Good to have this community.

---

### Post by ibjsb4 on 2012-12-15
And don't forget  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by offgridguy on 2012-12-15
Lots of good info in this thread, a keeper.

---

