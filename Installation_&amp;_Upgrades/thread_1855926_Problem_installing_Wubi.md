---
title: "Problem installing Wubi"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by jedi1 on 2011-10-07
Hi,
I have a problem with Wubi. It was working fine until some kernel upgrade, I didn't really feel like fixing it, so I just thought I would uninstall it completely and start w new installation. However, now it is not working at all. I've tried with both Wubi 10.04 and 11.04. Both have been working fine earlier. There are no changes in the hardware.

I manage to install it if I choose acpi_workaround option, but after install it won't boot. I just get a black screen with a flashing cursor after I choose Ubuntu from grub in both normal and safe mode. There is an error before grub is loaded as well, but I can't read it, as it disappears very fast.

Here is a report of my hardware if that's any help [http://pastebin.com/HwNp9b6P](http://pastebin.com/HwNp9b6P)

Any ideas what might be wrong?

---

### Post by Rubi1200 on 2011-10-07
Hi and welcxome to the forums :)

Take a look at this thread and see if there that can help with options at boot time:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I suggest trying nomodeset.

---

### Post by bcbc on 2011-10-07
That acpi_workaround only applies to the installation process. (It's applied to the kernel that loads to run the install - it doesn't get transferred to the Ubuntu that is installed).

So you need to do it one more time to get it booting, and then try to address the issues. See post #1 in that link Rubi1200 posted. Even though this says **(not for wubi)** it is the same after the initial install.

---

### Post by jedi1 on 2011-10-23
Thanks for your replies, I have fixed the issue by reinstalling Windows. Now everything works fine without any workarounds.

---

### Post by Rubi1200 on 2011-10-24
If you found a solution please mark this thread Solved using the Thread Tools near the top of the page.

Thanks.

---

