---
title: "tried installing jaunty beta but it freezes at desktop."
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by imlinux on 2009-03-29
i have tried installing jaunty beta, but after booting successfully it freezes at desktop as if its a wall paper.there is no response to any click.my system configurations are pentium4 3ghzt with HT,82865 motherboard,512 mb ram.

---

### Post by SunnyRabbiera on 2009-03-29
It is a beta, I would expect errors.
Typically for new users I would avoid betas, they are nice to play with and file bug reports and such but I would not use it fulltime.

---

### Post by Piraja on 2009-03-29
> **imlinux said:**
> i have tried installing jaunty beta, but after boot successfully it freezes at desktop as if its a wall paper.there is no response to any click.my system configurations are pentium4 3ghzt with HT,82865 motherboard,512 mb ram.
Does it have an integrated Intel graphics card (e.g. of the type i845 or so)? If so, you might try adding 

```
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main
```

to your /etc/apt/sources.list (gksudo gedit /etc/apt/sources.list); then do 

sudo apt-get update

and accept the updates. After that, if this works, you might want to comment out the new lines in you /etc/apt/sources.list.

Worked for me, but don't take my word for it.

**Disclaimer**: They call themselves "[xorg crack pushers]("https://launchpad.net/~xorg-edgers/+archive/ppa")"...

---

### Post by imlinux on 2009-03-29
> **Piraja said:**
> Does it have an integrated Intel graphics card (e.g. of the type i845 or so)? If so, you might try adding 

```
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main
```

to your /etc/apt/sources.list (gksudo gedit /etc/apt/sources.list); then do 

sudo apt-get update

and accept the updates. After that, if this works, you might want to comment out the new lines in you /etc/apt/sources.list.

Worked for me, but don't take my word for it.

**Disclaimer**: They call themselves "[xorg crack pushers]("https://launchpad.net/~xorg-edgers/+archive/ppa")"...

how do i do that? its not even responding at desktop.

---

### Post by Piraja on 2009-03-29
> **imlinux said:**
> how do i do that? its not even responding at desktop.
**[NB (later edit/addition): Please read Roger's reply below! DO NOT hard-reset yet...]**

When X has completely stopped responding and even your keyboard does not work, you will either have to ssh from another machine or just hard-reset, i.e. press the power button a few seconds. After rebooting, choose "Recovery mode" from your GRUB boot options and when the recovery mode options come up, choose the root shell (or whatever it's called in the options screen). Then edit your /etc/apt/sources.list as explained above and do sudo apt-get update. After that, resume normal boot [**Oops**: you cannot just resume when you're in the shell, but instead, you need to "sudo reboot"]. I guess.

---

### Post by Piraja on 2009-03-29
Oh, sorry, I forgot one thing: If you are not familiar with terminal applications, you may wonder how to edit the sources.list file. You might want to use Nano:

nano /etc/apt/sources.list

EDIT: The key combinations you need with Nano are Ctrl+o to write the output to the file (i.e. save changes) and Ctrl+x to exit after editing.

Take it easy, installing a beta on older hardware is a way to learn a few things... you just need some patience and willingness to learn.

---

### Post by ramjet_1953 on 2009-03-29
> **Piraja said:**
> When X has completely stopped responding and even your keyboard does not work, you will either have to ssh from another machine or just hard-reset, i.e. press the power button a few seconds. After rebooting, choose "Recovery mode" from your GRUB boot options and when the recovery mode options come up, choose the root shell (or whatever it's called in the options screen). Then edit your /etc/apt/sources.list as explained above and do sudo apt-get update. After that, resume normal boot. I guess.

Bad advice.
You NEVER hard reset, unless nothing else works.
There is a key sequence that allows you to gain control of a frozen system.
It is called [COLOR="Blue"]Raising Skinny Elephants is Utterly Boring[/COLOR]

Here is the key sequence:

```
Alt SysReq R
Alt SysReq S
Alt SysReq E
Alt SysReq I
Alt SysReq U
Alt SysReq B
```

This key sequence safely allows you to re-start, without damaging any system files.

Regards,
Roger :)

---

### Post by Piraja on 2009-03-29
Thanks Roger! I'm a sort of novice myself, and have wondered what that mysterious [[COLOR="Blue"]Raising Skinny Elephants is Utterly Boring[/COLOR]]("http://en.wikipedia.org/wiki/Magic_SysRq_key") is all about. Now I know, then! Learning all the time...

---

### Post by imlinux on 2009-03-29
> **Piraja said:**
> 
nano /etc/apt/sources.list

EDIT: The key combinations you need with Nano are Ctrl+o to write the output to the file (i.e. save changes) and Ctrl+x to exit after editing.

Take it easy, installing a beta on older hardware is a way to learn a few things... you just need some patience and willingness to learn.
thank you so much ,i shall go for that adventure :)

---

### Post by Piraja on 2009-03-29
> **imlinux said:**
> thank you so much ,i shall go for that adventure :)
Good for you! Don't forget to Raise the Skinny Elephants before you go, even if it Is Utterly Boring!

Bon courage!

---

### Post by imlinux on 2009-03-29
> **Piraja said:**
> Good for you! Don't forget to Raise the Skinny Elephants before you go, even if it Is Utterly Boring!

Bon courage!
 oh yea sure,i won't:lolflag:

---

### Post by Sef on 2009-03-29
Moved.

---

