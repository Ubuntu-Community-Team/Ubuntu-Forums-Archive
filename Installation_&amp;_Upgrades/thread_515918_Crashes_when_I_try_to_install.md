---
title: "Crashes when I try to install"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by animeanonymous on 2007-08-02
Well, I'm a brand new user who's trying to install 7.04 on a vaio laptop.  I get the initial screen with the logo, the options to start or install ubuntu, the memory check option, and the disc check option, among the others.  Whenever I select the start or install ubuntu option, the word loading comes up but the computer freezes there.  The same thing occurs when I select the check disc option.

Earlier when I tried a 5.04 live cd, it said

"I cannot start the X server.  It is likely that it is not set up correctly."

I suspect based on other forum threads in addition to these two failed attempts at ubuntu, though I'm not sure since I couldn't be any newer to ubuntu, that it's having trouble configuring the graphics processor.

So I'm downloading the alternate cd as we speak to see if the text based installer would work better.  

But I still have no idea what I'm doing. 

Any suggestions as to what my problem might be?

My specs are an onboard gpu, 1.66gh intel processor, and a gig of ram.

---

### Post by dabl on 2007-08-02
Probably it is failing to automatically configure itself for your graphics card.  If, when you're looking at the "crashed" screen, you try Alt-F1 or Ctrl-Alt-F1, you may find that you have a text console available.  You can log in there.  Then see if you can follow this to get a VESA display going:

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

In Ubuntu, you won't use "kcontrol", you'll use the "Hardware Information" that is under the "System/Preferences" menu.  :)

---

### Post by animeanonymous on 2007-08-02
So I Click on Start or install Ubuntu, the words loading come up, and I try to press Alt-F1 and Ctrl-Alt-F1 and it does nothing but give me that beeping sound.

---

### Post by dabl on 2007-08-02
Hmmm.  Well, let it run for awhile without touching it (after booting the CD).  Sometimes it takes a considerable while to load up from the CD.  You might be declaring it "hung" before it has finished loading.

Or else, I dunno .....  :confused:

Did you check the md5 sum on your downloaded ISO file?  Did you burn the CD nice and slow, like 4X?

That's about all I can think of ...:confused:

YES, I always get better results from the Alternate Install CD.

---

### Post by animeanonymous on 2007-08-02
Nope I burned it as fast as I could so I'm trying 4x now.  But I didn't check the md5 sum.  

I let the loading screen just sit there for about 20 minutes once before giving up on it.  

So when I try the alternate cd, is it going to be more complicated than the graphical installer?

---

### Post by animeanonymous on 2007-08-02
Well it looks like burning it slow did the trick, I got it to move beyond the loading screen.  Thanks for your help.

---

