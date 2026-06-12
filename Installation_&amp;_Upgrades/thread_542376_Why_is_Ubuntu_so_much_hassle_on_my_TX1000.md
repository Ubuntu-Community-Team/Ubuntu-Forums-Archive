---
title: "Why is Ubuntu so much hassle on my TX1000?"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by i_love_windows_vista on 2007-09-03
It can't even boot the live cd....

---

### Post by scxtt on 2007-09-03
cause of your username . . . ;)

what brand/model laptop?  what are the specs?

---

### Post by Pumalite on 2007-09-03
Post specs. 256 MB RAM>Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by i_love_windows_vista on 2007-09-03
HP TX1000la (Latin America)

amd turion 64 x2 1.6ghz
2gb ram
120gb drive
dvd burner

---

### Post by Pumalite on 2007-09-03
Your memory is OK. You might graphics problems. Graphics?

---

### Post by scxtt on 2007-09-03
what happens when you put the CD in and boot the laptop?  are you sure it's set to boot from CD/DVD?  if so, are you getting any Ubuntu specific screen?

what video hardware?

---

### Post by i_love_windows_vista on 2007-09-03
Graphics is an nVidia Geforce Go 6150 with shared memory.

No error, I hear the disc spinning but it does nothing.  If I take the disc out and reboot it goes to Windows fine.

---

### Post by Pumalite on 2007-09-03
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by i_love_windows_vista on 2007-09-03
Thanks Pumalite, but obviously if the disc was not a boot disc it would ignore it during the boot cycle, not try and fail to boot off it without an error.

---

### Post by Gremlinzzz on 2007-09-03
Sounds like the drive cant read the cd maybe you should try burning a new one.

---

### Post by i_love_windows_vista on 2007-09-03
I'll try burning it again.  Why can't it recover or bail gracefully if there's an error with the disc...

---

### Post by Spectre31337 on 2007-09-11
when you try to boot do you see the Ubuntu splash screen?

If so then the issue is your video card and that is an easy fix

select F6 on the bootup slash

type ```
vga-791
``` at the end of the line you should be good to go. Once you have installed Ubuntu before restarting:

```
sudo gedit /boot/grub/menu.lst
```

Find each line that start with Kernal and add ```
vga=791
``` to the end of it

---

### Post by startlinuxtoday on 2007-09-11
Why Is Windows So Much Of A Problem On Anything At All?

---

### Post by spikermn on 2007-09-14
When starting up the live cd, press f6 and add the following to your boot options;

```
doscsi noapic
```

Until I updated my kernel, I had to use those options to boot even after I installed ubuntu. I have the TX1000 CTO or whatever it is called. Now I don't use those options anymore, The main things I can't get to work now are hibernate and suspend. The webcam doesn't work either. Mine didn't come with a fingerprint scanner because HP told me they couldn't add it and a webcam because of space limitations. A month later, my dad ordered the same laptop and he has the fingerprint reader, webcam , mic, etc. Stupid HP. Anyway, I have everything else working fine.

---

### Post by EddieGuarraro on 2008-01-08
Hey everyone, there is an EXCELLENT forum post on the TX1000 series. I have ubuntu working BEAUTIFULLY on it, way better then even XP. The only thing not working is hibernation.

[http://ubuntuforums.org/showthread.php?t=442483&highlight=hibernate+tx1000&page=52](http://ubuntuforums.org/showthread.php?t=442483&highlight=hibernate+tx1000&page=52)

Search for the ACPI boot flags, i didn't have to use irqpoll or noapci after i got the correct ACPI boot flag.

---

