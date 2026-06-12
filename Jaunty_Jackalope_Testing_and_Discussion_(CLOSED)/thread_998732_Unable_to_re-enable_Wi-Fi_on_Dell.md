---
title: "Unable to re-enable Wi-Fi on Dell"
date: 2008-12-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by phenest on 2008-12-01
I have fn+F2 set to disable/enable wireless only on my Dell laptop. I can disable the wireless ok, but it will not re-enable, even after a restart. The only way I could get it working again was to boot up Intrepid, then reboot back into Jaunty (both Intrepid and Jaunty share /home).

---

### Post by priegog on 2008-12-01
Oh, I'm not updated with my mad-wifi-console-skillz (all my wifi cards work out of the box now), but I know it is certainly possible... possibly using the modprobe command. I'll just let some other member help you out with this one.

---

### Post by adult swim on 2008-12-01
if your device is wlan0, try sudo ifconfig wlan0 up

---

### Post by RAOF on 2008-12-01
> **phenest said:**
> ... but it will not re-enable, even after a restart. ...

Is that a power-off restart?  Does it work if you shutdown, un-plug it, take out the battery, and then start it up again?  Does it still appear in lspci?

It sounds like the driver in Jaunty's kernel is writing some 'really, really disable' value to the card, but is unable to start it up again.  If you use the Intrepid kernel in Jaunty, does it successfully bring the card back up?  If you use the Jaunty kernel in Intrepid, does it fail to bring the card back up?  What's the first kernel version that does this, etc.

---

### Post by phenest on 2008-12-02
If I shutdown, unplug, and remove the battery then power up again, the WiFi will come back on. A normal shutdown or reboot doesn't work.

As for trying with different kernels in different Ubuntu versions, I don't feel confident about switching kernels around. All I can say is this didn't happen in Intrepid (or Hardy), but does in Jaunty kernel 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64 GNU/Linux.

---

### Post by RAOF on 2008-12-02
Try with the 2.6.28 kernel.  If that doesn't work, file a bug, following the kernel team's [guidelines](https://wiki.ubuntu.com/KernelTeamBugPolicies).  In particular, dmesg and lspic before and after hitting the disable button on a kernel that works and doesn't is likely to be interesting.

---

### Post by Starks on 2008-12-02
Sometimes just reinstalling your current kernel works.

---

### Post by nightfrost on 2008-12-13
phenest, did you file a bug report about this?

Can you look in /sys/class/net/[your wlan interface]/device/rfkill/rfkill0, and see if you have a file named "state" there. If you do, could you post the value it has *before* you disable wireless, *after* you disable wireless, and *after* you try to re-enable wireless?

I'm having a similar problem on my Asus with Jaunty's version of hal + networkmanager. Somehow the rfkill state is set to 2, which, AFAIK, means wlan is off by means of a hardware switch, and then nothing can get it back from that state. The hal guys claim it's not a hal issue, so I'm trying to figure out what it might be...

---

### Post by knix on 2008-12-14
try modprobing out your kernel driver, then putting it back in.
Are you using wl or ndiswrapper? or do you have an intel wireless card?

---

### Post by Peter09 on 2008-12-15
I have a similar problem on my Satellite Pro Laptop. The only way I have found of re-enabling the wireless card again is to go into the System->Admin->Hardware menu and disable my Atheros driver then re-enable it again. 

It connects straight away after that.

Is this the same problem?

---

### Post by phenest on 2008-12-15
I have an Intel card. I haven't thought of this as being major, and only as something I noticed. I disabled the switch in the BIOS to stop me accidentally turning it off. I haven't really looked into it any further.

---

