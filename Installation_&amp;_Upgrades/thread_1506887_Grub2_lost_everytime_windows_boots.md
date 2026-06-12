---
title: "Grub2 lost everytime windows boots"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by Barbalras on 2010-06-10
I have a dual boot system with Lucid Lynx and a Windows 7 that came with the laptop (it's a Dell Studio with an i3 processor).

Grub2 boots into Win7 and Ubuntu just fine. The thing is that if I choose Win7, next time Grub doesn't show up. I can't boot anything and the screen turns black. I can reinstall grub2 with Ubuntu's live CD and the cycle starts all over again, it's very annoying.

These facts may or may not be important:
I think that this started happening when I uninstalled wubi after being able to install ubuntu through another method
When reinstalling grub there's an error that repeats through many lines of the terminal (I can't remember what it says, if you think it's important I can check). Anyway, it ends up saying the installation finished successfully.

I've googled a lot and at some forum they recommended uninstalling Windows' services. So I did, I uninstalled the services that seemed relevant to the issue, with no luck.

Any ideas?

---

### Post by darkod on 2010-06-10
There is some idiotic Dell software running in the backgound that they never tell you about. It deletes part of grub2 every time you run windows. Look here for more:
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by garvinrick4 on 2010-06-11
Check to see if there is a wublder or something close to that in your Windows boot manager. Boot into windows 7 open a command line and.

```
bcdedit
```If you see one with the wubider or close to that then wubi left it in Windows boot manager happens sometimes if user uses Add and Delete programs in windows instead of uinstalling
from the Wubi folder in C: Drive. .

```
bcdedit delete { number in wublder with these brackets}
```Sorry I have forgotten the name of the identification number but you will see it in the {brackets}

Just incase darkods site does not help. If does not help you maybe someone can gain off of this post. darkod is right though Dell butchers Windows and sneeks in a hidden  Dell recovery partition and then gives you a disc with its own proprietary drivers. That recovery partition is usually sda1 that I have seen. Is just a mess Dell wants to make for some reason.

---

### Post by Barbalras on 2010-06-12
Excellent! darkod's solution did the trick! As simple as effective

damn Dell

thanks a lot!

---

