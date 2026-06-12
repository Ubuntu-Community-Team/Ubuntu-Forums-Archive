---
title: "Problem upgrading to 9.04 from 8.10"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Adali on 2009-04-06
Hi I'm having a serious problem upgrading. While the upgrade was taking place and installing the new packages my computer suddenly crashed. When I tried to restart Ubuntu I got an error saying that x server wasn't the default. I can't get the GDM(Gnome Display Manager) to start. What do i need to do to get ubuntu back to normal??
 Please help!!

---

### Post by linuxuser21 on 2009-04-06
> **Adali said:**
> Hi I'm having a serious problem upgrading. While the upgrade was taking place and installing the new packages my computer suddenly crashed. When I tried to restart Ubuntu I got an error saying that x server wasn't the default. I can't get the GDM(Gnome Display Manager) to start. What do i need to do to get ubuntu back to normal??
 Please help!!

Do you have the CD?  Or how did you install it?

---

### Post by Adali on 2009-04-06
I used the command "update-manager -d".
I do still have the CD for Ubuntu "Hardy Heron"
???

---

### Post by tommcd on 2009-04-06
Are you able to boot to recovery mode? If you can, then verify that your /etc/apt/sources.list is pointing to Jaunty and run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
If you get errors then run:
```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by paxmark1 on 2009-04-06
That is how I updated in the end of the Alpha process.  

I had no problems, but recently I am not sure if it was importing window fonts or all the upgrading going on - things are very weird on my puter.  I have only rectangles instead of text and that only if x does not crash.  

While you wait for other advice - if you have decent download speed and aren't capped for amount you can download the daily build tomorrow,that might fix things.  And then you can go into recovery mode in a more graphical way with the daily build cd as opposed to the command line via grub.

peace, mark

---

