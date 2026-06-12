---
title: "Panels disappear!! Can't right-click desktop!!"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by campb.andrew on 2010-12-11
I need help urgently.

My panels disappeared after i clicked the log out button and i had to shut down the computer by right-clicking the desktop and clicking shut-down. However when i rebooted, the panels were still gone, my icons on the desktop weren't there and i couldnt right-click on the desktop. i tried updating to 10.10 to solve the problem but that didnt work. running xfce4-panel via "alt-f2" didnt work either. So i'm stumped. Please help. :-(

---

### Post by miegiel on 2010-12-11
> **campb.andrew said:**
> I need help urgently.

My panels disappeared after i clicked the log out button and i had to shut down the computer by right-clicking the desktop and clicking shut-down. However when i rebooted, the panels were still gone, my icons on the desktop weren't there and i couldnt right-click on the desktop. i tried updating to 10.10 to solve the problem but that didnt work. running xfce4-panel via "alt-f2" didnt work either. So i'm stumped. Please help. :-(

On the up-side "alt-f2" works (right?). Run *xfce4-terminal* to start a terminal. At least that way you can see errors in the terminal.

I just ran *xfce4-panel* in the terminal and it gave me this error:
```
xfce4-panel-Message: Xfce4-panel already running
```

---

### Post by lmarmisa on 2010-12-12
Maybe this thread could help you:

[http://ubuntuforums.org/showthread.php?t=574881](http://ubuntuforums.org/showthread.php?t=574881)

If you need to open a text mode terminal, press Alt + Ctrl + F1.

According with the referred thread, I recommend to type these commands:

```

cd
cd .config
cd xfce4
mv panel panel.old

```

You can reboot your computer with this command

```

sudo reboot

```

Best regards,

Luis

---

### Post by Megaptera on 2010-12-12
This little app may help in the future:

PanelRestore, allows you to quickly and easily restore the default Gnome panels in Ubuntu and to backup and restore your existing custom panel configurations.

[http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/](http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/)

---

### Post by azertyh on 2010-12-12
hello,
[https://help.ubuntu.com/community/XubuntuPanels](https://help.ubuntu.com/community/XubuntuPanels)

---

### Post by campb.andrew on 2010-12-14
Thank you. Sorry i took so long to reply. I've had exams at school and havent really had a chance to come online. 

Your link had the solution i needed. Hopefully i wont have to resort to it again however. :-)

---

### Post by campb.andrew on 2010-12-14
[COLOR=Indigo]Thank you everyone for your help. I tired running this command from the terminal. 

```
xfce4 -panel
```It didn't work. I used the link from the above user and got this command:[/COLOR] [COLOR=Indigo]

[/COLOR]```
 [COLOR=Indigo]
rm -rf ~/ .cache /sessions[/COLOR]
```[COLOR=Indigo]It worked perfectly well. I even got two extra workspaces. :D[/COLOR] [COLOR=Indigo]

Sorry i took so long to reply. School has been killing me. It's nice that you all responded. However, it kinda bugs me that there are so many variants of this one problem if there are so many offered solutions. [/COLOR] [COLOR=Indigo]:-( Wish i knew more about programming. I'd love to work on the Ubuntu Project myself. 

Oh well, once again. Thank you everyone. Gonna mark this solved now. Hope it helps someone in the future.[/COLOR]

---

