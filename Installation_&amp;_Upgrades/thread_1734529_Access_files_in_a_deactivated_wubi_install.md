---
title: "Access files in a deactivated wubi install?"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by wlbragg on 2011-04-20
Deactivated is probably not the right word to use. I have a copy of a Wubi installed Ubuntu folder on a hard drive that is no longer tied into any boot loader. Is there a way to access the user files in that folder either directly through a helper application or, if not, then can a boot loader be configured to load that install? I'm looking for the easiest way to access user files in that folder, if possible, and then I'm done with it and will discard it. So unless reconfiguring to be able to boot is really simple I'd prefer to just access the files through a helper application if one even exists.

The Wubi install FOLDER was copied over from another computer that was originally a Duel boot XP/Wubi installed Ubuntu.

The current system I'm working with is Duel boot Ubuntu 10.10/Win7/XP. XP was installed first on F: with boot record on C: partition 1. Then Win 7 was installed on C: partition 1, creating duel boot 7/XP on partition 1. Then Ubuntu was installed on C: beside 7 on partition 2 creating a triple boot (so to speak) on C:. First boot loader (I think it is Ubuntu/Grub) allows Ubuntu or WIN7loader to be loaded. If WIN7loader is chosen then WIN7Loader comes up and allows Win7 or XP.
The copy of the Wubi installed Ubuntu folder is on F:

Any help greatly appreciated.

---

### Post by ~Plue on 2011-04-20
you can access it from the ubuntu install by running the following from a terminal
```
mkdir ~/wubi
sudo mount -o loop /path/to/root.disk ~/wubi
```that would mount the root.disk to a folder named 'wubi' in your home directory.
when you're done, run *sudo umount ~/wubi* to unmount it

to access it from windows, try [ext2read]("http://ext2read.blogspot.com/")

---

### Post by wlbragg on 2011-04-20
You are genius. I was just getting ready to post that I found the solution but you beat me to it. 

Thanks

---

