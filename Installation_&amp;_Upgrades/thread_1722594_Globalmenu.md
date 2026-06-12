---
title: "Globalmenu"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by TimmyK. on 2011-04-05
Hi, I am having trouble downloading globalmenu. Does anyone have a direct download link or terminal command for installing it on Ubuntu 10.10, if that version exists?

---

### Post by uRock on 2011-04-05
```
sudo apt-get install unity
```

---

### Post by TimmyK. on 2011-04-06
OK, I downloaded it, now how do I get to it?

---

### Post by calchal on 2011-04-06
Maybe this link could help? 
[http://ubuntu-tweak.com/source/globalmenu-team-ppa/](http://ubuntu-tweak.com/source/globalmenu-team-ppa/)

This is the command I used to install Global menu in Lucid lync:
sudo add-apt-repository [B]ppa:globalmenu-team/ppa

[/B]But, hey, why dont you download Ubuntu natty beta, it comes with global-menu-style in default, and I think it is more stable than 10.10 (in my case using netbook)

---

### Post by TimmyK. on 2011-04-06
Yeah, maybe I'll upgrade to Natty someday if my computer ever crashes. I'm not going to do it now, though, as I do not want to loose all my documents and installed programs.

Nope, couldn't find anything there that helped me. So exactly how do I change my Menu Bar to a finder? Can someone please explain the whole procedure?

---

### Post by calchal on 2011-04-06
> **TimmyK. said:**
> Yeah, maybe I'll upgrade to Natty someday if my computer ever crashes. I'm not going to do it now, though, as I do not want to loose all my documents and installed programs.

Nope, couldn't find anything there that helped me. So exactly how do I change my Menu Bar to a finder? Can someone please explain the whole procedure?

Yeah you're right, sorry for the stupid suggestion (-.-), anyway after you installed it, you must right click the panel--> add to panel --> select global menu, and restart your session

---

### Post by uRock on 2011-04-06
If you installed Unity, then log out and at the bootm of the screen there is a drop down(up) that you can select classic gnome or Unity.

---

### Post by TimmyK. on 2011-04-06
I logged out and logged back in, and now my computer has changed all my preferences! I don't even know how to change them back! Docky is gone, there's this weird menu bar on the side, I can't get to applications, and there's no main menu! What do I do?

And no unity when I logged out or in 'add to panel'.

---

### Post by uRock on 2011-04-06
Log out and select classic gnome, then uninstall Unity.

---

### Post by TimmyK. on 2011-04-06
Classic gnome from where? The only controls there are the date/time, Universal Access Preferences, and Shut Down/Suspend/Hibernate. And this bar on the side, is that what unity is supposed to do? 

I'm sorry if I didn't make myself clear. When I meant I wanted a finder, I meant a Mac-like finder bar that would appear in the top panel. I want something that gives the menu for each application in the finder bar.

Are globalmenu and unity the same thing? I don't understand. Which one gives me the Mac-like finder bar? I am pretty sure this is globalmenu. But is it the same as unity?

I've given up on Unity, even if it is the thing to get the finder bar. Can someone just tell me how to get rid of it?

---

### Post by TimmyK. on 2011-04-06
To get rid of Unity, do I delete File System/usr/share/Unity, and then restart? Will this restore it to default GNOME settings?

---

### Post by uRock on 2011-04-06
You must properly uninstall it via CLI, Synaptic or the Ubuntu Software Center.

---

### Post by TimmyK. on 2011-04-06
OK, I uninstalled unity. But how do I restore classic GNOME settings? And is there a keyboard shortcut for logging out? There is no button for it anywhere on my desktop. The only things I can access are those things I put on my Dock.

---

### Post by TimmyK. on 2011-04-06
Or perhaps there is a command in the terminal to restore GNOME classic?

---

### Post by Frogs Hair on 2011-04-06
I used this ppa to install the Global Menu in 10.10 . There is no need to install the Unity desktop. after you have added the menu to the Gnome Panel from the add to panel menu restart the computer. 

[http://www.webupd8.org/2010/11/install-gnome2-globalmenu-in-ubuntu.html](http://www.webupd8.org/2010/11/install-gnome2-globalmenu-in-ubuntu.html)

---

### Post by uRock on 2011-04-06
Select Classic Desktop at the login screen. You will have to click on the login name first.

---

### Post by TimmyK. on 2011-04-06
That's what I thought would be the best idea too, but I can't get to the login screen. There are no panels, no menus, nothing. I couldn't access anything if it weren't for the dock. Is there either keyboard shortcut or a command in the terminal to log out? Or to set classic GNOME back again?

---

### Post by TimmyK. on 2011-04-06
I could especially use a command in the terminal.

---

### Post by TimmyK. on 2011-04-06
Alright, I used the Ctrl + Alt + L to lock screen, and then hit switch user to get to the login screen. I then set the theme thing to Ubuntu Desktop edition. However, when I logged in, nothing was different. I then restarted my computer, and still, nothing changed.

So is there a command in the terminal to set it to GNOME classic? Please help. I am getting quite desperate. Should I just save all my documents and reinstall my operating system?

---

### Post by Simian Man on 2011-04-06
> **TimmyK. said:**
> I logged out and logged back in, and now my computer has changed all my preferences! I don't even know how to change them back! Docky is gone, there's this weird menu bar on the side, I can't get to applications, and there's no main menu! What do I do?

Something tells me this will happen to a lot of people later this month :).

---

### Post by TimmyK. on 2011-04-06
I have one clue as to the problem.  If I open the 'Visual Effects' tab on 'Appearance Preferences', it is on 'No effects' and if I try to change it, it says 'Mutter is running, can't change between effects'. What is mutter?

So for the last time, does anyone have a terminal command for restoring GNOME classic, or should I just reinstall my OS?

---

### Post by uRock on 2011-04-06
Have you tried turning it off and back on again?

---

### Post by TimmyK. on 2011-04-06
Woo-hoo! When I restarted it and logged out and changed some stuff, it worked! Thank you! You *do* rock!

---

### Post by TimmyK. on 2011-04-06
OK, now back to the original topic, in the terminal I typed in
```
sudo add-apt-repository ppa:globalmenu-team/ppa
```
It made me type my password and did its stuff. However, when I right-clicked the panel, I saw nothing about globalmenu. Is it maybe that I'm using Maverick and not Lucid as calchal said?

---

### Post by Frogs Hair on 2011-04-06
> **TimmyK. said:**
> OK, now back to the original topic, in the terminal I typed in
```
sudo add-apt-repository ppa:globalmenu-team/ppa
```
It made me type my password and did its stuff. However, when I right-clicked the panel, I saw nothing about globalmenu. Is it maybe that I'm using Maverick and not Lucid as calchal said?

Try the instructions at the link in post 15 .

---

### Post by TimmyK. on 2011-04-06
Thank you! You have made my day. One last question: isn't it supposed to have the icon of the open window in the corner?

---

### Post by Frogs Hair on 2011-04-07
> **TimmyK. said:**
> Thank you! You have made my day. One last question: isn't it supposed to have the icon of the open window in the corner?

It does not display the panel on the left side in 10.10 . I'm not sure if that is part of the global menu in Unity  or a separate function. I will find out in a few weeks.

I Installed the global menu to see how much I would use it and to see if it would get in the way . I found it much easier to use when I enabled tiny mode because I have 1280 x 1024 resolution.

---

### Post by bowens44 on 2011-04-07
> **TimmyK. said:**
> I logged out and logged back in, and now my computer has changed all my preferences! I don't even know how to change them back! Docky is gone, there's this weird menu bar on the side, I can't get to applications, and there's no main menu! What do I do?

And no unity when I logged out or in 'add to panel'.

That IS unity , the great 'improvement' from Ubuntu.Making it difficult to access appellations seems to have a primary goal of the developers.

---

### Post by TimmyK. on 2011-04-07
OK, now it makes sense. I thought that unity and globalmenu preformed very similar tasks, just adding the finder applet to the panel. Now I understand. Thank you for your help guys. I am still learning about globalmenu, so feel free to add any more comments.

---

