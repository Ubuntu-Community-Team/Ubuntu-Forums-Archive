---
title: "cannot install any ubuntu"
date: 2014-12-25
forum: Installation &amp; Upgrades
---

### Post by tuomas4 on 2014-12-25
so the problem is that i have tried installing 22 different distros for an desktop computer by using it's hard drive in place of this one that im now using.
also i tried to install various light versions of ubuntu to an asus eee pc 4g (701) without success. if any of you could recommend what os to use in that kind of netbook i would appriciate it dearly.
i did try to install the easypeasy and the eeebuntu too and neither of them worked. i got the errrno 5 error of input/output 6 different times on all of the alternative post 12.XX versions all the way to an 8.XX versions, i have tried 3 different usbs. to sort out that the usb is damaged? i have used universal usb installer on windows 7 versions 1.9.5.5 and 1.9.5.8 and they seem to install the .iso files just right.

it may be that the eee pc's hard drive has come to its read write limit due that it is an ssd drive? i need to buy a new hard drive to it to continue its installations.
but the strange thing is that the asus eee pc's original asus based os works just fine. i just want to have a bit of more free space from the hard drive when i eventually get it.

but to the current and more important issue.
i also get errno 5 input/output error on an desktop computers hardrive, it is an barracuda 7200.7 160 gigabyte seagate drive. and it has no broken things in it, i managed to check this by one lubuntu version that i managed to run via an usb stick that i have used to try these different ubuntu os's. the furthest ive gotten on these numerous installation attemps has been to the desktop via the usb on this barracuda, in versions of ubuntu 10.10 and an lubuntu 12.XX 

the issue that i expect to run into later, and perhaps the reason i cannot run the installations beyond different points is that, i try to install ubuntu via usb, using entirely different computer than the one where it is going to be, once i manage to install an working version of ubuntu. this computer that i am currently using the forums runs on 64 bit system, the older one is 32 bit. so i try to install a 32 system to an hard drive described above?? maybe this is also wrong, but the problem is the desktop may not be rescueable due i cannot enter even bios on it when it is connected to the old desktop pc. so i try to use this ''newer'' computer to run the installation to its working hard drive?

i have managed to format the barracuda by using lubuntu 12.04 32bit alternative but it didn't install itself on the hard drive most likely due this computer is 64 bit system?

thank you from your time!! happy holidays as well! :smile:

---

### Post by Bashing-om on 2014-12-25
tuomas4; Hi ! Welcome to the forum .

Tell us again the system that you are trying to install ubuntu onto ? Is it a UEFI system ? How much ram is installed into the machine ?

Have you verified the md5sum of the .iso file ?
Have you verified the USB burn ?

After the verifications, the next thing is to see how the system performs in the "try ubuntu" mode. IF all works, then install to the hard drive.


[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by tuomas4 on 2014-12-25
the md5sum of the .iso is correct
the usb was not, now i try to reinstall it to the usb and check again.

the thing is that im trying to install the linux to an hard drive that i connected from the older device that i have little info of other than it has 1g of ram. it is an hp pc. and used to have an windows xp on it.
it doesnt boot to the bios setup nor can i currently run linux via usb on it?

heres the windows disk manager window, i didn't really understood what you meant?

[IMG]https://38.media.tumblr.com/34a31a9bb461fc6bdeee989e3b9afc60/tumblr_nh5evpImzv1sc476ho1_1280.png[/IMG]

//// edit   here is the md5sum window. it doesn't still match?

[IMG]https://31.media.tumblr.com/62aa1af79385190b960cdc6497be48ea/tumblr_nh5f2eoSNR1sc476ho1_1280.png[/IMG]

---

### Post by Bashing-om on 2014-12-25
tuomas4; Hey;

We are making progress.

As you have/had XP on the system, we are looking at a bios based firmware, not UEFI.

OK with but 1 Gig of ram, as it takes 2 Gigs for a good experience with the top of the line edition ubuntu  -  you want to consider a lighter release. May I suggest Lubuntu ?
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Verify the MD5sum from a Windows system:
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)

Burn the .iso as an image from Windows:
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073) <-sudodus/Howto make USB boot drives
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

install tutorial:
[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

---------------------
Follow those, get a useable liveUSB and if there continues to be a problem, we next look at the graphics situation.

[INDENT][INDENT]looks doable to me
[/INDENT][/INDENT]

---

### Post by tuomas4 on 2014-12-25
downloaded the win32diskimager to try as a different usb tool.
downloaded the lubuntu 14.10, that i seemingly already had but just to be sure did so again.


now the win32diskimager wrote it. but that i try to access it with win7 it gives an error like this?
[IMG]https://33.media.tumblr.com/9b752bd9a5c5a8e7ae81386356ea8718/tumblr_nh5i0rGuRh1sc476ho1_1280.png[/IMG]

---

### Post by Bashing-om on 2014-12-25
tuomas4; UHMMMM...

Are you trying to impose ubuntu ( ext4 filesystem) on Windows file system (NIFS) ? No can do.

Take the easy way to install ubuntu.

Verify the .iso file
Burn the liveUSB
Set in bios to boot the liveUSB as 1st boot priority
Boot the liveUSB to the Boot options screen ( As soon as the bios screen clears depress and hold the right -shift- key -> language screen, escape to accept the default -> boot options screen) and choose "check disk for defects". Let the disk check complete and reboot.

Now you are ready to see what (L)ubuntu is -> boot up in "try ubuntu" mode from the boot option. Play with the system in this mode. 

All is functional ? Then;
Install (L)ubuntu
Start the installer and choose " install ubuntu alongside of" .
I do recommend NOT to check the boxes for "install 3rd party software" , "install updates" ; as we do not know what the graphics situation is or the hard ware the system has. These are things we can take care of better after the install completes. It is simple to do after the install.

The install wizard will take care of everything - as you are presently under the 4 primary partition limit.
All you need to do in the install process is answer a few simple questions: Your location, verify your keyboard, user name you will use, and your system password. Do not forget this password - tattoo it on your eyelids ! -  in 'buntu the password is critical .

Done 

Reboot into ubuntu, tell us the situation and we will advise on completing the install by doing the updates and installing the 'extras' .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by tuomas4 on 2014-12-25
managed to unpack the lubuntu 14.04 i358.iso to an different usb, due the win32 unpacker messed up my kingston. it was 4g and now it has only 700mb's :// but now i got the lubuntu working finally to the older desktop! thank you Bashing-Om!

---

### Post by Bashing-om on 2014-12-25
tuomas4; Outstandingly great !

Pleased you are up and running.

[INDENT][INDENT][INDENT]cook'n with Crisco now
[/INDENT][/INDENT][/INDENT]

---

