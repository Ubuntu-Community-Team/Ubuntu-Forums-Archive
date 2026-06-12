---
title: "Failed Install of Ubuntu Netbook Remix 9.10"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by Marfish on 2010-01-31
For the past few days I've been trying to get the newest netbook remix of ubuntu installed on my netbook; However, I've been running into a lot of problems. The first install didn't seem to go so bad, but when trying to boot up, a simple message of "GRUB" came up on the top left hand corner and nothing else. I tried to install it again, but on the external SD card (it's an acer aspire one, so it had an 8 gb SD card for a hard drive as well), but came up with the same message as before. On the third try, it got even worse, with a failed install on the main SD card, with a message saying "The attempt to mount a file system with type ext4 in SCSI2 (0,0,0), partition #1 (sda) at / failed". I'm at a loss of what to do, can anyone help me out?

---

### Post by Marfish on 2010-01-31
*bump*

---

### Post by MartyBuntu on 2010-01-31
During the setup, are you using automatic partitioning?

---

### Post by Marfish on 2010-01-31
I completely formatted the disk and asked it to use the whole HDD.

---

### Post by Marfish on 2010-01-31
*bump*

---

### Post by Freshmeadow on 2010-01-31
Hi from Guelph Ontario. This is what worked for me and several other people on Asus EEE PC's. I know you have an Acer, but this may work for you. I installed another OS on my SSD drive first (Jolicloud in this case) , and then UNR 9.01 installed over it with no freezes in the partitioning window. When I formatted the SSD first and removed the OS, UNR froze in the partitioning window. Apparently there is a bug in the installer.
Hope this helps.
Also, some people replaced the new grub-pc in UNR 9.01 with the older package, grub. However, replacing grub can be very tricky. Do a Google search on replacing the grub-pc bootloader in 9.01.
Good luck.

---

### Post by Marfish on 2010-01-31
Thx, I'll give it a shot.

---

### Post by theaskanison on 2010-02-01
I also had the same problems with my Acer Aspire one ZG5.

1st, I had the error message about portioning my hard disk. Then I read in a another thread that the trick is to partition your HD leaving some free space (258MB) at the beginning of the disk. This worked! and I was able to start installing...

It all went well until when I was about 90% when the error message :"the program "ubiquity" closed unexpectly- pop up. I tried a second time and the same error showed up at 80%. So I decided to install Ubuntu 8.10 (using the same free space trick on my HD) and the installation went thru. 

Keep in mind that when trying to install remix, the Ubuntu disk partitioning utility under remix would crash and I had to re-boot under a 8.10 live version to use the disk partitioning tool there, re-format my HD (with the free space at the beginning) and then switsh to Ubuntu remix live boot to try and re-install. Regardless, the installation failed at the end as I said before.

Now from 8.10 I'm Upgrading to version 9.04. I wonder if I can upgrade to remix from there?

Hope this helps

---

### Post by usagi247 on 2010-02-01
I have a Toshiba NB205 and currently have an ill-functioning Linux 7 running on it.  I just created a bootable flash drive for Ubuntu Netbook Remix 9.10 but I can't get it to actually boot.  I'm a complete noob and I've read that the problem probably has to do with partitioning.  According to the instructions I've been using, all I need to do is figure out what number the flash drive is and make it active.  Problem is, I can only find instructions for this using Windows, not Linux.  Help?

It could also have to do with attempting to boot this from a netbook that already has linux.  When I try to load the drive, I get a Disk I/O Error.  When I put the flash drive on my PC, it recognizes it as a bootable flash drive.

---

### Post by jwm93k on 2010-02-17
I have a new twist on the 9.19 UNR install. I have a Asus eee 901. I have installed from the USB but I didn't like the partitions. I reinstalled with new partitions but they started to fill up after time. I wanted to do another install and change my partition sizes. I booted to the USB with UNR. Good so far. I clicked on Install. Then it looked like it was busy for a minute and then nothing happened. I used gparted to remove the old partitions and format the old hard drives and still it will not install. This is the same EEE using the same USB with the same UNR to do the same install, but no fun. The I click on install, I used both run live, and install (seem to be the same affect) from the boot menu. The USB boots, but when I click on the install 9.10 icon I get nothing. No messages, no windows and no install. Do you have any ideas?

---

### Post by jwm93k on 2010-02-18
Greetings, In regard to the USB install I posted yesterday, here is more info. The 2G USB with the UNR image was not working. It had been created using the tool in Ubuntu to create a USB image. I had also used this same USB to install UNR(Ubuntu Netbook Remix) twice on a ASUS 901, and a Dell 10v. The ASUS loaded well both times it was just a matter of trying to get every thing to fit. The Dell 10v loaded well but it took more work to get the networking working. It seems I needed a restricted driver and needed to do this manually. The USB on the 4th install (3rd on the ASUS) would not work. The USB would boot, and software would run, but when I clicked on the install button nothing would happen. Initially I thought it saw that there was an updated 9.10 on the system already and stopped. I removed the partitions and it still would not install. Just to see what happens I went and recreated the UNR image on the same USB device. When I booted to the USB device, I was able to install UNR with no troubles. I don't know if there is a limit to how many times you can install from a USB or not. Regarding the ASUS 901, I wanted this to be my last install. The 4GB SSD was too small for Ubuntu after a few downloads and updates (even after running janitor and doing a clean). I choose to load the OS on the 16GB SSD (I don't know why there are two SSDs). This one is reported to be slower but it is larger. I made the 4G SSD by /home. I also had to change setting in the SETUP to boot to the 16G SSD. This was not straight forward but easy to figure out after spending some time in the SETUP Util. After one day my root and OS system size is 3.5GB. This would fill the 4GB SSD.
_**In summary **_if your USB bootable image will boot but not install, it might be your USB image.
I like my Asus 901 but the 4GB and 16GB SSD layout is annoying. I would prefer a hard drive. Happy Trails....

---

### Post by jwm93k on 2010-02-18
Sorry more data:
-I used gparted on the live USB to remove the partitions.
-The setting in SETUP(BIOS) had an affect on my booting. Before I made the SETUP changes the PC just looked at my other SSD and just gave me a blinking curser and nothing more. This may be affecting some of your issues at reboot. One thing to try is the boot from menu on the PC. How you get there on your PC is dependent on your PC. On my system I hit ESC during the boot-up. Then I can select where to boot from. If this works and you can boot to your SD, then the problem is most likely in you SETUP settings and not Ubuntu.
-System info under the Adm/system tools, under the file system tab (during a live boot) can give some good info on the current usage and formats of the installed SSD and Hard drives. I found this very handy. Sorry for being verbose.

---

