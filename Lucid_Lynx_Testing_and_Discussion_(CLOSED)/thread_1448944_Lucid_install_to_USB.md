---
title: "Lucid install to USB"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lum on 2010-04-07
Recently I tried to create a bootable USB device to run lucid 10.04 (I  used a daily snapshot from about a week ago). This is not a live USB  stick rather, I used a live USB stick, booted the system and selected  another USB stick to install onto. I've done this on various Ubuntu  incarnations in the past. 

All appeared to go OK, however, at the end of the install neither the  installed USB OR the live USB worked. Yes - it damage the live usb  install. I repeated this twice with the same result each time. I then  booted a VM with the lucid live CD, and tried to install to USB. same  result. The USB stick - although it does have a filesystem, it isn't  bootable. The VM no longer boots. 

At a guess, I'd say that the installer is messing up /dev/sda and  corrupting the boot media somehow. 

As I say, I've used this method lots of times in the past on earlier  Ubuntu systems so it should work OK. 

Any thoughts or anyone else seen the same thing ?

Thanks !

---

### Post by QLee on 2010-04-07
[QUOTE=lum]Any thoughts or anyone else seen the same thing ?[/QUOTE]

I hope you realise that Lucid is not released yet, still in beta.

I can't advise trying to do things with older snapshots, in my opinion you should have the latest upgrades to ensure that you aren't chasing a bug that has already been corrected and confusing lots of the people who read these posts..

Just writing that the thing isn't bootable doesn't give much data, how far along does it get? What error message does it drop? Where did you have the installer install GRUB MBR.

---

### Post by lum on 2010-04-07
Thanks for the response. A few more details....

At the time of starting the tests I had the latest daily build of the live ISO available so unless the issue has been resolved in a later build (& I'll chk that shortly), I suspect the issue still exists. 

The nature of the issue is that the files appear to have been transferred but when the system is rebooted, I never see Grub, so it maybe a corrupt mbr or grub itself. More worrying is that not only is the USB that I was creating non-bootable, the live USB that was creating the image was also corrupted and no longer bootable. This gets stuck at grub rescue. The issue was repeatable & occurred in a VM also. 

A bit of background, I've been working with Ubuntu since Hoary (5.04) using all of the versions in-between on, well, too many installs to recall. This is the first time I've tried to work with pre-release stuff so I understand that its WIP.

I'll try a later release & see if thats any different. Thanks.

---

### Post by QLee on 2010-04-07
[QUOTE=lum]... More worrying is that not only is the USB that I was creating non-bootable, the live USB that was creating the image was also corrupted and no longer bootable. ...[/QUOTE]

Might this only mean that the MBR isn't correct, I would be really surprised for an install to have mucked up the install media system files, although, if you wrote to the wrong MBR it could be a problem next time you try to boot.

---

### Post by lum on 2010-04-07
> I would be really surprised for an install to have mucked up the install  media system file
yes, me too. 

The install process is automatic & I've not had to run anything other than the default installer. I didn't invoke grub manually. Everything is straight off the live USB. I guess the difference that I have over a typical install is that I am installing to a USB stick not a HDD. 

9.04 installs & runs OK on the same stick so thats odd in itself and more odd is the upset it is causing to the live boot media from which I'm installing. It does look like the installer got confused as to the media it needed to update to add grub.

---

### Post by QLee on 2010-04-07
[QUOTE=lum] It does look like the installer got confused as to the media it needed to update to add grub.[/QUOTE]

I thought I remembered some place where you had the choice of where to install GRUB as part of the install process, not just rely on it being the MBR of sda. I only have alpha install disks, can't check but has that feature been removed?

---

### Post by QLee on 2010-04-07
Thinking about the issue you describe, if the hints about the MBR don't help. it probably would be a good idea to have some detail about your system. For example, what device node was the install media on when you installed, what device node is the drive that you are trying to install to on, and are there other drives connected, as well as where did you write the MBR. 

One easy way to present info that a lot of helpers here like to see is by using Boot Info Script courtesy of forum member meierfra. This is the page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
If you take the time to post this, someone may have some useful ideas for you and this might easily turn out to be the fastest way to get a satisfactory answer.

---

### Post by wilee-nilee on 2010-04-07
Did you do a full install on the 2nd usb and not notice in the last gui window the advanced button which is shows where grub is pointed at. It should be pointed at the usb device with no partition #.

It sounds like grub was installed in the wrong place.

---

### Post by cphwizard on 2010-04-08
> **wilee-nilee said:**
> Did you do a full install on the 2nd usb and not notice in the last gui window the advanced button which is shows where grub is pointed at. It should be pointed at the usb device with no partition #.

It sounds like grub was installed in the wrong place.

I had the same experience as lum, trying to install from CD to a USB.
The installation was properly done on the USB - /dev/sdb, however grub was installed on /dev/sda, making it impossible to boot from either.

---

### Post by kansasnoob on 2010-04-08
> **cphwizard said:**
> I had the same experience as lum, trying to install from CD to a USB.
The installation was properly done on the USB - /dev/sdb, however grub was installed on /dev/sda, making it impossible to boot from either.

Grub2 always installs to /dev/sda by default. In order to change that you must first know how the installation media recognizes your drives. That can usually be achieved by either running the command "sudo fdisk -l" or looking in Gparted.

Then when you get to the final installation screen where you get to review your installation parameters you'll see a box labeled Advanced in the lower right hand corner. You must click on that and select which drives mbr to install grub2 on.

Note: it's almost never a good idea to install grub2 to a partition rather than the mbr of a drive!

---

### Post by kansasnoob on 2010-04-08
Also that can be fixed after the install. I like to use a chroot to restore grub2 like:

```
sudo mount /dev/sdXY /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

Note that the XY = the proper partition designation of the installed Ubuntu root partition aka, / , eg: /dev/sda1 or /dev/sdb1.

```
grub-install /dev/sdX
```

Of course there the X = the proper drive designation.

Note: if "grub-install" reports any errors run:

```
grub-install --recheck /dev/sdX
```

Then exit the chroot and unmount the partition:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

So if the installed hard drive is sda and it's Ubuntu root "/" partition is sda1 you'd mount and chroot /dev/sda1, then "grub-install" to /dev/sda.

To make the external bootable you must first have the BIOS set to boot from USB first (mine is actually set to boot CD first, USB second, and hard drive third).

Then you must install it's grub to it's mbr, so if the external is sdb and it's root partition is sdb1 you'd mount and chroot /dev/sdb1, then install it's grub to /dev/sdb.

Clear as mud?

---

### Post by cphwizard on 2010-04-08
> **kansasnoob said:**
> Clear as mud?

Crystal! Thanks a lot.

That's what I get for mucking about with this stuff while Champions League is on :P

---

### Post by lum on 2010-04-09
> Grub2 always installs to /dev/sda by default
I see it but I don't believe it. Logically if you are installing a new operating system to a harddisk formatting the whole thing in the process I would have though that you would put the bootloader onto that. Seems not. 

Thanks to all  for  the replies. I had earlier managed to get the stick bootable so it's OK now, I guess when I did this in the past the USB stick got enumerated differently hence why it worked in earlier releases.

---

