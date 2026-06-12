---
title: "Lost keyboard and mouse during upgrade 10.04 -&gt; 10.10"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by jtullos on 2010-10-20
I am (was?) currently running Kubuntu 10.04 AMD64.  I started the upgrade process as I was leaving work one day.  Came back, attempted to check on it, and couldn't.  The screensaver was up and the computer was locked, with no response.  I am able to connect via SSH, and have killed the screensaver to see that I am in the middle of the upgrade (currently, I have a dialog to replace a configuration file or keep my custom one).

I am using a USB keyboard and mouse, connect through a KVM switch.  I've tried power cycling the KVM switch, disconnecting and reconnecting the keyboard and mouse, and even using a different USB port.  Nothing is getting the system to respond to them.  I'm very leery of rebooting in the middle of an upgrade, is there anything I can run to get the USB devices to be detected?  Or redirect the current desktop to a remote session?  Or just move the upgrade to a remote session, command line or graphical?

Thank you for helping.

---

### Post by lemming465 on 2010-10-21
*sudo lsusb -v* should tell you what USB devices are being seen.  *sudo /etc/init.d/dbus restart* might give device recognition a kick.  If none of those help, I think you are stuck with the reboot & pray option.

---

### Post by jtullos on 2010-10-22
Interesting.  It is detecting the mouse (according to lsusb), but not responding to any input from it.  I tried a keyboard and the same thing is happening.

I'm going to wait a bit longer before I reboot it, it's not critical just yet, but I will need it back up soon.  Thanks for your help though.  And at least I learned something new.

---

### Post by johnerskine2010 on 2010-11-02
I've had the same problem. Keyboard completely locked, and I can't even type in a password.

---

### Post by danielblw on 2010-11-07
I have the same problem, does anyone know how to fix it? thanks so much.

---

### Post by Surfrock66 on 2010-11-14
This is happening to me as well; I was still using 10.04 and some update happened yesterday, I started experiencing strange keyboard/mouse behavior, so I tried to move to 10.10 and still have the problem.

It's weird, when I boot I can use the KB/Mouse fine, then I'll be in one application, and suddenly the KB works but the mouse doesn't, or vice versa.  I'll notice if I lose the mouse, it'll still work in docky but nowhere else, or if I lose the keyboard it'll work in chrome but nowhere else; like the input for 1 device gets stuck in a program, with no way to clear it.

I can't discern a clear pattern, but it developed yesterday to an update for 10.04, and is persisting in 10.10.

---

### Post by indigene on 2011-02-02
Same problem here. 

I got this usual alert for updates while using 10.04. Updates went on for a long time.  No issues till I finished work last night. 

Today morning, obviously the first reboot since the updates were enforced, keyboard (Microsoft Wired RT2300) is not being recognized at password entry screen. Keyboard works in BIOS.

Also, now I get the Kubuntu 10.10 screen during startup.

The issue with the mouse (Microsoft Basic Optical v2.0) is that its not recognized the first time but funnily, if you pull out the mouse USB and put it back, it works!

This is a pattern.

Luckily I have an older desktop with Kubuntu Lynx - the same keyboard and mouse work fine there.

Is this a new driver (for these Microsoft devices) compatibility issue peculiar to 10.10?

---

