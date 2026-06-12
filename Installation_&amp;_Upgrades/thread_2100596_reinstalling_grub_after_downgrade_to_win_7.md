---
title: "reinstalling grub after downgrade to win 7"
date: 2013-01-02
forum: Installation &amp; Upgrades
---

### Post by aronwalker on 2013-01-02
NRELIABLE and their use is discouraged..
/usr/sbin/grub-bios-setup: error: will not proceed with blocklists.


How can I fix this? What are blocklists? Should I use Blocklists or is they another way round? 

Please help!

Aron

---

### Post by aronwalker on 2013-01-02
Ok half of my message got cut off

Hello

I have just downgraded from windows 8 to windows 7 (why downgrade - I hate "windows" 8 - why windows? Compatibility.) I tried to reinstall grub from a live usb using this [http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)
However, I got stuck on the last bit

It the error reads as follows

root@ubuntu:/# grub-install /dev/sda
/usr/sbin/grub-bios-setup: warning: disk isn't LDM.
/usr/sbin/grub-bios-setup: warning: Embedding is not possible. Grub can only be installed in this setup using blocklists. However, blocklists are UB

---

### Post by darkod on 2013-01-02
The chroot procedure is longer and not really needed in your case. But it should have worked. I guess you did something wrong.

Look here for a shorter procedure. Focus on Reinstalling grub for 9.10 and later.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You basically need just two commands instead of the chroot procedure. But make sure you know which one is your root partition from the fdisk results as explained there.

---

### Post by aronwalker on 2013-01-02
Tried this aswell - get the same error message - I have even called my friend who runs a small linux datacenter and he says he has never come across this before...

---

### Post by Hakunka-Matata on 2013-01-02
try this link, look at post #9

[https://bbs.archlinux.org/viewtopic.php?id=149772]("https://bbs.archlinux.org/viewtopic.php?id=149772")

---

### Post by darkod on 2013-01-02
It may or may not be the LDM issue. Another option is that you could be running the disk with a gpt table but turned it to msdos with the win7 install.

Grub2 needs a small bios_grub partition in order to install on gpt disks.

Depending how was win8 installed (legacy or uefi), and how exactly you downgraded to win7 (again, legacy or uefi), issues might pop up.

It might be time to run the boot info script from my signature, or run boot-repair to create the bootinfo (they both do the same).
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Post the results.txt that the script created or post the link boot-repair provided, so we can see more details.

I hope you are not running Dynamic Disks in windows because that might give issues with the dual boot. I'm not sure about that.

---

### Post by aronwalker on 2013-01-02
Got it fixed now - did the arch linux get arround and then grub-install. Thanks everyone for helping!

Aron

---

### Post by PePas on 2013-02-04
> **aronwalker said:**
> did the arch linux get arround and then grub-install.

I think I have the same problem. What is the "arch linux get around"??
What did your geub-install command line look like?

---

### Post by Hakunka-Matata on 2013-02-05
archlinux - see post# 5

---

### Post by aronwalker on 2013-02-09
[QUOTE=https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255/comments/26]
It is actually the backup copy at the end of the disk that appears to be the problem. Zeroing out the last sector of the disk should fix it. To do this, you want to follow steps similar to this:
sudo fdisk -lu /dev/sda
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Note the sector count. Subtract one and that leaves 488397167, which you can then use with dd to dump that sector:
sudo dd if=/dev/sda bs=512 count=1 skip=488397167 | hd
At this point you should see somewhere on the screen the string "PRIVHEAD". If you do, that is the LDM label sector. You can then zero it out with:
sudo dd if=/dev/zero of=/dev/sda bs=512 seek=488397167 count=1
It is vital that the command be executed correctly or you can trash your whole disk, so triple check your typing and math before hitting enter.[/QUOTE]
 
this is it - it seamed to work at first, but it is not the best way of doing it. If I was to do this again, then i would have backed up all of my data, and then installed windows on all of my hard-drive, and then got ubutnu to repartition my hard-drive so that it is 1/2 and 1/2

---

### Post by oldfred on 2013-02-09
Just be sure you do not still have dynamic partitions, but have basic partitions. Or you may damage your Windows partitions.

Grub/Ubuntu used to not even see nor work with any Windows in dynamic partitions. They seem to be upgrading to at least recognize the dynamic partitions but in doing so still see left over data at end of drive.

Windows tools do not houseclean well when you convert from dynamic to basic.

       Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

---

### Post by aronwalker on 2013-02-12
Another Update - after doing this i noticed my whole computer started to become really slow. I did a memory test and other tests and it turned out my hdd had an i/o error. If this is due to this or something else, I dont know. I ended up having to change my harddrive. If you do this and notice that your computer becomes really slow, it is probably because of this. I recomend that you backup your data, reinstall windows, and THEN install ubuntu.

---

