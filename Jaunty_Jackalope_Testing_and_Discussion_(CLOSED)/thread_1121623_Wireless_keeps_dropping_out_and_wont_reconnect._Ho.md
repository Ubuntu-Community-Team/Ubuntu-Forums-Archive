---
title: "Wireless keeps dropping out and wont reconnect. How do I kick it."
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-04-10
Am using wicd. Even putting laptop next to router doesn't do it, have to restart pc.

How can I kickstart it.

---

### Post by philinux on 2009-04-10
Update:-

Suspend kills off wireless too. Only solution reboot.

Unless there's a terminal command to kickstart it?

---

### Post by taavikko on 2009-04-10
There's plenty of tools, such as "ifup" (see: man ifup)
That should kick the interface back up, unless it by some weird chance is improperly managed by kernel (bad modules)

---

### Post by dro0g on 2009-04-10
> **philinux said:**
> Update:-

Suspend kills off wireless too. Only solution reboot.

Unless there's a terminal command to kickstart it?

I'm using NetworkManager and a Broadcom 4312 card. I've found that after suspend I have to do a 'sudo modprobe -r wl;sudo modprobe wl' to get the wireless to come back up. 

I've created a file called broadcom in /etc/pm/config.d with the line SUSPEND_MODULES=wl in it, I will test it in just a bit.

---

### Post by Reiger on 2009-04-10
> **philinux said:**
> Am using wicd. Even putting laptop next to router doesn't do it, have to restart pc.

How can I kickstart it.


Did you try:

First disconnect using WICD, then:

```

sudo /etc/init.d/networking restart

```
Or forcing it using:
```

sudo /etc/init.d/networking force-reload

```

Or more manually:

```

sudo ifconfig [interface] down
sudo modprobe -r [driver]
sudo modprobe [driver]
sudo ifconfig [interface] up

```

And finally, reconnect using wicd?

(If not try purging as many wpa_supplicant.conf files in /etc first, then that code.)

---

### Post by philinux on 2009-04-11
When the wireless drops out wicd shows "No wireless networks found".

Clicking refresh doesn't do anything. It's as though there is no signal even if laptop sat next to router.

---

### Post by smbm on 2009-04-11
Have you tried unloading and reloading the module for your card?

For me it is:

```
sudo modprobe -r iwl3945 && modprobe iwl3945
```

Obviously replace iwl3945 with whatever drivers you need for your card though.

That has never failed to get wireless back working for me when things have gone bad.

---

### Post by philinux on 2009-04-12
Ok I'll try that but lsmod does not show my iw driver.

---

### Post by Reiger on 2009-04-12
And you don't happen to use ndiswrapper ? ;)

I think you may have misread my post earlier: first disconnect using WICD if it still thinks you are connected; next take-your-pick of the command sequences I posted; finally re-connect using WICD. (So disconnect/reconnect aren't separate options, they are part of 'em.)

---

### Post by jfernyhough on 2009-04-12
Huh... I thought my wireless problems were due to my Intel 5100... I leave it overnight to download stuff and I wake up to find it died about 5 minutes after I go to sleep. It repeatedly breaks if I close the laptop lid - nm-applet says there is a connection but there is no network activity. A reconnect to the network fixes it, but it's bloody annoying.

I'm wondering if this is a kernel-based issue. Might have to try moving from .29 now...

---

### Post by Reiger on 2009-04-12
This has more likely something to do with your power savings settings: closing a laptop lid usually is a sign for OS to hibernate/sleep [obviously that kills your connections].

Easiest thing to do, is probably to just leave the machine running; only turn off the screen.

---

### Post by jfernyhough on 2009-04-12
Even if I leave the machine well enough alone the connection still dies. As for power settings, I have mine set so 'When laptop lid closed: "Blank screen" '. It's never been a problem until fairly recently, actually probably since 29-final or 29.1. As I say, I'm downloading 30-rc1 now and I'll test it later.

I've also installed a second wlan card (Dell BCM4311, works OOTB for Mac OSx86 :wink:) and will see if that one does the same thing. (Yes, that's right, the Acer 5930G has a spare Mini-PCIE slot. :D)

---

