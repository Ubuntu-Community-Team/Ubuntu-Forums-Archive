---
title: "Feisty Clean Install Over Edgy Question"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by zero244 on 2007-07-25
Hello: I have Edgy running with my home directory on a separate partition. 
If I do a clean install of Feisty and not format the home partition will I still have my evolution mail and address book intact. Or will the install overwrite my mail data etc.
Is it better to just back up and format the Home partition and really start from scratch.
Thanks

---

### Post by TBerben on 2007-07-30
If you do not format your home partition the installation shouldn't affect your evolution settings and address book... Everytime you start Evolution, it looks for a settings directory /home/<your username>/.evolution .. If that directory is present it will use the settings it finds there. If the directory is not present it will create one. When you mount your home partition under Feisty and start Evolution it should find the /home/<your username>/.evolution directory and use the data stored there..

I'm not 100% sure though, so I recommend that you back up your mail and contacts (which is good practice when installing a new OS anyway)

---

### Post by bigken on 2007-07-30
done it loads of time never had any problems :)

---

