---
title: "No window-manager started after upgrading to 10.4"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by martinichka on 2010-05-01
Yesterday I upgraded my Ubuntu installation to 10.4. In my account everything works fine. But on my wifes account no window-manager does start (no borders and window buttons are around windows). As I believe *compiz* and *compiz-decorator* should be running. This is what I see when I entered my account.

When I (on my wifes account) start ```
compiz --replace
``` it all works. So I know a work-a-round would be to start compiz by hand. However I am wondering why it does not start by default.

I thought it might be a wrong configuration, but even when I renamed ~/.compiz directory and then logged in to the account compiz didn't start as well.

Does anyone have suggestions to check why no window manager is started?

---

### Post by jabudia on 2010-05-02
Hi, same happened to me. I quickly fixed it by changing Visual Effects from none to normal. Hope it 'll work through reboots.:)

---

### Post by drgcpatel on 2010-05-02
I upgraded to Ubuntu 10.04 yesterday and was not getting window manager working hence could not get the minimize / maximize / close bar and had to restart the computer as no command over windows or the bar at the bottom of the screen for hiding the windows or changing the desktop etc were not controlled. Then on referring the forums I found the help and it worked for that session. I went to click Applications>Accessories>Terminal and then typed gnome-wm and then pressed enter. But on restarting the computer I need to follow the same procedure again. So can anyone help me to fix this issue forever. I am new to Ubuntu.

---

### Post by dionysius on 2010-05-02
@ **martinichka**
I've had a similar problem with Karmic. I fixed it by adding Compiz to the Startup Applications. 
System > Preferences > Startup Applications
Add a new item, command should be /usr/bin/compiz (but check that before you add it) and then when you reboot Compiz should do its thing without your encouragement. 

@ **drgcpatel**
I don't know why gnome-wm doesn't start when you boot up, but the above should fic your problem as well: 
System > Preferences > Startup Applications
Add a new item, command should be /usr/bin/gnome-wm, and then when you reboot it should be solved. 

Let us know if you got it working :)

---

### Post by martinichka on 2010-05-03
Thank you for your suggestion dionysius. Indeed it works to start compiz by Startup Applications, so the work-a-round is clear. 

On the other side I am currious for the cause of this problem as well. Therefore I would like to find out:
* From where normally compiz is started?
* Why doesn't it start it in this special case?

---

### Post by jurrabi on 2010-05-03
One more with the same problem.

I tried adding compiz to the starup programs, but then I get the busy mouse icon all the time.

The system works fine but it's not nice.

I also would like to know the right way to fix this.

---

### Post by sarsbretta on 2010-05-03
I have the same problem too. Every time I restart I lose my compiz, window manager, awn settings and my workspace switcher settings.

I also found this thread that might apply to us:
[http://ubuntuforums.org/showthread.php?t=1466754&highlight=window+manager](http://ubuntuforums.org/showthread.php?t=1466754&highlight=window+manager)

---

### Post by 47tuc on 2010-05-09
A slightly more elegant workaround:
Select:  System -> Preferences -> Startup Applications
then under the "Options" Tab just click the "Remember Currently Running Applications" button.  No need to select the "Automatically remember running applications when logging out" option.
This did the trick for me although it is really just a workaround rather than a true fix.

---

### Post by martinichka on 2010-05-25
My problem solved by debugging the xsession, by setting in **/etc/X11/Xsession.d/99x11-common_start** to
```
exec  $STARTUP --debug
```Then in the file **~/.xsession-errors** I found that:
```

gnome-session[1870]: DEBUG(+): GsmManager: starting phase WINDOW_MANAGER

gnome-session[1870]: DEBUG(+): Starting app: /org/gnome/SessionManager/App2
gnome-session[1870]: DEBUG(+): GsmAutostartApp: starting 1093b8a60e2e935db3125718966394064900000015390023.desktop: command=/usr/bin/compiz.real --sm-client-id 1093b8a60e2e935db3125718966394064900000015390023 --ignore-desktop-hints --loose-binding move resize place decoration animation ccp startup-id=1093b8a60e2e935db3125718966394064900000015390023
gnome-session[1870]: WARNING: Could not launch application '1093b8a60e2e935db3125718966394064900000015390023.desktop': Unable to start application: Failed to execute child process "/usr/bin/compiz.real" (No such file or directory)
gnome-session[1870]: DEBUG(+): GsmManager: ending phase WINDOW_MANAGER

```So the error seems to be that a saved session tries to start compiz.real (which does not exists after the upgrade anymore), and failes.
By removing all files in **~/.config/gnome-session/saved-session/** the problem is solved :))))

For people with similar problems it might help to delete the saved session. If that does not help you can debug the xsession and search in the **.xsession-errors** file for compiz (or anything that has to do with your problem).

I got the debug info from: [http://ubuntuforums.org/showthread.php?t=1466754&highlight=window+manager](http://ubuntuforums.org/showthread.php?t=1466754&highlight=window+manager)

---

### Post by cake nom nom on 2010-06-12
I Find that it gets messed up after i do an update

---

### Post by martinichka on 2010-06-15
> **cake nom nom said:**
> I Find that it gets messed up after i do an update
Hi cake nom nom.

It is not clear to me:

[LIST]
[*]what get messed up for you?
[LIST]
[*]that active programs saved in sessions in 9.10 are not correct working in 10.4 like in my case?
[/LIST]
[*]after what update?
[LIST]
[*]did you mean an upgrade from 9.10 to 10.4?
[/LIST]
[*]or something else?
[*]what you want to tell with your message?
[/LIST]
Marten

---

### Post by jarregui on 2010-12-10
Hi all,

I suffered the same problem. I know I caused it when deleting some entries in the "Other" menu, using the System -> Preferences -> Main Menu.

I solved this issue editing ~/.local/share/applications/metacity.desktop and ~/.local/share/applications/compiz.desktop.  In those files, I changed Hidden=True to Hidden=False


Regards,

Javier

---

