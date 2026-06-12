---
title: "Major help needed"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by hatmancan on 2008-11-08
I had to restart after installing a program and now i cannot log in
keeps asking me for a desktop password but i have never used one..
i had ubuntu , kubuntu and kde installed..
can someeone please help asap to get me up and running again???
ty
hat

---

### Post by taurus on 2008-11-08
You never set a password for your account?

Boot into recovery mode from GRUB menu (press ESC when you first turn on your computer if you don't see the menu) and at the prompt, create a password for account, assuming that your login name is hatmancan.

```
passwd hatmancan
```
Then reboot.

```
shutdown -r now
```

---

### Post by hatmancan on 2008-11-08
i got onto another comp so i have 2 now i can use..
it asks me for login password , then password for dave-desktop???
if i never used a password will the above work???
just before i shut down again..
also i have comp set with xp on one and ubuntu on second hard drive...
ty again hat
will await response before proceeding..

---

### Post by hatmancan on 2008-11-08
oh just again i used no password for login then i used my password for desktop..
it will take me to dave-desktop $

what do i do here???

---

### Post by taurus on 2008-11-08
> **hatmancan said:**
> oh just again i used no password for login then i used my password for desktop..
it will take me to dave-desktop $

what do i do here???

I am not exactly sure what you mean you used no password to log in then you have to use a password for desktop!  When you boot Ubuntu, do you see a GUI login screen?  Do you need to type in a password to log into your account from there?

What happens if you run this command at the prompt?

```
startx
```

---

### Post by hatmancan on 2008-11-08
i get to where kubuntu logo runs on screen and then has a lot of descriptions and takes me to a ubuntu 8.0.4 or something
wants my login password then
wants my dave-desktop..
if i hit enter it takes me to dave-desktop and i enter my password for sudo
then this takes me to dave-desktop $
this is far as i can get..
if you tell me how i can reboot and let you know all the descriptions..i will have to write them down and send on the other comp..
advise me pls.
ty
hat

---

### Post by taurus on 2008-11-08
Sounds like there is something wrong with X server; that's why it drops you into a console.

Reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Once it's done, restart X again with <Ctrl><Alt>Backspace.

And by the way, **[COLOR="Blue"]dave-desktop$[/COLOR]** is your prompt, not your desktop.

---

### Post by hatmancan on 2008-11-08
i will try and see what happens
ty taurus
hat

---

### Post by hatmancan on 2008-11-08
ok my promt is actually dave@dave-desktop~$ if this matters
below iswhat happens and just takes me back to above
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.20081108214244

any suggestions for this?
hat

---

### Post by taurus on 2008-11-08
Either restart your X again with <Ctrl><Alt>Backspace or reboot.

```
[COLOR="Blue"]dave[/COLOR]@[COLOR="Red"]dave-desktop[/COLOR]$~
```
[COLOR="Blue"]dave[/COLOR] is your login name.  [COLOR="Red"]dave-desktop[/COLOR] is the name of your machine/desktop.  ~ means that you are currently at your home directory, $HOME or /home/dave.

---

### Post by hatmancan on 2008-11-08
ok if i use startx it takes me to a grey screen and then brings up my ubuntu desktop.. i can see all my programs there..
only thing is i cannot switch to my kde desktop..
i am new to this os thing...should i reinstall all kde programs again..???
when i log out of ubuntu it only takes me to the prompt page again..and only way to log in is startx , but only way to shut down is by using button on the comp. not the way i need it to be(lol)
hat

---

### Post by hatmancan on 2008-11-08
here is what i get after reboot:
Kinit:name_to_dev_t(/dev/disk/by-uuid/c3b8982c-c4ed-484b-9f34-6353dd89d8ed)=s dd5(8,21)
Kinit:trying to resume from /dev/disk/by-uuid/c3b8982c-c4ed-484b-9f34-6353dd89d8ed
Kinit:no resume image,doing normal boot...
ubuntu 8.04.1 dave-desktop ttyl
dave-desktop login:

does this help
hat

---

### Post by taurus on 2008-11-08
If you want to use KDE instead of Gnome, at the GUI login screen, click Sessions at the bottom left corner and pick KDE from the list.

---

### Post by hatmancan on 2008-11-08
taurus that would be nice but i cannot get to that choice..i am always brought to m prompt login ifyou look in my last post
ty
hat

---

### Post by hatmancan on 2008-11-08
taurus is there anyway to repair the xserver???
having to log in every time this way is going to be painstaking?
should i reinstall kde?
can you help me out?
ty
hat

---

### Post by hatmancan on 2008-11-11
> **hatmancan said:**
> taurus is there anyway to repair the xserver???
having to log in every time this way is going to be painstaking?
should i reinstall kde?
can you help me out?
ty
hat

has anyone found a solution for this???
ty
hat

---

