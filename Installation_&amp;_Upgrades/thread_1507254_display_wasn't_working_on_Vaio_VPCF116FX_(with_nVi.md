---
title: "display wasn't working on Vaio VPCF116FX (with nVidia) after installing Lucid"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by plentyTypos on 2010-06-11
After installing Lucid 64 bit on a Vaio VPCF116FX the display was wrong; this is for those who have an nVidia graphics card, or at least specifically the GeForce GT 330M:

The symptom was that no matter what System->Preferences->Monitors settings I tried, the "screen" (in the virtual sense) was larger than the physical screen. Items at the right or bottom of the "screen" were off the right edge or bottom of the physical screen. There are plenty of posts in various forums about this, and I think it's a problem with other computers than just the Vaio, but in any case it seems to be common on a Vaio.

Many approaches to solving this are also posted actually, but in my opinion the following is the simplest. First be sure that you have a working internet connection (that you can actually access the internet; forgive me if this seems too obvious but it did at first happen to me that I forgot to enter the ISP settings). Then go to the System->Administration->Hardware Drivers menu. You should be presented with the chance to "activate" the proprietary nVidia driver(s). Do this. Then in Terminal (Applications->Accessories->Terminal) enter this command:

sudo nvidia-xconfig

After you activate the nVidia drivers the System->Administration->NVIDIA X Server Settings menu item should warn you that you need to run the "nvidia-xconfig" command by the way, if you happen to check that (but you don't need to).

Among other things that command generates a file called "/etc/X11/xorg.conf", that is, the file is called "xorg.conf" and you'll find it inside of "/etc/X11/". You next need to edit that *as root*; for example you can open it with this command in Terminal:

sudo gedit /etc/X11/xorg.conf

Scroll down and find the section called "Device". Add the following lines to that section (I put them at the end of the section right before "EndSection"):

Option "ConnectedMonitor" "DFP-0"
Option "CustomEDID" "DFP-0:/proc/acpi/video/NGFX/LCD/EDID"

Then restart the computer and you should have a working display.

This solution depends on there being an "EDID" file located at "/proc/acpi/video/NGFX/LCD/EDID", and though there are various posts describing how to extract and export one from Windows, at least on my system there was in fact one already at that location so none of that was necessary. (Edit: I've since learned---that is, I think the following is true---that /proc is a kind of virtual file system; it's actually a way to access data that the kernel offers. If it so happens that you can't use the EDID "file" that's "there" then you can try extracting/exporting one from Windows, if you have access to Windows on your computer.

Hopefully this helps somebody.

---

