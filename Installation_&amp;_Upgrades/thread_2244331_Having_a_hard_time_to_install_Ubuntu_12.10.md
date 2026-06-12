---
title: "Having a hard time to install Ubuntu 12.10"
date: 2014-09-15
forum: Installation &amp; Upgrades
---

### Post by christopher_3 on 2014-09-15
Hey Guys,

So i am actualy trying to install Ubuntu 12.10 on my Desktop computer and it turns out that when i always boot from Installation CD, it goes black with a blinking underscore line. But when i put nomodeset on the commandline before it boots all i see is a black screen but this time without the blinking underscore line.. just nothing.. and The lights on y keayboard are actually blinking too which is weird... I also have another Ubuntu and its 14.04 which is the latest version but its on a usb so far same thing happens..

Just for you to know, my Computer has the Gigabyte B85M-HD3 mobo , a 4GB DDR3, a 500GB seagate HD, a Palit Nvidia GT630 2048 MB (2GB) DDR3, The "Hasswell" Intel i3 4130 with processor speed of 3.40 GHZ (Gigahertz).. Also i bought a PCI firewire card which is connected to my MoBo then to my camcorder , then my A4tech keyboard, Wireless Microsoft Mouse 3500, and a home theatre Speaker connected to it...

I also disabled the SecureBoot, i set my SATA to AHCI..

Oh! , i almost forgot, when putting the nomodeset thingy on the command line replacing the quick splash.. i get tons of text which is white and a black backround which is normal and suppose to happen, then the Ubuntu lists my Devices and hardwares and everything.. so far it shows that everything is ok except for the Sound Card and graphic card because next to it, it exactly show [ fail ]  .. i will be recording a video and post it here.. probably upload it on YouTube for you guys to see..

Its my first time to be here in Ubuntu forums.. but been using Ubuntu since 5 years already, im actually typing this down with my Ubuntu machine on Lenovo G700.. ubuntu is my main operating system.. i deleted Windows 8.. 

Thanks in Advance.. i'll be waiting for answers.. i might uploaad the Video tomorow , its quite late in here  already.. :D

---

### Post by dave131 on 2014-09-15
When you get that black screen, try ctrl/alt/t and see if a text-base login screen appears.  If not, try ctrl/alt/F1.  If you can get logged in via a terminal (it won't echo your password as you type it - just press enter when you've finished typing it), then we can take a look at your video and see if a driver of some sort needs to be installed in order for X to work properly with your video card:

lspci -v | grep -A9 -i  vga <press enter>

to make a file which you can then copy to a removable media and take to another computer for posting back here:

lspci -v | grep -A9 -i vga > ~/myfile.txt <press enter>

then just copy the myfile.txt file from your home folder to the removable media.  [COLOR=#0000cd][I]EDIT:  if you want to use a removable USB flash drive, as an example, it will probably be a device listed (by uuid I think) in the /media/<your username here> folder.  You can find this via the same terminal with:

ls /media/<your username here>

you may want to start with no flash drive plugged in, do the above, then do it again after the flash drive is plugged in to know what folder is the flash drive.  After that, copy the file via:

cp ~/myfile.txt /media/<your username here>/<the folder that is the flash drive>/myfile.txt

flush any possible buffering:

sync

Now it should be safe to remove the flash drive and take it to another system to post back here.[/I][/COLOR]

Please post that output back here in a reply.

---

### Post by grahammechanical on 2014-09-15
Your motherboard, was it released for sale before or after 2012? What about the graphic adapter? Before or after 2012? Ubuntu 12.10 may not be compatible with hardware released for sale after its release date of October 2012. The video drivers may not be compatible with the video adapter if the driver is older than the adapter.

Besides all that Ubuntu 12.10 has reached end of life. The repositories are now closed. The installer will not be able to download newer drivers. So, start again with Ubuntu 14.04.1 and you will have a better chance of success.

You may need more than one F6 option to get to a working live session and from there an installer. We sometimes have to use a combination of those F6 options. Look down to section 6 - F6

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

EDIT: I suspect that this machine has hybrid graphics. Does it? Does it have Intel integrated graphics as well as that Nvidia adapter? Does it have Nvidia Optimus Technology?

> [COLOR=#000000][FONT=Arial]The integrated graphics has changed, too. Intel used to embed its GT2 core into select dual-core CPU models, but now it is available in every Haswell-based Core i3.[/FONT][/COLOR]

[http://www.xbitlabs.com/articles/cpu/display/core-i3-4340-4330-4130.html](http://www.xbitlabs.com/articles/cpu/display/core-i3-4340-4330-4130.html)

---

### Post by dave131 on 2014-09-15
Ooppss - I didn't know all of that.  Sorry about my post.

---

### Post by christopher_3 on 2014-09-15
[http://oi58.tinypic.com/2s9pp1s.jpg](http://oi58.tinypic.com/2s9pp1s.jpg)

---

### Post by christopher_3 on 2014-09-15
Ok, so i went to my MoBo's website which is Gigabyte, i put my moder board model in the search bar, and seems like it dosn't support linux at all.. It only supports Windows... but i search in google that they can hackintosh a computer with this kind of MoBo, Hackintosh is installing a Mac OS X on a Windows computer or Non Apple Machine .. they even said that all the drivers work good including the sound etc.. If they can hackintosh with this MoBo, it should also work in Ubuntu..

---

### Post by christopher_3 on 2014-09-15
i beleive it has integrated graphic card coming from the Haswell CPU, it is Intel HD 4400.. i dont know if my Graphic Card nvidia is Hybrid although it was released on May 29,2013 then on August 5, 2013 B85M-HD3 was released which is my MotherBoard, i dont know though if it has Nvidia Optimal Technology, i think i dont have that one..

---

### Post by oldfred on 2014-09-15
Gigabyte has not posted that is is Linux compatible with many motherboards, but they usually work. 
Some require extra boot parameters or you may have to change BIOS settings.
But with nVidia you must have the nomodeset boot parameter until you install nVidia proprietary driver. But may also need the other parameters as well.

Other models but you may need similar settings:
 Gigabyte 970 chipset board  - GRUB_CMDLINE_LINUX="iommu=soft" and Disable iommu in bios
[http://ubuntuforums.org/showthread.php?t=2143433](http://ubuntuforums.org/showthread.php?t=2143433)
[http://ubuntuforums.org/showthread.php?t=2114055](http://ubuntuforums.org/showthread.php?t=2114055)
Gigabyte GA-MA790GPT-UD3H USB boot issues
[http://ubuntuforums.org/showthread.php?t=2205776](http://ubuntuforums.org/showthread.php?t=2205776)
      
 turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)

---

### Post by dave131 on 2014-09-15
I know they would still need nomodeset for the nvidia card, but the motherboard also shows as having VGA, DVI and HDMI outputs.  Is it also possible the onboard graphics need to be disabled in the BIOS?  Should there only be 1 video connection?  Meaning, should a monitor/tv only be connected to the nVidia card to get this working?  Obviously I don't know, but I just wanted to throw that out there, and now I'll be gracefully (?) bowing out.....

BTW - the outputs I asked for initially might still be helpful ;)

---

### Post by oldfred on 2014-09-15
I would think you should only be using nVidia.
But some change connection to Intel on board to see if it works. 
What monitor and does it support the type of connection you are using.

Does live installer work in live mode?

May be related?
 Audio issues on Z97
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421)
[http://ubuntuforums.org/showthread.php?t=2234198](http://ubuntuforums.org/showthread.php?t=2234198)

---

### Post by christopher_3 on 2014-09-15
ok, i managed it to boot from the installation usb with 14.04.. im no longer using the ubuntu 12.10 because as what [ 						 					]("http://ubuntuforums.org/member.php?u=1087323") 				 				 					 						 	[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") said, the 12.10's life already ended.. So i went to bios and disabled Intel's integrated graphics.. then boot up with nomodeset.. and it did work.. But i wonder if the nvidia card will work after the installation... Im going to school now, i will see what i can do when im back...

---

### Post by dave131 on 2014-09-15
I would follow oldfred's advice on getting the correct driver.  It's also probable you'll at least temporarily need to use nomodeset after the install until you get the correct driver.  After the install and reboot of it, you may want to look in additional drivers and see if it lists something there.  I'm not familiar with nVidia anymore as I haven't used one of their cards in a good 1 1/2 years or more.

---

### Post by oldfred on 2014-09-15
I have an older nVidia card and have to use nomodeset until I install nVidia proprietary driver from repository. It may boot in low resolution with the open source driver and nomodeset.

I do not suggest nVidia direct download and only if you have a very new nVidia card or want to experiment then you may want to use the ppa which has very new drivers.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by christopher_3 on 2014-09-16
alright im back from school, installing ubuntu now, *Fingers Crossed* i hope it works

---

### Post by christopher_3 on 2014-09-16
alright, the installation was succesfull.. I didn't put nomodeset when it tried to boot for the first time without the USB that comes with Ubuntu Installer, then when i put my password in log in screen, i went to system settings  and click display and it had my native resolution ( 1440x900 ) .. Sound seems to work, Internet works also but when i click "About this Computer" which is on the top right side of the taskbar, at the graphics it's shown another Graphic Adapter not my Palit GT 630 GPU, never mind at the Intel HD Graphics, because as what i said i disabled it already from my BIOS. i will gonna post a Screenshot in this thread..

---

### Post by christopher_3 on 2014-09-16
[IMG]http://s9.postimg.org/mfk22ba3z/Screenshot_from_2014_09_16_21_05_25.png[/IMG]


I am now using my Desktop Computer not my laptop while typing this down. But the graphic driver seems different.. Check the screenshot

---

### Post by christopher_3 on 2014-09-16
Ok just an update. Everything is working except my Camcorder which is connected via FireWire, if you read my first post on this thread, i Said that i have a CamCorder connected via PCI Firewire Card 1394...

---

### Post by oldfred on 2014-09-16
I suggest a new thread with FireWire in the title so those who may know more about that can see that thread and offer help.

Since FireWire is more of a Apple thing you may want to search in the Apple sub-forum and see if there are any threads there.

---

### Post by christopher_3 on 2014-09-16
ok then, but my Graphic Driver dosn't seem normal, My Graphic Card is a Palit Nvidia GT 630 2GB ... everytime i press the Super Button + S the effects  were very laggy Compared to my Intel Penitum Intel Integrated HD Graphics Lenovo G700, there were no lagginess at all.. But on my Desktop Computer.. Massive lagg, any fix?

---

### Post by christopher_3 on 2014-09-16
Nevermind, i solved it by going to the Launcher and type Software & Updates then i went to Additional Drivers tab and downloaded the Nvidia binary driver version 343.13... 


Thanks for helping guys and suggesting some suggestions and giving me Idea.. 

PS: You can also install Nvidia binary driver in Terminal, but it is a lot more easier if you just go to Software & Updates and everything.. ..

---

### Post by dave131 on 2014-09-16
> **christopher_3 said:**
> Nevermind, i solved it by going to the Launcher and type Software & Updates then i went to Additional Drivers tab and downloaded the Nvidia binary driver version 343.13... 


Thanks for helping guys and suggesting some suggestions and giving me Idea.. 

PS: You can also install Nvidia binary driver in Terminal, but it is a lot more easier if you just go to Software & Updates and everything.. ..

That's what oldfred was telling you to do, but I'm glad you got it figured out and I'm glad everything seems to be working for you!

---

### Post by christopher_3 on 2014-09-17
Yeah i just noticed it right now, i didn't saw oldfred's post.. Anyways, thanks also for the help and giving me some ideas  Dave

---

### Post by dave131 on 2014-09-17
No problem, but I think others had more to do with getting it going for you, so I'll extend your thanks to the others that really helped.  We are all glad it is working for you!  Remember you can post any questions you might have - I post a LOT of questions and I don't worry about looking stupid.  Just because I don't know something and need help doesn't mean I'm any different from anyone else - everyone started from scratch!

Best of luck with your new install! ;)

---

