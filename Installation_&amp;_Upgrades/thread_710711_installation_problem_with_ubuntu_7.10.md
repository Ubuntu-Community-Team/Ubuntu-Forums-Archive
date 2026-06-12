---
title: "installation problem with ubuntu 7.10"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by aquaticneko on 2008-02-28
Hello,

I am a newbie at installing ubuntu and i recently downloaded the ubuntu gutsy gibbon. I followed tutorials and correctly burned the image to a cd. But my problems lies whenever i try to load the live cd.
It boots correctly and I select install. the first option in the ubuntu menu. The orange bar zooms left and right for a while and then it moves to a screen with this on it.

[*********) "buffer I/O error on device fd0, logical block 0


Where the asterisk is some numbers are. The screen continues to be filled with this line, with the exception that the numbers increase.
After a while it skips to busybox, asking me for a command.


please tell me the problem...

---

### Post by overdrank on 2008-02-28
> **aquaticneko said:**
> Hello,

I am a newbie at installing ubuntu and i recently downloaded the ubuntu gutsy gibbon. I followed tutorials and correctly burned the image to a cd. But my problems lies whenever i try to load the live cd.
It boots correctly and I select install. the first option in the ubuntu menu. The orange bar zooms left and right for a while and then it moves to a screen with this on it.

[*********) "buffer I/O error on device fd0, logical block 0


Where the asterisk is some numbers are. The screen continues to be filled with this line, with the exception that the numbers increase.
After a while it skips to busybox, asking me for a command.


please tell me the problem...

Hi and welcome, with those errors for me it usually means a bad burn or a cd drive failing. Did you check the cd for errors and  Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by aquaticneko on 2008-02-29
i tried downloading the iso again and using the checksum, which was the same with the hash on the website. but the same error message keep coming up again.


any other suggestion?

---

### Post by Beet-hoven on 2008-02-29
I have what appears to be the same problem.  I've downloaded the 7.10 iso, which I checked the hash of (it was correct), and then I tried to burn the iso onto a CD.  My CD burning software told me the ISO was too big for a CD (argh?!?!), so I burnt it onto a DVD instead.

I booted from the DVD, and was offered a list of options, and chose the 'Install Ubuntu' one.  The bouncing bar comes up - and then it suddenly drops me out with this error message:

[IMG]http://img132.imageshack.us/img132/9333/ubuntuinstallationproblpz0.jpg[/IMG]

I tried burning another DVD, and put 'write verify' on this time, but this new DVD behaves exactly like the first one I made.

Any thoughts?

---

### Post by Pumalite on 2008-02-29
[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

---

### Post by Beet-hoven on 2008-02-29
> **Pumalite said:**
> [http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

That's a long, complicated thread!  But, the answers in the first few pages seem to me to fall into four camps:

1) Use the 'driver CD' option from the list, and just keep using the CD you've burnt
2) Put a random floppy in the floppy drive
3) Boot off a different drive
4) Use the server installation CD iso instead of the desktop installation CD iso

I managed to get Ubuntu to boot by booting the DVD I burnt in my *other* DVD drive, not the one which burnt the disc.

Hopefully this kind of stuff will be rapidly fixed - falling at the first hurdle with crazy output on screen is offputting to newbies.

---

