---
title: "No Graphics Upon Installation"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by Memnoch999 on 2007-04-05
Hi guys,

This is my first time with linux and i'm having some really annoying problems i can't seem to get around.

Hardware:

Amd64 X2 3800+
Abit Fata1ity AN8 mobo
XFX 6800gs XXX Graphics Card
2gb ram
1x WD 320 Gb
1x WD 300 Gb
Hyundai L17T Image quest moniter

Ok first i tried to install edgy from the live cd,Is only viewable in 1204x768x32 except i have no curser, can move round and install using tab and the ctrl button to find the curser (annoying as hell). soon as install is completed live cd is removed and boot into ubunto, ubunto splash sceen comes up and loads. then lots of pretty colours as everything goes haywire graphics wise. monitor is report that the input is currently 720x400 

Tried to reinstall but this time enabled the nvidia settings while in live cd from add/remove programs setting, enable it with sudo command then installed. exact same problem all over again.

Tried with the feisty beta amd 64 alternate version, went though install fine, selected correct resolution, everything worked fine. rebooted splash loading screen comes up (in colour this time) but then back to the multy colour hippy screen. monitor again reports input of being 720x400

am mildly stuck on what to do now, any clues would be helpfull..would really like to get this working and find a good alternative to XP

Thanks



Incase needed the following partions were used:
WD320:
12Gb for root file (EX3) 
3Gb for Swap (Fat 32)
20Gb window Xp (ntfs)
the rest was data (ntfs)

---

### Post by Memnoch999 on 2007-04-05
you can lock this now, figured out how to get restart xorg and input correct monitor and graphics card info.

---

