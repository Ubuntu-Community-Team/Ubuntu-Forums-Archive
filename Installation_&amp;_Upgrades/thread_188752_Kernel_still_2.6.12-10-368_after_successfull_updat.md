---
title: "Kernel still 2.6.12-10-368 after successfull update."
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by Nordoelum on 2006-06-04
Greetings,

I have just found out that my kernel is still out of date :(

Can I find out which version I have installed, and maybe edit GRUB? Since I haven't replaced the GRUB loader when I updated.

---

### Post by taurus on 2006-06-04
Did you update your kernel?  You can tell whether you have a newer version by looking in /boot!  Then, check /boot/grub/menu.lst to make sure there is an entry for the new kernel...
```

ls -la /boot
uname -a

```
```

sudo gedit /boot/grub/menu.lst

```

---

### Post by Nordoelum on 2006-06-04
Did an $sudo grub-update:
> Found kernel: /boot/vmlinuz-2.6.15-23-368
Found kernel: /boot/vmlinuz-2.6.12-10-368
Found kernel: /boot/vmlinuz-2.6.12-9-368
Found kernel: /boot/memtest86+.bin
Rebooting now.

---

### Post by Sukarn on 2006-06-04
You have to (as far as I know) manually select and install a new kernel from the repositores.
Go into synaptic (or whatever you use) and search for **linux-image** and install the kernel you want to have.
As of the time of writing this, the latest kernel in the repositories of Ubuntu is 2.6.15-23.

To remove an old kernel -
1) delete the corresponding kernel files in /boot
2) delete the corresponding kernel directory in /lib/modules
3) run **sudo update-grub**

I'm sure theres more stuff that can be removed (for the old kernel), and if someone knows it, then please tell me about it.


EDIT: seems that you got a reply and made a reply while I was on the phone with a half-written reply.

---

