---
title: "Grub rescue error after clean install 14.04.1 LTS"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by ibates on 2014-08-04
I run Windows on one HDD and am attempting to run Ubuntu 14.04.1 LTS on a separate HDD.  Previously I was operating Ubuntu 12.04 LTS on that separate HDD and have overwritten it with a new install.

The new install was made using the CD downloaded and burned and everything looked fine during the install.  Including the Grub updates.  Very few options were provided during the install, essentially choices about overwriting 12.04, or 12.04 and Windows.  The option to overwrite 12.04 was selected and that was pretty well the only input in the install.

However, upon booting, I receive a dialogue on a blank screen stating "error: no such device: f611205f-xxxx-xxxx-fdcd2d04239c grub rescue >"  The device ID is correct and has been checked in Disk Utility on an Ubuntu 12.04 prior to installing 14.04.1.

I have downloaded and burned Super Grub2 Hybrid 200s2 to a CD, but am a bit wary of how to use it.

I can boot to my Windows disc manually, but cannot boot to the new install of Ubuntu 14.04.1.

I am aiming for a Grub loader choice at boot up as I had previously.

Any ideas?

---

### Post by yancek on 2014-08-04
Using the Ubuntu 14.04 installation medium, go to the site below and read the instructions on how to use the bootinfoscript in the link in the Description box.  Then download and run the script and post the output, a results.txt file here.  This won't repair anything but will provide a lot of information which should help someone to help you. 

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by ibates on 2014-08-04
Bootinfoscript RESULTS.txt output:

Please note:

sda is the Windows XP HDD which is normally the secondary boot up disk.  
sdb is the Ubuntu 12.04 HDD which I am using at this moment but which itself has a boot problem following an automatic graphics update, which is the reason for upgrading to Ubuntu 14.04.1
sdc is the Ubuntu 14.04.1 HDD which I am attempting to setup as primary bootup disk but which results in the grub resue error message described in my first post.

All other HDD and other drives are peripheral and have no bearing on this issue.

---

### Post by yancek on 2014-08-04
Wow!  Nice collection of kernels you've got there.  I see you have Grub2 installed to the mbr of four drives.  The 14.04 is on sdc, the grub equivalent would be (hd2,3) yet your grub.cfg file on sdc1 shows it as (hd0, msdos1).    The grub.cfg shows in the os-prober on sdb1 grub.cfg as (hd0, msdos1) while the other entries above it in that same file show Ubuntu on (hd3,msdos1).  I'm not sure which drive you are booting from.  If it is sdc, then the entry is not correct as it is showing (hd0,msdos1).  sdc1 should have the grub entry as (hd2, msdos1)  Have you swapped drives, removed/replaced or changed boot order?

---

### Post by ibates on 2014-08-05
Yoou are absolultely correct.  There is a fine collection of kernels.  If I knew how to housekeep them away I would certainly do that.  But I might just wait until this matter is cleared up, then most will simply go away by removing this HDD.

HDD sdb is in fact a removable drive physically mounted in a removable tray.  When I installed sdc (14.04.1) which is a stand alone permanently installed HDD, the HDD which shows here as sdb was not in the machine.  It has simply been reinserted in order to boot up Ubuntu.  Without it I cannot do that as sdc is the disc I am attempting to run as my permanent Ubuntu HDD.  When it is up and running (i.e. when this problem is solved), sdb will be permanently removed and reformatted for other use.

I can access sdc after booting on sdb through "home" folder; I simply can't boot from it.

In its previous life, the HDD which is now sdc was also an Ubuntu 12.04 disc, but for some reason , it became unusable in that, one day, it simply became unbootable.  Despite many attempts to correct the problem, including a series of discussion on this forum, I was never able to get it to boot up.  It started to boot, but always "hung" halfway through the bootup.  It was for this reason that I chose that disc for the installation of 14.04.1.  I did not re-format it, but simply installed 14.04.1 over the top of what was on it.  Should I have formatted it first just in case something continued to reside on the disc?  Could that in some way be the cause of this problem?

Is any of this making sense?  Can you see a solution to the problem?

---

### Post by yancek on 2014-08-05
Before doing any of the steps below, make sure you have a pen and paper handy to make a note of what exact changes you made and later note the results. 

You say you are booting from the drive labelled sdb.  If that is the case and you have 14.04 on sdc1, boot and when you see the grub menu, tap the 'e' key on your keyboard to edit.  You should then see the menuentry which is in the grub.cfg file.  Use the arrow key on your keyboard to move down to the line below:

```
set root='(hd3,msdos1)'
``` 

Change that to:

```
set root='(hd2,msdos1)'
```

Grub2 counts drives from zero and partitions from one.  The first entry above is pointing to sdd1 which you don't have, the second to sdc1 which you do.  If you scroll down in the bootinfoscript output until you get to the sdc1 information, you will see that its grub.cfg file points to sda1 (hd0, msdos1).

Another thing you can try is changing the boot priority to each drive and trying them all to see if any work.  Not sure where you installed Grub when you installed 14.04, the default is usually the first internal drive which would be the windows drive and according to the script, it does have grub2 installed.

If this works, it is a one-time thing, editing the boot menu so you need to record what you do.  If the first change I suggested works, you will need to enter that change in the grub.cfg file and then copy that menuentry to the /etc/grub.d/40_custom file as root and save the change then run:  sudo update-grub.

---

### Post by oldfred on 2014-08-05
If not booting from sda, then the BIOS drive order gets messy.

The boot drive is always hd0.

In my case I skipped a SATA port on my motherboard and if I plug in  a flash drive it is sde. But if I reboot it is sdb. But I boot from sdd, normally and that is hd0, so sda then becomes hd1 etc.
Sometimes I get so confused I just keep trying different numbers till it works. Old part of oldfred? :)

Error seems like it may be booting from a grub in a drive that is looking for the old install and new grub is in another drive.
If you use any of the default installs, it always installs to the drive seen as sda. But that can vary as some systems promote a flash drive to sda (perhaps a skipped port).
Always best to use Something Else and specify that grub is installed to the same drive as install.
And do not run autofix in Boot-Repair as it installs one grub to all MBRs. You may want different boot loaders in every MBR.

---

### Post by ibates on 2014-08-06
I am afraid you have unwittingly identified the nature of the problem.

I cannot edit anything in the grub menu because I do not get any grub menu.

At the completion of the BIOS routine, the first and only thing I am getting is the error message detailed in the first post of this thread.  There simply is no grub menu.

In fact, the only way I can access my Windows HDD is to insert this Ubuntu 12.04 HDD, select Boot Menu, and after the BIOS routine, I then select the Ubuntu 12.04 HDD, which in turn does give me a grub menu such that I can then select Windows.  But the Ubuntu 14.04.1 HDD is not shown on this list.

The only way I can access the `14.04.1 HDD is to boot up on this 12.04 HDD and then select the 14.04.1 HDD from the home menu.  There is simply no way I can boot to that HDD.

For your information I am attaching a copy of the grub.cfg file, compressed.  You will note that the device ID given in the grub rescue error message does not appear in the grub.cfg file.

I hope this sheds a bit more light on what is goiong on, or more to the point, what is not going on.

---

### Post by yancek on 2014-08-06
>  I then select the Ubuntu 12.04 HDD, which in turn does give me a grub  menu such that I can then select Windows.  But the Ubuntu 14.04.1 HDD is  not shown on this list.

You indicated in an earlier post that you did not have this drive containing 12.04 attached when you installed 14.04 so there would not be a 14.04 entry on it.  Boot to this system and run:  sudo update-grub and watch the output to see if you get an entry for the 14.04 drive with the newer kernel of 14.04.  If you get it, reboot with the same drive and try selecting the 14.04 entry to see if you can boot to it.

---

### Post by oldfred on 2014-08-06
If you are able to boot into your system even with the work arounds, it is easy to reinstall grub to the MBR of that drive only.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb

Grub also remembers where to reinstall on major updates. You need to make sure it reinstalls to correct place and reset if not correct.

 [http://askubuntu.com/questions/503417/how-to-prevent-ubuntu-from-overwriting-grub-bootloader-after-update/503446#503446](http://askubuntu.com/questions/503417/how-to-prevent-ubuntu-from-overwriting-grub-bootloader-after-update/503446#503446)
#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc(BIOS) or dpkg-reconfigure grub-efi-amd64 (UEFI)
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by ibates on 2014-08-09
To oldfred:


While seemingly impatient, I have been continuing to work my way through this issue.  This is the latest.

I re-installed Ubuntu 14.04 LTS, note: not 14.04.1 LTS.  (I did this mainly to see if the installation program would give me the option of overwriting the 14.04.1 at installation.  It didn't).

So now I have 14.04 LTS installed.  And at boot-up, I am getting a Grub menu, but an irregular Grub menu (which by the way goes nowhere upon selecting the Linux option).

Whereas in the past, at the Grub menu the Linux option always contained the latest kernel details in first line.  Now, I am getting no reference to a kernel, simply the word Linux.  (I can't remember for sure, but it might say "Ubuntu".  And the saecond line is the same with "Recovery mode", also with no kernel details.  There are then the memtest lines, and a line for Windows, and a line for 12.04, with kernel details.

As I said, selecting the first line, "Linux", leads nowhere and I receive a message to the effect that " ...gave up waiting".

Any further suggestions you can give would be greatly appreciated.

For information: this thread is now finished, and it has been overtaken by a newer thread of mine in Genel help > Problems installing 14.04.1

---

