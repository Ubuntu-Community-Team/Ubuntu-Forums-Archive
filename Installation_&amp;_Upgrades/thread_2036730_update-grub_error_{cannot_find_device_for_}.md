---
title: "update-grub error {cannot find device for /}"
date: 2012-08-02
forum: Installation &amp; Upgrades
---

### Post by Odys1 on 2012-08-02
Hello every1, I've been trying to install xubuntu on my Asus EEE 1101ha, which is known to present some problems due to lack of efficient poulsbo drivers. By following the instructions in the official documentation of Ubuntu, I managed to reach a working live CD environment and install Xubuntu. The next step I had to follow was to edit a grub text and then update grub for the changes to take effect {If I discarded this step, grub wouldn't load, giving me an error message which I will mention if needed}. Unfortunately, when I used "sudo update-grub" to update it, the following error came up:

/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?). 

I mounted all the filesystems yet it didn't help. I tried running grub-probe by double clicking it, but again it didn't seem to run, nor was grub updated since it kept giving me the same error. I googled the error a bit, but although I tried a thing or two, it was no use.  Any help would be appreciated.

---

### Post by Beacon11 on 2012-08-02
It sounds like you're trying to make the grub changes on your (Xubuntu-installed) filesystem from a LiveCD. Is that correct? Please do explain what was wrong in the first place requiring a change.

If you are indeed running update-grub from a live CD you'll need to mount the virtual filesystems and chroot first:

```

# Mount root partition:
sudo mount /dev/sdXY /mnt # /dev/sdXY is your root partition, e.g. /dev/sda1

# If you have a separate boot partition you'll need to mount it also:
sudo mount /dev/sdYY /mnt/boot

# Mount your virtual filesystems:
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done

# Chroot
sudo chroot /mnt

```

NOW you can do grub-install and update-grub and whatnot and it'll operate on your installed system rather than the LiveCD.

---

### Post by Bluphx on 2012-08-03
Hey I'm was having the same problem with 32bit and trying to setup dual boot with xp (got 32bit working minus some drivers missing as a solo OS never dual) but have 4gb ram so wanted to use 64bit to utilize hardware n figured id just emulate xp if I have too, but while installing 64bit server or desktop, I cannot get around this error.

 I was given a vaio vpcz11cgx/x, has dual solid state drives Im pretty sure it's raid0. I've tried letting it auto setup on (striped drive) and errors on bootloader install. /dev/mapper is what shows up as default it, I've tried /dev/sda and the Ubuntu OS partition, blank partitions fat/ext/blank on beginning and end of disk =P. On manual partitions I've tried just ext4 n swap space as primary, I've left a 2gb primary partition to instal grub n put ext4 n swap in extended logical partition, also tried 2gb primary with ext as primary n swap on extended. I think my error due to either a raid config or partitioning... Lol or both

Also curious which has a more stability 64bit server or desktop. Thanx for help in advanced.

---

### Post by Odys1 on 2012-08-03
The virtual filesystems are not found. What do I do wrong? Sry, I'm kinda new to linux... heres what I type and what it returns:

```
xubuntu@xubuntu:~$ for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
mount: mount point /mnt/dev does not exist
mount: mount point /mnt/dev/pts does not exist
mount: mount point /mnt/proc does not exist
mount: mount point /mnt/sys does not exist
mount: mount point /mnt/run does not exist

```I reinstalled Xubuntu in a single partition choosing the automatic installation option. The root partition is therefore /dev/sda1. What is there to be done then?

P.S. You guessed right, I'm using the console from a Live USB stick :)

---

### Post by drs305 on 2012-08-03
The error message usually means the system partition was not mounted properly. Did you mount your real xubuntu partition (sda1) on /mnt before running the command?

You might try installing Boot Repair (see link in my sig line) from the LiveCD/USB Desktop and let it try to fix GRUB. If it can't do it with the "Recommended repair" button there is an Advanced option that can take you through the 'chroot' method. 

If neither of the Boot Repair options fixes things, it has an option to run a boot info script, which can provide us with information we need to give you more specific advice.

---

### Post by Odys1 on 2012-08-03
Nvm, although the update-grub didn't work so the text file wasn't modified, grub2 loads normally and I finally booted xubuntu from the hard disk installation. I hope grub keeps that way. I won't label the thread as solved today, cause, I'm not still sure about how stable grub is. Furthermore, maybe Bluphx can get some help from here before I close it. Thanks again for your help guys, I hope someday I'll be amongst you who offer help around here.

---

### Post by Bluphx on 2012-08-03
Yo thanx for the heads up, Im going to try to run the bootrepair program if this install doesn't work. I've setup the partition in gpart before hand this time as:

ATARaid volume 0 238.48gb /dev/mapper/isw_bfdjejgiae
extended 238.48gb
ext4 200gb
unallocated 39gb
linux-swap 4.2gb
unallocated 4mb

I have left 4mb on the end of the drive b/c all the other screens and my other computer that runs ubuntu fine has an extra 2mb on end of HD. I've also left 39gb floating between ext4 and swap b/c if i can get a working install I'd like a XP partition to dualboot or VM from.

All goes fine till very end of install n get a GRUB error and ask to reselect where to install boot. Default it tries /dev/mapper/, i've tried volume #'s and sda/b/ect.

Thanx again in advanced, ex apple genius so starting to learn the lingo n new ways of ubuntu.

---

### Post by Odys1 on 2012-08-04
Here I am again... ok, I don't know how I did it, but it seems like grub tries to load from the live usb, even though I have already installed xubuntu on the hard disk. Here's the case: If I try to load xubuntu from the hard disk without having the usb stick plugged, grub doesn't load. If I plug the usb stick, grub loads normally and xubuntu boots from the hard disk {This means I can't even boot from the live usb, yet I can't boot from hard disk without it!}. So... please tell me some good news... I will keep you updated in case I successfully update grub and solve this nonsense :P

---

### Post by Odys1 on 2012-08-04
Well... I've done all I could. I followed all three steps of this guide: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

yet nothing changed. I still need the usb stick to boot. If I don't use it, grub doesn't start and I only see a flashing cursor. I believe that the problem lies in that grub tries to load from the usb stick instead of the hard disk. I came to this conclusion after I prompted: 
sudo update-grub
in order to finish the third option given on the guide linked above, for as soon as I pressed enter the usb started flashing, indicating data transmission to the usb stick! I don't believe its a coincidence. I prompted "sudo update-grub" while the console was running from the hard disk, but I believe that this commanded the update of the usb stick's grub. When I removed the usb stick and retried using the update-grub command, the update was again completed successfully {Which means that after I removed the usb stick, the command now went for the hard disk's grub... right? :O} Omg I know all this is confusing but, does anyone know some way to direct grub startup to the hard disk's grub installation {In human terms: I want the .txt file where the grub boot path is written, so that I can modify it to lead grub to boot from the hard disk}? Or is it something else? Help!!!

---

### Post by drs305 on 2012-08-04
Odys1,

Normally all that should be required is to change your boot drive's MBR instructions to point to your Ubuntu partition rather than the external device. You do this with the 'grub-install' command. 

Boot to your normal Ubuntu OS (even if it requires using the USB initially). After it boots, run the following command, using the correct drive letter. Just make sure the drive designation is what you think it is (sda, sdb, etc). You can run "sudo fdisk -l" to check first if necessary. Do NOT use the partition number:
```
sudo grub-install /dev/sda
```

The next time you boot just make sure the external is not inserted and the BIOS should look to the sda drive's MBR for instructions on where the bootloader files are located.

---

### Post by Odys1 on 2012-08-04
Yep, that was it. At last I can boot normally without the usb stick. Thanks for everything!

---

