---
title: "[SOLVED] Reinstalling GRUB"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by Vadi on 2007-09-04
Hello,

I know this definitely isn't the first topic about, but my problem is somewhat more specific, and I just want a bit more clarification before I take any steps (university starts tomorrow, and I need a working laptop!)

I have Edubuntu and Ubuntu installed; both are on separate partitions, and both have their own swap partitions. Edubuntu was installed first, then Ubuntu. Edubuntu is on sda1, Ubuntu is on sda4, but I'm not sure which one of them uses sda2, sda3 (both of those are swap partitions).

I want to remove Edubuntu altogether, as on my 40gb hard drive, it's getting a bit cramped. Reformatting the patritions would be easy enough, but the part I'm stuck on is GRUB, and afraid to do any work with it before I get some instructions that I understand.

As I understand it, because I installed Edubuntu first, it first goes to the Edubuntu grub. In there, edubuntu is listed first, and under "other operating systems" is my Ubuntu. So when I select Ubuntu, I think it goes to Ubuntu's grub, which loads right away.

So this is where the problem lies. I can't just remove the edubuntu grub, because the Ubuntu one is 'after' it, and I don't think it'll automatically become the first one. I've been told that since Ubuntu uses UUID's, I can just find out by them with swap does Edubuntu use, erase it, and erase the Edubuntu partition, and 'just' reinstall GRUB after that. The last part I suspect is the most vital and one I'm not totally sure I can do without messing up yet.

Any help would be appreciated if you could.

---

### Post by banewman on 2007-09-04
You haven't got it quite right there. The operating system that is installed last is the one that gives the choices when you boot up. If edubuntu is the first choice on your boot menu then that is what was installed last. Is that what you get? If you uninstall edubuntu then you will need to reinstall ubuntu's grub, which is not so hard if you have a live cd. Let us know what is the first choice on your boot menu and if you want more help. :)

---

### Post by logos34 on 2007-09-04
No, if Ubuntu was installed AFTER edubuntu then grub is pointing to the /boot on the ubuntu partition...it detected the edubuntu and added it to the bottom of menu.lst, as well as fstab.

So just unmount edubuntu, delete it (along with the corresponding swap--you actually only need one even when multibooting linux distros), and then take out the entries in /etc/fstab so it doesn't freak out on next boot trying to mount nonexistent partitions.  Remove the entry in  /boot/grub/menu.lst.

If you should ever want to add it (or any other ubuntu flavor) back later you can simply install the '(x)(k)(ed)ubuntu-desktop' metapackage within ubuntu.

EDIT:sorry, misread this:
> As I understand it, because I installed Edubuntu first, it first goes to the Edubuntu grub. In there, edubuntu is listed first, and under "other operating systems" is my Ubuntu. So when I select Ubuntu, I think it goes to Ubuntu's grub, which loads right away

So you must have installed Edubuntu LAST because it detected ubuntu and added it to bottom of menu.lst.

So just do what banewman suggested and [reinstall grub from the live cd,]("http://ubuntuforums.org/showthread.php?t=224351&highlight=catlett+live+cd") pointing to /boot on ubuntu partition.

---

### Post by rsambuca on 2007-09-04
You don't need the live CD to reinstall grub!  You can just boot ubuntu and type in sudo grub-reinstall

---

### Post by logos34 on 2007-09-04
> **rsambuca said:**
> You don't need the live CD to reinstall grub!  You can just boot ubuntu and type in sudo grub-reinstall

actually it's 'grub-install'

sudo grub-install /dev/hda (or sda --> puts grub on mbr)

but yes you're right, OP doesn't need live cd in this case.  coffee break time...

---

### Post by rsambuca on 2007-09-04
> **logos34 said:**
> actually it's 'grub-install'

sudo grub-install /dev/hda (or sda --> puts grub on mbr)

but yes you're right, OP doesn't need live cd in this case.  coffee break time...

:lolflag:  Nice grab.  I must be tired this morning!

---

### Post by Vadi on 2007-09-04
Wait, wait.

When I boot up, I first get Edubuntu, then under 'Other Operating Systems', I get Ubuntu.

That sudo grub-install looks like a really easy way, my only concern is, will I be even able to  boot into Ubuntu after I remove edubuntu?

Or... can I just reinstall ubuntu's grub before edubuntu's, so then I can remove edubunut safely?

---

### Post by logos34 on 2007-09-04
> **Vadi said:**
> Wait, wait.

When I boot up, I first get Edubuntu, then under 'Other Operating Systems', I get Ubuntu.

That sudo grub-install looks like a really easy way, my only concern is, will I be even able to  boot into Ubuntu after I remove edubuntu?

Or... can I just reinstall ubuntu's grub before edubuntu's, so then I can remove edubunut safely?

You need to boot into Ubuntu and run grub-install from there.  It will overwrite the existing grub (which points to Edubuntu root) with a new one pointing to the ubuntu root partition.  Then you can safely delete edubuntu.   

To recap:

-boot to the grub menu.  
-choose 'ubuntu' under 'Other operating systems'
-open a terminal and type:

**sudo grub-install /dev/hda** (or sda, etc.)

done.

---

### Post by Vadi on 2007-09-05
Okay, thanks! I'll try it out.

---

### Post by Vadi on 2007-09-05
Okay. I've done the grub reinstall in ubuntu, I didn't reboot yet, but could just someone verify that it's right before I reboot?

```
vadi@vadi-laptop:~$ sudo grub-install /dev/hda
Password:
/dev/hda: Not found or not a block device.
vadi@vadi-laptop:~$ sudo grub-install /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
vadi@vadi-laptop:~$ 

```

Thanks. Usually I'm somewhat reckless in trying out things, but the semester just started, and I need a bootable laptop :D.

---

### Post by Vadi on 2007-09-05
It worked flawlessly. Whew, what a relief.

---

### Post by banewman on 2007-09-07
How did it go Vadi? Are you on a bootable laptop?

---

### Post by Vadi on 2007-09-07
Yeah! Just doing "sudo grub-install /dev/sda" did it.

I can't seem to expand my patritions though, GParted doesn't seem to want to make them bigger... but that's another topic I guess, heh.

---

### Post by merlinus on 2007-09-07
Are you using gparted live cd?

-merlin

---

### Post by Vadi on 2007-09-07
Yah.

Grub is fine with downsizing the patritions, but not incresing their size. it's just not allowing me to.

---

### Post by roschell on 2007-09-25
just accepted offered download of new kernel image, installed, reboot, and could not get to system anymore. it starts for few seconds then the screen turns black. i am writing this way as i have not figured out yet how post new post here.

thanks

---

### Post by Vadi on 2007-09-26
Ouch. I got a new kernel thing too, but it booted up okay for me...

Do you have a live CD? If you do, can you get on it and post your menu.lst (sorry, I don't remember where is it located, you might need to use search).

---

### Post by craigyjack on 2007-09-26
grub's menu.lst is located at /boot/grub/menu.lst

when you installed the new kernel image, the old one should still be in your grub boot list. does the old one still boot?

if so, you can boot with it, go into menu.lst (sudo gedit /boot/grub/menu.lst) and comment out the new kernel version, and just use the old one. it doesnt really solve the problem with the new kernel, but it gets that new version out of grub, so you boot up with the kernel version that works.

---

### Post by theonlykman on 2007-10-02
hi, so when doing "sudo grub-install" how do I know which device to use? I have two hard drives plus an external one...when I do /dev/hd and tab I get hda hda1 hdb hdc hd1 and when I do /dev/sd and tab I get sda. How can I figure out which  represents my usb hard drive (where I want to reinstall grub on)?

Edit: I should probably explain some more. I had feisty installed on my external hard drive with one computer and now I've moved the external over to another computer and I installed feisty again on a seperate partition - however I did not install grub again at that point, mainly because I didn't know how the external was defined (as my question above states), and I would prefer not to overwrite the windows bootloader on the other hard drive, but right now grub doesn't recognize the installation on the new partition.

---

### Post by Vadi on 2007-10-02
Check gparted (gnome patrition editor), it'll tell you which drive is which easily.

---

### Post by theonlykman on 2007-10-02
Thanks, I just realized that. I also found the device mappings file in /boot/grub. That helped significantly.

---

