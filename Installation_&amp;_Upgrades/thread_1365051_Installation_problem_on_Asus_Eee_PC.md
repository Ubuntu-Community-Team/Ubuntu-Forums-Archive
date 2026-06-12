---
title: "Installation problem on Asus Eee PC"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by cutman on 2009-12-26
I just got an Asus Eee PC and put Ubuntu Netbook Remix on it doing a dual boot with the Windows XP that came with it. It was working great but then I realized that the software center wouldn't let me install stuff so I googled the problem and it told me to go into the terminal and enter "sudo apt-get update" so I did and everything was going great I downloaded the security updates but the updater thing wouldn't x out after it was done but the software center started showing the install button again but it wouldn't download the file with all the codecs and whatnot because it said that the security updates were still up. Well the security updates had already finished downloading so I decided to restart and now it won't boot up and I get stuck in the shell. Not only that, my bootup screen used to have Two Ubuntu options and Two Windows XP options plus a Windows NT option now it has Four Ubuntu options (if memory serves there are different numbers, one with a -14 and another with a -16) Am I going to have to reinstall the OS or can the problem be fixed in the shell? HELP!

---

### Post by phillw on 2009-12-26
> **cutman said:**
> I just got an Asus Eee PC and put Ubuntu Netbook Remix on it doing a dual boot with the Windows XP that came with it. It was working great but then I realized that the software center wouldn't let me install stuff so I googled the problem and it told me to go into the terminal and enter "sudo apt-get update" so I did and everything was going great I downloaded the security updates but the updater thing wouldn't x out after it was done but the software center started showing the install button again but it wouldn't download the file with all the codecs and whatnot because it said that the security updates were still up. Well the security updates had already finished downloading so I decided to restart and now it won't boot up and I get stuck in the shell. Not only that, my bootup screen used to have Two Ubuntu options and Two Windows XP options plus a Windows NT option now it has Four Ubuntu options (if memory serves there are different numbers, one with a -14 and another with a -16) Am I going to have to reinstall the OS or can the problem be fixed in the shell? HELP!

Hi,

the -14 and -16 are different ubuntu kermels (the bit that runs the computer - the operating system) having two entries for each is normal - you should have -14 and something like -14 rescue - the same for -16

If you're running 9.10 flavour of ubuntu, you're on Grub2.
What I'd suggest is re-set Grub2 

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If that fails then. re-do the Win MBR, get it to boot, then put grub2 back on

All the options are covered in that thread - just remember you're in Grub2, not Grub legacy.

Regards,

Phill.

---

### Post by cutman on 2009-12-26
Ok, thanks, but I have no problem getting into Windows XP. I just can't get the Ubuntu to work. Whenever I chose any of the ubuntu options I get the text line. Should I just re-install Ubuntu?

---

### Post by cutman on 2009-12-26
Here are some screenshots I took with my iphone. I have no idea what any of it means.

First this
[ATTACH]141288[/ATTACH]

Then this
[ATTACH]141289[/ATTACH]

---

