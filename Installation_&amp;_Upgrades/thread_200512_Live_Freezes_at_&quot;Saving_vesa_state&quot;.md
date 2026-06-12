---
title: "Live Freezes at &quot;Saving vesa state&quot;"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by littletone2002 on 2006-06-20
I've been trying to run Ubuntu Live for a week now and after:

- Doing a checksum to make sure my iso wasn't corrupt
- Reburning the CD at 4x because at 12x it would corrupt the disk
- Doing the whole noapic nolapic command

Finally the system looks like it's starting to load only to freeze at the following

cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory
Saving Vesa State 

and then nothing. The only fix I've found was [[COLOR="Red"]Here[/COLOR]]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-April/017581.html") but it says that you need to boot in recover mode and make changes to some code. I can't do this because I'm trying to boot the live cd. Can anyone help?

---

### Post by littletone2002 on 2006-06-21
*bump* Fix anyone?

---

### Post by bennysp on 2006-06-24
Has anyone gotten this to work?  I am having the same exact problem. 

Thanks
Ben

---

### Post by bennysp on 2006-06-24
I am trying the "alternative" cd and will let everyone know how it turns out.  I was using Breezy and it was working just fine until I upgraded to Dapper.  Unfortunately, I re-partitioned and so I am using the alternative method to get Ubuntu installed and hopefully try the methods from littletone2002's link for the SAVE_VBE_STATE=false setting.

Ben

---

### Post by bennysp on 2006-06-24
Well, I have the Ubuntu installed but the above did not help.  I just sits with a cursor blinking.  Any help would be appreciative.  I have enabled noapic, nolapic, nodma acpi=off vga=771.... not sure what else to do.

Ben

---

### Post by bennysp on 2006-06-25
I finally got it working...  I installed with the alternative CD and then put the following boot options on.

noapic nolapic nodma acpi=off vga=771

I also had problems with my X server, so I had to turn off gdm from starting up.  That is resolved now by editing xorg.conf and making sure the driver says "sis".

Ben

---

