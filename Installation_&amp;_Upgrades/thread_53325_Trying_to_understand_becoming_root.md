---
title: "Trying to understand becoming root"
date: 2005-07-31
forum: Installation &amp; Upgrades
---

### Post by Hamster. on 2005-07-31
Hi,

I've just installed Kubuntu, having come from using debian for several years.

I'm trying to understand what kubuntu has done to the root user - I don't understand at all.

During the install process I chose "expert install" and gave root a password when requested.

If I go to a terminal (by hitting ctrl-alt-1, ctrl-alt-2 etc), I can log in as root with no problems.

But under Konsole in KDE, if I type `su -` and try to become root that way, it gives me an error "su: Authentication failure".

Now I've read the wiki entry at [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) and it says that root is disabled. But my understanding of the situation on my machine is that root is *not* disabled - `cat /etc/shadow` clearly shows a root password, and the fact remains that I can login to a console as root. I just can't do so from a terminal in konsole.

Can someone explain to me why `su -` works in a terminal, but not in konsole? And how do I make `su -` work in console? 

I really am quite confused.

Hamster.

---

### Post by kosmic on 2005-07-31
hum, i'm runing Ubuntu (gnome) not kubuntu, but in ubuntu if I do an expert install I can also choose the root password, and in a console  or terminal I can do su - with no problem's, it looks like a bug in kubuntu.

---

### Post by erisco on 2005-07-31
I am using ubuntu and in the install, from my understanding I would have entire control of the system. Well, that doesn't seem to be true.... I can't get to the root user... Is there any way I can set the root user up? I seem to have just made a typical user.... that can't alter anything in the root directory.

---

### Post by az on 2005-07-31
Does "su" work, as opposed to "su -"?

---

### Post by erisco on 2005-07-31
su - 
Brings me to root =0
But couldn't i just do 
cd /
and get the same result? As far as a gui point of view, could I log into root? And have root gui?

---

### Post by Hamster. on 2005-07-31
[QUOTE=erisco]I am using ubuntu and in the install, from my understanding I would have entire control of the system. Well, that doesn't seem to be true.... I can't get to the root user... Is there any way I can set the root user up? I seem to have just made a typical user.... that can't alter anything in the root directory.[/QUOTE]

I believe you might be looking for the link below. Root is disabled by default

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by erisco on 2005-07-31
hamster, thanks for the verification... I was just learning about that shortly after I posted my post. Though that page made things very clear, thanks again. It will be something to bookmark =0

---

### Post by kevlar16 on 2005-07-31
Hamster,
Try switching to root user by typing: sudo -s -H followed by user password. 
If that still doesn't work, then enable the root account by typing: sudo passwd root
- Goodluck

---

### Post by Hamster. on 2005-08-01
[QUOTE=kevlar16]Hamster,
Try switching to root user by typing: sudo -s -H followed by user password. 
If that still doesn't work, then enable the root account by typing: sudo passwd root
- Goodluck[/QUOTE]

As I said above, the root account *is already enabled*.

In any case, the problem seemed to fix itself when someone on IRC told me to add updates to my sources.list. The problem seemed to fix itself.

Thanks though!

---

