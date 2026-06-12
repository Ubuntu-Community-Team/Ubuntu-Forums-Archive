---
title: "/etc/modprobe.d/options missing in 9.04??"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by alex88 on 2009-04-05
hi, i'm tring to modify my boot options for modules, in ubuntu 8.10 it was done by editing the /etc/modprobe.d/options, now, i'm using ubuntu 9.04 beta, what should i do? Because there is no file /etc/modprobe.d/options.
Searching on google i've found this:

module-init-tools in Ubuntu Jaunty change logs
/etc/modprobe.d/options: Dropped this file, changes to default kernel
    options should be changed in the kernel so that they also take effect if
    the module is built-in; and also to make sure they're kept in sync with
    any changes to option names or defaults (or even module names) in the
    kernel.

so we have to modify kernel options? and then recompile it? i can do...but i think (and i hope) there is a better and faster way to do that..

---

### Post by BilliShere on 2009-04-05
yeah this is kinda wierd.. i dunno how to get my hda intel sound card working under 64 bit ubuntu without /etc/modprobe.d/alsa-base

---

### Post by Flag on 2009-04-06
/etc/modprobe.d/alsa-base.conf

---

### Post by alex88 on 2009-04-06
Yes the file is /etc/modprobe.d/alsa-base.conf, but i need options because i have to use software encryption for my intel 4965...

---

### Post by redenex on 2009-04-10
hmmmmm I find that file missing as well. :rolleyes:

---

### Post by cresny on 2009-04-11
did you try adding a kernel boot option instead? 

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

This worked for my intel bx2 secondary marvell sata controller.

in 8.10, /etc/modprobe.d/options
options ahci marvell_enable=1

in 9.04, /boot/grub/menu.lst
# kopt=.... ahci.marvell_enable=1    ('#' is NOT to be removed)

---

### Post by Zorael on 2009-04-12
At least pre-9.04 it parsed all files in /etc/modprobe.d/ for options. I had a script that I always ran after installation that created **/etc/modprobe.d/iwl3945** with some options needed for my Intel 3945 wlan card. So unless stuff has really changed (?) you should be able to just touch a new options file.

---

### Post by chili555 on 2009-04-13
I believe the new method is to create an options file appended with *.conf.* I put my iwl3945 options in a file */etc/modprobe.d/iwl3945.conf.* According to *dmesg,* no errors were noted upon boot.

---

### Post by markbuntu on 2009-04-13
When I boot I get a message flashing by

FATAL: file etc/modprobe.d/options missing blah blah... 

or something like that. Obviously not fatal since it boots but...

---

### Post by chili555 on 2009-04-13
> FATAL: file etc/modprobe.d/options missing blah blah...or something like that.Did *dmesg* capture it more exactly for us?

---

### Post by zika on 2009-04-14
> **chili555 said:**
> Did *dmesg* capture it more exactly for us?
I'm getting the same kind of messages: before```
19+0 input
19+0 output
```ater stating that ata was not ready and that soft-reset was needed for that device it gives (from the memory that is not in dmesg, it seems it is before it starts logging)```
FATAL:modprobe could not find the file /lib/modules/2.6.{28-...,30-...}/modules.dep
```which is there and is OK.
after  ```
19+0 input
19+0 output
```everything goes its way and gives boot time of less than 30 seconds ...

---

