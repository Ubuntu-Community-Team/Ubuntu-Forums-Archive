---
title: "buffer i/o error on device fd1, logical block 0"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by roystreet on 2007-11-10
Hello,
    I can't seem to find an answer to this one - I've searched here, so I'm going to have to ask.  I'm trying to install Ubuntu 7.10 & it shows the logo & the prompt of if I would like to start & install - I of course want to install.  It shows the logo & shows the "progress bar" bouncing back & forth like it's going to work.

 I eventually getting an error like:
230.495117] Buffer I/O error on device fd1, logical block 0

I thought it was originally the CD drive - Works fine...Next...
I replaced the HD with a fairly new one that I know works - Same problem.

The original HD I'm trying to install Ubuntu on has a working version of win 2000 pro, so why wouldn't it work?  It has 2 partitions, but I never get to the point where it even asks for a partition.  I currently now have both HD in the machine & it's continuing to list more & more buffer errors like above.  Every once in awhile it will spin the CD some, but then stops.

If this helps, I have burned another CD with version 7.10 & the same problem has occurred.
I also used a CD I have of an earlier version - Which I know the CD worked because I've used it on a previous machine.

Any Ideas?

Thanks,
---roystreet

It now has been running for half an hour or maybe more & it has stopped generating more buffer errors - The last one showing is:
499.166629] Buffer I/O error on device fd1, logical block 0

The CD will still spin here and there for a little bit & then stop.  I'm going to leave it on for awhile longer & then see if anything else happens...Boy do I miss ubuntu!!!

---

### Post by confused57 on 2007-11-10
You could try disabling your floppy controller in bios...if this doesn't work, you might try installing with the alternate cd.

---

### Post by roystreet on 2007-11-12
Well, I've tried using more than one CD...If that's what you mean by alternate CD?  Same problem.  I've unplugged the floppy drive, but now I've taken that further step as you suggested & have gone into the BIOS & change the floppy drive settings to not installed.  I can still go & tell it to start...Now, it shows the ubuntu logo for a long time.  Then the screen goes blank.  The whole time the CD player shows activity here & there (SomeX's for quite a while)

It's still doing it & so I'm going to let it go for a while & come back to see if it worked.  This is unfortunate because I would love to have it on this machine.  I don't like the idea of buying a whole new motherboard & processor for this when win 2000 works on it.  I'm confused.:confused:

Thanks.

---

### Post by confused57 on 2007-11-12
> **roystreet said:**
> Well, I've tried using more than one CD...If that's what you mean by alternate CD?  Same problem.  I've unplugged the floppy drive, but now I've taken that further step as you suggested & have gone into the BIOS & change the floppy drive settings to not installed.  I can still go & tell it to start...Now, it shows the ubuntu logo for a long time.  Then the screen goes blank.  The whole time the CD player shows activity here & there (SomeX's for quite a while)

It's still doing it & so I'm going to let it go for a while & come back to see if it worked.  This is unfortunate because I would love to have it on this machine.  I don't like the idea of buying a whole new motherboard & processor for this when win 2000 works on it.  I'm confused.:confused:

Thanks.
I was referring to try installing with the alternate install cd:
[http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/)

---

### Post by roystreet on 2007-11-12
Question: How is that CD different than the one I've already downloaded?  I've never used the "Alternate"

Thanks - I'm downloading right now.
---roystreet

---

### Post by confused57 on 2007-11-12
> **roystreet said:**
> Question: How is that CD different than the one I've already downloaded?  I've never used the "Alternate"

Thanks - I'm downloading right now.
---roystreet
The alternate install cd is a text-based installer...here is an excellent guide & screenshots for the alternate install cd:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by roystreet on 2007-11-13
Hello, all of a sudden it dawned on me - Check how much RAM is in this thing.  (I had assumed it was much more) There was only 64mb of RAM!  I never thought win 2000 pro would work on that, but maybe it was installed while there was more memory in it.  Well, I happen to have a stick of 128, so I added that to it.  It still wouldn't.  But I threw in ubuntu server edition in there & it has begun installing.  I'm still downloading the newer alternate version that you had mentioned using.  But my guess is it all had to do with the memory - Or the lack thereof.

I will mention if it works!

Thanks - Do you know what the minimum RAM that is needed to install the graphical version is?

---roystreet

---

### Post by confused57 on 2007-11-13
> **roystreet said:**
> Hello, all of a sudden it dawned on me - Check how much RAM is in this thing.  (I had assumed it was much more) There was only 64mb of RAM!  I never thought win 2000 pro would work on that, but maybe it was installed while there was more memory in it.  Well, I happen to have a stick of 128, so I added that to it.  It still wouldn't.  But I threw in ubuntu server edition in there & it has begun installing.  I'm still downloading the newer alternate version that you had mentioned using.  But my guess is it all had to do with the memory - Or the lack thereof.

I will mention if it works!

Thanks - Do you know what the minimum RAM that is needed to install the graphical version is?

---roystreet
I believe Ubuntu 7.10 requires over 300 Mb ram to run the graphical GUI...you could try Xubuntu(alternate install cd):
[http://www.xubuntu.org/](http://www.xubuntu.org/)
I would recommend Xubuntu 6.06, rather than 7.10 for 190 Mb of ram.

---

### Post by roystreet on 2007-11-15
confused57...I thank you for your help so far & I do apologize, I haven't really had the time the last few days to install it.  But I didn't want to leave you hanging wondering if I was ever going to let you know if it worked or not.  (*I should've responded earlier*)  I may be able to try tonight or tomorrow.

---roystreet

---

### Post by roystreet on 2007-11-17
FYI - I tried to install the server version & it installed, but when I tried to install the ubuntu standard desktop, X server failed & it doesn't really tell me why.  

The error I get is:
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
<Yes> <No>  

I select yes

/etc/gdm/failsafeXServer: line 47: [: too many arguments 
Warning: Could not retrieve EDID because get-edid is not installed (1)
Warning: Could not retrieve PCI IDs because discover is not installed (1)
FATAL: Error inserting battery
(/lib/modules/2.6.22-14-server/kernel/drivers/acpi/battery.ko): No such device
: error: this program does not know how to configure the "10 shared/default-x-server doesn't exist" X server
Warning: Could not generage /etc/X11/xorg.conf.failsafe for vesa driver.



So, I decided I would grab a stick of 512 ram from the machine next to it & then install the full desktop version.  So, the machine is now a 733mhz celeron with 512 mb ram.  It should install just fine, right?  Well, I'm getting the same errors now.  I'm kinda stuck here because I don't know how to fix x server & even with enough ram, the regular desktop version won't install.  Do you think it could be the video card?

It finally started to act like it was installing & stopped saying block errors after a couple of them.  But now the screen is blank & the lights on my monitor are blinking.  It has been doing for this about 5 minutes.  Could it still be working somewhere in the depths of the system & I just can't tell?


(I later got the same above error even with 512 ram & a new video card - Brand new!)

I've given up trying today - I though it would've worked?

Thanks,
---roystreet :confused:

---

### Post by confused57 on 2007-11-17
What video card are you using?

---

### Post by roystreet on 2007-11-17
I just put in a Radeon 9550, 256 mb.
The old one I'm not sure what it is, I'm looking...

I'm wondering by the error msg if it has something to do with the ACPI?

Not sure, but it does state when it's booting that it can't enable because it's an old versino (1997) and I get the drift it has to be from 2000 or newer.

Thanks...
---roystreet

---

### Post by confused57 on 2007-11-17
> **roystreet said:**
> I just put in a Radeon 9550, 256 mb.
The old one I'm not sure what it is, I'm looking...

I'm wondering by the error msg if it has something to do with the ACPI?

Not sure, but it does state when it's booting that it can't enable because it's an old versino (1997) and I get the drift it has to be from 2000 or newer.

Thanks...
---roystreet
That's a possibility, you might try adding boot parameters to the kernel...you can do this by highlighting your Ubuntu entry in the grub boot menu, press "e", then highlight your kernel line, press "e" again, try adding "acpi=off" and "noapic" (without quotes) to the end of the kernel line, press "enter", then "b" to boot...this is temporary, but worth trying.

If the above doesn't work, when you get to the xserver error message, press "Ctrl+Alt+F1", this should get you to a console, login, then enter:
```
sudo dpkg-reconfigure xserver-xorg
```
Select "no" at the first screen to autodetect, then you can probably go with the defaults for everything else, except the video driver...try "ati" or "radeon".  Once your xorg is reconfigured, type "startx", without quotes...or "sudo reboot", if startx doesn't work.

---

### Post by roystreet on 2007-11-17
I tried the acpi & it didn't seem to work...(It was worth a try & I've never worked with anything in the kernel before, so it was a good exerpience - Thank you)
The "sudo dpkg-reconfigure xserver-xorg" command sounds familiar to me.  when I use it, I get the following msg: (I'm not typing the whole thing here)
Package 'xserver-xorg' is not installed an no infor is available.
Use dpkg --info (= dpkg --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed.

But I'm quite sure I installed it way earlier.  So, I'm not sure how this happened.

Thanks.

---

### Post by roystreet on 2007-11-17
I just tried "sudo apt-get install xserver-xorg" & it went through some stuff pretty quick...so it was hard to read. It mentioned stuff about selecting things that were once deselected..?  Sounds like it was installed, but certain options were not.  

I then tried the configure command you gave me once again.  It did make me select the type of video card, some resolution questions & even mouse/keyboard prompts.  It completed it's course warning me that "xserver-xorg postinst warning: overwriting possibly-customised configuration file; back in /etc/X11/xorg.conf.20071117195125" ...Then the below error

(This One consistently keeps showing up here & there:
FATAL: Error inserting battery (/lib/modules/2.6.22-14-server/kernel/drivers/acpi/battery.ko): No such device.

Like it's still looking for some type of battery...

Thanks - I'm now going to let it totally reboot & see what happens.


-New info-
It eventually brings me back to "jkr@userver:~$" and I type startx
It then responds with "-bash: STARTX: command not found"

Maybe I'm trying something that wont work here?  I am still new at Linux, but I'm trying.

---

### Post by confused57 on 2007-11-18
If this is your server install, you wouldn't have a GUI installed, which may be why there wasn't an xserver-xorg.  You could try installing ubuntu-desktop, but first update your system:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop
```
It'll be a fairly large download, but you'll get the option to continue or not.

or

```
sudo apt-get install xubuntu-desktop
```

---

### Post by roystreet on 2007-11-19
Hi,
    After I installed the OS, I did the upgrade & update.  Then I downloaded the huge desktop & installed it.  So, it should've had it already - It was a huge download as you had said.  That's why I was confused because I thought X server was installed.  
     Do you have a clue as to why it keeps mentioning a battery??  I'm almost convinced that the whole issue revolves whatever is causing this error.  I'm seriously wondering if it is connected to the ACPI issue. 
     I know that has to do with the power in some fashion.  I will mention when you had me edit how the kernel started, I also tried entering: ACPI=force.  Reason being is because when the OS is booting it mentions that error concerning the how old the BIOS is.  It mentions on that screen that ACPI will have to be set to "force", so I tried it.  Arrgh!  I'm not upset with you, but this is a good learning experience that I was not planning for, esp considering I'm going out of town soon!  


Thanks...
---roystreet

---

### Post by TracyO on 2007-11-19
Hi,

I have Gutsy installed, I have 256 RAM, and I received almost the same error message when I initially installed Gutsy.  Mine was "buffer i/o error on device fdo, logical block 0"

What's happening now is that whenever I try to download something, it downloads completely, fails, and then cycles to try again.  This happened when I did the Memory Test--it did the memory test over and over for nine hours until I stopped it.  

Basically I'm trying to figure out if that error message had anything to do with this, so what happened to you after all of this?

I first noticed it in trying to download podcasts and codecs.

Thanks,
Tracy

---

### Post by confused57 on 2007-11-19
> **roystreet said:**
> Hi,
    After I installed the OS, I did the upgrade & update.  Then I downloaded the huge desktop & installed it.  So, it should've had it already - It was a huge download as you had said.  That's why I was confused because I thought X server was installed.  
     Do you have a clue as to why it keeps mentioning a battery??  I'm almost convinced that the whole issue revolves whatever is causing this error.  I'm seriously wondering if it is connected to the ACPI issue. 
     I know that has to do with the power in some fashion.  I will mention when you had me edit how the kernel started, I also tried entering: ACPI=force.  Reason being is because when the OS is booting it mentions that error concerning the how old the BIOS is.  It mentions on that screen that ACPI will have to be set to "force", so I tried it.  Arrgh!  I'm not upset with you, but this is a good learning experience that I was not planning for, esp considering I'm going out of town soon!  


Thanks...
---roystreet
When you enter acpi=force, make sure it's all lowercase.  Have you tried the Dapper 6.06.1 alternate install cd(not the server iso download)?  A server install can be done with the alternate cd by selecting install Command-Line installation...the server install cd has a different kernel than the alternate cd server installation and would work better with a GUI and Gnome, however, you would probably want to select the first option of Text-based install to install a GUI initially.  It was my experience on an older pc I had that Dapper ran better than Gutsy 7.10.  

You might also try booting up a small distro, such as Puppy Linux:
[http://distro.ibiblio.org/pub/linux/distributions/puppylinux/](http://distro.ibiblio.org/pub/linux/distributions/puppylinux/)
The 3.00 Seamonkey iso is only a 98 Mb download...I think you'll like the desktop & functionality of Puppy-2.15CE Final, which is a 130 Mb download...You might try these, just to see if they work on your pc.

I can empathize with your frustration, but I haven't actually experienced the problems you're seeing.  If I find anything that might be helpful, I'll post back.

---

### Post by roystreet on 2007-11-20
confused57 - I'd like to first thank you for all of your help thus far.  Hopefully one day I will be able to help you.:)  

 I think I have tried acpi=force in lowercase.  I am sitting here wondering...Why does it keep mentioning a battery??

Tracy0, unfortunately this has not been resolved. 

...confused - I want to give you a lot of credit for helping me so much thus far.  Hopefully one day I will have an opportunity to help you.

...I believe I tried acpi=force in lowercase also to no avail.  I am sitting here trying to cling on to any questions that I know I need to ask, which is: Why does it keep mentioning a battery??  [Please note: I'm saying this with a frustrated voice]  It's ultimately still just a computer & I will have to figure out some other way.  

...Unfortunately, I am seeing the only other option revolves around building another PC or buying one.  We have gotten further than the i/o error to a degree, but the GUI just isn't wanting to work.  I am going to try your sugesstion of using the alternate CD & I know I can add on the server features later.

I will try that & get back with you...
---roystreet

---

### Post by confused57 on 2007-11-20
Hardware compatibility problems with linux can be difficult(sometimes impossible) to overcome.  The battery error message may be a bug with your system with Ubuntu, a Google or forum search may turn up something.  The acpi=force message is just reported if your bios predates 2000...the bios in the old computer I had was Dec 1999 and I received the same message trying to run Gutsy 7.10.  I didn't receive this message in any Ubuntu versions prior to 7.10.

If it were my system, I would try installing a text-install(full GUI, 1st selection in the first screen) with the alternate install cd...I personally would install 6.06.1, but with the amount of ram and video card, 7.10 should work OK.  Once you've done this, note the error messages you're getting when booting up after install, and hopefully your biggest concern would be getting your video card configured.

You still might want to burn a live cd of Puppy Linux, to see if it is a linux problem or an Ubuntu problem.

---

### Post by Presto123 on 2007-11-30
A little late to post this...but it is most likely your HD. I am trying to get some other HD's to work, including my old 80g that crashed a long time ago. I keep hoping that something will work for it, but, that's the error I keep getting right now.

I think it's entirely dead on the main sector, or has some major errors...will return with some info if I can get it running.

---

### Post by roystreet on 2007-12-01
Hello,
...Thanks for your thought.  [COLOR="Blue"]Just an FYI: My problem has still not been resolved & I'm not sure what direction I'm going to take.[/COLOR]  :(

...I thought about the HD before, but it's nearly a brand new HD & had a working version of Win XP on it.  The old HD had a working copy of Win 2K.  So, both worked very recently.

Thanks & I'm Still Looking For Any More Ideas...
---roystreet

---

### Post by g45uk2 on 2008-04-11
> **confused57 said:**
> That's a possibility, you might try adding boot parameters to the kernel...you can do this by highlighting your Ubuntu entry in the grub boot menu, press "e", then highlight your kernel line, press "e" again, try adding "acpi=off" and "noapic" (without quotes) to the end of the kernel line, press "enter", then "b" to boot...this is temporary, but worth trying.

If the above doesn't work, when you get to the xserver error message, press "Ctrl+Alt+F1", this should get you to a console, login, then enter:
```
sudo dpkg-reconfigure xserver-xorg
```
Select "no" at the first screen to autodetect, then you can probably go with the defaults for everything else, except the video driver...try "ati" or "radeon".  Once your xorg is reconfigured, type "startx", without quotes...or "sudo reboot", if startx doesn't work.

i had the same problems as you, i put ubuntu on my laptop and am going windows free in my home, so i put ubuntu on to my PC and got the I/O same errors i restarted and at the bootscreen do the following:
1) Press F6 
2) add this to the end ( before --) acpi=off noapic nolapic no387 ide=nodma 
3) press enter and leave it for a while you will still get the I/O errors but leave the system mine took 15 mins to get past this and its a fast PC
4) after this you might get lucky and get straight in with a working GUI if not press ctrl+alt+f2
5) type sudo passwd and put a password you can easily remember
6) type su and enter password when promted to chage to root 
7) sudo dpkg-reconfigure xserver-xorg
8 ) go along with everything here but for video card choose "VESA" and when asked for video card channel (or something along them lines ) delete all the info thats already there and press enter
9) for monitor setting select only 800x600 and carry on to the end of this process
10) now type "startx" without quotes and leave it a few mins to load up, 

thats it, it worked for me i managed to install following this method hope you all have some luck with this

gaz

---

