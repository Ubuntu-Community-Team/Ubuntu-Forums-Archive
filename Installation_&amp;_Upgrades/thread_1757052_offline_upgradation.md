---
title: "offline upgradation"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by rahulnair on 2011-05-13
hello everyone :),
   i am having a strange problem while upgrading to maverick from lucid.yesterday i downloaded an alternate cd of maverick from the ubuntu website.i have a horrible internet connection at home and it took me about 8 hours to download the 695MB iso.but then finally got it downloaded.
  I mounted it using the command,
 ```
sudo mount -o loop 10.10alternate.iso /media/cdrom
```  Strangely it didnt display the upgrade pop-up like it usually does.(I have previously upgraded ubuntu 2 times before,using the same methodology).
  Ok now i manually went into the /media/cdrom directory and (...by doing a bit of research about googling about the problem...),ran the command,
 ```
gksu "sh cdromupgrade"
```  This time i got the pop-up running,but strangely it makes it imperative,to download all the packages (APPROX 779 MB) AGAIN!!..from the internet before the upgradation process starts.
And if i click "NO (i wish to stay offline)",then the whole process rollsback.

 Why is this happening this time?

(never encountered this problem while previous upgrades..i remember i upgraded the OS each time completely offline !)

 Is the alternate cd useless,if i again have to download 779MB again?
 
 Or is there something that i am missing out?

thank you.

---

