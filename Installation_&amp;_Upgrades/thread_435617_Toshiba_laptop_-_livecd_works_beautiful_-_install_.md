---
title: "Toshiba laptop - livecd works beautiful - install fails ?!"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by FizzBuntu on 2007-05-07
Hello
I've just installed Feisty Fawn on my laptop using the livecd which worked great, even with the desktop effect and wi-fi, so I installed it.
When I start on the hard drive, it boots, give me the logon screen, I log on and I just get n empty screen with only the light brown background and the mouse pointer, the system isn't frozen, there's no error message, I even get an empty window if I put a cd...

---

### Post by hal8000 on 2007-05-07
Have you tried ctrl-alt-F1 and logging in at an alternate console?

If you can, see if you can read /var/log/messages or /var/log/Xorg.0.log for clues.

---

### Post by FizzBuntu on 2007-05-07
ok, logged in an alternate console et checked the messages. Seemed it was referring to a problem with resetting the wi-fi card.
I remove the card and re-installed Ubuntu, get the same result on screen.
The messages are talking about cml:readonly:/etc/gconf/gconf.xml/mandatory resolve to a read-only configuration source position 0
then 1, 2 and 3
net : Registered protocol family 10
lo: Disabled Privacy Extensions
ADDRCONF(NETDEV_UP): eth0: link is not ready

... :(

---

### Post by FizzBuntu on 2007-05-08
ok, installed Kubuntu and it worked, but I don't like kde much, i'd like to fix what seems to be a gnome related issue

please, help !!!

---

### Post by FizzBuntu on 2007-05-09
still stuck guys, I just can't use the laptop on livecd only...

---

### Post by mostholy on 2007-05-09
gotta love irony, I'm able to function under gnome but kubuntu won't load, stalls at 11%.  Naturally I favor KDE over gnome but want to give it a fair shake as I have never really tried it before (was told that it was for MAC types).  But I guess forums tend to bring out these frustrations.

---

### Post by FizzBuntu on 2007-05-10
OK mostholy, as I'm still waiting for a solution to my gnome related problem, all I can offer is a laptop exchange, kubuntu worked just fine on mine...

---

### Post by FizzBuntu on 2007-05-14
up

---

### Post by FizzBuntu on 2007-05-15
help, still stuck...

Help, I need somebody, help !!! (the Beattles)

---

### Post by hashimoto on 2007-05-15
Did you try to install ubuntu-desktop on kubuntu?

---

### Post by FizzBuntu on 2007-05-15
No, I didn't
is that possible anyway ?
How do you do it nd wht kind of system will I end up with ?

---

### Post by hashimoto on 2007-05-15
Yes, it is possible and you will end up having both kde and gnome desktop environments. You can select which, when logging in.

To install, open terminal window (don't remember what it is called in KDE), and run:
```
sudo apt-get install ubuntu-desktop
```
Give your password when asked and then just wait for the magic.

---

### Post by floke on 2007-05-15
You can do it that way; or you could try using the alternative installer rather than installing from the LiveCD

---

### Post by sandman55 on 2007-05-15
When you downloaded the CD did you check the check sum to see if the download was OK and when you burnt the disk did you check the disk for errors

---

### Post by FizzBuntu on 2007-05-15
Ok, i've tried the apt-get install ubuntu-desktop thing. It says that it can't find the package...
Iv' already tried the alernate CD and got the same result
Each time I've checked the checksum and made media check when first booting the cd.
The installation of Ubuntu on the desktop computer just went great.
Why would there be any difference here (beside the fact that it's an all different computer)

thx for your support

any other ideas ?

---

### Post by gorkur on 2007-05-15
Try going the easy way out by installing Ubuntu-Desktop via Synaptic.

---

### Post by hashimoto on 2007-05-16
> **FizzBuntu said:**
> Ok, i've tried the apt-get install ubuntu-desktop thing. It says that it can't find the package...

Did your network card work on Kubuntu? Reading your earlier posts hints that it was not properly configured on Ubuntu, but you don't actually say if it works on Kubuntu. Not having internet you naturally can't install ubuntu-desktop (it's not on the Kubuntu install cd).

If your wifi-card/internet works, then you should be able to install ubuntu-dekstop provided that your sources list is OK.

---

### Post by kingtsy on 2007-05-16
I have the same situation with FizzBuntu with my Toshiba Laptop. I can't install ubuntu 6.06, 6.1 and even 7.04. What i did was to install Kubuntu 6.10 first and it work fine. Then i install Ubuntu 6.06 and it install and replace the Kubuntu. I don't know why but it did install and replace the kubuntu.

Then i decide to install Ubuntu 7.04 and it didn't install again due to gnome problem so i install Kubuntu again afterward install Ubuntu 7.04.

If you like you can try what i did.

I think the problem is in the Gnome Display manager.

I hope it might help you.

Thanks.

---

### Post by FizzBuntu on 2007-06-26
Just for info...
I've tried to install Xubuntu 7.04 and installs fails at ext3 fs creation
I've tried Ubuntu Dapper drake
I've tried Ubuntu 5.1
and both livecd didn't open a gnome session
finally I've installed a Xubuntu Dapper drake, then upgrade to 7.04 - works greate
tried install ubuntu-desktop, installation works, but opening a gnome session doesn't work...
anyway, I'm fine with the upgraded Xubuntu...

---

