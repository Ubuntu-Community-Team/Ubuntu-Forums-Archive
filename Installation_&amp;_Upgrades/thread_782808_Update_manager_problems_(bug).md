---
title: "Update manager problems (bug?)"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by bsh on 2008-05-05
i saw there are multiple posts regards no updates in hardy etc.
my problem is a bit different, so i thought i open a new thread for that.

my install (on the file server in the office) was like: install 7.04 from a live cd, download all updates, then upgrade to 7.10, updates, then upgrade to 8.04. i use the default ubuntu (with gnome), but instead of gnome i use xfce (but it's not a "pure" xubuntu install, strictly speaking)

the server is not headless (yet), but i used to maintain it over vnc (because i am lazy to go there physically)

i have the following problems when i use vnc:

when i start the update manager, it shows a window "building dependency tree" (or something, my language is hungarian, but that's what it reads), and the progress bar stops and doesn't ever finish.

i tried changing the software sources, regardless of what server i choose, i get a dialog "downloading package information, file 2/14", and it doesn't move. when i open the files list there, i see many unsuccessful file downloads. the whole thing runs like half hour long (instead of just a few seconds), and finishes with an error: couldn't get files list, abort.

strangely enough, when i log in physically and do the above, everything works fine and fast, yet there are no updates.

if i select the main ubuntu server, i get 69 updates - other servers have no updates.

so... i dunno... the update manager is definitely not working with vnc for me, that's sure. i am not sure, why i don't get updates with my local ubuntu servers, only with the main server...

anyway, if anyone has any ideas, it's much appreciated.

---

### Post by az on 2008-05-05
Perhaps the updates have not propagated to the mirrors yet?

Also, maybe your network connection can't sustain the vnc traffic along with the downloading of packages at the same time?

---

### Post by bsh on 2008-05-05
> **az said:**
> Perhaps the updates have not propagated to the mirrors yet?

Also, maybe your network connection can't sustain the vnc traffic along with the downloading of packages at the same time?

i doubt the updates aren't propagated yet...

i doubt the other too. i'm on a LAN with a 768kbit internet, that 30kbyte/s that vnc might use, won't knock out the LAN... anyway, i tried to start the update then closed the vnc session to avoid this kind of traffic - to no avail.
and it's not just the downloads that don't work. the update manager itself doesn't work! it doesn't rebuild dependency trees over vnc, and things like that. it works fine on 7.04 and 7.10, but not on 8.04

---

### Post by cocjh1 on 2008-06-01
I'm experiencing the same problem.  My headless xubuntu 8.04 box is only accessible via VNC from another PC.  The update-manager kind of 'pauses' whilst during its execution.

At the start I simply terminated the program but have found that constantly moving the mouse cursor within the update-manager window allows it to continue.  Its as if the update-manager will only continue with some mouse input...

Anyone else seen this with ubuntu, uptate-manager via VNC.

Thanks,
Chris

---

### Post by N1LZ on 2008-07-30
Hi,
beside the update-manager my packet manager of gnome produces the same problems via vnc.

hope someone has an idea to fix it.

Greetz

---

### Post by subgeneric on 2008-11-14
I don't know if this is any help to anyone but I was having this problem and I managed to get around it.  I don't know what causes it but I assume it has something to do with vnc?  Anyway, I am using xubuntu on a headless desktop system and I use vnc to remotely control it.  I found that you can run x programs through ssh by running:

ssh -X username@hostname

So I just did that, got my ssh terminal, and then ran:

update-manager

And update manager loaded in a window on my local machine, for the remote system.  It loaded without any problems and I was able to update the remote machine.

An interesting side note, and possible security concern:  I log into my ssh session with my normal username, which doesn't have root privledge.  Normally when you run update-manager it will let you select updates and then when you apply them it asks for your root password.  However, it never prompted me for my root pass when running it through ssh.  Strange!

It looks like this is an old thread but I hope that helps!

---

### Post by PenzoiderS on 2008-12-02
Hi I have the same problem via VNC here on my headless xubuntu boxes.

I **WORKAROUND** like this:

Open a Terminal window and type: 

```
sudo apt-get upgrade
```

and if needed:

```
sudo apt-get dist-upgrade
```

to upgrade packets with changed dependencies.

then -if kernel upgrade simply reboot. ;)

hope it helps!

---

