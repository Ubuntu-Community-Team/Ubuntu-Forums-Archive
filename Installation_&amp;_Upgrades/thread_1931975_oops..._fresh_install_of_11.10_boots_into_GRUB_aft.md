---
title: "oops... fresh install of 11.10 boots into GRUB after getting the updates."
date: 2012-02-26
forum: Installation &amp; Upgrades
---

### Post by ijason on 2012-02-26
oh dang.

i just finished installing 11.10 onto my aged laptop, and everything worked splendidly until i rebooted after doing the big first update. now it boots me directly into the GRUB prompt :<

i assume that everything is actually ok, and the GRUB has just slipped a cog. however, i don't know how to start to figure out the solution, and searched for "11.10 boots into grub" return - somehow - no results on the forum.

please help! :)

typing "exit" reboots me back into GRUB
typing "boot" returns "no loaded kernel"
typing "ls" returns "(hd0) (hd0,msdos1)"  - the computer only has a single drive, so this seems ok
typing "normal_exit" change my prompt to "grub rescue>" typing exit here results in a system beep and the error message "no bootable devices"

---

### Post by oldfred on 2012-02-26
You may be able to manually boot, but Boot-Repair often is an easy way to fix things.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

Manual boot:
See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg
# that requires a valid grub.cfg, if not then directly boot from kernel
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux (hd0,1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,1)/initrd.img
boot

Do not know if it is just my screen or not, but commas are looking like periods. All (hd1,0) are with commas.

---

### Post by ijason on 2012-02-26
thank you for your quick reply! i have not yet tried your advice, because my ls command returns a different result than your walkthru indicated it should :<

> grub> ls
(hd0) (hd0,msdos1)
grub>

i have followed your walkthrough, despite the presence of "msdos" in my Grub prompt. 

all of the commands appeared to be accepted, and when i entered "boot" at the end the screen scrolled and scrolled and SCROLLED with what looked like errors, but eventually it looked more like a normal boot sequence, and finally ubuntu has shown up.

UNFORTUNATELY, after a reboot... i am again facing the grub> prompt. i am currently downloading the boot-repair disk.

---

### Post by oldfred on 2012-02-26
msdos1 & 1 are the same. I think the example I posted should work. But that is why I suggest Boot-Repair as it seems to automatically sort everything out. And if not then you can run boot info script so we can see details.

Grub started using the msdos to make it clear that it was msdos vs gpt. I use gpt on my boot drive with BIOS although gpt is only required for large drives over 2.2GB or 2GiB, or UEFI booting. But gpt is also suggested for Linux only and SSD drives, now since it is a new but only slightly better partitioning.  So my setting often is (hd2, gpt2).

---

### Post by ijason on 2012-02-26
thank you for your continued help :)

i have downloaded the boot repair disk, and rebooted the laptop with it. i chose the "repair automatically" option, and let it run the course. after ejecting the disk and rebooting i now see - briefly - a grub selection menu... with a regular sounding ubuntu version as the top option.

the top option selects itself after a few seconds and tries to boot. then it displays :
  error: out of disk.
  press any key to continue...

after a few moments ubuntu boots on its own, and things appear normal. any idea what my problem is?

---

### Post by oldfred on 2012-02-26
I think I have seen Boot-Repair fix that also.

Is this an older computer that has a BIOS that will only boot from the first 137GB of a drive?

You can easily test by using gparted from liveCD to shrink / (root) partition. Or reinstall with a 10-25GB / (root) partition and use the rest of the drive as /home.

If all fails to the link to  the boot-info script output that Boot-repair offers. We may or maynot see something else.

Some times BIOS settings like LBA not IDE make a difference.

---

### Post by ijason on 2012-02-26
alright.. i'm not entirely certain which (or if it was both) steps fixed the problem. but i took your advice and reduced the first partition to below 135gigs, and i re-ran the boot rescue cd,and things seem to be happy now.

the grub menu does show up for 7 seconds, but i'm not required to be at the keys to select anything other than the default. so no complaints there. i've rebooted a few times and everything seems solid

here are the results from the boot rescue output report

> grub2 is installed in the MBR of /dev/sda and looks at sector 1 of the same hard drive for core.img. core.img is at this location and looks for (,msdos1)/boot/grub on this drive

sda1:
file system: ext4
boot sector: type -
boot sector: info
operating system: ubuntu 11.10
boot files: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

i guess it's ok that boot sector type is listed as " - " ?

thanks again for your help.

---

### Post by oldfred on 2012-02-27
Glad you got it working.

Only in rare occasions is grub installed to the PBR partition boot sector, so empty boot sector is fine. Windows has to have a NTFS boot sector.

You can add a partition at the end of the drive to move /home to, or for data. Or just reinstall. I normally suggest a / (root) of 25GB and separate /home for the rest of the space you want for Ubuntu, and swap of  2GB or the size of RAM in GiB if you want to hibernate.

---

