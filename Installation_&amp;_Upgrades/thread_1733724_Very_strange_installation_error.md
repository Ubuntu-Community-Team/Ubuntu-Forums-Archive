---
title: "Very strange installation error"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by rhyslegge on 2011-04-19
Hello, this is my first post as I have not been an Ubuntu user for some time.  I am trying to install on an ASUS i7 laptop, which I have wiped the hard drive.  Upon trying to install 11.04 from USB stick, I get as far as the "select install or run from disk, etc." option, and i select install to hard drive.  The Ubuntu screen and scrolling dots appear, and then the screen locks to what looks like a crossword puzzle and a black and white maze.  I have tried all possible install options, USB, CD, 10.10, all with the same result.  Has anybody else had such an issue, and is it fixable?  I have since re-installed windows 7 and ran chkdisk, my hard drive is good.  I have also run memtest overnight with no errors.  Any help would be appreciated, thanks!

---

### Post by Blasphemist on 2011-04-19
It could be a video issue. Have you tried the run from disk option? That will show if your video hardware is supported "out of the box
". Whether that works or not, post your hardware specs here please. What kind of pc is it, how much memory, what hard disc and of course what video controller as that is quite likely the cause of this.

---

### Post by rhyslegge on 2011-04-19
Yes, I have tried that also.  I have an ASUS G51J, i7-720 proc, 8GB DDR3, Nvidia Geforce GTS 360 CUDA video card with 1GB dedicated.  Hard drive is 320GB 5400RPM WD SATA 2.
I agree with you about the video issue, and hope there is a fix or temp. workaround.

---

### Post by Blasphemist on 2011-04-19
I don't know how new your live usb is but I believe you can install the current nvidia package as shown in this launchpad page. [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=natty](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=natty) 

You can update your system with unsupported packages from this untrusted PPA by adding ppa:ubuntu-x-swat/x-updates to your system's Software Sources.

---

### Post by rhyslegge on 2011-04-19
That info is great, thanks for the leg work!  But how do I integrate that into the installer?  If I cant get to the OS, I am kind of stuck, being a relative noob to this kind of thing.

---

### Post by Blasphemist on 2011-04-19
I've been thinking this through and definitely see your point, finally. I was hoping someone else would have jumped in but others seem to have just viewed this thread. 

I think you could create a custom installation but that would require more than I think you have, such as a working Linux system. Just in case you do want to jump in and can, here is the link to how to do it [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

So, other options. Try a different Linux is one option. Kubuntu or Xubuntu for example. I have no experience with them. 

As I mentioned earlier I don't know when you downloaded the iso. Is it possible it has been long enough that the current Ubuntu daily build might be updated from what you have and solve it? It might be worth a try but I can't tell for sure if this is updated in the daily build. [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

I'm afraid I tried to help here in something above my head and I may get grief for that, deservedly. I'm hoping someone else comes in that can get you where you need to go.

---

### Post by rhyslegge on 2011-04-19
No trouble, I appreciate the assistance!  Ill keep trying the daily releases in hopes that my video card will be compatible.

---

### Post by Dutch70 on 2011-04-19
Have you tried other boot options like nomodeset?
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by Blasphemist on 2011-04-19
This looks real promising rhys.

Thanks very much Dutch!!

---

### Post by rhyslegge on 2011-04-20
I havent, I will give it a shot i n a few, thanks!

---

### Post by rhyslegge on 2011-04-20
OK, that worked for the install.  It also works if I boot from the CD, but now when I try to boot from the install on hard drive, blank screen.  I imagine I have to embed that command into the boot order, and then install the Nvidia drivers from the Nvidia website while booted into the OS, sound about right?  Any help, as always, would be appreciated.  Thanks!

---

### Post by Quackers on 2011-04-20
When booting hold down the shift key. This will bring up the grub menu. With the top item highlighted (Ubuntu) press the "e" key.
In the new screen using the arrow keys, navigate to the end of the line which currently ends with "quiet splash" (but without the quotes). At the end of quiet splash press the space bar and then type in nomodeset then press ctrl+X to boot.
If the desktop loads ok, go to System > Admin > Additional drivers and install any graphics drivers (Nvidia - recommended) and reboot. Hopefully it will now boot normally.

---

