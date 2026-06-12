---
title: "No Main Page?"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by ughhhmathisss on 2008-04-02
Ive tried many times to get this to work, but idk? I think im doing it right. Ive put in the Live CD of Gusty Gibbons, it boots no problem. It goes select screen, I choose "Install Ubuntu" after it looks as if it could have possbily glitched? then fixes itself and goes to the loading page. The little orange bar never starts moving any faster at all and after 5 mins or so, the screen goes black leaving me with a little flashing white box at the top left hand corner.

Help me please?

---

### Post by ridgeland on 2008-04-02
With the screen at the flashing white box try
[Alt]+[Ctrl]+[F1]
anything?

---

### Post by ughhhmathisss on 2008-04-03
I got a screen that says [    0.000000] ACPI: no DMI BIOS year, acpi=force is required to enable ACPI Loading please wait...


????

---

### Post by Partyboi2 on 2008-04-03
When you boot the live cd when you get to the main menu screen press F6 this will allow you to add acpi=force to the boot options to see if it works. At the end of the line add
```
acpi=force
``` then enter.

---

### Post by ughhhmathisss on 2008-04-03
Ok i did that, somthing happend. It did as normal, i got to the loading screen but after id say a minute? it came up with a screen that said

 "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
  Enter 'help' for a list of built-in commands."

  (initramfs)

is this supposed to happen?

---

### Post by ridgeland on 2008-04-03
hi ughhhmathisss,
Here is something else to try for info.
After [F6] delete the "--" and the word "quiet" then add "acpi=force" to the end like Partyboi2 suggests.
You should get a splash with orange text of progress under it.  How much does it say?
To get even more text take out "splash" too.  The screen will stay black&white and you get more messages.  What are the last few before it dies?
I cannot promise that will help but I'm curious.
Also what hardware are you using?  How old, what processor, how much RAM, what kind of monitor and video driver?
I looked in Synaptics for BusyBox.  Looks like it provides some basic Unix commands.  My only experience with an acpi issue is with old hardware with low ram.

---

### Post by raaj_bharath on 2008-04-03
may be that your hardware is not compatible with the operating system.
but mostly this does not happen!

---

### Post by ridgeland on 2008-04-03
Linux Google for "DMI BIOS year"
found
[http://kerneltrap.org/mailarchive/linux-kernel/2007/3/6/62728](http://kerneltrap.org/mailarchive/linux-kernel/2007/3/6/62728)
and more.  They talk about DMI and ACPI problems with embedded x86 machines.  I think this is heading toward a hardware issue.
Next step is to try other Ubuntu CDs. Like maybe:
Ubuntu Alternate
Xubuntu
Xubuntu Alternate

---

