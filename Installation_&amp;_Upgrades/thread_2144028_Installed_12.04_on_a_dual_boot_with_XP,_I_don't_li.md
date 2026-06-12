---
title: "Installed 12.04 on a dual boot with XP, I don't like it and want to go with 10.04"
date: 2013-05-10
forum: Installation &amp; Upgrades
---

### Post by jukingeo on 2013-05-10
Hello all,

I am putting a new system together and I made the mistake of installing a 'newer' version of Ubuntu without first checking it out.   I am currently used to using version 10,04 which I have on my computer, but for my wife's new computer I installed 12.04 as this was the latest LTS version.   However, the thing I didn't contemplate on is that everything is totally changed.

1) taskbar is on top (can't move it to the bottom, or at least I don't know how to move it now)
2) start button is on the right, not left (can't seem to move that either)
3) max, min, close buttons are on the left side (whereas older versions of Ubuntu and Windows have it in the 'normal' right position....and yes, it seems you can't move that either).
4) minimized windows are on the left (???)
5) I can't find the terminal as I want to edit grub so Windows is the defaut.

Needless to say, since this is going on my wife's computer and _I_ am having trouble finding my way around, she will _NEVER_ get it.

Granted 12.04 is pretty and does have a nice 'wow' factor.   But being intuitive it isn't...I have to teach my wife this and as such 12.04 has to go.

What I would like to do is set up my old version of Ubuntu, 10.04 on a dual boot WITH WINDOWS AS DEFAULT ON BOOTUP on my wife's machine.   How do I do this without obliterating her Windows partition?

Thank You,
Geo

---

### Post by ibjsb4 on 2013-05-10
You can install Gnome Classic which looks like 10.04 to your current 12.04 install and choose at login by clicking on the login icon.

```
sudo apt-get install gnome-session-fallback
```

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by jukingeo on 2013-05-11
> **ibjsb4 said:**
> You can install Gnome Classic which looks like 10.04 to your current 12.04 install and choose at login by clicking on the login icon.

```
sudo apt-get install gnome-session-fallback
```

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

Hello,

Ok, I did get my old directory structure back and my open windows show up at the bottom, however, the main taskbar is still on top and the min,max,restore icons still appear on the left.  Any way to change those back?

I had another thought...would it be possible to change the entire desktop gui to something like KDE or XFE to get the 'old' desktop back, but yet still keep with the current LTS version?

Thank you for your help....in the very least, I found my terminal so I can properly change my grub settings.   The machine now boots to Windows first.

Geo

---

### Post by ibjsb4 on 2013-05-11
How to change your min/max to the right is covered in the classic tweaks link.

Another thing, to change panel options now takes Alt + right click on a blank spot.

Want the XFCE desktop?  You could try either the desktop install or the full install to your current install.

Desktop
```
sudo apt-get install xfce4
```

or full install

```
sudo apt-get install xubuntu-desktop
```

---

### Post by marianoa on 2013-05-11
Hi junkingeo,

I'd suggest you to try and get used to the new interface, is not that bad after using it for a few hours and I personally find it better than the old one. To answer your questions

- Moving the window buttons
Open dconf-editor, search for "metacity" and among the settings related to metacity you can find a variable called "button-layout", it should have the value "close,minimize,maximize:" and you should change it into ":close,minimize,maximize" that is move the colon at the beginning of the string, changing the order of the elements listed in the string changes the order of the corresponding buttons in the window titlebar

- Installing xfce or kde interfaces
In order to get xfce or kde guis you should install the packages xubuntu-desktop and kubuntu-desktop respectively, after installing either of them you should be able to select the gui you want to use at the login window. These packages have many dependencies, if you've installed you system recentely maybe it's better to reinstall it using a different ubuntu flavor (xubuntu or kubuntu) but I imagine it's useful to try them first

Hope it helps!

---

### Post by SuperFreak on 2013-05-11
XFCE is a good intuitive DE but you might also try [Cinnamon DE (HERE) ]("http://cinnamon.linuxmint.com/") which I have found to be very user friendly and more like the older style of Ubuntu and also XP
It has most of the features you are after and is highly configurable (for example you can have the task bar at top, bottom or both and can adjust the width of it also window buttons are on right side by default)

---

### Post by ibjsb4 on 2013-05-11
> Open dconf-editor, search for "metacity" and among the settings related  to metacity you can find a variable called "button-layout"

That is another point.  Metacity button layout can still be found in gconf editor.

[ATTACH=CONFIG]242465[/ATTACH]

However the Unity desktop depends on compiz which can also be used as a DM for the classic desktop.  I use metacity, but if your comfortable with compiz, you have the option :)

---

### Post by jukingeo on 2013-05-12
Hello All,

> **ibjsb4 said:**
> 
However the Unity desktop depends on compiz which can also be used as a DM for the classic desktop.  I use metacity, but if your comfortable with compiz, you have the option :)

Usually I never bothered with compiz, caused problems on a past machine in fact.   I never heard of metacity. 

> **SuperFreak said:**
> XFCE is a good intuitive DE but you might also try [Cinnamon DE (HERE) ]("http://cinnamon.linuxmint.com/") which I have found to be very user friendly and more like the older style of Ubuntu and also XP
It has most of the features you are after and is highly configurable (for example you can have the task bar at top, bottom or both and can adjust the width of it also window buttons are on right side by default)

THAT looks good. Heck, I even like the way that looks over my 10.04 version.  So how do you add this?  Does this load up into your login menu and you can choose it from there?

> **marianoa said:**
> Hi junkingeo,

I'd suggest you to try and get used to the new interface, is not that bad after using it for a few hours and I personally find it better than the old one. To answer your questions

I had a good laugh with my wife today as I will explain as I go.   I showed her a few things with 12.04 using the 'fallback' DE as recommended by ibjsb4 below.  Since now I could find my way around even though 12.04 is still not to my liking, I explained a few things to my wife.   With the standard 12.04 installation (differing from mine in that I have Ubuntu Studio and the included apps are different), she has a full office suite and email already loaded up.  Since she spends most of her time on the internet, I explained that there is less of a chance of corrupting her Windows OS if she doesn't use that OS for doing on-line work and that she strictly use Ubuntu for all on-line work.   Her favorite application is Google Chrome and I set that up for her.

After a few hours of using Ubuntu, she comes back to me and says that perhaps she wants to have the machine boot into Ubuntu as a default now!  LOL!   She did mention that perhaps since she is new to Ubuntu, the changes in 12.04 are not apparent to her as they are to me.  So in the end it might seem that Ubuntu is here to stay for my wife as well.  She just came in the room and I showed her the Cinnamon desktop and she likes.  So hopefully I can put that on my system (and hers) without messing things up.

> 
- Moving the window buttons
Open dconf-editor, search for "metacity" and among the settings related to metacity you can find a variable called "button-layout", it should have the value "close,minimize,maximize:" and you should change it into ":close,minimize,maximize" that is move the colon at the beginning of the string, changing the order of the elements listed in the string changes the order of the corresponding buttons in the window titlebar

It was not only the order, but also the location.  I preferred it to be on the right side as it is in Windows.

> 
- Installing xfce or kde interfaces
In order to get xfce or kde guis you should install the packages xubuntu-desktop and kubuntu-desktop respectively, after installing either of them you should be able to select the gui you want to use at the login window. These packages have many dependencies, if you've installed you system recentely maybe it's better to reinstall it using a different ubuntu flavor (xubuntu or kubuntu) but I imagine it's useful to try them first
Hope it helps!

Actually, seeing that Cinnamon desktop I would like to go that route.  Now I am using Ubuntu _Studio_ 10.04 so I hope I can use Cinnamon with that too.

Thank You all,

Geo

---

### Post by SuperFreak on 2013-05-12
Not sure if this will work with 10.04 but to install Cinnamon on 12.04 or later follow these steps. Yes you will be able to select you DE from the login screen and you could install XFCE also and make that available. Good Luck!


1. Open a terminal window.

2. Type in the following commands then hit Enter after each.

sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon


EDIT: Don't recommend installing on 10.04 see [here]("http://ubuntuforums.org/showthread.php?t=1983183")

---

### Post by SuperFreak on 2013-05-12
By the way I would suggest that you install the latest LTS (12.04.2) because 10.04 is no longer supported (you won't receive updates or security patches) unless you are on the server edition

---

### Post by marianoa on 2013-05-13
> **jukingeo said:**
> 
It was not only the order, but also the location.  I preferred it to be on the right side as it is in Windows.


Moving the colon is what puts the buttons on the right. They've been moved to the left because when the window is maximized the titlebar merges with the panel and in that case having the buttons on the left is the only option (on the right you have the notification area)

---

### Post by ibjsb4 on 2013-05-13
>   I never heard of metacity. 

If your not using compiz you default to metacity.

---

### Post by iponeverything on 2013-05-13
I was in the same boat as you, using 10.04 but installing 12.04 on my wife's laptop.

While I doubt I'll ever grow to like the "change for sake of change" tweaks and the unity blah blah blah.. 

My wife just had one or two minor complaints when I first gave it to her and she has loved it ever since.. I think it is something like the "mac effect" - that is the more you understand computers the less sense it makes.

---

### Post by jukingeo on 2013-05-14
Hello All!

Ok, major update on my end. I went to the Cinnamon site and I saw that they didn't support Ubuntu version 10.04.   Given that a week or so ago 10.04 expired AND I wasn't too happy with the way Jack (a feature of Ubuntu Studio) worked in that version, I figured perhaps now would be a good time to look into upgrading my system.  Another given was that I probably could assist my wife more with Ubuntu if we both were on the same version.

So last night I took the dive and downloaded the iso for Ubuntu Studio 12.04 and installed it.  The installation (while it is working) didn't turn out right due to the older partitioning system I was using, so I am going to have to redo it. (Just for the curious, the install put both the root AND home folders together on a very small 13 gig partition).

With that being said, I am open to some experimentation and decided to try Cinnamon out to make sure it works and is to my liking.   I followed the instructions from this site:

[http://www.howtogeek.com/103691/install-linux-mints-new-cinnamon-desktop-on-ubuntu/](http://www.howtogeek.com/103691/install-linux-mints-new-cinnamon-desktop-on-ubuntu/)

And the results are.....

> **SuperFreak said:**
> Not sure if this will work with 10.04 but to install Cinnamon on 12.04 or later follow these steps. Yes you will be able to select you DE from the login screen and you could install XFCE also and make that available. Good Luck!


1. Open a terminal window.

2. Type in the following commands then hit Enter after each.

sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon



(Yep, did that and) ....it didn't work.   Everything seemed fine until the last line.  When I input sudo apt-get install cinnamon, this was the output of my terminal:

geo@Geo1:~$ sudo apt-get install cinnamon cinnamon-session cinnamon-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'cinnamon' instead of 'cinnamon-session'
Note, selecting 'cinnamon' instead of 'cinnamon-settings'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cinnamon : Depends: gir1.2-muffin-3.0 but it is not going to be installed
            Depends: libcogl5 (>= 1.7.4) but it is not installable
            Depends: libmuffin0 (>= 1.0.0-0ubuntu1~precise) but it is not going to be installed
            Recommends: gnome-themes-standard but it is not going to be installed
            Recommends: gnome-session-fallback but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
geo@Geo1:~$ ^C
geo@Geo1:~$ ^C
geo@Geo1:~$ 

What do y'all make of that?  Apparently I am missing something.

As a reminder, I installed UBUNTU _STUDIO_ 12.04 on my system, not regular Ubuntu 12.04.   I had noticed that Ubuntu Studio is using an Xfe desktop and I am wondering if that might have something to do with that.    I am wondering if I should try it out on my wife's machine since her's is regular Ubuntu.

BTW, is the new Ubuntu Studio, really Xubuntu?

Thanx,

Geo

---

### Post by SuperFreak on 2013-05-14
> geo@Geo1:~$ sudo apt-get install cinnamon cinnamon-session cinnamon-settings
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'cinnamon' instead of 'cinnamon-session'
Note, selecting 'cinnamon' instead of 'cinnamon-settings'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
cinnamon : Depends: gir1.2-muffin-3.0 but it is not going to be installed
Depends: libcogl5 (>= 1.7.4) but it is not installable
Depends: libmuffin0 (>= 1.0.0-0ubuntu1~precise) but it is not going to be installed
Recommends: gnome-themes-standard but it is not going to be installed
Recommends: gnome-session-fallback but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
geo@Geo1:~$ ^C
geo@Geo1:~$ ^C
geo@Geo1:~$

What do y'all make of that?


Did you enter "sudo apt-get install cinnamon" ? looks like you entered " sudo apt-get install cinnamon cinnamon-session cinnamon-settings" instead

---

### Post by jukingeo on 2013-05-15
> **SuperFreak said:**
> Did you enter "sudo apt-get install cinnamon" ? looks like you entered " sudo apt-get install cinnamon cinnamon-session cinnamon-settings" instead

Whoops!  Sorry about that, it looks like the information you presented IS different than what I got from that site.   Apparently the information on that site is old and outdated as I went through the terminal again using what you posted here and that worked fine!  As a nice side effect I also now have Gnome on my system as well.

Now that I am in, I have a couple of questions in regards to Cinnamon

1) How do you make a desktop icon, it doesn't seem that dragging and dropping seems to work.
2) On my wife's computer, her min, max, close buttons moved to the right, which is what I hoped for.   On my machine they also stayed on the right, however, the buttons are still in the "Xfce style".   So is the style in Cinnamon JUST for the desktop?
3) My wife and I really got a kick out of how you set up the time/date format on the bottom right of the taskbar.  It is completely customizable!

Thank You,

Geo

---

### Post by SuperFreak on 2013-05-15
I am not at my Ubuntu PC right now but to get a program as an icon on your desktop open the menu and right click on any program I think that gives the option to make a desktop icon or put a launcher in the panel. If you right click on the panel you will find options to customize that (ie put at top or bottom or both, add applets etc).
I think to change XFCE buttons you may have to change the theme you use. You can find System settings in menu under System Tools .There you will find settings for Windows,Themes and many more features

---

### Post by jukingeo on 2013-05-15
> **SuperFreak said:**
> I am not at my Ubuntu PC right now but to get a program as an icon on your desktop open the menu and right click on any program I think that gives the option to make a desktop icon or put a launcher in the panel.

Yes, that is how I managed to do it on my computer, but that same trick doesn't work on my wife's machine.

> If you right click on the panel you will find options to customize that (ie put at top or bottom or both, add applets etc).

While not an ideal solution, we are using the panel as a work around until we can figure out how to get the drag 'n' drop to work.   I did some digging and found out that the issue is a conflict between the file managers.   So I would be still looking for a solution to this issue.

> 
I think to change XFCE buttons you may have to change the theme you use. You can find System settings in menu under System Tools .There you will find settings for Windows,Themes and many more features

Yes, I did try that and downloaded a couple of themes...however that didn't change the windows or buttons, they are still in Xfce.  Another thing I noticed is that when I set a theme, the background image shown in the theme doesn't go on the desktop.   However, the menus and fonts DO change, albeit only on the desktop, not the windows.

I hope these issues can be ironed out as I do like the Cinnamon desktop.

Thank You,

Geo

---

### Post by SuperFreak on 2013-05-15
Try going to Themes and then click on Tab "Other Settings" I have mine set up as per screenshot[ATTACH=CONFIG]242634[/ATTACH]

Your wife does have cinnamon installed right?I have used several versions of Cinnamon and right clicking on menu subcategories always brings up the option to either add to panel, add to desktop or add to favorites. Menu is in top left corner of screen(on mine)

---

### Post by jukingeo on 2013-05-16
> **SuperFreak said:**
> Try going to Themes and then click on Tab "Other Settings" I have mine set up as per screenshot[ATTACH=CONFIG]242634[/ATTACH]

Your wife does have cinnamon installed right?I have used several versions of Cinnamon and right clicking on menu subcategories always brings up the option to either add to panel, add to desktop or add to favorites. Menu is in top left corner of screen(on mine)

Yes, I did put Cinnamon on her machine.  Her options are there where the little "up arrow" is on the panel.   I set both of our machines up the same way have set yours and I still can't drag to the desktop.

Now both of our machines, that 'up arrow' is also where the themes are.  I loaded a couple of themes on both mine and my wife's machine.  Now when I go to to "Appearance" in the main menu the theme doesn't show up there.   In addtion the picture for the theme doesn't come up on the background.  So something is definitely wrong there.

Thanx,
Geo

---

### Post by SuperFreak on 2013-05-16
Sorry if I am not understanding. This screenshot shows how my menu looks when I right click on a program or launcher that I want to add to either desktop or panel

I think the arrow button on the panel you refer to opens Cinnamon settings but has nothing to do with adding icons to desktop. You can add some applets via that setting menu though

---

### Post by SuperFreak on 2013-05-17
If you want to install the complimentary File Manager (instead of Nautilus) to cinnamon:
```


        sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
        sudo apt-get update
        sudo apt-get install nemo


```

First command is probably redundant

---

### Post by jukingeo on 2013-05-17
> **SuperFreak said:**
> Sorry if I am not understanding. This screenshot shows how my menu looks when I right click on a program or launcher that I want to add to either desktop or panel


Oh, I knew what you were referring to, and that DID work on my machine, however, it isn't working on my wife's machine.   Dragging and dropping the launch icon (which *should *be working) doesn't work on either machine.

> 
I think the arrow button on the panel you refer to opens Cinnamon settings but has nothing to do with adding icons to desktop. You can add some applets via that setting menu though

Sorry, that was a separate issue I should have been clearer on.  My wife and I wanted to add new themes and found we can load them using that up-arrow.  However, the background doesn't change to the theme's picture, nor can you select it in the Appearance selection on the main menu

Thanx,


Geo

---

### Post by SuperFreak on 2013-05-17
Not sure what the problem is with your wife's computer. It may be necessary to remove cinnamon and purge and then reinstall with the commands I gave before but I am not sure.

---

### Post by jukingeo on 2013-05-18
> **SuperFreak said:**
> Not sure what the problem is with your wife's computer. It may be necessary to remove cinnamon and purge and then reinstall with the commands I gave before but I am not sure.

Can that be done with the package manager or would that have to be done manually.

Would you know anything about the other issue with the themes not changing over properly and not showing up in the Appearance section?

Thanx,

Geo

---

### Post by SuperFreak on 2013-05-18
I am not sure if the problem is related to the first set of commands you used in err. I would not like to hazard a guess on how to undo those commands but you may find some instructions on the web site where you found them. Sorry I could not be of more help

---

### Post by jukingeo on 2013-05-18
> **SuperFreak said:**
> I am not sure if the problem is related to the first set of commands you used in err. I would not like to hazard a guess on how to undo those commands but you may find some instructions on the web site where you found them. Sorry I could not be of more help

Actually the first set of installation commands I used on my machine, and the technique you explained works on my machine.  On my wife's machine, I ONLY used the commands you posted.

At any rate, since my wife wanted her drag n drop ability right away.  I put her back on the Ubuntu-Classic desktop and she said she is fine with it it.  I think I might switch to that desktop as well as it seems there are some conflicts between Gnome and Cinnamon, mainly with not being able to change the themes properly.  Also another thing I can't explain is why I can't change the menu bars from the original Xfce style.  But it is funny how that works out form me in the Ubuntu-Classic desktop as the +, -, X buttons are on the right where I want them.

I think it just boils down to it that certain desktops just can't be mixed completely outside of the OS that it it designed for.   Cinnamon is by right for Minty Linux, Gnome is for standard Ubuntu, Xfce is for Xubuntu, KDE is for Kubuntu.   I remember a long while back, I wanted to try KDE out on my Ubuntu Studio rig (this was way back with version 8.04) and I really got some unusual results.   I tried out Kubuntu on a live disk and the problems went away.   The thing was that KDE is a resource hog and even though I didn't try it with the then real-time kernal for Ubuntu Studio, I think I probably would have ran into trouble.

Right now as it stands my 'theme' seems to be a mix of Cinnamon, Gnome, and Xfce. LOL!

Oh, well, we tried it out anyway.  Thank you for the help anyway.

Geo

---

### Post by SuperFreak on 2013-05-19
Glad you were able to get it sorted

---

