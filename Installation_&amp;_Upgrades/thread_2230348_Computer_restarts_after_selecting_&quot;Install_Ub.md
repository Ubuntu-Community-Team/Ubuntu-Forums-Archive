---
title: "Computer restarts after selecting &quot;Install Ubuntu&quot; or &quot;Try Ubuntu without install&quot;"
date: 2014-06-18
forum: Installation &amp; Upgrades
---

### Post by kgbarrington on 2014-06-18
Greetings!

I am operating on Windows 7 32bit. I downloaded ubuntu-14.04-desktop-i386.iso and used unetbootin to place the iso on a 16gb USB. I restarted my computer and booted from the USB drive. When the first screen appears for Ubuntu options (Help, Try with out installing, Install Ubuntu, etc) my computer just restarts after selecting try with out installing our install Ubuntu. Any suggestions? I also did a Md5 check to verify my iso integrity (its all good). 

Thanks in advance.

---

### Post by sudodus on 2014-06-19
Welcome to the Ubuntu Forums :-)

Are you sure you are running 32-bit Windows?
Are you running BIOS and not UEFI?
Can you check if the USB drive can boot another computer?

If you specify your computer, it will be easier to help.

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by kgbarrington on 2014-06-19
Sudodus, thank you for responding. 

I am sure I am on windows 7 - 32 bit.

I have a dell xps 630
CPU: Intel Core 2 Duo CPU E8400 @ 3.00GHz 3.01GHz
Ram: 4.00 GB
Graphics card: AMD Radeon HD 5800 Series
Wifi: None, connected directly to router via LAN cable.

As far as UEFI vs BIOS I am not sure. When my computer restarts it says press F12 for boot menu, which I assumed is the BIOS. 
Also, I do not have a second computer to test from.

Thanks in advance. I appreciate the help :)

---

### Post by sudodus on 2014-06-20
With 32-bit Windows we can be rather sure you are running in BIOS mode.

You have checked the md5sum, and Unetbootin is usually reliable to make USB pendrives. If possible, can you visit a friend, relative or ask a colleague to test booting in their computer? It is important to be sure the pendrive is working properly (the pendrive itself might be a bad booter or you might need another method to make it bootable).

But the main problem might be the graphics card or some other hardware for example ACPI. There are two ways to get further,

- try with some boot option, start with **nomodeset** but also other options (more than one at the same time is possible). See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

- try the special boot option **text**, to avoid a graphical desktop environment
- ***remove*** the standard boot options **quiet splash** and try while booting again

---

### Post by kgbarrington on 2014-06-20
Thanks again for the response. I used a CD instead of USB drive. Worked just fine. No issues. Must be the USB device. 

I appreciate all your help.

Writing to you from ubuntu :)

---

### Post by sudodus on 2014-06-20
Congratulations :KS

I'm glad you found a solution. Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

If you need more help later on, please start a new thread with a relevant title.

---

