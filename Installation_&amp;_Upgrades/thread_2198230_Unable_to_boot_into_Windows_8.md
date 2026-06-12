---
title: "Unable to boot into Windows 8"
date: 2014-01-07
forum: Installation &amp; Upgrades
---

### Post by kevinpinga52 on 2014-01-07
I have an Acer Aspire V3-571g and it has Windows 8 on it.
I wanted a dual boot so I installed Ubuntu alongside it. 
After installing, I can boot into Ubuntu but not into Windows 8.

Here's the error I get when I try to boot into Windows 8:

```
File: \Boot\BCD
Status: 0xc000000c
Info: the boot configuration data for your pc is missing or contains errors
```

I tried running boot-repair but it still has not work. [http://paste.ubuntu.com/6711446](http://paste.ubuntu.com/6711446)

I've attached an image of Gparted of my current system:

[IMG]http://i.stack.imgur.com/9pJk6.png[/IMG]

I'm new to this and I'd really appreciate your help.

Thank you!

---

### Post by oldfred on 2014-01-07
Please attach screenshots not post in line. Not everyone has highspeed Internet.
You can easily attach with the advanced editor and paperclip icon in edit panel.

(KevenP in askubuntu?)

You will probably have to convert drive from gpt to MBR(msdos). Windows only boots from gpt drives with UEFI, so you may have had a hybrid MBR/gpt. 
Ubuntu will boot from gpt with BIOS or UEFI. 
And both Windows and Ubuntu only boot from MBR drives with BIOS.

       [URL="http://www.rodsbooks.com/gdisk/hybrid.html"]http://www.rodsbooks.com/gdisk/hybrid.html

[/URL]
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

