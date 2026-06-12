---
title: "Clean Instalation but no mouse and keyboard"
date: 2012-07-21
forum: Installation &amp; Upgrades
---

### Post by TakisX on 2012-07-21
After 2 years my hard disk died .
In the new i installed win7 and ubuntu64 11.04 
The installation went fine as always in this machine but i have an desktop but no mouse or keyboard.I cant enter my password
I have installed ubuntu in many machines of my friends with no problem. I am thinking to install 10.10 and upgrade

---

### Post by GreatDanton on 2012-07-21
What do you mean with I don't have keyboard. You don't have it, or Ubuntu doesn't recognize it?

I would suggest you to do fresh install instead of upgrading 10.10. After upgrades there are usually problems.

---

### Post by TakisX on 2012-07-21
It does not recognize it 
I made clean install
The upgrade from 10.10 was ok the clean intalation problematic
I have comon microsoft mouse and keyboard (usb )

---

### Post by oldfred on 2012-07-21
I had exactly that issue and found that ps/2 mouse & keyboard worked. Then I found the correct solution was just a BIOS setting to enable USB mouse & keyboard. 

It seems both Windows & Ubuntu have their own drivers but grub uses BIOS settings. Once at login though Ubuntu's driver should be the one you use to login with.

---

### Post by TakisX on 2012-07-21
Of course i have the USB mouse and keyboard enabled in bios and worked fine in ubuntu 2 years now 
Something i wrong in the new version of ubuntu

---

### Post by TakisX on 2012-07-21
Anyone ?

---

### Post by oldfred on 2012-07-21
I have used 10.10 as my standard until 12.04 came out. I also had installed every version as 64 bit full Ubuntu since 9.10 and once I changed BIOS have not had any keyboard issues with any version.  My system also is core2 but bit older and with nVidia. 

What else is unique with your system. Does liveCD boot ok?

---

### Post by TakisX on 2012-07-21
I booted with an older version of kernel and worked
I updated the system and booted with the latest kernel and it works
The only problem that i have is , when i choose restrat freezes when the 5 white spots apear and if i choose shut down works ok

---

### Post by oldfred on 2012-07-21
Is this from hibernation? I have not followed issue, but have seen several threads with that in the title.

---

### Post by TakisX on 2012-07-21
No hibernation , from desktop i choose restert and freezes

---

### Post by oldfred on 2012-07-21
May be related to this?

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/987220](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/987220)

---

