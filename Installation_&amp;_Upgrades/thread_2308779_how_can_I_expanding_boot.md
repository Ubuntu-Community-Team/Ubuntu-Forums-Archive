---
title: "how can I expanding /boot"
date: 2016-01-05
forum: Installation &amp; Upgrades
---

### Post by aCeeDub on 2016-01-05
I know that similar questions have been asked, but I can not apply any of the fixes....
I have a production 14u04 sitting on Hyper-v, it used an "out of the box" install, onto 140gb disk. This resulted in a 67mb boot partition. I often had to purge the boot of out of date images; it was fine until recent updates.

I have tried for instance 
apt-get -f install 
apt-get update
apt-get upgrade
apt-get dist upgrade
apt-get autoclean
apt-get autoremove
in all colours and all sizes! In the hope of unblocking the log jam

uname -r returns 3.16.0-56-generic


Yet errors appear to be connected with disk full error when "trying to extract data for" vmlinuz-3.16.0-57-generic, etc.

I have the following initrd.img files in /boot for 3.16.0-45, -50, -51, -52, -53, -55, & -56,   despite having manually removed them.


I've tried to install gparted, but no space, as it's trying to unpack initrd.img.3.16.0-57 ! And of course it asks me to try apt-get -f install, and has "unmet dependencies" (as expected)

At the moment I am playing with a copy of my VM so not too bothered about it going pair shaped.

I'm going potty now, can anyone help please?

Kind regards

---

### Post by oldfred on 2016-01-05
When you say manually removed, did you use dpkg to totally purge as then all the related files also get removed.

You may need to do this?
[http://ubuntuforums.org/showthread.php?t=2308561&p=13417427#post13417427](http://ubuntuforums.org/showthread.php?t=2308561&p=13417427#post13417427)
       cd /boot
ls -l /boot/vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.13.0-{XX,XX,XX,XX,XX,XX}-generic
sudo apt-get purge linux-image-3.13.0-{54,55,57}-generic

---

### Post by ian-weisser on 2016-01-05
> **aCeeDub said:**
> I have the following initrd.img files in /boot for 3.16.0-45, -50, -51,  -52, -53, -55, & -56,   despite having manually removed them.
Please describe, in as much detail as possible, how you 'manually removed' them.
It matters.

The basic theory is simple:
Aptdaemon queues package actions. Autoremove is at the back of the queue. Any failure in a package action (like 'no space left on device') aborts the entire remaining queue.

So regularly, before your /boot is full, run autoremove. Every two weeks. Every day. Regularly. Or enable the unattended upgrades setting to run autoremove daily for you.

Since your /boot is full, use dpkg to remove one old kernel (occasionally two kernels), freeing enough space for the queued apt install to complete, then autoremove can run and happily remove all the rest of the old kernels.

This is a bug: [LP #1357093]("https://bugs.launchpad.net/bugs/1357093"). A fix has been proposed, and is awaiting the next release of unattended-upgrades. Once released, perhaps in 16.04, I will try to get it applied to older releases of Ubuntu.

---

### Post by aCeeDub on 2016-01-19
Sorry for the delay....
@Ian, I used the commands above in my OP
@oldfred, ls -l /boot/vmlinuz*  returns my current boot level "3.16.0-56-generic"
and one build higher (which fails to install due to space restrictions) "3.16.0-57-generic"
uname -r  returns "3.16.0-56-generic"

@Ian, if I run dpkg -l | grep linux-image  i get a list of "rc linux-image-3.16.0-30-generic.... " etc. This concludes (eventually) with "iU linux-image-generic-lts-utopic 3.16.0.57.48"

please see images:
Can I remove 3.16.0-57 as a start?

I would regardless like to expand /boot if possible as I seem to be at an impass.
As mentioned this is hosted on hyper-V and I have allocated more disk-space, although not yet apportioned it.

Many thanks for your help so far & kind regards

---

### Post by aCeeDub on 2016-01-19
@Ian, I note this entry in your bug link:
"The issue here  isn't so much the absolute space initially allocated to the /boot/ LV,  it is that the installer allocates 100% of the Volume Groups space.
 The great advantage of LVM is that space can by dynamically allocated and removed from Logical Volumes as needed.
 [COLOR=#ff0000]If the installer were to leave 5% of the Volume Group unallocated it  would be possible for the system to detect this out-of-space condition  and extend the /boot/ LV:[/COLOR]

 lvextend -l 50%FREE VG/boot
resize2fs /dev/mapper/VG-boot # assuming ext file-system
 and at the same time display a prominent warning and options for automatically removing the superseded kernel versions."


The implication is that now that I have allocated additional space for the VM, the system should automatically apply space where needed?
In confirming that the current copy VM is working correctly, I have booted it several times, and I have not seen any change in volume size.

Regards
Adrian

---

### Post by ian-weisser on 2016-01-19
[EDIT]
rm the initrd.img from -55.
The failure of the package manger to remove that file should have caused an error back when you started to have problems...unless you removed kernels some other way.

Then try configure -a to finish installing -57.

---

### Post by aCeeDub on 2016-01-19
a colleague sugested the following...

[LIST]
[*]Copy the contents of /boot to another folder in the main partition e.g. /boot2, making sure the permissions are the same. 
[*]Unmounted /boot and edit fstab to make sure it is not mounted again. 
[*]Renamed /boot2 to /boot 
[*]Made sure that the system would boot correctly next time (I think using grub?) 
[/LIST]

I'm unable to even create a directory in "/" (GUI), so assuming that I could do his from the command line, would this approach be feasible and/or safe? (I'm using a copy VM, but would rather do it once and do it right!). The solution appears to be to use a live CD to operate upon the target system, however I'm not certain that this can be done on a VM.

In the meantime, can I remove 3.16.0-57-generic, and if so, is it then possible to ensure that 3.16.0-56-generic is correctly installed without the machine attempting to fetch 3.16.0-57-generic again?

---

### Post by ian-weisser on 2016-01-19
I don't understand the question.
You are already running -56, so it seems installed properly already.
You cannot remove -57 until it is finished installing.
You already know the -55 initrd.img is the space hog. rm it.

---

