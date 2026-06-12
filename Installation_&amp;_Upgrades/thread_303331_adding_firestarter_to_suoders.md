---
title: "adding firestarter to suoders"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by drakedog on 2006-11-20
I want to give firestarter to startup(latest ubuntu, DE = Gnome). I did it like this: 

sudo export EDITOR=gedit && sudo visudo

folowing lines after
%root ALL=(ALL) ALL -->
%myusername ALL= NOPASSWD: /usr/sbin/firestarter:-k 

add to Preferences-->Sessions

gksudo /usr/sbin/firestarter --start-hidden

restart, and it requests root pass, even if i start it later manually. what is wrong?

---

### Post by frodon on 2006-11-20
Just in case you didn't know, this is a bad idea to make firestarter launchable by another user than root, it is just unsecure.

So my question is why do you want to launch firestarter as a simple user ?

---

### Post by drakedog on 2006-11-20
I´m used to see an icon-notification when i´m a victim of a portscan, like  windows do it. This is an old habbit, but i want to have it on linux too. :cool:

---

### Post by frodon on 2006-11-20
Ok, but you won't have the same kind of input than in windows, only an advanced knowledge will allow you to understand the log produced.

If you do such a thing keep in mind that someone who get access to your computer will be able to disable completely your firewall in 2 seconds, it's the same in windows by the way. So ask you the question how useful will be your firewall if someone who come in your computer came disable it in 2 seconds.
Remember that the first thing that do a hacker is to disable all your protections.

---

### Post by drakedog on 2006-11-20
Ok this is a not secure solution.

---

