---
title: "multiple installation/boot problems"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by Skabsavage on 2012-04-29
Alright my problems started when I decided to upgrade to 12.04 from the update manager. I had 11.10, been working fine since oct. During the upgrade I lost my internet connection and the upgrade froze. I force quit the update manager and when I went back to restart it, it wouldnt start. I tried to open a terminal and that wouldnt start. I tried to open firefox and that wouldnt start. So I figured oh whatever ill restart the computer and it will be fine. 

When I tried to reboot it gave me a filesystem not found error. Maybe force quiting the upgrade corrupted data, or overwrote some files?

I decided to reinstall 11.10 from USB. Well after getting into the grub menu, and I choose "try ubuntu without installing" I get a blank screen. "install ubuntu" also goes to blank screen.

I looked up the sticky [http://ubuntuforums.org/showthread.php?t=1743535&highlight=11.10+boot+from+usb+blank+screen](http://ubuntuforums.org/showthread.php?t=1743535&highlight=11.10+boot+from+usb+blank+screen) but I get lost somewhere around step 2-3 and all of the things Ive tried relating to the graphics card continues to give me a blank screen. 

Now heres where the biggest problem happened. I decided to delete the partition that linux was on from windows (dual booted) and now when I restart it [http://ubuntuforums.org/showthread.php?t=1743535&highlight=11.10+boot+from+usb+blank+screengoes](http://ubuntuforums.org/showthread.php?t=1743535&highlight=11.10+boot+from+usb+blank+screengoes) into the grub rescue. Ive been reading through things since yesterday morning and I am still stuck. Thanks in advance.

My computer setup: 
Asus G73j
i7 CPU at 1.6ghz (i think)
ATI Radeon 5870 card
500gb harddrive and 24in Dell external monitor

---

### Post by oldfred on 2012-04-30
At this point install this:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

You can either add it to an Ubuntu liveCD or USB or download it as a full liveCD.

It should let you add a Windows boot loader back to boot Windows if you want. 

Your issues may be with your video driver but I use nVidia and have to use nomodeset. Not sure if you need nomodeset or not.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Some i7 or similar systems also needed other boot parameters.

Are you booting in UEFI or BIOS mode. If you do not know you probably are in BIOS mode.

---

### Post by Skabsavage on 2012-05-01
I was trying to boot in UEFI mode. I downloaded the boot rIepair and put it on a USB with Unetbootin, and when I tried to boot from it, I got the blinking bar and it hung. So I was gonna try with a disc and I found a disc with 11.04 on it and I was able to boot from that.

Im going to run the Boot repair from the LiveCD and hopefully get back  into windows and then reinstall 11.04 from there. Hopefully that will fix  my issues and I can try to update to 12.04 down the road.
Thank you for your help, I dont think I would have found the Boot Repair on my own.

---

### Post by Skabsavage on 2012-05-01
The boot repair worked. Ran it through the terminal and followed the directions. I was able to boot back into windows 7 again. 

I will try installing 11.04 in the morning.

---

### Post by darkod on 2012-05-01
There is something strange. If the internet stopped during the download, nothing should happen. It doesn't start the upgrade until all files are downloaded first.
If the actual upgrade started, it doesn't matter if the internet connection is working or not. It already has all files downloaded locally.

To finish off a started download, you can try booting the recovery mode, dropping to root prompt and running:
dpkg --configure -a

If it complains it's in read only mode, try booting into live mode, mounting your root partition, entering with chroot and doing the same. If we assume your root is /dev/sda5, it would be like:
```
sudo mount /dev/sda5 /mnt
sudo chroot /mnt
dpkg --configure -a
exit
```

Don't forget to mount your correct root partition if it's not sda5.

---

