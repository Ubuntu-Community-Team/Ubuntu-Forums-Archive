---
title: "Help booting"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by rs710i on 2007-09-15
Hi

I just put ubuntu on my computer, and after i install it i have to restart the computer (as says) and take the cd out.  When i do that it will say "GRUB...Error 21"  Then i shut the computer down and now i cant even start windows.  I have tried Ultimate Boot CD, and that didn't work eather.  I have a Gateway 700XL w/ 1 gb of RAM 2 hdd's one w/ 120GB of space, and one w/ 20GB (the 20GB is a SCSI, and that is the hdd that i am putting Ubuntu on).  If someone can help me bi-pass the error please respond to this.

---

### Post by Pumalite on 2007-09-15
Try Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
You can restore Windows with your installation CD: hit 'r' for Recovery>FIXMBR>FIXBOOT

---

### Post by confused57 on 2007-09-15
Pumalite's suggestion of SGD is an excellent idea.  You might also enter your bios setup and check that the Ubuntu drive's controller is set to "auto"...I had error 21 & discovered the slave drive controller was set to "off".

---

### Post by rs710i on 2007-09-15
alright...i got my computer working again, but i will have to use the super grub cd every time...is there a way that i could get the grub to be fixed so that i don't have to boot from the cd every time?

---

### Post by Pumalite on 2007-09-15
Read the documentation. There is a way to fix the problem permanently.

---

### Post by rs710i on 2007-09-15
thanks a lot for the help:)

---

### Post by Pumalite on 2007-09-15
You are welcome.

---

### Post by rs710i on 2007-09-15
I'm sorry to ask another question after i thought i fixed the problem, but the instructions say to...
   1.  boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3. Gnu/Linux
   4. Fix Boot of Gnu/Linux (GRUB)
   5. select your Linux partition
   6. see message, 'SGD has succeeded'
   7. you're done! reboot

I do steps 1-5 and then i get the message, "SGD has not Succeed" i dont know what to do after that iv tryed so many things and none of them seem to work.

---

### Post by Pumalite on 2007-09-16
Post:
sudo fdsk -lu
cat /boot/grub/menu.lst

---

### Post by rs710i on 2007-09-16
Are these the commands that i will have to preform to make my computer work?

---

### Post by Pumalite on 2007-09-16
Sorry, you have to boot with a Live CD, mount your partition and post those commands from the Terminal. The outputs are needed to see if I can help you in some other form.

---

### Post by rs710i on 2007-09-16
I tried to run "/boot/grub/menu.lst" but when i select my SCSI hdd (were Ubuntu is located and is my 2nd hdd) it responds with a message saying, "Nothing to do" i don't know if this means that i installed Ubuntu wrong, or did  i do something else wrong.

---

### Post by Pumalite on 2007-09-16
You probably didn't mount your partition right.There is Knoppix(mounts all partitions automatically): [http://www.knoppix.org/](http://www.knoppix.org/), burn the iso as 'image' to a CD, boot from it and you'll be able to access your system.

---

### Post by rs710i on 2007-09-16
Ok, but i put Ubuntu on a 20GB SCSI HDD, and i have a whole other HDD for Windows.  Is the SCSI the problem, or can Ubuntu support them?

---

### Post by Pumalite on 2007-09-16
Ubuntu supports SCSI that I know of. In any case, it doesn't matter where you put Ubuntu, Knoppix will pick it up.

---

### Post by rs710i on 2007-09-16
Ok...and it doesn't matter what cd version i download, they all should work?

---

### Post by Pumalite on 2007-09-16
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

Click 'Download'

You can choose your language and your mirror.

---

### Post by rs710i on 2007-09-16
And after i download this and burn it i just boot it and i should be fine or is there a prosess i have to go through?

---

### Post by Pumalite on 2007-09-16
No, you boot Knoppix, then go looking for the Terminal; there post the commands (taking into account where your partition is mounted), copy and paste the output here.

---

### Post by rs710i on 2007-09-16
So i booted the Cd and im in the Terminal Program, but now what do i do?

---

### Post by Pumalite on 2007-09-16
Sorry, it escaped me that you can boot into ubuntu with your Super Grub too. But now that you are in Knoppix, go to terminal choose the partition where Ubuntu is and post: cat /boot/grub/menu.lst

---

### Post by rs710i on 2007-09-16
I got the terminal program open, and i put the command, "sudo fdsk -lu cat/buut/grub/menu.lst"  this is the correct command to post right, i keep getting the response, "command not found"  Please notify my if there is an error in what i am typing.

---

### Post by rs710i on 2007-09-16
Okay im in the terminal program, but how do i select the partition/hdd that ubuntu is on?

---

### Post by Pumalite on 2007-09-16
Tere are two separate commands:
sudo fdisk -lu
cat /boot/grub/menu.lst (check your typo)

---

### Post by rs710i on 2007-09-16
i get the respond saying, "no such file or directory."

---

### Post by Pumalite on 2007-09-16
You are not accessing your partition. It must be in /media or /mnt

---

### Post by rs710i on 2007-09-16
knoppix@Knoppix:~$ sudo fdisk -lu

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   234436544   117218241    7  HPFS/NTFS

Disk /dev/sda: 18.3 GB, 18370117120 bytes
255 heads, 63 sectors/track, 2233 cylinders, total 35879135 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    34282709    17141323+  83  Linux
/dev/sda2        34282710    35873144      795217+   5  Extended
/dev/sda5        34282773    35873144      795186   82  Linux swap / Solaris
knoppix@Knoppix:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
knoppix@Knoppix:~$ sudo fdisk -lu

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   234436544   117218241    7  HPFS/NTFS

Disk /dev/sda: 18.3 GB, 18370117120 bytes
255 heads, 63 sectors/track, 2233 cylinders, total 35879135 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    34282709    17141323+  83  Linux
/dev/sda2        34282710    35873144      795217+   5  Extended
/dev/sda5        34282773    35873144      795186   82  Linux swap / Solaris
knoppix@Knoppix:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

These are the Commands that i preformed if they are wrong please tell me what my mistake is and how i can fix it-Thank you.

---

### Post by Pumalite on 2007-09-16
Forget Knoppix. Get in Ubuntu with your Super Grub. Go to terminal there and post the commands.

---

### Post by rs710i on 2007-09-16
So I should now boot Ubuntu using Super Grub?

---

### Post by rs710i on 2007-09-16
Should i boot using my Super Grub boot cd, or boot using my Ubuntu Boot cd?

---

### Post by rs710i on 2007-09-16
Im running Ubuntu, and im in the Terminal now what do I do, run the commands?

---

