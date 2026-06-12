---
title: "boot problems after first update."
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by anklebone12 on 2010-03-07
Hi!

After installing 9.10 without a problem, I went to install all the updates and before the updates were finished, it asked me to restart the computer to finish. so i did. now when i try to boot, after selecting the top option on the Grub screen i something that looks like this:

fsck from util-linux-ng 2.16
 /dev/sda1: clean, 149168/7143424 files, 101022/28559545 blocks
init: udevtrigger main process (444) terminated with status 1 init: udevtrigger post-stop process (447) terminated with status 1
 init: udevmonitor main process (443) killed by TERM signal
 init: networking main process (448) terminated with status 1


I'm now booting from the live cd. can anyone help me? I did some googeing and it looks like some other people had the same problem.


what they claim works is doing this in the Terminal form the live cd:


  "1. - Download/grab a live cd.
 2. - Start live cd and when it loads the desktop open a gnome-terminal.
 3. - Create this dirs:
 **sudo mkdir /media/karmic**
 **sudo mkdir /media/karmic/proc /media/karmic/dev /media/karmic/etc**
 4. - Mount your linux partition (for me sda1):
 **sudo mount /dev/sda1 /media/karmic**
 5. - Bind the dirs:
 **sudo mount -o bind /proc /media/karmic/proc**
 **sudo mount -o bind /dev /media/karmic/dev/**
 **sudo mount -o bind /dev/pts /media/karmic/dev/pts**
 6. - Copy this file
 **sudo cp /etc/resolv.conf /media/karmic/etc/resolv.conf**
 7. - Update your real linux partition with chroot:
 **sudo chroot /media/karmic apt-get update**
 8. - Upgrade your real linux partition with chroot:
 **sudo chroot /media/karmic apt-get dist-upgrade**
 9. - If you have some broken package:
 **sudo chroot /media/karmic apt-get -f install**
 10. - Reboot and voilá! Fixed for me."


when I get to 7, a bunch of text comes up with this at the end:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 



that line keeps coming up when i try to continue with the steps.

I tried sudo dpkg --configure -a and i still get the same problem when i try to continue with the steps. 



Any suggestions/tips would be nice. maybe a completely other way to fix this problem.
Thanks.

---

### Post by tom4everitt on 2010-03-07
You should probably run:

sudo chroot /media/karmic dpkg --configure -a

in case you missed the chroot thing.

---

### Post by anklebone12 on 2010-03-07
> **tom4everitt said:**
> You should probably run:

sudo chroot /media/karmic dpkg --configure -a

in case you missed the chroot thing.


It says command not found.

---

### Post by anklebone12 on 2010-03-07
> **anklebone12 said:**
> It says command not found.

nevermind, I entered misspelled the command.

---

### Post by tom4everitt on 2010-03-07
I almost suspected that :) Let me know how it proceeds

---

### Post by wolterkabolter on 2010-03-11
I tried this, but the file /etc/resolv.conf seems not to exist. Can anyone help me out here?

I decided just to continue, and got to the end. But it did not work anyway. Any one knows how I can remove kernel update 2.6.31-20?

---

### Post by garvinrick4 on 2010-03-11
etc/resolv.conf is for your internet connection.

Just mount karmic and open in root so you can save to etc/resolv.conf

open your live cd file of etc/resolv.conf at same time and copy and paste it
to the karmic etc/resolv.conf and save it.

You will now be able to have internet access. If you were wired would not have to do this step only for wifi access. 

You are using the Label of karmic in command line. You did Label the partition karmic didn't you. 

Once you have directory and mount the sudo chroot /media/karmic will give you root access and will say root at command line.

Line 6 should make a copy of etc/resolv.conf to karmic but sometimes I have to do it the old copy and paste.

---

### Post by cesium62 on 2011-04-19
This works for me.  My notes on the slight differences:

* I downloaded the live CD.  When booting from the live CD I was offered the choice of "trying" ubuntu or installing.  I chose "try".

* I used System::Administration::Disk Utility to display and mount my hard disk drive.

* I initially skipped over step 5 thinking it wasn't necessary because of the way I had mounted my drive.  This step basically overlays dynamic parts of the file system on top of locations in the hard drive.  Don't skip this step.

* The apt-get dist-upgrade step failed for me with an error stating that /boot/vmlinuz-2.6.32-30-generic could not be found.  I ignored the error and successfully rebooted from my hard drive.


For me, I got into this problem by starting up an upgrade on one account, then switching to another account while letting the upgrade run in the background.  A couple of days later (I had forgotten about the upgrade), a power failure during a storm caused the computer to reboot.  It would be nice if the software upgrade could be more safely staged so that we could recover without having to burn a live cd.

---

