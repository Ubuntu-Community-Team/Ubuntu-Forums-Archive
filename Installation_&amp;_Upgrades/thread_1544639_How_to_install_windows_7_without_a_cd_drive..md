---
title: "How to install windows 7 without a cd drive."
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by JACrosman on 2010-08-02
Hi all,
I am having an issue where i can not seem to figure out how to install windows 7 on unbuntu. I have a netbook and it has no cd drive so what i did was copy all the windows 7 installation files over to my desktop in a new folder and just ran the setup.exe using 'Wine'. That goes ok and it pops up saying install windows 7. After hit that it tells me"

"Windows installation encountered an unexpected error. Verify that the installation sources are accessible, and restart the installation. 

Error code: 0x800000100

I tried this same process on another machine which is running vista and it works fine. Any help would be greatly appreciated! Thank you!

---

### Post by Darkness Des on 2010-08-02
Microsoft recognized Wine and immediately made it so that almost all of their software doesn't work if they detect the Wine key in the user's registry. There are multiple options for doing this without a CD drive. So far the best option seems to be installing from a USB Drive. It has to have at least 4 GB of space on it.

[http://wudt.codeplex.com/](http://wudt.codeplex.com/)

---

### Post by Mark Phelps on 2010-08-03
> **JACrosman said:**
> Hi all,I tried this same process on another machine which is running vista and it works fine. Any help would be greatly appreciated! Thank you!
That's because you can't use Wine (or any of its variants) to install MS Windows, only to install MS Windows applications.

And, of course it works in Vista, because it's NOT running in Wine.

As for the remark that MS made it so that most of their software doesn't work if Wine is detected, LOTS of folks in the Wine subforum would disagree with that ridiculous remark.

---

### Post by MCVenom on 2010-08-03
Wait, Windows 7 can be installed from an .exe? 

I'm so confused...

---

### Post by Darkness Des on 2010-08-05
Not precisely a ridiculous remark, but I'm not here to flame/argue. Granted, I've never seen any PROOF of this registry seeking, but it does sound like something that MS would do to beat down the competition. Carry on.

---

### Post by YesWeCan on 2010-08-05
> **JACrosman said:**
> Hi all,
I am having an issue where i can not seem to figure out how to install windows 7 on unbuntu. I have a netbook and it has no cd drive so what i did was copy all the windows 7 installation files over to my desktop in a new folder and just ran the setup.exe using 'Wine'. That goes ok and it pops up saying install windows 7. After hit that it tells me"

"Windows installation encountered an unexpected error. Verify that the installation sources are accessible, and restart the installation. 

Error code: 0x800000100

I tried this same process on another machine which is running vista and it works fine. Any help would be greatly appreciated! Thank you!

Erm, your last sentence is challenging. The "same" process would be to run Wine on Vista and then install Windows 7 using Wine. Which is impossible. But I think what you mean is you installed Windows 7 on Vista, thus replacing Vista. Sure.

To install Windows 7 "on" Ubuntu (keeping your Ubuntu installation) will require VMWare or VirtualBox. You can install from an ISO file that you can make from the Windows CD. I use VirtualBox (free) and it works pretty well although I am having trouble with USB. You need plenty of RAM for decent performance (3 or 4 GB) as both OS's run concurrently.

It is easier to install Windows 7 on a separate hard disk (preferable) or partition.

---

### Post by C.S.Cameron on 2010-08-05
If you have an USB stick, you can format it NTFS, add boot flag, copy DVD to it, or extract iso to it and boot from it after selecting it in BIOS as boot device.
This works for 7, not for Vista or XP.

---

### Post by Darkness Des on 2010-08-07
> **C.S.Cameron said:**
> If you have an USB stick, you can format it NTFS, add boot flag, copy DVD to it, or extract iso to it and boot from it after selecting it in BIOS as boot device.
This works for 7, not for Vista or XP.

... Why did nobody think of this before?

---

