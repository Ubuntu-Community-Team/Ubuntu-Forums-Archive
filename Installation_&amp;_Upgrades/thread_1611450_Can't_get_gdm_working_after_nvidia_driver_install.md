---
title: "Can't get gdm working after nvidia driver install"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by extremejosh on 2010-11-01
OK ill first say that im still a Linux noob so really would like the help and also i posted this problem a while ago but i have new info and i think i posted in wrong section last time. I recently downloaded and installed Ubuntu 10.10. I thought it was awesome...still do. OK, the problem is i was prompted to install some proprietary drivers and so i did but thats when the problems started. After reboot i couldn't get the GUI or gdm (not sure what to refer it to) to work. It goes directly to a terminal screen every time so i actually reinstalled Ubuntu and tried installing the drivers all different ways but no luck.  i also can get into recovery mode and do low graphics. the driver version im trying to get working is nvidia 260.19.12. my graphics card is a geforce 7 series cant remember the number i have a 32bit processor. so i hope someone can help me with this problem still real new to Linux and im totally lost as to what to do

---

### Post by nicoelba on 2010-11-02
HI!
I'm using the recovery mode too, cause on last upgrading from 10.04 to 10.10 my old Nvidia GeForce3 can't work. With linx I was using driver nvidia 96, and now I can see that I'm using the current.
How to fix the xorg.conf for using this driver also on the normal boot? 
It's not a problem using Compiz or enabling the desktop effects, I can survive also without them, but every time I switch on the PC I have to choose the recovery mode from the grub menu..
Thanks for help!

---

### Post by alexandari on 2010-11-02
Well ok then,why don't you run recovery mode and choose to fix X? I mean,this will revert things the old way. And my advice is to install the drivers from the "Hardware Drivers" ,so that you wouldnt have problems with such things (ok well you can but,you shouldnt)
And,when you installed the drivers,you say you got into a terminal screen on boot. Have you tried running some commands from there,like "startx" or something?

---

### Post by extremejosh on 2010-11-02
I'd like to also add that when i use the command "sudo /etc/init.d/gdm start" through the terminal i get a message back saying:


[B][SIZE=2]Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm start

Since the script you are attempting to invoke has been converted to an upstart job, you may also use the start(8) utility, e.g. start gdm


[/SIZE][/B][SIZE=2][SIZE=1]I have know idea what that means.[/SIZE]
[/SIZE]

---

### Post by extremejosh on 2010-11-02
OK, ill try to do something in recovery but the first time i tried to install the drivers was through system/administration/additional drivers then i rebooted and had the terminal problem thats when i started trying to install the drivers different ways

---

### Post by extremejosh on 2010-11-02
OK, i rebooted and when the terminal came up i logged on and typed "startx" this is what i got  in a was too much to type so only putting what i thought are main points:

[SIZE=2][B]
Fatal: Module NVIDIA not found......


NVIDIA: failed to load the NVIDIA kernel module. please check your system's kernel log for additional error messages.......

Fatal server error:
No screens found.

[/B][SIZE=1]Can anyone tell me what to make of this? also i would have tried other commands but im still a noob with ubuntu and i dont know any commands.[/SIZE]
[/SIZE]

---

### Post by extremejosh on 2010-11-02
OK, just wanted to add that the farthest i got was adding the drivers through ppa 

[B][SIZE=2]sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings[/SIZE][/B]

ok when doing it that way i reboot and come back on and everything looks fine it loads up good says drivers are activated in /system/administration/additional drivers/   but when i try to turn on visual effects it opens the additional drivers menu and tells me to activate the drivers ok so i run the nvidia-xconfig in terminal reboot and the problems start all over again no gdm 


i think ill have to reinstall and duel boot with windows till i figure this all out
and i truly did search for hrs for answers only to find other people  with this problem but no answers

---

### Post by extremejosh on 2010-11-02
OK, i found something interesting related to my problems guys if anyone has been looking at this thread.
check this link out right here [http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat ]("http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat")
ok some people posted the same thing on there that's been happening to me. the last comment though someone posted how they solved this problem 

> **Had similar issues installing, when I ended up at the terminal window I  re-ran nvidia-xconfig which saved in my home folder, moved it to  /etc/X11 and rebooted and all is working wonderfully now** 

ok well like i said before still a linux noob and i have know idea how to do what he/she says so can someone give me details on how? then maybe i can finally solve this.

---

### Post by extremejosh on 2010-11-02
I read some where that through terminal command "sudo rm /etc/x11/xorg.conf" will help but the only thing i get is

[B][SIZE=2]rm: cannot remove `/etc/x11/xorg.conf': No such file or directory

[/SIZE][/B][SIZE=1]now when i look in the directory itself i see the file [/SIZE][SIZE=2][SIZE=1]i thought maybe i can delete it myself but cant 
so if anyone knows a salution that would be great im still looking it up everywhere and i cant find one thing that works for me also if im doing something wrong please tell me
[/SIZE][/SIZE]

---

### Post by extremejosh on 2010-11-02
Bump...help??

---

### Post by extremejosh on 2010-11-02
OK, ive come a long way and i know this information is probably common knowledge to most of you but its new to me and most of it im learning by myself though experience i have just learn through my last attempt at reinstalling that i can get the drivers working perfect and everything but when i use the update manager to update my system thats when all the problems start so theres probably an easy solution for this but i don't know it. If someone was kind enough to tell me what i do that would be awesome 

thank you

---

### Post by blaszta on 2010-11-02
> **extremejosh said:**
> 
[B][SIZE=2]rm: cannot remove `/etc/x11/xorg.conf': No such file or directory


You currently doesn't have xorg.conf (Ubuntu can run without it), so you need to create one:

```
sudo dpkg-reconfigure xserver-xorg
```

Once you managed to install the driver, you need to tell driver to update the config file:

```
sudo nvidia-xconfig
```

If you're inside the gdm, you need to restart the gdm (CtrL + Alt + Backspace or reboot).

Then you might need to configure the display:

```
sudo nvidia-settings
```

---

### Post by extremejosh on 2010-11-03
> **blaszta said:**
> You currently doesn't have xorg.conf (Ubuntu can run without it), so you need to create one:

```
sudo dpkg-reconfigure xserver-xorg
```Once you managed to install the driver, you need to tell driver to update the config file:

```
sudo nvidia-xconfig
```If you're inside the gdm, you need to restart the gdm (CtrL + Alt + Backspace or reboot).

Then you might need to configure the display:

```
sudo nvidia-settings
```


hey man this is awesome thanks it worked great although i ended up doing it on 10.04 because i accidentally ruined my 10.10 disc im sure it will work on 10.10 too though so thanks

---

### Post by extremejosh on 2010-11-03
OK, im sorry i was a little hasty on marking this thread as solved just re downloaded Ubuntu 10.10 tried installing the nvidia drivers got the terminal screen on reboot tried the fix but didnt work this time  :(
OK, im reinstalling ubuntu again and hoping someone will be able to help me by the time its done ive tried at least a 100 ways of install these drivers but no matter what i do i get the terminal screen on reboot and i dont know how to fix it. and for some reason i cant find a single thread that explains this problem am i the only one out there that this is happening to? that cant be possible can it?

---

### Post by 1stcontact2035 on 2010-11-03
Well, just to have it on here, yes, I have a similar/same problem.  I tried installing nvidia drivers for a 7 series GeForce graphics card (now, out of curiosity, is your computer a HP Media Center PC made in 2007?  That would be TOO ironic, and might explain some things here).  From what I can tell, me being probably far more of a noob than you are at Ubuntu (this was my very first install), this was a botched install of nvidia but Ubuntu is acting like it did install so what happens is nvidia won't load the graphical interface w/o a working graphical processor, and therefore it kicks to what I'm just going to call DOS, whether its technically called DOS or not.

That's about all I know with any certainty.  Honestly I don't have a second computer so I don't want to actually work on this [my computer] unless I have a definite solution.  I had to as much remove and later reinsert my Windows drive in all of this, or else be out of a computer if anything went wrong (it did).  So all I can do is be a person to bounce ideas off of, but fortunately I know a few people who are more experted in Ubuntu and I'll try to bounce ideas off of them, too.

1stcontact2035

---

### Post by extremejosh on 2010-11-03
> **1stcontact2035 said:**
> Well, just to have it on here, yes, I have a similar/same problem.  I tried installing nvidia drivers for a 7 series GeForce graphics card (now, out of curiosity, is your computer a HP Media Center PC made in 2007?  That would be TOO ironic, and might explain some things here).  From what I can tell, me being probably far more of a noob than you are at Ubuntu (this was my very first install), this was a botched install of nvidia but Ubuntu is acting like it did install so what happens is nvidia won't load the graphical interface w/o a working graphical processor, and therefore it kicks to what I'm just going to call DOS, whether its technically called DOS or not.

That's about all I know with any certainty.  Honestly I don't have a second computer so I don't want to actually work on this [my computer] unless I have a definite solution.  I had to as much remove and later reinsert my Windows drive in all of this, or else be out of a computer if anything went wrong (it did).  So all I can do is be a person to bounce ideas off of, but fortunately I know a few people who are more experted in Ubuntu and I'll try to bounce ideas off of them, too.

1stcontact2035

ok wow this is pretty ironic i have the exact same computer as you and i hope we can come up with a salution to this problem

---

### Post by extremejosh on 2010-11-03
Ok. ive been searching and searching and i think i have installed these drivers just about every common way possible but i did find one [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) that i have not tried and im not sure if i should it says its not recommended 
and it also says it is strongly recommended that you already have Xorg working acceptably with the 'nv' drivers included. not sure what the means or how to check if it is

---

### Post by 1stcontact2035 on 2010-11-03
> **extremejosh said:**
> ok wow this is pretty ironic i have the exact same computer as you and i hope we can come up with a salution to this problem

I figured as much.  I've heard of people having this type of computer and running Ubuntu (which is why I gave it a try), but they also had seriously upgraded their hardware before they did anything (among other things, they were running a GeForce 8 or 9 series video card... I suspect the issue has something to do with this specific video card being manufactured for HP to tie into the Media Center hardware and software, which is all very Windows specific).  

I really hate to say this, but if you can spare even $60 to upgrade your video card, I think that would take care of the issue.  I think this type of video card we have when its stuck in this specific machine will tend to not be compatible with Ubuntu, for one reason or another.  I hope I'm wrong, though.

1stcontact2035

---

### Post by extremejosh on 2010-11-03
OK. i just finnished installing ubuntu again so i did my updates as usualy from update manager thins went to additional drivers menu and installed nvidia drivers again rebooted and it went to the terminal again tried a couple commands like start gdm  and  startx nothing worked so rebooted again went into recovery mode and back to where i start maybe there isn't a fix for me and i have to go back to windows till i can upgrade my system

---

### Post by extremejosh on 2010-11-03
Can anyone tell me if i might have better luck with more stable version like 10.04 or will that not help any?

---

### Post by extremejosh on 2010-11-03
Bump:)

---

### Post by extremejosh on 2010-11-03
OK the fix for my terminal screen on boot up that was givin to me earlier when i marked this thread as solved works perfectly for Ubuntu 10.04 but doesn't work at all for 10.10 so should i just switch to 10.04? I'm not sure of the difference of the two are. so if someone could list the difference of Ubuntu 10.04 and 10.10 ill make my decision  of whether or not to switch

---

### Post by extremejosh on 2010-11-04
New problem ive been installing and uninstalling different nvidia driver versions and now instead of a terminal screen a boot up i get a completely blank screen so ok fine ill boot up into recovery NOPE!! same thing blank screen OMG!!! i think ill have to reinstall the os now

---

### Post by extremejosh on 2010-11-04
Well ill leave this thread unsolved but looks like ill have to go down to ubuntu 10.04 there just doesn't seem to be a fix for my problem i hope that maybe when i upgrade my system i will finally be able to use 10.10

---

### Post by extremejosh on 2010-11-04
Ok there is one more error i want to post before i quit for good maybe it will help someone help me. after a fresh install i always do all the updates first ive just realised an error i always get after doing all the updates then rebooting. right before i boots up i get an error```
Modprobe Fatal: could not load /lib/modules/2.6.35-22-generic/modules.dep: No such file or directory found
``` but then my system boots up and everything looks perfect then thats when i do the driver installs and i get the terminal on reboot so maybe that first error has something to do with it?
idk maybe it will help maybe not im not holding my breath im already downloading another distro to try out

---

### Post by extremejosh on 2010-11-07
Just wanted to say that i found the fix that worked for me for both 10.04 and 10.10. before boot up i enter the grub and hit "e" and after quiet splash i type vmalloc=192M then hit ctrl+x to boot i tried 256M at first but 192M works best for me hope this helps other people. but if someone could tell me how to make this permanent so i don't have to go into the grub every time i start up that would make things so much better

---

### Post by nicoelba on 2010-11-08
Follow this guide: 
[http://www.microsmeta.com/dblog/articolo.asp?articolo=976](http://www.microsmeta.com/dblog/articolo.asp?articolo=976)

for installing the driver.
And for enable Compiz follow this:
[http://www.microsmeta.com/DBLOG/articolo.asp?articolo=927](http://www.microsmeta.com/DBLOG/articolo.asp?articolo=927)

Worked for me!:P

I'm using an old GeForce3 Ti200 on Ubuntu 10.10

---

### Post by extremejosh on 2010-12-02
i marked this thread as solved a while back and it is solved but i have come across a weird observation. now with most linux distributions i have to put into the grub vmalloc=192M or 256M or what ever # to get the nvidia drivers working properly so i have been doing this for a while now but out of pure luck i have found out that removing the TV tuner WinTV-HVR-1600  i dont have to use the vmalloc fix anymore everything works perfectly i have tested this with multiple distros putting it in and removing it so can anyone tell me why this is and what i should do about it? the tv tuner isnt a big deal i never used it but if there is a simple permanent fix for this ill listen

---

### Post by iosuna86 on 2010-12-16
I had the same issue and I have finally solved it.

Here is what I did.

1. I downloaded the driver from NVIDIA's website (NVIDIA-Linux-x86-260.19.29.run)

2. Then, I opened a terminal
```
sudo apt-get --purge remove xserver-xorg-video-nouveau 
```

3. Then I hit CTRL+ALT+F1 in order to switch to command-line.

4. Typed: 
```
sudo init 3
```
```
sudo stop gdm
```

5. Then I installed the drivers manually.

I went to the folder in which I had downloaded the drivers, which was Downloads

```
cd /home/--username--/Downloads
```

Then I run the package

```
sudo sh NVIDIA-Linux-x86-260.19.29.run
``` 
or if you don't have any other .run files in that folder
```
sudo sh *.run
```

6. The NVIDIA driver installation will start, you will have to accept the license, then say Yes to something regarding the X server. It will also try to purge your conflicting/previous NVIDIA drivers.

I have done it twice and it had worked like a charm.

I hope that can solve your problem too.

---

### Post by MTHarden on 2010-12-29
I have a GeForce 6600 on 10.10 and I can't get this to work either. Even trying iosuna86 solution results in rebooting and crashing. 

I don't know where to edit grub to add in vmalloc=192M so that is also slowing me down. I looked for /boot/grub/menu.lst but I don't have that file.

---

### Post by noctiphile on 2011-01-06
I have a problem getting my Nvidia card working all of a sudden so would like to know what you had to do.

> **extremejosh said:**
> I read some where that through terminal command "sudo rm /etc/x11/xorg.conf" will help but the only thing i get is

[B][SIZE=2]rm: cannot remove `/etc/x11/xorg.conf': No such file or directory

[/SIZE][/B][SIZE=1]now when i look in the directory itself i see the file [/SIZE][SIZE=2][SIZE=1]i thought maybe i can delete it myself but cant 
so if anyone knows a salution that would be great im still looking it up everywhere and i cant find one thing that works for me also if im doing something wrong please tell me
[/SIZE][/SIZE]

I don't see why that wouldn't work. Try
**ls -l /etc/x11/xorg.conf**
to verify that the file exists, and look at the permissions.  I thought sudo would automatically provide write/delete permissions, but maybe not.

---

