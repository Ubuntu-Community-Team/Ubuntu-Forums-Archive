---
title: "Ubuntu 10.10 does not boot"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by Heitor on 2011-02-20
For the first time that I tried to install Ubuntu 10.10, it did not boot from the Live CD. Then I used the option "acpi=off". It worked and I installed the operating system in the computer (an ASUS A6000KM).

Now, Ubuntu is not booting from the hard drive. Maybe it is the "acpi=off" issue again?

What could I try to have Ubuntu working?

---

### Post by Quackers on 2011-02-20
Hold down the shift key whilst booting and you should see the grub menu appear. The top item will be your Ubuntu sysyem and it will be highlighted. Press the "e" key and on the next screen, navigate to the end of the line which says "quiet splash", then delete those two words and then type in "acpi=off" (without the quotes) and press ctrl+X to reboot.

---

### Post by sikander3786 on 2011-02-20
> **Quackers said:**
> Hold down the shift key whilst booting and you should see the grub menu appear. The top item will be your Ubuntu sysyem and it will be highlighted. Press the "e" key and on the next screen, navigate to the end of the line which says "quiet splash", then delete those two words and then type in "acpi=off" (without the quotes) and press ctrl+X to reboot.
And if that is successful, you will need to make the acpi=off change permanent by editing your /etc/default/grub file. Let us know how that goes so we can guide you with the later part ;-)

---

### Post by Heitor on 2011-02-20
Thank you, guys.
It worked, but Ubuntu started in text mode...
Any ideas?

---

### Post by Heitor on 2011-02-20
> **sikander3786 said:**
> And if that is successful, you will need to make the acpi=off change permanent by editing your /etc/default/grub file. Let us know how that goes so we can guide you with the later part ;-)

I have managed to start Ubuntu with the GUI.

Please, could you help me with the /etc/default/grub file?

---

### Post by sikander3786 on 2011-02-20
Edit you /etc/default/grub by,

```
gksudo gedit /etc/default/grub
```

Find this line.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Type acpi=off at the end of that line so it looks like,

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```

Save and close the file. Now run in Terminal,

```
sudo update-grub
```

There shouldn't be any errors in the output. Reboot and let us know if it was successful please.

---

### Post by Heitor on 2011-02-21
It was successful.
Thank you very much.

> **sikander3786 said:**
> Edit you /etc/default/grub by,

```
gksudo gedit /etc/default/grub
```

Find this line.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Type acpi=off at the end of that line so it looks like,

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

Save and close the file. Now run in Terminal,

```
sudo update-grub
```

There shouldn't be any errors in the output. Reboot and let us know if it was successful please.

---

### Post by Quackers on 2011-02-21
Well done :-)
The only problem with acpi=off is that it can impact on your pc's hardware. If you notice that fans are running constantly, or not at all, be careful. If your pc shuts down unexpectedly it can be caused by overheating (fans are controlled by acpi). Just keep an eye on it for a while.

---

