---
title: "Install Ubuntu,ACPI problems (what is ACPI ?)"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by SSStylish on 2010-11-03
I have an older machine **(AMD 3000 2ghz, 1.5G Ram, fx 5200, phoenix award bios 2003 )** and I want to install **Ubuntu 10.10** but when i put the live cd  20 secs after boot up it freezes and I need to restart the computer (tried Live cd and installed Ubuntu and freezes 20-30 sec after boot up).I know this is ACPI related problem.

But with Ubuntu 8.04 I do not have these problems, it seems that the ACPI drivers(or whatever controls that thing o.O) are working fine.
lI can play the live cd without ACPI = off, and the live cd works normally (i read somewhere that there wre some ACPI changes in,or after the **8.04**,so i tried the 8.04 and it worked without acpi=off, btw 6.06 (Drapper Drake) also gave me problems with ACPI), but  because 8:04 is slightly outdated version and i love  10:10 (looks beautiful,i like the new features, and i heard there were some performance improvements ? o.O) ... 

And I want to ask if there is a chance to install Ubuntu 10.10 with ACPI = off, or to disable  ACPI in Bios  (now do not know whether it will harm the computer , I do not know whether it is necessary or critical feature ?)... and what precisely does ACPI do?
If someone knows how to fix this please tell me, already spent one year wonder how to install a new version of Ubuntu with or without the ACPI ...**it's really giving me a hard time** :(

Or should i stick with 8.04 if it is a good version of Ubuntu(although the gui looks bad ,i like the 10.10),and can i tweak 8.04 so it gives better performance,and looks like 10.10?

---

### Post by sikander3786 on 2010-11-03
Just found this.

[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

> There is much less state information for the BIOS to retain and manage because the OS manages it. This leads to a simpler implementation at the BIOS level.

It is a feature built into the Linux kernel. If you are able to boot the 10.10 live CD with acpi=off, install it and you can later make those changes permanent in /etc/default/grub, no harm at all.

---

### Post by SSStylish on 2010-11-04
THX man !
Great tip it really helped me :D
I was just wondering why ubuntu 8.04 live cd works flawlessly without acpi=off,and the newer versions don't o.O
And can you be more specific about making these changes permanent?(I'm new into this :D)
I don't want to disable acpi in bios because i want to dual boot(windows xp).
THANKS again !

---

### Post by SSStylish on 2010-11-04
> **sikander3786 said:**
> Just found this.

[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)



It is a feature built into the Linux kernel. If you are able to boot the 10.10 live CD with acpi=off, install it and you can later make those changes permanent in /etc/default/grub, no harm at all.

How to make acpi=off changes permanent,so after the reboot it doesnt freeze?
Making a change to survive reboots,and change to survive upgrades,because i read somewhere that after kernel or grub updates the changes might reset ?

---

### Post by sikander3786 on 2010-11-05
To make that apci=off permanent, edit the grub file by

```
gksudo gedit /etc/default/grub
```

Navigate to the line that looks like,

```
GRUB_CMDLINE_LINUX=""
```

And put acpi=off in there.

```
GRUB_CMDLINE_LINUX="acpi=off"
```

Save and close that file.

Now update grub by running,

```
sudo update-grub
```

And restart to see if it worked.

---

### Post by Lebuin on 2010-11-09
I had similar problems, and ubuntu works with acpi=off. However, this also means that I cannot see the battery status, set the brightness of the screen. Also, my fan works non-stop.
How can I solve these problems?

---

### Post by Lebuin on 2010-11-09
I had similar problems, and ubuntu works with acpi=off. However, this also means that I cannot see the battery status or set the brightness of the screen. Also, my fan works non-stop.
How can I solve these problems?

EDIT: excuse me for the double post

---

### Post by ImaLamer on 2010-11-09
> **Lebuin said:**
> I had similar problems, and ubuntu works with acpi=off. However, this also means that I cannot see the battery status, set the brightness of the screen. Also, my fan works non-stop.
How can I solve these problems?

Have you tried other options found here:

[https://help.ubuntu.com/community/BootOptions#Kernel Options]("https://help.ubuntu.com/community/BootOptions#Kernel Options")

Because the issue may be instead related to the IRQ management and so forth. I would try, one at a time, some of those various settings to see if you can boot without turning the ACPI functions off. This worked on my laptop (HP dv9000) - but your mileage may vary.

---

