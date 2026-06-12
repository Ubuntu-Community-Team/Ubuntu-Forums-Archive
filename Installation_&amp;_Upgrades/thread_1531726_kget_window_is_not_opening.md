---
title: "kget window is not opening"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by harpinder on 2010-07-15
[B]i have downloaded the kget and installed it successfully,it was working but from tomorrow i am not able to open it.i have reinstalled but all in vain.
please help me in opening the kget
thanks[/B]

---

### Post by ankspo71 on 2010-07-18
Hi,
I haven't used Kget very much, but I know that it doesn't like to show the main window very much.:(

Try pasting these  commands into the terminal (or Konsole):
```
killall kget
kget --showDropTarget
```This will stop kget from running in the background and tell it to run again with the drop-traget icon shown on the desktop. You can use this icon to control Kget.

You can also change your kget start menu entry to:
kget --showDropTarget

When you get Kget's main window open, go to Kget's options in the menu and tell it to "show drop target", so that it always shows.

If you don't want to use the drop target icon, you can open and close Kget from the Konqueror browser.
Hope this helps.

---

### Post by harpinder on 2010-07-19
thanks buddy i will try

---

### Post by harpinder on 2010-07-20
i am getting this.

harpinder@ubuntu:~$ kget --startwithoutanimation
QApplication::qAppName: Please instantiate the QApplication object first
kget: Unknown option 'startwithoutanimation'.
kget: Use --help to get a list of available command line options.

---

### Post by ankspo71 on 2010-07-20
Hi,
These commands are case sensitive in Linux, so we need to use upper and lower case letters. You are right though, Kget is not responding well to the --startWithoutAnimation command option. It's not starting in the foreground with that option in the command.

Go and open Kget again, either by using the command "kget" or "kget --showDropTarget". When it opens, go into the main window of kget, then go to the menu called "settings" then choose "configure kget". The options dialog will pop up: Try enabling "Show drop target", and disabling "Enable Animations". Now quit kget and try the startmenu shortcut again. It should work now (hopefully). 
Hope this helps.

---

### Post by harpinder on 2010-07-21
[SIZE=3]harpinder@ubuntu:~$ kget --showDropTarget
QApplication::qAppName: Please instantiate the QApplication object first
kget is already running!

but it don't start kget drop target.whats going wrong with me.[/SIZE]

---

### Post by ankspo71 on 2010-07-21
> **harpinder said:**
> [SIZE=3]harpinder@ubuntu:~$ kget --showDropTarget
QApplication::qAppName: Please instantiate the QApplication object first
kget is already running!

but it don't start kget drop target.whats going wrong with me.[/SIZE]

Sorry, I should have said to use the 'killall kget' command to close kget first before opening it again.

I'm also using Kubuntu 10.10 (development release) so there might be differences in the way Kget operates for me. I personally feel kget is just being a pain (it needs work), the reason why I haven't used it much. I also have high speed Internet though, so it's rare for me to need a download manager... but sometimes I do need one because I might download something that is large and has a very slow download rate.

An alternative to kget is gwget and that seems to work better for me. It might have a few differences, but at least it opens the gui and gives me an icon in the notification area (kget did not). 

Hope this helps.

---

### Post by harpinder on 2010-07-22
[SIZE=2]sorry brother i was on the wrong way as i am not a computer savvy.i am a normal user.
i am using ubuntu thats way i was facing the problem but now i have installed kde package 4.4 in ubuntu for dual session and its working.kget is also working now in both sessions.
now may next question is can we remove the gnome session as i want to only kde?
the speed is little bit slow in kde than gnome but interface is good.my hardware specs are amd dual core 1.8ghz,1gb ddr2 ram,160 gb hard disk,nividia gforce 7000m.i think these hardwares are enough to run the kde smoothly but i am getting a slow speed.
i am using this in dual boot with windows 7.
thanks
[/SIZE]

---

### Post by ankspo71 on 2010-07-22
Hi,
Before I tell you to go ahead and remove anything Gnome related, have a look at this link I wrote about making KDE perform a bit better. [http://sticky-bones.blogspot.com/2010/07/how-to-tweak-kde4-for-perfmormance.html](http://sticky-bones.blogspot.com/2010/07/how-to-tweak-kde4-for-perfmormance.html) 

I'm not sure if I can tell you how to remove the gnome session alone without making it too complicated or ruining it for you. That probably involves editing xsession or removing gnome-session and gnome-panel or something. I wouldn't recommend doing this unless someone here could give you the right instructions though.

However, I know people can easily remove Gnome entirely with the following advice... If you don't mind losing any of the default applications that came with Ubuntu, then you can use the following link... This is a link that gives a single command for people paste into the terminal that will remove Ubuntu and install Kubuntu so that it is pure KDE desktop.
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

If there are any applications that came with Ubuntu that you wanted to keep you can easily reinstall each application afterwards. The above command shouldn't remove any applications that you installed personally, because it will only try to remove the default ones.

---

### Post by harpinder on 2010-07-22
i need firefox.will it be removed.if yes,how to get back firefox in kubuntu.

---

### Post by ankspo71 on 2010-07-22
Hi again,
The command says it will remove firefox but the command to install firefox again afterwards would be:
sudo apt-get install firefox

There is going to be a package manager in Kubuntu (kpackagekit), but you will probably also want to keep Synaptic Package Manger too, to make installing other packages a little easier.
sudo apt-get install synaptic

You can use those commands after using the big command from the reply above (the one from [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde))

---

