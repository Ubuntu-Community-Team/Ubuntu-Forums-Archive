---
title: "Need help upgrading from Kubuntu 14.04 to 16.04 without breaking system."
date: 2016-12-15
forum: Installation &amp; Upgrades
---

### Post by Telxonator on 2016-12-15
Hello all, I was thinking of updating to Kubuntu 16.04, but last time I did a dist-upgrade, it screwed up all of my hardware configs for my GPU and others. I want to avoid all that unnecessary stuff this time around, as it took me several days to get my graphics card working properly, and I forget now how I did it. As it stands, my system is working fine now, but I want to know how to instruct the install to not alter my graphics card driver settings or my custom GRUB settings, as I really don't want to redo them.    
Info: 
Kubuntu 14.04 LTS 64 bit  
kernel: 3.16.0-59 generic 
 4 GB RAM  
GPU: VGA compatible controller: NVIDIA Corporation G94 [GeForce 9600 GT] (rev a1)   
driver Nvidia legacy binary driver 304.132 from nvidia 304 

Would it be less hassle to just leave it alone, being I have a few more years of support on 14.04, or should I go ahead and upgrade it. Any other info I can provide, please let me know.

---

### Post by TheFu on 2016-12-15
* dist-upgrade takes 14.04.1 --> 14.04.2 (and similar) replacing packages and dealing with dependencies in a "smart" way.  It does NOT go from 14.04 to anything that isn't 14.04-based.

* To update between distros, there is a tool called **do-release-upgrade** which cleans up the APT sources to the bare mins, then changes the sources to the next release (or perhaps LTS to LTS) and does an upgrade.

* binary drivers often are not compatible between different kernels. THAT is probably what happened previously.  After every kernel change, the drivers need to be re-linked for the net kernel entry points.

Anytime there are system updates (which are important for security!), there is a risk that something will break.  Before doing it, just create a snapshot or backup so if things go badly, there is a record of the old setup and you can revert if needed, before trying again.

If you aren't on 14.04.1 or 14.04.5, then your system isn't properly maintained.  I'm running 3.13.0-100-generic kernel. Newer isn't always better. Support is dependent on which kernel is being run and whether it is supported or not.  [https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support) 3.13.x or 4.4.x.x are the officially supported kernels for 14.04.x. Anything else is NOT supported. Beware.

What does all this mean to you?  You really need to get onto a supported kernel line. Being on the internet without a properly patched system is dangerous.

Any updates to the kernels needs to impact grub. No way around it.  Just make a backup of any config changes so those can be put back, iff they are altered. This really applies to anything on the system.

---

### Post by Telxonator on 2016-12-16
Ok, well I do update the system at least twice a week, either using muon or apt-get update and apt-get upgrade. I'm running 14.04.5 currently. I will likely stay with 14.04.x until it is no longer supported, just to avoid the hassle as long as possible.
In the future, what's the best way to insure I don't have to spend days getting my system back up and running because it borked the drivers? A snapshot just seems it would get me back to where I was, but it still wouldn't be upgraded. All my important stuff is backed up on 3 external HDDs and a NAS, and that has saved my ass a few times!

---

### Post by TheFu on 2016-12-16
The supported 14.04.5 release uses a v4.4.x kernel. Something isn't correct with your system.
The v3.16.x kernel support ended with 14.04.2 support. You need to use **apt-get dist-upgrade** to get to a supported kernel or use backups to get back to the v3.13.x.x kernels.  Those are the two that have support today.  

You are at risk currently - since August.  Did you review that link?

If you only use kernel-provided drivers, by selectively choosing hardware, that will drastically reduce driver issues.  Using proprietary drivers raises the risks, IMHO.  Nvidia didn't have the best reputation for creating solid drivers. I've been using Intel GPUs for years, so don't really keep up with proprietary GPU drivers. Sorry.

Most of my server systems are on 14.04.1 with v3.13 kernels. No GUI. This is a highly selective effort.

3.16.0-4-amd64 is the supported kernel for a debian release. Could that be the OS you are running?

I update weekly, during approved maintenance periods. We are taking steps to reduce downtime during those times too, but that won't help a desktop user.

---

### Post by Telxonator on 2016-12-16
Ok, I may just need to start from scratch then, or update to the new LTS, as running the dist-upgrade did not change the kernel. I don't know why it is at an older version. I am kind of stuck with the hardware I have, can't really afford to drop $50-$100+ on a new GPU, when this one works for me. I'm going to back up all my important stuff, and give the do-release-upgrade option a go, after reading about it. Edit: running sudo do-release-upgrade shows "no new release found" Looks like going from scratch is the only option now.

---

### Post by Telxonator on 2016-12-17
Ok, so I have sort of a fix that worked for me, but might not be feasible for others. I simply put a second empty hard drive in, installed 16.04.1 on it fresh, and kept the original drive as an extra backup. I have lost the use of the GPU, as the stupid driver manager doesn't want to find it, but the internal graphics chipset seems to work fine for streaming videos, so I'll likely just stick with it.

---

