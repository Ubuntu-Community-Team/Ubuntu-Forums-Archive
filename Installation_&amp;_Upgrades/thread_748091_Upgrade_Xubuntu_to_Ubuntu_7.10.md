---
title: "Upgrade Xubuntu to Ubuntu 7.10"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by simonlugi on 2008-04-07
Is it possible to upgrade from Xubuntu to Ubuntu 7.10 
If yes please can you send instructions as fo a beginner.
Thanks simon

---

### Post by prshah on 2008-04-07
> **simonlugi said:**
> Is it possible to upgrade from Xubuntu to Ubuntu 7.10 
If yes please can you send instructions as fo a beginner.
Thanks simon

If you have more than 256Mb RAM, then Ubuntu is suitable for you. Assuming you are running xubuntu 7.10 all you need to do is ```
sudo apt-get install ubuntu-desktop
```

---

### Post by Sef on 2008-04-07
> If you have more than 256Mb RAM, then Ubuntu is suitable for you. Assuming you are running xubuntu 7.10 all you need to do is
Code:

sudo apt-get install ubuntu-desktop



If you have the memory, then you should do this code first:

```
sudo apt-get update
```

then

```
sudo apt-get install ubuntu-desktop
```

The update assures that you download the latest updates that are in the repositories.

---

### Post by simonlugi on 2008-04-08
Thanks I will give it a go and let you know results

---

### Post by ZeSteves on 2008-04-08
and then don't forget to remove the xubuntu desktop. unless you want to have the 2 sessions option!!
it worked fine for me for a while, but then i had some issues with it. careful regarding some programs and libraries.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
 
this site also gives you a detailed step-by-step of installing and removing diferent flavours of ubuntu.
good luck :)

---

### Post by simonlugi on 2008-04-08
I followed the instructions to uninstall the xubuntu and now i just get an orange screen. Had to go to windows to post this. pse help

---

### Post by prshah on 2008-04-08
> **simonlugi said:**
> I followed the instructions to uninstall the xubuntu and now i just get an orange screen. Had to go to windows to post this. pse help

Open a terminal with Ctrl+Alt+F1, login and give the command ```
metacity --replace
```

Then switch back to X with Ctrl+Alt+F7, and if you still dont have a proper display (only orange background), then press Ctrl+Alt+BkSpace to restart the X server.

---

