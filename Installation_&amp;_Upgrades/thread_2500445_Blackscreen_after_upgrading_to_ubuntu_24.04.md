---
title: "Blackscreen after upgrading to ubuntu 24.04"
date: 2024-09-02
forum: Installation &amp; Upgrades
---

### Post by kbeeson on 2024-09-02
Hi all,

I am encountering a black screen after upgrading from ubuntu 22.04 to 24.04. My device is a HP 840 G7 laptop. I normally dual boot with windows 10 and ubuntu 22.04. 

I have booted from a USB stick and run boot-repair, this is the report [https://paste.ubuntu.com/p/CB9jHPmZ2G/](https://paste.ubuntu.com/p/CB9jHPmZ2G/). If I click on recomended repair it then tells me "grub-efi-amd64-signed purge cancelled".

I have also tried to go into safe mode when booting up. That puts me into initramfs with the following message:
```
Begin: Waiting for root file system Begin: Running/scripts/local-block ... done.

done.

Gave up waiting for root file system device. Common problems:

     - Boot args (cat /proc/cmdline)

        - Check rootdelay= (did the system wait long enough?)

     - Missing  modules (cat /proc/modules; ls /dev)
 ALERT!  UUID=28fb8e59-f65f-48ca-9240-ff1fe5f96ff3 does not exist. Dropping to a  shell!

BusyBox v1.30.1 (Ubuntu 1:1.30.1-7ubuntu3.1) built-in shell (ash)

Enter 'help' for a list of built-in commands. 
(initramfs)
```

Not really sure how to proceed. Thank you in advance for any help!

---

