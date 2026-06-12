---
title: "Ubuntu, sudo command [Resolved]"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by phpzer0 on 2006-11-26
Hi,

I've just installed Ubuntu on my PC and I get the following message: user name & password which I write and then I get asked for a sudo command. What should I write?

Thanks for your help

Best
William

---

### Post by taurus on 2006-11-26
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by phpzer0 on 2006-11-26
> **taurus said:**
> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
I dont know what I shall do with that code in the article?

---

### Post by 23meg on 2006-11-26
[QUOTE=phpzer0]I get the following message: user name & password [/QUOTE]Please clarify; do you mean what you should enter when you use the *sudo* command and are asked for a password? If that's the case, you should enter your user password which you set up when installing Ubuntu.

---

### Post by phpzer0 on 2006-11-26
I have installed ubuntu alternate and grub boot loader. When i select ubuntu (i can also select windows) on the boot menu when i start my computer, it asks for my user name and password, i write my user name and my password, AFTER that it asks for a sudo command and i don't know what i shall write in there?...

---

### Post by taurus on 2006-11-26
> **phpzer0 said:**
> I have installed ubuntu alternate and grub boot loader. When i select ubuntu (i can also select windows) on the boot menu when i start my computer, it asks for my user name and password, i write my user name and my password, AFTER that it asks for a sudo command and i don't know what i shall write in there?...
Do you see a GUI login screen (with music) after Ubuntu finishes booting up?

---

### Post by phpzer0 on 2006-11-26
No :-)

---

### Post by taurus on 2006-11-26
Did you install a server or a desktop version?

So, you see a command line asking you to log in, right!

---

### Post by phpzer0 on 2006-11-26
> **taurus said:**
> Did you install a server or a desktop version?

So, you see a command line asking you to log in, right!
I installed alternate in text mode.

It says:

Login: And then i write my user name (white text, on a black bagground)
Password: and then i write my password

And after i write my user name and password it asks for a sudo command.

Best
William

---

### Post by taurus on 2006-11-26
What username did you use?  After you enter your password and hit the return key, it then asks you to type in sudo???

---

### Post by phpzer0 on 2006-11-26
> **taurus said:**
> What username did you use?  After you enter your password and hit the return key, it then asks you to type in sudo???
My username is: "William"...

Then it writes: william@william:~$

---

### Post by taurus on 2006-11-26
That, william@william:~$, is what we call a prompt.  It means you are in...

Now, see if X is working for you or not.  At that prompt, type

```
startx
```
and tell me what happens.

---

### Post by phpzer0 on 2006-11-26
-bash: startx: command not found

---

### Post by taurus on 2006-11-26
So, look like you don't have X on your machine.  Now, you just need to install it.  From the prompt, do

```
sudo aptitude update
(use the same password that you use to log in...)
sudo aptitude install ubuntu-desktop
startx
```
Now, do you see a nice Gnome window manager?

---

### Post by phpzer0 on 2006-11-26
> **taurus said:**
> So, look like you don't have X on your machine.  Now, you just need to install it.  From the prompt, do

```
sudo aptitude update
(use the same password that you use to log in...)
sudo aptitude install ubuntu-desktop
startx
```
Now, do you see a nice Gnome window manager?
ok i'll try it

---

### Post by phpzer0 on 2006-11-26
Wow it takes alot of time... It unpacking alot of files... ;)

---

### Post by taurus on 2006-11-26
> **phpzer0 said:**
> Wow it takes alot of time... It unpacking alot of files... ;)
Yip.  You are installing Gnome window manager and since it requires X, it will install xorg as well.  I bet it's about couple hundreds MB.  So, if you have a DSL/broadband, it wouldn't take too long!  Just let it run and when it finishes, run the "startx" again to see if you see a nice window manager.

---

### Post by phpzer0 on 2006-11-26
Oki doki. Thank you so much!! ;)

---

### Post by taurus on 2006-11-26
We're not quite done yet so hold that thought!!!  ;)

---

### Post by phpzer0 on 2006-11-26
"I bet it's about couple hundreds MB. So, if you have a DSL/broadband, it wouldn't take too long!"

- I don't have plugged my internet cable into my laptop!? :S

---

### Post by phpzer0 on 2006-11-26
It's regenerating font cache, again and agian ... :(

---

### Post by phpzer0 on 2006-11-26
It works!!! THANK YOU... WUUUUHU! :D :o ;) :)

---

### Post by taurus on 2006-11-26
> **phpzer0 said:**
> It works!!! THANK YOU... WUUUUHU! :D :o ;) :)
Man, you just woke up the whole neighborhood!!!  Now, reboot and see if you get a nice GUI login screen...

---

### Post by phpzer0 on 2006-11-26
> **taurus said:**
> Man, you just woke up the whole neighborhood!!!  Now, reboot and see if you get a nice GUI login screen...
hehe... Where can i download themes for ubuntu_

---

### Post by taurus on 2006-11-26
If you ask, you'll get...

[http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by phpzer0 on 2006-11-27
> **taurus said:**
> If you ask, you'll get...

[http://www.gnome-look.org/](http://www.gnome-look.org/)
Thank you! But how to install? It's a "emerald" file ;)

And what about firewall?

---

### Post by taurus on 2006-11-27
> **phpzer0 said:**
> Thank you! But how to install? It's a "emerald" file ;)

System -> Preferences -> Theme -> Install Theme...

> And what about firewall?

Your machine probably already has iptables running so if you need to configure it, install firestarter.

```
sudo aptitude update
sudo aptitude install firestarter
```

---

### Post by phpzer0 on 2006-11-27
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

I can't find out how to connect to wireless network.

---

### Post by taurus on 2006-11-27
```
sudo dpkg --configure -a
```
to fix your problem.  And if you have questions about your wireless card, make a new thread with the name and model of your card...

---

### Post by phpzer0 on 2006-11-27
Ok, thank you very much!... Just a last question; Is it recommended to update to 6.10 edge? If yes how to? :)

---

### Post by taurus on 2006-11-27
If you want to upgrade from Dapper to Edgy, then follow this guide...

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Again, it works for some while others run into some real serious problems.  If you can back up all your important files, I recommend you install Edgy from fresh...  Could save you some headaches and hair too!  ;)

---

### Post by phpzer0 on 2006-11-27
**If you have questions about your wireless card, make a new thread with the name and model of your card...**

*I dunno what the name is of the card. I have an acer travelmate 2413 LMI. Wireless 802.11b/g*

---

### Post by taurus on 2006-11-27
Is it built in or an PCMCIA wireless card?

---

### Post by phpzer0 on 2006-11-27
Built in

---

### Post by taurus on 2006-11-27
See exactly what it is with these two commands.

```
lspci
sudo lshw
```

---

### Post by phpzer0 on 2006-11-28
Thank you! ;)


How to get a buttom menu like this: [http://img245.imageshack.us/my.php?image=vagueteasermacosxfrontitd9.jpg](http://img245.imageshack.us/my.php?image=vagueteasermacosxfrontitd9.jpg) in ubuntu? :)

And what about AntiVirus? ;)

---

### Post by taurus on 2006-11-28
> **phpzer0 said:**
> Thank you! ;)


How to get a buttom menu like this: [http://img245.imageshack.us/my.php?image=vagueteasermacosxfrontitd9.jpg](http://img245.imageshack.us/my.php?image=vagueteasermacosxfrontitd9.jpg) in ubuntu? :)

kxdocker.

> And what about AntiVirus? ;)

You don't need an antivirus!  I've never had one for all those years and never infected once, not even once...

---

### Post by phpzer0 on 2006-11-29
ok, thank you very much!

---

