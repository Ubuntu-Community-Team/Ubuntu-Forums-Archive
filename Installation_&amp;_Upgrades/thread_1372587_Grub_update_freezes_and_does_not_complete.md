---
title: "Grub update freezes and does not complete"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by Carcarius on 2010-01-04
Hello,

I have an odd issue that someone has hopefully seen before or can provide a next step.  Firstly, I installed Ubuntu 9.04 about 7 months ago and things ran fine.  I then did an upgrade (via apt-get) to the 9.10 kernel:
*
Current: Linux 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux
*
Still, I had a properly functioning system.  I then decided to install selinux since I was interested in learning how to set it up and get familiar with it's security features.  When I was installing it, it got stuck on the portion where it had to modify Grub.   It got stuck in a similar point as the following:
__
sudo dpkg --configure -a
Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
__

It just hangs at this point and never completes the installation.  I get no error, it just freezes at this point.  The above is where I am now where I can't complete a Grub install.  Initially, I had rebooted the system and got stuck at the sh: grub> prompt instead of a proper Grub boot menu, but I have since fixed that and can boot into my existing Ubuntu desktop from a proper Grub menu.

Has anyone seen the attempt to update Grub, or install selinux, get stuck at this point in the installation?  

I appreciate any insight that can be provided.

---

### Post by drs305 on 2010-01-04
> **Carcarius said:**
> 
Has anyone seen the attempt to update Grub, or install selinux, get stuck at this point in the installation?  

I appreciate any insight that can be provided.

I have, but in my case it appeared to have found all the kernels I was interested in and I merely hit CTRL-C (after giving it a very long time to search my disks) and proceeded on. I then ran "sudo update-grub" and it seemed to work the next time 'round. 

If you get into Ubuntu, you could try:
```

sudo dpkg-reconfigure grub-pc
sudo grub-install /dev/sdX

```
For the first, make sure you use the space and tab keys to make the entries. For dpkg-reconfigure, usually nothing is required on the first input, and if you want "quiet splash" on the second. The important is the third, where you need to make sure at least one (and the one you want) partition has an asterisk in it (with the space bar). Then tab to OK and continue.

Run grub-install afterward, making sure to designate the correct drive. Then "sudo update-grub" again just for good measure and see if it finds your other installs.

Hopefully you won't get the same hangup.

---

### Post by Carcarius on 2010-01-04
> **drs305 said:**
> I have, but in my case it appeared to have found all the kernels I was interested in and I merely hit CTRL-C and proceeded on. I then ran &quot;sudo update-grub&quot; and it seemed to work the next time 'round. 

If you get into Ubuntu, you could try:
```

sudo dpkg-reconfigure grub-pc
sudo grub-install /dev/sdX

```

 Thanks for the reply.  I attempted to execute your suggested commands (sudo dpkg-reconfigure grub-pc) and received the following response:  /usr/sbin/dpkg-reconfigure: grub-pc is broken or not fully installed  So, it is likely not fully installed.  I presume that the attempted selinux installation may have not gotten fully installed and the issues with grub-pc is a consequence of that.  It looks like I have more looking to do to fix this.  I also find that attempting to access my home directory freezes as well.  However, I can access sub-directories inside my home directory.  My system is not real healthy right now

---

