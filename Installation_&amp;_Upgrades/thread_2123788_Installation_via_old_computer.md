---
title: "Installation via old computer"
date: 2013-03-08
forum: Installation &amp; Upgrades
---

### Post by neogeo1128 on 2013-03-08
Hi, I would like to install 12.04 into my old notebook computer... 

the old notebook computer have a nice hdd but the cdrom was broken :( (and usb boot/install not work also)

I can pull out the hdd drive (erase the whole hdd is ok) into other computer to copy the installation program.... I think I can copy the installation program into the hdd drive and take back into the notebook computer and then start installation from HDD boot 

Kindly advise any informations on how to do this

Thanks!

---

### Post by ibjsb4 on 2013-03-08
You can go ahead and install it from the other computer.  When you put back in the orginal it should detect the change and adjust itself to the new environment.  Disconnect the HDD in the slave computer so you don't mess up its boot loader.

---

### Post by neogeo1128 on 2013-03-08
thanks for reply... it's not a bad idea... but

1. other computers are 4-core or even 8-core computer... don't know if this work on a Pentium 3.0MHz notebook
2. I would like to learn to how to do this and using this "worked" partition on other old model notebook computers  (I have a friend selling 2nd hand notebook and would like to have a OS installed so customers can start running a OS after purchased, like a brandnew notebook,OS will install once you turn on the computer)

---

### Post by MAFoElffen on 2013-03-09
If you do a search on "Ubuntu install without CD"... It going to get you to here as the top search answer (which just happens to be the right one):
[Installation without a CD]("https://help.ubuntu.com/community/Installation#Installation_without_a_CD") 

Which would give you some ideas... Of course from what and the way you are talking about it ... Use a Linux 32bit sys. Get whatever distro's install cd iso copied to the root of the drive. Then you need  bootable grub floppy disk. You need something to boot that can boot Linux....

This is a few notes form experience helping out at a computer recycler's. We install Linux on resale computer that we rebuild and re-certify.

Your first obstacle is getting it on the drive. A laptop with a Pentium 3 is going to have a PATA laptop drive. They do not have the same connecter as a desktop PATA drive. There are USB adapter kits that can connect to any drive, laptop or desktop. We use them for that purpose, to work on and test drives before recylced resale.

Second is you need to have something to boot from that can at least transfer the boot to the iso image. This could be from a floppy or or that drive made bootaable while being prepped.

But before you do any of that, you really need to look at that laptop hardware wise. Always a good idea to see what you are dealing with and what you are going to be setting up. The concerns are: 

- How much RAM does it have and how much can it be upgraded to? If it does not have at least 1GB of RAM, a full-blown version of Ubuntu is not going to run well. You need at 64MB to boot a commandline text only linux base. For that, 128MB does better. You can boot a low-overhead graphics in 256MB, but 500mb is better. 500MB - 750MB for Lubuntu and Xubuntu... Use an Ubuntu branch that can run the memory you provide for it.

- How much HD space? The recycler I help out, they settle on 20MB as a minimum. I get a lot of smaller drives from them for free, becuase they figure the are not large enough to resale. It takes about 4.8 MB's to install a FAT version of Ubuntu.

- CD drive not working? It has one right? If it does have one, does it spin and not read? If if mechanically works but does not read, it's not going to cost you anything to try to clean it right? If it doesn't work, broke is broke, but it's not going to be any worse. Take two tissues. First one, roll up a corner. Dampen with clean water. Squeeze out as much water as you can. With the drive tray open, wipe lightly around the lense. Take the other clean tissue and wipe lightly around the lense to make sure it is dry. Then take the first tissue and wipe the rubber drive ring clean. Dry that with the second (dry) tissue. Test it.

- If it at least has a floppy drive, at least you have something right?  As a recycler, we give away old laptop floppy drives... (We replace them with CD drives.)

- You can't boot a Pentium 3 computer from USB... But if you have a floppy drive, you can boot from a GRUB bootable floppy to boot a USB storage device (such as a thumbdrive)

- If you do take the drive out and install, say, non-pae 32bit linux... and keep it a generic install... It will boot on a that Pentium 3. I have test drives here that I can put in different machines (as well as portable linux thumbdrives) that boot between machines. The only problems I've had about what you are talking about, is when I use 64bit installs on some of my test drives, installed on... Where there is major changes in the number of processors and cores. A pentium 3 is 32bit single core which still adapts well in a 32bit linux sys. I don't know how it would do with PAE, depending on the board and memory controller. I've installed P and P II as PAE, but around Pentium 4, some of the memory controllers wig on PAE. So (forewarned) if not, then try the Netboot non-pae install iso.

Biggest obstacle... You need to do some homework before you set out to get it to work. Sharpen your skillset. Don't go into it blind. Make it a success. Don't set yourself up for failure. Old laptops sometimes require a little tweaking.

Give us a make and model of that laptop and I can recommend what may run on it and avenues to get there. Without specifications, it's all speculations and fortune telling.

---

### Post by neogeo1128 on 2013-03-09
Dear MafoElffen

Thanks for your reply....
This is Dell Pentium 750MHz Notebook (Sorry for saying it is a P3 model)
and a 20GB HDD but a damaged CDROM and cannot boot from USB 

I did some research and I have other computers worked in my home.... So I found a solution..... I posted it here and make a reference for other buddies....

1. I have a 4 Quad Computer with Ubuntu + Virtualbox installed.... so using Virtualbox is a good choice..
1a. Also I have a USB to SATA/IDE adapter.... sample can be like [this ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812232002")
2. Setup a Virtual Machine and using 256MB Ram, "Create a virtual hard disk drive", and using VDI (Virtual Disk Image) and hard drive file type... 
2a Remember to find the location of that vdi file (for ubuntu linux, usually should be /home/<username>/VirtualBox VMs)
3. Using "Dynamically allocated" as virtual hard drive
4. Go to settings , storage and select the Lubuntu iso image file as your cdrom drive (which you should downloaded in your 4Quad computer before)
5. Start the virtual machine and press F12 immediately and press "c" for making booting from CDROM Drive (as this moment your virtual hard drive is empty ...so nothing can be booted)
6. Do normally in the installation and reboot after finished....
7. After you have a "done" virtual machine image... the next step is put this image into your notebook hard drive
8. Turn off your old notebook.. plug off the power cord and batter and pull the hard drive from the notebook 
9. Connect the hard disk drive with the adapter and insert this into the USB port of 4-quad computer 
10. Then you will see the hard drive was mounted 
11. Go to Disk utility (*Palimpsest*) and select the usb drive, remember the device location (e.g.: /dev/sdd) and click "unmount" the drive 
12. Exit the utility
13. Open the terminal and then convert the virtual disk image into a .img file by typing 

VBoxManage clonehd file.vdi output.img --format RAW
(since file.vdi is the virtualbox disk image file [usually /home/<username>/VirtualBox VMs] and the output.img is the output file name and this file will write into the new harddrive)

14. It takes some time... when finished... we can put that image file into the hard drive by typing:
sudo dd if=output.img of=/dev/sdX
(since /dev/sdX is the device drive location of your notebook hard drive, my ones is /dev/sdd)

15. It takes MORE longer time.... when ok... pull out the usb connection and then put the hard drive back into the noteook
16. start up and should be ok (as first time they will the the uuis is incorrect or something like that... it should be ok after a reboot)

This is my experience... please write any comments on that..
Thanks everybody!

---

