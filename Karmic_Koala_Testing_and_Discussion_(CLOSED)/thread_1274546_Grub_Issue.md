---
title: "Grub Issue"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by seamuso on 2009-09-24
I noticed I had a lag happening between my bios screen and when the grub2 menu first displayed .. Yes, I've read the bug reports and it's resolved on my system now, but in resolving it, I discovered a rather disturbing thing ..

My system (sig desktop system) is and always has had my multiple OS installs confined to their own drives and booting from their own MBR. I select the drive I want to boot via the bios boot device select menu (esc key during boot). Currently, I have 2 installs .. Win7 and Karmic

sda1 - Win7

sdb1 - karmic


one of the updates I've run apparently allowed grub2 to rewrite the MBR on sda, so I am no longer booting via the win7 installed MBR, but rather through grub2 .. which put my grub2 MBR on a different drive and caused the slow load .. my default boot drive was sda .. when I switched the default boot to be sdb, grub was speedy again.


At issue here is that if I remove karmic from sdb, I'm pretty certain that I will no longer be able to boot win7 (the reason why I keep my installs seperate).

So the real question is whether someone else has had this happen and if so is there a way to insure that grub2 is only updating to the drive on which it's installed?



On a side note, /etc/default/grub

```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x720

```

worked to resize my menu display and looks nice .. vbeinfo shows 1920x1200 as an option (my monitor's native resolution), so I'm off to give that a try ..:P

---

### Post by VMC on 2009-09-24
Usually when it wants to update grub it asked several questions, one of which is to keep the current menu. You didn't see that?

---

### Post by seamuso on 2009-09-24
> **VMC said:**
> Usually when it wants to update grub it asked several questions, one of which is to keep the current menu. You didn't see that?

This wasn't in regards to keeping a menu .. this overwrote the MBR on a separate drive that was used to boot win7 exclusively. Now when I try to specifically boot my win7 install, I am greeted with grub instead of going directly to win7.

I can recover the win7 MBR, so that's not a problem, but I don't feel like fixing it repeatedly.

---

### Post by ronacc on 2009-09-24
IIRC there is an option during install to tell ithe installer if and where to install grub . if you have win7 on sda and karmic on sdb , reinstall the windows bootloader to sda , and you will be able to boot it by setting sda to the default boot device even if you remove karmic from sdb , keep grub2 on sdb .

---

### Post by kansasnoob on 2009-09-24
Just curious, has anyone had to restore a Win 7 mbr/boot?

I've googled a bit and not found an answer. Admittedly I've not googled a lot because I have no intention to run Win 7.

I tried Win 7 and I don't see much improvement.

---

### Post by seamuso on 2009-09-24
> **kansasnoob said:**
> Just curious, has anyone had to restore a Win 7 mbr/boot?

I've googled a bit and not found an answer. Admittedly I've not googled a lot because I have no intention to run Win 7.

I tried Win 7 and I don't see much improvement.

locate and download mbrfix.exe .. save it in your c:\ .. open an administrator lvl cmd ... cd \ .. mbrfix

that will generate an html doc which gives more info on the program.

to fix vista/win7 is easy ..```
 c:\mbrfix /drive <num .. 0,1, etc> fixmbr /vista
```

answer yes when it asks, reboot and the mbr is fixed. I jacked up all of my mbr's a few years ago (vista rc1/2 timeframe). The linux drives and XP were pretty easy to restore, but I was unable to restore my vista partition until I found mbrfix.

All of my clients use windows, so it's pretty beneficial for me to have access to the various opratig systems .. with that said, I used vista x64 (4GB+ memory and better driver support than the alternative XP x64) .. 9 months later, win7 released and I've been using it as my windows OS since .. Really haven't had any problems and some progs (DVDshrink being one) that refused to run in vista run perfectly in win7 .. On top of supporting my clients, I like playing games and linux is kind of lacking in that department (but I've known that since my first slackware install in 1996 :lolflag:).

[quote=ronacc]IIRC there is an option during install to tell ithe installer if and where to install grub . if you have win7 on sda and karmic on sdb , reinstall the windows bootloader to sda , and you will be able to boot it by setting sda to the default boot device even if you remove karmic from sdb , keep grub2 on sdb .[/quote]

Would it boot? If all of grub files/configs are located on sdb and that drive was wiped, would the grub install to the mbr of sda be able to chainload the win7 install on sda?

---

