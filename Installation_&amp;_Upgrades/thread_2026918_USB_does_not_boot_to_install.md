---
title: "USB does not boot to install ?"
date: 2012-07-16
forum: Installation &amp; Upgrades
---

### Post by falconzx on 2012-07-16
I've downloaded the ISO file, used Unetbootin to burn the ISO to my USB and made it bootable.

But when I restart my laptop, the usb does not boot at all and just start up windows like normal (even when I press F12)

Can anyone help me please ?

---

### Post by sudodus on 2012-07-16
Welcome to the Ubuntu Forums :-)

Maybe I can help by asking some questions :-)

- What is printed on the screen after you type F12? And what did you select?

- Have you checked your BIOS menu system, if there are ways to give your USB drive priority to boot? Reboot with the USB drive connected, and check (in the BIOS menus) if it is recognized as one of the hard disk drives, and in that case put it first in the list.

- Did you check (with md5sum) that the download was good?

- Can you check in another computer, if you can boot a live system 'try Ubuntu' without installing it?

---

### Post by OM55 on 2012-07-16
Hello falconzx,

Did you remember to change the BIOS boot priority to put USB HDD (and USB key) first on the list?
If not -

1. Plug in your bootable USB (very important - it has to be plugged in) and reboot.

2. When prompted, press the hot key to enter the BIOS screen (usually, DEL, F2, or some other key combination. It will show on the screen).

3. Go to the 'Boot' menu, identify your bootable USB on the list and use the proper keys (usualy F6,F5 or arrows) to bring it up to the top position before everything else.

4. Then switch to the 'Exit' menu and 'Save' when exiting.

Now the system should boot from the USB key.

If that is not the case, please describe in detail what you are doing and what is happening and we'll try to help further.

---

