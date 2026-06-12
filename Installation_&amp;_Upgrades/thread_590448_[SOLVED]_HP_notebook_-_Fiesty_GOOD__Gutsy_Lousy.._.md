---
title: "[SOLVED] HP notebook - Fiesty GOOD / Gutsy Lousy.. Help please"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by granz on 2007-10-24
Gutsy  Boot Problem,related to  acpi=off  ???????  
HP tx 1001au (Turion TL-60 2.0GB, 120GB Sata HDD, 1 GB ram, nVidia GeForce Go 6150,  )
It is dual boot with Vista Home Premium, was working fine with 'Fiesty' .. no tweaking needed (it 'just worked'). Fiesty was real good.
As Gutsy can read/write to ntfs better, and media codecs are handled better. I want to upgrade ..
I did a clean install of Gutsy Gibbon (seemed successful) ...rebooted, and as soon as it finished the 'loading bar' the screen greyed out and it froze.
I googled and the only 'fix' I could see that might work was a reference to editing Grub. 
I did that ... with a live 'puppy linux' CD (the Ubuntu CD 'greyed out' too ) adding, acpi=off
This sort of worked, I can now boot into the desktop BUT only for about 30 seconds, then I lose the usb  mouse (but touchpad works) and I lose eth0 connection.
I'm not sure what to do now, this has got beyond my experience .... I'm disappointed, I thought Ubuntu was getting better.
Any help appreciated ... tell me what info to get from a terminal to help identify the exact problem please. 

by the way ... I have an HP Presario R3211AP ( R3000 series, 3 years old) Laptop, and Gutsy works just fine, I'm writing this on it. So it's not ALL HP lap/notebooks, but obviously a lot. The newer ones ??

---

### Post by granz on 2007-10-25
no-one knows ????

---

### Post by granz on 2007-10-25
added   ...   noapic nolapic   to the end of the kernel line in 'boot/grub/menu.lst'.
Starts and seems to run ok now ... but NO SOUND (not sure what else )

... I'll mark this thread as sort of solved now.
and move on to the NEXT problem   :-)

---

