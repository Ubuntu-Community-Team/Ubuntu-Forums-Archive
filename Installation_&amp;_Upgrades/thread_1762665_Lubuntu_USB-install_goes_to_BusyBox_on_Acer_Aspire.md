---
title: "Lubuntu USB-install goes to BusyBox on Acer Aspire One"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by JohnFante on 2011-05-19
I am trying to install Lubuntu 11.04 on a Acer Aspire One 110 (the one with the 8 gb SSD).

I am using the USB method and have used the build startupdisc creator to make a bootable USB stick with Lubuntu.

The stick boots fine and then I first get to the language selections menu. From there I choose "Danish" and then "Try Lubuntu without installing". The machine then starts to boot but after 3-5 seconds it changes to BusyBox with the following error:

"No init found. Try passing init= bootarg."

I have tried a lot of different USB-sticks both an Unetbootin and the built in startup-disc creators. All gives the same error.

Any suggestions?

---

### Post by ajgreeny on 2011-05-19
Are you sure the md5sum of the iso file is good?  Using your current linux distro (Ubuntu?) run the command md5sum lubuntu-11.04.iso from the folder where you have iso file.  The output should be ```
76e5865ce8d0d08fa9f833d781016fe3  lubuntu-11.04.iso
``` If there is any discrepancy in the alphsnumeric, the iso file is corrupt, and you will never get a good OS from it, so download again, preferable with a torrent client.

If you don't have Ubuntu or another distro to use, the md5sum can be found in windows also.  Details at [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by JohnFante on 2011-05-20
The md5sum is correct. Just checked again. 

And there is nothing - as far as I can see - wrong with the Acer. I am running 10.04 xubuntu fine at the moment.

I have had the problem with different versions of 10.10 also. Both xubuntu and lubuntu. 10.04 runs fine. 10.10 and unwards goes to busybox. :-(

---

### Post by linuxinstalledfromhdd on 2011-05-20
You want a light system. 

I would try crunchbang pure debian ..  XFCE instead.

---

### Post by JohnFante on 2011-05-20
I will give Crunchbang a go. 

Any suggestions for the USB-install problem?

---

### Post by JohnFante on 2011-05-22
Found the solution. The SD HC card in the built in storage expansion caused the error. I took it out and now everything works.

Thanks for the suggestions thou. :-)

---

