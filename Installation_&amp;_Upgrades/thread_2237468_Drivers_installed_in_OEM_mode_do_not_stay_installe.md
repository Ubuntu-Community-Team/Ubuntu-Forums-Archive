---
title: "Drivers installed in OEM mode do not stay installed"
date: 2014-08-02
forum: Installation &amp; Upgrades
---

### Post by John_Squar on 2014-08-02
For a bunch of computers I am building for some clients, there is a conflict between the open source drivers for my video card and my motherboard/gpu, leading to random restarts.  I can fix this by installing the proprietary drivers.

So on a fresh hard drive on a different motherboard I install Ubuntu in OEM mode and install the proper drivers.  I put the hard drive in the new computer, and it works fine.  Then I click "prepare for shipping to end user" and restart the computer.  It boots back up and asks me startup configuration questions like its supposed to.  Then it restarts, because for some reason it has reverted back to the open source default drivers even though I went to the trouble of installing the proper drivers in OEM mode.  Isn't that what OEM mode is for?  Installing drivers and custom backgrounds and stuff beforehand so the end user doesn't have to?  Why is this not working?

Basically, I need to configure the computer in OEM mode so that when a client receives their new computer, the proper drivers are ready to go.  There can't be a chance that it will revert to the default drivers, not even during installation, because then the computer will stop working.  Preferably I'd like it so that the clients cannot easily change the drivers back.  How do I do this?

---

### Post by sudodus on 2014-08-05
Hi,

I found your thread un-answered after three days.

I have used OEM, and as far as I understand, the OEM user is almost like any user. If you install user specific tweaks, that are stored in the user's home directory (often as hidden files or hidden directories), they will disappear, when the OEM user is deleted (as it is, when the 'end user' is created).

But if you install drivers for the video cards, they are installed to the system (and with superuser privileges) and stored outside the OEM user's home directory. I can't understand why and how those drivers are removed. But I can think of a situation, when they are not activated: If you port the system to a computer with another brand of graphics chip, a built-in driver will be used. For example, you have installed an nvidia proprietary driver, and the new computer has radeon graphics.

- Can you check if you have the same problem in a normal installation of the same version and flavour of Ubuntu?

- Or have you been doing this in ***a live system***, that reverts back to the original setting after reboot? (Live alias booted from the install CD/DVD/USB drive)

-o-

If users can get superuser privileges (run sudo and gksudo) they can do 'anything' with the computer, but only with those privileges activated. So it should not happen by mistake, if the users understand to be extra cautious while running sudo commands.

The next step is to give the user a standard account without superuser privileges and leave a 'guru' or 'admin' account, and only you have the password for that account. If the end user wishes, you might be able to log in remotely and fix minor problems.

---

### Post by freechelmi on 2015-01-30
I confirm this problem which is very annoying, When we preinstall the Nvidia Blob, the oem-config-dm then just fail with a black screen.
Then we don't ship this driver at all. 

Why do we have such problem ? I don't get it.

---

