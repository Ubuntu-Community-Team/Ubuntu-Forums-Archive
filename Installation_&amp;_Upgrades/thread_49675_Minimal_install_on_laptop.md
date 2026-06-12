---
title: "Minimal install on laptop"
date: 2005-07-17
forum: Installation &amp; Upgrades
---

### Post by vdorta on 2005-07-17
I want to dual-boot my current XP with Ubuntu on my old 333MHz laptop on which I only can free up about 2GB. I have searched and found two different and helpful threads. One of them suggests entering "server" at the install prompt (I will then install only the applications I want); the other thread suggests entering "linux archive-copier/copy=false" (so that the installer doesn't cache some 300MB of data to the hard drive).

1. In order to minimize use of valuable hard drive space, can I enter **both** the above suggestions at the install prompt?

2. The "server" thread then suggests to "sudo apt-get update" followed by "sudo apt-get install x-window-system-core xfce4 synaptic gnome-sudo gdm acpi acpi" (I like xfce and want to install some Gnome applications, so this looks perfect for me). However, my laptop doesn't support acpi, only apm. Should I enter apm instead of acpi? should I leave acpi off, or does it matter?

Thanks very much.

---

### Post by mingus on 2005-07-18
The acpi package is for power mgmt utilities, which is different from the acpi support in the kernel.  Not only will these utilities not work on your laptop, but probably you will need to disable acpi in your boot kernel statement.

The apm package is also utilities, which you can give a try.  APM is set up by the kernel, although with some old BIOS's it occasionally also has to be disabled.

---

### Post by vedro on 2005-07-18
ellow...

I woul sugest you that you disable acpi at the beginning of the installation. Type elxpert acpi disable and then install the system. That worked for me on my R40... Now I can use Fn+ ... buttons for on/off LCD Klaptop is working without any problem... With acpi I had some issues....

have a nice day,
vedro

---

