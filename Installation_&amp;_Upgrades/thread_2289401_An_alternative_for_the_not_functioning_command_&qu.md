---
title: "An alternative for the not functioning command &quot;halt&quot; in Grub?"
date: 2015-08-03
forum: Installation &amp; Upgrades
---

### Post by siggi2 on 2015-08-03
Hi,

I have a grub menu to boot from a live USB stick
```
menuentry "lubuntu-14.04.2-desktop-amd64.iso on sdb2" {
	set root=(hd0,2)
	set isofile="/lubuntu-14.04.2-desktop-amd64.iso on sdb2"
	loopback loop (hd0,2)$isofile
	linux (loop)/casper/vmlinuz.efi root boot=casper persistent iso-scan/filename=${isofile} locale=en_US bootkbd=de console-setup/layoutcode=de quiet splash
	initrd (loop)/casper/initrd.lz
        }

menuentry "boot from internal HD " {
set root=(hd1)
drivemap -s (hd0) (hd1)
chainloader +1
}

menuentry "reboot " {
reboot
}

menuentry "off" {
halt
}
```
Everthing works fine except the last command "halt" in the menuentry "off". Here I get
```
unknown opcode 0x6
unknown opcode 0x12
unknown opcode 0x8a
ACPI shutdown failed
```
I have read that is a more general problem, e.g., [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=766853]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=766853")https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=766853. But I am not expert enough to follow these recipes through with all these scripts.

Is there a different Grub command that will shut off/shut down my Samsung Notebook NP300E5C-S04DE?

Thank you,

siggi

---

### Post by grahammechanical on 2015-08-03
> Is there a different Grub command that will shut off/shut down my Samsung Notebook NP300E5C-S04DE?

Not according to the Grub manual. And there is one.

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Regards

---

### Post by oldfred on 2015-08-03
I  have not acutally used it lately, I have used the reboot.
But there still is an ismod in grub.

       menuentry "System shutdown" {

 echo "System shutting down..."

         insmod halt
 halt

 }

I use these two also:
 # spacer line
menuentry " " {
set root= 
}

   menuentry "System restart" {

 echo "System rebooting..."

         insmod reboot
 reboot

 }

---

### Post by siggi2 on 2015-08-04
> **oldfred said:**
> I  have not acutally used it lately, I have used the reboot.
But there still is an ismod in grub..........

```
menuentry "System shutdown" {
      echo "System shutting down..."
      insmod halt
      halt
}

```
Does not work, I get the same error message as shown in my first post!

"spacer line" does nothing.

"reboot": thanks, but I have this already in my Grub menu.

So, I guess "halt" is from a bygone GRUB area :(

---

### Post by oldfred on 2015-08-04
I went back and tested on my system and halt  does work on my system, so must depend on UEFI/BIOS that you have.

Spacer line is just that, a blank line so you can organize menu slightly better.

---

