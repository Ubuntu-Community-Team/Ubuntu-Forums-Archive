---
title: "Eror during install - Buffer I/O error on device fd0, logical block 0"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by AndrewTheArt on 2007-05-10
Precondition - I did search the Ubuntu forums for this error, and found several topics on it. However, no results fixed my problem or were conclusive as to what the issue might be.

Basically, though, I'm getting a strange error when I boot up the Kubuntu 7.04 Feisty Fawn CD.

(1) First of all, I select the "Run or install to HDD" option on the splash screen (or w/e it is called). That loads fine.
(2) Then, It goes through a long process where a blue progress bar goes back and forth for about 2 to 3 minutes. This is fine as well.
(3) Finally, it brings me to a blinking cursor and spits out the following error-

```
<some large integer here> Buffer I/O error on device fd0, logical block 0
```

The <some large integer here> is the exact location of the error, I assume.

Anyway, after this, i get kicked to a shell as user "ubuntu". Nothing installs.

Here are my questions you you wonderful people - 

(1) Does anybody have any ideas as to what could be wrong? I want to "upgrade" from Fedora Core 6. I believe that Ubuntu is both better and the future of Linux more than any other distribution. 
(2) Would the alternate install CD help here, and if so, where can I find it?

Some small notes -

(1) I don't have a floppy drive.
(2) My CD-RW drive had been acting up, so after unsuccessfully trying the install with it attached, I remove the power and the (IDE?) connector from it. This didn't help of course.
(3) Using DVD drive to load the Kubuntu CD-R disc.

Thanks!!!

---

### Post by Noname02 on 2007-05-10
I'm getting the same- but after installation. My problem is that the system can't identify my FDD even though it's there. I've investigated this one by myself so far. Posted questions about it but haven't had any replies yet.

What i've discovered is this:
 These I/O buffer errors seem to stem from the fact that the system is either trying to read a drive that isn't there, or that it's reading the wrong drive and not seeing what it expects to. 

I'm wondering if your problem may be that one or other of the drives is chained on the cable rather than a seperate IDE connector- basically hardware setup rather than the O/S configuration- seeing as it's not installed yet....this is a pure guess.

Either way, there seems to be an issue here. What version are you (trying) to run? The one I'm having the problems with at the moment is 5.10....

---

### Post by AndrewTheArt on 2007-05-10
I'm trying to install Kubuntu 7.04 (Feisty Fawn).

What you say makes sense though - the chances of it being a hardware issues are very high indeed. However, I can't even image what device it can't read because even WITH the broken CD burner plugged in, it still gives me the same error. (The entire reason I pulled out the CD-RW drive is because the install failed).

I'm going to have to examine my hardware setup carefully, but please everybody, continue to post tidbits of iinformation for me.

---

### Post by Noname02 on 2007-05-10
Hi again. Suggest you read this thread:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306)

this sort of sounds familiar!

---

### Post by AndrewTheArt on 2007-05-11
> so I swapped out the DVD/CDRW drive with a basic CD-Rom drive and the install went perfectly. Apparently there's an issue getting the combo drive to be recognized during install. All works well now!

I have a feeling I need to do the same thing and take out my DVD-CD combo drive and the problem will be fixed.

This sucks in general though, because my CD-RW drive recently broke and I'm currently using an old, SLOW CD drive that would make the install take several hours.

If this truly is the problem, I wish the installer would recongnize and accept a wider array of DVD-RW drives. Fedora and SuSE sure did.

---

### Post by Noname02 on 2007-05-11
I think you're right. 
For some reason this distro doesn't seem to recognise much. I've just tried out the USB function, and although it sees my flash disk, it can't mount it. This has just about finished it for me for the moment because although I do have a working system, I can't get data out from it by any medium at all.
I haven't yet tried to conect a router (I'd have to buy one) because I fear the result would be the same.
For this reason I'm going to try another distro that has more chance of dealing with my hardware- which is rather old it has to be said. 
Sorry Ubuntu!

---

### Post by AndrewTheArt on 2007-05-14
Seriously though, they need to fix such as basic issue like this. If every other distro I've used can recognize my 3 to 4 year old DVD drive, I'd expect the bleeding edge Ubuntu to do it.

This truly sucks for the common person.:(

---

### Post by Noname02 on 2007-05-15
As a quick postscript to this...
I decided to try another distro as I mentioned and tried Mepis. Based on Ubuntu, I figured it wouldn't be all that different (apart from it's KDE).
This time- everything works. Drives, flash drives, USB you name it. I didn't even get the display problems that this distro is famous for.

So- it looks like my problem was compatability with Ubuntu. Now I've got something that actualy works it will give me a chance to learn more about Linux in general. I still want to come back to Ubuntu eventually - at the very least to find out exactly WHY this problem occurred..[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

---

### Post by kjkrum on 2007-05-20
I'm getting the same error when trying to install 7.04 on my roommate's Dell Latitude.  (Not sure exactly how old it is, but it has a 700MHz CPU.)  It does not have a floppy drive.  After printing the error twice, it does nothing for fifteen minutes.  (Then I rebooted.) I get the same error when attempting to check the disk for integrity, run or install, install in safe graphics mode, or install in "text mode" (which looks exactly like the graphical installer... huh?!)

Considering that this was a known and widespread problem in beta, how the hell did 7.04 go final with it unfixed?  And while I'm ranting, whose idea was it to remove the menu you normally get when you select "other options" on the Debian installer?  Hate to say it, but my impression of 7.04 is that it's a botched abortion on the scale of Mandrake 9.0 or whichever completely unusable version that was that made me finally give up on MandrakeSoft.

---

### Post by eclispe86 on 2007-05-23
yeah... got the same problem here. I running an older Latiude CPi.

---

### Post by tomtoromtom on 2007-05-24
and the same problem here - an old Gericom Silver Shadow.

---

### Post by AndrewTheArt on 2007-05-25
This is really disappointing... I just want to install and run Ubuntu and I can't even do that. 
Any ideas from the dev team how to fix this? 
This is really a letdown for me and several other people (as you can clearly see above)... it's obviously a recurring theme for many people and a serious bug.
I hate being in Windows land.

---

### Post by Melcar on 2007-05-25
I experience the same problem on an old Latitude laptop.  Funny thing is that today I made another attempt at installation, and even though I got the same error, I left the installation going, and after receiving that same error about 10 times, the installation process went past that and continued as if nothing was wrong.  I have no idea why this happened.:confused:.  Unfortunately, the installer fails to create partitions, meaning that I can't finish the installation; it says my HDD has errors.

---

### Post by sitric on 2007-05-26
ok now, i had a similar problem with a secondary HDD which was not reletively important to ubuntu, and it was giving me a hell of a time installing ubuntu because of all the bad sectors... then finally what i did was, i just took out the power plugin of the secondary HDD.. and voila, very nice and trouble free setup...

now what i suggest is, open your CPU and just take out the power connector giving power to your fdd... and the setup will go awsome.

PS: the computer must be switched off before attempting anything that changes things in the CPU or you might be left with a faulty system. so switch off your system before you kill the power of the fdd...

---

### Post by AndrewTheArt on 2007-05-26
The thing is, I don't even have a floppy disk drive, and I disabled it anyway as a possible option in the BIOS. That's what I'm having a hard time understanding.

---

### Post by teistiz on 2007-05-26
Same here, Compaq Evo N600c with no floppy drive at all.

[  177.976000] Buffer I/O error on device fd0, logical block 0
[  211.912000] Buffer I/O error on device fd0, logical block 0

**The installation seems to proceed after that**, though, it just doesn't produce any other output for a while  so it looks like it's crashed. My guess is some retarded script assuming there IS a floppy drive.

Not even my desktop computer has one of those, noticed it wasn't connected to the mobo half an year after building the box and just removed it as its huge data cable was messing with the case's ventilation.

---

### Post by AndrewTheArt on 2007-05-27
I was running a program in Windows recently, and it thought my 9 in 1 card reader was a floppy disk, as well as my iPod. Maybe the installer thinks in the same outdated, stupid way (This was a Win 95 program)

---

### Post by Grayhambo on 2007-05-27
I have exactly the same problem:

**[INDENT]Buffer I/O error on device fd0, logical block 0[/INDENT]**

...which just repeats...and repeats...until the PC crashes.

It can't be anything to do with the installation CD, as I have previously used this to install Feisty on another PC - with no problems at all. However, I've just upgraded my PC:

[INDENT]Intel Core duo 2.40 GHz E6600
Sapphire X1950 XT graphics card
ASUS  P5W DH Deluxe motherboard
and the same LG CD/DVD optical drive as I used in previous PC[/INDENT]

Any of the Admin Team have an idea of how to overcome this, as I am able to install OpenSUSE 10 without difficulty...but would prefer to stay with Ubuntu?

Thanks!

---

### Post by teistiz on 2007-05-27
I tried installing Feisty in VMWare on my desktop computer (Athlon 64 in 32-bit mode, 1 GB RAM) out of curiosity, set the VM to be somewhat similar to my laptop (256 MB RAM, no floppy drive) which I was ultimately unable to install Feisty on - the live CD took ages to make it to the desktop after the errors with device fd0, and it was so slow the installer was unusable.

This time in the VM the live CD took around 20 minutes to reach the desktop, tried starting the installer but after accessing the virtual machine's drive for several minutes it hadn't even managed to get the install window open. At this point I shut the virtual machine down.

The previous Ubuntu version's live CD worked just fine and booted on an old computer in less than five minutes. I guess I'll just try the alternative installer, this time in VMWare *first*.

---

### Post by jimbean on 2007-05-29
set all bios settings to default
let bios  do any configuring
if no default setting
set to auto
make sure you low level format hardrive
fdisk drive to make sure no partitions are set active
then use alternate ubuntu install disk
just some idea`s that worked for me in the past 2 decades

---

### Post by Snabbdist on 2007-05-29
yes this happens to me too!
I did default bios at least.

no floppy
cd/dvd drive

---

### Post by regomodo on 2007-06-01
Exactly the same problem here.

I've just installed Xp in 1st half of drive. Intended on putting Ubuntu in the 2nd.  Get 2 of those errors but the bootup works through anyway.  

Installed using manual partition setup. 

Setup goes fine.

Reboot.

Grub - ERROR 17.   

Bloody awesome. I wish i didn't throw out my Edgy disc.

---

### Post by AndrewTheArt on 2007-06-22
I think I might know what the problem is, although the remedy is somewhat beyond me (at least for Ubuntu itself - other distros might be different). My best guess is that the Ubuntu installer is mistaking it's inability to find a driver (most likely a graphics card driver) for an inability to "read fd0". I came to this conclusion when I tried installing simplyMEPIS recently, and when the installed booted up for the first time, I picked "graphical mode". Got a similar error to Ubuntu's installer. Anyway, I rebooted and tried to option "graphical install with nvidia drivers". It worked!

However, this doesn't explain why Ubuntu doesn't work for me even with "safe graphics mode" and "text mode".

EDIT: As an update to this, simplyMEPIS woulden't install to the hard disk, but I did at least get tot he LiveCD portion. Anyway, I tried ANOTHER distro after all of this called Mint Linux (based of Ubuntu), and I got the SAME exact error! This is incredibly frustrating. 

Buffer I/O error on device fd0, logical block 0

What in the world could that mean? I've detached ot gfx card and gone to the integrated one (didn't help) unplugged my DVD Drive (didn't work), uplgugged my 8 in 1 card reader (didn't work). What could it be looking for? Dev tem, PLEASE help.

---

### Post by Ken Iovino on 2007-07-21
I'm getting the same error. No floppy and it's disabled in the BIOS. The md5 Hash is correct and I've got a cd-rw and a dvd player installed. I'm just going to let the install do this for awhile and see what happens. I'm testing this on a spear PC I have. AMD 1.6, 2 sticks of 1g DDR...

Update: It's now on [667.462880]...

I'm a little dissapointed,  I was excited to get out of Windows.

[SIZE="3"]**EDIT:**[/SIZE]

After letting the installer just run for about 15mins, I get this message now.

```

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-In shell (ash)
Enter 'Help' for a list of built in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

```

Any ideas? I'm going to poke around for awhile and see what I can come up with.

---

### Post by AndrewTheArt on 2007-08-03
Anyway, this error was never rectified so I'm use openSUSE 10.2, which didn't have any such issues.

---

### Post by CaptainPanick on 2007-10-04
I'm having the same problem:

OS: Ubuntu Feisty Fawn 7.04
CPU: Intel E6850 Core 2 Duo
Mobo: ASUS P5K-SE
RAM: 2x1GB DDR2 800MHz Samsung
HDD: 1x320GB SATA, 1x200GB SATA, 1x120GB SATA
Video: 7800GTX
No Floppy Disk

Condition:
- Boot up with Ubuntu install disk
- Boot menu starts ok.
- Start installation, progress bar runs for a minute or two, then goes to blank screen with prompt.
- After a few seconds, the following error starts appearing: [address] Buffer I/O error on device fd0, logical block 0.

Tried:
- Tried disabling the FDD but then the Ubuntu installation produces an error straight away and sits in a prompt.
- Tried the nofloppy flag but didn't make any difference.
- Tried burning new disk and made sure checksum was correct and did an error check on the disk after burning.
- Told Ubuntu boot menu to look for errors on disk but the same error occurs.
- Looked at various other threads discussing the same problem but haven't been able to resolve the issue.

---

### Post by chente7hb on 2007-10-08
Yep, I am having a similar problem installing Ubuntu on my sony vaio.  Its current operating system is windows '98 and I am looking forward to the switch after I successfully installed Ubuntu onto my desktop.  I am able to boot into the installation list; however, when I go to install Ubuntu the process gets hung up and the same error message "Buffer I/O..." appears.  

I made extra room on the hard drive and the problem persists.

---

### Post by Vajpero on 2007-10-10
Have someone tried solve it like: [http://www.cyberciti.biz/faq/linux-end_request-ioerror-dev-fd0-sector0/](http://www.cyberciti.biz/faq/linux-end_request-ioerror-dev-fd0-sector0/)

---

### Post by gajones on 2007-10-28
I had the same issue on my Dell Inspiron 8000.

I got around it by using [Unetbootin]("http://lubi.sourceforge.net/unetbootin.html;)

I now have a fully working Ubuntu 7.10 installation.

---

### Post by coln_sanders on 2007-11-20
I don't know if this will help anyone else, but it sure helped me in a big way.  I got this same error, but the first time through (installing 32-bit 7.04), it displayed the error and hung for a bit, but did continue on (slowly) and complete the install.  Now I'm reinstalling after destroying my X config, using 64-bit 7.10.  When I tried to reinstall, the same error popped up and my computer was going haywire.  I don't have a floppy disk plugged in, but the problem (for me) was in the BIOS settings.  I'm running a Gigabyte K8U-939 and in the BIOS, and in the menu "Standard CMOS Features", a floppy disk channel was enabled and looking for a drive without it being physically present.  I changed this feature (Drive A) to "None" and now it works fine.

In short, all I'm trying to say is make sure your BIOS settings match your actual hardware setup.  So far this install is going very smoothly, and I only changed one single BIOS setting.

---

### Post by schibros on 2007-11-29
i have the same problem with my toshiba tecra 8200. no floppy drive.

it shows this error 4 times with different increasing integers then starts loading the hardware. after that, the sound comes up. the displays but not complete. i can only see the taskbar of ubuntu7.10 a couple of inches to the top of my screen. the bottom part of my screen looks like its a corrupt graphics and you cant make out anything. because of the graphic issues i cant install ubuntu, cos i cant see where the install icon is located on the desktop.

i have tried installing the alternate version but the cd does not seem to boot. i dont know where all this problem is coming from, but i would like to get a solution. because i fell in love with ubuntu the day i saw i.

also need help on how to burn the alternate cd and the files that are to be in it. thats ubuntu 7.10

please help

---

### Post by schibros on 2007-11-30
hello guys,

thanks for the advice on the error with the buffer on device. i was able to disable the floppy drive in my bios and i dont have that error again.

though i still cant install ubuntu cos i cant see the full desktop on my monitor.

all the cds i have downloaded do not seem to boot from startup. the only way i can get them to boot is when i install the wubi-cdboot file. Only after installing this i have the option of selection ubuntu from the boot menu. 

i have downloaded the alternative version of 7.10 but it doesnt boot too. i think maybe i didnt write the files to cd the right way.

i need help on how to burn the iso file of ubuntu 7.10.

PLEASE HELP.

---

### Post by peanut butter on 2007-12-08
Hello all. I ran into the same error with 7.10. I fixed it by pressing F6 at the screen asking weather you want to install, go into oem mode etc. I fixed it by pressing <F6> and adding 

floppy=off 

to the boot line. Im still unsure how this Dell thinks it has a floppy, but aparently it does.

EDIT: gparted hangs for a bit, but works after a couple miniuts.

---

### Post by yorgos1 on 2008-02-24
Same problem here with ubuntu 7.10 desktop

On an IBM Thinkpad T21 256MB Ram

after some time it boot's up but during install it hangs at 15%

---

### Post by AndrewTheArt on 2008-04-05
Try the beta of Ubuntu 8.04 - that's my advice.

---

### Post by gopodge on 2008-04-13
Hardy Heron Beta (8.04) is no different.

When booting from the install CD, the progress bar pauses for some time before continuing as normal.

This does not occur for me once the install has completed.

---

### Post by AndrewTheArt on 2008-04-16
Right - well, at least I can install Ubuntu on my desktop at ALL now. That's a significant improvement from 7.04 for me. (7.10 did install on my laptop if I recall correctly)

---

### Post by SteveZsuzska on 2008-04-20
I got this problem too, with a Toshiba Portégé 3110ct, trying to run the Xubuntu Live CD on 192 MB RAM. This unit has a plug-in floppy drive and when I plug it in the error message no longer appears. The install sequence tries to access the floppy and the floppy drive's LED comes on for a short period. The fact that there's no floppy in the drive doesn't appear to matter.

Now the next hurdle is that I'm left with some text from something called BusyBox and a (initramfs) prompt.....

---

### Post by ottojwittner on 2008-05-23
I'm (as I'm writing this) installing Ubuntu 8.04 on my Toshiba Portégé 3110ct. I did what was mention by Yiftos here [https://answers.launchpad.net/ubuntu/+question/7697]("https://answers.launchpad.net/ubuntu/+question/7697"). I checked the "alternate desktop CD" option before downloading the CD image. 

(... I tried the other CD image too and got into the same situation as you did.)

... some hours later...:
Ubuntu 8.04 turns out to be to much for a Torshiba Portégé 3110ct (which is really not supprizing when you consider the minimum specs given on the download page.) However Xubuntu, installed from the "alternate CD", is now running happely on my Toshiba.

---

### Post by djotaku on 2008-07-05
I'm having the same problem with 8.04 and an Emachine T6524.  There are no floppy drives, but there's a DVD/CD-RW and a CD-RW and a built-in card reader.

---

### Post by hellzkeeper1216 on 2008-07-15
I know this is an old post, but Doing some research i stumbled across this.

[http://www.techontour.com/os-servers/2008/04/20/buffer-io-error-on-device-fd0-logical-block-0-on-ubuntu-install/]("http://www.techontour.com/os-servers/2008/04/20/buffer-io-error-on-device-fd0-logical-block-0-on-ubuntu-install/")

---

### Post by fitalic on 2008-07-19
i installed ubuntu but my monitor is blinking? wat shud i do please?

---

