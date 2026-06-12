---
title: "Acer Aspire A315 Install Notes"
date: 2017-12-12
forum: MINT
---

### Post by friedchips2 on 2017-12-12
This may or may not be the right place for this, but I wanted to document some of this and let others know my experience.

First I had to enable F12 at boot to even have option for USB boot. I also created a supervisor password to allow disabling secure boot.

I installed to hard drive and picked EFI partition for grub. I left windows installed for time being which ended up being huge because I found issues with freezing that I hoped a firmware update would help.

After updating firmware I found I was locked out of BIOS! Firmware update borked my password. I nearly returned the laptop after Acer says I have to send it back and pay for password removal.

After a lot of trying things I figured out that the update changed my password to all CAPS..... No idea why. Dumb as all get out. Whatever. Glad I got it figured out. Not thinking I'll ever buy Acer again after this experience with them treating me like I just forgot my stuff.... Firmware doesn't change passwords they say. Not true. I used my go to password so I knew I wouldn't forget.

So far everything works out of box. Not sure if I'm out of the woods on freezing yet. So far so good. I'll keep you guys posted. FYI this is a mint install. Hope this helps someone. Especially the password deal.


FriedChips.

---

### Post by QIII on 2017-12-12
Moved to MINT

---

### Post by friedchips2 on 2017-12-12
Update.....

Still have an issue with random freezing. A little baffled on the cause and where to start. Any suggestions are appreciated.

---

### Post by friedchips2 on 2017-12-26
Update. All is well for me here. I have updated to the kernel files for ubuntu from  [HTML]https://github.com/M-Bab/linux-kernel-amdgpu-binaries[/HTML]. I also disabled the network manager applet based on reports of it crashing cinnamon during network status changes. Have Been running good and solid after some work on this Laptop. If there's any way I can help anyone else who has a similar lappy please don't hesitate to ask.

---

