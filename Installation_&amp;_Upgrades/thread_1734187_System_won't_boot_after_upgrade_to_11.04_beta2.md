---
title: "System won't boot after upgrade to 11.04 beta2"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by treksully on 2011-04-20
I ran the upgrade from Ubuntu 10.10 to Ubuntu 11.04 beta 2 today. When the installation completed, the computer restarted with a screen that says "Grub 1.97 beta4" at the top of the screen. There is a prompt at the bottom that says "sh:grub>". Any suggestions on how to fix this or revert back to 10.10? I was able to boot manually by running the "linux /vmlinuz.old" command that I saw on the Grub2 (grub.enbug.org) wiki.

---

### Post by Sef on 2011-04-20
> Any suggestions on how to fix this or revert back to 10.10?

The only way to revert back is to reinstall 10.10.

---

### Post by Hedgehog1 on 2011-04-20
> **treksully said:**
> I ran the upgrade from Ubuntu 10.10 to Ubuntu 11.04 beta 2 today. When the installation completed, the computer restarted with a screen that says "Grub 1.97 beta4" at the top of the screen. There is a prompt at the bottom that says "sh:grub>". Any suggestions on how to fix this or revert back to 10.10? I was able to boot manually by running the "linux /vmlinuz.old" command that I saw on the Grub2 (grub.enbug.org) wiki.

Sadly, the upgrade path does not yet work for Natty/11.04

You can re-install 11.04 using a Natty LiveCD/LiveUSB (save your data first).

Or you can re-install 10.10 using a 10.10 LiveCD/LiveUSB (save your data first).

***The Hedge***

:KS

---

### Post by Blasphemist on 2011-04-20
I'm confused Hedge. I've done an upgrade and I've see others on these forums that did. Sure some have had issues but what is it you mean about the upgrade path?

---

### Post by ezsit on 2011-04-20
Since your system was 10.10 upgraded from Karmic (with grub 1.97~beta4), your original system might be too old, at least your version of grub2 might be a little too old.

---

### Post by drs305 on 2011-04-20
> **treksully said:**
> I ran the upgrade from Ubuntu 10.10 to Ubuntu 11.04 beta 2 today. When the installation completed, the computer restarted with a screen that says "Grub 1.97 beta4" at the top of the screen. There is a prompt at the bottom that says "sh:grub>". Any suggestions on how to fix this or revert back to 10.10? I was able to boot manually by running the "linux /vmlinuz.old" command that I saw on the Grub2 (grub.enbug.org) wiki.

From a LiveCD please download and run the boot info script. Post the contents of the RESULTS.txt and we can see what condition your boot files are in.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by stephenlamb on 2011-05-01
I also have this problem after upgrading from 10:10.  The computer dual boots with Vista.  Now I cannot access either Ubuntu or Vista.

---

### Post by jz32300 on 2011-05-01
Me too. Beginning to wish I hadn't taken the suggested upgrade... :(

I had a dual boot setup - Windows XP and Ubuntu 10.10.

Since upgrading the PC hangs when I try to boot into 11.04 - blank screen with Caps Lock key light flashing. The same when I try to boot into XP except that there is also a flashing underscore in the top left of the screen.

If I select "recovery mode" I get a message in the top left telling me that kernel version xxx.Xxx.xxx is loading, but the PC hangs.

If I select "Previous linux versions I can boot into 10.10 but the GUI has changed - I no longer have the task bar at the bottom with the choice of multiple desktops, just a type of dock on the left with icons of available programs etc.

Please can somebody tell me how I can recover from this? I need to access the installed XP and I want to get rid of 11.04 as it is obviously not ready for distribution.

[EDIT] Additionally, I no longer have the menu at the top of the screen in 10.10 - how do I get this back?

Thanks in advance
Clive

---

### Post by jz32300 on 2011-05-01
I seem to have resolved my problems with XP and 11.04. Very strange, and I now know that the user interface issue is due to Unity being installed even for my 10.10 installation - I REALLY didn't want that!

But I can't find a way to switch back to Gnome - SO annoying!

Well thanks for all help.

Cheers

> **jz32300 said:**
> Me too. Beginning to wish I hadn't taken the suggested upgrade... :(

I had a dual boot setup - Windows XP and Ubuntu 10.10.

Since upgrading the PC hangs when I try to boot into 11.04 - blank screen with Caps Lock key light flashing. The same when I try to boot into XP except that there is also a flashing underscore in the top left of the screen.

If I select "recovery mode" I get a message in the top left telling me that kernel version xxx.Xxx.xxx is loading, but the PC hangs.

If I select "Previous linux versions I can boot into 10.10 but the GUI has changed - I no longer have the task bar at the bottom with the choice of multiple desktops, just a type of dock on the left with icons of available programs etc.

Please can somebody tell me how I can recover from this? I need to access the installed XP and I want to get rid of 11.04 as it is obviously not ready for distribution.

[EDIT] Additionally, I no longer have the menu at the top of the screen in 10.10 - how do I get this back?

Thanks in advance
Clive

---

### Post by drs305 on 2011-05-01
> **jz32300 said:**
> I seem to have resolved my problems with XP and 11.04. Very strange, and I now know that the user interface issue is due to Unity being installed even for my 10.10 installation - I REALLY didn't want that!

But I can't find a way to switch back to Gnome - SO annoying!

If you are now using Unity, try clicking the top right start/shutdown icon. Select 'System Settings', then in the System section: Login Screen. Unlock, and then click on the "Select xxx as default session" selection box and choose "Ubuntu Classic"

---

