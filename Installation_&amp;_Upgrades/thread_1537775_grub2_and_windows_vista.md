---
title: "grub2 and windows vista"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by Xamindar on 2010-07-24
Did a few searches but didn't find anything to do with this issue. 

After installing Ubuntu on another partition in my system the existing Vista installation will not start from the grub2 prompt. It will go to the windows loading screen and then just reboot the computer again and again. I can boot into vista just fine from a boot usb drive I made and Vista works fine when Ubuntu is not installed so the only thing I can think of is that grub2 is the problem. I have other computers that are able to multiboot just fine with linux and windows using other boot loaders like grub or lilo.

Why did Ubunto switch to grub2 as its clearly not ready. Anyone know of a fix to get it working? Or should I just downgrade to a better boot loader?

Thanks for any help.

---

### Post by hal8000 on 2010-07-24
Until you get a better answer.
I have XP, windows 7 and currently PClinuxOS2010.1 on one hard drive.
Install order is XP, then Win7 then PClinux. All 3 can be booted normally,
the difference is PClinuxOS uses grub legacy.

Grub2 does have advantages over grub legacy, however for me, changing anything in grub2 requires altering a long bash script. By contrast in grub legacy its only a matter of editing menu.lst  (In addition grub legacy has spalsh screens, colours etc and looks same as grub 2 ).

One way is to change from grub2 to grub legacy, although this may not be the Ubuntu answer. However this is linux, and there's always more than one solution.
HTH

---

### Post by oldfred on 2010-07-24
Run this so we can see what is where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Xamindar on 2010-07-25
hal8000, thanks for the suggestion. I went ahead and changed to the legacy grub and all is working fine now. That grub 2 is not ready.

oldfred, I appreciate the suggestion but there is no need. It was a fresh install of Ubuntu so it was set to whatever the installation does. The problem is grub2 not working properly (or missing an unknown option) so I doubt the script would tell me that. 

Best option is to stick with the older, working version of grub.

---

