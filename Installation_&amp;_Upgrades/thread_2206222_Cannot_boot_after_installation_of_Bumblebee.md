---
title: "Cannot boot after installation of Bumblebee"
date: 2014-02-18
forum: Installation &amp; Upgrades
---

### Post by Lhynard on 2014-02-18
I have a Dell Inspiron laptop with a hybrid graphics card system. I also had it partitioned and set up to dual boot with Windows 7 and Kubuntu 12.04. About a year ago, I loaded Bumblebee. I recall running into some difficulties then, but I solved them and could use optirun to turn on my NVIDIA card for graphics-heavy programs. All this is to say that at one time everything was working perfectly.

Then a while ago, my Linux kernel got corrupted somehow, so a few weeks ago, I reinstalled Kubuntu from scratch and have been slowly installing software as I need it.

Today, I tried to install Bumblebee. I used:

$ sudo add-apt-repository ppa:bumblebee/stable

and

sudo apt-get install bumblebee bumblebee-nvidia virtualgl linux-headers-generic

following the directions on [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee).

When I rebooted and selected Kubuntu from my GRUB menu, I got the following error:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I did a Google search on this error and "Bumblebee". One person suggested adding a delay to the startup of Bumblebee by editing the etc/init/bumblebeed.conf file. This changed nothing. Then I tried to change the setting PMMethod to none in etc/bumblebee/bumblebee.conf. This also changed nothing.

Finally, I decided to resort to using Live to run boot-repair, which has saved me in the past. After running with the default options, I now got a new error.

error: invalid arch independent ELF magic

Having read more, I suspect that I may have ruined things by not using

sudo apt-get install bumblebee bumblebee-nvidia virtualgl linux-headers-generic-lts-raring

but at this point, I don't know what to do. HELP!

Here is my boot info: [http://paste.ubuntu.com/6952636/](http://paste.ubuntu.com/6952636/)

Thankfully, GRUB still boots me into Windows just fine. I only cannot boot in Kubuntu anymore.

---

### Post by Lhynard on 2014-02-19
I figured out the issue that was causing the arch ELF magic error. I have a caching SSD for use in Windows that was "using" the hard drive so that Boot Repair could not mount properly to repair the boot. After going into Windows and shutting off the acceleration, I could then use the Live CD and Boot Repair to fix Grub. After booting successfully into Kubuntu, I could then go back into Windows and turn back on the acceleration.

Bumblebee, however, failed to install properly at all. And I still don't understand how it broke the boot in the first place.

---

