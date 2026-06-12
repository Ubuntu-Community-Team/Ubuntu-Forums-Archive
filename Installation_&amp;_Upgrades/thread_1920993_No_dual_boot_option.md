---
title: "No dual boot option"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by dogtag1968 on 2012-02-05
I just did a side by side install of Ubuntu 10.10 along side my Win7 install, my problem is that from the first boot after install I've not had the option to choose between Win7 and Ubuntu. Now I have to say that I have no problems at all with my Ubuntu 10.10 . Everything is working as it should be , but I have some pictures in my Win7 that I would like to recover.

Any help would be greatly appreciated.

TIA

---

### Post by searchfgold6789 on 2012-02-05
Your Windows 7 should be easily accessible from Linux, if it's still there. Hold the shift key when the PC boots to see if Windows is an option for booting. Or, in Ubuntu, Try opening your home folder and seeing if the hard disk is listed on the left pane; that way you can recover your data. Also it should be appearing in the launcher bar on the left.

---

### Post by Mark Phelps on 2012-02-06
If you want to be able to choose which OS to boot into, from a menu, then do the following:
1) Boot into Ubuntu
2) Open a terminal and enter "sudo update-grub" (without the quotes).  This will regenerate the default GRUB config file.  Watch while it runs and you should see it detect Windows 7 on your PC.
3) When done, reboot.

You should now automatically get an OS selection menu when you reboot -- and you can choose which OS to run.

---

### Post by darkod on 2012-02-06
First try what Mark suggested above. This should work as long as ubuntu can detect the win7 boot files correctly.

If it doesn't find them, you will need to run the boot info script (link in my signature) and post the results as explained there so we can see more details.

---

