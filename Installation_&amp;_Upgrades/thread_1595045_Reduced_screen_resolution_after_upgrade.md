---
title: "Reduced screen resolution after upgrade"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by jonathanhayward on 2010-10-12
I have a 1920x1200 monitor that was displaying correctly under 10.4, and after the upgrade to 10.10 it is displaying at 1280 x 720 (the highest resolution it has), and does not list 1920x1200.

How can I ask 10.10 to display at 1920x1200?

---

### Post by tommcd on 2010-10-12
What video card do you have? And do you have the proper driver installed?
If you have a nvidia or ati card you may need to update the driver for it.
Otherwise, you can try to use **xrandr** to add undetected screen resolutions:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by jonathanhayward on 2010-10-13
I have a VMware virtual machine on a Mac Mini.

I reinstalled VMware tools after the upgrade.

---

### Post by jonathanhayward on 2010-10-14
By the way, there is a related thread at [http://communities.vmware.com/message/1626819#1626819]("http://communities.vmware.com/message/1626819#1626819"). It provides a fix which is claimed to work under Debian; I haven't yet gotten it to work under Maverick (I get an error message about an unsupported X resolution).

---

### Post by tommcd on 2010-10-15
> **jonathanhayward said:**
> I have a VMware virtual machine on a Mac Mini.

So what video card is in the Mac Mini?
Have you tried using the xrandr utility?
I have no experience running Ubuntu in VMware.

---

### Post by bobbabai on 2010-11-22
Here's what fixes auto-adjust resolution for me.  What a pain.  This sure ain't Windows or MacOS.  I have re-learn this at least twice a year as I go through Ubuntu upgrades. 

1. Install vmware-tools following VMware instructions

2. sudo update-initramfs -u

3. Log out and log back in

Bob

---

### Post by jonathanhayward on 2010-12-27
Thank you; those didn't work for me this time.

How can I probe the video card to display relevant information?

---

### Post by 1492 on 2010-12-27
I had the same problem upgrading from 10.04 to 10.10

This worked for me:

> **sikander3786 said:**
> Try reconfiguring the graphics.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```It if says file not found, ignore and  proceed to the next one.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```Reboot.

---

### Post by jonathanhayward on 2010-12-27
I just installed the new 3.1.2 VMware update and tools.

When it boots there is a GRUB complaint about a syntax error; could that be connected to it?

---

