---
title: "No boot on chinese laptop"
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by federico3 on 2013-09-09
Hello, I am a european boy living in Shanghai(China), couple days ago I bought a Toshiba Qosmio X70 here. I clearly had chinese OS so I decided to install ubuntu and english windows 8(I could not change the language from the options).
I had usb sticks of both of them but even changing the BIOS booting options the pc would boot the chinese OS.
So I burned a DVD with ubuntu but after the initial menu the laptop would get stuck on a black screen. Same happened with the Windows stick(except it would stuck on the "starting windows" screen).
So I tried to change the BIOS, but the only one available on the official site was 1.0 version meanwhile I have 1.1 version and the .exe bios flashing program says it's not compatible.
Can someone please help me? I don't know what to do, I paid a lot for this pc and I feel like I wasted the only money I had on it.

---

### Post by varunendra on 2013-09-09
Hello, and Welcome to the Forums federico3 ! :)

Being a new system, it is almost certainly [UEFI]("https://help.ubuntu.com/community/UEFI") based. Does it have Windows 8 preinstalled? If so, it must have "Secure Boot" enabled. Disable it from the UEFI setup or from within Windows, whichever is applicable : [https://help.ubuntu.com/community/UEFI#SecureBoot](https://help.ubuntu.com/community/UEFI#SecureBoot)

Then try booting again with the USB. If installing in UEFI mode, you must use 64 bit Ubuntu.

---

