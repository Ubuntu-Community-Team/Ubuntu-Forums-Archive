---
title: "Fully uninstall Kubuntu9.10 to get Hard drive space back?"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by GazRockK on 2010-01-21
Sorry if there's already a thread like this one, but I'm in a bit of a hurry to get this finished.

I've recently tried to install Kubuntu 9.10 alongside Windows XP sp3. Unfortunately it didn't work, and I assumed it was just a one-time error. I tried again, and came out with another error. (The error was during the final installation process). I then changed cd drives, and booted the installation from my F:/ drive (instead of my E:/). It still did not install. I then checked my hard drive space (the drive I had tried installing to) and the amount of free space left went from 45gb to 9, and the capacity went from 60gb to 30. I figured the problem would go away if I deleted the partitions, so i went ahead to the disk management and deleted all 6 of them from Windows XP, and restarted my computer. I came back to see that the problem didn't disappear, as i I still have only 9gb free space and a capacity of a mere 30gb. Any help here? Hopefully It's not permanent.:(

Sorry if there isn't enough info here. just ask and I'll do my best to get an answer:)

---

### Post by USB_NL on 2010-01-21
hello

if you boot from the kubuntu cd

goto the terminal

type
```
sudo gparted
```

maby that will help

---

### Post by darkod on 2010-01-21
Assuming I understood correctly and your XP partition was shrinked to make space for kubuntu partitions, deleting them does not automatically expand your XP partition again.
Look in disk management again and it should show unallocated space on the hdd.
Unfortunately, the option to expand your windows partition with disk management ws only introduced since vista, XP doesn't have it.
You either have to use windows third party software, or Gparted and similar. Usually you would boot a cd with Gparted on it, and it will allow you to expand the XP partition. Make sure you create backup of your XP data first, just in case.

---

### Post by GazRockK on 2010-01-21
Update

I'm pretty new to this linux talk so I'm not sure what I just got. 
The only word I don't know the meaning of so far is "gparted" I'll go look it up later, but I'd like to know a user's definition of the program. If it IS a program.

---

### Post by darkod on 2010-01-21
Gparted = Gnome Partition Editor
In other words, windows disk management in superior form. :)

Gparted is included in the ubuntu cd in System-Administration but since you have kubuntu, which uses KDE as opposed to Gnome in ubuntu, I doubt Gparted is on the cd.

However, you should still have a partition manager in System-Administration. I like Gparted better, but I would expect you can expand the XP partition with the partition manager of kubuntu too.

And that command that is suggested:
sudo apt-get install gparted

might be able to install it temporarily in the live desktop even though you will be on kubuntu live desktop.

---

### Post by ajgreeny on 2010-01-21
Gparted is another partition editor program, rather like Partition Magic, I think, though I have never seen that to really know.

It is available by default on the ubuntu live CD, and no doubt there is something similar on the kubuntu live CD.  It also is available as a stand-alone live CD.  To use it, boot from the live CD; if using ubuntu go to gparted in the system-administration menu, not sure about details in kubuntu but look around.  Gparted live CD will boot to the gparted screen so no further selection needed there.

EDIT:
You're too quick for me, darkod.

---

### Post by GazRockK on 2010-01-21
I just finished downloading and burning GParted from an iso to a boot disk. I played around with the program and can't seem to merge my free disk space with my C:/ drive (the one with 9gb free space) 
any help on how to use GParted for this? (adding the free space to my c:/ drive?)

---

### Post by USB_NL on 2010-01-21
hello again

i googled merge gparted

this link came up first

[http://ubuntuforums.org/archive/index.php/t-941624.html](http://ubuntuforums.org/archive/index.php/t-941624.html)

maby that will help

---

### Post by GazRockK on 2010-01-21
AH tyvm USB_NL for this thread [[http://ubuntuforums.org/archive/index.php/t-941624.html](http://ubuntuforums.org/archive/index.php/t-941624.html)] It's given me some hope in fixing my problem.. 

Another question just to keep you guys busy; I was thinking of ditching kde and just going back to nice old gnome, but I have no real experience in this desicion..  What's the difference between Ubuntu and it's kde using counter-part; Kubuntu? What do you suggest I use?:confused:

also, should I be using "Partition Magic" instead of gparted?

---

### Post by GazRockK on 2010-01-25
SOLVED

I found another page that solved my problem. 
People's answers here helped me learn more about Linux. Thx.

---

