---
title: "Can't boot Windows or Ubuntu and Windows repair doesn't work"
date: 2014-05-20
forum: Installation &amp; Upgrades
---

### Post by miao2 on 2014-05-20
Well, I have just one day of experience of Ubuntu and I am desperately stuck. After I installed Ubuntu with Yumi in a second partition next to Windows 7  I couldn't get Windows to boot again.
I booted from the Windows 7 recovery CD and probably made a second mistake in typing bootrec /fixmbr and bootrec /fixboot before selecting the Windows repair.
Now there is nothing happening, I just get a cursor...

I can boot in Ubuntu from a USB key in trial mode (If I try to reinstall Ubunto to the hardrive I get the message "no root file system is defined").
Is there a simple way to repair the MBR from this external Ubuntu, even if it destroys the resident Ubuntu? I really need to be back in Windows.

Alternatively, If I boot in Windows from an old harddrive, can I plug the new not-functioning harddrive from a USB enclosure and repair it with EasyBCD?

---

### Post by Bucky Ball on 2014-05-20
Welcome. You could try Boot Repair. Follow the instructions for running from a LiveCD (or burn a Boot Repair CD and boot from that):

[https://help.ubuntu.com/community/Boot-Repair#A1st_option_:_get_a_CD_including_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#A1st_option_:_get_a_CD_including_Boot-Repair)

---

### Post by miao2 on 2014-05-20
thanks. I tried to install it directly from the terminal as explained on the page but it failed. I am now downloading it but don't know how to burn a CD from Ubuntu. Do I need to download a player?

(I am not too keen on trying to install it on the USB key because it's my last chance to go online.)

By the way, can you tell me why installing Ubuntu with Yumi has corrupted the MBR for Windows? I would have hoped that by now those apps would master the issues with dual booting. I remember those issues with EasyBCD almost 10 years ago

---

### Post by miao2 on 2014-05-20
Brilliant! Thank you Bucky Ball, Boot Repair restored my Windows 7 MBR in a minute and I have learned a few things.

I am still trying to organise a dual boot but I am now very wary of Yumi. Do you think EasyBCD can manage or do you recommend something else?

---

### Post by oldfred on 2014-05-20
I thought Yumi was more of a way to create a multi-boot flash drive, so you could boot different ISO all from one flash drive.

Grub2 is the standard boot loader for Ubuntu and in the vast majority of cases works well with Windows. Of course there always are exceptions.

Use Windows own tools to shrink the Windows NTFS partition, but not to create any partitions. Then reboot into Windows to make sure it has run chkdsk and updated to its new size.

If you have an available primary partition to use as an extended then Ubuntu should install without issue. If using Something Else you have to create a ext4 partition as / (root) and swap. Optioally you can create /home as another partition. You cannot create a NTFS partition during install but if dual booting that is also suggested, but use gparted before or after install to add that.

 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
[https://sites.google.com/site/easylinuxtipsproject/first](https://sites.google.com/site/easylinuxtipsproject/first)
Install with screen shots, auto install option
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)

---

### Post by miao2 on 2014-05-22
Thanks. I found help in the various links and have finally been able to install a dual boot of Ubuntu and Windows 7. 

Just wanted to share my experience as not many users mention my ultimate issue: I couldn't install anywhere from a liveUSB (I made 3 of them and tried them from every USB socket). I would get a warning about a CDROM partition and the install would freeze. But as soon as I burned a bootable DVD, things went well. Not sure why.

I didn't create a swap partition, partly to avoid the risk of an additional manipulation of the partitioning. Is it a bad decision considering I have 4GB RAM plan to use Ubuntu more for learning than daily use?
Is it easy to add a swap subsequently?

---

### Post by oldfred on 2014-05-22
I have 4GB of RAM on desktop and almost never use swap. And I do not recommend hibernation anyway, but that requires swap.

But on my laptop only have 1.5GB of RAM and uses swap if I open too much, and gets real slow when it does. So I have learned not to open many large apps at once and do the same on my desktop. On laptop I can run Firefox, Zim and browse, but then if I open Thunderbird or LibreOffice it gets real slow. I can do that on desktop without issue. Do not attempt to edit videos, but otherwise you should be ok.

You can also create a swap file. Only if you have used all 4 primary partitions does it become difficult to add a swap partition later.

       [URL="https://help.ubuntu.com/community/SwapFaq"]https://help.ubuntu.com/community/SwapFaq
      [/URL]
 HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

    [URL="https://help.ubuntu.com/community/SwapFaq"]

[/URL]

---

