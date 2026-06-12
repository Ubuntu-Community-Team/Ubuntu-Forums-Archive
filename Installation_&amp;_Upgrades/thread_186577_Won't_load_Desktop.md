---
title: "Won't load Desktop"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by kuratkull on 2006-06-02
I upgraded from Breezy by changing the labels in the repositories from Breezy to Dapper. The install displayed errors something about icons and stuff.
After the install I did sudo apt-get install -f and that displayed some errors too.
After a reboot it loaded XFCE(before the upgrade my default was gnome, Fxce wasn't even installed, i think) login screen and i entered my logins. When i pressed Log in it displayed the Root console(asking username) for a second and then threw me back to the login window. And this just keeps repeating :/

Anyone know what to do? I'm desperate, i can't wait until my free CD's ship to fix it.


Thanks

---

### Post by Harold P on 2006-06-02
Once you're logged in try:

```
startx
```

---

### Post by kuratkull on 2006-06-02
Well i used repair console(or whatever it's named), and I typed startx and i got in, xfce(writing from there now). But i still need it to load normally. Any tips how to repair this?
Are there any logs i can show you? Or something.

---

### Post by kuratkull on 2006-06-02
how can i fix the X loading sequence or something after inserting the login credentials. HELP! :(

---

### Post by ubuntu_demon on 2006-06-02
first make sure that there are no broken dependencies and the upgrade went allright. Look here :

[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

If that doesn't work use cat or pico to view these files :
$ cat /var/log/Xorg.0.log
$ cat ~/xsession-errors 

You could boot from a live-cd, mount your Dapper partition so you can post these files here. I've explained in my guide how to mount a partition from a live-cd.

---

### Post by kuratkull on 2006-06-03
I CAN get into Xubuntu when i startx from the repair console. So i'm using Xubuntu right now. But I did everything according to [http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)
and it didn't show errors.
When I want to log in normally:
1)I insert my login credentials
2)PRess login
3)The screen goes blank for a sec, then shows a console for a sec and then loads the loginmanager again(i know this because it shows the nvidia white screen again).

[http://koffer.ee/kuratkull/ubuntinf/Xorg.0.log](http://koffer.ee/kuratkull/ubuntinf/Xorg.0.log)
[http://koffer.ee/kuratkull/ubuntinf/lspci](http://koffer.ee/kuratkull/ubuntinf/lspci)

I'm gd desperate :/


PSPS!!! I think i managed to find out the problem: LOGIN window.
Because when i tried to change it's settings from the System Login Screen window it threw me out of the system(when I only opened the window).
And now it doesn't even open IT. How can i remove the login screen from the console? And then reinstall it. Because right now it shows me the Xfce login window.

---

### Post by kuratkull on 2006-06-03
ping.

just tell me how can i change the login screen without the "login window" in the system menu.

---

### Post by ubuntu_demon on 2006-06-03
Maybe this post helps :
[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

---

### Post by ubuntu_demon on 2006-06-03
[QUOTE=kuratkull]ping.

just tell me how can i change the login screen without the "login window" in the system menu.[/QUOTE]
I don't understand what you mean. I'm sorry.

---

### Post by kuratkull on 2006-06-03
[QUOTE=ubuntu_demon]I don't understand what you mean. I'm sorry.[/QUOTE]

Well, I have to change my login screen somehow, because i have a good reason to believe that my incapability to log in is caused by the faulty login screen.
But if i try to change my login screen from the "MEnu-System-Login Window" button, it crashed the first time, and the second time it didn't open it anymore.
So i need a way to change the login screen, or disable it completely without using the Login Screen button in the menu. But how?

---

### Post by ubuntu_demon on 2006-06-03
You could try to forcibly re-install some essential packages including the login manager. See my next post.

---

### Post by kuratkull on 2006-06-03
Well, it didn't work. Well, seems like my system is pretty screwed up. I give up. I'll wait until my CD's get here and then do a clean install.

Thanks for all your help anyway! :)

---

### Post by tseliot on 2006-06-03
Does this command help?
```
sudo dpkg-reconfigure gdm
```

If not, it might be that there is something wrong with your account.
Try to make a new one:

Boot in recovery mode
type:
```
adduser your_new_username
passwd your_new_username
```

NOTE: replace "your_new_username" with the new username you want to use

visudo

look for these lines:
```
# User privilege specification
root    ALL=(ALL) ALL
```

and add a line with your username in the following way:
```
# User privilege specification
root    ALL=(ALL) ALL
your_new_username    ALL=(ALL) ALL
```

Save and exit

then reboot as usual and try to login with your new username (you will then need to move your files from /home/your_old_username to /home/your_new_username

---

### Post by kuratkull on 2006-06-03
Didn't help :S

It's very weird, because when i use repair console to "startx" it loads beautifully and works almost perfectly(although the kicker panel is a bit buggy). And it doesn't show the dreaded login screen.

Hmm, would it help if i would uninstall the whole xfce package, that would remove the xfce login window too...unless the fault is systemwide.

---

### Post by ubuntu_demon on 2006-06-04
Please post your /etc/apt/sources.list

I've updated my guide on broken dependencies with a couple of things :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

I've also included this link :
[http://www.ubuntuforums.org/showpost.php?p=1090468&postcount=12](http://www.ubuntuforums.org/showpost.php?p=1090468&postcount=12)
and this :
> 
An example :
if your problem of broken dependencies is somehow related to getting into X. Something like this may help :
$sudo apt-get remove xserver-xorg x-window-system-core gdm -f --purge


---

### Post by kuratkull on 2006-06-04
I'm using the sources list you gave in another topic.
But i managed to login, after I removed some/most important Xfce packages(or Xubuntu packages). It then restored the login screen to the default UBuntu screen. But after i reinstalled Xubuntu or Xfce it became useless again.

EDIT: I used the "apt-get remove xserver-xorg x-window-system-core gdm -f --purge"
command, and the login screen changed to kubuntus. But after trying to log in the screen turns black for a sec and then throws me back to the same login screen.

And for errors, i'm not getting any.
The problem MUST be Xfce, because I CAN get in from the repair console, cause it doesn't show the login screen, it directly goes to the desktop after the startx command.

:S

---

### Post by rcarring on 2006-06-04
Can your system run Gnome? You state that after installing xubuntu and xfce again it became useless. 

If you can get into Gnome, then do a complete removal of xbuntu-desktop and xfce, reboot and if you can still get to the Gnome desktop, then do 

sudo apt-get update
sudo apt-get install xbuntu-desktop

(My understanding is that xfce is the window manager for xbuntu so should get installed by default)

---

### Post by kuratkull on 2006-06-04
[QUOTE=rcarring]Can your system run Gnome? You state that after installing xubuntu and xfce again it became useless. 
........[/QUOTE]

I'll do the following now:

1. I'm in Xubuntu right now(startx from the repair console brings me here)
2. I'll find the Xubuntu packages and remove them , the system will problably behave weird.
3. I'll do a reboot and it SHOULD bring me to the default ubuntu login window.
4. I'll problably get in and i'll remove the rest of the xubuntu packages
5. I'll reinstall the xubuntu-desktop.
6. I'll report here.

I just want to thank you for being so helpful, i'm trying to do my best to follow your directions :) And make my problem as clear as i can for you.
Thanks.

---

### Post by ubuntu_demon on 2006-06-04
To clarify for everyone you should use this sources.list for upgrading :
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

Did you initially forget to comment non-official repositories ?

Please make sure **to read and understand** the full post :
HOWTO fix problems regarding broken dependencies
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

After reading you should try following the guide and post the errors here.

If it becomes too frustrating after a while you could always install Dapper from cd (always make a backup of your personal files before upgrading and installing).

I'm off for a while. Good luck!

---

