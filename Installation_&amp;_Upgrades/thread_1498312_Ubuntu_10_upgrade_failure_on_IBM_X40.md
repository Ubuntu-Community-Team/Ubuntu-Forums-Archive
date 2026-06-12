---
title: "Ubuntu 10 upgrade failure on IBM X40"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by markling on 2010-05-31
Computer won't startup after upgrade from Ubuntu 9 to 10.04 Lucid.

Upgrade performed through Update Manager.

Have repeated this exercise with the same result. (After failed first time, reinstalled v9 successfully. Waited a few weeks then tried updating to v10 again. Same unsuccesful result as last time I tried it.)

Got one error message during upgrade: "Missing resoureces. The Network Manager Applet could not find some required resources. It cannot continue."

Upgrade otherwise appeared to operate smoothly.

But:

When upgrade complete, and on restart, the following happens:

Gets to purple start-up screen fine. The dots tick away for a little while, the hard drive accesses, then goes to blank screen and all stops. Nothing. Keyboard doesn't work. Screen backlit, but no-one's home.

Restart again makes no differnce.

Machine: IBM Thinkpad X40

---

### Post by Gerard08 on 2010-05-31
Markling,

This may be way off, but check to see whether synaptic has a later version of the kernel that you can install. If you have a Nvdia graphics card, see whether there is a new version of the driver in synaptic. If there is, install the driver first, then the new kernel. I was really stumped during one upgrade with a blank screen and a blinking cursor. Also try a fresh, live cd

Ger

---

### Post by markling on 2010-06-02
Thanks Ger. Will try these and let you know what happens.

---

### Post by utnubuuser on 2010-06-02
You might also try the "nomodeset" fix...  It's a fairly common solution to a fairly common problem.
 
Here's a link to a how-to:[http://www.absolutelytech.com/2010/05/01/solved-blank-screen-while-booting-lucid-lynx-on-older-ati-graphics/]("http://www.absolutelytech.com/2010/05/01/solved-blank-screen-while-booting-lucid-lynx-on-older-ati-graphics/")

Have a read through forum sticky on common issues for Lucid.

The easiest way to check the nomodeset fix is to select the kernel to boot in grub, while selected, press e then use the arrow keys to scroll to the line that begins with 'kernel', then scroll to the end of that line and add nomodeset after quiet splash, then cntrl+x to boot.

---

### Post by markling on 2010-06-13
Thanks chaps. Please excuse me for this late reply to your kind suggestions.

My graphics is neither nvidia nor ATI.

It's an Intel 82852/855GM integrated graphics.

I have further info re. the failed install.

Ubuntu 10.04 will not install on my machine from a CD either.

I have a brand new installation of 9.10 on my computer, with all the updates. I have an Ubuntu 10.04 CD in my external USB drive (downloaded from Ubuntu downloads and burned as ISO image).

If I boot from CD the following happens:

Boots up with purple Ubuntu title screen. The CD works hard for about a minute while the dotdotdotdot ticker ticks on the Ubuntu title screen. Then the screen goes blank and all activity stops.

Note: it did not even get to begin the installation process.

This compares to my failed attempt to upgrade to 10.04 using the Update Manager in the following way:

The update upgrade appeared to work, it went through all the motions, giving me installation options, appearing to get to the end of the process. But on restart it does the familiar hang: purple Ubuntu 10.04 title screen, tick-tick, blank screen, dead.

The external CD upgrade just goes straight to the familiar hang: purple Ubuntu 10.04 title screen, tick-tick, blank screen, dead.

Note 2: I have repeated this process using the update manager again after verifying in Synaptic (to the best of my ability) that the kernel was the latest version.

Note 3: If after upgrade I press <Esc> while on the purple tick-tick title screen before it hangs, I get to see command lines - i have time to catch the first:

"(process: 255) GLib-warning getvid getpwid_r(): failed due to unknown user id(0)".

To recap: I am unable to install 10.04 on my machine using either bootable CD or upgrade using Update Manager.

---

### Post by inversecow on 2010-06-15
> **markling said:**
> 
My graphics is neither nvidia nor ATI.
It's an Intel 82852/855GM integrated graphics.


Hi markling,

Sorry to be the bearer of bad news, but you have struck afoul of a "known-bug".

You can find more information on it (and some potential fixes below).

# Basic fixes
[URL="https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes"]
https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes[/URL]
(NOTE: Method A worked for my laptop (Compaq Presario M2010US, same GFX chipset), enough to be operational but without the ability to do any graphical "heavy lifting" (like watching movies or playing intensive games))

# Advanced fix
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511?comments=all]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511?comments=all")

Hope this helps.

---

### Post by markling on 2010-08-27
Thanks v much, inversecow. I shall have a look at this and let you know how it works out.

---

### Post by markling on 2010-08-27
No good. Still not working.

I tried:

# Advanced fix
[https://bugs.launchpad.net/ubuntu/+s...1?comments=all](https://bugs.launchpad.net/ubuntu/+s...1?comments=all)

I do indeed have that chipset and this is indeed a problem that seems to afflict my computer. But. I did the fix. Then tried to upgrade to Ubuntu v10. It crashed during startup in exactly the same way it did before I did the fix.

So I reinstalled 9.10 again. I still cannot install v10 on my machine. Boo hoo.

---

### Post by markling on 2010-08-27
Seems I may have erroneously followed the commands given for that patch. But another problem has arisen.

Of the given commands to install the patch, the first is incorrect (apt-add instead of add-apt). In trying to correct that mistake I ended up entering the other commands incorrectly instead.

But now another problem with the same patch. Last command in the sequence generates the following error:

couldn't find package linux-image-2.6.34-v9patch-generic

---

### Post by markling on 2011-01-10
I got further advice on this bug from Canonical's support bods.

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

On attempting to install 10.10 on the IBM ThinkPad X40 again, but using the latest 10.10 download, it simply worked.

I've yet to discover whether the given workaround is required.

---

### Post by brianthefolksinger on 2011-02-01
i just upgraded LTS H to L on an IBM x40. same problem. managed a temp workaround choosing recovery mode at boot up then choosing "failsafe - low-graphics" mode, which works, though is not a solution, but then everything seems to work, except wireless WEP authentication windows keeps popping up continually..though the web keeps working in the background whether I keep connecting or cancel the window, then it seems to be gone. I'm using it now. though wireless indicator says red exclamation, probly need to reconnect. 
want to stay with 10-4 LTS to avoid constant upgrades (system is for my 81 yr old ma, who was happy with hardy post XP) the low-graphics mode seems good enough if I could make it boot this way automatically that could be ok. seems the existing solutions didn't work for markling, though he said 10-10 works, figure 10-4  should be able to. suggestions?
thanks!

took a lot of trial and error to finally try the solution,, still in 10.4 LTS, not 10.10
used
[http://ubuntuforums.org/showpost.php?p=10067580&postcount=7](http://ubuntuforums.org/showpost.php?p=10067580&postcount=7)

which I found among the many solutions but tried others first, this was nice and clear version, though for 10.10 not 10.4 it seems to work so far, haven't edited grub though that is mentioned in post, assume it refers to a solution didn't work in earlier trial-error efforts. (i915.modeset=1 suggestion)
wish there was a way to bring final solutions to fore somehow..reduce trial and error forum search time.. spent a few hours trying and searching though the final solution took minutes. perhaps searching by computer model is best. would have been quicker if I'd hit this post first
[http://ubuntuforums.org/showthread.php?t=1633807&highlight=x40+10.4+LTS](http://ubuntuforums.org/showthread.php?t=1633807&highlight=x40+10.4+LTS)
perhaps make it a top result for any "x40" searches?
it didn't come up in my original searches while this thread seemed right on my problem
now to search for a solution to networking problem!

---

