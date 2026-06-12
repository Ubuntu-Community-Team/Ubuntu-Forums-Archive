---
title: "CD wont boot to install"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by Beyla on 2008-08-07
Hi,

I downloaded Ubuntu recently and burned it to a cd (checked for cd integrity and it was fine) and I rebooted to boot from the cd but I got an error message when I selected "install Ubuntu". 

I checked here and it suggested changing quiet splash-- with a couple of commands (nothing, noapic nolapic, acpi=off, irqpoll, lapic pci=routeirq) I tried all of them and none of them worked.

Was wondering if anyone else had any other ideas or if there was a way to install Ubuntu straight from vista desktop?

---

### Post by overdrank on 2008-08-07
> **Beyla said:**
> Hi,

I downloaded Ubuntu recently and burned it to a cd (checked for cd integrity and it was fine) and I rebooted to boot from the cd but I got an error message when I selected "install Ubuntu". 

I checked here and it suggested changing quiet splash-- with a couple of commands (nothing, noapic nolapic, acpi=off, irqpoll, lapic pci=routeirq) I tried all of them and none of them worked.

Was wondering if anyone else had any other ideas or if there was a way to install Ubuntu straight from vista desktop?

Hi and welcome, could you give us some system specs? Then you may want to do a checksum on the iso 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
You may also look at Wubi for install within windows.

---

### Post by Beyla on 2008-08-07
Thanks for the quick reply. I'm using:

q6600 quad core intel cpu
evga 780i nforce mobo
9800 nvidia gtx
4 gbs of ram
and running windows vista 64bit

---

### Post by overdrank on 2008-08-07
What was the error you received? With the graphics card you may have to use the F4 option.

---

### Post by Beyla on 2008-08-07
I cant remember the exact error, I'll try again and try the f4 option as well, thanks

---

### Post by prshah on 2008-08-07
> **Beyla said:**
> or if there was a way to install Ubuntu straight from vista desktop?

Yes actually, you can; start vista, put in the ubuntu cd, and look for an option in the autostarted program called "Install within Windows" (words to that effect, I think it's the second button on the screen.)

This is OK for a short term measure, but in the long run, you'd probably want to go full ubuntu; but see if wubi (install within windows) works for you at first.

---

