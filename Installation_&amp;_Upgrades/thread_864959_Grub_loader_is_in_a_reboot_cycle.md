---
title: "Grub loader is in a reboot cycle"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by philip_doherty on 2008-07-20
Hi,

I have two hard drives. Vista was my main OS, it is on a partition on the first hd. I then installed ubuntu on the second hard drive, after the installation the grub menu came up fine and i could boot into ubuntu, however the opt ion for windows was 'embedded XP'. 

I changed the boot parameters to point to the vista partition on the other drive, which then booted sucessfully, however it only booted once.

After the first boot of vista my machine now gets past the bios and flashs up one line (i think it says grub loader) but then it immediately reboots itself, then it repeats this cycle over and over. Does anyone know whats happened? I'm not even sure which hd the grub loader is on and I can't get into either OS to change it! Help!

---

### Post by coffeecat on 2008-07-20
Offhand, I can't think how Grub could reboot itself, but why not boot up with the live CD, mount the installed Ubuntu partition and inspect your /boot/grub/menu.lst. If you can't see what's wrong you could always post the contents of menu.lst. If you can, you can edit from the live CD. And if you need to post, you should be able to do so from the live environment.

Marvellous things these live Linux CDs, aren't they? :)

---

### Post by Vishal Agarwal on 2008-07-20
use the pause key and enter key quickly at keyboard to see the message (I am use to do the same at booting time to see system messages).In one or two hits u will be able to see the message. After then it will be easier to handle the problem.

---

### Post by philip_doherty on 2008-07-20
> **coffeecat said:**
> Offhand, I can't think how Grub could reboot itself, but why not boot up with the live CD, mount the installed Ubuntu partition and inspect your /boot/grub/menu.lst. If you can't see what's wrong you could always post the contents of menu.lst. If you can, you can edit from the live CD. And if you need to post, you should be able to do so from the live environment.

Marvellous things these live Linux CDs, aren't they? :)

I managed to use the live cd to get onto ubuntu, I can mount the drive and look at the grub menu.lst. I even have the original which I know works, the problem now is that I dont have permissions to change this file and can't figure out how to set them up, how do i browse to that directory from the terminal, I dont know the syntax to browse the 2nd hard drive.

---

### Post by Yannick Le Saint kyncani on 2008-07-20
> **coffeecat said:**
> Offhand, I can't think how Grub could reboot itself

+1, I've never seen grub rebooted when a problem occur, it just prints the problem and does nothing.

So I'd say the problem is not grub-related and lies elsewhere.

---

### Post by confused57 on 2008-07-20
> **philip_doherty said:**
> I managed to use the live cd to get onto ubuntu, I can mount the drive and look at the grub menu.lst. I even have the original which I know works, the problem now is that I dont have permissions to change this file and can't figure out how to set them up, how do i browse to that directory from the terminal, I dont know the syntax to browse the 2nd hard drive.
Once you mount the Ubuntu drive, using the live cd, right-click & select properties, then "Volume" tab...see how the drive is designated, e.g. /media/disk or /media/disk-1...then from terminal:
```
gksudo gedit /media/disk/boot/grub/menu.lst
```

You might also want to post the output of:
```
sudo fdisk -l
```
-l is a small "L"

---

### Post by coffeecat on 2008-07-20
> **philip_doherty said:**
> I managed to use the live cd to get onto ubuntu, I can mount the drive and look at the grub menu.lst. I even have the original which I know works, the problem now is that I dont have permissions to change this file and can't figure out how to set them up, how do i browse to that directory from the terminal, I dont know the syntax to browse the 2nd hard drive.

From the live CD, all you have to do is 'gksudo gedit /path/to/file/you/want/to/edit'. You are not prompted for a password but you are given administrator rights.

It's a bit of a two-edged sword really. The live CD is an excellent way of tweaking and repairing systems but it's almost too easy to get root privileges. That's why computer security always starts with physical access to the machine.

---

### Post by philip_doherty on 2008-07-22
OK,

I got into the menu.lst file and replaced it with the original but that didn't solve the problem.

My machine was working fine using grub loader to boot in Ubuntu on my second hard drive but something has changed when I altered the grub menu.lst and booted into vista on my primary drive. 

Would the boot into Vista have caused vista to change something i.e. where the comp is looking for the grubloader, or maybe its not even looking in the right place anymore. I've tried changing my boot options from primary hd to secondary hd but nothing seems to be working.

Should i try a ubuntu reinstall on my second hard drive and see if that sorts it - I'm still left with the original problem though of not being able to boot into vista from the grub loader.

any help appreciated, phil.

---

### Post by confused57 on 2008-07-22
> **philip_doherty said:**
> OK,

I got into the menu.lst file and replaced it with the original but that didn't solve the problem.

My machine was working fine using grub loader to boot in Ubuntu on my second hard drive but something has changed when I altered the grub menu.lst and booted into vista on my primary drive. 

Would the boot into Vista have caused vista to change something i.e. where the comp is looking for the grubloader, or maybe its not even looking in the right place anymore. I've tried changing my boot options from primary hd to secondary hd but nothing seems to be working.

Should i try a ubuntu reinstall on my second hard drive and see if that sorts it - I'm still left with the original problem though of not being able to boot into vista from the grub loader.

any help appreciated, phil.

Mount your root partition with the live cd, then post the output of:
```
gedit /media/ubuntu/boot/grub/menu.lst
```
you can probably just post your Ubuntu & Windows boot entries.
and please post the output of:
```
gedit /media/ubuntu/boot/grub/device.map
sudo fdisk -l
```
-l is a lowercase "L"

You say you're not able to boot into Vista with grub, can you boot into Ubuntu from grub?  If so, you don't need the live cd to edit your menu.lst.

---

### Post by miracleman on 2008-07-22
I have a similar problem and the solution can be found here:

[http://ubuntuforums.org/archive/index.php/t-625562.html](http://ubuntuforums.org/archive/index.php/t-625562.html)

basically what you have to do is:

[I]Try this. Boot from the Live CD.

Change "#groot (hd1,0)" in menu.lst to "#groot (hd0,0)"

In a terminal:


sudo update-grub
sudo grub


At the "grub>" prompt:

find /boot/grub/menu.lst

This will return something of the form (hdx,y), probably (hd1,0)

root (hdx,y)
setup (hdx)
quit

(of course replace x and y by their actual values)
[/I]

Extracted from the thread which is linked above.

It solved my problem immediately, but it is not a permanent solution! The problem reoccured after a few more reboots. 

I'm still trying to look for a permanent solution, anyone has any ideas?

---

### Post by philip_doherty on 2008-07-23
> **miracleman said:**
> I have a similar problem and the solution can be found here:

[http://ubuntuforums.org/archive/index.php/t-625562.html](http://ubuntuforums.org/archive/index.php/t-625562.html)

basically what you have to do is:

[I]Try this. Boot from the Live CD.

Change "#groot (hd1,0)" in menu.lst to "#groot (hd0,0)"

In a terminal:


sudo update-grub
sudo grub


At the "grub>" prompt:

find /boot/grub/menu.lst

This will return something of the form (hdx,y), probably (hd1,0)

root (hdx,y)
setup (hdx)
quit

(of course replace x and y by their actual values)
[/I]


It solved my problem immediately, but it is not a permanent solution! The problem reoccured after a few more reboots. 

I'm still trying to look for a permanent solution, anyone has any ideas?

Thanks but that still hasn't solved the problem, i think ill try a new install to see if that sorts out the grub issue, although i may be back at the start again, fingers crossed.

---

### Post by Sef on 2008-07-23
> I have two hard drives.

If one is a sata and the other is a pata, then check out this [launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497") report.

---

### Post by philip_doherty on 2008-07-28
> **miracleman said:**
> 

Change "#groot (hd1,0)" in menu.lst to "#groot (hd0,0)"

In a terminal:


sudo update-grub
sudo grub


At the "grub>" prompt:

find /boot/grub/menu.lst

This will return something of the form (hdx,y), probably (hd1,0)

root (hdx,y)
setup (hdx)
quit



Does the # at the start of the line not mean that is actually commented out, so changing that number wont actually do anything. I'll change the number and comment it out to see what gives. I have another issue with the grub now too but that can wait.

---

### Post by philip_doherty on 2008-07-28
Ok, its definately the vista boot doing something.

When I install Ubuntu and the grub loader it works perfectly when I only boot into Ubuntu. When I go into the menu.lst file and change the Vista line to boot from hd(0,0) (it wont boot otherwise) this works but after I close down Vista the computer goes into a reboot cycle everytime I turn it on - it doesnt even make it to the Grub screen. 

Does anyone have any idea why the Vista boot is causing this - is is redirecting the boot location away from the grub loader. 

I hope this makes sense.

Thanks.

---

