---
title: "Ubuntu in Virtual PC 2004, sound is crackly"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by Frostshock on 2006-10-15
Ok, so I followed the guide at:

[https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004](https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004)

and strangely enough I didn't have to change the DefaultDepth to 16 for me to use Ubuntu. So I went on my merry way and added in the line to /etc/modules so it would detect the emulated sound card. The problem is the sound is crackly, is there a way to fix this?

---

### Post by AnimalMother on 2006-11-26
I have the same exact problem.  Sorry that I cannot help. there seems to be two other problems that ubuntu on Virtual PC commonly has:
no mouse scroll
cannot adjust screen resolution

no amount of tweaking on Xorg.conf fixes these.  Do you have these problems as well?

---

### Post by Frostshock on 2006-12-05
0_0 Holy crap a response. I almost forgot I bookmarked this topic.

I have the same mouse scroll problem! Annoys me to no end in Firefox. I think I can change resolutions though...I can't remember. I keep my virtual machines at 1024x768 so they fit in my 1280x1024 screen.

Hmm...I would be using VMWare since it went free, but it wants a phone number. Maybe I'll try there VMWare Player if that doesn't need a phone number. Or QEMU.

---

### Post by AnimalMother on 2006-12-06
I have to use Virtual PC because it doesn't install a virtual network device on the host O.S.  Virtual PC uses Windoz magic to get around it.  VMware player installs a virtual networking device on the host O.S. <-- I cannot get away with doing that at work. I do use VMware player at home on my wife's Laptop, the only thing it has problems with is DVD playing/recording.  I am sure there is a way around it, but I have not looked into it enough as I mostly use my Linux box at home.

---

### Post by Hendrixski on 2006-12-06
The sound on virtual PC is always crackly.  I use it at work when we're testing software we write for clients, and that windows startup sound on the guest Windows instance sounds like an old vinyl record after a kid with a nail went to town on it.

I was at a clients' and they were using VMWare, and it was amazing, the sound didn't scratch at all, and it integrates better so that you can barely tell that you're virtualizing.

The one time I tried installing Ubuntu on Virtual PC (late at night) I didn't get very far...  Thanks for posting that link, my problem may have been the screen depth.

---

### Post by Hendrixski on 2006-12-06
Ok, so I tried it again with the directions in that first link.  It's a pain to try installing it when the graphics are all funky.  But I decided to just grin and bear it.  After it reboots, shazam it just works.  So to anyone trying to install it, don't worry if your screen looks like a really wide dark mass of squigles, there's Ubuntu under there somewhere.

I didn't hear any sound :(.

---

