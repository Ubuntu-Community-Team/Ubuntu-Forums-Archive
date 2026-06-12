---
title: "Help with upgrades"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by JJR12 on 2008-07-02
So I recently installed 8.04 and I am running into some issues.  I can't connect wireless even though it sees my card.  

But my question relates to something else for now....  I am a newbie so please bear with me.  After install I noticed I had 205 upgrades... so I install upgrades and I now come up with this message...

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What does that mean??  How do I fix it??

Thank you

---

### Post by Partyboi2 on 2008-07-02
Open a terminal (Applications>Accessories>Terminal) and do what it suggests
by typing
```
sudo dpkg --configure -a
```

---

### Post by davec64 on 2008-07-02
Hop this helps:)
I took this from the MAN page of DPKG. To see it for yourself run 
```
man dpkg
```
in a terminal.
It gives a lot of information!

       --configure package...|-a|--pending
              Reconfigure an unpacked package. If -a  or  --pending  is  given
              instead  of  package, all unpacked but unconfigured packages are
              configured.

              Configuring consists of the following steps:

              1. Unpack the configuration files, and at the same time back  up
              the  old  configuration  files,  so that they can be restored if
              something goes wrong.

              2. Run postinst script, if provided by the package.

---

### Post by swan23 on 2008-07-02
Hei!
I have the same problem, but I cant fix it...the terminal says that I need Super User rights...I am the administrator...isnt it the Super user????
How can I fix it???????

---

### Post by Partyboi2 on 2008-07-02
To gain super user privileges put sudo infront of the command. So
```
 dpkg --configure -a
``` would become[FONT=monospace]
[/FONT]```
sudo dpkg --configure -a
``` You can read more about sudo from[URL="https://help.ubuntu.com/community/RootSudo"][COLOR=Blue] here[/COLOR]
[/URL]

---

### Post by swan23 on 2008-07-02
But then he aks for the password, and if i type it, he said, that the password is wrong...

---

### Post by Partyboi2 on 2008-07-02
If you have not already done so try a few more times, maybe you accidentally pressed the wrong key (Happens to me often) Remember that linux is case sensitive, if you have no uppercase letters in your password make sure that the caps lock is off.

---

