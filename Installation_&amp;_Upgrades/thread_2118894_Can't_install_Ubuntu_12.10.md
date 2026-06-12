---
title: "Can't install Ubuntu 12.10"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by Maxim20 on 2013-02-22
Hi everyone! Yesterday I tried to launch Ubuntu OS from LiveUSB but the only result I had was this: [http://upload.wikimedia.org/wikipedia/commons/e/e0/Win3x_Black_Screen_of_Death.gif]("http://upload.wikimedia.org/wikipedia/commons/e/e0/Win3x_Black_Screen_of_Death.gif")

Here are my computer's characteristics [http://img42.imageshack.us/img42/3435/11680240.jpg]("http://img42.imageshack.us/img42/3435/11680240.jpg")

May be because I don't switched off "Secure Boot", but i coldn't find it in my BIOS...

Can anybody help me with this issue? Thanks a lot!!!

---

### Post by oldfred on 2013-02-22
Welcome to the forums.

Is this a system with Windows 8 pre-installed. Then it would be UEFI with gpt partitioning. But if you installed it yourself, it may be BIOS/MBR. And if an older system may not even have UEFI. Newer systems were UEFI/BIOS and even the newest Windows 8 still have a BIOS compatibly or CSM mode.

You may just have video issues. What video card?

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Maxim20 on 2013-02-24
> **oldfred said:**
> Welcome to the forums.

Is this a system with Windows 8 pre-installed. Then it would be UEFI with gpt partitioning. But if you installed it yourself, it may be BIOS/MBR. And if an older system may not even have UEFI. Newer systems were UEFI/BIOS and even the newest Windows 8 still have a BIOS compatibly or CSM mode.

You may just have video issues. What video card?

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Thanks for answering my thread! 

No, I installed Windows 8 by myself, Windows 7 was originally installed.

Here are my Video Card's characteristics [http://img837.imageshack.us/img837/7577/videocardz.jpg]("http://img837.imageshack.us/img837/7577/videocardz.jpg")  -  it's integrated into the motherboard.

---

### Post by Maxim20 on 2013-02-24
> **istealth shadow said:**
> well it says on the download page you need x64 ubuntu 12.10 so you download that...

I downloaded exaxtly that version wich my computer needs: ubuntu-secure-remix-12.10-64bit

---

### Post by grahammechanical on 2013-02-24
Do you get that black screen when you run the live session? or after you have installed Ubuntu? It will make a difference to what you can do.

If it is when trying to run the live session try:

1) at the first purple screen press Enter.
2) and the next screen press Enter to select English as the default.
3) at the Try - Install screen press F6
4) scroll down the little menu and select nomodest and press Enter.
5) Press Esc to get back to the TRY - Install screen.
6) Try Ubuntu should be highlighted, So press Enter to Try Ubuntu
7) or scroll down to Install Ubuntu and press Enter.

Regards.

---

### Post by Maxim20 on 2013-02-24
> **grahammechanical said:**
> Do you get that black screen when you run the live session? or after you have installed Ubuntu? It will make a difference to what you can do.

If it is when trying to run the live session try:

1) at the first purple screen press Enter.
2) and the next screen press Enter to select English as the default.
3) at the Try - Install screen press F6
4) scroll down the little menu and select nomodest and press Enter.
5) Press Esc to get back to the TRY - Install screen.
6) Try Ubuntu should be highlighted, So press Enter to Try Ubuntu
7) or scroll down to Install Ubuntu and press Enter.

Regards.

I get the black screen when trying to launch Ubuntu from LiveUSB previously made ...

---

### Post by Maxim20 on 2013-02-26
And if I will install older Windows (XP or 7) would it change something?

---

### Post by oldfred on 2013-02-26
Have you tried the nomodeset? From the little icons at bottom of screen as shown in links above?

Some with Intel may work with these settings instread of nomodeset.

       Older Intel video card: i915.modeset=1 or i915.modeset=0 

newer:  i915.i915_enable_rc6=1
       
 Force Intel Video mode as boot parameter in grub menu (but use your size)
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

    Some new systems also need other boot parameters.

---

### Post by Weyete on 2013-02-26
Have u try using wubi.exe ?
win ubuntu installer ?

> **Maxim20 said:**
> Hi everyone! Yesterday I tried to launch Ubuntu OS from LiveUSB but the only result I had was this: [http://upload.wikimedia.org/wikipedia/commons/e/e0/Win3x_Black_Screen_of_Death.gif]("http://upload.wikimedia.org/wikipedia/commons/e/e0/Win3x_Black_Screen_of_Death.gif")

Here are my computer's characteristics [http://img42.imageshack.us/img42/3435/11680240.jpg]("http://img42.imageshack.us/img42/3435/11680240.jpg")

May be because I don't switched off "Secure Boot", but i coldn't find it in my BIOS...

Can anybody help me with this issue? Thanks a lot!!!

---

### Post by Maxim20 on 2013-02-26
> **Weyete said:**
> Have u try using wubi.exe ?
win ubuntu installer ?

Well, there is written: "Windows installer is not compatible with Windows 8 or UEFI firmware."

Sure, I may install older windows one, but how I know if I have UEFI firmware or not?

Thanks!

---

### Post by oldfred on 2013-02-26
If you installed Windows 8 yourself, you do not have secure boot. And then system more than likely is in BIOS/MBR mode even if new enough to have UEFI. UEFI has a BIOS compatibility mode and most older Windows 7 systems were in the BIOS mode.

---

### Post by Maxim20 on 2013-02-26
> **oldfred said:**
> If you installed Windows 8 yourself, you do not have secure boot. And then system more than likely is in BIOS/MBR mode even if new enough to have UEFI. UEFI has a BIOS compatibility mode and most older Windows 7 systems were in the BIOS mode.

Perfect then! Could I use wubi.exe to install Ubuntu with Windows 8?

---

### Post by oldfred on 2013-02-26
It should work. The issue is really gpt partitioning and Windows 8 in pre-installed systems is always UEFI and UEFI requires gpt partitioning.

Most users that have installed Windows 8 themselves have installed in BIOS with MBR(msdso) partitioning.

 Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

   wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

   HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

