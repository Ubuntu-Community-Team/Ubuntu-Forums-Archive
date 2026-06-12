---
title: "Blank screen problem when &quot;Try Ubuntu&quot; from USB &quot;live&quot; bootable stick."
date: 2022-10-18
forum: Installation &amp; Upgrades
---

### Post by softfoot on 2022-10-18
I have created a bootable USB stick with Rufus and "ubuntu-22.04.1-desktop-amd64.iso" and it works OK on my laptop but not on two machines that have NVIDIA GeForce 210 video cards fitted. I see the "grub" messages but when I choose "Try or inastall" the boot continues but all I get is a blank screen and a message from the monitor about "frequency out of range".

If I remove the NVIDIA card it works OK but I cannot get the screen resolution I need (1920x1080) for the trial on the embedded graphics card.

Is there a way around this ???    I do NOT want to install Ubuntu on these machines yet if I can possibly help it.

I tried editing grub.cfg (to force the resolution) on the flash drive as suggested elsewhere but it had no effect at all.

Regards,
Dave

---

### Post by &amp;KyT$0P# on 2022-10-18
Does it work with the "safe graphics" option or booting with [FONT=Courier New]nomodeset[/FONT] boot parameter?

---

### Post by ActionParsnip on 2022-10-18
Try the boot option:
```

nouveau.nomodeset=0

```
or
```

nouveau.blacklist=0

```

---

### Post by MAFoElffen on 2022-10-18
What they are talking about (instructions):
**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**

---

