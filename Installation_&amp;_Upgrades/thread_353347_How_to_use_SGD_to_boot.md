---
title: "How to use SGD to boot"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by ShirishAg75 on 2007-02-04
Hi all,
       I'm going to install Edgy Eft (6.10) & want to use SGD to install instead of GRUB. The reasons being he has 2 hdd & both have Windows XP partitions. I have seen quite a few times GRUB failing & giving error 17 & error 18 at my own & couple of friend's places. Now the way I want to use it is have this SGD which will push it to Ubuntu. If the CD is not present then push straight to Windows XP. This way if sometime the boot fails, then also the system is running. If somebody has precise steps how to accomplish this, would be looking forward. Thnx in advance :)

---

### Post by confused57 on 2007-02-04
Maybe this will help:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Herman on 2007-02-04
Shirish,
According to adrian15, the developer of SGD, we cannot install SGD Grub to hard disk. At least not very easily anyway. There might be a way, but it would be a lot of work.
If you mean you want to install Ubuntu but you do not want to install Grub to MBR on the first hard disk, you can instead choose to install Grub either to a second or third hard disk MBR, or to a floppy disk, or to the first sector of the Ubuntu partition. As long as you decide to install Grub somewhere, the installer will be happy and will continue the installation process. With the 'Alternate' install CD, you can even install no bootloader at all. The installer will protest, (warn you), but it will continue without any bootloader if you insist. 'Alternate' CD info is in my sig link as you probably remember.
The 'Desktop' CD can now also let you decide where to install Grub. In step 6, after partitioning is over, there is a line about half way down the page, it says: 'Grub wil be installed to: (hd0)'
The letters '(hd0)' are inside a button you can click with your mouse to edit that to (hd0,1)(if that is your new Ubuntu partition), or (fd0), (when you have a floppy disk in the drive), or wherever you wish.
Then you can still use SGD to reboot with if you like, from CD, floppy disk, or USB Disk.
But I don't think it's easy to install SGD to hard disk.

Is that the right information you need?
Regards Herman :)

---

### Post by ShirishAg75 on 2007-02-05
First of all hi herman,
             A belated Happy New Year 2k7. I see tht u have developed the sites nicely. A little off-topic thing first. In ur site [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) u haven't given a link from where to download the alternate CD's . For newbies, it would be good to have tht in one go. 
            Now I read SGD as well as GAG. I think what my thing would be GAG. What I need is not at all touching the NTLDR & have GAG boot from CD & boot into Ubuntu. 

              This is the scenario at my friend's end. He has 2 optical drives & 2 hdd, in the BIOS it shows 

 Primary     Master  DVD-ROM/RW
 Primary     Slave    CD-RW
 Secondary Master  Huge 160 GB hdd (ATA 6)
 Secondary Slave    Small 80 GB hdd 

          Both the hdd have XP, now I'll be installing it on the 4th hard disk, so hd**d **& some partition therein. Now if I wanna install Grub therein then how do I go about tht, also how can I use GAG without going the full routine. The guide is short on many a points like tht.

Each time he would be going for GNU/Linux he would be going to BIOS, making sure he boots with the Secondary Slave Drive as the second option & use GAG to boot to it, now what things he need to do in GAG?

---

### Post by Herman on 2007-02-05
And Happy (belated) New Year to you too, Shirish :)

Perhaps my web pages are getting too big to be helpful, or maybe it's time to review my indexing. All the information is there, but I spend a good amount of time directing people with the appropriate links so they can find what they are looking for. 
To be brief, GAG Boot Manager is a very good Linux boot manager, but it is not a boot loader, it needs a boot loader like Grub or LiLo to be installed in the first sector of the Ubuntu partition or nothing will happen when we try to boot Ubuntu or any other Linux with it.
We can install Grub or LiLo to the first sector of our Ubuntu partition with the 'Alternate' install CD, just choose 'No' when it asks to install Grub to MBR, and then type (hdx,y) on the line when it asks where else would you like to install Grub then? Where the letters x,y represent your hard disk number, in your case d might be 3, and whatever the partition number will be. Or you can type /dev/hddy, where 'y' is a partition number. You will need to know for yourself what partition you are installing in, so you would have needed to take a note of it earlier in the install if it is a complex partitioning scheme. Here is where this is explained in my website, 
[                      If you choose <No> (not to install to MBR), you will be given an opportunity to specify where else you might like GRUB installed]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location")
Also, on each of the install pages there are links to this and also to the GAG Boot Manager Page.
If you do it that way you will need your GAG floppy disk or CD ready before the install begins to reboot with at the end of the install, or a SuperGrubDisk, and your CMOS (bios) configured to boot from floppy or CDROM drive.
This is already well explained on the website, maybe it is getting too big (verbose?) 

It is also possible to control where to install Grub with the 'Desktop' install/Live CD now too. In step 6 about half way down the page you click on the (hd0) button to edit it.

GAG comes with plenty of instructions of its own too, and I recommend people should read those as well. They are quite informative.

Oh, and happy installing.
Regards, Herman :)

---

