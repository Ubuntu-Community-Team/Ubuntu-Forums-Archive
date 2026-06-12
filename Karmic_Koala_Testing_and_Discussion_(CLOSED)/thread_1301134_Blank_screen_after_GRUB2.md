---
title: "Blank screen after GRUB2"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by soelk on 2009-10-25
I have a problem with the Karmic RC: 

GRUB2 starts and shows both Ubuntu and Windows (and Windows boots just fine). When I try to boot Ubuntu exactly nothing happens. I can press ctrl-alt-FX (F1, F2, F3 and so on) and get a blinking prompt-like thing which doesn't respond. It does reboot if I push ctrl-alt-del when the blinking prompt is visible, before that ctrl-alt-del does nothing.

To elaborate a little bit more, I've been using Windows a lot lately, but I thought to give the Karmic RC a try. I popped in the live CD and... it rocked! :guitar: 
The live CD, that is. Everything simply works and it drives like (ahum) a Ferrari (like I would know).

Consequently, I safely backed up all my data and then I did a fresh install of karmic. And now I'm stuck with no idea of what to do. Except the usual suspect: my old ATI Radeon X800. (But it works great on the live CD - Google Earth under Compiz, and everything.)

Ubuntu works in safe mode and I've been able to download and install the latest upgrades. Fglrx is not installed, which is a good thing, because it's not installed when I run the live CD either. I basically just want my installation to work like the live CD.

---

### Post by soelk on 2009-10-26
I'm half-bumbing this and adding the fact that I can run X from the recovery console by using **startx**.

I can tell from the general behavior of 3D apps that it is running a different video card driver version, although I don't know how to read driver versions in Ubuntu.

The driver in the live CD is very fast, but does give me some flicker in 3D apps when I have multiple windows open. The driver in X (started from console in recovery mode) is quite robust, but much slower and choppier in 3D.

---

### Post by ranch hand on 2009-10-26
There are a bunch of links to great information on the post linked in my sig.

They are all grub2 and I believe your problem is more with, as you say, your ATI card (I have one too).

Have you checked to make sure you do not have a xorg.conf file.  Without adding a driver or other configuration, you should not have one.  If you do, try deleting or renaming it.  It may help.

---

### Post by soelk on 2009-10-26
Thanks for the reply and link. I will browse through that.

As I said this was a clean installation, so there's no xorg.conf file involved. I experimented with a minimal xorg.conf file, that just asks for the ati driver and PCI address or IRQ or whatever it was, and that does indeed break the ability to start X even from the command prompt.

So yeah, rm xorg.conf seems to be a good tip in general. But there was no xorg.conf to begin with in my case, since it was a clean install of Karmic 9.10 RC.

My best guess is that something breaks in the splash screen or login screen program or whatever it's called. (Is it Xsplash? I mean the program that paints a progress animation right after you've selected Ubuntu in GRUB.)

---

### Post by ranch hand on 2009-10-26
You get, in this order, usplash, xsplash, GDM, xsplash, desktop.  I believe that x is supposed to start with the first xsplash.

---

### Post by soelk on 2009-10-26
Allright, progress at last! :)

I figured out a simple workaround. It is basically the first thing one would normally think to do, except I didn't know that you need to use a different key combo on Karmic. When it goes blank, simply push:

[HTML]alt-print screen-k[/HTML]

Easy enough, once you realize that ctrl-alt-backspace is no more.

I think I've had the same symptom on a previous version of Ubuntu. It might be a video card-specific bug that has crept back in. Problem solved for me. However grandma and grandpa would be stuck at this point.

---

### Post by coffeecat on 2009-10-26
> **soelk said:**
>  [html]alt-print screen-k[/html]Easy enough, once you realize that ctrl-alt-backspace is no more.

Not that this helps you much now, but just a fyi about ctl-alt-backspace in Karmic. Once you've got yourself a desktop, go to System > Preferences > Keyboard > Layouts tab > Layout Options button. 8th one down is "Key sequence to kill the X-server" which you can re-activate. Welcome back ctl-alt-backspace! I missed you in Jaunty. :p

Best of luck fixing your ATI card issue. Sorry I can't help you - no experience of ATI cards here.

---

### Post by soelk on 2009-10-26
Ah, thanks. Good to know.

To clarify: my ATI card works great as long as I start X in the usual fashion (plus a restart of X apparently). I'm amazed by the speed of the latest free/community radeon drivers in both 2-D and 3-D apps and in 3-D apps under Compiz in particular. 2-D apps are noticeably faster and snappier than in my Windows XP installation which is reasonably new and non-bloated.

Flash is also faster in Karmic than in Win XP, even in full-screen. It seems that the community developers have done a great job on the older Radeon cards.

---

