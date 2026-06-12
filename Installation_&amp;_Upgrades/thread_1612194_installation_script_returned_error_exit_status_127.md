---
title: "installation script returned error exit status 127"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by pacice on 2010-11-02
E: linux-image-2.6.32-25-generic-pae: subprocess installed post-installation script returned error exit status 127
E: linux-image-generic-pae: dependency problems - leaving unconfigured
E: linux-generic-pae: dependency problems - leaving unconfigured

Every time I try to use Synaptic or do an update I am getting this message.
Any suggestions to fix this problem.
Thanks

---

### Post by Barriehie on 2010-11-02
> **pacice said:**
> E: linux-image-2.6.32-25-generic-pae: subprocess installed post-installation script returned error exit status 127
E: linux-image-generic-pae: dependency problems - leaving unconfigured
E: linux-generic-pae: dependency problems - leaving unconfigured

Every time I try to use Synaptic or do an update I am getting this message.
Any suggestions to fix this problem.
Thanks

Could be your /etc/apt/sources.list file is screwed up.  This [link](http://repogen.simplylinux.ch/) can generate another one.  Or you can try to fix it via the CLI:
```

aptitude -f -s install linux-image-generic-pae
```
the -f will tell aptitude to try and fix and the -s says to simulate.  It won't do anything except tell you what would happen without the -s switch.

---

### Post by pacice on 2010-11-03
As you can see from below, I am still getting the error message.
I have replaced the etc/apt/sources.list as per the link.

> phil@phil-laptop:~$ sudo apt-get install -f
[sudo] password for phil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 39 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-25-generic-pae (2.6.32-25.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic-pae
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 32: title: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-25-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.32-25-generic-pae; however:
  Package linux-image-2.6.32-25-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.32.25.27); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.32-25-generic-pae
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by Barriehie on 2010-11-03
You've got something wrong with grub!  I'm only vaguely familiar with legacy grub; it never breaks.  Do you know what version of grub you've got?
```

# > grub --version
```

---

### Post by pacice on 2010-11-04
Couldn't get the grub version command to work.
Kept on saying grub was not installed.

I checked Synaptic and found an ! mark against the grub file, right click showed an upgrade option.

I tried the upgrade but got the same error.

I took the brave step of deleting grub, and reinstalling it.

Problem solved.
Thanks for your thank and guidance.

---

