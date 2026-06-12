---
title: "new install"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by mikebl on 2012-10-18
Right now I'm using Win7. I have a seperate drive which is empty. I plan on installing 12.10 on that drive. My question is with 12.10 installed, at start-up of my computer will I get a screen that gives me the option of which OS I want to use?

Thank you

---

### Post by williejones on 2012-10-18
> **mikebl said:**
> Right now I'm using Win7. I have a seperate drive which is empty. I plan on installing 12.10 on that drive. My question is with 12.10 installed, at start-up of my computer will I get a screen that gives me the option of which OS I want to use?

Thank you
  
Yes, you will boot into GRUB, which then gives you the option to select which operating system to load.  I also want to mention that you need to make sure the bootloader (Grub) is installed on the drive you install Ubuntu (example If you install Ubuntu to /Dev/Sdb1 then grub would need to go on /Dev/Sdb)

Also in the installation screen you may need to select "Something Else" to get the option to install to your second drive.













a

---

