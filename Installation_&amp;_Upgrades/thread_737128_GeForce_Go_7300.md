---
title: "GeForce Go 7300"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by adi003 on 2008-03-27
I cant install unbutu 7.10 on my Asus F3T Laptop, the screen goes black and i can only see the mouse cursor during installation. I have a geforce go7300 videocard. What should i do?

---

### Post by Rocket2DMn on 2008-03-27
I'm surprised nobody answered this.  You should try using the alternate install cd - it uses a text based installer, but it is very easy to use.  The LiveCD doesn't work for everybody, mostly because of video driver problems, so you can get the alternate install cd at [http://ubuntu.com/getubuntu/download](http://ubuntu.com/getubuntu/download) by checking the box at the bottom for alternate cd.
Your video card should work OK after you install.

---

### Post by cmckdub on 2008-05-16
I am running an ACER laptop with a NVIDIA GeForce  Go7300. I am running Ubuntu 7.10. I know this does not help you, except that it is possible to run.I don't remember doing anything special when I installed from the CD, except that I trialed from the CD for a few days before doing the full install from the CD.
Now I am wanting to upgrade to 8.04, but the live CD is not recognising the NVIDIA card properly. However, it still does not go blank as yours did, it just doesn't give me all the features.

---

### Post by Rocket2DMn on 2008-05-16
It is not unusual for the LiveCD to have problems with video cards that otherwise work normally after installed.  You should be OK to proceed with your upgrade to Hardy.  If you installed restricted drivers with Envy in Gutsy, you should remove them first by running
```
sudo envy --uninstall-all
```
Then after your upgrade to Hardy you can use restricted drivers from within Ubuntu (System->Administration->Hardware Drivers - this is new in Hardy), or you can use the newer version of Envy called EnvyNG to autodetect and install NVIDIA drivers from their website.  See here - [http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)

---

### Post by cmckdub on 2008-05-17
Thanks. I think I will use the live CD to install though, as I don't have a very good internet connection (I think it would take all day to upgrade otherwise). Also, from what I have found [on another thread]("http://ubuntuforums.org/showthread.php?t=793768&highlight=upgrade+CD"), it sounds safer to do a full install. I have a seperate home partition, and most other things I could think of backed up.
I didn't use envy before. I hadn't heard of it before. It seemed like Gutsy had autonatically detected the Nvidia.

---

