---
title: "Recieved error at boot after upgrading to Hardy"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by PseudoOne on 2008-04-26
Hi, I recently upgraded my Ubuntu Server edition to 8.04 hardy.  I used the command `sudo apt-get upgrade` to upgrade.  I am not sure whether it installed properly or not, dpkg froze when I ran dpkg --configure -a.  Now when I rebooted the server, I recieved the following lines of messages, the first one of which is normal.

Starting up ...
[                0.000000] ACPI: BIOS age ( 1998 ) fails cutoff (2000), acpi=force is required to enable ACPI
[    81.609915] RAMDISK: ran out of compressed data
[    81.610011] invalid compressed format (err=1)
[    81.613021] Kernel panic - not syncing:  VFS:  Unable to mount root fs on unknown-block(0,0)

I am unable to enter any text into the console, even in recovery mode.  Any help here please? :(

---

### Post by Partyboi2 on 2008-04-26
try adding acpi=force as a boot option. When you boot and see grub loading press esc to get to grub menu then select the kernel you are going to boot into and press "e" to edit then highlight the line starting with kernel and press "e" then at the end of the line add ```
acpi=force
```then enter then "b" to boot. If this works you will need to make it permanent in grub menu.lst

---

### Post by PseudoOne on 2008-04-26
I can't enter Grub because it's not reading the keyboard input :(

---

### Post by garton on 2008-05-02
I have this exact same problem, and acpi=force didn't help. It removed the kernel panic, instead the system gave me an error message saying that my NIC wasn't a 8139 chip and that it would try 8139too instead. It froze there.

---

