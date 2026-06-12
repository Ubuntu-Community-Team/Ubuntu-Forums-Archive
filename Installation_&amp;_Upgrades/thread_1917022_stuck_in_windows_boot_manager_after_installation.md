---
title: "stuck in windows boot manager after installation"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by customan on 2012-01-29
hi guys,
I have installed ubuntu system x32 today, the latest ver. i think it was 11.10 and before i had win7 running on my machine.
so the installation went fine +all the updates needed.
But after i rebooted the machine, it got stuck in the old windows boot manager window which had win 7 and ubuntu but neither works if i try to run them. 
the win7 os isnt supposed to run though cause it was erased by the lin.Ubuntu.
So can any of you genius guys help a mate in trouble? 
thanks in advance. 
                              -Ravid-

---

### Post by BC59 on 2012-01-29
You have to download the Boot-Repair. It's an .iso file (image). You have to burn it in a bootable CD and boot from it. Then just click the button for the recommended fix and that's it.
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by holytree on 2012-01-29
Did You use wubi or a partition??

---

### Post by customan on 2012-01-29
i use a partition-the whole drive.
hmm...how to burn it as abootable cd/dvd disc while using the ubuntu demo cd os? because i dont have any other computer to burn it with...so do i have to download some software or i can just burn it with the demos default-basic burner?

---

### Post by BC59 on 2012-01-29
You can install Boot-Repair using the Live CD. While you have boot from the LiveCD or Ubuntu installation CD, run these commands:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair
```
Then search for Boot-Repair in the installed applications.

---

