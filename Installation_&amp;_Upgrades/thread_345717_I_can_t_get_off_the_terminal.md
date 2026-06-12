---
title: "I can t get off the terminal"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by kostaschatzi on 2007-01-24
Dear users hello again....

i have just installed ubuntu 6.10 on my pc and i have the problem that it doesn t give me any graphical environment.I just stay on the black screen and the only thingi can do is login.Generally i am a newbie and more newbie with ubuntu.I would appreciate any help

---

### Post by taurus on 2007-01-24
After you log in, what happens if you run this command?

```
startx
```
Did you install the desktop version or the server version?

---

### Post by kostaschatzi on 2007-01-24
It says command not found...
and i am not completely sure...but i think the desktop version...
however i have a question...
it asked me if i want to install dns or lamp or something during the installation andi said dns...
can it be that i installed the server version?

---

### Post by taurus on 2007-01-24
Yip.  You installed the server version alright.  Now, you just have to install Gnome so you can have a nice working window.

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```
Or reboot when it's done if you want.  Now, you should see a gdm GUI login screen.

---

### Post by kostaschatzi on 2007-01-24
Should i maybe just do a fresh installation better?I don t want to have created any problems anyhow...

---

### Post by taurus on 2007-01-24
Shouldn't be a problem installing Gnome now.  However, if you want to reinstall it again, please get the desktop CD since it's the one that comes with Gnome.

---

### Post by kostaschatzi on 2007-01-24
It didn t work...It was also almost obvious to me because it said that no packages were installed..

---

### Post by taurus on 2007-01-24
What didn't work?  Did you run these two commands first?

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by kostaschatzi on 2007-01-24
Yes i did...but after i ran sudo aptitude install ubuntu-desktop it said that it was not installing any packages

---

### Post by taurus on 2007-01-24
Is there anyway you can post the entire message after you ran both of those commands?

---

### Post by kostaschatzi on 2007-01-24
It said that it didn t find any packages in order to install...

---

### Post by taurus on 2007-01-24
Can you post your /etc/apt/sources.list here?

```
cat /etc/apt/sources.list
```

---

### Post by kostaschatzi on 2007-01-24
Unfortunately not.I don t know how to copy it anyhow...but after the first almost every sentence started with Err
I don t know if this tells you something

---

### Post by kostaschatzi on 2007-01-24
Well,first of all when i ran the command it went very quickly so it was difficult,however there are a lot of webpages somehow in this source.list

---

### Post by taurus on 2007-01-24
Are you surfing this site from another computer with window running?  You can save /etc/apt/sources.list to a USB thumbdrive from your server and then paste it here with the computer that you use to connect to this forum!

---

### Post by kostaschatzi on 2007-01-24
I have no usb in the computer that i am running the software...I am sorry...i am really unhelpful...i think i will just download the correct version somehow...

---

### Post by kostaschatzi on 2007-01-24
Dear taurus thank you very much for your good will.I will really do this.I will download the correct cd.I surely don t want to install a distribution that i won t be able to use so i will patiently download the correct one.I am sure that in the near future i will need the help of this forum again so i really suggest that we leave this discussion here.It s late even already in greece.

For sure the ubuntu forum is really something completely different that the other forums.I used to have suse and i have been in forums that were not as friendly and helpful as this forum...thanks again.

kostaschatzi

---

