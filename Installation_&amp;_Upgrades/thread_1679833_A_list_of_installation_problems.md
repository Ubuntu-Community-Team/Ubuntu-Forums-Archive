---
title: "A list of installation problems"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by DD75 on 2011-02-01
Hello all!

I've been working with computers running windows for years now, but I have grown interested in using ubuntu. Installing seemed quite harder then was say on those fancy download pages. Maybe all of these problems have been solved in some other thread, yet I couldn't really find any.

I started downloading ubuntu 10.10 Live CD. Burned it (three times over trying the following again) an then booted it. Then It gave some errors about line 7: can't find ..blahblah../cdc  ..blahblah../cdd . .blahblah../cde a couple of times over.

That didn't work, so I download the USB version. Installed. I couldn't boot it. WHY!!!

Then I tried some other stuff, ubuntu 10.04 too. Can't remember what went wrong there.

I tried 10.10 again, which miraculously booted only when I had put my USB (with ubuntu too) in the computer at the same time. Wow! Progress!

I even got a chance of trying ubuntu, which was totally epic. From there I tried to install it. I even got to the point of entering passwords and assigning and making partitions, which was hard, because I new to this all.

There it stopped however. The installer then had some fatal error about not being able to find additional application data or something and the screen went black. Tried it again with some newly burnt disks, same result.

It kinda drives me crazy, you know. I feel like I've tried everything. Maybe it's my computer and I should buy a new one, or just give up on ubuntu. I have seen a lot of unsolved installation problems on this forum, so you probably can't help me either.
Sorry for the long post and thanks in advance.

---

### Post by davidmohammed on 2011-02-01
hi there - welcome to the forums and ubuntu.

If you give us your computer specifications, maybe we can help

RAM?
Graphics Card?
Processor?
any other cards installed?
USB stuff plugged in?

---

### Post by grahammechanical on 2011-02-01
I got my first Unbuntu CD from a computer magazine. Could you get one that way? It might give you a more accurate CD. I have since downloaded 10.4 & 10.10 and burned them to disc and live booted and installed from them. No problems. But then I was doing it through Unbuntu.

If you look at a forum dedicated to problems you will see nothing but problems. It is just like going to visit the doctor. When I do that all I ever see in the waiting room is sick people.

Make sure your CDs are clean and without scratches and are large enough for the iso file. As regards using a live USB stick, make sure the computer is set to boot from USB in the BIOS. A silly mistake but it is one that must be discounted.

It seems that the CD has inaccuracies or is lacking some files.

Regards.

---

### Post by DD75 on 2011-02-02
About the specifications:
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
CPU Speed: 2.2 GHz Performance Rated at: 4.4 GHz
RAM: 3.0 GB
OS: Windows XP service pack 3
Video Card: GeForce 9400 GT

I copied it from systemrequirementslab.com, because I'm not sure what it all is. You also asked for the USB stuff plugged in. The only thing plugged in besides the mentioned USB stick (16 GB Kingston, don't know if that's important) is a turned off printer. I hope it helps you a little.

About the CD. It was a totally clean disk (no scratches or whatsoever), CD (not DVD) with 700 MB of space. I downloaded the iso twice from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) . I used the same iso for the USB, so making it able to boot from USB doesn't get me much further I think.

Your right about the doctor comparison. I was just a little desperate because I had been trying to get it to work the entire afternoon. I'm more optimistic now.

---

### Post by steveneddy on 2011-02-02
The CD needs to be burned as an image - and at a slow speed - 4X or slower. EZ CD Creator or Nero should take care of this for you.

Try locating the alternate CD install and DL that. Find it here:
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

Also there are sites where you can purchase a CD and have it mailed to you - that may work out better for you.


I thought Ubuntu used to give out CD's on request - if that is the case you may consider going down that road also.

This link should help you with the last two suggestions.

---

### Post by davidmohammed on 2011-02-02
ok you said that you've managed to install but when rebooting you saw just a black screen with a blinking cursor??

Also you said that you've got a nvidia card.  Can I recommend you try and boot with "nomodeset" to see if you can get to a desktop.

When booting, press and hold shift.  This will display Grub.  Press e to edit the boot option.

Find the line containing "quiet splash" - amend the line so that it reads "nomodeset quiet splash" i.e. add the word nomodeset immediately before the text "quiet splash" - then press CTRL+X to boot.

---

### Post by DD75 on 2011-02-03
To steveneddy:
CD was already burnt as an image at the speed of 4×, with deepburner.
And what exactly is the alternate CD?

To davidmohammed:
The install wasn't fully complete, and then after an error went to black screen. After rebooting it just went booting the CD again as if nothing had happened.
Also, what's grub? I know I'm probably asking stupid questions.
I will try that grub thing though.

---

