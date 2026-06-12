---
title: "Unable to load Ubuntu LiveCD"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by snoguy986 on 2012-06-01
Hey guys.  I'm having issues getting the 12.04 x64 live image to load onto my laptop.  Regardless of the method I try and boot from, I get an error message:

```
panic occurred, switching back to text console
```

I've never had any problems loading Ubuntu on my laptop in the past (up to and including 11.10), and I can install other Linux distros on there as well (latest Fedora release installed no problem).  The only difference between then and now is I upgraded my memory from 4GB to 8GB.  Windows ran just fine on 8GB.

I've tried the regular desktop release via USB and CD.  I've tried the DVD release via USB and DVD.  I've tried the alternate installer via USB and CD.  I've changed BIOS settings, I've ran memory checks, I've run disc integrity checks and it always halts at the same spot mentioned above.

My laptop is a Dell Studio XPS 1340.  Has a Core 2 Duo 2.53GHz processor, 500GB HDD, nVidia graphics 9500GS Hybrid card and the 8GB of memory.

Does anyone have any ideas?

---

### Post by wilee-nilee on 2012-06-01
I would try any of the ISO's you have in vbox to see what happens.

---

### Post by snoguy986 on 2012-06-01
Loaded up the 12.04 x64 DVD image I had handy into VirtualBox, gave it the same amount of memory that my laptop has (desktop has 16GB) and it loaded just fine.  I'm staring at the live desktop right now.

---

### Post by wilee-nilee on 2012-06-01
> **snoguy986 said:**
> Loaded up the 12.04 x64 DVD image I had handy into VirtualBox, gave it the same amount of memory that my laptop has (desktop has 16GB) and it loaded just fine.  I'm staring at the live desktop right now.

Well, hopefully someone will have an idea for the HD, it seems you have tried everything that would find the problem.

Check out post 6 here this is just a quick look at bugs with this computer model.
 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/984387](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/984387)

I would look though bugs,

---

### Post by snoguy986 on 2012-06-02
> **wilee-nilee said:**
> Check out post 6 here this is just a quick look at bugs with this computer model.
 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/984387](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/984387)

I would look though bugs,

Going through those comments got me what I was looking for.  I'll post what I did for anyone else who comes across this.

- Boot with a 12.04 Live CD or USB.
- Select your language.
- Press F6 to edit the command line (advanced options), then press esc to dismiss the popup.
- On the kernel command line, after the --, add ```
ite_cir.blacklist=yes
```
- Press enter

This will allow you to boot into the Live environment and try out or install 12.04.

On first boot, you'll be affected by this problem again, so:
- When booting, right after your PC's POST routine finishes, press the right SHIFT key. Keep it pressed until the GRUB menu appears.
- Press 'e' to edit parameters for the boot entry.
- Move down to the "linux" line (second to last), then move your cursor to the end of that line.
- Again, type ```
ite_cir.blacklist=yes
```
- Press CTRL-X.

This will allow you to boot into your installed 12.04 desktop.  Once you're here, you need to create a blacklist file that will prevent the ite_cir driver from loading.

As sudo/root, open up your text editor and place the following line in it:
```
blacklist ite_cir
```
Save the file in etc/modprobe.d/ as "blacklist-ite-cir.conf" which will blacklist the file permanently.  Reboot your machine and it should boot up without any additional changes from you.

---

