---
title: "Hardy upgrade broke xorg.conf for GeForce 7100"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by bkline on 2008-04-27
I upgraded four machines from gutsy to hardy in place.  The first three worked fine (once I figured out that the device file had been renamed for a hard disk on one of them), and with the fourth everything looks OK except the video resolution, which is downgraded from the 1280x1024 we had under Gutsy to a pretty much unusable 800x600.  I would be very grateful for any instructions on how to get it working again.  At this point I feel as if I'm flailing, and I'm afraid I'll make things worse (if I haven't already pushed things beyond repair).

Thanks!

---

### Post by chek2fire on 2008-04-28
Have you install nvidia driver? Try to install them with programme envyng from synaptic.

---

### Post by PmDematagoda on 2008-04-28
Could you post here how you installed the Nvidia driver in the first place?

---

### Post by bkline on 2008-04-28
I installed envyng-gtk, then ran "sudo envyng -t" and asked it to install the NVIDIA driver.  I got the error message telling me id did not recognize my card as compatible with any version of the driver.  So then I ran it and chose the option to install the driver manually.  I made sure the bus ID was set correctly, and then started up gdm.  I got the low resolution dialog, and went into configure.  I picked nvidia as the driver for the card, and the appropriate monitor (same as I had working under gutsy), but the Test button reported that this combination didn't work.  So I was stuck in 800x600 mode.

That's where I was when I posted the original message in the thread.  Since then I went to the NVIDIA web site and downloaded the latest driver package and ran it.  I now have 1280x1024 resolution, but I'm hoping someone can provide a way to get the Ubuntu solution to work, for two reasons.

The first is that, as I might expect, the ATI script didn't leave all the parts of the system as aware of what was going on as it should have.  For example, the applet icons in my Gnome desktop had all been moved to the wrong place.  That wasn't a very difficult problem to solve (I just moved them back to where they belonged), but a worse manifestation is the login screen, which doesn't really seem to know what the screen resolution is, with the result that the username/password box is considerably offset to the right and below center, and the session options at the bottom of the screen are completely inaccessible.  Who knows what other similar gotchas I'll run into.

The second, more serious problem is that I've stepped outside of the package manager's domain, and future updates will be manual and more error-prone than (with the exception of this video problem) I've come to enjoy in the dpkg world.  I suppose one way to look at this is that it was the package manager system which failed me here in the first place, and maintaining the video subsystem by hand on this machine is the best I can hope for.  I would be delighted to discover that that's not right, and to have someone who is able to show me the way back into the fold here.

Cheers and thanks,
Bob

---

### Post by bkline on 2008-04-28
> **PmDematagoda said:**
> Could you post here how you installed the Nvidia driver in the first place?

I realized, after I posted my previous long-winded reply, that you were probably asking about how I got it working in Gutsy, not what I did when it failed on the Heron upgrade (after all, you did say "in the first place").  Sorry for not paying close enough attention. :)

I'm afraid that with the Gutsy experience I was so relieved when I got it working and the experience was so painful that I didn't have the good sense to write down what I did.  I do recall that I had to do some research into how to get the bus ID information from lspci and plug it into xorg.conf, and I know I tried envy at some point, though I'm not certain whether that was part of the eventual solution.

I suppose I'd be more willing to bite the bullet and do a fresh install on this machine if I didn't know in advance that envy still doesn't know how to recognize my card (the GeForce 7100), even though it's been on the market for a while, and it's in lots of machines out there (this is an HP desktop system), but if you tell me that's the only way back to dpkg sanity, I suppose I'll have suck it up and get started.  I'd prefer a solution where I learned something along the way, like where the (driver) bodies are buried, how to tell what's installed, and how to start fresh with the video driver installation without doing a complete system re-install.

Cheers,
Bob

---

### Post by PmDematagoda on 2008-04-28
Did you try installing the driver manually?

---

### Post by bkline on 2008-04-28
> **PmDematagoda said:**
> Did you try installing the driver manually?

I can think of three things you might mean by the question, and the answer to two of them is "yes" and the answer to the third is "no."  I tried the manual install option in envyng, which didn't work, and I downloaded and ran the install script from nVidia, which sort of worked, but left the system in a less than satisfactory condition (for example, parts of the login screen are not reachable).  If by "installing the driver manually" you meant did I download (or build) the binary driver and drop it into the file system in the right place by hand, then no, I didn't do that.

---

### Post by beesthorpe on 2008-04-29
I've also tried Envy, Ubuntu's restricted driver manager and manual installation to try to get a GeForce 7100 to give me 3d acceleration without freezing solid every ten minutes or so, all with no luck.  However I believe I've now located a solution at - [http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-04/msg02948.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-04/msg02948.html) 
This involves installing a recent Nvidia beta driver which "Restored compatibility with recent Linux 2.6 kernels."

---

### Post by bkline on 2008-04-29
Here's an update on what I've learned since the last post.

[LIST=1]
[*]It turns out that gdm thinks that the resolution the monitor is using when the login screen is displayed will always be the first value in the Modes line of the Screen section of xorg.conf, so I was able to correct the funky login screen display by just juggling the order of the values on that line.
[*]There's a bug in envyng [1] which Alberto Milone (the author of the package) believes is responsible for the failure of envyng to set up the video driver in a usable state.  Once that's resolved, I expect to be able to use envyng again (hopefully by the next upgrade).
[*]The fact that envy didn't recognize my card was caused by the fact that Alberto uses a less complete (but he says more reliable) list from nVidia.  I've posted a patch to add the ID for this card, which I've confirmed works with the new nVidia driver. [2]
[*]On a similar note, I found that although the database of PCI IDs distributed with heron does not include the ID for this card, after I ran update-pciids lspci now recognizes and correctly displays the information about the card.
[/LIST]
Hope this information is useful for someone else.  If nothing else, when I come back in six months and have forgotten everything I'll have something to jog my own memory. :-)

[1] [https://bugs.launchpad.net/ubuntu/+source/envyng-core/+bug/221304]("https://bugs.launchpad.net/ubuntu/+source/envyng-core/+bug/221304")
[2] [https://bugs.launchpad.net/envy/+bug/224004]("https://bugs.launchpad.net/envy/+bug/224004")

---

### Post by bkline on 2008-04-29
> **beesthorpe said:**
> I've also tried Envy, Ubuntu's restricted driver manager and manual installation to try to get a GeForce 7100 to give me 3d acceleration without freezing solid every ten minutes or so, all with no luck.  However I believe I've now located a solution at - [http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-04/msg02948.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-04/msg02948.html) 
This involves installing a recent Nvidia beta driver which "Restored compatibility with recent Linux 2.6 kernels."

So you haven't experienced the lack of success which that thread appears to have ended with (so far, at least)?  I guess the focus of the thread was a different card, so perhaps their difficulties won't affect the 7100.

---

### Post by beesthorpe on 2008-04-29
> So you haven't experienced the lack of success which that thread appears to have ended with (so far, at least)?

Ok -  I know it sounds eccentric using an idea that's already been tried and reported as failing, but 1. I was desperate and 2. Don't knock it - it works :) (well at least  the moment...)

The only slight problem I've had so far is convincing it to run at 1289 x 1024.

---

### Post by beesthorpe on 2008-04-29
> The only slight problem I've had so far is convincing it to run at 1289 x 1024.

Hmm - this turns out to be a bit more than a "slight" problem. I ended up having to edit the xorg file and naturally everything is now fubar again :(

---

### Post by bkline on 2008-04-29
> **bkline said:**
> I'd prefer a solution where I learned something along the way, like where the (driver) bodies are buried, how to tell what's installed, ....

I found that the [NVIDIA driver's README manual]("http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/") provides a good step in this direction.

---

