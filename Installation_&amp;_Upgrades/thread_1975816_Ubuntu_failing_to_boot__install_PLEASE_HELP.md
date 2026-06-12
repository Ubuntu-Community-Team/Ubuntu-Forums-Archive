---
title: "Ubuntu failing to boot / install PLEASE HELP"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by decagonalist on 2012-05-07
So ive recently decide to insyltall ubuntu 12.04 because windows cannot boot.(appears as if not installed)  after like 4 tries I couldnt finish the install with a usb.so I burned a Dvd Rom with the Iso and when I select it to boot some code appears and eventually the purble screen with the ubuntu logo and five white dots. The dots continue to turn red then white again but nothing else happens. Its been like half an hour and I think it may have something to do with the previous tries in witch I got to about 40 percent and then freezes indefinately.  Is there a way I can just completely wipe everything from the boot menu?roi even need to do that?
sorry for the errors I'm on a tablet.

---

### Post by jadtech on 2012-05-07
first did you try the  alternate ISO ??

really need more details about the computer to help a lot :)

---

### Post by decagonalist on 2012-05-07
> **jadtech said:**
> first did you try the  alternate ISO ??

really need more details about the computer to help a lot :)

Didn't try the alt. The computer is a **** toshiba satellite c55d or something like that. It had win7 originally.
Also where can I get this alt Iso?

---

### Post by vVvSHADOWvVv on 2012-05-07
> **decagonalist said:**
> So ive recently decide to insyltall ubuntu 12.04 because windows cannot boot.(appears as if not installed)  after like 4 tries I couldnt finish the install with a usb.so I burned a Dvd Rom with the Iso and when I select it to boot some code appears and eventually the purble screen with the ubuntu logo and five white dots. The dots continue to turn red then white again but nothing else happens. Its been like half an hour and I think it may have something to do with the previous tries in witch I got to about 40 percent and then freezes indefinately.  Is there a way I can just completely wipe everything from the boot menu?roi even need to do that?
sorry for the errors I'm on a tablet.

Are you trying to dual boot or what. You must provide what you are trying to do.

get the Ubuntu 12.04 LTS iso by the way

---

### Post by decagonalist on 2012-05-07
> **vVvSHADOWvVv said:**
> Are you trying to dual boot or what. You must provide what you are trying to do.

get the Ubuntu 12.04 LTS iso by the way

I just want to wipe everything and start afresh with ubuntu

---

### Post by jadtech on 2012-05-07
> **decagonalist said:**
> Didn't try the alt. The computer is a **** toshiba satellite c55d or something like that. It had win7 originally.
Also where can I get this alt Iso?

not really dure that is what you really need to be honest here is where you can get it from [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

you dont have another computer with win vista or win 7  you can make a repair cd from to fix the MBR or have a windows install cd ..

burn the ISO to a dvd at the slowest speed if this fails  try make a boolable USB of the ISO ..

sometimes the answer is just staying clam relaxed and try try  again  the dvd can seem to take  a long time to lod from part to part it is probing and detecting all the hardware and trying to boot a bare bones system ...

---

### Post by decagonalist on 2012-05-07
No other win7 Pcs I'm just going to let it sit overnight.

---

### Post by darkod on 2012-05-08
You can also try burning it a cd since it fits on it and there is no need to use a dvd. I know more people have dvds at home now rather than cds, and in theory it should work, but in a way that's a different device.

And the fact that you already tried an install and failed has nothing to do with booting from cd/dvd. Booting from cd/dvd should work even if you have no hdd in the computer, it doesn't care what's on the hdd.

One thing you could try is this:
When the dvd starts loading, immediately in the first purple screen hit Esc. That will open the older type main menu. Hit F6 for advanced options, select nomodeset. Close the submenu and select Try Ubuntu from the main menu. See if that loads it correctly in live mode.

Always first try the live mode before installing because it will show if it can run, or you need some workaround.

If the nomodeset works, you can install from live mode but note that you will need to add the nomodeset to the first boot so it an boot once and let you install a video driver.

---

