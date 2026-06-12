---
title: "Laptop shut down during update"
date: 2017-08-06
forum: Installation &amp; Upgrades
---

### Post by ajaolander on 2017-08-06
Right in the middle of my update my laptop turned off, and now will only boot to the gnu grub screen. So I used my live usb to run boot repair, but after doing the recommended repair option, entering the commands it told me to into terminal and going through all of it until it told me to reboot I still wound up back at the grub. I've been using ubuntu for about 5 years now, but I am still very much a novice when it comes to anything beyond basics. This girl will probably need to copy/paste commands for every step of fixing this problem- finding any help on other similar issues so far has found either slight enough differences to make the info of no use to me, or answers that assume I already know how to do one or two steps that don't get explained. Hope that doesn't make me a daft pain in the ass, I just don't want to lose all my files if I can help it and I'd rather never touch a computer again than go back to Windows.Thank you in advance for any help, I greatly appreciate it and DO actually make a point to pay attention and learn for the next time :)  This is the info from boot repair: [https://paste.ubuntu.com/25259573/](https://paste.ubuntu.com/25259573/)

---

### Post by RobGoss on 2017-08-07
Hello and welcome, Loosing power in the middle of a update is problematic only because it hard to pin point what update is causing the machine from not booting correctly 

Please see this post I came account it's worth a read [https://askubuntu.com/questions/111563/lost-power-during-upgrade-how-do-i-recover](https://askubuntu.com/questions/111563/lost-power-during-upgrade-how-do-i-recover)

If you can get in to recovery mode you can them restart the updates again this should fix any broken packages caused by the power shut down

---

### Post by Autodave on 2017-08-07
If you can download a new version (or if you have the installation media from when you installed Linux before) you could use that to boot the machine and then choose "Try ?buntu." If that boots, you could then at least copy all of you files onto an external media and save them in case something goes wrong.

People PLEASE!!!!!  You need to make backups of any important files. And you need to do this continually! An external hard drive is not expensive anymore.

---

### Post by RobGoss on 2017-08-07
+1 Autodave, it's  extremely important to have a backup just in case things go wrong, unless you're like me and keep everything to a minimal

---

### Post by Keith_Helms on 2017-08-07
Mine did that too a couple of days ago.  I was playing a game in the foreground while updates downloaded in the background and I just assumed that some prompt popped up right when I hit enter in the game.  Once I powered it back on there were no apparent problems.

---

