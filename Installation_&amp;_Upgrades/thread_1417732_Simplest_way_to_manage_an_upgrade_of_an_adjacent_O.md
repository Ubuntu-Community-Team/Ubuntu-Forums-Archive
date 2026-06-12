---
title: "Simplest way to manage an upgrade of an adjacent OS"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by EMR on 2010-02-27
I've been dual booting Ubuntu and Windows for about a year now.  I know that Windows is nasty and all, but game publishers haven't gotten the memo, and Windows 7 isn't *that* bad.  How do I know?  I've been using the trial.  Except that runs out tomorrow, so I'm going to have to install the full version.  Which leads to the problem:

If I install it onto the partition where I had the old install, will grub find it?  Will it roach my Ubuntu partition?

If that won't work, it leads to a second problem: The Internet connection on that PC is so awful (for reasons that I'd rather not get involved in here), that I'd rather not, if I have to re-install Ubuntu, download all of the packages I have installed again.  Is there a reliable way to back up (and, more importantly, restore) all of the libraries and programs?

Finally, if neither of those options are possible, is there a way to select the packages directly, and download them with a well-connected PC?

---

### Post by slakkie on 2010-02-27
> **EMR said:**
> I've been dual booting Ubuntu and Windows for about a year now.  I know that Windows is nasty and all, but game publishers haven't gotten the memo, and Windows 7 isn't *that* bad.  How do I know?  I've been using the trial.  Except that runs out tomorrow, so I'm going to have to install the full version.  Which leads to the problem:

If I install it onto the partition where I had the old install, will grub find it?  Will it roach my Ubuntu partition?


Windows will rewrite the MBR (on installation, not sure about upgrades), so you will lose the ability to boot into Ubuntu. If you have a liveCD you can restore your grub by chrooting and installing grub again in the MBR and update it, so the os-prober will see your windows partition. From there you should be good to go.

Howto's:
[Grub]("http://ubuntuforums.org/showthread.php?t=224351") for release prior to 9.10 (karmic) and [Grub 2]("https://wiki.ubuntu.com/Grub2#Recover Grub 2 via LiveCD") for karmic and later.

You could use [Clonezilla]("http://clonezilla.org") to make a copy of your disks/partitions before you do this. Just in case things go bad.

> 
If that won't work, it leads to a second problem: The Internet connection on that PC is so awful (for reasons that I'd rather not get involved in here), that I'd rather not, if I have to re-install Ubuntu, download all of the packages I have installed again.  Is there a reliable way to back up (and, more importantly, restore) all of the libraries and programs?


```

# Get the list of packages:
dpkg --get-selections > package.list

# To install them on a new system
sudo dpkg --set-selections < package.list
sudo apt-get dselect-upgrade

```

---

### Post by oldfred on 2010-02-27
You should not have a problem, windows does not even see ext3/4 partitions. It will overwrite grub in the MBR and does not even give you a choice.  Make sure you have a liveCD with the correct version of grub.

slakkie's listing of packages still requires you to download them again.

Offline update
see also aptonCD
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by EMR on 2010-02-27
I'm pretty sure the machine is running hardy, so I'll look at that tutorial.

Basically, it'll overwrite the boot sector of the disc, and I'll have to re-install grub from the live CD if I want to get at my Ubuntu partition, correct?

Now about the packages, I must have not made the problem clear-I'd want to download them on the well-connected (this) machine, burn them to a disc, and move them (via sneakernet) to the other machine (not install them).  What would be the option to download only (I'm not a master of command-line apt-get, but I'm fairly sure that there is a way to do this).

---

### Post by slakkie on 2010-02-28
You can do this waith aptoncd (never used it), but you can use the package list to download all of your packages:

```
sudo aptitude --download-only install $(awk '{print $1}' packages.list)
```, which will download the packages and put them in /var/cache/apt/archives. You then need copy this directory to the other machine, and run dpkg --set-selection, apt-get dselect-upgrade and you should be good to go.

Hardy has grub-legacy, so any livecd from hardy onwards should be ok.

---

### Post by EMR on 2010-02-28
Okay, I get the tutorial, and most of the responses.  Thank you for your quick and useful information.  I'm a little edgy about actually doing the upgrade, and still have a couple of questions left.

First, how do I know what the partitions are named, so that when I'm installing windows, I don't accidentally overwrite the wrong partition.  Second, The tutorial's use of ? vs 0 is a bit confusing, is the following correct?

Boot from the Hardy cd, open up a terminal
(bold being what one must actually type)

$      **sudo grub**
(opens grub prompt)
grub>  **find /boot/grub/stage1**
(returns two integers, *a* and *b*)
grub>  **root (hd*a*, *b*)**
grub>  **setub (hd*a*)**
grub>  **quit**
(re-start and grub will be good as new, allowing for friendly dual-booting)

Right?  Again, thank you very much for the free support-I hope some day I can return the favor to some other newbies, once I get better at this...

---

### Post by EMR on 2010-03-01
Seems to have worked exactly as it was supposed to, thank you very much!

---

