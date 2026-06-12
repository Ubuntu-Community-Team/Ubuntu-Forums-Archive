---
title: "need to switch from Lubuntu to Ubuntu"
date: 2017-10-07
forum: Installation &amp; Upgrades
---

### Post by Dreadsen on 2017-10-07
Hello 

I had a problem with ubuntu being stuck in login loop.

I followed some instructions that had me switch to Lubuntu and from there applied some remedies that fixed the loop problem.

But now I'm stuck with lubuntu, no task bar, folder launcher, nothing. Just a plain lubuntu screen and a mouse pointer.

How do I switch back to ubuntu and get my old out of the box desktop back?

---

### Post by RobGoss on 2017-10-07
How did you switch to Lubuntu from Ubuntu, did you do a clean installation?

---

### Post by Dreadsen on 2017-10-07
No it wasn't a clean installation. 

Same files, same hard drive encryption password.  

Same log on password. 

Everything stayed the same

---

### Post by RobGoss on 2017-10-07
I would suggest making a complete backup of any important data and files, download what version of Ubuntu you want to install and do a clean installation to avoid problems like this. I for one do not know how to convert over from one distribution to another with out doing a clean installation.

---

### Post by Dreadsen on 2017-10-07
Oh I see this is what I did.

It installed lubuntu desktop environment. But it's still ubuntu

[https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)


Does this help explain what happened?

---

### Post by mörgæs on 2017-10-08
I agree with the poster above: Try a clean install of Lubuntu. It will give people here a much better foundation for helping.

---

### Post by Dreadsen on 2017-10-08
It's still ubuntu this was the command

sudo apt-get -y install lubuntu-desktop

This will install a much lighter desktop environment which should work for now (should enable you to login and use your computer). Once that is done, reboot (sudo reboot), and when you are confronted with the login page, select the Lubuntu environment instead of Ubuntu."

I'm trying to understand what happened. In terminal it says it's ubuntu.   But the login screen say lubuntu. 

What did that command do? It didn't install lubuntu it just changed the appearance.   I guess I can go find a large enough external drive to back the files up and do a clean install.   But I'd still like to know what those instructions did

---

### Post by vanadium on 2017-10-08
In your case, a reinstall might not be needed. Try solving the login loop issue using the instructions you linked to. You can easily do that from within your working Xubuntu session. Then log out, and when logging in, select the Ubuntu session to check whether the issue was solved successfully.

if you try to understand what happened: a login loop may be caused by wrong permissions of a configuration file .Xauthority. This can happen if you incorrectly run graphical programs as root. Next time, you can't graphically log in anymore because of that.
Wat you did was to install the lubuntu desktop. This installs the lubuntu desktop next to your regular Ubuntu desktop. At login time, you can select (clicking the cog icon) what session you can use. In your case, you will have an Ubuntu and a Lubuntu session.

---

### Post by Dreadsen on 2017-10-08
> **vanadium said:**
> In your case, a reinstall might not be needed. Try solving the login loop issue using the instructions you linked to. You can easily do that from within your working Xubuntu session. Then log out, and when logging in, select the Ubuntu session to check whether the issue was solved successfully.

if you try to understand what happened: a login loop may be caused by wrong permissions of a configuration file .Xauthority. This can happen if you incorrectly run graphical programs as root. Next time, you can't graphically log in anymore because of that.
Wat you did was to install the lubuntu desktop. This installs the lubuntu desktop next to your regular Ubuntu desktop. At login time, you can select (clicking the cog icon) what session you can use. In your case, you will have an Ubuntu and a Lubuntu session.

yes i do not think so.  okay i no longer have the login loop.   but now this where i am at.    its like i have ubuntu with lubuntu at the same time.  i'll post photos of what happens now when i boot up.  i get the burgundy screen from ubuntu but then it goes to these lubuntu .  

but if i hit ctrl , alt f3  you can see it is still ubuntu.  

the login loop is resolved.  now i want the ubuntu environment back

---

### Post by again? on 2017-10-08
When you install lubuntu-desktop you will be able to choose the Lubuntu session from the panel at the greeter.
This command tells you what desktop session you are in.
```
echo $DESKTOP_SESSION
```

---

### Post by Dreadsen on 2017-10-09
> **guber2 said:**
> When you install lubuntu-desktop you will be able to choose the Lubuntu session from the panel at the greeter.
This command tells you what desktop session you are in.
```
echo $DESKTOP_SESSION
```

Yes I just did this. Ubuntu was pre selected. Immediately after I sign in that top bar disappears.

---

### Post by vanadium on 2017-10-09
Reset your unity settings to factory default. Open a terminal and issue following commands:
```

dconf reset -f /org/compiz/
setsid unity

```

To have the default login screen back, edit the

```

gksudo gedit /etc/lightdm/lightdm.conf

```

Make sure user-session and greeter-session look like:

```

user-session=ubuntu 
greeter-session=unity-greeter

```

---

### Post by Dreadsen on 2017-10-09
> **guber2 said:**
> When you install lubuntu-desktop you will be able to choose the Lubuntu session from the panel at the greeter.
This command tells you what desktop session you are in.
```
echo $DESKTOP_SESSION
```

Thanks. I tried that. Ubuntu was already selected. 
Th after I signed in that top menu bar disappeared. 

So my session is ubuntu but it still is in that lubuntu environment

---

### Post by again? on 2017-10-10
Does "echo $DESKTOP_SESSION" show **Lubuntu** when you are logged into the **ubuntu** session.?
What happens when you log into the Lubuntu session then?
The lubuntu session has it's own default applications and panel.
[ATTACH=CONFIG]277072[/ATTACH]

Did you try running vanadium's suggestion.
```
dconf reset -f /org/compiz/
```
Then logging out and into the Ubuntu session.

---

### Post by Dreadsen on 2017-10-11
On the first command this is what happened

---

### Post by Dreadsen on 2017-10-11
> **vanadium said:**
> Reset your unity settings to factory default. Open a terminal and issue following commands:
```

dconf reset -f /org/compiz/
setsid unity

```

To have the default login screen back, edit the

```

gksudo gedit /etc/lightdm/lightdm.conf

```

Make sure user-session and greeter-session look like:

```

user-session=ubuntu 
greeter-session=unity-greeter

```

This is what happened after I tried the 2nd command

---

### Post by again? on 2017-10-11
The commands given by vanadium are meant to be run from a graphical session not a tty terminal(ctrl+alt+F1)
If you cannot log into either the Ubuntu session or the Lubuntu session, I suggest as others have said...backup and reinstall.
When you don't fully understand what you're doing it's hard to figure out what's wrong or how to fix.

PS A tty terminal shows "Ubuntu" at the top because whether or not Lubuntu is installed the base files are still Ubuntu
and you're not logged into a graphical environment.
All the sessions selectable at the greeter use the same Ubuntu base files.
Lubuntu uses the LXDE desktop environment in place of Ubuntu's Unity graphical shell.

---

