---
title: "After upgrade, network-manager is in broken state"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by georgz on 2007-12-05
After today's upgrade with apt-get upgrade there is a problem with network-manager on my system.

The upgrade installed the new version of network-manager, but configuration fails:

-----
Richte network-manager ein (0.6.5-0ubuntu16.7.10.0) ...
 * Reloading system message bus config...
   ...done.
 * Restarting network connection manager NetworkManager
dpkg: Fehler beim Bearbeiten von network-manager (--configure):
 Unterprozess post-installation script gab den Fehlerwert 2 zurück
-----

Sorry it's in german but it says that the post-installation sub-process gave error 2... What it does is that it tries to restart network-manager service and this hangs... When I try to start this process manually myself, it hangs at the stage of restarting network-manager.

Installing other packages is broken due to this, as it always tries to do the missing configuration of network-manager. 

Any suggestions what to do? At least how to debug further?

I'm using 7.10 x86.

Thanks,
Georg

---

### Post by georgz on 2007-12-05
For those interested, any aptitude/synaptic etc asks me now to dpkg reconfigure:

$ sudo dpkg --configure -a
Richte network-manager ein (0.6.5-0ubuntu16.7.10.0) ...
 * Reloading system message bus config...                                                                                                                                                               [ OK ] 
 * Restarting network connection manager NetworkManager   


And there it hangs forever. So maybe the question is rather NetworkManager related, I just can't find out what the problem is. At this point I don't have network of course, which makes everything break... Need to cold restart.

---

### Post by georgz on 2007-12-06
For anyone who is interested:

Needed to remove the bcm43xx kernel module
# rmmod bcm43xx

Then it worked.

---

### Post by TrioTorus on 2007-12-06
I've got the exact same problem. On 7.10 amd64. But I don't have bcm43xx module installed. How can I get around this? I'm unable to update anything, and I have no idea on how to start the Network Manager Service manually. dpkg --configure -a hangs. Quite a serious upgrade flaw if you ask me. How to troubleshoot? Thanks.

```
sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules
```

---

### Post by killerbeesateme on 2007-12-06
I'm suffering from the same issue on a generic kernel 386 system.  I've removed it from the starting on boot using "sudo update-rc.d NetworkManager remove" and after a reboot, I still can't update it.  It just hangs at reloading network manager.

I also can't even remove it.  It just hangs my system.  

The module listed above is not loaded,

Any suggestions?

---

### Post by BigStan23 on 2007-12-07
I have the exact same issue.  7.10 on amd64 with no bcm43xx module.

I have to actually hit the reset button to reboot the system.  This is a MAJOR problem!

Is there a way to get around this problem?

> **TrioTorus said:**
> I've got the exact same problem. On 7.10 amd64. But I don't have bcm43xx module installed. How can I get around this? I'm unable to update anything, and I have no idea on how to start the Network Manager Service manually. dpkg --configure -a hangs. Quite a serious upgrade flaw if you ask me. How to troubleshoot? Thanks.

```
sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules
```

---

### Post by killerbeesateme on 2007-12-07
Well I managed to work out some kind of a fix with the help of hairulfr in the #ubuntu IRC channel.

Here's how I removed the network manager package that was causing me a headache while trying to upgrade or install anything.

KEEP IN MIND THAT THIS REMOVES THE PACKAGE.

I ran "sudo update-rc.d NetworkManager remove"  to remove network manager from starting at boot.  I then rebooted the system.

Then, I fired up synaptic.  I clicked the status button in the lower left hand corner, then in the new menu, I chose "Not Installed (Residual Configuration)"  (or something like that).  

You should see the network manager package giving you all the trouble listed.  

I then marked it for Complete Removal.  

I don't have the applet by the clock anymore, but at least I can use apt again without hanging my system.

Hope it helps!

---

### Post by ztirffritz on 2007-12-08
> **georgz said:**
> For anyone who is interested:

Needed to remove the bcm43xx kernel module
# rmmod bcm43xx

Then it worked.

Doesn't that break the wireless?

---

### Post by BigStan23 on 2007-12-19
As a final updateI tried this process, but it didn't work.

I finally ended up just using kill -9 on the network manager process, then running  "sudo dpkg --configure -a" from a terminal window and everything finally worked went through.  Problem solved.

> **killerbeesateme said:**
> Well I managed to work out some kind of a fix with the help of hairulfr in the #ubuntu IRC channel.

Here's how I removed the network manager package that was causing me a headache while trying to upgrade or install anything.

KEEP IN MIND THAT THIS REMOVES THE PACKAGE.

I ran "sudo update-rc.d NetworkManager remove"  to remove network manager from starting at boot.  I then rebooted the system.

Then, I fired up synaptic.  I clicked the status button in the lower left hand corner, then in the new menu, I chose "Not Installed (Residual Configuration)"  (or something like that).  

You should see the network manager package giving you all the trouble listed.  

I then marked it for Complete Removal.  

I don't have the applet by the clock anymore, but at least I can use apt again without hanging my system.

Hope it helps!

---

### Post by aldo_m on 2007-12-19
well im in the same boat i just did the update and i use a netgear wg511t and now under network it no longer shows after the restart but my usb belkin fd works fine.

---

