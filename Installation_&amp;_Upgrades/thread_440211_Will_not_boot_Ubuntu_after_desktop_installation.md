---
title: "Will not boot Ubuntu after desktop installation"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by Red 5 on 2007-05-11
I finally took the plunge and am installing Ubuntu on my desktop, it has been a challenging but fun experience so far. 

I burned an image of the OS and was able to boot off of my CD-ROM drive, no problem. I ran the desktop installation and had Ubuntu completely format my hard-drive so that Ubuntu is the only OS on my computer. 

When the installation completed, it told me to continue using live CD or to restart. I clicked on restart but my computer hung without actually restarting.

I power-cycled the machine and removed the live CD. Ubuntu does not boot. I can put the live CD back in and it boots fine, but it will not boot from my HD.

Any information is greatly appreciated.

---

### Post by Ateo on 2007-05-11
When you reboot, do you seen *ANY* activity on the screen? Do you get to the grub screen? Do you get a kernel panic? Any more information would be helpful.

---

### Post by Red 5 on 2007-05-11
It is an HP computer, I see the HP splash screen that gives me the option of going to the boot menu, help, etc. then it goes to black screen.

No error message that I saw.

---

### Post by Red 5 on 2007-05-11
I went home for lunch and tried changing the boot order to HD first and CD-Rom second.

I restarted the machine and saw the following.

HP Splash screen - ok
Message indicating that GRUB was loading - ok
Ubuntu Splash Screen with "loading" bar that shows loading progress. 
   The loading bar completely fills up and then goes to the following.
A static looking "task bar" looking thing shows up on the bottom of the screen.
The cursor shows up on the screen as a spinning wheel that seems to indicate something is loading.
Then---- black screen, nothing happens.

Again, any information is appreciated.

---

### Post by jtnoob on 2007-05-12
I am having roughly the same problem. I get "grub error 15". Do you know what that means?

thanks

---

### Post by bulldog on 2007-05-12
> **jtnoob said:**
> I am having roughly the same problem. I get "grub error 15". Do you know what that means?

thanks

[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)

@Red 5,
What kind of graphics do you have?
Can you boot into recovery mode,and perform```
sudo dpkg-reconfigure xserver-xorg
```
to see if this changes some thing?

---

### Post by jouke on 2007-05-12
GRUB BOOT ERROR

After rebooting after installing Ubuntu 7.04 I got the following message:

"GRUB BOOT ERROR". I could only boot through the CD.

After trying all kind of things, just to get things back to work I gave up and bought a new harddisk, a Samsung ATA SP1654N with 160Gb. I connected the harddisk on the first IDE connection at the motherboard; selected the CD-rom as first boot device; booted from a 7.04 Feisty Dawn Kubuntu live CD, and installed it.

After rebooting after the fresh new install, telling the partitionmanager to use the whole disk (for linux and swap), I was veryu supprised meeting the same message again: "GRUB BOOT ERROR". I was stunned! 

The next actions were for me 'the solution'.

Starting with giving me the root -privileges:
root@my-machine:/# sudo -s

After gaining more rights I tried to find out how the linux and swap -partitions were mounted by:
root@my-machine:/# fdisk -l

This gave me..
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             614       19457   151364430   83  Linux
/dev/sda2               1         613     4923891   82  Linux swap / Solaris

Partition table entries are not in disk order

Then I removed the MBR (Master Boot Record):
root@my-machine:/# dd if=/dev/zero of=/dev/hda
 bs=446 count=1
1+0 records in
1+0 records out
446 bytes (446 B) copied, 2.6382e-05 seconds, 16.9 MB/s

root@my-machine:/# dd if=/dev/zero of=/dev/sda bs=446 count=1
1+0 records in
1+0 records out
446 bytes (446 B)
 copied, 0.000246514 seconds, 1.8 MB/s

root@my-machine:/# dd if=/dev/zero of=/dev/hda1 bs=512 count=1
1+0 records in
1+0 records out
512 bytes (512 B) copied, 2.8364e-05 seconds, 18.1 MB/s

root@my-machine:/# dd if=/dev/zero of=/dev/sda1 bs=512 count=1
1+0 records in
1+0 records out
512 bytes (512 B) copied, 2.7552e-05 seconds, 18.6 MB/s

Note that I executed the commands for hda and sda. I just was not sure, but thought sda should be enough. Anyhow, just deleted as much as I could.

Finally I re-installed the MBR again by:
root@my-machine:/# grub-install /dev/sda

It gave me a happy message:
Installation finished. No error reported.

This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)  
 /dev/sda

It all left me with a few remaining actions to do:
root@my-machine:/# grub
Probing devices to guess BIOS drives. This may take a long time.
root@my-machine:/#             

Entering the GRUB -shell, I typed:

grub> install (sda,1)/boot/grub/stage1 d (hd0) (sda,1)/boot/grub/stage2 p (sda,1)/boot/grub/menu.lst

Note: You should open another terminal window and locate your grub/menu.lst, using the 'find' command.

I rebooted and the problem was solved!

---

