---
title: "win 7 dualboot question"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by MuffinMan123 on 2010-03-26
So my computer has ubuntu 9.10 installed 1st and I want to install win 7 in a separate partition. Basically, ubuntu 1st, win 7 later

so far from what I learned from search results, grub 2 have problem with win 7 installed later and what was recommended was install win 7 before ubuntu. how ever I do not have the time to start over again because there are too many things to back up or install again.

So has this problem been solved? or can I simply revert grub 2 to grub 1 again and resolve the problem?

what are some known solutions to this problem?

---

### Post by Wiebelhaus on 2010-03-26
It's not exactly a problem more like a design , you must install 7 first them install Ubuntu , there's no way around it.

---

### Post by derekeverett on 2010-03-26
Windows has a nasty habit of thinking it's the only show in town and will not recognize your Ubuntu partition. It will just wipe it out.

The easiest way is to install Win7, then Ubuntu.

I have seen long winded tutorials that will do it the other way around but they seemed like more trouble then they are worth.

---

### Post by divague on 2010-03-27
I've installed win 7 after installing ubuntu 9.10 and i had no problems. Just do a normal Windows install, and follow this guide to reinstall grub 2 [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202).

---

### Post by Wiebelhaus on 2010-03-27
> **divague said:**
> I've installed win 7 after installing ubuntu 9.10 and i had no problems. Just do a normal Windows install, and follow this guide to reinstall grub 2 [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202).


Yea , I didn't think about installing grub after , Good call.

---

### Post by presence1960 on 2010-03-27
> **Wiebelhaus said:**
> It's not exactly a problem more like a design , you must install 7 first them install Ubuntu , there's no way around it.

Not true at all. When installing windows after linux the GRUB bootloader is overwritten by windows and the windows bootloader is placed on the MBR. The ubuntu partitions are still intact & untouched. All that needs to be done is to reinstall GRUB to the MBR.

See these for more info:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Same procedure for windows 7. I just wish people in here will stop saying that you have to install windows first because it just is not true. What they should say is that they do not know how to help if you have linux installed first then decide to install windows.

I have 10.04, 9.10, Mint 8, Sabayon 5.0 and Vista installed. Installed Vista last. Took all of 60 seconds to boot from the Live CD and reinstall GRUB to MBR.

---

### Post by presence1960 on 2010-03-27
> **derekeverett said:**
> Windows has a nasty habit of thinking it's the only show in town and will not recognize your Ubuntu partition. It will just wipe it out.

The easiest way is to install Win7, then Ubuntu.

I have seen long winded tutorials that will do it the other way around but they seemed like more trouble then they are worth.

Totally false! See post #6. It takes all of 60 seconds after windows is installed to boot the ubuntu Live CD and reinstall GRUB to MBR. I don't know what how-to's you have been reading.

---

### Post by oldfred on 2010-03-27
+1 for presence1960

And grub2 is much better at finding windows installs than old grub legacy.

After reinstalling grub2 to the MBR and rebooting.
run this to find windows:

sudo update-grub

---

