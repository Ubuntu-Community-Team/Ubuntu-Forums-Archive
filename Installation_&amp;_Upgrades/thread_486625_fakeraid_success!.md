---
title: "fakeraid success!"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by elightbo on 2007-06-28
Well, it worked, I'm dual booting Windows Vista and 640bit Ubuntu Feisty Fawn on a fake-raid RAID 0 setup.  I followed these excellent instructions:
[https://help.ubuntu.com/community/FakeRaidHowto#head-7918ab0def192cdf40484077136a40241732c669](https://help.ubuntu.com/community/FakeRaidHowto#head-7918ab0def192cdf40484077136a40241732c669)
Thanks to whoever put it together. 

I do have a couple of minor (I hope) problems, though.  When I was on the part that instructed to install ubuntu-desktop (apt-get install ubuntu-desktop), it worked minus the  four packages usplash-theme-ubuntu, ubuntu-desktop, brltty, and brltty-x11.  I tried running the command after installation as well, and had a similar error message:
```

$ sudo apt-get install ubuntu-desktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up usplash-theme-ubuntu (0.14) ...
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.20-16-generic
dpkg: error processing usplash-theme-ubuntu (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on usplash-theme-ubuntu; however:
  Package usplash-theme-ubuntu is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up brltty (3.7.2-7ubuntu3) ...
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.20-16-generic
dpkg: error processing brltty (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of brltty-x11:
 brltty-x11 depends on brltty (= 3.7.2-7ubuntu3); however:
  Package brltty is not configured yet.
dpkg: error processing brltty-x11 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 usplash-theme-ubuntu
 ubuntu-desktop
 brltty
 brltty-x11
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I tried installing the packages individually, but came up with smilar errors with all four pakcages being listed at the bottom.  

Also, under administration, I only have keyring manager, network tools, printing, system log, 
system monitor, and update-manager as options.   Is this related?

Thanks once again for the help.
~eric

---

### Post by Pumalite on 2007-06-28
Check the size and occupancy rate of your partitions:

Code:  df -h

---

### Post by elightbo on 2007-06-28
This is what I get returned:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/isw_dhgjhgehib_Boot7
                       74G  2.6G   68G   4% /
varrun                502M  104K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M  120K  502M   1% /proc/bus/usb
udev                  502M  120K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   39M  464M   8% /lib/modules/2.6.20-16-generic/volatile
/dev/mapper/isw_dhgjhgehib_Boot5
                       23M   19M  3.2M  86% /boot


```

---

### Post by Pumalite on 2007-06-28
Where is /home? Or did you just do '/' and 'swap'? Try installing through Synaptic.

---

