---
title: "ThinkPad T30 - Hidden partition"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by mantu on 2007-04-23
Hi,
I have a ThinkPad T30 with Windows XP and I'd like to install Ubuntu 7.04 in dual-boot. The 40 GB hard disk has currently the following partitions:

/dev/hda (37,26 GiB)

--> /dev/hda1 ntfs 35.58 (boot)
--> /dev/hda2 fat32 1,68 (hidden, lba)

hda2 is the IBM hidden partition needed to restore the laptop to factory state. In fact I don't need this hidden partition for IBM sent me the recovery CDs some years ago by mail. So at the moment I have the following dilemmas:

When installing Ubuntu can I safely delete the hidden partition?

If I choice to keep the hidden partition, will I be really able to use the hidden partition to restore the system after installing Ubuntu? In other words in the boot menu will I have an option to start the factory recovery program?

Thanks
Mantu

---

### Post by sdyson on 2007-04-23
I've just installed Kubuntu Feisty on on Thinkpad R60 which also has a hidden recovery partition. I opted to keep the partition since it was only using about 5 gig on a 100 gig hard drive. To be on the safe side I also created some recovery CDs so it's unlikely I'll ever need the recovery partition. I would say keep it if you think you'll still have plenty of space on the harddrive. I found some useful information about installing Linux on a Thinkpad at [http://www.thinkwiki.org]("http://www.thinkwiki.org"). In particular there is information about recovering the preloaded OS at [http://www.thinkwiki.org/wiki/How_to_recover_the_preloaded_OS]("http://www.thinkwiki.org/wiki/How_to_recover_the_preloaded_OS")

---

### Post by Judicata on 2007-04-23
FWIW, when I installed Ubuntu on my T41 last year I just axed the hidden partition - but I wasn't dual.  This is just to say that deleting it doesn't break anything (except factory restore from the HD, of course).

---

### Post by mpvano on 2007-04-23
I'm having some power management crashes/resume failures , wireless problems (need to blacklist 2 of the three sets of drivers loaded incorrectly) and a few other problems on my T30, so I'd wait until the first round of updates if I were you.

I was cautious enough to do my feisty testing on a separate, new, ata drive I swapped into the internal drive slot, so I haven't yet installed 7.04 to coexist with XP, but see no reason why the procedure I've always used shouldn't work for 7.04 when I'm ready. The usual drive for this machine has 6.06 installed that way, and all the original partitions still exist and work fine (but of course, I had to reduce the size of the XP partition).

The procedure varies too much to give you step-by step instructions, but here's a rough explanation of what you need to figure out how to do.

1. Don't mess around with things like this unless you are confident you can restore things in case you screw up (or don't care if you lose the original partitions).

2. Use an installer that does NOT automatically install the boot loader into the MBR (master boot record) at the end of the installation. For Ubuntu, this usually means you MUST use the alternate install disk, which prompts you about where to install GRUB.

3. Don't delete any partitions during the install - you'll need to manually do the partitioning and the details will depend on your disk size and exact version of the computer. You'll need to resize the XP partition to make it smaller to make room for the install.

4. Create two partitions - one for the ubuntu root and another for the swap space. The root partition needs to be a PRIMARY partition (#1-#4). If #1-4 are already used, you can't do this. Usually only two PRIMARY partitions have been used up by XP, so this is not a problem. You can put the swap space into an extended partition if you need to.

5. At the end of the install, you need to specify that grub be installed to the root PARTITION, not to the disk drive itself. E.G. this means that if you installed to partition 3 on the first ide drive you want GRUB installed to /dev/hda3 (or /dev/sda3 in the case of feisty).. DON'T use the default (which will install grub to /dev/hda or /dev/sda).

If all goes well and you don't screw up, your machine should boot fine, and if you enter (or permanently enable) the grub boot menu, it should have entries for everything including the IBM recovery system, and selecting them should work.

At any later time, resetting the "boot flag" with fdisk or another disk utility (even from another OS) will restore the original boot-up behaviour and ignore grub until you reset the "boot" flag for the partition to which you installed grub.

I usually enable the option in grub that remembers the last boot selection, since this makes updating XP easier (it usually does several automatic reboots, and navigating the grub menu for each one gets boring after a while). The rest of the time, the last OS you booted is usually the one you want to boot again...

Again, DON'T try this yourself unless you know what you are doing, and I can't provide tech support to you if you screw this up, but it should work fine on most systems, since this is the way the IBM PC boot system was designed to keep the peace between competing operating systems....

The only problem I've ever encountered is when a new version of linux suddenly decides that you don't need to get the option to decide where to install GRUB! (They ALL used to do this - if you're not sure, make sure you ask someone first who's run the installer in question!). If there's any doubt at all, find a utility (or instructions using dd) that will let you back up your MBR before trying this.

Mario

---

### Post by mantu on 2007-04-23
Hi, thanks for your replies :) 
let's say I don't need the hidden partition and I delete it during the install process. Let's say I chose to use the standard Ubuntu CD that automatically install GRUB into the MBR at the end of the process. Is really necessary, in this case, for the root partition to be a PRIMARY partition? Could I use only a Windows Primary partition and leave all other partitions as Logical (Ubuntu root included)?
Mantu

---

### Post by mpvano on 2007-04-23
I didn't mean to imply that you couldn't use more complicated partitioning schemes, only that my explanation (and desire to discuss this!) dealt with the simplest case....

In fact I have more partitions than I admitted to on my 6.06 system and several are secondary partitions. I like storing multimedia raw data on partitions I can clear completely for each project!

I believe that you probably want to install grub to a primary partition, however, and I'm always afraid to do that to the boot record of a partition belonging to another OS since someone else may already have decided to hide something proprietary there. Hence I recommend having at least ONE of your linux partitions be a primary so that you know it's safe to use.

(Actually, on one of my desktops, I've got grub installed to a tiny primary partition that's not even been formatted since it's too small for anything else - it references and boots to a second disk drive!)

Mario

---

### Post by mantu on 2007-04-23
Hi mpvano,
you suggest to T30 owners to wait until the first round of updates ships. I'm new to Ubuntu and I'd like to know if the patches you're speaking about will be included in (a new version) of the official 7.04 CD or the CD will remain the same and the patches will be shipped apart via online updates.
Mantu

---

### Post by mpvano on 2007-04-23
Whoa!

I'm just like you, a user with no inside info!

I just happen to have a few more resources and tried a clean install on a spare disk driv before committing to it permanently on the machine I'm typing on right now.

I'm just reporting what I found.

If you don't need your wireless working, and if you don't need to be able to suspend and resume reliably and if you don't need to use USB devices after resume, then feel free to go ahead and try it! By the way, there are other reports here of the USB problem with thinkpads on the Feisty release.

I stopped playing with it at this point because I didn't feel like wasting any more time. I'm ASSUMING someone will fix it and issue an update, but I have no idea if or when that will happen. Updates are almost NEVER rolled back into ubuntu release disks, however. I think the only time they do this is for the "LTS" edition and feisty is NOT an LTS edition.

waiting and watching like everyone else....

Mario

---

