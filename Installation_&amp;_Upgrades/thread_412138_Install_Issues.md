---
title: "Install Issues"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by patrickalexson on 2007-04-17
Ok im sorry if there are multiple threads set aside for this but im short on time so I posted here.

Im new to Ubuntu so keep that in mind although im very fluent with computers and installing OS

My computer specs are as follows:

AMD Athlon 64 4000+ ~2.4GHz
ATI Radeon x700 PRO 256mb GDDR3 PCI Express
1 40GB WD IDE HARDDRIVE << Im installing Ubuntu to this, ive set the bios to not read the sata
1 80GB SATA HD
1 GB DDR (not sure on speed)

Ok so I start my computer, goes into the boot sequence, I boot the cd

Then it gives me the options to check cd for defects, install, etc

I pick install or whatever it is and I go from there. During the boot sequence of the cd where it shows the logo and the animated bar scrolling back and forth it freezes.

First off, the entire screen is in grayscale (and a bit rough as in pixel quality smoothness)

The graphics of the animated bar are distorted after it scrolls from left to right on the first flyby

It does continue and since I dont really give a heck about the screen quality during install as long as it fixes itself afterwards, I wait

Then after the loading bar stops and it begins to install or boot, it reaches 80 - 90% and locks up completely

WHY? Some hardware conflict? I have tried it on different cd drives, with different disks downloaded at seperate times.

---

### Post by kornhead127 on 2007-04-17
Try this. Highlight the install menu item, and press F6 you will see some text at the bottom right. make the text look like this 

```
blahblahblah splash no apic --
```

hope that helps.

---

### Post by patrickalexson on 2007-04-17
Dang that was fast, alright will give it a try.

Thanks man

---

### Post by patrickalexson on 2007-04-17
Ok now I have a new problem, the booting doesnt lock up although the graphics are still pixely and in grayscale, but now its telling me that it failed to start the x server (graphical interface) and that it might not be set up correctly.

I looked at the report that it compiled and the fatal error is that 'there are no screens found'

Im not real sure what the problem unless it doesnt like my hardware.

Any help on this?

---

### Post by kornhead127 on 2007-04-17
"no screens found" means it doesn't like the combination of the video card and the driver. When it dumps you back to a terminal type this...
```
sudo dpkg-reconfigure xserver-xorg
```

Follow the instructions and when it is complete type startx hopefully that helps.

---

### Post by patrickalexson on 2007-04-17
Its not wanting to dump me back to the terminal, it stays on the blank screen with the cursor underscore blinking, is the terminal loading or is that the terminal itself because it doesnt accept commands, it just allows you to display text.

---

### Post by patrickalexson on 2007-04-17
Should I type it in under the boot options (F6)?

---

### Post by kornhead127 on 2007-04-17
Ok press control+alt+F1 and you should get to a terminal.

---

### Post by darkwarrior on 2007-04-17
HI Guys new to linux as well , i have a boot problem downloaded , and burnt the ubuntu 6.10 to cd , install went perfectly (It seems) and the after rebooting the 'grub' loaded and gave me a error 18 not sure what this is, the machine is a Pentium 3 , 256MB Ram a biostar bios, a compaq 18gig scsi HD a 52 x cdrom, adaptec 2940 ultra wide scsi card, i erased the drive prior to installation and had ubuntu auto partition the drive, i have reinstalled it but to no avail same error message comes up any help would be greatly appreciated....

---

### Post by patrickalexson on 2007-04-17
ok what I am doing now is switching to my onboard graphics (ATI Radeon Xpress 200 - 64mb or something) and see if it works this way, from what I am seeing though it still looks grayscale and pixely.

It asked me for the bus number of the PCI Express Graphics Card so I got to see about getting that.
Any other things I should be aware of.

---

### Post by patrickalexson on 2007-04-17
Ok wow never mind it works now, I think. Give me a sec to find out. It booted straight into Ubuntu.

---

### Post by kornhead127 on 2007-04-17
Ok even with your onboard video card, Linux must be configured to use that card so I doubt it will work off the bat.


As for the other guy this is what I found...
> 18 : "Invalid or unsupported executable format"

This error is returned if the kernel image boing loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD).

Are you sure the install wen without a hitch? It seems the vmlinuz file is corrupt or something. This is beyond my scope and I'm afraid I can't help you.

---

### Post by kornhead127 on 2007-04-17
Oh ok thats cool. Now you can look up how to get that particular video card working.

---

### Post by cyrusdh on 2007-04-17
Well I have the same issue, the "failed to start x server issue".  I am using the live cd and this happens during the beggining stages of setup, actually i dont even get to setup this is when it is trying to boot.  After I get the error I cannot get back to at erminal, even when i do the cltr+alt+f1 it takes me to a new terminal but I have no prompt just a blinking cursor.  I read somewhere that I should boot into "recovery" mode but when i do f6 = boot: rescue, after a few seconds it gives me an error saying failed to mount xxx.... also I tried using the command live-expert and I once again recieved the same failed to mount error...Just to emphasize, i have not installed ubuntu at all, i just popped in the cd and i tried doing "start or install ubuntu" and the second option" install in safe grpahics mode".... i have been attempting to resolve this problem for the last few days so any ideas will be greatly appreciated.

---

### Post by kornhead127 on 2007-04-17
Ok if you can't get a terminal you can start in recovery mode, but you did it all wrong. after you press f6 change the text so it looks something like this...

```
 blahblahblah splash single --
```

---

### Post by patrickalexson on 2007-04-17
Ok great it works and I just installed although I think it locked up when it asked me to remove the cd from the drive when it restarted but no worries. Ive just manually restarted and its booting so looks good and it gives me the os choice menu so I can boot my Vista Premium 64bit or Ubuntu whenever I feel like it.

Im very happy. This went better than my failed attempt to install Gentoo Linux. : ]

---

### Post by patrickalexson on 2007-04-17
Thanks man, very grateful

---

### Post by cyrusdh on 2007-04-17
Okay, well we are half way there.  The good news is I got to a command prompt and ran the sudo dpkg-reconfigure xserver-xorg command and successfully started the x server which allows me to navigate the operation system,  but now how do i get back to the install.

---

### Post by kornhead127 on 2007-04-17
If you've gotten into the graphical user interface then the install should be on the desktop. If not navigate your way to /home/ubuntu/Desktop.

---

### Post by cyrusdh on 2007-04-18
Yea I found the install, however I am having a completely different problem now :(... once i get through the first few pages of the install (i.e., setting up the partiion, i get to the screen (6 of 7) which asks me to enter username, etc... well my keyboard is not functioning at all.  Now before I run the install in ubuntu, i can use the keyboard perfectly within ubuntu, but once i begin the "install" the keyboard goes to **** and does crazy stuff.  For instance if i hit 1 it will start scrolling n's all over the place... any ideas?  I have tried going into the keyboard settings but cant seem to get it to change.

---

### Post by FeelTherush1 on 2007-04-18
i have an ATI X800 and get the same problem as you. I am pretty sure that the driver for the ATI X series is not up to sp[eed... i have come to several ends on how to fix this but it seems that it must be installed in order for this update to take place and be able to use ubuntu. the live cd version will not save the drivers i think. also when i do the "startx" it says the server is already in use and refuses to restart from me... any suggestions for the both of us?

---

### Post by kornhead127 on 2007-04-18
cyrusdh:
[INDENT]Try downloading an alternate install cd and running that instead. It's a text based installer and should give you no problems at all.[/INDENT]

FeelTherush1:
[INDENT]As I've stated before (I think) the 'radeon' driver supports up the X850 and after that you need the 'fglrx'. In your case you will use the 'radeon' driver. Don't use the 'ati' driver. It is proprietary and most likely won't work with the X800.[/INDENT]

---

### Post by klein de usa on 2007-04-18
hi
i have one question for everyone that is having problems in this post, are you trying to install a pci video card in a mother board that has an on board video card ? 
because i'm having the somewhat same problem, and i'm finding that the pci buss adress in xorg.conf isn't right ?

---

### Post by kornhead127 on 2007-04-18
They are trying to install AGP video cards. AGP is on the PCI:1:0:0 bus PCI is on the PCI:0:1:0. Which video card do you have, maybe I can help?

---

### Post by badboy_24u on 2007-04-18
[SIZE="4"]HI, just wan't to ask if ubuntu 6.06 desktop version support raid 0 and 1? thank you[/SIZE]

---

### Post by kornhead127 on 2007-04-18
[SIZE="5"]Yes, Ubuntu 6.06 Supports RAID 0 & 1![/SIZE]

---

### Post by klein de usa on 2007-04-18
hi 
i have a gx200 and am trying to install a radeon 9250 pci, the problem is dell doesn't disable the on board video it just bypasses it if there is another video card installed and edgy is picking up the on board card and not the pci card .
install goes well with the alternate cd right up to the reboot then when it go to the login screen i get a black screen with a blinking curser . when the xserver takes over i think and uses the xorg.conf file it is sending all the info to the on board video instead of the pci card thus the black screen 
i tryed the live cd and it went to black screen  with a blinking curse when it should of brought up the desk top 
so i don't know if it is the same problem i can change the driver in the xorg.conf file to vesa and change the pci address and it will use the pci card it flickers a lot , i can't get the xorg.conf file and the ati driver configured right 

this is the second pci card i tried in two diffrent computers both the same thing one this dell gx200 and a dell 3000   i think it has to do with the bios , on board video and no way to disable the on board video no jumpers all bios controled on the other hand puppy and dsl work with no problem on the new pci card so that leads me to maybe there is a bug in edgy ??????????

---

### Post by kornhead127 on 2007-04-18
Do an lspci at the terminal and paste the output please.

---

### Post by klein de usa on 2007-04-18
ok 
the computer i'm working on isn't hooked to the internet so what you need to know i will have to tipe here

pci 01:00.0  on board video 
pci 02:07.0  vga on the pci card dsub connector  ati rv280 radeon 9200 pro
pci 02:07.1 hd connector on the pci card  secondary  ati rv280 radeon 9200 pro


the box says 9250 though pci 02:07.0 is what i would like to use as my out put

---

### Post by kornhead127 on 2007-04-18
use PCI:0:2:0 it looks like both the card and the chipset are on the same bus. Any way yeah try PCI:0:2:0. As you can tell from my sig. I was pretty much in the same boat as you, except I have an agp Radeon 7000 so it was a much easier fix. Anyway hope that helps.

---

### Post by klein de usa on 2007-04-18
hi
no that didn't fix it, it made it worse, but it did give me an idea i will try what i'm thinking and tell you if it works.

---

### Post by kornhead127 on 2007-04-18
Well if it isn't PCI:0:2:0 then it must be PCI:0:1:0.

---

### Post by klein de usa on 2007-04-19
ok
pci:0:1:0. didn't work either, so what i'm going to do is reinstall edgy fresh and begin from there when i get that done, i'll let you know what i found.

---

### Post by kornhead127 on 2007-04-20
I think it should have been PCI:2:0:0 but if you got it working thsi is very irrelevant right?

---

