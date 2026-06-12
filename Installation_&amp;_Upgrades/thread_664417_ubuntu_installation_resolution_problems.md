---
title: "ubuntu installation resolution problems"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by ttmw on 2008-01-11
Im a complete noob to linux and decided to give ubuntu a go last night on my laptop. i booted from a live cd  and even then the resolution wasn't correct and i couldn't see the bottom of the installation screens fully but i could just about manage to press the buttons when i used the hide properties on both top and bottom menu bars to complete the installation.

Now when i start up the resolution seems wrong still with no choice to change on  |system>preferences>screen resolution | and i this disturbing image ...

[IMG]http://img148.imageshack.us/img148/6796/arghuk9.png[/IMG]

Also the graphics dont seems very crisp and everything seems a bit pixalated although it might be because everything looks so big in the wrong resolution.

thanks for any replies and bear in mind i know nothing about linux or ubuntu yet.lol

---

### Post by grokwik on 2008-01-11
You should begin by describing your computer... it would help a lot ;)

---

### Post by ttmw on 2008-01-11
Ive got a fujitsu amilo pro v2030 with ubuntu

here the spec...

[http://www.ciao.co.uk/Fujitsu_Siemens_AMILO_Pro_V2030_Edition__6372704]("http://www.ciao.co.uk/Fujitsu_Siemens_AMILO_Pro_V2030_Edition__6372704")

---

### Post by Glugglug on 2008-01-11
I have an old 12 inch monitor that does this  just wait until it loads and when its on the login screen press    Ctrl + Alt+ -   and keep pressing the - button untill  you get the right resolution.

---

### Post by chewearn on 2008-01-11
Try this:
[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html](http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html)

---

### Post by ttmw on 2008-01-11
It does nothing for the first suggestion about "ctr+alr -" and i cant get the second suggestion to work either, it just says command not found when i type either of the commands in the terminal box.

shame it didn't work.any other suggestions?

---

### Post by chewearn on 2008-01-11
> **ttmw said:**
> It does nothing for the first suggestion about "ctr+alr -" and i cant get the second suggestion to work either, it just says command not found when i type either of the commands in the terminal box.

shame it didn't work.any other suggestions?

Which command didn't work, and what is the error message?  Are you running something other than ubuntu (gnome)?  Like kubuntu or xubuntu?

---

### Post by ttmw on 2008-01-11
> **AstalaVista said:**
> Which command didn't work, and what is the error message?  Are you running something other than ubuntu (gnome)?  Like kubuntu or xubuntu?

this step didnt work...

"Type 'sudo gedit /etc/usplash.conf' or 'sudo nano /etc/usplash.conf' to edit the file-'usplash.conf'.It will look like this-"

and neither did the begining of step 2.

And ive only downloaded ran and installed the buntu 7.10 - Supported to 2009  Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM) that it has on the ubuntu website. ive done nothing further after that.

and the error i get is...

"sudo gedit /etc/usplash.conf: command not found"

and 

"sudo nano /etc/usplash.conf: command not found"

---

### Post by chewearn on 2008-01-11
I'm going to hazard a guess that you are running Kubuntu (based on your blue screenshot).  Try:

```
sudo kate /etc/usplash.conf
```

I don't have a Kubuntu set-up, so you have to figure out if this is what you are running.

---

### Post by ttmw on 2008-01-11
ok, that last code didnt work but it made me wonder if id left a space out of the previous command and i had! now the command worked so i went through all the steps and rebooted to a central ubuntu logo instead of the previously 'on the side' one. but after that i get nothing but a black screen, what will i need to do now? nothing works, i seem to have gone backwards lol.

how can i repair it to how it was? or just get it going again so i can try again or something new?

p.s. thanks for your patience

---

### Post by chewearn on 2008-01-11
> **ttmw said:**
> ok, that last code didnt work but it made me wonder if id left a space out of the previous command and i had! now the command worked so i went through all the steps and rebooted to a central ubuntu logo instead of the previously 'on the side' one. but after that i get nothing but a black screen, what will i need to do now? nothing works, i seem to have gone backwards lol.

how can i repair it to how it was? or just get it going again so i can try again or something new?

p.s. thanks for your patience

So, did you choose a resolution which your monitor support 1024x768?
Did you hear the "drum" login sound to indicate you have reached the login prompt?

If yes to both questions, then press CTRL+ALT+F2; you should drop back to a console login.

Login using your username and password, then run this:
```
cat /etc/X11/xorg.conf | grep Driver
```
Note down the graphics driver used.  Based on the website you gave for the Fujitsu amilo, it says VIA graphics controller.  I'm not sure which one of the xorg driver support this, thus you need to find out from existing configuration.

Then:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Answer the three questions.  Then restart the graphical login by:
```
sudo /etc/init.d/gdm restart
```

Note:
If the existing video driver don't work, choose VESA.
Make sure to type in exactly, since you will be unable to copy/paste.

---

