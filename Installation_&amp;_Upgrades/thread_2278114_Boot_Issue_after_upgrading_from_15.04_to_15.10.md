---
title: "Boot Issue after upgrading from 15.04 to 15.10"
date: 2015-05-14
forum: Installation &amp; Upgrades
---

### Post by michael284 on 2015-05-14
Hi all,

I have a HP notebook running Ubuntu, and today I ran the software update utility to upgrade from 15.04 to 15.10.
The upgrade appeared to go through fine, however after a reboot I experienced boot issues.

I have Ubuntu full disc encryption enabled, after being prompted at the purple Ubuntu screen to enter my passphrase I was taken to a command line screen for a few seconds and then immediately to a black screen.
On this black screen I can't seem to do anything, other than Ctrl+Alt+Del which brings up a purple ubuntu screen and reboots.

Any ideas here guys how I can get back to booting normally and access my OS? Just to recap, I boot and am prompted for my encryption password for disk - after that all I get it a black screen.

Thanks in advance.

EDIT: Upgrade was from 14.04 to 14.10 - apologies.

---

### Post by ajgreeny on 2015-05-14
I note this is your first post to the forum, so I assume you might be a new user of Ubuntu and possibly Linux, so my first question has to be why, oh why did you choose to upgrade to 15.10 which is almost bound to have many and varied problems as its development gets started?

15.04 has only been released about 3 weeks ago, so there really is no point in moving to 15.10 unless you want to help in its development, and I am afraid there is no way to go back to the previous version, 15.04 short of reinstalling from scratch.

In your situation, if you really are a new Linux/Ubuntu user yu would probably have done better to stick with the 14.04 version which is supported for another 4 years; 15.04 has only 8 months support now, and 15.10 is not yet released, nor will it be until October.

---

### Post by michael284 on 2015-05-14
Hi there,

Thanks for your response. 
I understand where you're coming from - it's my own fault I know. I just upgraded due to curiosity I suppose, and wanting to have the latest version, my bad.

Would you have any suggestions however?

Thanks,

---

### Post by coffeecat on 2015-05-14
> **michael284 said:**
> I have a HP notebook running Ubuntu, and today I ran the software update utility to upgrade from 15.04 to 15.10.

Are you sure? To upgrade from the current 15.04 to the hardly-started-yet 15.10 you would have to run a terminal command, not the software updater. Did you mean upgrade from 14.04 to 14.10?

---

### Post by michael284 on 2015-05-14
You could be quite right there, I ticked the option in Software Updater to show all new versions of Ubuntu and I updated it that way.

---

### Post by dino99 on 2015-05-14
from a terminal, please run >  lsb_release -a and post the output. Also tell us which graphic/chipset is used and with which graphic driver
that issue may let you boot from the "recovery mode" and then do the needed stuff

---

### Post by coffeecat on 2015-05-14
> **dino99 said:**
> from a terminal, please run ```
lsb_release -a 
``` and post the output. Also tell us which graphic/chipset is used and with which graphic driver
that issue may let you boot from the "recovery mode" and then do the needed stuff

The OP wrote:

> **michael284 said:**
> after being prompted at the purple Ubuntu screen to enter my passphrase I was taken to a command line screen for a few seconds and then immediately to a black screen.
On this black screen I can't seem to do anything, other than Ctrl+Alt+Del which brings up a purple ubuntu screen and reboots.

Wouldn't that make running lsb-release challenging?

---

### Post by grahammechanical on 2015-05-14
At the boot menu do you see Advanced Options for Ubuntu? If so select Advanced Options and the select the recovery option.

At the recovery menu select Resume. That may load to a desktop using an open source video driver called llvmpipe. You will need as usual to unlock the disk encryption.

If you get to a working desktop then go to System Settings>Software & Updates>Additional Drivers tab. Allow the utility to find video drivers and then experiment with a different video driver. If all you get is the wallpaper, then right click the wallpaper and select Change Desktop Background. That will open System Settings.

Regards.

---

### Post by michael284 on 2015-05-14
Hi all,

Thanks for your response.

I do get the GRUB options, and I can boot through into Recovery Mode. At the prompt I unlocked the disk, and selected the option to resume booting.
After that I was prompted to enter my username and password at the command line. Once I did this, I am still at a command-prompt screen with no GUI.

I entered the command lab_release-a and I am running Ubuntu 14.10

Is there a command I can enter to continue pass this and start the normal GUI?

Thanks,

---

