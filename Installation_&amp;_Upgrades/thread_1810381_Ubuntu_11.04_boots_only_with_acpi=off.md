---
title: "Ubuntu 11.04 boots only with acpi=off"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by alexPhil on 2011-07-22
SInce I installed 11.04 I need to change with a live CD and chroot, the grub bootloader to acpi=off. If not, the system will not boot. After the Grub message at start, the screen is just black. That's it...
Even when booting from the Ubuntu DVD, I have to press F6 and choose acpi=off, else I can not start the installation.
With Ubuntu 10.04 and 10.10 There was not problem like this. It just works...

So I am really not wondering, why many people don't like Linux and prefer WIndows. Because you need to be a specialist to change the kernel options for booting.

---

### Post by 2F4U on 2011-07-23
This has not much to do with Linux. It has to do with hardware vendors  implementing features that don't stick to the specification. It is the  same hardware vendor who then creates the device drivers for Windows and  its obvious that they work with Windows. However, this same vendor  doesn't develop drivers for Linux nor does he provide the necessary  information to Linux developers. So how is Linux supposed to work with  that hardware?

---

### Post by tommcd on 2011-07-23
> **alexPhil said:**
> 
So I am really not wondering, why many people don't like Linux and prefer WIndows. Because you need to be a specialist to change the kernel options for booting.
2F4U said what I wanted to say about your hardware.

As for being a "specialist", I have absolutely no technical background at all. In fact, I purchased my first computer 9 years ago when I was 42 years old. At that time I was so clueless I did not even know what Internet Explorer (or any web browser) was.
 I have since managed to learn how to use many linux distros, including Slackware.

You you need to understand that linux is not Windows. Everything you know about Windows computers means precisely *nothing* when starting with linux.
I am sure that you did not learn how to use Windows in one day. You likely accumulated knowledge over some time. The same will be true for linux.
How much you decide to learn about linux is entirely up to you.

---

### Post by IWantFroyo on 2011-07-23
I had this same exact problem with 10.10. 

Try booting with pci=noacpi,  and put acpi=off/pci=noacpi in /etc/default/grub so they start automatically. Put it between the ""s.

---

