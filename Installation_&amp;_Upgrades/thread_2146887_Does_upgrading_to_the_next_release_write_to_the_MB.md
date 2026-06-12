---
title: "Does upgrading to the next release write to the MBR?"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by bluesloth on 2013-05-20
I have Ubuntu 11.10 and Debian.  Debian is what I use every day, and is what the GRUB 2 installation on the Master Boot Record points to.

If I upgrade Ubuntu to 12.04, will it overwrite the MBR with it's own GRUB?  In other words, will it run grub-install without asking me?

If it does, it should find Debian, so I can still boot into Debian and run grub-install to get things back the way they were.  But there's several opportunities for things to go wrong there, and anything with the potential to cause GRUB problems makes me nervous.

Maybe I'm being paranoid (I tend to do that sometimes), but I want some reassurance that my MBR will be untouched.

---

### Post by Irihapeti on 2013-05-20
Nothing wrong with being cautious when it comes to upgrading!

If you upgrade from 11.10, you shouldn't be asked to install grub at all. (But do a backup first, because too many people have got into a mess when upgrading.)

If you do a clean install of 12.04, you have the option of not installing grub. It's been a while since I last did a 12.04 install, but I installed it without installing grub on a number of occasions. Doing partitioning manually is more reliable, I think.

If the worst comes to the worst, and assuming that your Debian install hasn't been damaged, you can chroot into your Debian install, either from a liveCD or Ubuntu on the HD, and run grub-install that way.

---

### Post by grahammechanical on 2013-05-20
I have done many installs of different versions of Ubuntu. At the moment I have several versions installed. I have noticed that the last Ubuntu installed will install its version of Grub into the MBR with its Ubuntu at the top of the list. Unless we tell the installation to do things differently.

I have also notice that when a kernel is updated the MBR is sometimes written to and the boot order is again changed. You may find that once you upgrade to 12.04 you will get newer Linux kernels and the Grub configuration files are re-written. You may find that Ubuntu is  at the top of the Grub menu and Ubuntu is in change of the MBR. The simple solution is to boot into Debian and run

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

The first command will run the utility for updating the Grub configuration files. You will see all the operating systems found being listed. The second command puts this new information into the MBR of the first hard disk (sda). Assuming that you have both Debian and Ubuntu on the one and only hard disk. Change the sd bit if you have Debian on another hard disk.

What colour is the Grub background in Debian? In Ubuntu it is purple. So, you will always know when Ubuntu has taken control of the MBR. I use this method to keep a selected installation of Ubuntu in control of the MBR to avoid confusion because I have more than one Ubuntu installed.

Regards.

---

### Post by bluesloth on 2013-05-21
> **grahammechanical said:**
> I have also notice that when a kernel is updated the MBR is sometimes written to
Eep!  I wonder why it only does it sometimes.  And why it does it at all.

Anyway, you've inspired me to do more googling, and it turns out people are also complaining about Ubuntu writing to the MBR when GRUB is updated.  So, there're several reasons it might do it, therefore I can't expect it not to.

I did come across another idea:  I could let Ubuntu install it's own GRUB on it's partition's boot sector, and chainload it.  Then I wouldn't have to run update-grub in Debian everytime Ubuntu upgraded it's kernel, and Ubuntu could take care of it's own boot options and stuff.  And *hopefully* when I tell it to install GRUB in sda1 instead of sda, it will store that choice in a config file somewhere, and refer to it during kernel and GRUB updates, and not write to the MBR.  Now I just need to figure out what can go wrong with that procedure, and how to make it as un-scary as possible.  I know GRUB likes to warn people that doing that sort of thing is unreliable :(

> **grahammechanical said:**
> What colour is the Grub background in Debian?
Light blue. :)

---

### Post by Irihapeti on 2013-05-21
In my experience, it's not a kernel upgrade that may prompt writing to the mbr. It happens when grub itself is upgraded, which might coincide with a kernel upgrade. You should get a menu asking you what to do about it. i.e. which drive or partition, or not to do anything at all. I often have more than one install on a machine, and in those cases I'll tell one of the installs not to write to anything.

I was involved in testing for 12.04 before it was released, and I remember now that I did on one occasion have grub write to the wrong drive (bug was reported).

To avoid that, you can use the alternate install disk, which is much less automated than the live CD. I think the mini iso is similarly not automated, but it's been a while since I used it.

---

