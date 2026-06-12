---
title: "grub chainloading, invalid or unsupported executable format"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by wconstantine on 2011-04-06
I'm at a loss at why my Backtrack Linux grub boot loader doesn't work. Ubuntu's works fine, so does Windows 7.

/dev/sda3 - primary boot loader, grub v. 0.97
/dev/sda5 - backtrack boot loader, grub v. 0.97
/dev/sda9 - ubuntu boot loader, grub v. 2

I'm chainloading because I've got three OS's installed and I don't want any interference between them when I update either OS. Backtrack and Ubuntu are encrypted.

I've attached the output of a boot loader inspection script I found on sourceforge. You have the contents of all the menu.lst files in that output among other things. 

The only loader that doesn't work is Backtrack's. I get invalid or unsupported executable format when I'm trying to chainload into Backtrack's loader. 

Would greatly appreciate some help. :)

Edit: Yikes. I just realised that this might be the wrong forum to post in. I should have done it in Backtrack's forums. I'm so used to posting in Ubuntu forums every time I have problem with Linux. Sorry!

---

