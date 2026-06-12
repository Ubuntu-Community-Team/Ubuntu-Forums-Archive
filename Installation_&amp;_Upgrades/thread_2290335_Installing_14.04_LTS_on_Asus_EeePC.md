---
title: "Installing 14.04 LTS on Asus EeePC"
date: 2015-08-11
forum: Installation &amp; Upgrades
---

### Post by ClockworkMonk on 2015-08-11
I'm trying to talk a remote non-technical user through installing 14.04 LTS on her Win 7 EeePC 1015 on a Kingston Traveller 8GB USB stick I sent her. Her Windows is pretty messed up due to a botched (and unwanted/unrequested) Win10 download, so we've decided to move over. 

I've searched the forums and found a lot of similar problems, but none that correspond to the issue we're having. 

The EeePC won't boot from the stick by itself. By pressing ESC during start-up the option to boot appears and the PC will then boot, and we can start the install OK, but at the first point where the Ubuntu install process reboots the PC (and she presses ESC appropriately to divert the boot back to the stick) the whole install process starts from the beginning again and we can't get past that point.

We can also reach the BIOS settings via F2 (sometimes...). The USB stick is also the first boot device in the BIOS settings, but is in square brackets, which - the BIOS informs us - is disabled: "A device enclosed in the parenthesis has been disabled in the corresponding type menu.". So far, I've been unable to find what this means or how to change it, but I have found innumerable people asking! I don't know whether this is relevant to Ubuntu not picking up the install properly on the reboot. 

If we don't try to install from boot but go through to live Ubuntu, that works OK. However, if we then try the installation option from within the live OS, it behaves exactly as before and we get into the reboot-to-initial-install loop again. 

About the only thing I can think of trying is a different USB stick, but it will get very tedious and rather expensive having to iterate through that process by post. 

Any ideas?

Thanks,

Rupert

---

### Post by QIII on 2015-08-11
Hello!

If you are using the USB drive as an install medium and targeting the HDD on the eeePC as the install location, then the USB drive should be removed at reboot to allow the machine to boot from the HDD.

Or am I misunderstanding your intent?

---

### Post by mörgæs on 2015-08-11
Not that is solves your booting problem but an Eee is weak hardware. I would feed it something lighter than Ubuntu.

---

### Post by ClockworkMonk on 2015-08-11
Aha - I've just got off the phone with my remote installer, and there was a misunderstanding. I had told her to take the key out when the Ubuntu install had asked her to, and she told me it hadn't asked her to when it did the reboot - and I was assuming that this was some sort of interstitial reboot before the actual key-out stage. I've done a metric tonne of Ubuntu installs, so I should have known that doesn't happen, but when you can't see it and it's on hardware you don't know, then misunderstandings can creep in. 

It turns out that the install is rebooting on its own, immediately after the selection of how you want Ubuntu to co-exist (or not) with Windows, so the install process is actually crashing at that stage. I don't think there's anything odd about the disk set-up, which is a 250GB drive split into C and D of equal sizes and plenty of free space, and (I imagine) a couple of smaller partitions for the Asus stuff. 

I'll go and research that syndrome and if I find something, I'll mark this thread done. If anyone can point me at the right place before that happens, that'd be appreciated.

---

### Post by QIII on 2015-08-11
> **mörgæs said:**
> Not that is solves your booting problem but an Eee is weak hardware. I would feed it something lighter than Ubuntu.

This.

---

### Post by ClockworkMonk on 2015-08-11
My remote installer specifically requested Ubuntu, as she is somewhat familiar with it. Once we get it working, I may well send her something less beefy to try, but I'm a big fan of changing one thing at a time!

On research, my boot problem appears to be documented and is connected with the way the OEM partitioned the hard disk (the clue is that the installer offers "Install Ubuntu inside" (rather than "alongside") "Windows". While I don't have a fix yet, I do have a path forward - which will involve talking a non-tech user through partition changes, which I'm not looking forward to.

---

