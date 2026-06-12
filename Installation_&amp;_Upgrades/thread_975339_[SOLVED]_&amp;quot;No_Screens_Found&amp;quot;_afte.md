---
title: "[SOLVED] &amp;quot;No Screens Found&amp;quot; after Upgrade"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by Otustelija on 2008-11-08
After upgrading my x86-64 Ubuntu installation from 8.04 to 8.10 through the update manager I am unable to run X. Booting to Ubuntu I arrive at the command line login. Running startx takes a while and terminates with "no screens found".

Following advice on other threads and bug reports I have uninstalled VirtualBox and disabled the fglrx kernel module, but no improvement. I have tried deleting xorg.conf altogether, using the default one and the failsafe one - none work.

I also tried burning a livecd, but get similar errors when trying to boot to a live session. I've tried the x86 8.10 versions of Ubuntu and Xubuntu live cds - neither works. With 8.04 live cds I was able to boot normally. I haven't yet tried a clean install, precisely because the live cds don't work.

My computer is a Fujitsu Siemens Scaleo P desktop with ATI Radeon HD 3450 and a screen with a 1680x1050 native resolution.

Any ideas on what I should try?

Please let me know if any logs could help.

---

### Post by mik9dt on 2008-11-09
I had the same issue with my daughters pc.

It had 2 nvidia PX6600 GT TDH video cards installed although only one was in use with 8.04.

On update to 8.10 I got the same result as you... "no screens found" and a command prompt.

startx did not work.

I physically removed the unused video card and now all is well.

The updated video software could not decide which video card to use and so said that it could not find any, although it was telling me this using the attached screen!

---

### Post by Otustelija on 2008-11-09
> **mik9dt said:**
> I had the same issue with my daughters pc.

[...]

I physically removed the unused video card and now all is well.

The updated video software could not decide which video card to use and so said that it could not find any, although it was telling me this using the attached screen!

It might be something similar with my computer, since I have both an IGP (Radeon 3200) and a dedicated graphics card (Radeon 3450). However, I cannot remove one, as my screen only has a VGA connector and my IGP does not have one. So, your solution won't fix it for me... :confused:

---

### Post by Otustelija on 2008-11-09
A lot of people are [having trouble]("http://ubuntuforums.org/showthread.php?t=965237") with ATI drivers, but I think my issue is separate, because neither the low graphics mode nor a failsafe vesa xorg.conf get me to a GUI system.

---

### Post by yasar on 2008-11-10
Same issue here too.. just upgraded from 8.04 to 8.10.. 

(EE) Failed to load module "fglrx" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found
giving up.

---

### Post by Otustelija on 2008-11-12
I finally found a way to solve the problem. The solution was to boot into a live cd system and run sudo Xorg -configure. This probed for hardware and created a new xorg.conf from what it found. (For some reason it wouldn't run from the installed system.)

That new configuration file didn't work as it was, but it showed the problem: as mik9dt suggested, the problem was that I have two video cards. Ubuntu tried to use both as screens, though only one had a monitor attached.

After commenting out one of the screens from the layout section of the file I managed to start X.

---

### Post by terranz on 2009-02-10
I posted a thread with the same problem and the same hardware 3200 and 3450 but got no replies.  I'll try it when I'm home from work.

---

