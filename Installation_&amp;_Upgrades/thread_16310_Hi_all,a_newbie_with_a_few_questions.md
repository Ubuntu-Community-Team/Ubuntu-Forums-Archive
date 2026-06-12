---
title: "Hi all,a newbie with a few questions"
date: 2005-02-20
forum: Installation &amp; Upgrades
---

### Post by orangestyle on 2005-02-20
Hi,i'm new here and also to Linux.
I posted a new thread becouse i don't know if it's right to open old threads.I want to learn more about linux and have it not installed yet.I downloaded Ubunto and burnd it on a disk.After reading here for 5 minutes i'm sure that disk is useless.
I just dragt it to the disk and burned it. ](*,) But that won't be the problem,i will make a new one on the right way.I use the program what came with my dvd burner(Pinacle).I have there an option to make the disk bootable,do i have to choose that option?I want to run Ubunto on my notebook,a Compaq Armada E500,with Windows2000 installed on it.I don't think i can just format the disk and install Ubunto but maybe i am wrong.And it's better for me to run 2 operating systems becouse i know nothing yet about Linux. Is my notebook fast enough to run Ubuntu with it's p3 and 192 mb?Can i find the drivers for the WiFi card?The tutorial says nothing about Linux.Does it automaticly detect the rest like sound and video?
I readed somewhere that not every version of Linux works on a notebook,is that right?
Well,thats it for now  :grin: 
Greetings orangestyle

---

### Post by Jad on 2005-02-20
Hi, Welcome to Ubuntu linux forums && welcome to linux world the world of Free sofware and Free minds,
With your Burn software you need to tick create image,
about wifi driver mostly it will be auto installed and configured, 

for best experience please read Ubuntu guide 
[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by fxgogo on 2005-02-20
Hi Orangestyle

First off, when burning the disc choose an option to 'burn disc from iso'. This will automatically sort out the bootable disc thing. Most software has this option. It should be in the 'new' project section of your software.

Right now to your laptop. I am busy writing this email on the exact same machine as yours, with the exception of only having 128mb of ram. I am currently using the Vector Linux distro on this machine very successfully. This laptop seems to be very friendly to linux.

Will the machine be fast enough for Ubuntu?  I am currently evaluating that myself. I ran the live cd on the laptop and it seemed fine considering it was coming from the cd. Vector Linux is specifically optimised for older hardware so it is really fast. You say you have w2k on your machine. If you are running that, then I will say you should be fine. Personally I found w2k very slow, so I used windows 98se on the machine as it was faster.

You can just format the disk an install, it will be part of the install procedure for Ubuntu. I do suggest you keep w2k on the machine for now as you are still learning linux and you might need to get things done in w2k if things go wrong in linux. I currently run windows 98se (for my daughters games) and Vector Linux seemlessly.

Your sound and video should be sorted out in the install, I had sound and display working great in the 'live cd' version. I can't be sure about the wireless networking as that was not activated in the 'live cd' version, but would think it would be fine as the vector linux distro which is a few months old now just needed a bit of configuring.

Tell us how you get on.

---

### Post by orangestyle on 2005-02-20
Hi,thanx for your nice reactions.

I downloaded also the livecd  of Ubuntu and burned it as you say fxgogo.
When i boot i get a loadingscreen of Ubunto and it loads till the end,but then
the computer restart by itself.I think the cd is burned the right way.
After this reaction i go try it on our normal pc to see what happens.
When starting up it gives 2 failed messages,but it goes to fast to read what it says.
I think i go try to install Ubuntu and see what happens,But are there risks for my hardware if i try some things?

Greetings orangestyle

---

### Post by fxgogo on 2005-02-20
That is wierd, I never got that. Pity you cant tell what the messages are. Sounds like you have the cd burnt right as it does load and show screens etc. 

Be carful with installing. Make sure you don't erase you wk2 partition. After that you should be ok. if you mess up linux, you can always start again. You might actually get some better response when you start the installation.

---

### Post by orangestyle on 2005-02-20
Hi fxgogo,

I just tried it on the other computer and the same problem,it goes not further after the loadingscreen.I go try to install it and see what happens. I have an external dvd burner and i can also put a harddisk in that case.So i take an ld harddisk and try to
intall it on that.I hope it works  :wink: 
I'll let you know what happend and...thanks

Greetings orangestyle

---

### Post by wallijonn on 2005-02-20
Orangestyle,

You may need to fudge with your BIOS settings, like turning off certain devices, turning off Video & BIOS cacheing and shadowing, removing any PCMCIA cards, turning off USB, disconnecting an external mouse and video monitor, etc. 

How far does it progress in the install process, then?

---

### Post by orangestyle on 2005-02-21
Hi Wallijohn,

I can't find that options on my notebook.When i press f10 while boot up i get the following options:

File -system information
      -save to floppy
      -restore from floppy
      -restore defaults
      -ignore changes and exit
      -save changes and exit

security
      -power on password
      -device security
      -system ids

advanced
      -boot options
      -device options -num lock state at boot----off
                               -multiple pointing devices---enable
                               -usb legacy support---enable
                               -internal display controller---secondary
                               -video out---ntsc
                               -paralel port mode---ecp
                               -intel speedstep technology---automatic
                               -docking base unique identification---disable
                               -processor number---disable

It's not that important for me to get it work but there were more people on this forum with the same problem and it would be nice if we can solve the problem for future questions.
I go install now the full version and hope it works.I'll tried it before but had some networkproblems with my wifi card and go try it now with the internal modem.
The error i get 3 times after the grub start is somthing like this;synapistic reset failed.
I hope you can see anything on my settings,or maybe you know where i can find some more settings?
 
orangestyle

[COLOR=Red]edit: when i tried to run another linux livecd a message came up that the bootprocess could not be continued becouse the disk might be burnd at a to high speed.maybe is this the same problem.i can make a new disk tomorrow,but now i ran out of disks  :razz: [/COLOR]

---

### Post by wallijonn on 2005-02-21
> 
-multiple pointing devices---enable
-usb legacy support---enable
-internal display controller---secondary
-intel speedstep technology---automatic


Those are the ones which I suspect may be contributing to your problem.

Do you have more than one mouse? Or specifically, do you have an external mouse installed along with your laptop built in pointing device? If so, please remove the external mouse.

The USB legacy support you can probably leave enabled for now.

Why is the internal display set to secondary? Do you have an external monitor connected? If so please disconnect it from the back of the laptop.

I know very little how 'speedstep' may affect your Ubuntu install.

DO YOU HAVE ALL YOUR DATA BACKED UP? Chances are that if you are running on a laptop with MSWindows installed that the whole disk is formatted for FAT32 or NTFS. If you install Ubuntu there is every possibility that you will erase ALL your data. Backup now, please.

How big is the disk drive and how much free space do you have on it? If there is enough you will have to do a "clean-up" and a "defrag". Start -> Applications -> System Tools -> Clean-up. Reboot twice and do defrags each time. 

Do you have a re-partitioning tool available? I used BootItNG with good success, but there are many re-partioning tools on the market that may suffice, like Windows Commander, Norton Ghost, etc.

Exactly what laptop do you have that you will be installing Ubuntu on?

---

### Post by orangestyle on 2005-02-21
Hi,

The laptop is a Compaq  ArmadaE500 with the following specs:
Armada Family
x86 Family 6 Model 8 stepping 6
AT/AT  COMPATIBLE 
196,080 KB RAM
(strange thing is,it is a pentium3 500mhz and the bios says its 866 mhz i believe)
The disk is a HITACHI_DK23BA-10 with 10 gigabyte (write cash is enabled )

I tried it also without the externel mouse but the same result.I have no external monitor connected so i will turn that option off.I have nothing backed up and go do it 
after this reply :-) ,thanks

I use Partition Magic and have now 2 partitions since yesterday,but i made them after i tried to run the LiveCD,so that can not be the problem.
Disk C is 6.72 GB and have 2.74gb free
Disk G is 2.58 GB and have it all free now
There is some space disapeared  while i was fighting with Partition Magic. :roll: 

I go now backup,clean and defrag and see what happens.
Thanks for your time  :wink: 

orangestyle

---

