---
title: "Installation  issues..."
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by NINJAINVENTOR on 2010-06-17
Hi all. I have messed with ubuntu before, but never really got much use out of it, from 9.04 to 9.10. Last night I decided to give 10.04 a shot, and installed it through wubi. My previous experiences with wubi were excellent, so I was excited...When the installation completed, and I was just about to actually get access to the desktop (ie. after the corny slideshow), my computer "megacrashed." I heard a noise that sounded like ripping/burning (though no smoke/heat), and I guess ubuntu died. I was immediately back at a strange screen that looked alot like the black screen where I chose to use windows or ubuntu, with a bunch of other on screen stuff quickly scrolling. To me, this looked a lot like a power failure...except my computer was plugged in. I am now freaked out about ubuntu, as though I can afford to mess with it, I cannot afford to kill my computer for it. Any specific help on wtf happened/if it is fixable. Or should I just uninstall/swear off ubuntu.

---

### Post by darkod on 2010-06-17
Are you suggesting running ubuntu will kill your computer? Come on...

As for what happened, maybe just a video driver issue, or another hardware incompatibility. I would suggest burning the ISO on a cd, and try booting with it in live mode, Try Ubuntu option. That should show you if 10.04 will play nice with your hardware.

This is always recommended before installing, upgrading to a newer version, or installing wubi. You need to know of possible issues in advance.

Try to run the live mode.

And wubi is not a way to use ubuntu anyway, especially not long term. It's just a quick way to try, but you can do the same with the cd in live mode as mentioned. Wubi is trying to work inside windows which is not always achievable sometimes because of windows too, so I can't really recommend it.

Try with the cd, if you like it make a proper full ubuntu install, as dual boot with windows. Forget wubi.

---

### Post by NINJAINVENTOR on 2010-06-17
> **darkod said:**
> Are you suggesting running ubuntu will kill your computer? Come on...

As for what happened, maybe just a video driver issue, or another hardware incompatibility. I would suggest burning the ISO on a cd, and try booting with it in live mode, Try Ubuntu option. That should show you if 10.04 will play nice with your hardware.

This is always recommended before installing, upgrading to a newer version, or installing wubi. You need to know of possible issues in advance.

Try to run the live mode.

And wubi is not a way to use ubuntu anyway, especially not long term. It's just a quick way to try, but you can do the same with the cd in live mode as mentioned. Wubi is trying to work inside windows which is not always achievable sometimes because of windows too, so I can't really recommend it.

Try with the cd, if you like it make a proper full ubuntu install, as dual boot with windows. Forget wubi.

In term of suggesting Ubuntu's "killing potential", anything that dies and goes back to BIOS with strange noises and strange text etc. freaks me out. Plus, at the least, I was worried that I would not be able to boot into windows again. Just out of curiosity, assuming everything did play nice, why not use wubi long term (with a disk defragmenter of course)?

---

### Post by darkod on 2010-06-17
> **NINJAINVENTOR said:**
> In term of suggesting Ubuntu's "killing potential", anything that dies and goes back to BIOS with strange noises and strange text etc. freaks me out. Plus, at the least, I was worried that I would not be able to boot into windows again. Just out of curiosity, assuming everything did play nice, why not use wubi long term (with a disk defragmenter of course)?

I'm not an expert in wubi (in fact, not a huge expert in ubuntu too), but from my non-developer point of view I think it has to do with the fact that you are trying to make OS work inside another OS. Sooner or later there will be issues. And the longer you use it, the bigger the probability.
For example in wubi 9.10 there was one simple kernel update that was making it unbootable. You are using your wubi/ubuntu and you get notification that updates are available. Of course, you click Install and the next thing you know you can't boot it after that.

Even the developer of wubi has said that it's no long term install. The idea was that you either hate it, and uninstall it, or like it in which case you will go for full ubuntu installation. If the developer said that it wasn't planned wubi to be used more than a month or two, that's good enough for me.

After all, you don't have windows installed inside another OS right? So why push ubuntu to install like that. You will have trouble sooner or later. IMHO.

---

