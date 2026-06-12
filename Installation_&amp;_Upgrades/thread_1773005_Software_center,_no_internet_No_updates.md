---
title: "Software center, no internet? No updates?"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by MRoeDesigns on 2011-06-01
For some reason if I try to install anything from the Software Center, it says I have no connection to the internet, when obviously I do. Also, my system won't update because it says there are untrusted packages? The weirdest part is that if I try to install something from the console (sudo apt-get install whatever), it works fine. Any suggestions?

---

### Post by mörgæs on 2011-06-01
Yes :-) stick to installing (and updating, not the least) from the command line. There are lots of reports of Update Manager and Software Centre being buggy.

---

### Post by MRoeDesigns on 2011-06-01
The command for that is just "sudo apt-get update" right?
I did that, put my password in, and it updated a few things I'm sure, but it also said "Some index files failed to download. They have been ignored, or old ones used instead.", on top of listing before that a bunch of things it 'failed to fetch' D;

---

### Post by Rubi1200 on 2011-06-01
There seem to have been some issues with this over the past 36 hours or so. In most cases, waiting a few hours and then trying to update again has resolved the problem.

---

### Post by MRoeDesigns on 2011-06-01
Alright, I'll try again tonight or tomorrow and see what happens. Thanks

---

### Post by mörgæs on 2011-06-01
Always good to wait and/or try another mirror. 

The commands are 
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

