---
title: "[SOLVED] Dual booting Ubuntu 7.10 &amp;amp; Kubuntu 7.10 (?)"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by Multi-Booter on 2007-11-21
OK, I never did have much luck with the Kubuntu 6.06 that I installed, and I had trouble with editing grub with it too.

I blew it out tonight, so it is history now too.

I decided to do this a while ago after trying an Ubuntu 7.10 live CD. All seems to work much better with it.

So now I want to install it, but I also want to be able to play with both desktop environments. I want more experience with KDE.

So I am wanting to install and boot both.
Is this possible and if so, is there a preferred sequince?
Like can I do Ubuntu now and add Kubuntu later?
Will grub be overwritten by the last one installed?


[b]And of course, last of all.... is there not a way to just add KDE to Ubuntu and switch back and forth?
Just wondering since I did with Fedora.[/b]

---

### Post by 1/0 on 2007-11-21
The thing is that you are running the exact same operating systems so I don't see why you should dual boot. Instead set the display manager such as gdm or kdm to load different desktop managers. That way you can only install gnome without installing the same OS twice...

---

### Post by MrFSL on 2007-11-21
Exactly - when you are at the login screen you can choose which one you wish to use.

---

### Post by 1/0 on 2007-11-21
Guess I could have written more. To install Gnome on to your Kubuntu do this:
```
sudo apt-get install ubuntu-desktop
```

For KDE on Ubuntu just change the above to kubuntu-desktop

Then when you've booted to KDM select under session whether you want to run Gnome, KDE or whatever (fluxbox, xfce, e17...)

---

### Post by Multi-Booter on 2007-11-21
OK, good... so I can do it sorta like Fedora then.

That's what I was hoping for rather than having to install both.
I'm just going to put on Ubuntu 7.10.
Then after running it a while, when I get the itch I'll install KDE.

Thanks

---

### Post by Multi-Booter on 2007-12-01
Well I did it... and I am REALLY liking it... so far especially because I also get to have some Gnome stuff in with the KDE. I like it better than the Kubuntu I had.

I do have a problem though.
My sound does not work in KDE.
Any ideas?


Also, I didn't know which desktop manager to choose, so I went with KDM because I remembered you wrote that. What is different in the other option? (GDM?)

---

### Post by Multi-Booter on 2008-01-01
Well, I still haven't gotten the sound to work in KDE...
But I'm going to mark this one solved... as by the title it is solved.

---

