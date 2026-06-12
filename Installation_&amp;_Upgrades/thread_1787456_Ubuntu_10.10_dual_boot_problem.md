---
title: "Ubuntu 10.10 dual boot problem"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by wembleyboy on 2011-06-21
I had installed 10.10 on my dell laptop and then on a seprate partition the same disk installed 10.10 and was going to migrate all my docs etc when I got my chance. 

It was all good at start up I would get the option to pick which version of Ubuntu that I want to boot into. 

For a  long time I was not using the the older 10.10 , I then had to get some docs from the older 10.10 logged in just fine ....but now I no longer get the option at start up to pick the newer version of 10.10 that I want to log into . 

Thanks in advance ;)

---

### Post by nzjethro on 2011-06-21
Hi there, run the script

```
sudo update-grub
```

Check the terminal output. It should list your installed OSes. If two versions of 10.10 come up, reboot, and see whether re-writing grub.cfg has fixed the problem. If two versions do not come up, post the output of that command here, and we'll try to see what the error is.

---

### Post by wembleyboy on 2011-06-23
Hi nzjethro, 

Thanks for getting back to me below is the output of the command that you mentioned. 

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-28-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-27-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-27-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-25-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-24-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-23-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-22-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-22-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done


Thanks in advance !!!!!!

Chan

---

