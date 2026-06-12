---
title: "Where in the hell is &quot;COMPRESS&quot; utility for .Z files ?!?!?!"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by asbesto on 2007-07-23
[I]

root@gemini:~# compress
The program 'compress' is currently not installed.  You can install it by typing:
apt-get install ncompress
Make sure you have the 'universe' component enabled
-su: compress: command not found
root@gemini:~# 

[/I]

I have no words; a fundamental utility for every UNIX in the world is not present.

apt-cache search compress slap me in the face

and so I can't open files with .Z suffix.

This is REALLY AN HORROR :(

can someone help?

p.s. slackware and many other distro's have compress by default, as it MUST be.
:confused:

---

### Post by Seisen on 2007-07-23
Follow what is says

```
 apt-get install ncompress
```

---

### Post by asbesto on 2007-07-23
???

:confused::confused::confused:

N-compress ??

"N" compress ?!?!?!?

UNBELIEVEBLE

only DEBIAN can do those weird bullshits!!!!! 


:confused::confused:

---

### Post by notwen on 2007-07-23
wow, all you had to do was simply copy/paste the command that was echoed in your terminal to resolve your issue and you make a post to babble about it's differences from UNIX. :confused::confused:

---

### Post by Espreon on 2007-07-23
CALM DOWN:

I think he means do this in an terminal:

```
sudo apt-get install compress
```

---

### Post by dannyboy79 on 2007-07-23
are you talking about zip files or are you talking about gunzip files? please post the exact filename and extension of the file. If you do want to install a program to open  a .z file in fact, then do as it suggests and install ncompress. You'll also be shocked to find that no developer tools are installed by default either, like gcc, a compiler, etc etc. You'll need to install a package called build-essential to have the ability to compile stuff.

"only DEBIAN can do those weird bullshits!!!!! "

if you don't like using debian based distro, I am sure you're not forced to be using it, so don't use it. It will do you know good speaking like this within the forums. Ubuntu is Ubuntu, NOT Slackware or any other distro, it's Ubuntu so there'll be some differences.

---

### Post by Espreon on 2007-07-23
dannyboy is right if you think bad of Debian and its deratives like Ubuntu use something else. I suggest Sabayon (I heard it is kick-***).

---

