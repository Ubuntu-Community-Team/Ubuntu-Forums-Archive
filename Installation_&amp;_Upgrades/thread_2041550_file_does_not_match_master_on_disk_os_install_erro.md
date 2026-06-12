---
title: "file does not match master on disk os install error"
date: 2012-08-12
forum: Installation &amp; Upgrades
---

### Post by belac151 on 2012-08-12
when I try to install ubuntu 10.4.02 at the 23% mark an error pops up saying that a media file in one of the kernals does not match the source file on the disk. I have tried burning at a lower speed and making sure both the disk and reader are clean and free of scratches. I have tried two separate hard drives and two separate disk readers. my disk readers are old, however everything is working as intended. I have tried it at a cool temperature as well. I have tried to use the newest version but it crashes on loading of the disk, or it freezes right before install. I have burned several copies of 3 different versions at various speeds and nothing works. can I please get some help?
P.S
my sata devices only work on ide mode in bios. if I use raid it looks for floppy drives even though I disabled them, if I use ahci it cannot find the drives. my boot order is cd/dvd rom then hard disk.
thank you for your time
Sincerely Caleb

---

### Post by oldfred on 2012-08-13
Did you verify that the download is correct. You can check the md5sum. Is not 10.04 now at 10.04.04? 

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

Some just find using a different tool to create CD works. And others find the alternative or text based installer works. That is the same install without the gui.

[http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by belac151 on 2012-08-13
I have a GF7100P-M7S version 6 motherboard and in bios I set my 1st boot priority to "removable" and set the removable priority to load my live usb drive first. All my computer does on start up is show the temp of the cpu and fan rpm (like it always does) but it does not load my usb. I think the USB has some hidden files on it because it holds 3.5GB on it but only 2.45 are available. do I need a completely clean USB because I cannot get my computer to start installation off my USB drive. If I do can I get a link to a mac tool to clean my USB please. I am not tech savvy enough to do a text install and I really want my new computer to work. Can I get some more advice please?
Sincerely Caleb
here is a link to my mobo's specs.
[http://www.biostar.com.tw/app/en/mb/introduction.php?S_ID=312&tab=1](http://www.biostar.com.tw/app/en/mb/introduction.php?S_ID=312&tab=1)

---

### Post by oldfred on 2012-08-13
I have a different 775 based system. But with my system, I thought I was supposed to boot from USB device. It had a long list of USB type devices, CD, Floppy, Hard Drive & others, but none of them worked for my USB flash drive. Then one day I happen to have the flash drive plugged in and was changing Hard drive boot priority and there it was - my flash drive. USB Flash drive has to be bootable and is then under the hard drive list, not USB list. Also then my f12 one time boot drive choice also shows the USB flash drive.

I also have a nVidia card and have to add nomodeset to get it to completely boot.

---

### Post by belac151 on 2012-08-14
So it has to be under hard drives? Odd. I can only find mine under removable drives. Is there any way to change this? I also have a Nvidia Gforce 8800 GT 512 MB. How do I add nomodeset so it will boot correctly.
thanks for all the help
sincerely caleb
here is the link to my card.(i got it for $40! woo!)
[http://www.nvidia.com/object/product_geforce_8800_gt_us.html](http://www.nvidia.com/object/product_geforce_8800_gt_us.html)
P.S I am not savvy enough to use the root console or whatever the directions say to change base values and whatnot.

---

### Post by oldfred on 2012-08-14
We often use terminal as then you can copy &  paste commands. Ubuntu has several gui and then there are different ways to use the gui to find the way to edit something.

I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 

then - I think now if you tick to box to include proprietary drivers it will install the nVidia driver directly and you may not have to do this on first boot.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

---

### Post by belac151 on 2012-08-14
When i install off disk it shows a bunch of status reports saying what is being installed, after a while it stalls with a header sayingb init:ureadahead-other main process (1144) terminated with staus 4 and another with the 1144 replaced with 1145. It stops on various file downloads each time I retry and does not go any further. It also sometimes says stdin: error 0
Can I have some help?
Sincerely Caleb

---

### Post by oldfred on 2012-08-14
Usually those type of errors are related to a bad download. Did you run the md5sum?

---

### Post by belac151 on 2012-08-15
i have no idea what md5sum is. i did take out all my cards and try it again. it had two responses. it gave the termination error again and then either went to install but with about 600 by 800 resolution. the other one it went to ubuntu desktop but when i opened something it crashed. i got my disk from free geek and they burn theirs well. i have tried the newest version as well. this is what i have done so far
when it starts to boot from the cd i have scrolled down to "install ubuntu" i then press f6 and select nomodeset. i then used the command line that comes up and replace both quiet and splash with nomodeset. then after i press enter and wait it shows the files being installed in a dos style text screen. it will say unreadable and terminate. it always does this with two files and then freezes. i have not been able to get this to work for a week and i am starting to get really mad. can you please help me.
sincerely caleb
p.s right after this i will try the newest version and try to install it the way you described
p.p.s when i do not replace quiet as well it says stdin error 0 and does nothing else.
EDIT: i tried the 12.4 and the first time it completed and showed an ubuntu screen, but then went gray, then black, and when i tried to pull out the disk it showed a bunch of error messages. the next two times it went to the install menu where it proceeded to freeze at various points as it ussually does when i try to install.

---

### Post by oldfred on 2012-08-15
Did you get a full install of 12.04?

You need to check ISO that it is valid with md5sum.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

