---
title: "Windows Boot Trouble"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by SubliminalKid on 2007-01-18
<<Summary: When I boot windows it wants to reinstall>>

I decided to give linux a try, so I installed Ubuntu. I had trouble partitioning my drive(I wanted to dual boot), but I defragged a few times, and that fixed it. After the install, it did not ask me to install GRUB like I have read it's supposed to. So I manually installed GRUB, now when I try to boot windows I get "NTLDR is missing 
Press Ctrl + Alt + Del to restart"

I have already done a lot of searching for this problem, and found that I might need to copy ntldr and ntdetect from the Windows Setup CD to my drive( funny thing is I can find these files on my main drive, are they supposed to be in a certain folder because they are just sitting on the drive next to Documents, Program Files, etc).  However when I try to repair it asks me for my admin password...either I never created an admin pass in the first place(can't imagine how that would happen) or the passwords that I am 95% certain I might have choosen don't work. So this option is unavailible to me.

So I did a little more researching and found that SuperGRUB might be able to help, it was easy to use and I quickly began booting Windows(success I thought!) but alas, after going through the logo loading screen it goes to the Windows XP Setup, I DO NOT want to re-install windows. After trying everything I could to get around the setup, I finally succumbed and let it try to reinstall...but halfway through it starts telling me it can't copy certain files from the disc to the computer...even though it knows exactly where it is! 

So my question is if I can see all my old windows files and folders why does it think I need to reinstall it, rather than going to the login screen. (sorry for the long post, any help is appreciated, and if you need more information about my computer or what I did just ask)

---

### Post by bswilson on 2007-01-18
I don't think you have to do all of that.  Read [my recent post]("http://www.ubuntuforums.org/showthread.php?p=2031479#post2031479") on fixing the problem.

---

### Post by SubliminalKid on 2007-01-18
are you referring to the code:

rootnoverify (hd0,0)
makeactive
chainloader +1
boot

just double checking because I don't want to uninstall grub

---

### Post by SubliminalKid on 2007-01-18
I believe the troubleshooting section at: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
could help me, but I don't understand what that code is actually doing. 

This section applies to...

      Dual-boot setups in which Windows was installed after Ubuntu

      [B]Conditions where Windows failure forced a re-installation
[/B]
I believe this is my problem, although I am not sure...sorry for being such a newb to linux :confused:

---

