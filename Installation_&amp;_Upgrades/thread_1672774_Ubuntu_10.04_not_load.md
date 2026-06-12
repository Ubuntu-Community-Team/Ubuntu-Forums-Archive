---
title: "Ubuntu 10.04 not load"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by Janos1 on 2011-01-21
Hi to all.Try to load my system today and nothing come up,only the terminal window.What ever i type in is working,like now i type in the terminal firefox,and it is how i ended up here.Try to type thunderbird in the terminal and my mail server started no problem.But nothing on my screen,don`t no wher to go from here.Any help please??  Thank you.

---

### Post by dino99 on 2011-01-21
in a terminal: startx

then check the driver activation: system admin additional drivers

---

### Post by Janos1 on 2011-01-21
Thank you for your help dino,i try and not working.it sad user not authorized to run x server

---

### Post by sikander3786 on 2011-01-21
Try,

```
sudo service gdm start
```

And also, post the output of these commands.

```
lspci | grep VGA
```

```
glxinfo | grep vendor
```

```
cat /etc/X11/xorg.conf
```

---

### Post by Janos1 on 2011-01-21
Thank you for your time i try all what you sagest,and came up
#1 job is already running
#2 nothing
#3 nothing
#4 no such file or directory
but if i type in lspci a hole page come off,i try to copy and paste here but not working.
Sorry my knowledge is weary  limited with Ubuntu.(last 20 years used windows).
If any suggestion i will try.Thank you again.

---

### Post by ubudog on 2011-01-21
Welcome.

1. Did it used to work?
2. If so, did you change anything?
3. What are your specs?

---

### Post by sikander3786 on 2011-01-21
I am pretty sure you mis-typed those commands thats why they didn't come up with any outputs. Any ways, try reconfiguring your graphics.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Note, capital 'X' for X11.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot.

```
sudo reboot now
```

---

### Post by Janos1 on 2011-01-21
Thank you again sikander i try and come up with
#1 mv:cannot stat `/etc/X11/xorg.conf no such file or directory
#2 dpkg:need an action option
#3 sudo reboot now is working
One thing is funny.Before when everything was working my terminal window was different. 
and in the terminal window was janos@janos-desktop $  and now before the $ sign have something ~like that symbol.If i type cd / the symbol is gone.
If i try to reload Ubuntu from my CD will i lose everything what i have now??

---

### Post by Janos1 on 2011-01-21
My terminal has no header and no frame just white window and never had this before 
janos@janos-desktop:~/$

---

### Post by ubudog on 2011-01-21
> **Janos1 said:**
> Thank you again sikander i try and come up with
#1 mv:cannot stat `/etc/X11/xorg.conf no such file or directory
#2 dpkg:need an action option
#3 sudo reboot now is working
One thing is funny.Before when everything was working my terminal window was different. 
and in the terminal window was janos@janos-desktop $  and now before the $ sign have something ~like that symbol.If i type cd / the symbol is gone.
If i try to reload Ubuntu from my CD will i lose everything what i have now??

Sadly, yes, you will lose everything.  But, using the terminal, you can back stuff up onto a flash drive.  The command would be something like this...

Assuming you want to backup your entire home directory, you could do this:

```
sudo cp -a /home/yourusername /media/yourflashdrive
```

That should do it.

Before you try to reinstall, make sure you have EVERYTHING important backed up.  Good luck.

---

### Post by sikander3786 on 2011-01-21
> #2 dpkg:need an action option

That was the most important command in your scenario and you missed on that. Please make sure you are not mis-typing. Try again.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If you've got a separate /home partition, you won't lose any settings/configuration but will lose all the installed software in case of a re-install. If /home is not on a separate partition, and that is most likely the case with a default install, you'll lose everything on the '/' partition.

---

### Post by ubudog on 2011-01-21
> **sikander3786 said:**
> That was the most important command in your scenerio and you missed on that. Please make sure you are not mis-typing. Try again.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If you've got a seperate /home partition, you won't lose any settings/configuration but will lose all the installed software in case of a re-install. If /home is not on a seperate partition, and that is most likely the case with a default install, you'll lose everything on the '/' partition.

Yep, so back stuff up if you are going to do it.

---

### Post by presence1960 on 2011-01-21
From terminal run ```
sudo apt-get install ubuntu-desktop
```

---

### Post by ubudog on 2011-01-21
> **presence1960 said:**
> From terminal run ```
sudo apt-get install ubuntu-desktop
```

Or maybe reinstalling it might help...

---

### Post by Janos1 on 2011-01-21
Thank you all for your patient,try to save my staff,but all my beautiful fine tuned Firefox and all the bookmark will be gone.Now i try the USB stick but i have no clue what drive is the USB stick.Thank you again for your time and patient.

---

### Post by ubudog on 2011-01-21
As Sheldon would say, the one with the duck mouth.  :-)

---

### Post by Janos1 on 2011-01-21
Sorry guys not easy to get red of me.Try to sudo cp -a but error msg.no destination drive.
now i know the USB stick is the DUCK MOUTH ,but i have no drive letter.
Anybody have more patient?

---

### Post by Janos1 on 2011-01-21
Well i know all your guys give up on me but one miracle always could happen,like UBUDOG 
suggested sudo apt-get install ubuntu-desktop,reinstall everything and all my staff was saved.Nothing is missing and everything is working perfect.
Thank you again for everybody.

---

### Post by ubudog on 2011-01-21
> **Janos1 said:**
> Well i know all your guys give up on me but one miracle always could happen,like UBUDOG 
suggested sudo apt-get install ubuntu-desktop,reinstall everything and all my staff was saved.Nothing is missing and everything is working perfect.
Thank you again for everybody.

That's great!  Awesome.  Freaking awesome.  :p:p:p:p :popcorn::popcorn::popcorn::popcorn:

---

### Post by ubudog on 2011-01-21
> **Janos1 said:**
> Sorry guys not easy to get red of me.Try to sudo cp -a but error msg.no destination drive.
now i know the USB stick is the DUCK MOUTH ,but i have no drive letter.
Anybody have more patient?

To find the name of your flashdrive, type this in a terminal...

```
ls /media
```

That will list all flashdrives, cd's ect. plugged into your computer.

---

### Post by Janos1 on 2011-01-21
Thank you is yours again ubudog.

---

### Post by ubudog on 2011-01-21
> **Janos1 said:**
> Thank you is yours again ubudog.

No problem.

---

