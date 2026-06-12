---
title: "won't reboot"
date: 2010-04-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SlugSlug on 2010-04-27
Upgraded from Jaunty, and now I cannot reboot, if I issue reboot command the OS will reboot but not the PC...

---

### Post by SlugSlug on 2010-04-28
Sorry to bump but am I the only one with this problem?

---

### Post by MacUntu on 2010-04-28
Do you have kexec-tools installed? If so, what's in '/etc/default/kexec'?

---

### Post by SlugSlug on 2010-04-28
not sure if the -tools is installed I have a kexec command,

cat /etc/default/kexec
# Defaults for kexec initscript
# sourced by /etc/init.d/kexec and /etc/init.d/kexec-load

# Load a kexec kernel (true/false)
LOAD_KEXEC=true

# Kernel and initrd image
KERNEL_IMAGE="/vmlinuz"
INITRD="/initrd.img"

# If empty, use current /proc/cmdline
APPEND=""

---

### Post by MacUntu on 2010-04-28
```
# Load a kexec kernel (true/false)
LOAD_KEXEC=true

```

Change this to false and your box should reboot again (after rebooting once).

---

### Post by SlugSlug on 2010-04-28
Thanks I will try that tonight, 

Any idea why this happened? what is this exec do I need it?

---

### Post by MacUntu on 2010-04-28
If you have to ask, you probably don't need it. In my case kexec-tools got installed when I installed the tools necessary to compile my own kernel.

Forgot: if it doesn't work you maybe need to run 'sudo update-initramfs -u'.

---

### Post by SlugSlug on 2010-04-28
right yer, I was messing about trying to compile a kernel before I upgraded.

Cheers for your help

---

