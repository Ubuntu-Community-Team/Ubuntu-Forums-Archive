---
title: "Have to select last kernel revision on boot 16.04"
date: 2018-02-01
forum: Installation &amp; Upgrades
---

### Post by fattyz on 2018-02-01
Hi my install is not working after the last update.  When the machine starts it hangs on a blank screen after I select Ubuntu (or it selects itself) and I have to reboot go into advanced options in grub and select the previous version.  I am not sure what to do about this.   I don't feel confident to keep 'building it out' if I'm going to have to end up re installing again.

Dual boot Win 10 Ubuntu 16.04 Dell Inspiron Laptop 7567 

Any advice?

Thanks

---

### Post by ajgreeny on 2018-02-01
What kernel versions do you currently have installed?
Show us the output from terminal command ```
ls /boot | grep vmlinuz
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

Run command ```
sudo apt-get update
sudo apt-get dist-upgrade
``` and you may get a newer kernel version which solves this problem for you.

---

### Post by fattyz on 2018-02-01
Hi thanks,

```
 dad@dad-PC:~$ ls /boot | grep vmlinuz
vmlinuz-4.10.0-28-generic
vmlinuz-4.13.0-26-generic
vmlinuz-4.13.0-26-generic.efi.signed
vmlinuz-4.13.0-32-generic
vmlinuz-4.13.0-32-generic.efi.signed
dad@dad-PC:~$ 
```

I will give your suggestion a try.

---

### Post by vmiheer on 2018-02-01
I am facing same issue, exactly after update from kernel 4.10.0-28-generic to 4.10.0-31-generic. I update daily to check if newer kernel would work but none of the newer kernel is running.
I have dell inspiron 15 3000 series laptop.
----
```

:~$ ls /boot | grep vmlinuz
vmlinuz-4.10.0-28-generic
vmlinuz-4.13.0-31-generic
vmlinuz-4.13.0-32-generic

```
----
Please let me know if I should file ubuntu bug and if yes how to do that what information I should be providing.
Thanking you.
+miheer

---

