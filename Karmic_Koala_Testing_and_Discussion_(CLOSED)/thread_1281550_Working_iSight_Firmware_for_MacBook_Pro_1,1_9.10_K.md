---
title: "Working iSight Firmware for MacBook Pro 1,1 9.10 Karmic Koala"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by VanHammersly on 2009-10-03
Hopefully someone finds this useful.  I have a 2006 MacBook Pro 1,1 with Snow Leopard and 9.10 Karmic Koala installed.  At first, in order to get my iSight camera to work I tried installing the from here:

[https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight)

Unfortunately, the driver from Snow Leopard does not work.  

Here's what I did to make it work.  First, I installed the isight-firmware-tools:

sudo apt-get install isight-firmware-tools

When it asked to extract the firmware from the OS X partition I selected No.  Now the isight-firmware-tools is installed but it hasn't done anything yet.

Next, I downloaded the working firmware from here:

[http://www.mediafire.com/?81xtkqyttjt](http://www.mediafire.com/?81xtkqyttjt)

(as referenced by di0rz` in this post: [http://ubuntuforums.org/showthread.php?t=543185](http://ubuntuforums.org/showthread.php?t=543185))

and then went back to terminal and ran this:

sudo ift-extract -a /home/[your username]/Downloads/AppleUSBVideoSupport

After the firmware was installed I then shutdown my laptop (not reboot) and turned it back on.  I have checked this with Cheese and Skype video and it works flawlessly.

------------------

I should say that, aside from this, Koala looks and runs beautifully on my MacBook Pro.  Kudos to everyone involved.  This is shaping up to be a huge evolutionary step for Ubuntu.

---

### Post by kelvin.illa on 2009-10-26
Thanks, man. I stumbled upon this 3 weeks after your posting, trying to find an alternative to 'extraction from Mac OS partition' because I do pure Ubuntu.

I use a MacBook 2,1, and the iSight works "flawlessly" (like you said) and even without the "green filter capture" I used to have -- although I'm not sure whose fault is that since I did a clean install of Karmic-rc.

However, I didn't do 'ift-extract,' instead, I merely changed the default path of 'firmware-tools' to the path of the downloaded 'AppleUSBVideoSupport,' which is '/home/[your username]/Downloads/AppleUSBVideoSupport."

Karmic (even just the rc) is beautiful. The only thing not working out-of-the-box -- besides the above -- was the touchpad (and the brightness controls which is easily remedied by an installation of "pommed," and the audio for the speaker jack which is muted and can be unmuted by 'gnome ALSA mixer').

Oh, and thanks again.

Thanks again

---

### Post by fbugnon on 2009-10-27
Got it working now (MacBook Pro 1,1), sweet.
Thank you for sharing!:D

---

