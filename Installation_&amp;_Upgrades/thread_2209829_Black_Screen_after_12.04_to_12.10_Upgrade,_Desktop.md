---
title: "Black Screen after 12.04 to 12.10 Upgrade, Desktop AMD 64-bit"
date: 2014-03-07
forum: Installation &amp; Upgrades
---

### Post by BlueAZ on 2014-03-07
Hello,  I read most of the stickie on this subject, but just got baffled and overwhelmed.  Can't understand some of the insturctions.  Is 'grub menu' when it shows choices in upper left of: ubuntu / recovery mode / memtest, etc.?  OK, I do get that on restart.  It offers me 2 kernel versions of recovery mode and I've tried them both.  Selecting 'failsafe graphics mode' just gets me the same black screen with blinking cursor upper left, unresponsive to any keystrokes.  Have to do a hard shut-down, which I hate.

The only live CD I have is 11.10 and I can't follow the instructions on how to use it to solve this problem.  I've learned a lot about Ubuntu the past 3 years, but am not a geek!  I need step-by-step instructions on the instructions ;);)

I built this desktop: AMD quadcore processor, 64-bit with PNY Ge Force 8600GT graphics card, PCIe.  In 12.04 I had nVidia driver 295.2 installed, I believe (it may have updated after I made those notes).

What i really wanted was to get up to 13.04, which I have on this netbook I'm using rightnow.  Is there any way to bypass a distro and upgrade to the next?  Just curious.  Might have saved me this dilemma.

Many Thanks, Esteemed Ubuntu Warriors!!

---

### Post by phidia on 2014-03-08
Are you using the nvidia proprietary driver? See if one of the methods [listed her]("http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162078#162078")e will get back your desktop/gui?

---

### Post by BlueAZ on 2014-03-08
Yes, I had already read that.  I'm really out of my depth here.  When I start the computer, it will go into the completely unresponsive black screen unless I go into recovery mode.  Then I have the choice of kernel 3.5.0-47 or kernel 3.2.0-60.  I don't know which to use, so I've tried both.  In recovery mode, the only choice that gets me something useable is to go to the root shell, which scares me a lot.  But I've tried following coding directions in many posts now and nothing has worked.  At one point I could tell it wasn't connecting to the internet.  I found a code way to do something with the dhclient, and it did connect.  But still nothing I tried worked.
Having restarted a couple times, still with no fix, now it won't connect to the internet again, and I can't find the code to do it.  So that would be helpful.  Now I just get things like:  I put in sudo apt-get update, it says:  Failed...  Not using locking for read only lock file /var/lib/dpkg/lock.  Unable to write to /var/cache/apt/  and Package lists or status file couldnot be oparsed or opended.  This is getting wacky because I CAN"T COPY & PASTE!  Sorry...
I really need some help here.  Oh - I did find that there are kernel modules: nvidia_173, nvidia_304_updates, nouveau, nvidiafb all on the computer.  I don't know how to adjust any of that.  It says candidate is 304.88.  I tried to get it thru the terminal, but that's when I couldn't connect...  I'm about to tear my hair out

---

### Post by BlueAZ on 2014-03-25
Well, I never got any real help on this...  One moderator just kept PM-ing me to see if his posts on the subject were unclear, then telling me to just reinstall the OS.  OK, if I'd wanted to reinstall, i WOULD have, do you get me?
The problem here is that my Ubuntu OS repeatedly invites me to UPGRADE, and apparently I'm supposed to just KNOW that this is a bad idea!  Seriously?!  If you all want Ubuntu to succeed in the real world, either come up with an upgrade process that WORKS reliably, don't offer it, or offer it with a warning and a link to some actual instructions!

---

### Post by brad20 on 2014-04-19
this may help but when i first install ubuntu on my computer it would give a blank black screen and wouldnt go away, then i took everything out of the dvd/cd drive and took out usb, idk if it was trying to boot from those things but thats what worked for me:)

---

