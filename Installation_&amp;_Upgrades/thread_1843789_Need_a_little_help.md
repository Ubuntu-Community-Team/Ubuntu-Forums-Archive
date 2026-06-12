---
title: "Need a little help"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by eamonster on 2011-09-14
I am new to Ubuntu (linux in general) and I seemed to have run into a problem.  

Here is what happened:
A few days ago I bought a computer and decided I would like to Dual boot Windows 7 (already on the computer-I bought it used and it didn't come with the cd) and Ubuntu.  I first partitioned my HD then downloaded a dual boot program for windows.  After this I popped in the Ubuntu CD and downloaded it.  Once it fully downloaded it just went to a flashing purple screen and never actually loaded.  I then restarted my computer and went into the windows partition and repartitioned the HD back to just windows and saved the settings and restarted.  I got a message that says "Error: No such partition grub rescue?"  I couldn't get it to boot into windows and so I (probably a mistake) put in the Ubuntu CD and told it to download and replace the current OS and now it just sits at that damn purple screen again.  Any ideas?
Thanks.  Anything would help.

---

### Post by 2F4U on 2011-09-14
Are you saying you replaced Windows with Ubuntu, i.e. removed your Windows installation?

---

### Post by 2F4U on 2011-09-14
This article has some information about editing the boot menu:

[https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot](https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot)

You should remove the "quiet splash" entry so that any error messages during boot become visible. Also, could you provide the hardware specifications of the machine?

---

### Post by cebif on 2011-09-14
Did you try Live CD mode first, before the first install or installing and replacing windows? Can you boot up ubuntu in live mode now? Assuming the image you have on the CD can boot live.
If so is the screen still flashing purple?

---

### Post by cebif on 2011-09-14
> **eamonster said:**
> I then restarted my computer and went into the windows partition and repartitioned the HD back to just windows and saved the settings and restarted.  I got a message that says "Error: No such partition grub rescue?"
It looks like you left the grub boot sector on the computer HD. If you previously had a boot loader for windows and linux there was no need to install grub to the boot sector of the HD. In that case you would need to install it (grub) to the ubuntu "/" partition when you first installed ubuntu.

---

### Post by garvinrick4 on 2011-09-14
It is just a guessing game unless you use your Ubuntu Live CD (install cd using Try Ubuntu)
and run this boot script.
Download and extract to desktop. Make sure the file boot_info_script.sh is on Desktop:
Open a terminal and:
```
sudo bash ~/Desktop/boot_info_script*.sh 
```will give you a text file called RESULTS copy and paste here so we can diagnose problem and fix. After you copy and paste highlight whole thing and hit # sign in upper right of Message box so as to put in a nice box that is easy to read.

---

### Post by Aurauxis on 2011-09-14
I feel your pain.
I believe one of Ubuntu's weaknesses is that installation menus are not very clear. The first time I had installed Ubuntu it had overwritten everything and that was a pain. It is possible that Windows is still in your hard drive although unlikely.

If you had crucial data on your PC DO NOT install anything else leave it the way it is. Use testdisk to recover the data and possibly recover Windows along with it. If you are new to Linux I recommend that you find someone willing to help you. Teamviewer is excellent run it from LiveCD and we can directly help you fix your problem. For more information: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) 

If you just want Windows back it is likely that your PC came with a recovery disk. Use that to reinstall Windows although a note of caution your drivers will have to be installed at a later time and thats a pain. You may need to contact your ISP to set up the Internet connection on Windows before some of the drivers may install. This may take some time from past experience.

If you don't truly care for Windows let us know. Your (ubuntu) boot problem appears to be a driver issue. We can help you fix those. Are you using a Nividia GPU? I do not know much about them but they are rather infamous for causing problems.

---

### Post by jroa on 2011-09-14
>  I first partitioned my HD then downloaded a dual boot program for windows.

I don't know what you mean by "dual boot program for windows".  You do not need a dual boot program.  You just create a new partition and install Linux on it.


> Once it fully downloaded it just went to a flashing purple screen and never actually loaded. 

Did you check the checksum of the ISO image before you burnt the CD?  Did you check the CD after you burnt it?


> I (probably a mistake) put in the Ubuntu CD and told it to download and replace the current OS

Does your computer have a recovery partition?  If so, you can still probably repair Windows if you can access this partition.  I can help you do that, even if you do not have a recovery disc.

---

### Post by eamonster on 2011-09-14
> **garvinrick4 said:**
> It is just a guessing game unless you use your Ubuntu Live CD (install cd using Try Ubuntu)
and run this boot script.
Download and extract to desktop. Make sure the file boot_info_script.sh is on Desktop:
Open a terminal and:
```
sudo bash ~/Desktop/boot_info_script*.sh 
```will give you a text file called RESULTS copy and paste here so we can diagnose problem and fix. After you copy and paste highlight whole thing and hit # sign in upper right of Message box so as to put in a nice box that is easy to read.
 
 
I had to take a pic but this is what I got.  Hm.  I don't think it worked right.  Did I miss something?

---

### Post by eamonster on 2011-09-14
> **jroa said:**
> I don't know what you mean by "dual boot program for windows". You do not need a dual boot program. You just create a new partition and install Linux on it.
 
 
 
 
Did you check the checksum of the ISO image before you burnt the CD? Did you check the CD after you burnt it?
 
 
 
 
Does your computer have a recovery partition? If so, you can still probably repair Windows if you can access this partition. I can help you do that, even if you do not have a recovery disc.
 
 
 
I  may need your help with this.  I am not a fan of Windows but I would like to keep it until I figure Ubuntu out!

---

### Post by garvinrick4 on 2011-09-14
> **eamonster said:**
> I had to take a pic but this is what I got.  Hm.  I don't think it worked right.  Did I miss something?
Just forgot to put the boot_info_script.sh on the desktop is all.
If is still in .zip file right click on and open with archive manager and hit extract then extract again and will have the boot_info_script.sh just make sure is on desktop or drag and drop it there.
And run that line of code again. Should have gave you better instructions.

---

### Post by eamonster on 2011-09-14
> **cebif said:**
> Did you try Live CD mode first, before the first install or installing and replacing windows? Can you boot up ubuntu in live mode now? Assuming the image you have on the CD can boot live.
If so is the screen still flashing purple?
 
 
I did and still can boot into UBUNTU wiht the live CD.  It doesn't flash purple if I boot in that way.

---

### Post by eamonster on 2011-09-14
This is my system...
 
Intel i5 2500k
3.3GHz quad core
Sandy Bridge

8GB DDR3 memory

1TB Hard Drive

ATI Radeon HD 6850
1GB GDDR5 memory
DirectX 11

SuperMulti DVD-RW
HD Audio

---

### Post by YesWeCan on 2011-09-14
> **eamonster said:**
> I did and still can boot into UBUNTU wiht the live CD.  It doesn't flash purple if I boot in that way.
Boot the live CD, try without installing
open a console
type
[COLOR="DarkSlateBlue"]sudo fdisk -lu[/COLOR]
and see what your drive name is. It is probably /dev/sda, whatever it is use it in the next commands
[COLOR="DarkSlateBlue"]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/COLOR]

This replaces the standard MBR boot code and should allow you to boot Windows.

---

### Post by eamonster on 2011-09-14
> **YesWeCan said:**
> Boot the live CD, try without installing
open a console
type
[COLOR="DarkSlateBlue"]sudo fdisk -lu[/COLOR]
and see what your drive name is. It is probably /dev/sda, whatever it is use it in the next commands
[COLOR="DarkSlateBlue"]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/COLOR]

This replaces the standard MBR boot code and should allow you to boot Windows.

I am still unable to log in.  I get this message:

"Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key"

I know my windows 7 had a recover partition on the HD.  If I could only get to that I'm sure you guys could help me recover it.

---

### Post by Hakunka-Matata on 2011-09-14
Does this mean you cannot boot into liveCD/USB?  
If so, why not?, what happens?

---

### Post by eamonster on 2011-09-14
> **Hakunka-Matata said:**
> Does this mean you cannot boot into liveCD/USB?  
If so, why not?, what happens?

Yes I can.  It allows me to boot using the liveCD

---

### Post by Hakunka-Matata on 2011-09-15
> **garvinrick4 said:**
> It is just a guessing game unless you use your Ubuntu Live CD (install cd using Try Ubuntu)
and run this boot script.
Download and extract to desktop. Make sure the file boot_info_script.sh is on Desktop:
Open a terminal and:
```
sudo bash ~/Desktop/boot_info_script*.sh 
```will give you a text file called RESULTS copy and paste here so we can diagnose problem and fix. After you copy and paste highlight whole thing and hit # sign in upper right of Message box so as to put in a nice box that is easy to read.

That command line for boot_info_script is old:
Try this
```

sudo bash ~/Downloads/boot_info_script.sh
```

Then post the RESULSTS.txt file that produces between code tags.
open RESULTS.txt in text editor
highlight and copy the entire text
paste into new reply
highlight again
click on code tags - # icon

---

### Post by YesWeCan on 2011-09-15
> **eamonster said:**
> I am still unable to log in.  I get this message:

"Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key"

I know my windows 7 had a recover partition on the HD.  If I could only get to that I'm sure you guys could help me recover it.
It may be that the Windows partition boot record is damaged or the boot flag is wrongly set. It may be possible to boot the recovery partition by setting the flag. Need to see more details. Please post the output of
sudo sfdisk -luS
and bootinfoscript: [http://ubuntuforums.org/showthread.php?t=1832812&highlight=raid](http://ubuntuforums.org/showthread.php?t=1832812&highlight=raid)

---

### Post by eamonster on 2011-09-15
> **Hakunka-Matata said:**
> That command line for boot_info_script is old:
Try this
```

sudo bash ~/Downloads/boot_info_script.sh
```Then post the RESULSTS.txt file that produces between code tags.
open RESULTS.txt in text editor
highlight and copy the entire text
paste into new reply
highlight again
click on code tags - # icon

This didn't seem to work.  It said that:

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script.sh
bash: /home/ubuntu/Desktop/boot_info_script.sh: No such file or directory

---

### Post by eamonster on 2011-09-15
> **YesWeCan said:**
> It may be that the Windows partition boot record is damaged or the boot flag is wrongly set. It may be possible to boot the recovery partition by setting the flag. Need to see more details. Please post the output of
sudo sfdisk -luS
and bootinfoscript: [http://ubuntuforums.org/showthread.php?t=1832812&highlight=raid](http://ubuntuforums.org/showthread.php?t=1832812&highlight=raid)

Ok.  I ran the sudo sfdisk -lus and got:


buntu@ubuntu:~$ sudo sfdisk -luS

Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048 1936783359 1936781312  83  Linux
/dev/sda2     1936785406 1953523711   16738306   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     1936785408 1953523711   16738304  82  Linux swap / Solaris

---

### Post by Hakunka-Matata on 2011-09-15
> **eamonster said:**
> Ok.  I ran the sudo sfdisk -lus and got:


buntu@ubuntu:~$ sudo sfdisk -luS

Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048 1936783359 1936781312  83  Linux
/dev/sda2     1936785406 1953523711   16738306   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     1936785408 1953523711   16738304  82  Linux swap / Solaris

Other than swap partition being bigger than it needs to be, the disk sda looks ok. 

The best information you can provide is boot_info_script's output.,  The commands we are suggesting are not working because the directory entries are not correct, probably.  


[LIST]
[*]What directory is the boot_info_script.sh file located in?
[*]Open a Terminal window, don't change directories, just open the Terminal window and from there use: (if the file is located in **[COLOR=Blue]Downloads[/COLOR]**)
[*]```
sudo bash Downloads/boot_info_script.sh
```
[*]if the file is located in **[COLOR=Blue]Documents[/COLOR]** [COLOR=Black]then you type[/COLOR]
[*][COLOR=Black]```
sudo bash Documents/boot_info_script.sh
```[/COLOR]
[/LIST]
The file RESULTS.txt will be generated in the same directory that the file is located.

---

### Post by jroa on 2011-09-16
If you want to try to recover Win7 from the recovery partition, one option that I have used on several occasions is to use a program called GAG.  Download it and burn a boot CD, reboot your computer with the CD in it, select option 4: Install GAG (it will not actually install unless you save it, but Win7 will probably overwrite you MBR anyway).  Select your key board on the next screen, probably option 1:, then select you language.  On the next screen, press key S for setup, then select Add New Operating System.  You will be presented with several options, one of which is your recovery partition.  You may have to select them one at a time until you figure out which is the correct one.  You will be asked to name it, give it a password, and select an icon.  It really does not matter what you call it because it will only be used this one time.  When you are returned to the options list, **do not select the save option**, instead select the Return To Main Menu option and select the icon that you just created.  When you get the partition right, you will be presented with the Windows Recovery Screen.

Here is the download page if you want to try this option.  [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

Edit to add:

This will probably overwrite your MBR and you will not be able to access Ubuntu anymore.  When you get Windows working, we can then work on restoring Grub.

---

