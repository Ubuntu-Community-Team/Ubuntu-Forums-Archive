---
title: "Installation issues with grub (also kde)"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by yao_man on 2008-02-29
Hey, two (and maybe a half) questions. 

1) I recently got a 500gb external hard drive so I decided I want to run Ubuntu off that hard drive and run Windows off my internal hard drive. I ran the installation and everything went fine, but now I cannot boot into Windows without having the external drive attached. It boots fine and I can select my os through grub if the external drive is attached. When I boot without the external drive I either get Error 22. Sometimes when I boot with it attached I get Error 21, but it works after restarting it. How can I make it so I can boot Windows separately and Ubuntu separately?

2) I have been trying to install KDE, but I have been completely unable to do so. I have followed directions and placed sources in my source.list but I cannot get KDE. What should I do to get KDE?
[INDENT]2 1/2)The primary reason I want KDE is for some of its wireless network management (although I wouldn't mind the graphical interface as well) and Kopete messenger. Can I install those alone?[/INDENT]

Thank you very much for any help in advance.

---

### Post by Pumalite on 2008-02-29
Fix your Windows MBR with your installation CD>Recovery>FIXMBR>FIXBOOT. or Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Then reinstall, but when you get to step 8, gto to 'Advanced Tab' and change (hd0) to whatever is appropriate for your external drive. Otherwise, reinstall with internal drives disconnected.
After you have Ubuntu, you can do:
sudo apt-get install kubuntu-desktop

---

### Post by yao_man on 2008-03-01
First, my XP cd has long since been lost. I am trying to acquire one through a friend, but I'm not sure if that will happen or not. In the mean time, is there another option?

Second, I have tried that command and it returns that package kubuntu-desktop cannot be found.

[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kubuntu-desktop[/INDENT]

Thanks for your help Pumalite and any additional help as well.

---

### Post by Pumalite on 2008-03-01
The answer to your first question is: Super Grub
Try sudo apt-get install kde-desktop

---

### Post by yao_man on 2008-03-01
Thanks for your help Pumalite, but I don't quite understand how to work supergrub...also my cd burner is not working atm either, I'll have to talk to a friend about that one too. As for the KDE issues, I looked a little deeper in my system and found that the repositories weren't configured correctly. Anyway, thanks for the help Pumalite, I'm not quite sure what I'm going to do yet, but for now I'll just leave the external hard drive attached.

---

### Post by Pumalite on 2008-03-01
Good luck.

---

