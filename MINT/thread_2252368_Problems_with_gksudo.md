---
title: "Problems with gksudo"
date: 2014-11-11
forum: MINT
---

### Post by ben124 on 2014-11-11
I've been running Mint for a while. I'm trying to reinstall samba, but am having an issue. In the terminal I can't use gksudo to run anything. If I try to run nautilus from the terminal it asks for my password. When I enter the password, nothing happens. Any help? Just updated everything.

---

### Post by slickymaster on 2014-11-11
*Moved to the ***MINT*** sub-forum*

---

### Post by ben124 on 2014-11-11
Sorry, thanks.

---

### Post by Frogs Hair on 2014-11-11
The gksu package is no-longer installed by default in Ubuntu , but I'm not sure about Mint. Gksu is a dependency of some programs and some people install it without realizing it.

---

### Post by ben124 on 2014-11-11
I've installed/reinstalled gksudo. I don't think that's the problem. I'm prompted for my password but when I enter it, I get nothing - no error message, no blank screen, it just returns me to the terminal like nothing happened.

---

### Post by ben124 on 2014-11-11
I've installed/reinstalled it. I'm trying to modify smb.conf, using 'gksudo gedit /etc/samba/smb.conf' it prompts me for my password, but when I enter it, nothing happens. No error message or anything, I'm just returned to the terminal screen.

---

### Post by coffeecat on 2014-11-11
I doubt that this is the problem, because if it was, you should see a wrong password error, but let's check this anyway.

From a terminal:

```
gksu-properties
```

Make sure that authentication mode is set to sudo.

---

### Post by Frogs Hair on 2014-11-11
Mint uses different default file managers depending on version and desktop environment so if you are running Cinnamon or Mate you might not have Nautilus.

---

### Post by ben124 on 2014-11-11
Authentication is set to sudo, and I'm running Mate.

---

### Post by mc4man on 2014-11-11
what does this produce - 
```
sudo -H gedit /etc/samba/smb.conf
```

---

### Post by Frogs Hair on 2014-11-11
Mate uses caja so you might try the following.

```
gksudo caja 
```

---

### Post by ben124 on 2014-11-11
Prompts me for my password, and then this: 
"sudo: gedit: command not found"

---

### Post by coffeecat on 2014-11-11
> **ben124 said:**
> Prompts me for my password, and then this: 
"sudo: gedit: command not found"

Which means gedit is not actually installed. I would have thought gedit was the default GUI text editor in Mint Mate, but I don't have recent experience of Mint. Try installing gedit or do you know what the default text editor is?

---

### Post by Dennis N on 2014-11-11
Just tried it, and I can confirm that **gksudo caja** works in the MATE Desktop Enviroment to open the file manager (Caja) as 'root'.

---

### Post by coffeecat on 2014-11-11
Cough cough: [http://mate-desktop.org/](http://mate-desktop.org/)

> Pluma is a text editor which supports most standard editor features. It also extends this basic functionality with other features not usually found in simple text editors. Pluma is a graphical application which supports editing multiple text files in one window (known sometimes as tabs or MDI). Pluma fully supports international text through its use of the Unicode UTF-8 encoding in edited files. Its core feature set includes syntax highlighting of source code, auto indentation, and printing support (with print preview). [B]Pluma is a fork of Gedit.
[/B]

Have you ever run "gedit" from the terminal. My guess is you would need to:

```
gksu pluma /etc/samba/smb.conf
```

Or:

```
sudo -H pluma /etc/samba/smb.conf
```

---

### Post by ben124 on 2014-11-11
Thanks. Will try this. It's a bit beyond my depth I think which is why I end up getting confused. Trying to set up a share folder between my linux box and windows 8.1. It was working, but all the sudden my linux box can't just shows an empty smb:///. Hoping to tweak things...

---

### Post by coffeecat on 2014-11-11
Good luck, but this thread is getting a bit confused. It started off with the emphasis on you being unable to start the file manager with gksudo, then moved to the text editor. I would imagine that was a simple application naming issue, so let us know if using "caja" and "pluma" is the answer for those two.

If you are needing help with configuring smb.conf, I suggest you start a new thread with a descriptive title which will attract those best able to help with samba shares.

---

### Post by ben124 on 2014-11-11
I'm hoping the first part works, and then as you suggest, I was planning on starting a new thread...

---

