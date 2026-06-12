---
title: "New Install - Problem on wifi (rtl8188ce)"
date: 2012-01-10
forum: Installation &amp; Upgrades
---

### Post by catastrope on 2012-01-10
I decided to install ubuntu to my laptop and the download finished pretty quickly (I also use windows so I installed to the second partition)

I was asked to reboot as usual but this time when ubuntu was trying to install the drivers, it just got into an infinite loop when it was trying to install my wireless card driver.

My card is realtek rtl8188ce and ubuntu is trying to install the firmware for rtl8192c (since I'm guessing they use the same firmware) but this line keeps repeating

"rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin"

This line keeps repeating over and over. When I connect/disconnect usb drives or the ethernet cable' system responds which means it understands I connected something, and tries to install their drivers etc etc

I have tried to shut the laptop off (by using power button) and restart, but after I select Ubuntu from the boot menu, I just get a pink screen which I assume is because the system couldn't finish installing the graphics drivers since it never passed the wireless drivers.

I have tried to download again and reinstall, but it didn't do any good.

At this condition, system doesn't understand any keyboard input so I can't make it skip the wireless installation. If I can somehow make him skip it, I can reinstall the wireless drivers once I manage to run ubuntu. But I don't know if there is anything I can do to make it skip that driver/firmware.


So now the question is simple, what can I do? :)


Note: The installation is still on and the line keeps repeating. The only thing that change is the numbers before the line keeps increasing. Like:

"[ 2699.969770] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin"
"[ 2759.892597] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin"
"[ 2819.815546] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin"

Note2: Ubuntu version is 11.10

---

### Post by catastrope on 2012-01-10
I've left it open a fair amount of time, but nothing has changed of course. Meanwhile, I've been searching for a possible solution using forum search and google.

But most of the problems related to my wireless card occur after the installation (like wireless not working but everything else is fine), not while on the first boot.

---

### Post by catastrope on 2012-01-11
I wonder if an older version of ubuntu would make any difference? But if it's the same firmware, I think the result would be the same aswell

---

### Post by catastrope on 2012-01-11
I've been searching for a possible solution all day. But all I could find was possible drivers to fix the problem. But of course I need to be able to run Ubuntu to install any of them. Since I'm stuck at boot before the first launch, those drivers are quite useless.

If anyone has any suggestions, it would be really appreciated.

Thanks in advance

---

### Post by catastrope on 2012-01-12
I think I'm about to give up since I couldn't find anything that can help me.

If anyone has any suggestions, please tell me

thanks

---

