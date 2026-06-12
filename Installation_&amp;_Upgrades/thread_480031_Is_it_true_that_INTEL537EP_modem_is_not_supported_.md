---
title: "Is it true that INTEL537EP modem is not supported in feisty"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by swoll1980 on 2007-06-20
Let me know please. I have to configure my cpu for dial up this would be a huge problem if it's true

---

### Post by Bartender on 2007-06-21
Sure looks like
[https://help.ubuntu.com/community/DialupModemHowto/Intel537EP](https://help.ubuntu.com/community/DialupModemHowto/Intel537EP)

---

### Post by Matchless on 2007-06-22
You may be in luck have a look here: [http://ubuntuforums.org/showthread.php?t=210405&highlight=537ep](http://ubuntuforums.org/showthread.php?t=210405&highlight=537ep)
Chuckman has a very good thread going on the Intel 537ep

---

### Post by stchman on 2007-06-22
> **swoll1980 said:**
> Let me know please. I have to configure my cpu for dial up this would be a huge problem if it's true

Winmodems are typically not supported by Linux very well.  Ditch the winmodem and get a hardware 56K modem.  They work better.

---

### Post by chuck_h1987 on 2007-08-03
Wrong i have a Intel 537EP installed on a Dell E-310. I am useing Feisty and it works fine. If it aint supported ill find away around it.

---

### Post by Bartender on 2007-08-03
> **chuck_h1987 said:**
> i have a Intel 537EP installed on a Dell E-310. I am useing Feisty and it works fine. If it aint supported ill find away around it.

So, how about telling us how you did it?

---

### Post by chuck_h1987 on 2007-08-05
Ok first things first you will need Gnome ppp and the driver for it. i will upload the tar.gz file when i get to my g/f's and i can snag some faster internet. but heres the run down.

Terminal:
Login as Root
cd into the Intel-537 directory.
command make clean
command make 537
command make install

After this it should be in your Restricted Drivers.

the (assuming you have gnome-ppp installed) in terminal login as root again.
type gnome-ppp

go to properties instead of automatic DNS make sure you have manual DNS selected.

I warn you. If you are using dialup with Feisty Fawn you may encounter slow download/upload speeds.  even though you are connected at 52.6K. 

Hope this works.
Chuck H

(P.S. I will upload the driver at around 12:30 PM CST time. please bare with me until then.)

---

### Post by Sepero on 2007-09-17
Download your 537ep driver already compiled here:
[http://ubuntuforums.org/showthread.php?t=552090](http://ubuntuforums.org/showthread.php?t=552090)

---

