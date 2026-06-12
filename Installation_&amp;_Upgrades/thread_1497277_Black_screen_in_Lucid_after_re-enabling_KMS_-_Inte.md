---
title: "Black screen in Lucid after re-enabling KMS - Intel video"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by Contra75 on 2010-05-30
I was running Karmic on my Dell laptop with Intel video chip without any issues. Then I "upgraded" to Lucid. X would not boot in Grub into the 32 Kernel. 

I found this thread 
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

I first tried "Workaround D: use kernel other  than 2.6.32" - it worked for me with kernel 2.6.31. Lucid ran fine without any issues.

Then (I don't know why ](*,) ) I decided to try "Workaround A: re-enable KMS," and ran

echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u

Now I can't boot into Ubuntu at all. No matter which kernel (even the recovery modes) I now pick in Grub all I get is a black screen, no drums, no cursor, no nothing. I know I should not have touched what was working, but it's too late now. Any way I can reverse it?

---

### Post by efflandt on 2010-05-30
Have you tried **nomodeset** as a kernel boot parameter?  I think the issue may be that KMS does not work for your chip and you just made KMS the default.  Hopefully nomodeset boot parameter will still use the regular video modules instead of KMS.

I was not even aware the KMS was blacklisted for Intel video chips, which explains why there is no speed difference with my laptop using nomodeset or not.  But it is an older Toshiba from 2006 with no issues or special drivers at all.

---

### Post by Contra75 on 2010-05-30
How do I do it?

---

### Post by davidmohammed on 2010-05-31
when booting press shift to display grub - then press e to edit.

Before quiet splash add nomodeset

Once you've got to the desktop - to remove the changes you did with


echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u


type
sudo nano /etc/modprobe.d/i915-kms.conf

then
remove the text modeset=1


then type

sudo update-initramfs -u

I'm intrigued as to the graphics chip you have

can you type lspci | grep VGA

if its a 845 then you probably don't need to boot with an earlier kernel, just need to boot with nomodeset as described above

---

### Post by Contra75 on 2010-05-31
Something is not working.
After Grub got displayed, I hit "e" - here is what I see:

[I]recordfail
insmod ext2
set root="(hd0, 5)
search --no-floppy -- fs-uuid --set 8a7a030c-fcaf-4292-86b9-9f0514a12\eb2
echo "Loading Linux 2.6.31-21-generic ..."
linux /boot/mmlinuz-2.6.31-21-generic roo=UUID=8a7a030c-fcac-4292-8\6b9-9f0514a12eb2 ro single splash vga=788
echo "Loading initial ramdisk ..."
initrd /boot/initrd.img-2.6.31-21-generic[/I]

I even tried to boot from my liveCD and was able to find the file /i915-kms.conf but I don't know how to change its content as I am not booting as root from liveCD. 

**davidmohammed&#1073;** - Here is the display from  lspci | grep VGA:
*00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)*


I guess I could simply reinstall Ubuntu from the scratch, but then I would loose all the data I have there, so I would like to avoid it unless there is really no other way.

---

### Post by davidmohammed on 2010-05-31
ok - you seem to be booting from a non-lucid kernel recovery option - lucid kernels are 2.6.32.xx

also curious why you have vga=788 as your boot option

my laptop is the same chip as yours.  I boot with

i915.modeset=1

please can you reboot - but choose a lucid kernel (but not recovery option) - e to edit and remove vga=788

---

### Post by Contra75 on 2010-05-31
I will try that.
As I was writing above I was booting into a different kernel bk lucid kernel was not booting, so according to Workaround D I tried to boot from another kernel which worked from me. But then I decided to fix it and try to boot from the "right" kernel. Now nothing works and in this thread I am try to see how to fix it.

OK
display for 32 kernel is similar to 31, except for naming 32 kernel, and the following 
line ending like this: 
*linux /boot/mmlinuz-2.6.32-22-generic roo=UUID=8a7a030c-fcac-4292-8\6b9-9f0514a12eb2 ro splash vga=788*  quiet splash

I removed vga=788, and I got to a blinking cursor on the black screen, then for some second appeared a purple Ubuntu screen and back to complete darkness. I also tried typing *nomodeset* before *quiet splash* with and without deleting *VGA=788* Same result - BSOD.

---

### Post by davidmohammed on 2010-05-31
ok - as per my boot option described above - instead of nomodeset try i915.modeset=1

also remove quiet splash

do you see where it appears to hang?

---

### Post by Contra75 on 2010-05-31
Tried both options: black screen nothing else after Ctrl X

---

### Post by davidmohammed on 2010-06-01
... ok to summarise ...

1. booting with the lucid kernel with i915.modeset=1 briefly display a purple screen and then black with blinking cursor.
2. booting with the lucid kernel into recovery mode gave you nothing but a black screen and a blinking cursor.
3. booting with the .31 kernel now just gives you a black screen with blinking cursor
4. booting with the .31 kernel into recovery mode gave you nothing but a black screen and a blinking cursor
5. You have 855GM intel graphics chip.

If you can get to a cursor prompt in recovery mode, did you edit the i915-kms.conf file as per my post above to remove the modeset text?

if all of the above (1 to 5) are true statements then I'm out of ideas other than reinstalling and trying again.  

Can anybody help out here?

---

### Post by Contra75 on 2010-06-01
Ok, here is the recital of what happens:

Dell 700m laptop with Intel 855 video chip, which (as I could see from  other posts on this forum) sometimes has issues with  Lucid and its  kernel. Dual boot with XP. Everything worked fine with Karmic 9.10 then I "upgraded" to Lucid and did what I wrote in the very first post in this thread.

Now:
1) Either kernel boot w/o any changes - black screen.
2) Either kernel boot with typing "nomodeset" before or after "quiet splash" (in the line: *linux /boot/mmlinuz-2.6.32-22-generic  roo=UUID=8a7a030c-fcac-4292-8\6b9-9f0514a12eb2 ro splash vga=788*   *quiet splash*) - BSOD.
3) Either kernel boot with deleting vga=788, got blinking cursor, then a short purple Ubuntu screen, then (sometimes) quick 25 or something lines of loading Linux and then BSOD. No reaction to ALt-Ctrl-F2 or any other known to me combination.

I am about to scratch it all, delete Lucid and start over with Karmic. I know that some things could be fixed from LiveCD boot, could anything work here? :confused:

---

