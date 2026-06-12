---
title: "Can I copy/paste GRUB menu entries from openSUSE 10.3 ??"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by Average_Joe on 2007-11-11
Hello --

For a good year or so, I have used the Ubuntu GRUB boot loader to be able to triple-boot Ubuntu, openSUSE and Windows.

Recently though when openSUSE went to version 10.3, and very shortly thereafter, a new kernel (for 10.3), it seems that Ubuntu's GRUB boot loader can't grab the correct and current boot entry for the new boot kernel of openSUSE 10.3 .

Since openSUSE's version of GRUB doesn't find Ubuntu *at all* ... I am forced to either give up on one or the other operating system.  That's a shame because I have enjoyed triple booting for a long time, up until just here recently.

So here is my question.  Below, you will find the current, working, loadable kernel entries from GRUB-YaST2, which is openSUSE 10.3 boot loader.  (I repeat here, that if I now apply an Ubuntu GRUB loader on top of this one, it just fails to find the new and current 10.3 kernels.)

Please look below.  Can I copy these lines from below, and place them into the menu.lst for Ubuntu, and will that work to be able to have a corrent entry for booting openSUSE?  Thanks so much.

 
```
###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 10.3 - 2.6.22.12-0.1
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.22.12-0.1-bigsmp root=/dev/disk/by-id/scsi-SATA_ST3250823AS_3ND168TT-part7 vga=0x31a resume=/dev/sda5 splash=verbose showopts
    initrd /boot/initrd- 2.6.22.12-0.1-bigsmp

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 10.3 - 2.6.22.12-0.1
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.22.12-0.1-bigsmp root=/dev/disk/by-id/scsi-SATA_ST3250823AS_3ND168TT-part7 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd-2.6.22.12-0.1-bigsmp
```

---

### Post by meierfra on 2007-11-11
Copy and pasting those items should work. 

But I recommend a different method:
 Add this to you ubuntu menu.lst

title Suse
configfile (hd0,6) /boot/grub/menu.lst

If you select "Suse" in the Grub meny, this will load you Suse menu.lst.  (If you set  "timeout 1" in the  Suse menu.lst"  you will hardly notice that a second menu is involved and still have time to switch to recovery mode if ever needed.)

I prefer this method, since you won't have to change your menu.lst after Suse kernel upgrades.

---

### Post by hal8000 on 2007-11-11
Another way is to create symbolic links in the /boot directory of Suse.

The next time you load Suse 10.3, open a terminal and type:

cd /boot
ln -s vmlinuz-2.6.22.10-0.1-bimsmp vmlinuz
ln -s initrd-2.6.22.10-0.1-bigsmp

Now you have two symlinks, vmlinuz and initrd.  These are pointing to the newest and most recent kernel and initial ramdisk in Suse.

Whichever system you use to boot Grub, modify the menu.lst entry for Suse


Sample menu.lst
--snip--
#Suse section only
title openSUSE 10.3 - 2.6.22.12-0.1
    root (hd0,6)
    kernel /boot/vmlinuz root=/dev/disk/by-id/scsi-SATA_ST3250823AS_3ND168TT-part7 vga=0x31a resume=/dev/sda5 splash=verbose showopts
    initrd /boot/initrd


Each time you uprade Suse (but only if the kernel has been upgraded) change the symlinks to reflect the new kernel and initrd

---

### Post by Average_Joe on 2007-11-11
Two awesome, awesome methods to fix the problem for a more longer time period.

Thanks gentlemen !!  
This is exactly the better kind of solution existed !!

- Average_Joe

---

### Post by Average_Joe on 2007-11-11
Well, interesting, the method of meierfra didn't work.  It gives an error consistently, and meierfra I wondered if you couldn't double check for spelling etc. in your post above.  Perhaps there is a small tweak which would get it to work?

After that failed, I tried my original idea which was to simply copy/paste the menu.lst entry from openSuse 10.3, into the menu.lst of Ubuntu GRUB.  That also failed.

I'm now going to try to use hal8000's method, but if you can imagine anything I may have done wrong, please let me know, or tweak it and I will try it, I promise!

Thanks!!

---

### Post by Average_Joe on 2007-11-11
Well, heck -- all three methods have failed to work.
There must be something more to the story after these recent opensuse 10.3 kernel updates??

I should mention more about the above -- that all three methods failed when trying to make Ubuntu GRUB the boot loader.  

So now I will reverse the process and see if I can get the opensuse grub to boot up Ubuntu, instead.

I'll let you know.

I'm also wondering whether if I installed opensuse 10.3 on my secondary sata drive, if that would be easier in the end...?

---

### Post by meierfra on 2007-11-11
My bad: it is supposed to be

title Suse
configfile (hd0,6)/boot/grub/menu.lst

that is there is supposed to be NO space between (hd0,6) and /boot.

This should get you to the Suse Grub menu. But since the other methods failed I would expect  that something  will go wrong after you select  Suse from the "Suse Grub Menu".  Please inform us of any kind of error messages you might get.

I don't think installing Suse on the secondary drive will make things any easier. I'm booting Windows XP, Suse 10.3, Feisty  and Gutsy  all on one drive with no problems at all.

---

### Post by Average_Joe on 2007-11-13
meierfra --
Your solution with the correct syntax worked great.  Thanks for helping me.

For future readers:

You want to triple boot openSuse 10.3, Ubuntu 7.10, and a Windows version.  You want these on the same hard drive but in separate partitions.

(1)  Install Windows
(2)  Install openSuse 10.3
(3)  Install Ubuntu 7.10
(4)  Add the following (solution by meierfra) to the /boot/grub/menu.lst of your Ubuntu:
```
title Suse
configfile (hd0,6)/boot/grub/menu.lst
```

The following are Google search terms:
can't triple boot ubuntu 7.10 with opensuse 10.3 suse 10.3 opensuse won't boot ubuntu suse won't boot ubuntu won't boot opensuse 10.3 ubuntu won't boot suse 10.3 ubuntu 7.10 boot grub menu.lst menu

---

