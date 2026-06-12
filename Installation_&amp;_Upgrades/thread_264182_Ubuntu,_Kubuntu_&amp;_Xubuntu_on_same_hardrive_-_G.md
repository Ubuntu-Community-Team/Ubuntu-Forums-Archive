---
title: "Ubuntu, Kubuntu &amp; Xubuntu on same hardrive - Grub problems"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by Psquared on 2006-09-24
Hda1 = Ubuntu
Hda2 = Xubuntu
Hda4 = Kubuntu

I actually installed Xubuntu last (i created the partitions first so I picked the wrong one - should be on Hda4)

Anyway, the grub file in Xubuntu is the operative one. When I am in Ubuntu or Kubuntu and upgrade the kernel it changes the grub entries for that partition, but does not change or update Grub in Xubuntu which is the one that is active during boot. I have to manually edit Grub by going into Xubuntu and mounting/copying the entries from Ubuntu and Kubuntu. The problem is that they are all called Ubuntu.

Anyone got any ideas how to fix this or is it a limitation of Grub? Surely others are running all three distros and have seen this problem.

---

### Post by zxee on 2006-09-24
With dapper (I'm assuming this is the desktop cd of dapper for all three installs) it's much better IMO to use the alternative cd because you can select where grub is installed. Anyway that's what I do-I don't have xubuntu installed but I do have three different versions of ubuntu on seperate partitions (plus other distros)
Yeah the last ubuntu you installed would be the operative one because each one changes the mbr.
You could chroot to the install you want to be the 'master" or operative one and do 'grub-setup'. You would have to mount that partition and use sudo in front of those commands. 
For my installs I just have grub install to the partition so it doesn't mess with the grub I'm using. Hope that's clear.

---

### Post by Psquared on 2006-09-24
> **zxee said:**
> With dapper (I'm assuming this is the desktop cd of dapper for all three installs) it's much better IMO to use the alternative cd because you can select where grub is installed. Anyway that's what I do-I don't have xubuntu installed but I do have three different versions of ubuntu on seperate partitions (plus other distros)
Yeah the last ubuntu you installed would be the operative one because each one changes the mbr.
You could chroot to the install you want to be the 'master" or operative one and do 'grub-setup'. You would have to mount that partition and use sudo in front of those commands. 
For my installs I just have grub install to the partition so it doesn't mess with the grub I'm using. Hope that's clear.

I see what you mean. I wish I had done that when I installed. I used the rescue disk and gparted to setup the partitions. Originally I only had Ubuntu, but I wanted to try them all, but I hate mixing QT and GTK libraries.

If I use the chroot would I do that from Hda1? Would that make my original Ubuntu install Grub the one on the MBR and would it get updated when I upgrade the Kubuntu or Xubuntu kernel?

---

### Post by aysiu on 2006-09-24
I don't think there's a solution to this unless you reinstall Grub every time. I don't think Grub is made to detect new kernel versions on other partitions.

Did you install them all on separate partitions because you just like them "clean"?

---

### Post by zxee on 2006-09-24
I guess I'll provide a little more info here:
If you wanted hda1 to be the install that boots by default and also the one that's menu.lst is used during boot then how I would do that is to create a directory 'sudo mkdir /mnt/hda1' then 'sudo mount /dev/hda1 /mnt/hda1'
next step; 'sudo chroot /mnt/hda1' then enter grub by 'grub' and do 'grub-setup'
That should work.
There is no way I know of to get grub to automatically update your kernel changes in the seperate installs.

---

### Post by Herman on 2006-09-24
> Hda1 = Ubuntu
Hda2 = Xubuntu
Hda4 = Kubuntu Hello everyone,
You will find that in most Linux systems, and definitely in Ubuntu, there are symlinks up in our root directories for ther kernel and initrd.img files. You can see that if you do 'ls /', for example,> bin    dev   initrd          lib    opt   sbin  tmp  vmlinuz
boot   etc   initrd.img      media  proc  srv   usr  vmlinuz.old
cdrom  home  initrd.img.old  mnt    root  sys   var Can you see them? The ones called vmlinux and initrd.img? Those are shortcuts that always point to the newest kernel and ramdisk. Also you might notice vmlinuz.old and initrd.img.old, I won't bore you...
Okay , so if you want, it is pretty simple to alter your entries in you menu.lst files to boot by the symlinks instead of directly booting the specific kernel and initrd.img 
So for example, here is you Grub menu boot entry for another system in your PC,
 ```
title        Ubuntu, kernel 2.6.15-25-386
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-25-386
savedefault
boot
```You just alter it to look like this, 
```
title        Ubuntu, other system's hostname
root        (hd0,1)
kernel        /vmlinuz root=/dev/hda2 ro quiet splash
initrd        /initrd.img
savedefault
boot
``` See? I simply deleted where it says '/boot', (because I don't need that filepath now), and also the specific kernel and initrd.img details (numbers). Now it will boot via the symlinks and always boot up with the most up to date kernel. 
Regards, Herman :D

---

### Post by Herman on 2006-09-24
Another type of Grub entry that you can also use for multiple boot installations is the 'configfile boot'.
That loads the other system's own menu.lst, which should probably always be up to date with the correct specific kernel and initrd.img file details for that system.
To edit you menu.lst for a configfile boot, you just edit your operating system entry from something like this,
```
title        Ubuntu, kernel 2.6.15-25-386
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-25-386
savedefault
boot
```to something more like this,
```
title        Ubuntu Edgy Eft
savedefault
configfile   (hd0,1)/boot/grub/menu.lst
```That's another way to multi boot. You can edit the other menu.lst to hide the menu and turn down the timer if you want to save time at each boot, or install a nice spashimage and take your time to enjoy it.
Regards, Herman :D

---

### Post by Herman on 2006-09-24
And thirdly, you can install Grub to the first sector of the partition and chainload your other Linux operating systems, similar to the way we chainload Windows,
```
title        Ubuntu Edgy Eft
root        (hd0,1)
savedefault
chainloader    +1
```Now you know three different ways to set Grub up for multiple booting Linux systems. Just choose the one that you think you will prefer, or try all three and see which one you like best.
Regards, Herman :D

---

### Post by Psquared on 2006-09-24
> **aysiu said:**
> I don't think there's a solution to this unless you reinstall Grub every time. I don't think Grub is made to detect new kernel versions on other partitions.

Did you install them all on separate partitions because you just like them "clean"?

Yes. In the past Xfce and Gnome would get mixed up and Nautilus would take over the desktop. I wanted clean installs of each version so I could test them in their native environment without any outside influence.

---

### Post by Psquared on 2006-09-24
Thanks Herman. For now, just editing the Grub currently on the MBR seems the most economical way in terms of time spent and efficiency. All I do is mount the other partitions and go to boot --> Grub ---> menu.lst, copy the entries and paste them in the Grub that is actually controlling the boot. Sometimes it takes me a little time to figure out if its for Ubuntu, Kubuntu or Xubuntu, but it seems to be working this way.

However, I am thinking of installing Edubuntu now so I may try one of your solutions.

---

### Post by Herman on 2006-09-25
> editing the Grub currently on the MBR Yes, that's exactly what I'm talking about. :D

---

### Post by Psquared on 2006-09-26
Actually, the more I think about the more I like your next to last idea - linking the menu.lst from the other distros to the one currently on the mbr. I might give that a go.

---

### Post by TiredBird on 2006-10-23
I realize the last post to this was three weeks ago but I've got to put my two cents worth in anyway.

Herman taught me some things I didn't know but he failed to mention one very important point about Grub. Grub runs before Linux. It does not use Linux or any operating system other than its own. Therefore, it doesn't even have to be on a partition with Linux. 

I have anywhere from three to five OS's on the same machine, Win XP plus two permanent flavors of Linux and up to two experimental ones. I have one small partition, (20-30 MB will do easily), that is strictly for booting. At the top level it only has a 'boot' directory. That directory only contains a 'grub' directory and the 'grub' directory has the same files you normally find in the 'grub' directory.

That's the Grub that's installed in the MBR and that's where the controlling 'menu.lst' is. That partition is mounted on all the other partitions, (on /mnt/boot), so I can edit the menu.lst file from any of them. By using the symlink structure Herman described, no update is ever necessary to the menu to make it work. However, I can edit it regularly so that the titles properly reflect what is getting booted when you select that entry.

If I do an install on one of the other partitions that installs Grub in the MBR without asking me, I immediately run grub, (from any Linux partition), enter root as my boot partition and setup the boot partition in the MBR. That puts it and its menu back in charge.

VERY EASY MAINTENANCE!

---

### Post by tacubuntuforums on 2007-01-04
Your answer seems interesting to me. It is similar to Hermann's but having things more ordered.
I'm planing to install two or three versions and I might do that.
But how do you write the entries for each sistem in menu.lst. Do you have any preference? (I understand that any will work) chainloadloading or pointing to the smlinks?

The only thing I did not understand very well (I hope) is the last paragraph.
Do you mean that in the case an install changes your mbr, what you do is boot any sistem and do:

$sudo chroot /boot
$sudo grub
>grub-setup

I don't understand it well, since I don't understand very well what happens, the details of the problem, when the mbr is changed.

Couldn't you do the same fix by booting from a floppy with grub or stopping the PC's boot process and entering grub?

Finally: How do you update grub?

thanx

---

### Post by TiredBird on 2007-01-04
I wrote that over two months ago. I just went back and looked again at the paragraph you mentioned. I have no idea what I meant. :confused: I know I didn't chroot because I have yet to figure out a good use for that one.:rolleyes: 

As for writing the entries in menu.list, I'm using Herman's symlinks. I've had kernels upgraded on me a couple of times since I started this method and I haven't had to change a thing. It all kept right on running.

Going back to that confusing paragraph, sometimes an install doesn't bother asking if you want to install grub. It just does it. When that happens, the MBR gets rewritten and it now point to the menu.list on the new partition. 

That is obviously not what I want so first I edit the correct menu.list, (in my case its on partition 1), adding the new or changed partition, then I start up grub  ```
..$ sudo grub
``` then I tell grub what I am using as its root ```
>root (hd0,0) 
```which tells it the first partition on the first hard drive which is where the operative menu.list is located then ```
>setup (hd0) 
```which tells grub to write all the setup stuff to the MBR on the first hard disk. Then I quit grub. Now it should boot into my newly changed menu and from there to whatever operating system I want to run.

I've been using ubuntu now for a little over a year and as far as I know, grub has not been updated during that time. If the grub folks ever do put out a change I want to incorporate, I'll have to figure out how to do it at that time. 

I hope my answers have been of help.

---

### Post by tacubuntuforums on 2007-01-07
Yes, they help. Thank you!

I don't know if the lines of code I wrote would be equivalent to what you've just wrote, but nevermind, what you wrote is very clear. Only the fact that in this case your menu.lst and where you try to install the mbr are in the same disk, withdraws generality to the example.

Today I was thinking how to manage the sharing of folders between two installations. What are the good ways to do it?
I don't think it would be a good idea to share folders with system configuration.
What about the user's. I can't share users. I can have users with the same name and passwords and make everything seem that the user's are the same, but they are not the same ones. If I add one user or if one of them changes his passwd in a system it won't be changed in the other. Well, maybe that's not too important and I can handle it.
At least I would like to have the same folder for user john in system A as user john in system-B. So if I want to share the \home folder, with its own partition, existing in install-A with install-B. What should I do when I install B?. If I'm able to mount /home and keep the data during the B-install, which sounds dangerous, and even more if I don't use a new username during the install, will it work?
Or should I let the new system create a new home folder somewhere and then I make soft links (or maybe hardlinks) to the user's folders.

But now, again, maybe it is not so good idea, after all, to mix up personal configuration data (from both systems) in the users folders and I should mantain the personal configuration separate and only the user-data-files (not configuration files) that the users create consciously should be shared by a soft or hard link.

What are your ideas about this?

---

### Post by TiredBird on 2007-01-08
> Only the fact that in this case your menu.lst and where you try to install the MBR are in the same disk, withdraws generality to the example.I have also, on another machine, done this where the MBR was on one drive and 'menu.lst' on another drive. It works too. In the case of two drives I think it is better because it at least establishes that both drives are turning and delivering some data.

I also agree that sharing folders of system configuration data is probably not a good idea. However, it is commonly recommended that you put the 'home' directory, and thus all of the users, on a separate partition so you can change or upgrade your operating system without redoing the user data too. 

I really don't know how it handles different operating systems but I do have one system where both ubuntu dapper and xubuntu dapper, which each live on a separate partition, share a home directory which is on another partition. Although the only user is me, I am able to use either system.

I think that the important thing to avoid is duplicating the data. On my most used system, I have about 50 GB of data that is accessible to Ubuntu, Xubuntu and Windows XP. In the case of the Linux flavors, there is a single /home directory (with me as the only user under it) on its own partition with soft links to the data which is on yet another partition that is fat32 so it can also be read by XP.

Put your /home directory on its own partition. Any install you do (of Linux anyway) is going to allow you to use that as part of the new install. At least it has worked okay for me.

---

