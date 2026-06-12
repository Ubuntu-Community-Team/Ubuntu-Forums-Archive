---
title: "Replacing Grub on Windows Drive"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by walt11 on 2012-05-05
I have Ubuntu installed on an external drive, XP-SP3 on my internal drive, and Grub installed in the MBRs of both the internal and external drives. I would like to eliminate Grub from my internal drive (sda) and boot into windows.

Looking back at help I received 2 years ago, oldfred advised using lilo from within Ubuntu:
    sudo apt-get install lilo
    sudo lilo -M /dev/sda mbr

Questions:
Will that still work? (I'm running Ubuntu 11.04).
I assume that will overwrite the Grub boot loader- or do I need to do something first to delete it?

Thanks

---

### Post by darkod on 2012-05-05
Yeap, that will work. I recommend to run it from live mode so that lilo package is not left installed on your real system. It won't be a big problem if it is, but why risk it.

---

### Post by walt11 on 2012-05-05
Thank you for that quick reply! Thanks also for recommending live mode. That's good advice.

---

### Post by walt11 on 2012-05-05
Problems!

During the lilo install process, this message appeared:[INDENT]It is absolutely necessary to run liloconfig(8) when you complete this process
execute /sbin/lilo after this
LILO won't work if you don't do this
[/INDENT]I don't understand the meaning of (8) after the liloconfig command. When I try to run liloconfig, I get the following message:[INDENT]WARNING!
Your /etc/fstab configuration file gives device
UUID=a2e1bfbd-43e9-4815-9977-0d6732326b79 as the root filesystem device. This doesn't look to me like an "ordinary" block device. Either your fstab is broken and you should fix it, or you are using hardware (such as a RAID array) which this simple configuration program does not handle.

You should either repair the situation or hand-roll your own /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig again to retry the configuration process.
[/INDENT]None of that means anything to me.

I tried this from a live CD first, and then, thinking it was due to that, tried it from my real system. The same thing happened in both cases.

Sorry that my understanding of this is so limited.

---

### Post by wilee-nilee on 2012-05-05
If you have that original post it should say you will se errors. Have you rebooted to see if you're up and running?

You need to boot from that HD, to check, you may know this already.

---

### Post by oldfred on 2012-05-05
Oldfred still recommends lilo as a Windows boot loader and ignoring the error messages. But you just install the part to the drive's MBR that is a boot loader.

In fact if you do not ignore them you may create bigger problems as lilo is a full boot loader and was around long before grub. It works somewhat like Windows in using boot flag and having boot code in the PBR or partition boot sector. But it does not check for primary partitions like Windows.

If you install the lilo boot code to the Windows partition boot sector it will prevent Windows from booting.

---

### Post by walt11 on 2012-05-06
Thanks to both of you. What I hear you saying is that in spite of the error messages, I should go ahead and execute the original command, as planned:
  sudo lilo -M /dev/sda mbr
Is that right?
I won't get a chance to try it until later, this evening in fact, and will let you know what happens.

Oldfred, you said that lilo "does not check for primary partitions like Windows". My drive has 2 bootable partitions: sda1 which is the Windows partition, and sda2 which is a restore partition containing all the original software. If I install lilo to sda as above, I'm assuming it will boot sda1 and not sda2. Am I correct?

---

### Post by darkod on 2012-05-06
You can have the boot flag on only one partition, because that's how windows bootloader knows what to boot. In this case it's on your windows partition, not recovery (it should be anyway).

You can see the partition and flags in ubuntu terminal with:
sudo parted /dev/sda print

That will print the list of partitions and will show where the boot flag is. It shouldn't be on your recovery partition because then it will boot the recovery process automatically.

---

### Post by oldfred on 2012-05-06
While I still recommend lilo, there is another way that has worked for many.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

I believe Yanni used syslinux as the boot loader to repair a Windows install. I think Microsoft prevents anyone else from using their boot loader, which to me seems wrong if you really are fixing Windows. And the boot loader code in the MBR is only checking for a boot flag and jumping to the PBR - partition boot sector. The only real difference is some differences in error checking and copyrights.

---

### Post by walt11 on 2012-05-06
Thank you all so much for your help. Oldfred, I used the Boot-Repair utility you suggested in your last post, and it worked well. I am now able to boot directly into Windows, with or without the external drive attached.

However, now I can't boot into Ubuntu on the external! I get the Grub menu (Grub version 1.98+20100804-5ubuntu3), but if I press the enter key, I get these messages:
  error: invalid extent
  error symbol not found: grub_os_area_addr
  (and that last line is repeated)
Also, the timeout is not functioning, and the arrow keys aren't functioning.

After I made the boot repair, the utility saved a boot info summary at [http://paste.ubuntu.com/972581/](http://paste.ubuntu.com/972581/)

I could try using the Boot-Repair utility on Grub, but I need you to tell me what I have to fix!

---

### Post by oldfred on 2012-05-06
Boot script says grub 1.99 is in MBR, but your error is from grub 1.98? Perhaps grub did not update completely?

I think you need to totally reinstall grub. Not sure about all the advanced features of Boot-Repair?

Manually:

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by walt11 on 2012-05-07
Thank you oldfred, once more. I purged and reinstalled Grub from the Live CD following the procedure you directed me to, and I can now boot into Ubuntu on the external.

There is one small problem remaining. Instead of seeing the Grub menu, I see a greyish screen (I think with fine vertical lines.) The menu is there, because when it times out, it boots into Ubuntu - I just can't see it.

---

### Post by oldfred on 2012-05-07
Is video ok once you boot?

Have you tried holding shift from BIOS until you get menu? Or does menu still not appear?

Grub also has some video modes, but is supposed to use the Ubuntu mode by default. (I think). 

gksudo gedit /etc/default/grub
Use this with your monitor size in /etc/default/grub, if you know it:
GRUB_GFXMODE=1024x768

Of with a gui
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

#To see video:
sudo lshw | grep -A 11 display
#Resolution:
xwininfo -root

---

### Post by walt11 on 2012-05-07
It works if I set GRUB_GFXMODE=640x480 rather than my monitor's resolution. Thanks for suggesting a modification there. I also installed the Grub Customizer you pointed me to (and used it to conveniently change the resolution).

As usual, oldfred, your help has been outstanding as well as timely, and has been much appreciated. I'm going to mark this thread solved, but I'm planning to upgrade, and that always causes me Grub problems, so I may be back. (But, you've given me several good tools to work with on my own!)

---

