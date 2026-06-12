---
title: "Fix grub and error caused by Nordvpn"
date: 2020-11-26
forum: Installation &amp; Upgrades
---

### Post by gilles9 on 2020-11-26
Hello everyone, 

I just installed Nordvpn on my fresh ubuntu 20.04 and had some issues while rebooting. When i tried to put my password I had this message : 

"cryptsetup error "cannot process volume group vg ubuntu".

So I reboot and i press exit on startup to enter into the grub and I had two entries : 

-Ubuntu, with Linux 5.4.0-54-generic
and 
-Ubuntu, with Linux 5.4.0-42-generic

With the second entry, i can boot normally, but with the second i just cant enter my password with the crytsetup error. 

So I think it is a problem with the repo of nordvpn wich give an update from a non compatible debian version. so I removed it from "Softwares and updates" application. then I did an apt update and the system was up to date. So I guess that the problem comes from this repo. but it is not my main preoccupation at this time... 

 Now when I boot normaly, I boot on the 5.4.0-54 and I want to boot on the 5.4.0-42 because it is boring to press on exit eachtime I run my computer to avoid the error with cryptsetup. Can you tell me how to do it please ?

 And for the Nordvpn error, I will contact them to inform them there is a compatibility problem I presume. 

Thx in advance for your help and sorry for my poor english.

Have a nice day and thank you for all your work.

---

### Post by CelticWarrior on 2020-11-26
Please hold on your reporting because the error you mentioned has nothing to do with NordVPN, its repository or even Grub.
It may have something to do with a mistake during the installation you tried but not with the installation itself. 

You may want to read this: [https://askubuntu.com/questions/1256247/ubuntu-20-04-kernel-upgrade-encrypted-volume-group-cannot-be-found-crypttab](https://askubuntu.com/questions/1256247/ubuntu-20-04-kernel-upgrade-encrypted-volume-group-cannot-be-found-crypttab)

---

### Post by gilles9 on 2020-11-26
[COLOR=#000000]EDIT

Yes you are true, I forgot to make "sudo dpkg -i nordvpn-release_1.0.0_all.deb" before the install. I dont know if it is really the problem. but I still want to remove the [COLOR=#000000]Linux 5.4.0-54-generic and comeback to the first one. 

Thanks for your help.
[/COLOR]
[/COLOR]

---

### Post by gilles9 on 2020-11-26
I tried "sudo apt remove linux-image-5.4.0-54-generic linux-headers-5.4.0-54" but I'm not advanced anymore... It is the same

---

### Post by gilles9 on 2020-11-27
It was a little too hard to resolve for me so i made a new installation and now it work great. Thx for help. greetings

---

### Post by gilles9 on 2020-12-08
Actually, it was a problem with an update. I don't know how but the default language that I use to enter my cryptsetup password has switch with the one that i'm using on my Ubuntu session.
So I have make a new thread... [https://ubuntuforums.org/showthread.php?t=2454920&p=14005768#post14005768](https://ubuntuforums.org/showthread.php?t=2454920&p=14005768#post14005768)

---

