---
title: "Gutsy LiveCD &amp; bcm43xx error: how can I disabled the loading of the driver?"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by Shiroku on 2007-12-30
I'd like to install Ubuntu/Kubuntu on a pc's friend, but at the boot of LiveCD of Gutsy Gibbon I read the following message: 
 
```

bcm43xx: Error: microcode "bmc43xx_microcode5.fw" not available or load failed

```

and the operating system doesn't starts.
After a few searches, I've seen that to fix this problem I need to install other drivers, and to put the previous one (default) in blacklist .
But the operating system isn't installed yet, so I can't change the driver.

How can I disabled the loading of the driver at the boot time? (some orguments to pass to kernel?)

Thank's!

---

### Post by Seisen on 2007-12-30
This might help you fix your problem

[https://answers.launchpad.net/ubuntu/+question/20600]("https://answers.launchpad.net/ubuntu/+question/20600")

---

### Post by Shiroku on 2007-12-30
Thank's for the link, but the OS isn't installed yet, so I can't install the new drivers....

I'm looking for a way to disable the loading of wireless drivers at the boot time, so the system can starts (and then I can use the how-to in the link above).

In fact the message:
> 
bcm43xx: Error: microcode "bmc43xx_microcode5.fw" not available or load failed

is printed continually (like as a loop..)

---

### Post by pndragon on 2007-12-30
This is a common sight for HP and Compaq laptops... try this link and see if any of this info can help you... [http://ubuntuforums.org/showthread.php?t=575750]("http://ubuntuforums.org/showthread.php?t=575750")

---

### Post by Shiroku on 2007-12-30
> **pndragon said:**
> This is a common sight for HP and Compaq laptops... try this link and see if any of this info can help you... [http://ubuntuforums.org/showthread.php?t=575750]("http://ubuntuforums.org/showthread.php?t=575750")

The problem is the same: the OS isn't installed yet, and I can't use a shell to change the drivers...

There is a way to change the booting arguments? so I can disable the wireless when booting from LiveCD...

---

### Post by pndragon on 2007-12-31
Did you try "Start Ubuntu in Safe Graphics Mode" ?

---

### Post by pndragon on 2007-12-31
Let's start again...

First...```
bcm43xx: Error: microcode "bmc43xx_microcode5.fw" not available or load failed
```means that firmware for your wireless card is not immediately available and a little work will be involved.**[COLOR="Red"] Just a little!!!![/COLOR]**

You will need a wired connection.

Load the LiveCD and restart. When you see the Ubuntu boot menu choose the second option, "Start in Safe Graphics Mode."  You will still see that error message a couple of times but the LiveCD will load with 800x600 resolution.

Go to Kmenu>System Settings>Monitor & Display. Click the Hardware tab. Choose a generic monitor 1024x768. This probably does not match your resolution but it should be good enough for the install. To see the changes, you will need to restart the xserver. To do this, right-click anywhere on the desktop, choose "Log Out" from the context menu then Log Out from choice that appear center screen. You will now go a log-in screen. Choose "Restart X Server" from the drop-down list on the lower right and Log in. Put in "ubuntu" as the user name. Leave the password empty. Log-in again. You should now see the new resolution and be able to start your install with no problems.

Gutsy is supposed to support the Broadcom card. But so far support is somewhat unstable. I would try the method at the link I gave above.

---

### Post by Shiroku on 2008-01-01
Thank's for your reply!
I will try "Start Ubuntu in Safe Graphics Mode" when my friend came back from holiday.

Thank's!

---

### Post by Shiroku on 2008-01-17
> Did you try "Start Ubuntu in Safe Graphics Mode" ?
Yes, I tried and it works!


During the loading of LiveCd, I've found this error: 
```

PCI: Bios bug #81 found

```

What does it mean?

When I try to open the windows partition (from LiveCd), this error occurs:
```

hal-storage-fixed-mount-all-options refused uid 999

```

Does it bother me when I will install Kubuntu?

---

