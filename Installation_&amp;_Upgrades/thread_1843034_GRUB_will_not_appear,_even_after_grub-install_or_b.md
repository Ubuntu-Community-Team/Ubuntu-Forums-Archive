---
title: "GRUB will not appear, even after grub-install or boot-repair"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by padel on 2011-09-12
Dear all,
 
 
 
I've just installed Ubuntu 11.04 on my Sony Vaio VGN-731WN. Once installed, I reboot and GRUB does not appear. Instead, Windows XP appears.
 
 
I've been searching and trying to make GRUB work, such as running a Live and on it running grub-install /dev/sda in a chrooted environment ( mounting dev, dev/pts, sysfs, proc, etc. ), or using the Boot-repair program, but none worked. The result is always the same: Windows XP loading, and no GRUB starting. Furthermore, when running the bootinfoscript I always get:
 
 
[FONT=Verdana][COLOR=#666666]=[/COLOR]> Windows is installed in the MBR of /dev/sda.[/FONT]
 
 
How can I make GRUB work? How can I install it in the MBR?
 
 
The information of the bootinfoscript is attached here:
 
 
[http://paste.ubuntu.com/687886/](http://paste.ubuntu.com/687886/)
 
thank you very much

---

### Post by garvinrick4 on 2011-09-12
Put in Ubuntu live cd of 11.04 open a terminal and copy and paste these commands.
```
sudo mount /dev/sda6 /mnt
``````
sudo grub-install --boot-directory=/mnt/boot /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```Boot into Ubuntu and:
```
sudo update-grub
```Now should have installed grub to mbr and added Windows to config file and 
as a menuentry.

#umount is not a typo.

## [COLOR=Red]You look like you are missing boot files in your install of sda6[/COLOR], if above does not work we will have to install grub files from Live Cd (your install cd using Try Ubuntu) Post 6.

---

### Post by Quackers on 2011-09-12
It appears that grub is not installed.
Boot from the Ubuntu live cd/usb and select "try Ubuntu" and when the desktop loads please open up a terminal, then copy/paste these lines into it, one line at a time, pressing enter after each line.
It should report no errors.
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
``` If an error is reported when running the second command please run this one instead ```
sudo grub-install --boot-directory=/mnt /dev/sda
``` Once no errors are reported please reboot, taking out the Ubuntu cd/usb. 
You should then get Ubuntu booting directly. If it does, open a terminal and run ```
sudo update-grub
``` and watch the terminal screen as grub.cfg is run. You should see the Windows Loader recognised. If it appears please reboot and you should then see a grub menu giving you the choice of which operating system to boot.

---

### Post by coffeecat on 2011-09-12
Welcome to the forum. :)

I don't know why grub was not installed when you first installed Ubuntu. Using a chroot is a perfectly valid way of installing grub to the mbr, but there's a simpler way. See here, under Copy LiveCD Files:

[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)

You don't need to run fdisk as you know from your boot script output that your Ubuntu root partition is on sda6. Boot up with the live CD, choose "try Ubuntu" to get to the live desktop, open a terminal, and:

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Then reboot. Your grub.cfg looks OK so you may not need to run update-grub.

One odd thing about your boot script output. The boot flag is set on both sda2 your Windows partition, and on sda6, your Ubuntu partition. Windows needs the boot flag if it is booting from Windows mbr code, but not if booting from grub. But what I can't explain is how you have two boot flags and a boot flag on a logical partition, both of which I thought were impossible. Not that it should make any practical difference to your setup.

**EDIT**: aha! beaten to it by garvinrick4 and Quackers. You have to be quick round here! :p

---

### Post by Quackers on 2011-09-12
I didn't think 2 boot flags were possible! I don't think I've seen it before.

---

### Post by garvinrick4 on 2011-09-12
If previous post did not do it because of lack of boot files in sda6 install then this
will install boot files and put in mbr so you are up and working.
#Make sure internet is working in Live CD and open terminal and copy and paste one
at a time. (Live Cd in install CD using Try UBuntu and get internet working.

```
sudo mount /dev/sda6 /mnt
``````
sudo mount -o bind /dev /mnt/dev; sudo mount -o bind /dev/pts /mnt/dev/pts; sudo mount -o bind /proc /mnt/proc; sudo mount -o bind /sys /mnt/sys
``````
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
``````
sudo chroot /mnt
``````
apt-get update
```If that above gave errors you do not have internet connection
```
apt-get purge grub-common grub-pc
``````
apt-get install grub-common grub-pc
```When install grub it go's into sda not sda1 or sda6 but sda and you can toggle with tab key if have to at install of grub.```
update-grub
``````
exit
``````
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys; sudo umount /mnt
``````
sudo reboot
```Now should all be fine.

---

### Post by garvinrick4 on 2011-09-12
coffeecat, quackers,
 I have to sign off for 3 hours or so can you keep an eye on this Thread.
                       Thanks, Rick

---

### Post by Quackers on 2011-09-12
No problem for an hour or so :-)

---

### Post by coffeecat on 2011-09-12
I'm OK for about half-an-hour. :)

---

### Post by padel on 2011-09-12
Thank you very much for your replies

i followed the step that [garvinrick4]("http://ubuntuforums.org/member.php?u=899097") indicated, and it worked :)

thank you for replying so quickly :D

---

### Post by Quackers on 2011-09-12
Excellent! Happy Ubuntuing :-)

---

### Post by coffeecat on 2011-09-12
Good luck with using Ubuntu! :)

---

### Post by Blasphemist on 2011-09-12
I was following this and understood, except for the wierdness pointed out, until it came to what ended up working. Garvinrick could you explain what the binding and resolving conflict was doing? Thanks

---

### Post by garvinrick4 on 2011-09-12
> **Blasphemist said:**
> I was following this and understood, except for the wierdness pointed out, until it came to what ended up working. Garvinrick could you explain what the binding and resolving conflict was doing? Thanks
OP did not have all boot files in his install below is how it should have looked in bootscript.
> sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
#So you mount the install sda6 and have to bind /dev /dev/pts /sys and /proc to the mounted 
sda6 at /mnt to be able to purge and then reinstall grub-pc and update-grub from within chroot (or root) of that install sda6. You can update and upgrade from here or run dpkg commands  or install or remove packages really whatever you choose to do.
#The cp of /etc/resolv.conf to /mnt/etc/resolv.conf is copying the internet connection from the
Live CD to the mounted sd6 at /mnt
#You can use chroot from another install or Live CD as long as they are of the same architecture (32 bit or 64 bit).

## Below is a link written by drs305 that is a better explanation and one to keep in bookmarks.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")
## There are many ways to achieve the same goal so you will see different types of code, some simpler that others.

---

### Post by padel on 2011-09-12
thank you, it is great for the beginners like me to know that there are people like you. Helping a lot. 
 
I hope to learn and enjoy of Ubuntu :)
 
thank you

---

### Post by garvinrick4 on 2011-09-12
> **padel said:**
> thank you, it is great for the beginners like me to know that there are people like you. Helping a lot. 
 
I hope to learn and enjoy of Ubuntu :)
 
thank you
There are a lot of Ubuntu users in these Forums that are here to help and be helped also. I believe you will make a fine Ubuntu user you had a bit of an unusual problem and hung in there to get the fix while being polite about it. I hope to see you around these Forums in the future padel, enjoy your Ubuntu.

---

