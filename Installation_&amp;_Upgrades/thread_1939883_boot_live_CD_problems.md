---
title: "boot live CD problems"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by DenverChris on 2012-03-12
Hello again, all... 

I (a total noob), posted here before, and everyone was really helpful. I've been google-ing for answers to my situation, but havent been able to figure out my specific problem. Keep in mind I'm a newbie... ha ha

So, at first I tried- unsuccessfully-  to install Ubuntu... After lots o' problems, I was able to configure my laptop to dual boot Windows and Ubuntu... Ive been playing around with it for a month or so, and I love it!

Now.... I want to install a different distro... I dont want to dual boot. I want to just erase everything and start from scratch. The problem is, I cant get my live CD to boot. After I restart my computer, I get the screen that asks me what OS I want to run- Ubuntu, Windows, or the Ubuntu distro I was NOT able to load... All told, I have about 7 or 8 options to choose from on start up. Some say Ubuntu, and some say Ubuntu/recovery mode... I dont understand why there are so many options.....

So, basically, how do I get my live CD to boot???? When I successfully installed Ubuntu, after I restarted my laptop, the installation screen just automatically came up... Now, it just wont do that :(

What am I doing wrong???

Once again, I'm not very experienced, obviously, but I'm pretty motivated... and excited to learn more...

Please help!!!

Thanks!!!

-Chris

---

### Post by darkod on 2012-03-12
You need to double check if you are booting from the CD-ROM first, before the HDD. Check in BIOS.

If you are booting from the cd first, and the cd is good, it should load the cd regardless what you have on your hdd.

---

### Post by DenverChris on 2012-03-12
Hey Darkod.... thanks for the reply!

I'm sorry if this is tedious or offensive, but I dont know WHAT youre talking about.... I only understand your post in a vague, general sort of way....

Please keep in mind Im totally inexperiened. Im not adverse to figuring things out for myself- thats my motivation, actually, but I'm a bit lost... -;(

---

### Post by darkod on 2012-03-12
The computer needs to know in which order to try to boot from which device. This is called a boot order.

If it is setup to try the hdd before the cd-rom it will try to boot from the hdd ignoring the cd you have in the drive.

The boot order is inside your BIOS, you can modify it there. Depending on your computer manufacturer, you enter the BIOS by pressing a key when the computer is booting up. It is usually F10, F2, or Esc.

Also, usually there is option to call a boot menu by pressing F12 or similar, where you can select what device to boot from.

You need to tell it to boot from the cd-rom.

Try looking at your manual, it should have explanation how to enter the BIOS and how to change boot order.

---

### Post by DenverChris on 2012-03-12
I actually dont have a manual... but I'll try your suggestions randomly... I was thinking/hoping itd be a quick fix like that- I just wasnt sure which key to press. Thanks!

---

