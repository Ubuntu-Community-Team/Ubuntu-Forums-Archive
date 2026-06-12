---
title: "reinstalling bootloader after erasing MBR"
date: 2005-03-28
forum: Installation &amp; Upgrades
---

### Post by draco on 2005-03-28
I was reinstalling windows on computer with two systems: ubuntu and windows. I erased MBR, where was grub.
I want to install grub again, but I don't know what to do.
I was trying to run ubuntu-live, chrooting and then installing grub. 
```
cd /mnt
mkdir ubuntu
mount /dev/hda7 ubuntu
mount /dev/hda1 ubuntu/boot
chroot ubuntu /bin/bash
mount /proc
grub
> root (hd0, 0)
> setup (hd0)
```

But it doesn't work. After choosing kernel during boot, I received 'crc error' like this:
```
Uncompressing Linux...
crc error
System halt
```

I don't have warty-install cd at the moment. Is there any way to reinstall grub without resintalling or repairing system from warty-install cd ?

---

### Post by bored2k on 2005-03-28
[Q: How to restore GRUB menu after Windows installation?](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

I am not sure if that can be done with Live disc, because I haven't even touched a Live disc in ages .

---

### Post by Noobenstein on 2005-03-28
> I was reinstalling windows on computer with two systems: ubuntu and windows. I erased MBR, where was grub. 

I have a similar problem. I installed FreeBSD 5.3 on another partition on the same drive and opted to install it's bootloader (mistake). It recognises ubuntu as a bootable linux partition but all it does it beep at me when I try to select it. So I need to get Grub back on the MBR but can't figure out how to do it or what to do it with. I've been searching for 2 days for a solution, somebody please help me  [-o<

---

### Post by bored2k on 2005-03-28
[QUOTE=Noobenstein]I have a similar problem. I installed FreeBSD 5.3 on another partition on the same drive and opted to install it's bootloader (mistake). It recognises ubuntu as a bootable linux partition but all it does it beep at me when I try to select it. So I need to get Grub back on the MBR but can't figure out how to do it or what to do it with. I've been searching for 2 days for a solution, somebody please help me  [-o<[/QUOTE]
 Did you try with the fix on the post before yours?

only one post , this means you did not ask, no wonder you found no solutions :roll: .

P.S. - Your zombie avatar is rockin' .

---

### Post by Noobenstein on 2005-03-28
[QUOTE=bored2k]Did you try with the fix on the post before yours?

only one post , this means you did not ask, no wonder you found no solutions :roll: .

P.S. - Your zombie avatar is rockin' .[/QUOTE]


I have an issue with that fix. It says "e.g. Assumed that /dev/hda1 is the location of /boot partition" Assuming leads to one thing - trouble. Also, I wasn't sure windows rewrites the MBR the same way fbsd did, so the fix might not apply to me. Plus anything that has lines like (hd0,0) I find frightening because I know I'm messing with things that I don't understand which are altering my partitions. Second, the link provided has me loging in as the root from the install cd [http://ubuntuguide.org/#gainrootinstallcd](http://ubuntuguide.org/#gainrootinstallcd)  which contains the line "wherever your Ubuntu root device is". So me being the uber noob and all I don't know where that is. I don't suppose you could tell me how to get information like this so that I could help you help me?

I'll have you know I'm proud of my one post. It means that since I started Ubuntu a month ago I've managed to find an answer to every question I've had by searching these forums and the internet all on my own. So I posted only after searching long and hard on my own. I may be a noob, but I don't have to act like one.

P.S. - I stole the pic from the Wesnoth images folder, one of the games in the ubuntu gaming thread.

---

### Post by draco on 2005-03-28
Chrooting from warty-install cd and installing grub from there didn't work too.
Any ideas ?

---

### Post by draco on 2005-03-28
Anyway thanks for your time :)
I'll wait for stable release of hoary and reinstall ubuntu unless I found some way to repair it.

---

### Post by Noobenstein on 2005-03-28
I just started poking around in the console of the install cd, managed to log on as root and figured out how to reinstall stage 1 of the grub with the link he gave us and it worked perfectly. Now all I have to do is figure out how to get grub to see FreeBSD. The adventure continues.

---

