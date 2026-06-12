---
title: "ubuntu 12.04 can I use installation cd to update"
date: 2013-06-16
forum: Installation &amp; Upgrades
---

### Post by ponydrvr on 2013-06-16
I have freshly installed ubuntu 12.04 from the cd, but it freezes up before I can do any updates. Will running the cd in
"try ubuntu" keep any updates I do or should I reinstall again. All I'm wanting is to get it to work long enough to use unetbootin to put LXLE on this computer. Its a Dell dimension 2400 and has no usb boot option. I have 2 gigs of ram and the ubuntu 12.04 cd is all I have to work from.

---

### Post by Bashing-om on 2013-06-16
[COLOR=#000000]ponydrvr; Hi ! Welcome to the forum.

The liveCD in "try ubuntu" mode is a totally different and separate operating system to anything that is installed onto the hard drive. The Hard drives are not mounted until such time as you manually mount them.
Express the nature of the problem you are experiencing at this time. Perhaps it is as simple as getting a graphics driver installed into your ubuntu install ?  - We are here to help ->
[/COLOR][INDENT=3][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]

---

### Post by ronniew on 2013-06-16
No need to fiddle with that...

Use [PLop]("http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/") to boot on usb and dont' use unetbootin use [gdiskdump]("https://launchpad.net/gdiskdump") or pendrive linux to create the usb

---

### Post by ponydrvr on 2013-06-17
Hi! Thanks for the replies! It's a long story,but basically I have an old pc that is not up to running ubuntu 12.04.. I didn't realise this when I had it installed. Videos on youtube played very choppy and slow. So I tried a hard disk install of LXLE and it worked a lot better. But I had trouble actually installing it (I got an error message about partitions unable to unmount cdrom.) Finally the installer failed so I tried a fresh download and the same thing happened. Then it seemed to worked but I messed something up and got a blinking cursor. So now I have reinstalled ubuntu and am wanting to try again,but it locks up within a couple minutes. I can move the mouse but clicking does nothing. I have to shut it down with the power button. The freezes were not this immediate before as I had enough time to actually do the download.
@ronniew As I understand plop has to be on a cd or floppy and I don't have either. Also with the way it is freezing I can't do any downloading at this time. Thankfully, I have the pc that I am typing on at this post. I know in your other messages you say not to use unetbootin but I don't need it to be persistant (if I install to hard drive) do I?

---

### Post by Bashing-om on 2013-06-17
[COLOR=#000000]ponydrvr; I applaud your persistence.

Is 'buntu to be the only operating system installed ?
I highly recommend lubuntu if you have 512 megs of ram -more is better. Obtain it with the link at the top of the forum login page.

In this situation ... I offer that you use GParted ,available on the liveCD, to wipe the prior partitions from the drive; in GParted make a new partition table (default msdos in your case, - msdos is not microsoft disk operating system). This will preclude the installer, upon reinstall, being confused and will be starting with a clean slate. I expect then that the install will be slick as a whistle.

Read the help files for comprehension in use. GParted - partition editor for 'buntu - is easy to use and fairly straight forward... as this is to be a fresh install .. no mistake can be made that can not be corrected. Fumbling around to learn the process is acceptable. Remember, we are here to help you over any rough spots. just ask !

Keep in mind, this is a process to install 'buntu;
Point A to point G... each step in between to be completed prior to attempting the next progressive step.
[/COLOR][INDENT=2][COLOR=#000000]
I am try'n to help

[/COLOR][/INDENT]

---

### Post by ponydrvr on 2013-06-18
Okay...so once I have done the msdos partition looks like I will have to get some cds. I was sure hoping I would be able to download an iso and install to hard disk but maybe patience is better. I really want to be able to use the pc as an extra backup since both my pcs are old. Thank you for your help!

---

### Post by Bashing-om on 2013-06-18
[COLOR=#000000]ponydrvr; Hey . hanging in there with you.

Installing 12.04: one CD (12.04 still fits on a CD) is all that is needed... GParted is included on the CD desktop install medium.
Down load the 12.04 .iso file, check the md5sum to verify no corrupted download;
Burn that .iso file as an image -not copying "data" -  making it into a bootable CD, burn at a slow speed;
Boot the CD (bios set to boot cd as 1st priority) when the bios screen clears depress and hold the shift key -> language screen, escape key to accept the default -> boot options screen ... select "check disk", wait a bit while that disk is being checked ... advisory comes up that the disk is good.

Select "try ubuntu" -> boots to the desk top (unity) ! Launcher is on the left side of the screen, top icon is the "dash" click on the dash and search box pops up -> enter term "GParted" - without the quotes - in this search box and below it appears the result -> icon for GParted.

GParted ..take the time to read the help file to get an overall idea and direction. If you get stuck and need additional guidance/confirmation, we are here. Just ask !

Play with ubuntu in this "try ubuntu" mode, make sure all functions properly, if not advise so we may take action to assit you in the real install.
[/COLOR][INDENT=2][COLOR=#000000]
just try'n to help
 [/COLOR][/INDENT]

---

### Post by ponydrvr on 2013-06-18
I think you misunderstood me. I have used my 12.04 installation cd several times. In fact it is the version on this computer that I am using for these postings. The computer that I am wanting to salvage is too under powered for 12.04. I have used it to run g-parted before on that pc but not to get a msdos partition table. Does a cd lose integrity the more it is used to install? Maybe that's one of the problems? I meant that I would have to get some cd's to load lubuntu or any other os onto to install after making the partition which will in effect wipe 12.04 from that machine. The budget does not support buying cd's for a while, which is why I was trying the install to hard disk option with unetbootin.
Thank you for bearing with me. It means a lot.

---

### Post by Bashing-om on 2013-06-18
[COLOR=#000000]ponydrvr;

Does not matter how many times a CD is used, will not directly affect it's integrity... dirt, fingerprints, magnets and other abuses do !

I have never utilized "unetbootin" so of no help in that respect.

Lubuntu will run admirably on older lower spec hardware, there are still some "minimum" specifications for it to perform well. I have lubuntu 13.04 installed on an AMD sempron cpu powered  box ... excellent !
[/COLOR][INDENT=3][COLOR=#000000]
cheers

[/COLOR][/INDENT]

---

### Post by snowpine on 2013-06-18
If you already have Ubuntu installed, then simply:

```
sudo apt-get install lubuntu-desktop
```

or install it with a couple of mouse clicks in the Software Center. LXDE session will now be available from your login screen.

If you prefer to remove all traces of Unity (not necessary, but will reclaim a gig or so of hard drive space, if you're running low) see here: [http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu)

---

### Post by ponydrvr on 2013-06-19
Thank you snowpine, but the desktop doesn't help. I did that a few months back, and still had video problems. When I tried LXLE the video played pretty well and I figured in actual use after installation it would do the trick. My first post tells what the problem is.

---

### Post by ponydrvr on 2013-07-04
I put my hard drive into another computer that had windows that wouldn't boot. Now it doesn't freeze and I am able to use it. It even plays videos.

---

### Post by Bashing-om on 2013-07-04
ponydrvr; Hey

Where there is a will there is a way ! HUH !

There is no substitute for better hardware.
[INDENT][INDENT]
keep on keep'n on
[/INDENT][/INDENT]

---

