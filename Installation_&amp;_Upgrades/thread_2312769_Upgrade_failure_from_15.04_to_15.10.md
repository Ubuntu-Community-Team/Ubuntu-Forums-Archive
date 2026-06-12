---
title: "Upgrade failure from 15.04 to 15.10"
date: 2016-02-07
forum: Installation &amp; Upgrades
---

### Post by Edward_Diener on 2016-02-07
I have twice attempted to upgrade from 15.04 to 15.10 using the instructions at [https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes?_ga=1.139645555.1173134091.1453928447#Upgrading_from_Ubuntu_15.04](https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes?_ga=1.139645555.1173134091.1453928447#Upgrading_from_Ubuntu_15.04). Each time I attempt the upgrade the steps are successful until the downloaded upgrade files are being used to upgrade the installation. I will watch the upgrade for awhile but since it is a long process at that stage I walk away from my computer and recheck periodically how the upgrade is going. Both times I have attempted the upgrade I have come back to my computer, at about the time when about 40% or so of the process of upgrading the files are complete, only to find that my computer has completely shut down. When I try rebooting into Ubuntu I get a sign-on screen but after signing in the entire user interface is lost with only a few icons showing on the screen, no panels or launchers, and nothing is there to work.

I have taken a backup so I can always restore my partitions. But I have no idea why the Ubuntu upgrade from 15.04 to 15.10 fails. Of course the next time I try it I can sit at my computer for the hour or two the upgrading of the installation files is being done but this will be tedious and for all I know the upgrade process will probably shutdown again before I can see what is going on.

Does anybody have any idea why this simple upgrade is failing ? Is there any file I can look at, if I can get to a Ubuntu console itself, to see why the upgrade has failed ?

---

### Post by kansasnoob on 2016-02-07
The logs will be in /var/log/dist-upgrade.

I'd begin by checking to see if just running apt-get update and apt-get -f install provide any info or show any errors.

---

### Post by kansasnoob on 2016-02-07
BTW if you've not yet restored your backup you can open a terminal with Ctrl+Alt+F1. You could then try the commands above to see what the output says.

---

### Post by grahammechanical on 2016-02-07
Sometimes an upgrade to a newer version requires user action to OK something or other. If there is no input from the user the upgrade process may stop. Just a guess.

---

### Post by Edward_Diener on 2016-02-07
> **grahammechanical said:**
> Sometimes an upgrade to a newer version requires user action to OK something or other. If there is no input from the user the upgrade process may stop. Just a guess.

If the upgrade process stopped, that would be one thing. But shutting down the machine ?

I guess the next time I have to sit at my computer and watch the entire upgrade process.

---

### Post by Edward_Diener on 2016-02-09
By watching the upgrade continually when it is happening I discovered what is causing the upgrade to shutdown the computer. At some point in the upgrade process, after all the software has been downloaded and unpacked, the upgrade process is setting up its packages. During the setup of one of these packages a message is emitted by Ubuntu on the desktop, and outside of the Distribution Upgrade window itself, "UPS critically low" and Ubuntu then proceeds to shutdown itself based on this perception. Needless to say there is absolutely nothing wrong with the UPS connected to my computer. Some upgrade package being setup is no doubt causing Ubuntu to think that the UPS battery level shows that the UPS has no more backup power.

Is this a known problem with the upgrade from 15.04 to 15.10 ? 
Is there a workaround for this problem ? 

I suppose there might be some way to tell Ubuntu to not "monitor" the UPS on my system. The actual UPS I use is an APC Back-UPS XS 1500.

---

### Post by Edward_Diener on 2016-02-09
I was able to complete the upgrade without shutdown by removing the USB connection between my APC power supply and my computer so that Ubuntu did not think I had a power supply when I upgraded.

The upgrade completed without problems but after I rebooted and signed-in the only things I see on the screen are some icons, and there is no Launcher and no top Panel with the various icons and menus which I would normally see. Interesting enough the login screen itself does show the top panel area, but once I am logged in it completely disappears.

I had installed Nemo under Ubuntu 15.04 and set Nemo as the file manager instead of Nautilus, which I dislike. This may be the cause of why the Launcher and the top panel does not show.

I can get a terminal via Ctrl+Alt+F1.

Thoughts ? Ideas ? Any further help would be appreciated. 

If I can't solve the problem in the current 15.10 boot my thoughts are to restore back again to 15.04, make Nautilus the file manager instead of Nemo, then try to upgrade again.

---

