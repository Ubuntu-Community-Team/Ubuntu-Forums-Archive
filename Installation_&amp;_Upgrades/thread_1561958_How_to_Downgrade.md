---
title: "How to Downgrade?"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by undrline on 2010-08-26
I believe one of these updates made Ubuntu stop recognizing my USB ports.  I want to downgrade, see if that fixes the problem, and then update them one-by-one to find the culprit.  When I go into Synaptic>Package>Force Version, though, I have a limited choice of versions, which doesn't match ... am I missing something?  Also, how do I downgrade items that I can't force?

libfm-gtk0 (0.1.11-0ubuntu1~ppa1) to 0.1.12-1ubuntu1~lucid1
0.1.10 (DOWNGRADES LIBFM0)

libfm0 (0.1.11-0ubuntu1~ppa1) to 0.1.12-1ubuntu1~lucid1
0.1.10 (REMOVES OTHER PACKAGES)

linux-headers-2.6.32-24 (2.6.32-24.39) to 2.6.32-24.41
CAN'T FORCE

linux-headers-2.6.32-24-generic (2.6.32-24.39) to 2.6.32-24.41
CAN'T FORCE

linux-image-2.6.32-24-generic (2.6.32-24.39) to 2.6.32-24.41
CAN'T FORCE

linux-libc-dev (2.6.32-24.39) to 2.6.32-24.41
2.6.32-24.32

pcmanfm2 (0.9.5-0ubuntu1~ppa1) to 0.9.7-0ubuntu1~lucid3
CAN'T FORCE


The following are less suspect, because they're not as filesystem-related:
libvlc2 (1.0.6-1ubuntu1.1) to 1.0.6-1ubuntu1.2
libvlccore2 (1.0.6-1ubuntu1.1) to 1.0.6-1ubuntu1.2
mozilla-plugin-vlc (1.0.6-1ubuntu1.1) to 1.0.6-1ubuntu1.2
vlc (1.0.6-1ubuntu1.1) to 1.0.6-1ubuntu1.2
vlc-data (1.0.6-1ubuntu1.1) to 1.0.6-1ubuntu1.2
vlc-nox (1.0.6-1ubuntu1.1) to 1.0.6-1ubuntu1.2
vlc-plugin-pulse (1.0.6-1ubuntu1.1) to 1.0.6-1ubuntu1.2
chromium-browser (5.0.375.99~r51029-0ubuntu0.10.04.1) to 5.0.375.125~r53311-0ubuntu0.10.04.1
chromium-browser-inspector (5.0.375.99~r51029-0ubuntu0.10.04.1) to 5.0.375.125~r53311-0ubuntu0.10.04.1
chromium-browser-l10n (5.0.375.99~r51029-0ubuntu0.10.04.1) to 5.0.375.125~r53311-0ubuntu0.10.04.1

---

### Post by lukeiamyourfather on 2010-08-26
If I had to guess I would say the kernel update is the culprit. When booting the system you can select which kernel you want to use in GRUB. The one at the top is the most recent, so go down two options to the last kernel installed. If your USB works again then change the default option in GRUB so it boots into the older kernel.

---

### Post by undrline on 2010-08-27
Thanks for the response.  I only have Ubuntu Lucid installed, but Shift/Esc don't seem to work to get to the grub menu.  Also, commenting out one or both hidden values in /etc/default/grub doesn't work either.  Installed startup manager, the options there don't seem to work to show the grub menu, though it does look like I can choose another kernel that way, so I'll try that.

---

### Post by xangua on 2010-08-27
i belive it's Alt or Shift

---

### Post by uRock on 2010-08-27
> **xangua said:**
> i belive it's Alt or Shift
I've heard it was shift, but haven't had the fun of doing it yet.

---

### Post by undrline on 2010-09-01
Changing the startup kernel in Startup Manager somehow made the grub menu appear.  Neither Shift/Esc/Alt/Tab or any combination, on either side of the keyboard caused anything to happen at boot time.

I tried every kernel option offered (that wasn't a "recovery" option), and none caused my USB ports to be recognized.  None of the options, however, were those that Synaptic said I had upgraded from.  

So, now, I need to try permutations of kernel and the other items that were listed.

Not to say it can't be a hardware issue, but it can't: every single USB port, both front and back (used to be on separate controllers, I believe) have stopped working.  And, they haven't completely stopped working, since they still put out power for the iPod and the external CD/DVD drive.

I'm really looking for my USB ports to start working again, but, back to my original question, I want to get back to a snapshot in time, with exact versions in order to troubleshoot.  How do I do that?

---

### Post by utnubuuser on 2010-09-01
When you make a change in /etc/default/grub, you have to run update-grub afterwards for changes to be recognized, (I'm only mentioning it because you didn't explicitly say that you did).

What is not being recognized on the USB ports?  Flash-drives?

---

### Post by dino99 on 2010-09-01
to see the grub menu, hold "shift" key down [COLOR="Blue"]at end of bios process[/COLOR]

---

### Post by undrline on 2010-09-03
> to see the grub menu, hold "shift" key down [COLOR=Blue]at end of bios process[/COLOR]I tried it at every part of the process of starting up the machine.   Holding it down or pressing repeatedly.  Shift doesn't work, despite what the documentation says. Neither left (as in the documentation,) nor right. Manually adding a delay does work.

> When you make a change in /etc/default/grub, you have to run update-grub afterwards for changes to be recognized, (I'm only mentioning it because you didn't explicitly say that you did).I believe that may have been my issue.  As far as I can tell, all startup-manager does is gives you a GUI for doing this.  It worked, I downgraded (though, like I said, not the version Synaptic told me, and no dice anyway).

> What is not being recognized on the USB ports?  Flash-drives?Nothing USB is working even though it was all working fine before.  I can't use my printers,  webcam, external sound adapter (headset/microphone attached to a usb sound "card"), mouse (fortunately had a serial-usb adapter hanging around), or mount any volumes: external CD(-RW)/DVD(-RW), iPod Shuffle 3G, Flash drives.  I know they're still getting power, because the iPod charges, and the external drive blinks and spins.

I tried completely removing all the vlc packages mentioned.  That didn't change a thing.  I don't see how Chromium would have anything to do with it, since that doesn't even really have anything to do with devices, but that's the only thing left other than pcmanfm2 to try to downgrade before ruling out upgrades as the problem.

If you can point me to "Troubleshooting USB" sticky, I'd be happy to post all the outputs I can get.

---

### Post by coffeecat on 2010-09-03
A  couple of thoughts.

If there was a package update that caused all USB to fail on most machines, then there would have been a storm of threads on this forum. Which means either that you have been very unlucky with an obscure bug affecting your particular combination of hardware, or that a hardware fault developed coincidentally when you did the update. I suppose it's possible that the USB controller on the motherboard could have failed but that power is still getting through to the USB ports.

To exclude the possibility of a hardware fault, boot up with the live CD and test USB.

Apart from that I'm sorry I can't be of more help.

---

### Post by undrline on 2010-09-03
> **coffeecat said:**
> A  couple of thoughts.

If there was a package update that caused all USB to fail on most machines, then there would have been a storm of threads on this forum. Which means either that you have been very unlucky with an obscure bug affecting your particular combination of hardware, or that a hardware fault developed coincidentally when you did the update. I suppose it's possible that the USB controller on the motherboard could have failed but that power is still getting through to the USB ports.

To exclude the possibility of a hardware fault, boot up with the live CD and test USB.

Apart from that I'm sorry I can't be of more help.

My thoughts exactly.  The one that Canonical sends you snail mail, is that the Live CD?  Regardless, that's going to be a problem.  I originally installed Ubuntu Minimal from a flash drive, then put on LUbuntu, then installed Ubuntu-Desktop from the package manager.  My only CD drive is the one connected via USB.  I suppose I could try booting to USB, and just not partitioning/formatting, to see if it works.  That's a new idea.  Thanks.

---

### Post by undrline on 2011-06-16
k, it's been a long time.  I'm pretty sure I've found the root cause, and need to know how to fix it.  Here's what happened since last time ...


What I found was that I couldn't boot to usb either.  So I chalked it up to hardware issues.

Then, recently, I had a friend of mine come look at it who's much handier in a terminal than I, and it was head-scratcher for him, too.  According to everything he could see, it looked like it should be working.  He even compared my same usb stick between my machine and a different linux machine and found everything to be the same.  He suggested I buy a PCI-to-USB card.

The PCI-to-USB cards arrived today and I had quite the revelation: 
[LIST]
[*]I put in one card.
[*]Fired up Ubuntu (still Lucid).
[*]I put in my usb stick.  It still was bootable, though I wasn't booting to it.
[*]Ubuntu, to my happiness, mounted it.  Ubuntu also showed that it had an unmounted filesystem.
[*]I tried to unmount it via the panel applet.  Nothing happened.  I tried to unmount it via Docky.  Nothing happened.  I tried to unmount it via the icon that appears on the desktop.  Nothing happened.  I opened it via Docky and it showed the Nautilus window with the eject symbol.  I tried to unmount it that way.  It said it couldn't unmount it because usb0 wasn't in my fstab.
[*]I just went ahead an pulled out the stick.
[*]I then tried plugging my webcam into the same usb jack.  Cheese did not recognize it.
[*]I then tried pluggin my webcam into another usb jack on the same PCI card.  It was recognized.
[*]I tried plugging the usb stick back into the original jack, and it would not mount.
[*]I tried plugging it into the jack that the webcam was working on.  It mounted and showed the filesystem as before.
[*]It had problems unmounting, as before.
[*]I yanked it, as before.
[*]That jack stopped working, just as the other one did!
[/LIST]

So, I must be somehow screwing up my usb jacks by not safely removing devices (as I know I should).  That's gotta be the answer!

So, how do I fix it?

---

### Post by coffeecat on 2011-06-16
> **undrline said:**
> It said it couldn't unmount it because [COLOR=Red]usb0[/COLOR] wasn't in my fstab.

**Please** tell me that you have not installed the application usbmount. If you have, then uninstall it now and then we will be able to investigate a system that is working as it should.

I'll explain my thoughts later if usbmount is currently installed.

---

