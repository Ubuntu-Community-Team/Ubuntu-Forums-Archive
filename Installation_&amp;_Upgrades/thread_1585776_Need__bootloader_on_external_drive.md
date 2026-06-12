---
title: "Need  bootloader on external drive"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by rfbeck on 2010-10-01
I recently installed Maverick RC to a partition on my external drive.  
  Following the GUI, I used the advanced option and installed the bootloader to "sdb" and had Maverick install to a partition on the external drive (I want the GRUB to be on the external drive so I can boot directly into Win7 when I don't have the external connected). And, to note, I did set my BIOS to boot from the external drive first, I have that option in my BIOS.
  So, when I finished installing, I rebooted and all I got was a "-". Not even a "disk not bootable message". It just hung at "-" .
Okay, so help me! Thanks folks. :)
______
Robert

---

### Post by dino99 on 2010-10-01
So what is your choice ? either let w7 bootloader drive both w7 and ubuntu, or set grub-pc to drive both .

hdds: be sure of their names: fdisk -l

about hanging, i guess grub2 dont find its path, look for the partition name: first disk=0, first partition=1 (/dev/sda1)

sudo grub-install /dev/sda
sudo update-grub 

see grub guide below for more explanations

---

### Post by rfbeck on 2010-10-01
Okay, I'll give that a shot and report back in thirty minutes! 
______
Robert

---

### Post by oldfred on 2010-10-01
If you want to know where everything is installed for booting this script helps:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by rfbeck on 2010-10-01
Hi Oldfred,
I actually do know where all my devices are, and where all the partitions are. I used the following method to try to get GRUB on my external:

sudo mount /dev/sdb2
sudo grub-install --root-directory=/dev/sdb /media/"some long number"
sudo umount /dev/sdb2
Or words to that effect. The grub message indicates success. But, my external drive will not boot into it. Should I chmod the /dev/sdb? Some posts about this topic indicate that I should.
Thanks for any help.
______
Robert

---

### Post by wilee-nilee on 2010-10-01
> **rfbeck said:**
> Hi Oldfred,
I actually do know where all my devices are, and where all the partitions are. I used the following method to try to get GRUB on my external:

sudo mount /dev/sdb2
sudo grub-install --root-directory=/dev/sdb /media/"some long number"
**sudo umount /dev/sdb2**
Or words to that effect. The grub message indicates success. But, my external drive will not boot into it. Should I chmod the /dev/sdb? Some posts about this topic indicate that I should.
Thanks for any help.
______
Robert

I'm not sure your commands are correct follow this link, you were close, you don't have to run the unmount command. From a live Ubuntu cd with grub2.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

To install the W7 bootloader back to it's HD if needed; one command generally, using a install or recovery W7 disc at the repair command line.
Code:BootRec.exe /fixmbr

Basically just use the first method of the 3 offered for reloading grub the next ones are chroot and chmod commands probably not needed.

---

### Post by oldfred on 2010-10-01
This is what I have as the way to install grub to sdb.

Install MBR from LiveCD, Ubuntu install on sdb2 and want grub2 in drive sdb's MBR:
Find linux partition, change sdb2 if not correct, and/or even sdb if sda wanted:
sudo fdisk -l
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb

Then in BIOS set to boot from external drive.

Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
 HOWTO: Purge and Reinstall Grub 2 from the Live CD - drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by rfbeck on 2010-10-01
Hi again,
Okay I used the first method and it went smoothly until I rebooted (to live CD). 
When entering "sudo update-grub" I got the following error:
/usr/sbin/grub-probe error: cannot find a device for / (is /dev mounted?).
After that I just tried to boot to the external (by setting the BIOS to first boot exteranl) and it went ahead and booted off my internal drive instead (Win7).
I'm fixin' to give up. Perhaps my computer (VAIO VPCF115FM) just can't boot from an external hdd.
What's with the grub-probe error?
Thanks
______
Robert

---

### Post by drs305 on 2010-10-01
Re the grub-probe error:

When you attempted to update-grub via the LiveCD, had you accomplished the chroot procedure first? Otherwise you are attempting to update-grub on the LiveCD files, which will do no good. The way to make a change on your real installation files is to first mount your Ubuntu partition, chroot into it, and then run the commands.

There is a link to how to chroot in my signature line. You wouldn't use the purge and reinstall portion but it would supply the commands necessary to use the chroot procedure.

---

### Post by rfbeck on 2010-10-01
Okay,
I've done exactly as you two (oldfred and DRS305) have said. I don't get any errors (except "host ubuntu unresolved"). But other then that, everything is groovy.I get an a-ok message at each step.

But when I set the BIOS to boot from the external HDD, it just hangs with "-". Could this have to do with my external HDD being on a eSATA port? I think I might have a defective BIOS. 

I'm considering installing Maverick on my internal drive, just like I used to. Not really the best situation for me, but whatever works...
Any other suggestions for getting my external HDD to boot?
Thanks,
______
Robert
ps- some suggest disconnecting the internal drive when installing Ubuntu to an external drive. Is this necessary?

---

### Post by oldfred on 2010-10-01
Is it really halting before grub or after. If you only have one system, grub bypasses the menu unless you hold down shift key from BIOS until menu appears.

On my system first boot puts monitor to sleep unless I remember to add nomodeset to the end of the linux line in place of quiet splash. Then I have to install nvidia driver to get boot to work normally.  Did you system work ok with the liveCD or did it show any issues? What video driver do you have?

---

### Post by rfbeck on 2010-10-02
Well, the Live CD works fine. I have Win7 installed on my internal drive. I did make one change- I removed the USB Flash stick before attempting to boot, feeling that was what was keeping my eSATA HDD from booting. Now it doesn't hang anymore, but instead boots into Win7 (which is the second thing I've set my BIOS to boot- internal drive).
I have an NVIDIA chip, but it works okay with the Live CD. Maybe an eSATA drive can't boot... I don't know.
______
Robert

---

### Post by drs305 on 2010-10-02
With everything connected with the external connected, please run the boot info script now that you have tried to install G2 on the external.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

Please paste the contents of RESULTS.txt between "code" tags, which you generate with the # icon in the post's menubar.

---

### Post by oldfred on 2010-10-02
Grub defaults to install to sda, sometimes the flash drive is sda. Not sure how esata may be numbered. This is why boot script helps us understand what is where. Plug flash back in and run the boot info script.

---

### Post by efflandt on 2010-10-02
I have not used eSATA, but even if you try setting your BIOS to boot from USB or CD/DVD first, many PC's still boot from internal drive unless you press a specific key during BIOS splash screen to select boot device.  That is probably to avoid accidentally booting something unknown.  The only virus I ever caught was spread by floppy disks long ago.

I have not installed 10.10 RC from scratch (just upgraded beta to RC).  But when I installed 10.10 beta and put / on a USB drive, I was pleasantly surprised that install automatically defaulted to putting grub on the USB drive.

So maybe you just need to press something during the BIOS splash screen to select boot from the eSATA drive (unless subsequent tampering has broken that or having USB stick inserted during install from CD confused something).

---

### Post by rfbeck on 2010-10-02
But anyway, the point is moot. I have decided to install Musky Meerkat on my internal drive. I just need to make room for it. It's all good. Thanks for the help folks. I learned a lot.
______
Robert

---

