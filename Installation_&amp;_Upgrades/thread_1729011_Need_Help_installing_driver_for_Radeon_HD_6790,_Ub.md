---
title: "Need Help installing driver for Radeon HD 6790, Ubuntu 10.10"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by andyman420 on 2011-04-14
Hello to all.

Just wondering if there is anybody here who has any experience installing the drivers for an ATI Radeon HD 6790 GPU under Maverick.

I've tried downloading the driver package from the ATI website (apparently this is proprietary driver 8.831.2), and running the installer .sh. file.

With this file, I choose everything to install automatically, and afterwords I am given two choices under System > Preferences, they are "ATI Catalyst Control Center" and "ATI Catalyst Control Center (Administrative)"

Here's the problem, no matter which one I choose, I am immediately given the following error message

"There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig."

When I try to configure by entering the command "aticonfig --initial" in the terminal, I am told that "no supported graphics adapters detected."

I'm nearly at my wit's end, and just wondered if anyone here can shine some knowledge my way and help me with my issues.

Much Appreciated,

-Andy

---

### Post by tgckpg on 2011-04-20
Same problem here~

---

### Post by Tosa on 2011-04-22
I had the same problem a few months ago; the driver was installed but Control center said it wasn't...

I've checked /var/Xorg.log and found errors with loading the fglrx kernel module. The moduel wasn't installed and after I installed it through synaptic everything worked fine.

I suggest you have a look at Xorg.log for error(s) that are preventig the driver from working.

---

### Post by Jechem on 2011-04-22
This may help:
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Aticonfig_not_found_after_installation_.26_.22module_does_not_exist.22_after_boot](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Aticonfig_not_found_after_installation_.26_.22module_does_not_exist.22_after_boot)

---

### Post by chkneater on 2011-04-26
I just finished resolving the same issues you're having on 10.04 with Radeon.  I installed the drivers from the website just like you did, which was the right decision.

Try: sudo apt-get install aticonfig

I had to use this to do two things: " aticonfig --initial " which sets up the xorg.conf file and then
 " aticonfig --initial --input=/etc/X11/xorg.conf" in the terminal.  

The second command sets up the fglrx modules, WHICH btw make sure you have all your updates installed before doing this.  This should work for anyone with a newer ATI card and AMD system, which I don't understand why Ubuntu consistently neglects ATI cards over Nvidia for at least six months.  I guess ATI is more of a pain about proprietary stuff, even though they provide the drivers but no instruction on how to install since it's distropendent.

Hope this helps, if so spread the news!

---

### Post by dimiroo on 2011-06-19
hi, i am new to this forum. This is the only thread i found on ATI raden 6790 on ubuntu 10.04
i installed everything as you said with latest driver(6/15/2011)

the only problem that i cannot solve is the openGL 

on glxinfo |grep direct, i get:

[HTML] direct rendering: No (LIBGL_ALWAYS_INDIRECT set)[/HTML]i was suggested a dirty tweak, to unset it , but does not work for me..

on fglrx i get 

[HTML]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6700 Series   
OpenGL version string: 2.1 (4.1.10834 Compatibility Profile Context)[/HTML]which seems rigth according to wiki page (right? :()

can you help me through this one? if i install an older driver would it make any difference? 
does your direct rendering works fine?

---

