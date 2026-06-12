---
title: "Problens booting ubuntu 11.04 after installation (grub?)"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by KentNyberg on 2011-10-13
I installed Ubuntu 11.04 on my new HP and that already had Windos 7 installed.
I went through the complete installation and everything seems ok, but I just can not boot Ubuntu. It looks that if Ubuntu did not touch the MBR with grub?
I tried using easybcd on windows to boot Ubuntu but if I tell the windows bootloader to boot Ubuntu on /dev/sda5  it only shows the shell from grub, and nothing happens.
I do not know how to fix grub to be on MBR and to boot ubuntu, can some one help me with what to do?

It seems that a default installation of ubuntu does not let me choose where to install grub?
Should it not be put in the mbr of the harddrive? It seems not to be the case since my computer directly boots windows after a complete installation of ubuntu :(

---

### Post by Quackers on 2011-10-13
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Or alternatively, have a look here

[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

---

### Post by KentNyberg on 2011-10-13
Here is the information from that boot-repair program
[http://paste.ubuntu.com/707564/](http://paste.ubuntu.com/707564/)

---

### Post by oldfred on 2011-10-13
Many have reported that the boot repair program works. You do not have grub in the MBR and need that to boot Ubuntu.

Not sure how to configure if you want to keep EasyBCD as it is another third party boot loader. I think you then have to install grub2's boot loader to the / (root) partition which is not recommended but can be done.

---

### Post by KentNyberg on 2011-10-13
I *DO* want grub in mbr,  the installation of both Ubuntu 11.04 and now 11.10  just will not install it there. I do not understand why. I never even get to choose :(

---

### Post by oldfred on 2011-10-13
If installing you have to use manual install or Something Else. That gives you a choice on where to install grub2's boot loader. Default still is sda unless you choose otherwise.

But the default is to install to sda. Do you have one of the BIOS that has a bitlocker type lock on the MBR and will not let anything be written to the MBR. Check settings in BIOS.

---

### Post by KentNyberg on 2011-10-13
I checked my bios and did not see any information about bitlocking or otherwise.

I have tried an advanced installation and specificly choosed sda as the installation for grub, though nothing stil happens. All i get is windows booting. 
 Im getting mad soon.. haha

---

### Post by Quackers on 2011-10-13
Did you see any mention of UEFI in your bios settings?

---

### Post by KentNyberg on 2011-10-14
I am not completly sure right now,  but yes I think i saw it.. what is that?

---

### Post by KentNyberg on 2011-10-14
I checked, and for sure, my computer has that UIFI thingy..

---

### Post by oldfred on 2011-10-14
UEFI is the new replacement for the 25 year old BIOS. They all have a BIOS mode for compatibility. But Windows will only boot UEFI with a efi partition in a gpt not MBR (mdsos) partitioned hard drive. Your drive does not show a efi partition and is msdos partitioned.

[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)

Is the boot script you posted still current. If not post another one.

---

### Post by KentNyberg on 2011-10-14
Thanks for the reply, but I still do not get how this will help me to install Ubuntu om my computer.  Do not Ubuntu work with UEFI?  A default installation of Ubuntu om my computer will not let me boot Ubuntu, it only boots windows. Why?  And how do I boot Ubuntu?

---

### Post by oldfred on 2011-10-14
If BIOS is not preventing you from writing into the MBR.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda6 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by KentNyberg on 2011-10-14
You are my hero of the year!!!!   It works now,  thanks alot! :)
Wish you all the best :)

---

### Post by oldfred on 2011-10-14
Glad that worked.

Change thread to solved, Please.

---

