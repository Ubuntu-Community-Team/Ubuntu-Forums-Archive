---
title: "Problems to boot ubuntu 9.10 64bits"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by DecioSP on 2009-12-27
At first let me introduce myself.
I am a long time windows user with some understanding in programing because my graduation (languages like Pascal, C, java...) and recently I am trying to learn Python.
Beside that i confess that i tried (not so hard i admit) start to use linux as my primary OS a long time ago sometimes, but the lack of time and the difficult for a beginner to put it to work properly made me go back to windows every time i tried.
Now that i have a little more time available (thanks to professional stability) allied with my wish to learn Python i have made another try to use linux.
And I confess that I am surprised with the improvements that you have made from some years to make the system more friendly to use, just to make myself clear, not only ubuntu as also slackware (which give me some headaches years ago) recognized almost all my hardware and ubuntu even suggested the proper drivers. (And not to mention the visual improvement also, which made me think if I not wait to long to try linux again)
However, as always, the problems appeared.
Having no problem in use some new versions in my old computer and also having the ubuntu live cd working like a charm in my new, i decided to install it in my hd.
I have a 2.4 intel quad, with 4Gb of RAM and 3 Hds.

The first 2 of 500Gb each installed in raid 0 with 4 partitions:
I - 100 Gb with Vista 64 installed
II - 1 Gb for windows drivers
III - 50 Gb with XP 64 installed
IV - The rest in a partition used for storage for both systems
All four formated in NTFS.
Also, as long it was my first configuration, MBR is here.

The 3th, recently brought, is a 750 GB that was primary full formated for windows use  only (in NTFS), but after my decision, it was reformatted in:
I - 630 GB for windows
II - At about 130MB in the begging of disk for some windows unknown use 
II - 12 Gb for /
III - 4Gb for swap
IV - the rest for /home

I made the partitions using some tutorial from here using first the windows administrative tools and after that the ubuntu 9.10 64bits cd.
It went through the install with any problem, but after boot it went in windows boot loader (WBL) with no options to access linux install.
It is going to the 10th day that i try to use any info from lots of tutorials that I found everywhere and until know here is where I stand:
First I tried to edit WBL via bcdedit commands - No success.
After that I went through a great tutorial from someone of here that explain how to dual boot Win7 and ubuntu using EasyBCD 2.0 - And this time somethings happens:
If I use only the grub option and point it to the /dev/sda3 it opens a grub screen but tells that it cant find that files from grub-legacy (cant remember those names exactly, but i think it was menu.1st, stage...)
Since I learned that 9.10 uses grub2, i think thats not the way so I tried to use EasyBCD 2.0 with the option for grub2.
Now, two things happens:

I - If I point to O: (Where ubuntu is installed), the WBL gives a error message telling to reinstall windows.

II - If I leave the advanced option pointing to C: (Where vista is installed) it creates a folder named NST with a autogrub file in it and when I boot it opens the grub 0.4.4 dos.   I tried to use the commands set=root(hda1,3) and others that I found here, but using the TAB function after some commands it only shows the options to hd0 (hd0,1; hd0,2...) but dont access (I think because it is format in NTFS and in raid 0 too).
Also, it leaves only the options to access hd1,0 and not hd1,3 where ubuntu is installed, when I try to set root to hd1,3 or /dev/sda3 it gives a message telling that it cant find (or mount) the selected path.

I already tried to reinstall the grub using live cd as instructed here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
But it fails in the last step when i keep receiving the message **error: Cannot open /boot/grub/device.map**
I Also tried to create a partition only for /boot
Also tried to format in ext3
Also tried to leave ubuntu choose the partition table using the auto button.

I really think it is just a matter of make some small config to point windows boot loader to the linux partition, but I confess that I am trying hard in the last days with no success.
I also know that you might need some more technical info, like the results of fdisk -l (which gives error and asks to use parted)
But since I know you are probably tired after a big message like this one and since I will probably post more info then you really need I will wait until some response.
Anyway I would like to thanks in advance for the help and hope we could figure whats the problem is because I cant wait to start to use this new linux.

---

