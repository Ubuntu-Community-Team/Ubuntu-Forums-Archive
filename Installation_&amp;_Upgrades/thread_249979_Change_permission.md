---
title: "Change permission"
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by carltonx on 2006-09-03
I am running ubuntu 6.06 and I have RealPlayer folder with a closed lock on top of it on the desktop. I would like to remove it but when I try it tells me I am not the owner and therefore dont have permission to move it. Can someone tell me how to get permission so that I can move this folder. The folder is located at /home/carlton/desktop. please?

---

### Post by Shinzetsu on 2006-09-03
sudo chown <user> <path/to/wherever>

---

### Post by meng on 2006-09-03
Instead of
rm [foldername]
use
sudo rm [foldername]
and enter your USER password when prompted.
EDIT: rm is for removing, use mv for moving. On re-reading your post I'm not sure if you wanted to move or remove.

---

### Post by carltonx on 2006-09-03
I have tried what you suggested but it did not work. Can you tell me how to change permissiom for this folder:/home/carlton/desktop/RealPlayer?

---

### Post by meng on 2006-09-03
Note that the folder is probably called
/home/carlton/Desktop/RealPlayer
(it is case-sensitive, desktop and Desktop are different).
Did you try the chown command? Type in the command you tried exactly, perhaps there's a syntax error of some sort that we can help you with.

---

### Post by carltonx on 2006-09-03
carlton@Comp2:~$ sudo mv /home/carlton/Desktop/Realplayer
Password:
mv: missing destination file operand after `/home/carlton/Desktop/Realplayer'
Try `mv --help' for more information.
carlton@Comp2:~$

Meng this is what I did above and the result I get maybe now you can help me.

---

### Post by meng on 2006-09-03
Okay no problem, I can help with that.
When you move, you need a destination to move it to. You place that after your command, and a space. Make sure that your folder is named Realplayer and not RealPlayer, remember the case-sensitivity.
e.g. sudo mv /home/carlton/Desktop/Realplayer /opt/
should create /opt/Realplayer for you.
Another tip: ~ is shorthand for the current user's home, so
sudo mv ~/Desktop/Realplayer /opt
is identical

---

### Post by carltonx on 2006-09-03
Thank you Meng It worked!!!!!!!!!

---

### Post by meng on 2006-09-03
Great, it worked AND now you're more experienced with the console.

---

