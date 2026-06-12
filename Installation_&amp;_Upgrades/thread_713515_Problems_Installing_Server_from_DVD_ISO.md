---
title: "Problems Installing Server from DVD ISO"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by dsbw on 2008-03-02
I'm trying to install a Feisty server from a DVD ISO.

The image MD5 checks out. The burned DVD checks out.

The installation works up until the Select and Install software part. 

The syslog complains about "couldn't find task [software package]".

If I select the items I want (everything but Postgres and Print servers), I get errors on maill-server, ssh-server and samba-server. If I take those out (leaving DNS, LAMP and Ubuntu)...Well, wait,now it seems to be working. (Before, it seemed like I had to take everything out of the software installation list, but I guess that was the CD version.)

I almost wonder if it's some sort of hardware issue (as improbable as that seems to me) since I tried the same thing with the CD server version and had a similar problem. Come to think of it, I'm pretty sure I had this exact same problem with the machine this one is replacing.

The error always occurs after I'm required to pick screen resolutions. And probably significantly, the desktop doesn't start up. It didn't start up with the CD version, either. 

This is from a fresh install, every time. I'm not trying to preserve anything.

I guess my installation is okay and I just have to manually install the mail, ssh and samba servers, but the process lacks those Ubuntu good vibes. I saw other people with similar issues but not anything that really resolved it.

Meanwhile, is there an easy way to figure out (and install) what packages are used by the mail, ssh and samba server options?

Thanks!

---

### Post by louieb on 2008-03-02
First bring your new installation up to date ```
sudo aptitude update
``` then ```
sudo aptitude dist-upgrade
```
The easy way to find the packages your asking about run ```
sudo tasksel
```

---

### Post by dsbw on 2008-03-02
Thank you, sir!

---

### Post by dsbw on 2008-03-02
Oh, I've managed somehow in this to make it so that when I go to a command-line Ctrl+Alt+F7 doesn't bring me back to the desktop. (It just gives me a black screen with a blinking cursor. X/Gnome is still runing, I just can't figure out how to get back to it....

---

### Post by louieb on 2008-03-03
Use the ```
finger 
```command to find which tty X is using. I've noticed that sometimes after killing the x server it starts back up on tty8 .

---

### Post by dsbw on 2008-03-07
tty7 is working now. Weird. I'll keep that tty8 option in mind though if it happens again.

---

