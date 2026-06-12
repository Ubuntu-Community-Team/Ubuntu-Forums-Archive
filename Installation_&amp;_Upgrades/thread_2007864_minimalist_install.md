---
title: "minimalist install"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by buffchick on 2012-06-21
so, I want to use ubuntu desktop because I love unity but, I don't want/need 95% of the stuff that comes installed with it like office or movie players or calculators or pretty much anything else. Is there any way to do this? I've tried the minimal install CLI and added ubuntu desktop, alternate cd install, and regular install. I've googled like crazy but most articles are for ubuntu 9/10 with gnome. Can anyone point me in the right direction?

---

### Post by MG&amp;TL on 2012-06-21
> **buffchick said:**
> so, I want to use ubuntu desktop because I love unity but, I don't want/need 95% of the stuff that comes installed with it like office or movie players or calculators or pretty much anything else. Is there any way to do this? I've tried the minimal install CLI and added ubuntu desktop, alternate cd install, and regular install. I've googled like crazy but most articles are for ubuntu 9/10 with gnome. Can anyone point me in the right direction?

The *ubuntu-desktop* package is the one that provides all of that stuff. If you just want unity, you probably want the packages *unity-greeter* (for the login) and *unity* (for the desktop)

---

### Post by buffchick on 2012-06-21
oooo. now I feel really dumb! THANK YOU!

---

### Post by buffchick on 2012-06-21
Oh, one other question, does the minimal cd install the desktop kernel?

---

### Post by cortman on 2012-06-21
> **buffchick said:**
> Oh, one other question, does the minimal cd install the desktop kernel?

As of Ubuntu 10.10 the kernels were merged.
+1 for the minimal CD- I use it myself for all my Ubuntu installations. If you need any help getting x started or a DE, post back. Good luck!

---

### Post by buffchick on 2012-06-22
so, I followed these guidelines [https://help.ubuntu.com/community/Installation/MinimalCD#A64-bit_PC_.28amd64.2C_x86_64.29](https://help.ubuntu.com/community/Installation/MinimalCD#A64-bit_PC_.28amd64.2C_x86_64.29) and then ran apt-get install unity unity-greeter and I am unable to login. It keeps flipping me back to the unity greeter with a quick flash of error message that goes by too fast for me to see what it is and I'm not sure which log file to check. dmesg? syslog? Just point me in the right direction. Show me once and I remember forever. :D

---

### Post by buffchick on 2012-06-22
> **cortman said:**
> As of Ubuntu 10.10 the kernels were merged.
+1 for the minimal CD- I use it myself for all my Ubuntu installations. If you need any help getting x started or a DE, post back. Good luck!
oh... then... why won't ksplice work with the server version? Only the desktop version?

---

### Post by MG&amp;TL on 2012-06-22
> **buffchick said:**
> so, I followed these guidelines [https://help.ubuntu.com/community/Installation/MinimalCD#A64-bit_PC_.28amd64.2C_x86_64.29](https://help.ubuntu.com/community/Installation/MinimalCD#A64-bit_PC_.28amd64.2C_x86_64.29) and then ran apt-get install unity unity-greeter and I am unable to login. It keeps flipping me back to the unity greeter with a quick flash of error message that goes by too fast for me to see what it is and I'm not sure which log file to check. dmesg? syslog? Just point me in the right direction. Show me once and I remember forever. :D

I don't know which logs you'd want to check, but swtich to a tty login(Ctrl-Alt-F1), then run:

```
sudo service lightdm restart
```then try and login as normal. Get the problem (as normal), then switch back to the tty and see if there's any helpful output.

Also, you have installed the *unity* package...right? Obviously the greeter won't work if there's no environment available.

> **buffchick said:**
> oh... then... why won't ksplice work with the server version? Only the desktop version?

My guess is that ksplice is a graphical app and requires a GUI...unless it's more subtle than that?

*Hey Cortman! I've been a bit busy for a few days, but I'll probs be back on with you guys soon. ;)*

---

### Post by buffchick on 2012-06-22
> **MG&TL said:**
> My guess is that ksplice is a graphical app and requires a GUI...unless it's more subtle than that? I have a server that I installed a gui on. I know I know. Security. I read that page on the ubuntu wiki. I was mostly just playing around.

Thanks for all the tips! question, how unbloated is ubuntu-desktop --no-install-recommends?

---

### Post by cortman on 2012-06-22
> **buffchick said:**
> so, I followed these guidelines [https://help.ubuntu.com/community/Installation/MinimalCD#A64-bit_PC_.28amd64.2C_x86_64.29](https://help.ubuntu.com/community/Installation/MinimalCD#A64-bit_PC_.28amd64.2C_x86_64.29) and then ran apt-get install unity unity-greeter and I am unable to login. It keeps flipping me back to the unity greeter with a quick flash of error message that goes by too fast for me to see what it is and I'm not sure which log file to check. dmesg? syslog? Just point me in the right direction. Show me once and I remember forever. :D

Are you wanting to install a login manager? If you're going Gnome, use GDM or LightDM. If something lighter, try LXDM. Or you could skip it altogether, of course- log in from the CLI and run startx.
I would uninstall unity-greeter.

> **buffchick said:**
> I have a server that I installed a gui on. I know I know. Security. I read that page on the ubuntu wiki. I was mostly just playing around.

Thanks for all the tips! question, how unbloated is ubuntu-desktop --no-install-recommends?

Don't do ubuntu-desktop period if you want minimalism.
Are you looking for essential packages to install to get a GUI?

> **MG&TL said:**
> 
*Hey Cortman! I've been a bit busy for a few days, but I'll probs be back on with you guys soon. ;)*

Awesome, pal! Look forward to seeing you around. :D

---

### Post by MG&amp;TL on 2012-06-22
> **buffchick said:**
> I have a server that I installed a gui on. I know I know. Security. I read that page on the ubuntu wiki. I was mostly just playing around.

Thanks for all the tips! question, how unbloated is ubuntu-desktop --no-install-recommends?

```
apt-cache depends ubuntu-desktop
```

...might answer your question. ;)

---

### Post by LiamOS on 2012-06-22
> **buffchick said:**
> so, I want to use ubuntu desktop because I love unity but, I don't want/need 95% of the stuff that comes installed with it like office or movie players or calculators or pretty much anything else. Is there any way to do this? I've tried the minimal install CLI and added ubuntu desktop, alternate cd install, and regular install. I've googled like crazy but most articles are for ubuntu 9/10 with gnome. Can anyone point me in the right direction?
If you feel this way, I might take this opportunity to sway you towards looking at some other distributions. There are a fair few out there which are reasonably minimalist and based on Ubuntu, or you could even give Debian a go. 
If you love unity, you could try other desktop environments and add in a dock or something similar. You may even be able to get Unity on Debian, I'm not sure.

As for how unbloated ubuntu-desktop --no-install-recommends is, I'd put it as 'very', in comparison to regular Ubuntu; you won't even have Firefox or gcc. :O

---

### Post by MG&amp;TL on 2012-06-22
> **LiamOS said:**
> 
If you love unity, you could try other desktop environments and add in a dock or something similar. You may even be able to get Unity on Debian, I'm not sure.


Couple of comments (not intended as dig at you, just comments):

-Unity isn't just a dock, y'know. Might have been in 11.04....I think I'd find it rather hard to replace unity now.

-My understanding is that Ubuntu has modified Unity's backends rather too much for Unity to run on other distros. Arch apparently tried it and gave up. No other distros have Unity, although I believe that downstream distros could theoretically have it.

---

### Post by buffchick on 2012-07-09
yup. that's about it. I just want ubuntu with unity/unity greeter without firefox or all that other stuff. I'm going to be running nagios on it but, I also don't want to restart it every time there's an update so I want to use ksplice. Ksplice doesn't support ubuntu server and requires a graphical interface. I never liked gnome so I want unity. Make sense? There has to be an easy way to do this. :D

P.S. Sorry about the delay in response. I got hit by a drunk driver and I've been laid up in the hospital.

---

