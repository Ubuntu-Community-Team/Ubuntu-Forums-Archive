---
title: "After upgrade to 8.04, no entry in Grub for new kernel"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by Jored on 2008-06-29
I have upgraded my Dell LS400 laptop from 7.10 to 8.04. Upgrade completed successfully.
However, there is no Grub entry for the new kernel and the system boots into the 7.10 kernel (2.6.22.14-generic).

When I type into terminal:

lsb_release -a

I get Ubuntu 8.04, Hardy.

When I type:

uname -r

I get 2.6.22.14-generic

However,when I type:

sudo update-grub

I get:

"Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ...done"

So apparently, the new kernel has been found, yet Grub fails to update.

Can anyone help me edit grub manually, or any other way for grub to "see" the 8.04 kernel and boot into it?

By the way, System Monitor shows Ubuntu 8.04 and everything has been upgraded (OpenOffice, Firefox, etc) and works with the 7.10 kernel (??). With a few problems (microphone does not work, fonts in system Monitor, Terminal, etc are virtually unreadable, etc).

---

### Post by Pumalite on 2008-06-29
Delete.

---

### Post by Jored on 2008-06-30
Wow, that's a really explicit and helpful response.:confused:

Anyway, searching countless other posts, I did solve the grub entry problem by reinstalling 2.6.24-19-generic kernel with Synaptic and choosing the option to replace grub entries with developers choice.

However, still no microphone (internal or external) and lousy unreadable fonts in System Monitor, Terminal, etc.

Everything else seems to work fine an system is faster thn with Gutsy.

---

### Post by SkonesMickLoud on 2008-06-30
You could have also written the entry to menu.lst for yourself.

All you really needed to do is copy/paste the entry for the 2.6.22* kernel into said menu.lst and update the locations of the new vmlinuz and initrd.

Also, there doesn't seem to be a way to delete one's post on here, so I'm sure Pumalite didn't mean it the way it came across...

---

### Post by Licurgo on 2008-07-01
Jored:
I suggest to back up and make a fresh new install
This could prevent headaches
:lolflag:

---

### Post by polmir on 2008-07-01
> **Licurgo said:**
> Jored:
I suggest to back up and make a fresh new install
This could prevent headaches
:lolflag:What? This Linux is no Windows.


**Jored**
type in terminal```
cat /boot/grub/menu.lst
```and paste the output of the forum.

---

### Post by Licurgo on 2008-07-02
Polmir:

> What? This Linux is no Windows.
I feel you don't understand
Back up the information, the settings of mozilla, and evolution and make a fresh new install.

---

### Post by polmir on 2008-07-02
> ...a fresh new install.Why new installation?

We need information about installed in the system kernels.```
dpkg -l | grep $(uname -r)
```And the contents of the file```
cat /boot/grub/menu.lst
```

---

