---
title: "How can I dual boot Ubuntu MATE with Win 8.1?"
date: 2015-05-24
forum: Installation &amp; Upgrades
---

### Post by cwblanch on 2015-05-24
Hey,

I feel like the biggest noob ever for having to ask this, but I never fully installed Ubuntu (been using a VM) because when I got my Windows 8 PC it was pretty complicated, and it seems like it still is really complicated.

I googled how to dual boot Ubuntu with Win 8, but have been finding conflicting info about resizing partitions, and something about a thing called UEFI or something. I'm honestly not sure what any of this is.

If someone could give me an easy way that worked for them to dual boot Ubuntu (MATE) with Windows 8 I would really appreciate it, cause I'm tired of using a virtual machine.

Thank you

---

### Post by Vladlenin5000 on 2015-05-24
The Ubuntu flavor doesn't matter. If you've been googling about MATE alone that would certainly give you way fewer results than searching for Ubuntu. 
This is where you should start: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ajgreeny on 2015-05-24
There are many, many places in the dual booting using UEFI where you can trip up and Vladlenin5000's link is a good start, but depending on your machine's maker there may be other problems doe to the OEM's use of a non-standard UEFI which disables booting any OS apart from Windows.  There are available work-arounds for this problem, but as I no longer use or need Windows of any sort I have no experience of this problem nor how easy it is to implement.Ubuntu 32 bit will not work, or is very difficult to get to work, in UEFI as far as I'm aware, so why bother trying.

All below info is quoted almost verbatim from forum UEFI guru ans administrator, oldfred, to whom I offer many thanks.

    > GPT Advantages (older but still valid) see post#2 by srs5694:
    [http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
    [https://wiki.archlinux.org/index.php...antages_of_GPT](https://wiki.archlinux.org/index.php...antages_of_GPT)
    UEFI Advantages
    [http://askubuntu.com/questions/44696...y-vs-uefi-help](http://askubuntu.com/questions/44696...y-vs-uefi-help)


    Microsoft suggested partitions including reserved partition for gpt & UEFI:
    [http://technet.microsoft.com/en-us/l...8WS.10%29.aspx](http://technet.microsoft.com/en-us/l...8WS.10%29.aspx)
    Order on drive is important: msftres
    [http://en.wikipedia.org/wiki/Microso...rved_Partition](http://en.wikipedia.org/wiki/Microso...rved_Partition)


    Convert Windows BIOS to UEFI - Also command line install of files to efi partition uses rufus
    [http://www.eightforums.com/tutorials...e-windows.html](http://www.eightforums.com/tutorials...e-windows.html)
    [http://social.technet.microsoft.com/...n-to-uefi.aspx](http://social.technet.microsoft.com/...n-to-uefi.aspx) 

    For info on UEFI boot install & repair - Updated Mar 2015:
    [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

    Lots of detail, screenshots and essential info.14.04 Something Else example
    [http://www.dedoimedo.com/computers/u...all-guide.html](http://www.dedoimedo.com/computers/u...all-guide.html)
    [http://askubuntu.com/questions/34326...g-installation](http://askubuntu.com/questions/34326...g-installation)
    [http://askubuntu.com/questions/16396...-windows-using](http://askubuntu.com/questions/16396...-windows-using)


HP and some others will not let you set anything other than Windows as default in UEFI menu. But there are work arounds.
Thanks to oldfred for this info.

UEFI still lets you boot devices and the /efi/Boot folder has bootx64.efi which is the hard drive boot entry. If you rename that and make it be grubx64.efi then booting hard drive boots grub menu.

Other work arounds.
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Script that automates the rename. Not tested but looks like it should work.

script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix).


---

### Post by cwblanch on 2015-05-24
Yup I'm completely stuck. 
I changed a few of the UEFI settings in the BIOS but got an error screen. Something about Intel and being unable to boot, it kinda freaked me out so I quickly undid the settings and got Windows to work again. 
I'll probably do it again to get the error message.

---

### Post by Geoffrey_Arndt on 2015-05-25
Couple things:

}  Be sure to provide your hardware specs (ram, cpu, graphics card/chips, etc.)

}  Might want to check out YouTube:   [https://www.youtube.com/watch?v=C88g3p5l5l8](https://www.youtube.com/watch?v=C88g3p5l5l8)  Important to watch all 4 videos.   Plus, stop the video when needing to take notes.   Most important thing is to turn off fast boot, quick boot in windows.   Also, use the Windows tools to shrink windows, and make a new partition.   Be sure to restart Windows at least once (preferably twice) after shrinking the partition so Windows can start properly thereafter.

---

### Post by cwblanch on 2015-05-26
My specs are:
AMD A4-440M APU 2.7GHz (2CPUs)

4GB RAM

AMD Radeon HD 7520G

I've watched the videos and settled on [this]("https://www.youtube.com/watch?v=A0z0olUImac") one, but I'm getting stuck where he formats part of the hard disk for Ubuntu (I think that runs from 9 mins to 13 mins in)
It looks like he formats it as NTFS and when I boot into installing Ubuntu I get to the point where I pick the install point, but I can't do of the steps he describes to create the swap partition and such.
I'm not sure if he cut out a fix or something but I can't do anything at all with the partition I've created and I can't install to it. 
I always thought Linux ran on an EXT2 format (or one of those)

---

### Post by RobGoss on 2015-05-26
Hello and welcome to the forum, Installing Ubuntu is simple and straight forward even for a newbie. Ubuntu has made it easy to dual boot right along side of Windows, try this tutorial it should help you get started: [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop) 

There're many different flavors to choose from depending on your needs and expertise try this: [https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

One of the best things I love about Ubuntu is this support forum and the knowledgeable people you interact with- remember the only stupid question is the one you don't ask. 

Welcome to the World of Linux you've made a good choice.

---

### Post by cwblanch on 2015-05-27
I got it to work, it seems like in the video I linked he must have cut out a part. I'm not sure, but in the end I had to just fully format the partition I was using for Ubuntu.

Thanks for the help!

---

### Post by RobGoss on 2015-05-28
You bet glad you got it working and thank you for sharing your findings.

---

