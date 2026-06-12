---
title: "Latest update batch - Hibernation stopped working again"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Vietman on 2008-10-09
What gives?

Is there any way to reliably keep the hibernation function in Ubuntu Linux?

---

### Post by Vietman on 2008-10-09
Managed to get it working again. This helped:

sudo gedit /etc/default/acpi-support

* Change the value for HIBERNATE_MODE as
HIBERNATE_MODE=platform

* Save the file and retry hibernating.

And all the stuff from here:

[http://blog.vaxius.net/?p=43](http://blog.vaxius.net/?p=43)

Getting Suspend Working with nVidia in Ubuntu 8.04 (Hardy Heron)

I had just installed Ubuntu’s newest release on my HP laptop, and all was well until I went to suspend. It’s not to surprising that it didn’t resume, as Ubuntu has a long history of suspend and hibernate problems as configured out of the box. To be fair, about 99.9% of the time the fault lies with the driver; however, it’s still incredibly annoying. The following chronicles the journey to fully functioning suspend.

Note: Read the article on installing the nVidia driver in Ubuntu if you don’t already have it installed.
The journey begins!

The first step I took was to make the usual changes in acpi-support that has historically worked in the past. Change /etc/default/acpi-support to resemble the following using your favorite editor (I’ll show gedit for those new to Linux).

$ sudo gedit /etc/default/acpi-support

SAVE_VBE_STATE=false
POST_VIDEO=false
# It may not be necessary to set USE_DPMS to false, but it doesn't hurt.
USE_DPMS=false
It still doesn’t work?!

Having made those changes, I restarted to find that suspend still didn’t work. Further digging revealed that I needed to explicitly use the AGP module (evidently it handles PCI Express as well) by adding a driver option.

$ sudo gedit /etc/X11/xorg.conf

Insert the following line under the Device section:

Option "NvAGP" "1"

Note: You may also have to add agpgart to your blacklist to stop it from loading. Credit goes to buckminster.
$ sudo gedit /etc/modprobe.d/blacklist

Add the following line and save:
agpgart
It works! Well, it kind of works…

Another restart later, suspend worked, but only once until the next reboot. Further searching revealed another solution involving putting a script in /etc/acpi/suspend.d/. I’m thinking that there’s a mystery script somewhere that setting the settings we changed in acpi-support back to the old values. Here’s how I created the script (use a different two-digit number for you script if there’s one with a lower number, as we want this to be the first thing to run).

$ sudo gedit /etc/acpi/suspend.d/05-nvidia-override-post.sh

Make the script mirror the following:


#!/bin/sh

SAVE_VBE_STATE=false
POST_VIDEO=false
# Once again, I’m not sure if setting USE_DPMS to false is necessary.
USE_DPMS=false
Fully working suspend is mine (and now yours)!

Now the first action taken during suspend is to change all those settings set in acpi-support back to what we need them to be. Suspend now works no matter how many times you do it!

---

