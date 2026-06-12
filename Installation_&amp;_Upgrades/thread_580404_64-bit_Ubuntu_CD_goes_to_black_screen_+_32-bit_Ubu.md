---
title: "64-bit Ubuntu CD goes to black screen + 32-bit Ubuntu freezes/beeps on restart"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by lixoman100 on 2007-10-18
I was told to repost this here instead of General Help. so here it goes. I hope someone here is able to help me with this.


Hello there,


I'm having the strangest problems here.

I have a Core 2 Duo E6700 with 2gb of RAM here, currently running 32-bit XP and 64-bit Vista. Today I downloaded 7.10 64-bit, deciding to try moving permanently to Ubuntu once again.

When the cd finished downloading, I burned it to a DVD-RW, put it on my drive and restarted. After restarting, my computer booted, found the cd and showed up the menu. I selected the first option to boot into Ubuntu. I see a progress bar, the screen goes blank, something about "kernel setting tables" shows up on the bottom of the screen and the screen goes black. Nothing else appears, no matter how long I wait. It doesn't seem to be doing anything.

I though that maybe the DVD-RW was problematic so I got a fresh cd and burned Ubuntu to it and restarted. Same deal.

Ok, so then I try to select "Verify CD for defects" on the menu. Same thing happens, black screen and nothing else. Then I tried "safe graphics mode", same thing. Booting back to Windows, I decided to MD5 check the file, and it was correct.


Then I picked up 2 Feisty Fawn CDs I still had around (ShipIt CDs), one of them is 64-bit and the other is 32-bit. I tried the 64-bit one and the same thing happens - selected the first option, saw a progress bar, some message about the kernel setting some tables and then it hangs on a black screen. I left it there for like 10 minutes before giving up.

Then, for a last test, I tried to put the 32-bit CD and, well, it started! I was thinking, WTH, I'm using a 64-bit Vista, I used to have 64-bit XP installed on this machine, why can't 64-bit Ubuntu run? Well, ok, I'll download the 32-bit Gutsy while asking about it on the forums.

So I click the red power button on the top right corner and select "Restart". The screen goes black and my computer goes "BEEEEEP". It just stays on one constant BEEP with no signs of progress until I hard-reset the damn thing.


I found all this to be very strange, because I never had any problems with this computer before, neither did I have any problems like this with Ubuntu, so I don't really know where to begin trying to troubleshoot this. Any ideas and suggestions are appreciated.


Thanks.

---

### Post by Pumalite on 2007-10-18
After all that, I'd do a memtest to start.

---

### Post by lixoman100 on 2007-10-18
How do I do that?

---

### Post by lixoman100 on 2007-10-18
Ok, thank you for your help, but I think i got it fixed.

On the selection screen, I pressed F6, then I went to where it said "splash" I changed it to "nosplash". So Ubuntu booted fine, I saw the screen with the mouse cursor, then the screen died again. I just moved my mouse around the screen was back on. I'm posting from Ubuntu 7.10 Live right now!

Hope this ends up helping someone else.

---

### Post by lixoman100 on 2007-10-19
Dammit, sorry to bother you guys once again, but the problem is back. Well, sort of.

I got Ubuntu successfully installed and all, but now I can't boot into it. I select the first option on GRUB (Ubuntu), the screen goes black and doesn't get out of it (althou I think something might be happening, because I saw some activity on my HUB from my network card).

I booted into recovery mode and tried editing /etc/usplash.conf (changing xres and yres from 1280x1024 to 1024x768) but no dice. How do I add the "nosplash" thing on GRUB? Fixed my live CD, might fix my installation as well, I suppose.

Could it be because of my monitor? I have a LG Flatron L203WT, widescreen LCD connected to my video card via a DVI cable. Works perfectly under Windows.


Any ideas?

---

### Post by adamc55 on 2007-10-20
What kind of video card do you have? There's a nasty black screen bug that sometimes shows up on ATI cards: [https://bugs.launchpad.net/ubuntu/feisty/+source/xserver-xorg-video-ati/+bug/67487](https://bugs.launchpad.net/ubuntu/feisty/+source/xserver-xorg-video-ati/+bug/67487) -- I had that on Feisty.

---

### Post by lixoman100 on 2007-10-20
Yeah I heard about people having that bug on ATI cards, but that is not my case. I have a GeForce 8800GTX.

---

### Post by DeanFX on 2007-10-20
I installed ubuntu completely, now once the grub boot loader loads up, I click the ubuntu, and it shows it loading up in a status bar, then when its done, it just goes to a blank screen.....

anybody have any resolutions for this?
Is this a video card problem?:confused::confused::confused:

---

### Post by Zshazz on 2007-10-20
This is the second time I've had the same problem... interesting...

The 64-bit version of kubuntu (CD version) did this as well. However, it seems as if it loads the OS fine, you just can't see anything. If you give it a few minutes (enough time for it to normally boot up) and press the power button, it takes a moment, as if linux is gracefully trying to shut down the computer, like normal.

And I also have a 8800GTX, so I'd bet money that it is a card-specific issue!

Though, the 32-bit version appears to function fine (except for the fact that it wants me to upgrade to 7.10 even though I already have 7.10...)

---

### Post by StefAndrew on 2007-10-31
I am having the same problem.  Ubuntu Studio 64-bit and after installation, I go to start up and the screen just goes black.  It looks as if it is starting up, just no video.

Dell Vostro 1500
gefore 8600m GT

I've been trying to search for help fixing this, and haven't found anything yet.  If I find anything I will post it here.

Thank you.

---

### Post by Pumalite on 2007-10-31
For 8600-8800 GT

When grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

Hopefully you'll have an xserver
__________________

---

### Post by StefAndrew on 2007-10-31
I was able to get mine working.  It had to do with the usplash settings and vga setting in menu.lst for grub.  Was trying to find the post where I found the fix, but can't seem to find it now.

I've been working offline, so I haven't been able to install the geforce drivers yet.  I'll do that as soon as I get home tonight from work.  Hopefully won't have any problems after doing so, since it seems to be working now.

Just gotta get the sound working now...

---

### Post by noob09 on 2007-11-16
> **Pumalite said:**
> For 8600-8800 GT

When grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

Hopefully you'll have an xserver
__________________

I've been having the same problem. I have a Geforce 8800 GTX with Intel core duo E6600 and when I install 7.10 64-bit version I just get a black screen, 32-bit works fine for me. I'll try this out now.

Thanks!

EDIT: OK, so that didn't work because I can't access the internet from the terminal =/. I'll look into learning how to configure my connection through the terminal.

---

