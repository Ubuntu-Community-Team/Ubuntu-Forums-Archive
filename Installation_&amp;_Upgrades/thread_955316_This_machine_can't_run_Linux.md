---
title: "This machine can't run Linux?"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by Ole Juul on 2008-10-22
Is it possible that a (Biostar?) K8VGA-M board with an AMD Semperon 3300+ and Award BIOS cannot run Linux?

The machine in question has been running MS-XP-sp3 without problems. I have tried various live CD distributions in the past but none have worked. Now I **need** to install Linux on this machine and would like Kubuntu 8.04.1 but it hangs on "Starting Bluetooth services", even when all USB peripherals are unplugged. The same happens with 6.06.1 except it goes one line further which says "hcid sdpd". 6.06.1 also gives a fail on "Loading hardware drivers".

I have installed Kubuntu on many machines but this one has me stumped. :confused: The owner has been using MSWindows for years and was really looking forward to switching to Linux. :) What should I do?

---

### Post by sethvath on 2008-10-22
Reboot and try sudo /etc/init.d/sdpd stop 

Clt+Alt+F1 to get to a terminal if you experience it hanging again. Clt+Alt+F7 to revert back

To prevent the bluestooth stack from loading after boot, uncheck in the sessions tab.

---

### Post by Ole Juul on 2008-10-22
Thankyou for your answer sethvath. I cannot reboot and am still trying to get the installer to go somewhere. It just hangs. Clt+Alt+F1 or F7 does nothing. I can however get to a terminal in the usual way but there is no sdpd in /etc/init.d, so I can't run or stop it.

Here is what I did which got the system installed. I used the alternate version (Debian installer) which doesn't complain. When I boot the system it hangs at the same place, however I can then go to a terminal and type startx and then uncheck Bluetooth in the sessions tab. So, you were right about that. :) Thanks! Upon reboot it then works correctly, although there is still no sdpd to be found.

I will now have to figure out how to install KDE and perhaps Bluetooth if I need it later.

BTW: With the alternate installer I saw a message going by (fast!) which mentioned a USB problem at address 2 and error 71. I don't know what any of that means yet, but it looks like a clue.

---

### Post by sethvath on 2008-10-22
Firstly, is the bluetooth device in question a BT dongle or inbuilt like a laptop's?

Error-71 means a failure to read the configuration files. 

Try "lsmod | grep usb" without any usb device plugged in. Then once more with your dongle plugged in.

---

### Post by Ole Juul on 2008-10-22
I now have a working system and it looks like I will be able to move forward from here. The quirk here is that there is NO Bluetooth device. The problem was also the same (install hanging with "Starting Bluetooth") with both versions 6.06 and 8.04 and also with ALL USB devices unplugged. There is something with the hardware which is unusual. As I mentioned earlier, this system will not run all the live CDs that I've tried.

Cheers,
         Ole

---

### Post by cariboo on 2008-10-23
I found a solution to your problem here:

[http://ubuntuforums.org/archive/index.php/t-226939.html](http://ubuntuforums.org/archive/index.php/t-226939.html)

Once you see the Starting Bluetooth press Ctrl-c this should stop Bluetooth from loading and continue on loading to the desktop.

Jim

---

### Post by Ole Juul on 2008-10-23
"... press Ctrl-c this should stop Bluetooth."

That was the first thing that I tried and it has no effect. The regular installer is hooped on this system. It will not allow an install without hanging at the hardware discovery stage. Like I said before, no other Linux distro has ever been able to run on this system from a live CD. I feel lucky now. :) The person who has been running MS-XP on it is happy too as she can access her old files just fine. Now we just need to install KDE, get the scanner to work, and figure out why the Gimp hangs.

I think this is a Linux hardware compatibility problem with some USB related chip. Note that XP runs like a charm on it and Linux can't install. I have not encountered a computer giving me problems like this with a Linux install before.

However, I am over the first hump and now that I have a basic system installed (via the Debian installer), I am working on getting devices to work. The printer is fine, but the scanner being a USB device, does not work. The USB problem (whatever it is) will not allow SANE to load.

UPDATE:
  I don't have a solution yet, but I'm betting that the problem is with the VIA VT8237 chip on the south bridge. I've been doing some more looking around and found a lot of related bug reports, and this thread on ubuntuforums:  "Via USB and ehci_hcd bug" 
  [http://ubuntuforums.org/showthread.php?t=89266](http://ubuntuforums.org/showthread.php?t=89266)

---

