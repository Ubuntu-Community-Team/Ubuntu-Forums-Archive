---
title: "Black screen while trying to run Ubuntu 12.04 LiveCD"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by nipunshakya on 2012-05-06
Hello friends and gurus. 
I have Ubuntu 11.04 installed in my Dell Inspiron 1440 as the sole OS. Till now i am happy with my system. When 12.04 came out, i downloaded it, burnt it to a DVD and even made a live Usb of the iso. Every ubuntu distro i ever tested on my machine worked fine till this 12.04. 

I tried to run the 12.04 (64-bit) via livecd. But it ended up with a blank screen, no beeping underscore on top left corner and nothing. It just seemed like the laptop was sleep. I ended up with a hard power off.

Next, i booted to livecd and hit F6, selected NOMODESET and booted into live mode. This time, UBUNTU 12.04 appeared on middle of screen. But then, after a minute or so of the text's appearance, a series of error started to flow. it was written something like SQUASHF ERROR <Other texts>.....
and after sometime, a black screen showed up showing Authentication Failure.

This is the first time i had this error...any suggestions would be thankful...

---

### Post by darkod on 2012-05-06
Try to download the image again, it might have been corrupted during download. I prefer downloading from torrent because it check for corruption during download.

Then make the live usb again and try again. You might still need to use nomodeset.

If you are burning the image, try it on a cd, not dvd, and burn it at low speed, not more than 8x-10x.

---

### Post by nipunshakya on 2012-05-06
Copied that...im on it. :) thanks for the quick reply.

Happy Linuxing.

---

### Post by Bristol_Green on 2012-05-07
> **darkod said:**
> Try to download the image again, it might have been corrupted during download. I prefer downloading from torrent because it check for corruption during download.

Then make the live usb again and try again. You might still need to use nomodeset.

If you are burning the image, try it on a cd, not dvd, and burn it at low speed, not more than 8x-10x.

I used a dvd because I read somewhere that future installs would be too big for cd. I now have the error reported [here]("http://ubuntuforums.org/showthread.php?t=1965802"). Why would burning the iso to a cd rather than a dvd make a difference?

---

### Post by darkod on 2012-05-07
> **Bristol_Green said:**
> I used a dvd because I read somewhere that future installs would be too big for cd. I now have the error reported [here]("http://ubuntuforums.org/showthread.php?t=1965802"). Why would burning the iso to a cd rather than a dvd make a difference?

In general it shouldn't. Except the fact that DVDs are written much faster than CDs because of their higher capacity. 4x with dvd is not the same as 4x with cd.

A very good rule for an OS installation media is: the lower the burning speed, the better.

Any chance there was a bad image floating around, even if the disc check says it's OK?

I don't know about the size of future installs, but right now the image fits on a CD so you can burn it on one. When it fits only on a DVD we'll have to use them. :)

---

### Post by Bristol_Green on 2012-05-07
Thanks for that Info, Darko. I'll try burning it to a cd as soon as I can and report back.

ETA: I'd used DVDs successfully in the past, so not having a cd to hand, I downloaded the iso again and burned it at the slowest available speed (2x) to another DVD. Same crash as before: after importing my account. 

(I'm using 11.10, not 11.04 as it says on the left. I can't change my user profile until my post count >50.) I installed Lucid 10.04.03 alongside 11.10 with a view to upgrading from the previous LTS. Unfortunately it doesn't give me an internet connection via my Netgear wna1100, so I can't do that either.

ETA: Upgraded successfully from Lucid.

---

### Post by nipunshakya on 2012-05-10
Sorry for reporting late....

So i downloaded the torrent thing of the ubuntu 12.04 iso. It worked...and like before, without any hesitation, my system happily accepted linux without any modifications required...

Thanks Drako.

---

### Post by nipunshakya on 2012-05-10
So the installation went fine...but with a major error i guess... i got an error message that the installer has crashed...and that i had to report a bug regarding update manager or something like that.... i did... and restarted. Now, my system has 12.04 running, but on the notification area, i have this warning sign saying that i have unmet dependencies.
The Update Manager wont even open .... any ideas gurus?

---

### Post by nipunshakya on 2012-05-10
two things more...

1. the dash home  wont show applications.

2. the programs i installed when i used 11.04 won't show up too. Actually i had a separate /home back in my 11.04. While installing 12.04, i just marked my old /home as the new /home without marking it to format. Seems like i have all bookmarks of my previous firefox as they were back in 11.04. But the applications like ellipse, gimp, etc that i installed in 11.04 aren't available in 12.04 now. 

Any help would be much appreciated gurus. Thank you.

Happy Linuxing, :D

---

### Post by nipunshakya on 2012-05-21
Latest update. I guess the iso image i downloaded back then was corrupt. Now that i downloaded again, i checked the media for errors and after everything was ok, i installed again. the installation went fine...no problems till now...

Happy Linuxing

---

