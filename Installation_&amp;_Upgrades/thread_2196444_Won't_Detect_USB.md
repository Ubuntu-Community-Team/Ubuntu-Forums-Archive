---
title: "Won't Detect USB"
date: 2013-12-29
forum: Installation &amp; Upgrades
---

### Post by blake4 on 2013-12-29
**Computer**: [COLOR=#444444][FONT=UbuntuRegular]Acer Aspire M5-583P-6428
**Problem**: I have Ubuntu installed fine on my computer, nothing else. But on USB I have **Windows 7 Ultimate which I want**. But my computer won't detect the USB and won't install Windows but on another computer USB works fine. I did a GRUB update but no luck. 

Laptop has no CD insert place.[/FONT][/COLOR]

---

### Post by sudodus on 2013-12-29
There can be many causes for your problem. Start by reading the following wiki page (particularly the chapter 'Prerequisites' and 'Booting the Computer from USB')

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

and come back for further questions/comments/tips/discussion

---

### Post by blake4 on 2013-12-29
Well, I have Ubuntu I'm trying to install WINDOWS. But what I'm saying is that the computer isn't detecting my USB at all. Other computers are, why? Other Windows computers detect a flash drive that has windows on it. My laptop that now has Ubuntu on it won't detect flash drive that has Windows on it.

---

### Post by sudodus on 2013-12-29
Some possible reasons are explained in that wiki page.

- What pendrive is it (brand name, model)?

- Have you tried to change the settings in the uefi/bios menu system, to give priority to booting from USB or making the USB drive the first 'hard disk drive'?

- Can you try with another pendrive? Sometimes a certain pendrive will not cooperate with a certain computer (mobo or USB system). I have recent experience of that problem (helping my brother during Christmas).

---

### Post by sudodus on 2013-12-29
In your particular case there is also the '40_custom' method, because  you have a working linux system with a grub menu. See this link for a  background about grub

[Scripts: /etc/grub.d/]("https://help.ubuntu.com/community/Grub2/Setup#Scripts:_.2BAC8-etc.2BAC8-grub.d.2BAC8-")

Add the following text to the file **[FONT=courier new]40_custom[/FONT]**[FONT=arial] (notice that it is important to leave the first lines, that come with the file)

```

menuentry "External drive (on hd1) if no eSATA drive connected. edit if necessary" {
        insmod part_msdos
        insmod fat
        set root='(hd1)'
        drivemap -s (hd0) ${root}
        chainloader +1
}

```

and run the command

```
sudo update-grub
```[/FONT]

Then  you will get a grub menu option to boot from a second drive (hd1),  which could be a USB pendrive. If another drive is hd1, you can edit the  line to (hd2) etc.

---

