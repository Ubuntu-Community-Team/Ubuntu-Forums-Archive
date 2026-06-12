---
title: "Grub has lost the Ubuntu line after Ubuntu14.04 update"
date: 2014-12-23
forum: Installation &amp; Upgrades
---

### Post by aqk on 2014-12-23
I'm running a system with  Ubuntu 14.04 and Windows 8. (both 64-bit)
The latest Ubuntu update somehow stalled, necessitating me to cancel it.

 Now, when I reboot, the Grub menu only shows the following lines:
[B]Memory test
Memory test (serial console...etc)
Windows 8 loader[/B]

So I can boot into Windows 8 satisfactorily, but I am no longer able to boot into the Ubuntu system
A "c" will give me a  GRUB> command line, but I am totally inexperienced with this.
Grub>HELP will give me a plethora of commands of which only the last page can be seen! 

Is there any Grub> command that I can use to recreate the Grub config as per the update-grub command in Ubuntu?
Or should I DL and burn some "supergrub" boot disk?

---

### Post by carl4926 on 2014-12-23
Cancelling a distribution upgrade is probably one of the worst moves you can make.
Assuming you had already made a suitable backup (standard procedure)
You could just install clean
OR
Possibly using a DVD of 14.04, you might be able to chroot the Ubuntu system. But it's a bit of an unknown, because chroot necessitates using the same system as is installed IIRC. So it may be that 14.04 isn't actually installed but rather, what you were using previously 12.04?
Once chroot, you can usually run synaptic and fix it all

---

### Post by aqk on 2014-12-23
> **carl4926 said:**
> Cancelling a distribution upgrade is probably one of the worst moves you can make.
 l 

**Upgrade?**  No, I was just doing the ***weekly update*** to 14.04.
And after updating about 30-40% it sat there for two hours whilst updating one program. So I finally cancelled the update.
I've frequently done this when an update download stalls (usually due to loss of internet).
It usually corrects itself when I re-do the update next time.
Now, there *IS* no "next time", unless I fix the Grub config...

---

### Post by Bashing-om on 2014-12-23
aqk; Hello;

Might try and (RE-)install grub from the liveDVD(USB) ?
Check what partition 'root' is installed to:
from the liveDVD:
```

sudo fdisk -lu

```
check that kernels are intalled and boot files are in place:
from the liveDVD, mount the partition and have a look:
```

sudo mkdir /mnt/look
sudo mount /dev/sda1 /mnt/look
ls -al /mnt/look/boot
ls -al /mnt/look/boot/grub/grub.cfg
sudo umount /mnt/look

```
Here it is 'sda1' that holds 'root'.

If all looks good, then (re-)install grub:
```

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt

```
Again, "assuming" sda1 holds the root file system, that sda holds ubuntu, that there is no separate /boot partition.

Reboot into the install to a terminal, and run:
```

sudo update-grub

```

[INDENT][INDENT]how now brown cow ?
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-12-23
If an update did not finish then it did not download new kernels and run th update to initrd. Without those you have nothing to boot. I would have thought it would have had at least one older kernel to still boot with.

You probably have to chroot into system and install newest kernel as part of update. 
With Boot-Repair's advanced repairs, it walks you thru a chroot and a full uninstall/reinstlal of grub. That may include adding a new kernel or you need to include adding a kernel. And you may need extra commands to clear whatever issue it was having.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Manual chroot:
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Include these commands, if manually chrooted. With chroot sudo not required, if you get errors with any command, you must resolve those before continuing.

 #Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

   sudo update-initramfs -k all -c
sudo update-grub

---

### Post by aqk on 2015-01-01
Thanx for the above help and suggestions.
But I decided to find out a bit about GRUB and so solved my problem by booting into Ubuntu using the 
following GRUB commands in a terminal session
  1. Keep term from displaying more than a page at a time:
[SIZE=3]**[COLOR=#0000cd]grub>[/COLOR][COLOR=#B22222] set pager=1[/COLOR]**[/SIZE]
  2. List all the partitions that GRUB sees:
[SIZE=3][COLOR=#0000cd]**grub>**[/COLOR][/SIZE][COLOR=#B22222]** ls**[/COLOR]
    3. Use the ls command to see what files are on the system:
**[SIZE=3][COLOR=#0000cd]grub>[/COLOR][/SIZE][COLOR=#B22222] ls (hd0,1)/[/COLOR]**
      4.  ran these commands, using the own root partition, kernel, and initrd image:
[B][COLOR=#0000cd][SIZE=3]grub>[/SIZE][/COLOR][COLOR=#B22222] set root=(hd0,1)
[/COLOR][SIZE=3][COLOR=#0000cd]grub> [/COLOR][/SIZE][COLOR=#B22222]linux /boot/vmlinuz-3.13.0-43-generic root=/dev/sda1   ### -43- is the latest that I have (Dec/2014)
[/COLOR][COLOR=#0000cd][SIZE=3]grub> [/SIZE][/COLOR][COLOR=#B22222]initrd /boot/initrd.img-3.13.0-43-generic
[/COLOR][COLOR=#0000cd][SIZE=3]grub> [/SIZE][/COLOR][COLOR=#B22222]boot[/COLOR][/B]
...  this booted my Ubuntu satisforily.
   From there I issued  the update-grub    etc as above..
My GRUB now shows  both  Ubuntu 14.4  and  Windows-8 in its menu, and I can boot from either.
**[SIZE=5]BUT![/SIZE]**
 I now have a problem with EFI: 
[B][I][COLOR=#ff0000]Setting up refind (0.8.4-0ppa2) ...
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.   [/COLOR][/I][/B]
 etc etc  
 THIS THREAD CAN BE CLOSED-  THE **EFI PROBLEM WILL BE ISSUED AS A NEW THREAD**

---

### Post by Bashing-om on 2015-01-01
aqk; Great ;

Pleased ya up and running - 
It is an odyssey  in learning, indeed. How does this system boot ?

Thanks for providing your solution and guidance.
As only you can say when a matter is satisfactorily concluded, you are responsible to 'mark' a thread solved.
Marking a thread 'solved' ;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.

1st post -> thread tools -
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThread](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThread)

[INDENT]3 steps forward and only 1 back
[INDENT][INDENT][INDENT][INDENT]look'n good
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

