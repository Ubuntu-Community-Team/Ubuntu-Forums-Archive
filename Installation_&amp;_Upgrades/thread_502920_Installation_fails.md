---
title: "Installation fails"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by alfarin on 2007-07-17
Ubuntu starts to load the installations files.
I can see the progress bar and when i gets full, everything turns black.

If I press Enter key after the "black out"  I can hear the hard drive work so I guess the installation continues, but its kinda hard to get it right when I cant see anything :)

I have tried different screen settings and all that but nothing seems to work.

Text based installation could work but I rather see a solution to this problem.

AMD X2 64 5000+
2gig ram
ATI x1600

peace out.

---

### Post by Pumalite on 2007-07-17
Are you dual booting? With what? XP,Vista? Where did you get your iso. Did you do Md5sum of iso. Did you burn at 4x or less? If Vista; partition from WITHIN Vista. Check CD for corruption before install.

---

### Post by alfarin on 2007-07-17
I got XP pro 32 and 64 bit, each on different hard disks.
Downloaded from ftp.uninett.no The ftp is listed on Ubuntus download page.
No Md5sum. Only the "check disk" that the burning program (SONIC) did after I burned the CD.
I burned the CD at max speed, 24x. But I have no problems to read the CD.

I should add that I downloaded the 64bit version of Ubuntu.

---

### Post by Pumalite on 2007-07-17
The Md5sum is very important. it has to coincide with the one published in the site you discharged from or Ubuntu.org. Corruption in the CD is different to a bad iso. If Dual booting with XP: defrag several times, erase all temp files. I then Use Gparted [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) Alternate CD's are good alternative when having trouble with the 'Live CD'

---

### Post by alfarin on 2007-07-17
Both disks were defraged  before installation.
I will check the CD tonight.

So you don't think this has something to do with the graphics card?

---

### Post by Pumalite on 2007-07-17
I was just starting with the basics. But ATI cards in general and yours in particular could be a problem for the installer. That's why I was gently suggesting the Alternate CD. You avoid graphical interface problems.

---

### Post by dabl on 2007-07-17
It may be that what you perceive as a "freeze" is just a video display problem.  When you get to that black screen and nothing further appears to be happening, try Alt-F1, and if nothing happens, try Ctrl-Alt-F1.  If it's just a problem with the video display, you'll find a text login prompt waiting for you. :)

---

### Post by alfarin on 2007-07-17
Progress!

Ctrl-Alt-F1 did it.
After pressing those keys I find myself at the...the "cmd" if I can call it that without getting shot :)

And I get these error messages:

"**MP-BIOS bug: 8254 timer not connected to IO-APIC**"

and when I try to open any program that uses graphics I get 

"**Unable to open display**" 
or 
"**Display not set**".

I guess I need to get new drivers right?

I will investigate further but I am grateful for any help.

---

### Post by Czargio on 2007-07-17
I also am having an installation error, however when my boot sequence reaches the end of the loading bar graphic, it seems as if my computer becomes completly unresponsive. At this step I tried the alt+ctrl+f1 trick which worked for the OP, but my computer didn't respond. At this stage, the only way to turn off the computer is by holding the power button down until it turns off. The live CD works fine, and the installation goes well until one certain point every time. When I go to shut down the computer to try and boot without the CD, it will eject the CD, and it reads "Please remove the CD, close the tray (if any), and press ENTER to continue." At this point my computer becomes unresponsive also, even after hitting/holding enter, it is frozen, and I need to hold the power button to escape out.

Specs
AMD Turion 64 x2
2gig ram
Trying to dual boot with windows XP
Windows currently working fine. 
Partitions, 25gig for windows, 11 gigs for windows recovery, 6gig ext3 for /, 1gig for swap, and 74.5 gigs for /home in ext3.

---

### Post by Pumalite on 2007-07-17
At this point, after Crtl-Alt-F1>Command Line, you should both try first:

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
The default settings should be ok, only choose 'vesa' as the driver.

Let me know what happens.

---

### Post by dabl on 2007-07-17
> **alfarin said:**
> Progress! Ctrl-Alt-F1 did it. 

EXCELLENT!

> 
the "cmd" if I can call it that without getting shot :)

The pro's call it the _C_ommand_ Li_ne _I_nterface (CLI).  I call it "Oh, sh!t my Nvidia driver musta broke!" **

:)

Once you log in, follow Pumalite's advice.  When you start the reconfiguration script with ```
sudo dpkg-reconfigure xserver-xorg
```

on the first screen choose "NO" to autodetecting, and on the second screen choose "VESA" as the display type, and use your common sense for the rest of it. When it completes, it will dump you back to the CLI.  At that point, you can enter the command ```
startx
``` and you should get a reasonable GUI login. :)

** speaking of which, once you have a GUI and a browser and your minimum packages running, you're going to have to study up on ATI driver how-tos, which I cannot help you with.

---

### Post by alfarin on 2007-07-18
Thanks will try that when I get back from work :)

---

### Post by fjoesne on 2007-07-18
I have a very similar problem with my installation
but i believe that this is another ATI problem, tried both normal and VESA driver but the same thing happens:
Fatal Server Error: 
Caught signal 11. Server aborting

stopping gdm works fine, however:
$ sudo dpkg-reconfigure xserver-org   gives me: Package 'xserver-org' is not installed and no info is available. 

I guess I'm being punished for purchasing ATI graphics :/

just to make it clear, this is the ubuntu 7.04 desktop edition.

> **Pumalite said:**
> I was just starting with the basics. But ATI cards in general and yours in particular could be a problem for the installer. That's why I was gently suggesting the Alternate CD. You avoid graphical interface problems.

Alternate CD ? do you mean the server edition?

---

### Post by Pumalite on 2007-07-18
No, I mean the Alternate CD. 

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Check the box below the green sign that says: Start Download.

---

### Post by alfarin on 2007-07-18
> **Pumalite said:**
> At this point, after Crtl-Alt-F1>Command Line, you should both try first:

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
The default settings should be ok, only choose 'vesa' as the driver.

Let me know what happens.

Ok, so I tried all this and everything looks fin until im going to run "startx"

Then I get this Error message:

-------------

Already appears to be an X server running on display 0
Remove /tmp/.X0-lock

-------------

/tmp/.X0-lock does not exist, at least I cant find it in there.

How to i manually shut down X server on display 0?
Better start downloading the other Ubuntu version, but would be nice to get this working.

Now it would be good with that "OVERRIDE" button on the keyboard that Sylvester Stallone has in one of he's movies:)

---

### Post by Pumalite on 2007-07-18
You stop xserver with this:

sudo /etc/init.d/gdm stop

---

### Post by alfarin on 2007-07-19
I did that, many times and I also tried the other "gdm" options.
Still did not work.

I downloaded the text based iso and it works fine.

Thanks for all the help.

Its kinda sad to see that the installation process have had such a slow development in Linux. Easy installation should be something prioritized, yes the installation process is better now, if you have the right hardware. If you don't, BANG! and I get flashbacks from my first Linux installation 10 years ago.

---

### Post by heracles on 2007-07-19
Make sure APIC is disabled in your BIOS settings

---

### Post by alfarin on 2007-07-19
> **fjoesne said:**
> I have a very similar problem with my installation

$ sudo dpkg-reconfigure xserver-org   gives me: Package 'xserver-org' is not installed and no info is available. 



should be **xserver-xorg** and not -org I guess.

---

### Post by alfarin on 2007-07-19
> **heracles said:**
> Make sure APIC is disabled in your BIOS settings

I guess you refer to my error message.
And the negative effects of doing this? :)

Still need it on when I run XP.

---

