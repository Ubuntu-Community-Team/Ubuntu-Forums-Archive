---
title: "Acer 9300-3089 , Cannot Install 7.10 (BIOS Bug #81)"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by Rev_Chris on 2007-11-08
Hello,

I bought a new Acer 9300 laptop the other day , wiped Vista off and tried to install Ubuntu 7.10 ,
I see an Error pop up. "Bug #81 BIOS Error" (or something of the like.
 The live cd freezes just as the spashscreen comes (or sometimes the splashscreen finishes and goes black followed by nothing.

So i grabbed one of my 7.04 cds , which installed (it did show the Bug #81 error , but it continued anyway) 
I installed all updates and tried to install the distribution upgrade. After rebooting from the distro upgrade (and thus being at 7.10)  the splashscreen freezes and the laptop just hangs (i left it for 30 minutes , it didnt move).

Can anyone assist me in getting this install done up.

---

### Post by frank.bommeli on 2007-12-04
I can't help you, but I have exactly the same problem.
I.e., if you can solve this I'm very interested.

---

### Post by Pumalite on 2007-12-04
I'm afraid this is one of those Micro&%$ problems. Try:
DBan your drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Make one large partition of your whole hard drive and formatted ext3 ( some will say 'not needed', but believe me: it is)
Then install Ubuntu.

---

### Post by HughR on 2007-12-28
> **frank.bommeli said:**
> I can't help you, but I have exactly the same problem.
I.e., if you can solve this I'm very interested. me too.

I just bought this same model and 7.10 doesn't load properly..

I'll wander off to find out if there is a way to suppress the splash screen to see what is going on when the freeze happens.

There are BIOS updates for this computer but are only provided for WinXP, not WinVista.  I only have WinVista (that came with the machine). 
[http://support.acer-euro.com/drivers/notebook/as_9300.html](http://support.acer-euro.com/drivers/notebook/as_9300.html)

---

### Post by Partyboi2 on 2007-12-28
> **HughR said:**
> me too.

I just bought this same model and 7.10 doesn't load properly..

I'll wander off to find out if there is a way to suppress the splash screen to see what is going on when the freeze happens.

There are BIOS updates for this computer but are only provided for WinXP, not WinVista.  I only have WinVista (that came with the machine). 
[http://support.acer-euro.com/drivers/notebook/as_9300.html](http://support.acer-euro.com/drivers/notebook/as_9300.html)
If you are running the live cd, when you get to the main menu press f6 and at the end of the line you will see "splash" change it to "nosplash" (without quotes) then press enter.
If you are booting from Hard drive then when you see "grub loading..." press Esc to enter grub menu then press "e" to edit then scroll down to the kernel line and press "e" to edit then at the end change "splash to "nosplash" then enter then "b" to boot[COLOR=#ffffff][FONT=Bitstream Vera Sans Mono]ading stage1.5.[/FONT][/COLOR][COLOR=#ffffff][FONT=Bitstream Vera Sans Mono]Loading stage1.5.[/FONT][/COLOR]

---

### Post by HughR on 2007-12-29
> **Partyboi2 said:**
> If you are running the live cd, when you get to the main menu press f6 and at the end of the line you will see "splash" change it to "nosplash" (without quotes) then press enter.

Thanks.  I did go off and figure it out myself and am back to report some results.  BTW, I also  removed the "quiet" option.

Last thing on the screen is:
```
[    6.616000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
```
Note: HID stands for Human Interface Device (e.g. mouse, keyboard).
I don't know if the problem is with this module.

I tried again, this time without my USB mouse plugged in, the system still hung.  The last message was:
```
[    7.464000] squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher
```
I don't see any mention of HID in this log.

I tried the same, with the addition of "maxcpus=1".  It paused at the same location but after a delay (perhaps 30 seconds) and then proceeded.  It then hung again after much progress.  It hung after the log disappeared from the screen (I think that X actually started and then went blank).

This is not reliably repeatable.  noacpi does not clearly change things.

BTW, my system has BIOS version 1.17.  The latest version Acer has made available for WinXP is 1.20.

---

### Post by HughR on 2007-12-31
> **HughR said:**
> There are BIOS updates for this computer but are only provided for WinXP, not WinVista.  I only have WinVista (that came with the machine). 
[http://support.acer-euro.com/drivers/notebook/as_9300.html](http://support.acer-euro.com/drivers/notebook/as_9300.html)

I've updated the BIOS to v1.20, using a technique outlined here (in French): [http://www.nautile.org/Flasher-un-bios-de-portable-sous.html](http://www.nautile.org/Flasher-un-bios-de-portable-sous.html)

The BIOS bug message is still printed.
The machine still hangs with the same squashfs line on the screen.

---

### Post by HughR on 2007-12-31
The x86_64 version of the 7.10 live CD works!

I just tried it for the first time.  The screen comes up quite wrong, black and white, with no recognizable features.  Using Ctrl-Alt-F1 gets me a healthy text console.  The Ctrl-Alt-F7 gets me a nice Ubuntu desktop.

Fedora 8 Live i386 didn't work, but the x86_64 version did, mostly.  The problem that stopped me was that the X cursor was invisible.  No fun.

These observations show that something is fishy in the 32-bit world.

---

### Post by frank.bommeli on 2008-01-08
Thanks Hugh

I tried the 64 version of the 7.10 live CD it effectively brought me a little further. No everything works fine until I should have some Desktop!

Instead of having the desktop, I just get dots on the screen!
Not very funny and I still can't appreciate 7.10.

Has someone other ideas?

---

### Post by HughR on 2008-01-08
> **frank.bommeli said:**
> 
I tried the 64 version of the 7.10 live CD it effectively brought me a little further. No **[now?]** everything works fine until I should have some Desktop!

Instead of having the desktop, I just get dots on the screen!
Not very funny and I still can't appreciate 7.10.

Has someone other ideas?
You didn't say whether you tried to remedy the bad desktop using the trick I mentioned:

[LIST]
[*]wait until the system is quiescent
[*]press, together, the Ctrl-Alt-F1 key combination to switch to the first text console
[*]press, together, the Ctrl-Alt-F7 key combination to switch to desktop (X)
[/LIST]

---

