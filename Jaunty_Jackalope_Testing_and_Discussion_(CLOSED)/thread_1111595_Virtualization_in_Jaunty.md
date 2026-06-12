---
title: "Virtualization in Jaunty"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rcdeacon on 2009-03-30
I have just installed Jaunty Jackalope in a dual boot environment with Vista. Has anyone tried Virtualbox or any of the other products with success?

---

### Post by deep888 on 2009-03-31
I recently updated to Jaunty beta, and attempted to install VirtualBox for the first time, but I got shot down by some error telling me that there aren't any preconfigured thingys for my kernel... I had to abort

If anyone knows what I mean, please help!

---

### Post by jaqrah on 2009-03-31
I have the Jaunty Jackalope Beta running in Vbox currently.  I haven't had a lot of time to play with it yet.  

So far...no issues.


Oops...misunderstood your question.  Disregard my reply.

---

### Post by bodhi.zazen on 2009-04-01
Moved to the Jaunty Section as Jaunty is still in pre-release :)

I have only run Jaunty as a guest but installing and running as a host is on my to-do list.

If you have any experience, let me know and I can start to work on updating some of the stickies.

---

### Post by skillllllz on 2009-04-01
> **rcdeacon said:**
> I have just installed Jaunty Jackalope in a dual boot environment with Vista. Has anyone tried Virtualbox or any of the other products with success?

I have Jaunty installed on two of my machines; both have VirtualBox installed with multiple Windows XP and Ubuntu guests (incl. guest additions). Everything installed flawlessly out of the box and it all works perfectly, all around. Try it and see.

---

### Post by phenest on 2009-04-01
I'm running Jaunty as host, and have VirtualBox OSE installed. I have Ubuntu, Fedora, openSUSE, XP, and Vista as guests. Works very well.

---

### Post by p_squared on 2009-04-01
VMware server fails to list my virtual machines after a clean install of the Jaunty beta.  Within my web browser I get
```
One or more of the virtual machine configuration files are inaccessible. The cause of this problem may be transient (for example, because the virtual machine's datastore is not available). You can remove the virtual machine from the inventory if you believe the cause is permanent.Click the link below to remove the virtual machine from the inventory.
Remove Virtual Machine
To help diagnose the issue, you can check the virtual machine files at their last known location: "/media/Storage/.virtual_machines/vmware/Virtual Machines/Ubuntu Server 8.10/Ubuntu Server 8.10.vmx"
```
The output from /etc/init.d/vmware status shows
```
Bridged networking on /dev/vmnet0 is running
Host network detection is not running
Host-only networking on /dev/vmnet1 is running
DHCP server on /dev/vmnet1 is not running
Host-only networking on /dev/vmnet8 is running
DHCP server on /dev/vmnet8 is not running
NAT networking on /dev/vmnet8 is running
Module vmmon loaded
Module vmnet loaded
```
After I run /usr/bin/vmware-config.pl all is well until I reboot again.

I'm running version 2.0.0 build-122956, downloaded from vmware's site.  Anyone else run into this?

---

### Post by loomsen on 2009-04-01
Workin fine for me, using a XP I "enlightened" a little bit. Need it for my poker apps, though my postgresql Server runs in linux, VBox attached through virtual subnet.

> 
shot down by some error telling me that there aren't any preconfigured thingys for my kernel... I had to abort

If anyone knows what I mean, please help!

If you stood back up again you'd have been able to read a solution...

```
 sudo /etc/init.d/vboxdrv setup

```

---

### Post by nandemonai on 2009-04-14
I was able to get VMware Server 1.0.9 to compile the modules under Jaunty using a patch for Intrepid Ibex ([http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz](http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz)). It works but it doesn't perform anywhere near as well as it did under Intrepid.

I had keyboard shortcut errors which were alleviated by following the guide here: [http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html](http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html) (Step 3)

That being said I occasionally get some very odd behavior regarding the keyboard where a particular key will repeat lock, usually Enter. It's been so bad sometimes I've had to force breaking to CLI via Alt-Ctrl F1 which seemed to fix it, either that or a hard reset once when I wasn't able to do that even.

Performance wise the VMs are a tad sluggish and tend to thrash the hdd when first starting them causing a lot of lag and fading the VMware Server window like it's going to crash. They eventually load though.

I'm wondering if this is because I chose the option to encrypt my /home/ dir during install (I have my VMs on /home/)

This sums up my experience so far. If I can't work out the issues I'm having I'm going to have to look at changing virtulization options.

---

### Post by skillllllz on 2009-04-15
> **nandemonai said:**
> 
...Performance wise the VMs are a tad sluggish and tend to thrash the hdd when first starting them causing a lot of lag and fading the VMware Server window like it's going to crash. They eventually load though.

I'm wondering if this is because I chose the option to encrypt my /home/ dir during install (I have my VMs on /home/)...

Running a VM that resides on an encrypted filesystem is going to be terribly slow.

---

### Post by MysticGold04 on 2009-04-15
Just out of curiosity has anyone tried installing the non-OSE version of VirtualBox on Jaunty? I don't believe that Sun has a package for it yet, but I'm wondering if the Intrepid package will install... I might try it if I have some time.

---

### Post by skillllllz on 2009-04-15
> **MysticGold04 said:**
> Just out of curiosity has anyone tried installing the non-OSE version of VirtualBox on Jaunty?  I might try it if I have some time.

Yes, it works great.

---

### Post by nandemonai on 2009-04-15
> **skillllllz said:**
> Running a VM that resides on an encrypted filesystem is going to be terribly slow.

I kind of assumed that though I must say I've been playing with Virtual Box tonight and it's fast as it should be (VMs also on encrypted /home/). Probably better than VMware Server back on Intrepid (No encryption) so I'm not really convinced that the issues I'm having in VMware Server 1.0.9 under Jaunty are entirely encryption related.

---

### Post by skillllllz on 2009-04-15
> **nandemonai said:**
> I kind of assumed that though I must say I've been playing with Virtual Box tonight and it's fast as it should be (VMs also on encrypted /home/). Probably better than VMware Server back on Intrepid (No encryption) so I'm not really convinced that the issues I'm having in VMware Server 1.0.9 under Jaunty are entirely encryption related.

I've found that VirtualBox is much faster in general, especially when suspending and resuming VMs, and creating snapshots. Honestly, unless you require some (possibly) specific features of VMware Server, VirtualBox is the way to go right now.

---

### Post by Seventh Reign on 2009-04-15
> **MysticGold04 said:**
> Just out of curiosity has anyone tried installing the non-OSE version of VirtualBox on Jaunty? I don't believe that Sun has a package for it yet, but I'm wondering if the Intrepid package will install... I might try it if I have some time.

There is a Jaunty Deb Package on their website (Its in the same line as the Intrepid Package) and it works great.

---

### Post by bodhi.zazen on 2009-04-15
I find KVM is the way to go. This assumes you have the hardware of course ;)

---

### Post by dabl on 2009-04-15
VMWare Player 2.5.2 (64-bit) is installed and running great, but there is something hokey with the bridged networking.  Most boots (4 out of 5, maybe) I get the "bridged networking is down" error, but then once in awhile it comes up perfectly.  I don't get that at all.  :confused:

---

### Post by nandemonai on 2009-04-15
> **skillllllz said:**
> I've found that VirtualBox is much faster in general, especially when suspending and resuming VMs, and creating snapshots. Honestly, unless you require some (possibly) specific features of VMware Server, VirtualBox is the way to go right now.

After tonight I whole heartily agree. It seems for the moment though that the 2.1.4 version is a wiser choice. I had a lot of VM freezes with the 2.2 version in my testing tonight. Seems like a few others have noticed the same thing. Disabling ACPI on the guest seems to be the 'fix' but I downgraded to 2.1.4 myself as I don't need any of the additional features of 2.2 myself.

Edit: This is the OSE version I'm talking about. Thought it prudent I add that. ;)

---

### Post by MysticGold04 on 2009-04-15
> **bodhi.zazen said:**
> I find KVM is the way to go. This assumes you have the hardware of course ;)

KVM, as in separate PC? :)  That's how I'm testing Jaunty!

---

### Post by MysticGold04 on 2009-04-15
> **Seventh Reign said:**
> There is a Jaunty Deb Package on their website (Its in the same line as the Intrepid Package) and it works great.

Thanks, I'll check that out.. I didn't think they had a jaunty package just yet. 

:guitar:

---

### Post by bodhi.zazen on 2009-04-15
> **MysticGold04 said:**
> KVM, as in separate PC? :)  That's how I'm testing Jaunty!

:lolflag: no, KVM as in Intel VT (hardware virtualization).

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by vdings on 2009-04-16
what about kqemu, how does that compare with virtualbox?

---

### Post by FredB on 2009-04-16
> **vdings said:**
> what about kqemu, how does that compare with virtualbox?
Kqemu will be harder to set up. If you have a Intel or and AMD with virtualization in it, the best thing is KVM.

---

### Post by MysticGold04 on 2009-04-16
> **bodhi.zazen said:**
> :lolflag: no, KVM as in Intel VT (hardware virtualization).

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

LOL thanks, I'll read up about it.

---

