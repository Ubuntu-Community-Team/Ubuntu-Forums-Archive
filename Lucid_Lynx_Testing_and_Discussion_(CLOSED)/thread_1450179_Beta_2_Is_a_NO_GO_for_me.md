---
title: "Beta 2 Is a NO GO for me"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ToxicBurn on 2010-04-08
I just burned the ubuntu-10.04-beta2-desktop-i386.iso
 
booted from cd to get
 
( process : 330 ) : Glib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
 
 
[COLOR=red]Live CD iso = ubuntu-10.04-beta2-desktop-i386.iso


[COLOR=RoyalBlue][B]UPDATE : this problem can be fixed by following the instructions below

[/B][/COLOR][/COLOR][COLOR=RoyalBlue]**                     Originally Posted by [B]kansasnoob**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9097425#post9097425")[/B][/COLOR]                 
                 [I][COLOR=RoyalBlue]**from the boot menu press F6 which will display some boot options,  then just press the Esc key. You'll now see that the "boot parameters"  are displayed at the bottom of the screen. Just use the Backspace key to  remove **[B]only "quiet splash".

Then just hit Enter & try to boo[/B][/COLOR]t
[COLOR=Red]
_**Also I had to Remove my 2nd Monitor to get this to work . Having Dual monitors will cause or be part of the problem getting beta 2 installed**_[/COLOR]
[/I]

---

### Post by atlee on 2010-04-08
did you try and re-burn the CD at a lower speed, have you checked the CRC on the ISO to make sure it's not corrupt?

---

### Post by ToxicBurn on 2010-04-08
yeah i am re-downloading the iso now will post back after another burn fingers crossed

---

### Post by vger7 on 2010-04-08
> **ToxicBurn said:**
> I just burned the ubuntu-10.04-beta2-desktop-i386.iso
 
booted from cd to get
 
( process : 330 ) : Glib-WARNING **: getpwuid_r(): failed due to unknown user id (0)


I've been getting that error for a few days now in Lubuntu, with is the same as the main release but with the LXDE desktop. I've been updating everyday fixes/bugs. But if you just wait a bit it will still boot... after a long pause.  At least it does using VB.

---

### Post by ToxicBurn on 2010-04-08
ok will try again i just tried again with a new iso downloaded and burned and still same error .
 
why is this not a problem for everyone it doesnt sound like a hardware issue.

---

### Post by ranch hand on 2010-04-08
Did you check the md5sum.

I did not test the 32bit CD in ISO testing but there were not many problems with it booting there.

---

### Post by ToxicBurn on 2010-04-08
going to re-download a 3rd time and check the  md5sum this time .
 
will post reply in a few min

---

### Post by -Robert- on 2010-04-08
You're not the only one. ;)

On my desktop I just can't successfully boot 10.04, i tried several things. The Live CD hangs at the Ubuntu logo with the red and white dots (Plymouth?), the only thing I can do is press the shutdown button. After doing so I get the same message as you see. 

[screenshot]("http://i44.tinypic.com/wmu6o.jpg")

I am pretty sure that it's not a hardware problem or a problem with the CD itself.

Same problem: [https://bugs.launchpad.net/ubuntu/+bug/532984](https://bugs.launchpad.net/ubuntu/+bug/532984)

---

### Post by nix.peter on 2010-04-08
I know a lot of people love using CD's however i have similar problems with Operating System Installs kind of like what you guys are describing now.

If you can, try using a thumb drive (usb flash drive to some people), and using Unetbootin to load the image on the drive. This always ensures a good install for me, but that just me.

Just my 2 cents guys, its worth a try if your having problems still.

I also like using this method because then i don't have to burn a million discs which i used to do :x

---

### Post by ToxicBurn on 2010-04-08
wow i guess no Lucid for me for a few days hope a daily build wil fix this in a few days.
 
im bummed out now :(
 
 
i confirmed this on launchpad

---

### Post by ToxicBurn on 2010-04-08
> **nix.peter said:**
> I know a lot of people love using CD's however i have similar problems with Operating System Installs kind of like what you guys are describing now.
 
If you can, try using a thumb drive (usb flash drive to some people), and using Unetbootin to load the image on the drive. This always ensures a good install for me, but that just me.
 
Just my 2 cents guys, its worth a try if your having problems still.
 
I also like using this method because then i don't have to burn a million discs which i used to do :x
 
 
will give this a shot thanks

---

### Post by ranch hand on 2010-04-08
This is a major downer.

---

### Post by thatguruguy on 2010-04-08
> **nix.peter said:**
> I know a lot of people love using CD's however i have similar problems with Operating System Installs kind of like what you guys are describing now.

If you can, try using a thumb drive (usb flash drive to some people), and using Unetbootin to load the image on the drive. This always ensures a good install for me, but that just me.

Just my 2 cents guys, its worth a try if your having problems still.

I also like using this method because then i don't have to burn a million discs which i used to do :x

+1.  I have had MUCH better luck with thumb drives than with CDs.

---

### Post by ToxicBurn on 2010-04-08
just used Unetbootin and got to splash screen with same error 
 
for me the Live cd is NO good just will not work.
 
now i guess i can try the alternate install CD 
 
crosses fingers lol

---

### Post by -Robert- on 2010-04-08
> **ToxicBurn said:**
> just used Unetbootin and got to splash screen with same error 

Me too.

Maybe I just have to be a little bit more patient, after all..10.04 is still beta. 
I just wanted to see how it looked and what changes there were made, the Live CD is perfect for that purpose.

---

### Post by ToxicBurn on 2010-04-08
funny thing is i had no trouble with the alphas or beta 1 lol
 
sofar beta 2 is a step backwards lol
 
well not really but crazy how this bug slipped by

---

### Post by -Robert- on 2010-04-08
I tried Beta 1, Beta 2 and a Daily Build (several days ago), they all won't work.

Here are a few threads with the same kind of problems:

[http://ubuntuforums.org/showthread.php?t=1441392](http://ubuntuforums.org/showthread.php?t=1441392)
[http://ubuntuforums.org/showthread.php?t=1439638](http://ubuntuforums.org/showthread.php?t=1439638)
[http://ubuntuforums.org/showthread.php?t=1361231](http://ubuntuforums.org/showthread.php?t=1361231)

---

### Post by emarkay on 2010-04-08
Hey, CD's are how it's distributed, so while USB and DVD installs are fine, this could be a major issue in this case.

Can't do a complete reinstall now, but will tomorrow.

IMHO it's prob something simple, but those with this issue need to validate and verify, and then file a Launchpad bug.

---

### Post by ToxicBurn on 2010-04-08
I filed what i could in launchpad but i had to do it from with-in windows now all i can do is sit and wait lol i hate that.

---

### Post by ToxicBurn on 2010-04-08
Well after a full eve of messing with beta 2 just trying t get it to install i have to call it quits and go back to 9.10 
 
The Live cd image released by Ubuntu has to be realy messed up it just wont boot and install i will wait untill i can get a daily build on the 12th or 13th before i try again 
 
sad day

---

### Post by Didius Falco on 2010-04-08
I know it's a bummer that you couldn't install it, but you **did** file a bug report, and will contribute to making many others lives easier as a result.

Use the warm glow from being a good beta-tester to dry those wet eyes. :KS

---

### Post by kansasnoob on 2010-04-09
I have something else I'd appreciate those having trouble with the Live CD to rule out, but first if anyone hasn't already:

#1: Check the md5sum of the iso.

#2: Be sure to run the "Check CD for defects" test. Note: you must now press a key (any key) to get the usual "menu" w/options.

#3: If both of the above passed then from the boot menu press F6 which will display some boot options, then just press the Esc key. You'll now see that the "boot parameters" are displayed at the bottom of the screen. Just use the Backspace key to remove **[COLOR="Red"]only[/COLOR]** "quiet splash".

Then just hit Enter & try to boot.

---

### Post by cristianrosa on 2010-04-09
> **-Robert- said:**
> You're not the only one. ;)

On my desktop I just can't successfully boot 10.04, i tried several things. The Live CD hangs at the Ubuntu logo with the red and white dots (Plymouth?), the only thing I can do is press the shutdown button. After doing so I get the same message as you see. 

[screenshot]("http://i44.tinypic.com/wmu6o.jpg")

I am pretty sure that it's not a hardware problem or a problem with the CD itself.

Same problem: [https://bugs.launchpad.net/ubuntu/+bug/532984](https://bugs.launchpad.net/ubuntu/+bug/532984)
I just confirmed in the bug report, but I think there are many bugs with rather similar symptoms around. i.e. I only get the splash freeze you have when having more than one monitor plugged. However when having a running system with one monitor, at shutdown/reboot I see the message in your screen capture anyway. In my case it is almost certain that it is a bug with the new nouveau drivers.
EDIT: I found that there is already a bug report on this issue [533135]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/533135") Booting lucid + nouveau + more than one display freezes on boot

---

### Post by nix.peter on 2010-04-09
I hate to be the bringer of bad news but i used my flash drive, unetbootin, and the 64 bit beta 2 image and im posting this from the live 10.04 beta 2 right now.

I am using 64 bit though, have you all been trying 32 bit?

---

### Post by 67GTA on 2010-04-09
Ubuntu and Kubuntu 10.04 beta 2 64bit both boot fine on three different PC's. Maybe a 32bit problem?

---

### Post by geojorg on 2010-04-09
Remove quietsplash from the kernel line and it will work. I had that exact problem few weeks ago.

---

### Post by -Robert- on 2010-04-09
> **kansasnoob said:**
> 
#3: If both of the above passed then from the boot menu press F6 which will display some boot options, then just press the Esc key. You'll now see that the "boot parameters" are displayed at the bottom of the screen. Just use the Backspace key to remove **[COLOR=Red]only[/COLOR]** "quiet splash".

Then just hit Enter & try to boot.

That did it for me, I just booted the Live CD (Beta 2) and I actually saw the desktop! :)
I thought I tried that adjustment before, but then it wouldn't work...:confused:

Thanks Kansasnoob (edit: and Geojorg)!!!

---

### Post by kansasnoob on 2010-04-09
> **-Robert- said:**
> That did it for me, I just booted the Live CD (Beta 2) and I actually saw the desktop! :)
I thought I tried that adjustment before, but then it wouldn't work...:confused:

Thanks Kansasnoob (edit: and Geojorg)!!!

I would not be too surprised then if you have problems booting after installation. If so you'll need to edit the grub2 boot parameters in a similar manner.

If you have only one OS installed you'll need to hold down the Space Bar right after the System/BIOS screen passes to make the grub menu appear.

Then after selecting the OS using the up and down arrows press "e" instead of Enter and edit out only the words "quiet" & "splash", this of course is only a temporary fix.

If that "fix" works then to make it more permanent boot into Ubuntu and run:

```
sudo gedit /etc/default/grub
``` 

Then look for the line highlighted here:

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**[COLOR="Red"]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]**
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1" 

Remove only the words "quiet" and "splash" but leave the "", be sure to click on Save, then File > Quit. And remember to run:

```
sudo update-grub
```

And wait for it to say done.

I believe this is a bug in Plymouth so it should be reported as such, be sure to include your specific GPU info which can be found with the command:

```
lspci | grep VGA
```

At any rate it's not so much a failure of the "iso" itself which generally amounts to a failure in either ubiquity or casper, but a failure of other components in Ubuntu.

---

### Post by ezsit on 2010-04-09
Last night I downloaded and tried the 32bit Kubuntu desktop cd and I got the same error:

( process : 330 ) : Glib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

I waited a few seconds and got dumped to a login prompt. So I waited a few more seconds and the desktop loaded just fine. I spent an hour opening different programs and surfing the web with no problems whatsoever. So, this warning for me was by no means a show stopper, just an annoyance. My question: are people waiting a few seconds or minutes before passing judgment?

---

### Post by kansasnoob on 2010-04-09
> **ezsit said:**
> Last night I downloaded and tried the 32bit Kubuntu desktop cd and I got the same error:

( process : 330 ) : Glib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

I waited a few seconds and got dumped to a login prompt. So I waited a few more seconds and the desktop loaded just fine. I spent an hour opening different programs and surfing the web with no problems whatsoever. So, this warning for me was by no means a show stopper, just an annoyance. My question: are people waiting a few seconds or minutes before passing judgment?

I wonder if that's the same thing I was seeing when I reported this bug:

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/557000](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/557000)

As I said there:

> after each install the initial boot results in a very brief command prompt (TTY?) asking me to login. **It's preceded by one line of text that I've not been able to read because I'm visually impaired** and on the initial boot I've not had time to adjust fonts .

Maybe? It kind of sucks not being able to see clearly at times.

---

### Post by -Robert- on 2010-04-09
[QUOTE=kansasnoob]I would not be too surprised then if you have problems booting after installation. \
[/QUOTE]

Well, I surely hope this bug will get fixed before April 29th. It's a nasty problem with Plymouth and I already subscribed to a bug report at launchpad. Anyhow, I won't install 10.04 before the final release, too much risk that the system will crash because it's still beta and I really can't miss this PC.

By the way..I'm curious if this is also the (temporary I hope) solution for ToxicBurn?

---

### Post by c00lwaterz on 2010-04-09
I want to know if there is high temperature issue in beta2.

because I have High temp in karmic.

my machine is toshiba m900 core 2 duo 2.2ghz.

I have tried many distros and debian, pcbsd but no luck.

so i wait for 10.04 if no hight temp.

thanks

---

### Post by RJARRRPCGP on 2010-04-09
> **nix.peter said:**
> I hate to be the bringer of bad news but i used my flash drive, unetbootin, and the 64 bit beta 2 image and im posting this from the live 10.04 beta 2 right now.

I agree here. I'm typing this post with my tiny RAID 0 (3.0 GB) array. ;) 

With beta 1, creating a RAID 0 array caused disk errors to occur. (not bad sectors)  IIRC, it also caused me to get a nonsense error about the mounting of the swap partition failing. 

Looks fine with beta 2. Except I have another weird bug. High chance of being an offset issue. lol.

---

### Post by -humanaut- on 2010-04-09
If you have a spare usb pendrive try creating a liveusb with ubuntu's usb tool worked for me had to do it twice but It's been working fine since.

---

### Post by cariboo on 2010-04-09
I can't see if the op listed his hardware, but I've been playing with the 32bit Live CD all morning with zero problems. This is on an an old P4 1.6Ghz, ATI Rage 128 Pro Ultra and 512Mb ram.

---

### Post by praveenthivari on 2010-04-09
> **ToxicBurn said:**
> wow i guess no Lucid for me for a few days hope a daily build wil fix this in a few days.
 
im bummed out now :(
 
 
i confirmed this on launchpad

It does say tht but for me with this same problem I could boot into desktop, just wait for 2-3 min.

---

### Post by ToxicBurn on 2010-04-09
> **cariboo907 said:**
> I can't see if the op listed his hardware, but I've been playing with the 32bit Live CD all morning with zero problems. This is on an an old P4 1.6Ghz, ATI Rage 128 Pro Ultra and 512Mb ram.
 
 
 
Hi sorry my hardware is 
 
Intel® Desktop Board DG45ID 
 
Intel Core 2 Quad 2.66
 
4 gigs DDR3 ram
 
Nvidia 9600GT 
 
Dual  HP 2009 Lcd monitors

---

### Post by ToxicBurn on 2010-04-09
> **-Robert- said:**
> Well, I surely hope this bug will get fixed before April 29th. It's a nasty problem with Plymouth and I already subscribed to a bug report at launchpad. Anyhow, I won't install 10.04 before the final release, too much risk that the system will crash because it's still beta and I really can't miss this PC.
 
By the way..I'm curious if this is also the (temporary I hope) solution for ToxicBurn?
 
 
Going to try this now

---

### Post by ToxicBurn on 2010-04-09
UPDATE :

I post this reply from Beta 2 32bit  

I got it to boot and install with the follow trick below thanks to all of you for your help

 					Originally Posted by **kansasnoob** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9097425#post9097425") 				
 				[I] from the boot menu press F6 which will display some boot options,  then just press the Esc key. You'll now see that the "boot parameters"  are displayed at the bottom of the screen. Just use the Backspace key to  remove **[COLOR=Red]only[/COLOR]** "quiet splash".

Then just hit Enter & try to boot.[/I]
 

thanks again guys.

---

