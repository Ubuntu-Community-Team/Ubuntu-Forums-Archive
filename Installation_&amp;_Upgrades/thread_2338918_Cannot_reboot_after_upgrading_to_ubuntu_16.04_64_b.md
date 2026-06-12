---
title: "Cannot reboot after upgrading to ubuntu 16.04 64 bit"
date: 2016-10-03
forum: Installation &amp; Upgrades
---

### Post by hieule246 on 2016-10-03
hi everyone. I just installed ubuntu 16.04 64 bit on top of my current ubuntu 16.04 32 bit. During partitioning i point the new ubuntu to "/" as the shown in this instruction: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
When i reboot my laptop (thinkpad t520), i got this error shown in the file:

```
tpm_t is 00:05: A tpm error (6) occured attempting to read a pcr
value
/dev/sda5: clean, ........ files .... blocks (check in 5 mounts)
request_module: runawa loop modprobe binfmt-464c
run-init: /sbin/init:exec format error.
```

I wonder if anybody has the same issue or know how to fix this problem ? Any help is really appreciated.

Thank you :)

---

### Post by Bucky Ball on 2016-10-03
Welcome. Do you have a 64bit processor??? Are you dual-booting with Windows?

You might want to run Boot Repair and provide us with the BootInfo output by running the script with boot repair (don't do a recommended repair at this point, just run the Boot Info). There is a link at the end of the first line in my signature.

---

### Post by hieule246 on 2016-10-03
i have a 64 bit processor and yes, I dual boot with Windows 7.

---

### Post by Bucky Ball on 2016-10-03
Then please run the bootinfo script, as suggested in my last post and post the link you get at the end of the process back here, please.

---

### Post by hieule246 on 2016-10-03
I just ran the bootinfo. here is the output : [http://paste2.org/OX9kCdFX](http://paste2.org/OX9kCdFX)
and thank you so much for your help :)

---

