---
title: "help!! Mount of Filesystem Failed?"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by deadramonesxx on 2010-08-07
i've been running 9.10 for about six months or so. one day when i turned on my computer it was going through a file check that didn't exceed 5%. i was then taken to a screen that said Mount of Filesystem Failed. after reading through other posts i found that fsck took care of the problem for just about everyone. then is followed by asking two y or n questions that i have to answer yes to. once i'm there, i answer yes and it repeatedly asks me the same question and nothing is working. it's been this way about a month or so now and i don't want to have to get a new computer. please someone help!!

---

### Post by presence1960 on 2010-08-07
why would you need to get a new computer? In the worst case scenario you can reinstall ubuntu or any other OS for that matter. I need more info from you.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by deadramonesxx on 2010-08-07
the new computer thing is because i'm not sure why nothing is working for me and i was worried it's just a lost cause ha. it happened very randomly i was using my computer one morning and i turned it off for maybe an hour and i come back and it's been stuck ever since. now is the live cd the one i used to install it? because if that's the case i don't have it on me. and will anything i do erase everything that i have saved into my computer already? thanks so much for responding i really hope you can help me out

---

### Post by presence1960 on 2010-08-07
The Live CD is the one you used to install ubuntu. If you don't have one download the iso and burn another CD.

---

### Post by deadramonesxx on 2010-08-07
alright i'll do that, thanks. do you have any idea why fsck doesn't work for me but worked for everyone else?

---

### Post by presence1960 on 2010-08-07
> **deadramonesxx said:**
> alright i'll do that, thanks. do you have any idea why fsck doesn't work for me but worked for everyone else?

You need to run fsck from the Live CD. if you run it from a mounted partition you can cause severe filesystem damage. Boot from the Live CD, choose try ubuntu without any changes, when the desktop loads open a terminal and run ```
sudo e2fsck /dev/sdX -y -f -v -c -p
```

X in sdX = the disk that has ubuntu on it. If you only have one hard disk then it is sda

---

### Post by deadramonesxx on 2010-08-23
alright so i've installed a copy of the cd, but. same problem. i can't get my computer to go to the desktop many. it gets stuck in that filesystem check that won't exceed 5%, and when i run fsck in the other menu the same thing happens, i'm asked to ignore and rewrite the blocks, i put a y for yes, then it asks again. and again. and so on. hm... sorry it's been so long but i still hope you can help!

---

