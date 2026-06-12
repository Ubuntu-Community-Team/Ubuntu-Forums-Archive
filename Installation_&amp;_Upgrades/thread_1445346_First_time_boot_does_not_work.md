---
title: "First time boot does not work"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by dinkarinjosh on 2010-04-02
Hi, 

I am a novice to ubuntu. I installed it yesterday and booted it through usb(after following instructions from the forum itself).My problem is that OS is booting just fine (as I can hear those drums beating) but there is no display. I have read the forums for the same problem , it says to press Alt+Clt+F1 to get the terminal. O tried that too but there is no display whatsoever just the blank screen. 

I am using Lenovo notebook and i have installed ubuntu 9.10 and i have a dual boot the other one being win vista. Please help

---

### Post by oldfred on 2010-04-02
Are you getting any error messages. Is this a wubi install inside Vista or a dual boot with separate partitions?

---

### Post by TheNerdAL on 2010-04-02
> **oldfred said:**
> Are you getting any error messages. Is this a wubi install inside Vista or a dual boot with separate partitions?

It's on a usb flash drive.

---

### Post by TheNerdAL on 2010-04-02
Is the blank screen black or another color? "If you just get a black screen when running from USB, using the setting "Discarded on shutdown, unless you save them elsewhere" in usb-creator might help"

I searched on my favorite site called Google and I found this: [http://forum.eeeuser.com/viewtopic.php?pid=658619](http://forum.eeeuser.com/viewtopic.php?pid=658619) That might be helpful.

---

### Post by oldfred on 2010-04-02
Have you in BIOS set usb as first boot or used f2 or f12 or whatever to choose to boot the usb harddrive? It may have installed grub to the sda internal drive also.

You can run this from the livCd.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by dinkarinjosh on 2010-04-02
> **oldfred said:**
> Are you getting any error messages. Is this a wubi install inside Vista or a dual boot with separate partitions?


Hey, thanks for the reply. No it does not give any error message. It just does not show anything (a blank screen) though i hear the sounds of the drums , suggesting that the boot is successful.

---

### Post by oldfred on 2010-04-02
Then we are past grub and into booting. This is often a video disp problem. If you  are not getting a grub menu try holding down the shift key continuously after BIOS boot and see if you can get a menu. Try booting from the recovery mode.

And welcome to the forums.

---

### Post by dinkarinjosh on 2010-04-02
> **oldfred said:**
> Have you in BIOS set usb as first boot or used f2 or f12 or whatever to choose to boot the usb harddrive? It may have installed grub to the sda internal drive also.

You can run this from the livCd.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

I have set USB as my first boot device

---

### Post by dinkarinjosh on 2010-04-02
> **oldfred said:**
> Then we are past grub and into booting. This is often a video disp problem. If you  are not getting a grub menu try holding down the shift key continuously after BIOS boot and see if you can get a menu. Try booting from the recovery mode.

And welcome to the forums.


I do not know whether it would work or not (as i have yet to try) but i am really happy for the speedy reply and the warm welcome to the forums... thanks...

---

### Post by dinkarinjosh on 2010-04-03
> **dinkarinjosh said:**
> I have set USB as my first boot device

I tried to boot from CD, it showed me the selection menu. It boots just fine , but there is no display, i have tried holding down the shift key and Clt+Alt+F1, but it does not work.

any ideas??

---

### Post by oldfred on 2010-04-03
I think it is the f6 key when the menu is up that gives additional boot options. Many of those options are related to special video modes to get the system to work on systems that need non-standard video or interrupt settings.

---

