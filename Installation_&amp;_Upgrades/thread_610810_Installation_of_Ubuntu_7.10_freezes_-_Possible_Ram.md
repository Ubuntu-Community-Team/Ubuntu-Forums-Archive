---
title: "Installation of Ubuntu 7.10 freezes - Possible Ram issue?"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by nixed242 on 2007-11-12
Hi,

     I'm trying to install Ubuntu onto my system, but the installer hangs and locks the system. I either get to the screen where it's loading the drivers and it hangs (red status bar filling in from right to left) , or it'll hang directly after when it's trying to load the desktop. It seems like I get different results and it hangs at different points every time I try to install. I'm thinking it could be trying to address bad memory (1 gig and a 512mb chip installed) or maybe it might be having a problem with my video card (Radeon 9600)? The Safe Mode option gives me the exact same result. 

I'm trying to install the x64 bit version. I have an Athlon 64 bit chip on my system. Any help would be much appreciated.

---

### Post by xracer on 2007-11-12
Same issue here,

I have a Sony with intel Core Duo, tyring to install 7.10 desktop 64 bit 

1Gig memory
Nvidia video
it freezes when it tries to load teh desktop.

Thank for your help

---

### Post by dgtldaydrmr on 2007-11-12
Sounds similar to an issue I once had.
Check this out and see if it helps.
[http://ubuntuforums.org/showthread.php?t=549213](http://ubuntuforums.org/showthread.php?t=549213)

---

### Post by xracer on 2007-11-12
hmmm....

Thanks, I will try to do this as soon as i get home however you mention and alternate install.

Could you please elaborate on this?
Since there is no option to perform such install from taht i saw.

THanks for your help.

Xracer

---

### Post by nixed242 on 2007-11-12
Thanks for your reply. Not sure if it's a similar problem as I can't get past the driver load screen in install without the computer locking up. But I'll give it a shot. 

This is what was reccomend in the thread your mentioned 

---------------------
Get a command line: Ctrl+Alt+F1
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver; then: startx
--------------------

If this doesn't work, I will in fact start pulling memory chips to see if that helps.

---

### Post by xracer on 2007-11-12
Is this what you are refering to as the alternatate install??

"Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

This is located on the download page.

So basically i need to download a different install version correct?

---

### Post by dgtldaydrmr on 2007-11-12
After a text based (alt CD) install my computer would appear to freeze when it would try to load the window manager.It turned out that the video settings needed to be set on generic vesa drivers in order to be able to see anything. 

My computer would freeze 100% of the time on the live CD.
I would try the alt CD if you are not even making it to the end of an install.
If you do make it through the install and as soon as it's trying to load the desktop the screen goes black and stays that way... it is most likely that the video is set incorrectly and will need to be reconfigured via the steps in the link I posted.

Unfortunately I don't have any experience with ATI cards so I don't know all the possible quirks and such.
(my video is nvida based)

I could be wrong.
I am just trying to help out :)

---

### Post by nixed242 on 2007-11-12
Thank You, dgtldaydrmr

I'll give it a try. Can't hurt to try. :)

---

### Post by xracer on 2007-11-13
I will give a try.

However i am getting a little demoralized about the install :(

I have installed OpenSuse 10.3 and Suse enterprise 10 and they both work right away of course i didn't like that i had to do a billlliiiiiiiooooonnnn updates but is ok.

I will give Ubuntu a try again if the alt CD doesn't work i guess i will have to settle for Suse. 

Also i will make sure to review that other post throughly, I like to try all my options before i settle ;)

Thanks for the reply

Xracer

---

### Post by nixed242 on 2007-11-14
I was able to finally install Ubuntu using the alternate install.  My problem was indeed with the video. 

However, I'm demoralized as well. I was able to get into the desktop using Recovery Mode only to find that the install did not set a mount point for my firewire drive (don't know if Firewire is even configured), and it did not set up my network access. I can't get on the net. This worked fine the only time I was able to boot using the regular install.  Maybe it's because I was running in recovery mode?

I hope these configuration problems are easy to resolve, otherwise I might just forget about Ubuntu. Tonight I'll reconfigure X to run in vesa mode and then see what happens.

---

