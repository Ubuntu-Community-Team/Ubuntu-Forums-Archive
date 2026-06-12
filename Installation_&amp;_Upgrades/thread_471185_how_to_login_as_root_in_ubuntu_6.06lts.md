---
title: "how to login as root in ubuntu 6.06lts"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by taimur on 2007-06-11
how can i get login as root in ubuntu 6.06lts to acess admin priv's

---

### Post by taurus on 2007-06-11
You can use the sudo in front of a command to run it as root.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by taimur on 2007-06-12
hi buddy i try this page thousand times but i can't understand bec. i m the beiggner plz give any link which help me with screen shots or help me out step by step

---

### Post by Vola on 2007-06-12
> **taimur said:**
> hi buddy i try this page thousand times but i can't understand bec. i m the beiggner plz give any link which help me with screen shots or help me out step by step


You have tree choises:

1 - Run any administrative command with sudo:
     example:   sudo apt-get update

2 - Get a root console with:   sudo -i 

3 - Set a password to root use r with: sudo passwd


The sudo command allow you (you = the first user created into the system) to run command with root permissions. This avoid to login as root for execute administrations

---

### Post by taimur on 2007-06-12
i want to use administrative rights not in console want to use in gui will my 1st made user during installtion or no problem if make new user
thanks

---

### Post by taurus on 2007-06-12
If you want to run a GUI app with root privilege, then use the gksudo, i.e.

```
gksudo nautilus
```
If you create another account, then you need to make sure that new account belongs to groups adm and admin (in /etc/group) so that account can use sudo/gksudo.

---

### Post by pwaldo on 2007-06-12
It sounds like you want to log in as root (from the beginning log in screen).  If that is what you are trying to do, you can't by default, you need to log in as another user.  If that user is the one that you created during the installation process, you can use the "sudo" command as decribed above.

---

### Post by taimur on 2007-06-12
ok i want to login as another user but with administrative rights with root rights....like i see on one ubuntu 6.06 lts windows when i open computer then file system on root folder i can see some logo of like home or something and i can change files directly no need to do any thing
that's wat i want i want to login as normal user as super user rights permanently
plz help me
thanks for ur copuration

---

### Post by SkyNet2029 on 2007-06-12
Although this does require you using the CLI, it wil get you where you want to be, at least as I understand what you are asking.

in a tty (from login screen hit CTRL+F1)

$sudo startx -- :2

that will give you a root access GUI. be careful though, as things can go bad rather quickly if you are not careful. NO prompts, NO advice, just you as a ROOT user with system-wide ROOT access.

Cheers !

---

### Post by taimur on 2007-06-13
i try it when i go to login screen with out typing any thing it says (answer questions here and press Enter ehen done. For a menu press F10)

then i also type this on terminal then something is going on and screen then noting something like it is finish then i go to computer,,,computer does not open actually i cannot open anything and then i connot suhutdown my computer the just i can is i can logout the login again it works fine but cannot access like a super user

plz help me out step by step i m the begiinner

---

### Post by taimur on 2007-06-14
plz answer my question

---

### Post by pwaldo on 2007-06-14
I'm guessing you want to modify GDM to allow root logins.  I'm using KDM, so I'm not much help on the details.  

A quick google search says to modify
"/etc/X11/gdm/gdm.conf, set AllowRemoteRoot=false and AllowRoot=true."

Does this work for you?

---

### Post by taimur on 2007-06-14
thanx buddy for your help i try it but i dosen't work i need root access very badly i don't know wat to do...and i want permentally not temporary like don't want to use sudo or gksudo

---

### Post by pwaldo on 2007-06-15
Log in as the user you created during install.
Open a terminal
Type "sudo passwd root" 
When you see the prompt that says "Enter new UNIX password", enter the password you want for the root user.  You will be asked to confirm by typing it again.
Type "sudo gedit /etc/X11/gdm/gdm.conf"
Locate the line that says "AllowRoot=false"
Change it to say "AllowRoot=true"
Save the file
Exit gedit
Logout and reboot

Hopefully you will then be able to log in as root.  

Please be aware that that you are throwing away all protection afforded you by the Unix permission model by using root as your day-to-day login.  I highly encourage you to reconsider, and use your initially created user for non-administrative functions.  When you need to do something as root, you should use "sudo".

You have been warned, but good luck!

---

### Post by taimur on 2007-06-17
thanx budy for your help it really works

---

### Post by SkyNet2029 on 2007-06-23
I still don't understand what you did so as not to get things working to give you a full gui with root access
by way of 
CTRL+ALT+F1
and then logging in as your normal user account. at the prompt all you do is type

```
$sudo startx -- :4
```

then hit enter. That should have opened a second xserver up and logged you in as root in a gui.

NOTE: This cannot be run in a terminal like Konsole,xterm, etc...

---

