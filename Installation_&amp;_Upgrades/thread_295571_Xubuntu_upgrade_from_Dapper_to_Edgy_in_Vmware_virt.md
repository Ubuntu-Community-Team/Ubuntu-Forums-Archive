---
title: "Xubuntu upgrade from Dapper to Edgy in Vmware virtual machine problem..."
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by c_martini on 2006-11-08
I am running a vm on my Windows pc at work and running Xubuntu Dapper 6.06 as the guest o/s. It has been running flawlessly until the other day when I attempted to upgrade it to Edgy.

It all started with the software upgrade wizard (that cut down version of Synaptic that resides in the panel and notifies about updates)... I had not started the vm in a couple of weeks and I wanted to see if there were updated packages available...

The upgrade dialog returned with the message that Xubuntu 6.10 was available as a dist upgrade. I selected to run the dist upgrade. I made sure nothing else was running to avoid problems.

The upgrade took awhile, and I clicked to open the terminal window to make sure everything seemed to update smoothly. All seemed fine and the upgrade finished... The update window closed and it looked as though the install procedure attempted to reboot the pc (vm). It hung there with only the desktop background for about 30 minutes before I got tired of waiting and reset the vm. It then rebooted and seemed to go into grub and load the new kernel fine. The lovely new animated boot splash fired up and the progress bar got to the last led segment and just hung there. It will not go past this point. Even trying f2 to get into verbose mode does nothing. This new boot splash is nice except when something has gone wrong, you cannot see what the problem is...

It does not seem to freeze or hang the vmware player, as the activity icons are still animated, but it will just sit there at the boot splash and never get to the desktop or login prompt.

Does anyone have an idea what could be wrong?

:confused:

---

### Post by jensalpers on 2006-11-16
looks like the update process did not complete - went into recovery console and invoked apt-get update which did not worked, hint: dpkg --configure -a

i did so and it worked after reboot

so try this:
boot into recovery console
dpkg --configure -a
reboot

---

### Post by mungewell on 2006-11-16
Hi,
I had exactly the same problems (twice!) as the original poster. The upgrade process froze with just X background showing both via update-manager and manual changing sources.list & apt-get dist-upgrade.

Booted into rescue terminal, using 'dpkg --configure -a' (which processed more packages) and rebooted, but still doesn't work.

Booting into rescue terminal and running 'apt-get dist-upgrade' also continued by install more packages... still doesn't work.

Image currently boots into splash screen, progress bar shows activity until the last section when I get screen corruption (coloured dotted line across screen) and the system locks up.

Xubuntu 6.06 image was from vmware's website.

Any other suggestions?
Simon.

---

### Post by Qrilka on 2006-11-26
Did anybody solve this problem?
The only way  (not very pleasant one) i see at this moment is to reinstalll everything from the scratch :(

---

