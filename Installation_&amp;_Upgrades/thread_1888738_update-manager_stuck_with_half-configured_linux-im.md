---
title: "update-manager stuck with half-configured linux-image"
date: 2011-11-30
forum: Installation &amp; Upgrades
---

### Post by lordbah on 2011-11-30
This just isn't my day.

Ubuntu 11.04 32-bit, update-manager is hanging. The details window, bizarrely, doesn't support copy/paste, so I'll just retype a bit of it:
Setting up linux-image-2.6.38-13-generic (2.6.38-13.53) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-13-generic

and that's the last line in the details window, that's where it hangs.

Last line in dpkg.log is:
half-configured linux-image-2.6.38-13-generic 2.6.38-13.53

There is no /boot/initrd.img-2.6.38-13-generic. There is a zero-length initrd.img.2.6.38-13-generic.new however. There is still 75M free on the /boot filesystem (out of 193M total), so I hope it's not out of disk space. Rerunning gets stuck in the same place.

How can I unstick this?

---

### Post by lordbah on 2011-12-01
Any ideas? I am at Witt's End.

---

### Post by raja.genupula on 2011-12-01
```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by lordbah on 2011-12-01
Thanks.

dist-upgrade won't go and install 11.10 will it?

---

### Post by lordbah on 2011-12-01
Sadly, the dpkg --configure -a tries to do the same thing and hangs in the same place.

lordbah@penguin:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.38-13-generic (2.6.38-13.53) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-13-generic

I finally interrupted it, and decided to try the install -f anyway. It told me that I must run --configure -a to correct the problem!

Gave it another try, what the heck, but it still hangs. By 'hangs' I mean that I've waited over 10 minutes with no further output (that's today; yesterday I waited hours with no further output).

---

### Post by rcayea on 2011-12-01
I am not sure if this will but I figured I would post. I found this information while surfing for an answer to your problem:

 Edit /etc/hosts with an editor of your choice (e.g. sudo vi /etc/hosts). There should be two entries with IPv4 addresses starting with 127.0.x.x, like this:

127.0.0.1 localhost
127.0.1.1 mycomputername.mydomain

Remove the domain name from the entry starting with 127.0.1.1, leaving only the computer name and save the file. Now try again.

---

### Post by lordbah on 2011-12-01
Thanks, but changing /etc/hosts didn't help.

---

### Post by lordbah on 2011-12-02
I tried to reboot this system, and it exited X, but it couldn't finish shutting down. I powered it off and back on again. Got a panic during startup:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Guess I'll have to dig out a live CD and see if I can boot from that and fix the disk.

---

### Post by lordbah on 2011-12-02
What I wound up doing was using grub to boot the -11 kernel (current is -13). Then I went to synaptic and removed linux-*-12 and -13, thinking that update-manager would notify me that they were available as updates - it didn't. So .... I don't know. I probably screwed up something.

---

### Post by BC59 on 2011-12-02
Should be a good idea to install the Startup Manager from the Ubuntu Software center. Open it and change the default kernel to be the one is working.

---

