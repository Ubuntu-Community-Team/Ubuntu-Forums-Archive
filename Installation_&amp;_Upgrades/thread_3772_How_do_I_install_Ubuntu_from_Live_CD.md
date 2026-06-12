---
title: "How do I install Ubuntu from Live CD?"
date: 2004-11-09
forum: Installation &amp; Upgrades
---

### Post by avallon on 2004-11-09
I am having trouble with the installation from the install CD. Burned the Cd x2, after checking md5sum.
It appears that some of you boffens have tried to install it from the live CD. 
How do I do it? Any advice is appreciated.

---

### Post by Joeb on 2004-11-09
The Ubuntu Live CD does not have the an option to install to the hard drive.  That's not to say you couldn't hack something to get it to work, but it's not built in.  What are the problems you are having with the regular install CD?

---

### Post by avallon on 2004-11-09
The installation process starts nicely and goes through the following stages of installation: language, select a country (South Africa), hardware detection, network hardware detection (successfull, using DHCP and ADSL router connected to Ethernet 8-port hub). The following step should be: Partition your disks.
Instead I get a blank dark blue screen with a terminal line at the bottom and frozen cursor in the left corner. I left this for about half an hour and nothing happened further.
I tried some other installation options, e.g. vgi-71, noapci, nolapci, framebuffer because I thought it would be related to display and ATI Mobile Radeon 9200, which was usual problem with many other distributions which I tried to test.
Notebook is Fujitsu Siemens AmiloD7850, which I guess is the same as Fujitsu notebook of the same/similar designation. This range is just being sold mainly in Europe and South Africa by Fujitsu Siemens (jointly owned company).
Processor is MobileP4 3.2GHz with HT, 512MB RAM and 80 GB disk drive. Originally, the drive was Toshiba, but that one packed up within the first two weeks, and it was replaced about 3 weeks ago by IC25N080ATMR04-0 (whatever that is) drive.

Could the partitions on the hard drive be a problem?
This is what I have at present:
50MB FAT32 - BootMagic was unsuccessfully installed there. It has been reformatted in the mean time. Primary
30GB NTFS with Windows XP Home. Primary
10GB FAT32. Suppose to be "transition zone" to transfer the files from Linux to Windows, which I could not so far do directly to NTFS
35GB Linux Ext3
1GB Linux Swap.
All of the above partitions were created by using Partition Magic program.

Thanks for your trouble in replying.
I did post a similar question on Monday, but have not received any replies. I also did not provide so many details as now. I am completely new in this game, and trying to find my feet.

p.s. After loosing it with Ubuntu, I have installed Mandrake 10.0 on the above notebook in addition to Windows. Dual boot works fine from Lilo.

---

### Post by Joeb on 2004-11-10
Hmmm, I'm not sure what would cause Ubuntu to fail on the install.  I don't believe it's a grub vs lilo thing as it doesn't sound like it's gotten that far in the install.  As you've found out, Mandrake about installs on anything.  You might try looking in your /etc/lilo.conf and see what options it's passing to lilo for booting up.  It's a long shot, but maybe something there will strike your fancy.

It's possible that Ubuntu is choking on that bad 50MB partition you had.  Did Mandrake recognize it or did it get wiped when you installed it?  If you're still wanting to experiment, you can use Mandrake's partitioner (diskdrake) to create a small 5GB partition and try installing to it. 

If you try that, though, remember that grub will wipe out your lilo and you will have to recreate it if the Ubuntu install fails.  It's not that hard to reinstall lilo for Mandrake.  Just boot of the install cd, go to rescue mode and tell it to reinstall the lilo (it might say bootloader, I can't remember).

You might also want to repost your problem to the mailing list.  I know it's a hassle, but different people frequent different boards/lists and maybe someone there can help you.  You can do it without subscribing by using the forum that mirrors it (it's called Mailing list, I think).

OTOH, if your satisfied with Mandrake for now, you can wait till the next Ubuntu is released, this Spring.  It might better support your hardware.  But, it'd be nice to figure out what the problem is (even if you stay with Mandrake) so that others with your hardware don't get stuck, too.

---

### Post by avallon on 2004-11-11
Thanks for the advice.
This is what I have tried in the mean time, which is very similar that you have suggested.

By using Partition Magic, I have resized the 35GB partition containing mandrake to 20 GB, allowing me to have 10Gb for the experiments. I did not know until recently that I could partition and install many, not only two, operating systems.
10Gb has been formatted to FAT32, then deleted, as someone else suggested on the other mailing lists. I used Impi2 and install it to this partition, manually and using existing swap. Then, as you said, this installation program wipped out my lilo and I could only boot in Impi. Then I used installation CD from Mandrake and "upgraded" the instalation, since I did not know about shorter "rescue" procedure. For some reason, lilo did not picked up Impi boot. This doesn't worry me, since it appears that Impi's boot loader install itself into MBR and doesn't allow me to install it on the Impi partition. The following version should address this in Impi.
What was rather strange was the following:
Mandrake's diskdrake sees 50MB FAT32 and 20GM WinXP partition, and my "transssion" 10BG FAT32, but it also shows me 20GB additional NTFS partition which doesn't exist? I wonder whether there is a problem between Linux partitioning programs and Partition Magic? It could still be related to 50MB Boot Magic. I could never reinstall this program again.
But, the same Ubuntu install happened on the other notebook.
At present, I have winxp working, Mandrake 10 working and extra "data" partitions: 10GB FAt32, and 10GB /mnt/data for LInux data storage. 50MB is still there for now. I will try to get rid of it, since I can now use lilo from Mandrake in a user friendly way. Notebook doesn't have a floppy drive and BootMagic on a CD is German, and it did not work so well. It did not pick up either Mandrake or Impi partitions.
Further, my official Ubuntu CDs are coming shortly, so I will try again. Mandrake is working fine, except I need to admit a personal failure to get Ubuntu going. That's the worst!
Have a good day / night!

---

