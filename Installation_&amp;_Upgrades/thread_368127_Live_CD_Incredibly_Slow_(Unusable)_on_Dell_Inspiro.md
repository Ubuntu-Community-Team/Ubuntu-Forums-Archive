---
title: "Live CD Incredibly Slow (Unusable) on Dell Inspiron 2200"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by SendDerek on 2007-02-22
Hello All!

I've got a problem for ya's!  I'm trying to install 6.10 on a Dell Inspiron 2200 and I can't seem to get the Live CD to respond.  After about 15 minutes of waiting, I can finally see the desktop and "Install" icon, but the system is so slow that I cannot install it.  

There was an error stating this when I first login to the live cd:
> 
cannot enable rng. aborting
bcm43xx_microcode5.fw not available


And then once I'm in the live cd (right when the ubuntu splash screen pops up) I get this error:
> 
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:
Did not receive a reply.  Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.


I think that the Broadcom wireless/ethernet card is goofing things up by quite a bit.  I've read in other thread about it as well.  I was, however, able to install a very old version of Ubuntu on the machine.  The older version didn't have the live CD, it just walked you though a type of command prompt wizard and it installed just fine.  

Which leads me to my question:  If I cannot get the live CD to function correctly, can I install Edgy using some sort of command line instead?  Are there any instructions for that?

---

### Post by mikewhatever on 2007-02-22
You can try using an Alternate CD (text mode installer). It does not function as a live cd and can be downloaded from Ubuntu download page. You might be able to install with it, but if there are hardware problems, it wouldn't solve them, so you'll have to deal with them later.

---

### Post by SendDerek on 2007-02-23
Thanks a bunch...

That's probably exactly what I'll be doing.  I just wish I didn't have to spend 3 hours downloading the install CD... but then again, I would've already had it downloaded and installed if I did it right from the get-go instead of messing around with this.

I'll try that instead.

---

### Post by mikewhatever on 2007-02-23
You may still find the live cd useful, slow as it is, for troubleshooting and recovering. It is a good tool to have.

---

### Post by H.E. Pennypacker on 2007-05-06
I have the same laptop model.  If I am not mistaken, your laptop has 256MB RAM?  That's not going to be nearly enough.  I tried running the Live CD on 256MB, and it was extremely slow too.  Upgrading to 1GB was just what I needed.

Keep in mind that the LiveCD works using RAM.  

Slowness could also be caused by a bad download or a bad burn.  Check md5sum on the file you downloaded to make sure it matches the correct md5sum output.

---

