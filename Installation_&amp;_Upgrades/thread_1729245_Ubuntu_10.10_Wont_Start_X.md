---
title: "Ubuntu 10.10 Wont Start X"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by exploitations on 2011-04-14
I've been searching for days since I installed Ubuntu on my laptop here.
I can get into my computer, only if I login and type "startx".
I'd like it so that it automatically starts X and I can login to different accounts in the login screen.
I've been searching for days like I said, and I can't seem to get the right help.
If someone could help me with my problem it would be greatly appreciated. 

Thanks

---

### Post by exploitations on 2011-04-15
anyone?

---

### Post by exploitations on 2011-04-16
I'm starting to think nobody helps anyone on these forums. Whenever I post nobody answers.

---

### Post by Dutch70 on 2011-04-16
If anyone knows the answer to your problem, I doubt they would withhold the info from you. Also, it would be very difficult for anyone to help you with the amount of info you supplied. Read your post again, and imagine you're not sitting there looking at the computer. The only relevant information you gave is...Ubuntu 10.10
"I can get into my computer, only if I login and type "startx"

Reading this will help us to help you...
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1422475[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by exploitations on 2011-04-19
Well that's because what I wrote is all the information I can give.. and its not just this thread, but I've noticed many other people will another problem I have were completely ignored and they all had tons of information. but that's not my problem right now

When I turn on my computer it goes into terminal mode, and it asks me for my username and password.. then I have to type "startx"
but I followed a tutorial so that it starts x automatically when I login, but I'd like it to start it so I can use the graphical login..
I've tried reinstalling ubuntu three times and it wont work.

---

### Post by Dutch70 on 2011-04-19
Sounds like something to do with your graphics card, whatever card that is. Only you can know that. 
Did you read the link I gave you?

---

### Post by exploitations on 2011-04-19
I did.

I don't understand why its doing this now; I had the same version of Ubuntu installed before without error. I'll keep looking around online.

---

### Post by Dutch70 on 2011-04-19
Ok, I'm just going to take a shot in dark here. Have you tried other boot options such as nomodeset? Actually, I thought I already mentioned that, but apparently not.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

Also, please post the output of...
```
lspci | grep VGA
```

---

