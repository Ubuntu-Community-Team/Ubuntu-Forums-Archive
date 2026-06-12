---
title: "New install has no user"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by MarianHill on 2012-02-17
Don't ask me how, unless you really want to know.
I have a new install of [Ubuntu 10.04 "Lucid Lynx" Minimal CD]("http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/mini.iso") 12.5MB* (MD5: 7b383bcf55f09b1bb7e6614ed6e67a0e, SHA1: 40ea24c2c7a5a821d37fc93d5539f2160f7e1ef6)

I did the terminal expert install and I skipped the user & password part (thinking I was avoiding an annoyance I had on a previous install).

Bottom line is it boots to a black screen like this;

Ubuntu 10.04 LTS ubuntu tty1
ubuntu login:

I've tried user = Ubuntu and ubuntu
pass = nothing

I can boot to recovery mode and get a blank screen with only this;
root@ubuntu:~#

Any ideas?
From that prompt I go to /home# and there's nothing there

---

### Post by Bucky Ball on 2012-02-17
I would maybe start to google for how to create a new user and password. ;)

Here's a start:

[http://nixcraft.com/getting-started-tutorials/3293-create-new-user-account-ubuntu-linux-command-line.html](http://nixcraft.com/getting-started-tutorials/3293-create-new-user-account-ubuntu-linux-command-line.html)

... for instance:

```
sudo useradd MarianHill
```... or whatever you want to use. NB: if you are at 'root@ubuntu' you shouldn't need the 'sudo'.

On the other hand, if you have only just installed, maybe try again and this time include the user. You can't do much without one, obviously, and having a user and password is for security. Ubuntu won't run with no user registered. If the reason you left it out was because you didn't want to have to log in every boot, that can be switched off (although, again for security, not advisable). 

You need a user to change anything important on your machine (read: anything that will alter your machine setup).

PS: 10.04 LTS is stable, supported until April 2013, and a very good place to start.

PPS: Just noticed Minimal install. Can you supply a list of packages and apps you installed when you got to that part? This part needs to be well thought out and I generally use a pre-existing one from another user and change it to fit my needs. Did you install a desktop environment??? I prefer Xfce. One can get into all sorts of nightmares by missing a vital app or package. Remember; mini.iso *only* installs a base system (enough to get your hardware up ... hopefully), the rest is up to you (perhaps old news for ya).

You might try:

```
sudo startx
```

---

### Post by MarianHill on 2012-02-17
Thanks,
Really appreciate the help. I went ahead and reinstalled. It's still working on the problem. I was able to setup a user and password using this link [http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/](http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/)
But then I got to a prompt I'm not seen before just a $
I'm assuming that's all about starting a desktop "job"? I figured I may as well get back to the way normal people do it and just re-install right over the top.

---

### Post by Bucky Ball on 2012-02-17
Hold on though. Can you get online? I think you are omitting some packages. Can you provide the list you installed? Have you installed a desktop environment? Have you tried:

```
startx
```? You need to do the mini install with an ethernet cable plugged in (else you can't install apps/packages).

---

### Post by MarianHill on 2012-02-17
Currently it's installing all kinds of stuff "Installing the base system" 33% Yes it's got internet.
The other times I've installed ubuntu it was the full cd not the mini.

Will it give me some kind of a desktop at all?

---

### Post by Bucky Ball on 2012-02-17
Okay, you are going to get to a section where you need to install some packages after the bit it is on now. Here is where you install a DE, synaptics and whatever else you might need/want. I have a feeling you are missing this bit, perhaps. This is where you need to do some thinking and digging to find the command for your desired package. In short, you are looking at something like (example only):

```
sudo apt-get install synaptic firefox gcc thunderbird xfce4

```Get the picture? You may need more than this, naturally, to suit your requirements. What apps do you normally use? This is where you install them (although as you are installing a package manager you can install some later but others are essential at this point). 

Mini installs are extremely fast (as long as you don't install a full ubuntu-desktop in that last instruction!). Another point to remember is that the base system is the same for Xubuntu, Ubuntu and Kubuntu (and probably others) so the DE is up to you. 

 ;)

---

### Post by MarianHill on 2012-02-17
I got there and accidentally pressed enter ~ good heavens!
I got back though. Manual list is just mind boggling

I totally skipped this part the first time through...thanks

---

### Post by Bucky Ball on 2012-02-17
This is probably all you need:

```
sudo apt-get install gdm xorg xfce4
```... but will install xfce and NOT gnome. Add any other packages you need to that. I recommend adding 'synaptic' which will make it easier to install other stuff via the package manager, unless you are comfortable with a terminal, which is NOT included in that list unless xfce4 drags one in which is possible (it will include Thunar as file manager for instance but you can easily install nautilus or even include it in that list). Then there's this:

[http://www.stumbleupon.com/su/2CngWU/wiki.dennyhalim.com/ubuntu-minimal-desktop](http://www.stumbleupon.com/su/2CngWU/wiki.dennyhalim.com/ubuntu-minimal-desktop)

... and this:

[http://www.stumbleupon.com/su/2CngWU/wiki.dennyhalim.com/ubuntu-minimal-desktop](http://www.stumbleupon.com/su/2CngWU/wiki.dennyhalim.com/ubuntu-minimal-desktop)

... might help. I would replace fluxbox with another DE in the first link. As I say, for Xfce use 'xfce4' (without punctuation marks).

;)

---

