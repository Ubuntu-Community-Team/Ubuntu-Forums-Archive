---
title: "how to enter gui?"
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by tommy2c on 2005-07-13
ive just installed 4.10 and the console seems to be working fine but i do not know how to enter the gui, which i guess is xserver (or gnome, kde?).  Ive tried cont, alt f1-12 but it does not come up.  Also, what is sudo, does xserver need a certain command to load?

My system is rather old - a p-133 with only 32m and a weak vidio card - could the installation program not installed the gui because of this?

Thank you for any help you might offer.

---

### Post by dave9191 on 2005-07-13
Why dont you install the latest version 5.04? Anyway, what sort of installation did you do? You didnt type server or something during the install? A full intstall will boot directly into the graphical enviroment. 

But I dont know how it would cope on your system. But It should load or at least give you an error. 

Dave

---

### Post by tommy2c on 2005-07-13
im installing 4.10 because i have the disks from ubuntu.

i installed the auto default, might i have more success if i do a manual install?

thank you

---

### Post by dave9191 on 2005-07-13
What do you see when you boot the system? Does it go to a command prompt asking you to login? Does it give any error msgs? Try logging in and typin startx

And sry, I forgot to explain sudo. Putting sudo before a command will execute that command as the root user, and it will ask for the users, not the roots password. [http://www.ubuntulinux.org/support/documentation/faq/root/talkback/1101370914/discussionitem_view](http://www.ubuntulinux.org/support/documentation/faq/root/talkback/1101370914/discussionitem_view)

---

### Post by tommy2c on 2005-07-13
I am logged in, have tried both user and root.

Thank you for suggesting - startx-  but the console only give me a (comand not found).

thank you

tommy

---

### Post by dave9191 on 2005-07-13
If it says command not found, then you dont have X installed. This means you dont have any graphical enviroment installed, and therefore you dont have a complete version installed. I've come accross a number of threads such as this one in the past where people did a server install which doesnt install any graphic components. 

When you put the cd in and got the ubuntu command line for the first time, did you just hit enter and go through the usual install or did you type something there ? 

Dave

---

### Post by tommy2c on 2005-07-13
im sure i let the install program do its own thing.  you are correct, not only did xserver not install,  but many other packages also.

after a forum search of this problem, ive found some treads that might help.

i think this machine may not be up to the task, the vidio can't handle it.  I will try to install again and hope for better results.

thank you for your imput, wish me luck

---

### Post by dave9191 on 2005-07-14
You could always try to sudo apt-get install xserver or something. Im not sure how well kde or gnome would work on that machine, but you could use something basic like fluxbox. Hope the threads you found help, good luck :)

Dave

---

