---
title: "[SOLVED] so i completely effed my Ubuntu partition"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by pjizz on 2008-09-11
hi all,

as a eager but inexperienced explore of linux, i've had more than a few bumps along the road.

most recently, i had a nearly perfect dualboot system set up, one partition running vista and one running ubuntu.  i started with a 7.04 live cd and, after working out getting Ubuntu to recognize the NIC, upped to 8.04.  the only issue I was still trying fix was getting the resolution up to the native 1440x900 and trying to enable compiz.  but the dual boot was working fine and everything was stable.

so i decided to install the xfce desktop environment and then kde.  i started a session in each just to test the waters.

the problem ensued when i started a KDE session.  i saw that it had some extensive display settings.  i saw that my monitor was detected as simply "Plug n Play" so I thought I'd pick the closest one to mine (bad idea, I know) and I also checked off widescreen instead of 4:3.  I got a popup telling me the configuration wasn't tested but I ignored it and bravely proceeded to restart x with CTRL + ALT + backspace.  ever since, I've got nothing.  i tried to hard reset and boot into an older kernel i had in GRUB, but nothing.  so I tried one of the failsafe modes next time.  still nothing.  the screen is way screwed, no matter how I boot up (except vista, thank god, still works fine)

i first thought, "hey, i'll just delete the whole partition and start over." after all, i have nothing there that's irreplaceable.  but, before I take that plunge, I had one question, and that's what this whole story has led up to:

If I delete the partition, will the GRUB bootloader be somehow lost and leave me with no way to access my Vista partition?  obviously this is a serious question, and I need to be absolutely certain (rare when mixing noob + linux, i know) before I delete the Ubuntu partition.

no rush in replying as far as I can tell, but I would appreciate any and all useful information.

thanks,


pjizz

---

### Post by pjizz on 2008-09-11
i read up a little bit, and found some information saying that, if I boot into grub then GRUB is installed to the MBR.  I also read that if i delete the partition, GRUB will therefore still be there but not be able to find the menu.lst file and i will be up the creek...

(h/t [http://ubuntuforums.org/archive/index.php/t-209927.html](http://ubuntuforums.org/archive/index.php/t-209927.html))

so, am I looking at having to reinstall the windows bootloader?  if so, anyone have any advice/previous experience on that process?

---

### Post by bboyshane on 2008-09-11
Hello,

No need to delete the partition, you could just live boot the Ubuntu CD , I would suggest the later 8.04.1 version, and point it to the existing linux partition. likely it would be the largest ext3 partition showing. the install will preserve your vista install, and also load a new grub bootloader.

You could also run a partition disc like gparted live, or some other partition manager. this would allow you to delete the ext3 partition, and the swap partition. Just leave them blank, and unallocated. the installer will then ask you if you want it to install in the blank space, and partition itself accordingly.

Shane

---

### Post by pjizz on 2008-09-11
so you're saying i could use a live disc to reinstall ubuntu over the entire partition?  i don't seem to remember overwriting just one partition as an option in the setup.

i remember it looking like this...

[http://apcmag.com/images/apcapc/howto/Dualboot_-_Vista___Ubuntu__Vista_first__images/ubuntu_05.jpg](http://apcmag.com/images/apcapc/howto/Dualboot_-_Vista___Ubuntu__Vista_first__images/ubuntu_05.jpg)

i'm guessing  you can do that in manual?  i also of course had the 7.04 disc and not 8.04 so maybe there is a difference.

also...no offense to my bboyshane :) but if 2 or three more people could chime in and say this sounds like a good idea then i'd feel a lot more comfortable about it.


pjizz

---

### Post by roccity1 on 2008-09-11
If you have the alternate cd then you can just reinstall grub.When you boot it up go to where it says rescue a broken system and it will load like its going to install it will give you a option to install grub again.

---

### Post by pjizz on 2008-09-11
quick clarification...is there a difference btw what people refer to as live cd's and alternate cd's???

---

### Post by Marshal0505 on 2008-09-11
> **pjizz said:**
> quick clarification...is there a difference btw what people refer to as live cd's and alternate cd's???

The alternate CD uses a text based installer and cannot be used for live sessions.

---

### Post by robert shearer on 2008-09-11
The alternate cd also has extra functionality including an option to repair/reinstall grub

---

### Post by pjizz on 2008-09-11
okay well i am just armed with a 7.04 live cd

---

### Post by pjizz on 2008-09-11
also to clarify...grub is working fine on my machine...it's the Ubuntu OS which is having issues...specifically, the screen is all jacked up and i can't really see anything.

does anyone care to confirm or deny bboyshane's advice?  i'm admittedly paranoid about losing my vista partition

---

### Post by robert shearer on 2008-09-11
You could do some reading here...
[http://www.herman.linuxmaniac.net/p24.html](http://www.herman.linuxmaniac.net/p24.html)

You should download and burn the live cd for the latest release 8.04.1 and use this to install.

Your link      [http://apcmag.com/images/apcapc/howto/Dualboot_-_Vista___Ubuntu__Vista_first__images/ubuntu_05.jpg](http://apcmag.com/images/apcapc/howto/Dualboot_-_Vista___Ubuntu__Vista_first__images/ubuntu_05.jpg)

and point are correct, now that Ubuntu is installed if you use the largest FREE space the installer will look for OTHER than your existing Ubuntu install.

To overwrite the existing ubuntu partitions you would have to use the manual partitioning option and I am not sure you want to or are confidant to do that?

To use the Guide/largest free space option again you would have to wipe the Ubuntu partitions as per bbshane's post.

Do some more reading, back-up back-up back-up, and ask again if you are unsure.

Full dual boot/install link   [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by pjizz on 2008-09-11
okay let me get some things straight.

1) use 8.04 live cd
2) i have to either
    a) use manual partitioning in the installer, or
    b) wipe the ubuntu partition 


now, the only question I still have...will wiping the ubuntu partition leave me with a worthless computer, since GRUB is currently the bootloader and it looks at menu.lst, which is on the ubuntu partition?

if this true, then i am totally comfortable using manual...that's how i used to install ubuntu.  if i did that, would i just select the ext3 partition and it would take care of overwriting everything?

..the goal is to reinstall ubuntu so that both ubuntu and vista are working, preferably without losing my vista partition.  am i ready to rock n roll?

---

### Post by robert shearer on 2008-09-11
Caveats   I am not a linux guru, just a humble user.I have no experience with Vista but do dual boot XP and Ubuntu on 5 computers and have installed Ubuntu a dozen times or so.

You should backup all your personal data from your vista install and if you have discs to re-install Vista and your programs there, then all the better.

Over the next few hours there will be more posters on the forums- time zones and all that- so you may want to wait and see what wiser heads advise.

However,I have found Ubuntu to be well behaved around other O/S's.

So,

1)use the 8.04.1 live-cd  the .1 is the latest version.There is some 300+ Mb of updates from 8.04 to 8.04.1 so it makes sense to use the latest version with its bug-fixes etc.

2)b yes, if you wipe the ubuntu partition then the first part of grub will stay in the MBR but will be unable to find the next part( and thus the old Ubuntu and vista bootup configurations) so won't boot.

2)a to manually partition you have edit the partitions yourself pointing the installer to the Existing Ubuntu partitions and setting them as "/" and "swap" (and "/home" if you originally had a home partition in your first install??) 
Then the partitioner will advise you of the partitions you have chosen to use(check that this is correct) If you accept then those partitions will be overwritten with the new install.

The other option is to boot up the live cd and from the System==>Administration  menu open the Partition editor.
Once there you can select your current Ubuntu partitions and delete them. This will leave you with your Vista partition and free space where the Ubuntu partitions were. Apply.and reboot with the live cd. 
 Then install as you did for the original install selecting the same partitioning option- Guided/largest free space (which you just created)
 

Whichever option you choose the install will progress and at the end will write a NEW Grub. It will look for installed O/S's and should ask you if it has them before it writes.

Again, these links have a full explanation with screenshots of what you should see at each step. do read them.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Again, as hardware differs and what works for me is not a guarantee that it works for you, as power cuts during install can crash things ,as windows is not linux,and as life is random   Back-up backup backup.

---

### Post by jordanStone on 2008-09-11
I wonder if I am having a similar problem,  I tried to get my laptop to display to a 22" 1680x1050 acer widescreen monitor,  In experimenting to get it right I swictched the display settings and logged in and out probably 10 times (the last five showing an ominous descent into craziness) Now I can't boot.  I can boot in recovery mode and have been able to explore stuff, problem is, I don't really know what to explore and what to do about it.  I can see /var/log/messages but there is so much there to parse through.  The boot hangs at a line which either says something like, checking battery... or running local scripts (/etc/rc.local)  but rc.local reads simply #!/bin/bash;exit 0

help!

---

### Post by bboyshane on 2008-09-11
hello, robert has some good advice on your options, as to repairing the grub as an other post recommended, that will do nothing for you. As you figured out. Honestly don't waste time with the version 7, go with the 8.04.1. As it is much better, just download the latest 8.04.1 iso and give it a go.

You can just point it to the ext3 partition and it will install there, and vista will be fine..... no worries, although personally, I would delete the ext3 and swap partitions first. But not necessary.

shane

---

### Post by pjizz on 2008-09-12
okay guys, i think i'm going to go for it here...i think i'm going to go ahead and boot up with the 8.04.1 live cd and install that way...tell the installer to overwrite the ext3 and the swap and cross the fingers.  i guess i could delete the partitions while booted with the live...i think i remember gparted being there or something...but i am still nervous about deleting them and then not being able to get back to vista should all else fail.

i'll let yall know how it goes.  thanks!



and jordanstone: this is probably my 7th or so ubuntu install (makes me an expert, i know) and i can easily say that everytime i've fooled with screen resolution and display issues, i always eff it up.  in fact, that's what happened this time.  good luck!  try posting over in video & multimedia?

---

### Post by pjizz on 2008-09-12
no luck no luck no luck

so i burned, checkd md5sum for the iso, got good results, and booted from cd.  i did the "Check CD for defects" option at the splash, and it sent me promptly to command line with the following message:

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu 12) Built-in shell (ash)
Enter 'help' for a list of built in commands 

```
and then a few seconds later...
```
(initramfs) [139.775146]ata1.00:revalidation failed (errno=-5)
```

it then descended into a madness of code repeating more of the same.  i then tried the "Try Ubuntu without any change to your computer" option...thought I might check the CD from inside Ubuntu.  that gave me the exact same response.

am i luckless or what?  maybe I should just order a 8.04 disc...but by the time it got here 8.10 would be out....d'oh!


so...anyone got ideas on the disc burning issue?  i burned it slow

---

### Post by robert shearer on 2008-09-12
Good you checked the iso download md5sum.
Now lets take it step by step.
First check the cd md5sum
[http://twiki.org/cgi-bin/view/Wikilearn/CdromMd5sumsAfterBurning](http://twiki.org/cgi-bin/view/Wikilearn/CdromMd5sumsAfterBurning)

and this link looks like it may be useful....
[http://ubuntuforums.org/showthread.php?t=814539&highlight=(initramfs)+failed+(errno%3D-5](http://ubuntuforums.org/showthread.php?t=814539&highlight=(initramfs)+failed+(errno%3D-5))

---

### Post by pjizz on 2008-09-12
okay the link you sent me, he says "> In Windows

So far, I don't know of a way.  so since i can't boot into linux that doesn't help.

from the thread you gave me, i'm going to try adding the generica.all_generic_ide=1 code to boot....brb

---

### Post by mdpalow on 2008-09-12
Good luck with getting this all fixed. I would recommend next time you get your system as close to perfect as you had it last time - you back it up.

We're always tweaking and playing. A good back-up could have you up and running again in minutes.

I know this is not new to you, but it's always funny to me how we tend to wait until we get further along before we start considering back-ups. :)

Check my signature below for the QuickStart link. I think you might like it.

Best wishes...

---

### Post by pjizz on 2008-09-12
right....i can't tell you how much i've lost due to laziness to backup data!

when i get this set up nice, i will definitely (we'll see) back it up

---

### Post by pjizz on 2008-09-12
verryyy interesting.  i added generic.all_generic.ide=1 at the end of the boot options and it quickly went to a prompt and i saw "unrecognized command" with the generic... modifier after it, but then it booted up into a live session.  now i only worry if trying to install with this disc will give me problems...anyone got ideas?

---

### Post by pjizz on 2008-09-12
more interesting developments...

i opened GParted only to see that several of my partitions are locked, including both the linux ones.

i'll attach a screenshot to show you guys what i'm talking about...

---

### Post by pjizz on 2008-09-12
well i got so close....but so far away still.

i went ahead and used the installer to erase the two linux partitions, and everything seemed to be going fine.

after waiting for the installer i restarted and crossed my fingers.  i noticed just before that the live disc was displaying the correct resolution for my monitor (a good sign, eh?) and the extra vis effects had been working too (another problem i had previously run into) so I was feeling pretty good about the install.

got to GRUB and saw that, as I hoped, the old ubuntu kernels were gone and i just had the new 8.04.1, along with good ole vista at the bottom.  

then i selected ubuntu and i just got the loading screen forever...you know black screen with orange loading bar bouncing back and forth.  i felt despondent and tried to go back and do the failsafe ubuntu.  it got stuck repeatedly saying some error about ata1 not being accepted.  oh well.  maybe i just wasn't meant to play ubuntu....

---

### Post by robert shearer on 2008-09-13
About now I would be taking the cover off and checking that the hard-drives and optical drives all have 80 wire cables if ata and that all ide/sata plugs are firmly connected.That all master/slave jumpers are correctly configured and then looking in the bios settings to see that all drives are recognised and configured correctly.

Have you tried booting with the 'ide generic' tag you used with the optical drive?

---

### Post by IndyGunFreak on 2008-09-13
Nevermind, I missed your last post...

Hope you get it worked out..

IGF

---

### Post by pjizz on 2008-09-13
well, im not a hardware expect so i don't know about opening the box....but i wouldn't bet anything is going on there.  it's a brand new machine and hasn't had any problems with vista.

a friend did suggest using a better burning program, so i think i will try that, especially since i had issues with the disc working.  i'm using nero 7 this time, but still the same media.  disadvantage: it might still not work. advantage: that would allow me to further pinpoint the problem.

i'm feeling more confident this morning...the more i mess up, the closer i get to success

ill report back later

---

### Post by pjizz on 2008-09-16
well all is finally well in linux land over here 

i got it to work with the newly burned by nero 7 live disc of 8.04.1.  i still had to add the all_generic_ide command to the boot options when i first installed, but everything is working fine now.  mark this is solved due to a) not fooling with a year old install cd and b) using a quality burning program

---

### Post by robert shearer on 2008-09-16
Glad to hear it.

---

