---
title: "Want to go back to 10.10, 11 sucks!"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by SwingKid on 2011-05-20
I just did my update from 10.10 to 11 and the new version sucks. The bar is on the left and I can't do anything with the status bar up above. Everything is changed and I want my old desktop back. The possibility to get more desktops (like 4 different which you could choose to use) is also gone which also sucks. How can I fix this? :-x

---

### Post by MartyBuntu on 2011-05-20
Log out and log back in under "Ubuntu Classic".

Maybe you can live with that. Hope it helps.

---

### Post by Rasa1111 on 2011-05-20
lol,
why do people just upgrade their systems without trying the new one out first?

anyway, as marty said...
change to 'ubuntu classic' at the login screen after you click your name.
or reinstall 10.10.

---

### Post by MartyBuntu on 2011-05-20
> **Rasa1111 said:**
> lol,
why do people just upgrade their systems without trying the new one out first?



To be fair, Unity is not operational for most folks from the live CD.

---

### Post by oldfred on 2011-05-20
But many have large hard drives, today. And 10-20GB of hard drive space for new / (root) and an hour of time to install gives a full test. I just like having several / partitions so I can boot something when (not if) I break something.

---

### Post by coffeecat on 2011-05-20
> **SwingKid said:**
> The possibility to get more desktops (like 4 different which you could choose to use) is also gone which also sucks. How can I fix this? :-x

Click on the "Workspace Switcher" icon (it looks like a grid) in the launcher and you have a choice of 4 desktops. So it hasn't gone.

---

### Post by SwingKid on 2011-05-21
It worked with changing to Ubuntu Classic! I like it. I can not believe why Ubuntu would make such a horrible update. Unity sucks balls.
So anyway now I have some more problems here. The "special effects" are all gone. Before, when you right-clicked on the desktop itself and chose the menu "change desktop background" etc, you would always see the "special effects" menu. But now it is gone, there are only three menus left. Why is that? How can I get my special effects back? Furthermore, I seem to have lost the ability to have several desktops. Before when I clicked windowsbutton+A I could choose between all my opened programs, but now that keyboard shortcut is taken away and I don't really know how to fix it. Same thing with windowsbutton+E, which opened up an overview of all my desktops (4) and I could pick either one of them. This shortcut is also gone. How do I get these functions back running again?

---

### Post by Rasa1111 on 2011-05-21
Install CCSM, "compiz config settings manager".

---

### Post by SwingKid on 2011-05-21
> **Rasa1111 said:**
> Install CCSM, "compiz config settings manager".

Done! And now what? =)

---

### Post by Rasa1111 on 2011-05-21
> **SwingKid said:**
> Done! And now what? =)

Open it up and start playing with settings/plugins! lol

The "special effects/visual effects" are already enabled..
There's just not a tab for it anymore in the appearance settings.  

So all the same special effects and whatever you had before..
are all just some "clicks" away, in CCSM. 

I can't be specific, as I don't know exactly what you're going for..
but all the special effects and everything can be handled and tweaked, and turned on or off using CCSM.
Just gotta look around in it at all the different stuff. 

good luck!

---

### Post by SwingKid on 2011-05-21
> **Rasa1111 said:**
> 
Just gotta look around in it at all the different stuff. 

good luck!

**** Rasa..now I've done something really bad. I don't know why, but all of a sudden I can't take a grip onto the different windows with my pointer!?? I can't move them around. They are stuck. What did I do and how do I fix it? I think it might have been when I clicked something in this program (or I am sure of it) but I don't know what..:confused:

---

### Post by SwingKid on 2011-05-21
Please help me. I can barely do anything with my computer now!

---

### Post by Quackers on 2011-05-21
It may be that compiz has crashed.
If Alt + F2 opens a run window type in compiz --replace then hit enter and see if things return.

---

### Post by matt_symes on 2011-05-21
Hi

Try Quackers suggestion to restart Compiz.

 > I can't take a grip onto the different windows with my pointer!?? I can't move them around.

As an aside you can more windows around by pressing the ALT key and left mouse button at the same time and moving the window with your cursor .

Kind regards

---

### Post by SwingKid on 2011-05-21
Neither ALT+F2 or ALT+Left mouse key work..:(
after I installed this new Unity version, all my shortcuts except two (Ctrl+Alt+E = Nautilus, and Ctrl+Alt+T = Terminal) seem to have expired for some reason. Everything is gone and now I can't even use the pointer to grab onto windows. Really really weird. Big problem! :mad:

---

### Post by Quackers on 2011-05-21
Open a terminal and run ```
compiz --replace
``` and see if things return to normal.

---

### Post by SwingKid on 2011-05-21
> **Quackers said:**
>  see if things return to normal.


Nope..and now for some reason my shortcut to the Terminal is also gone, only one remaining obviously (to Nautilus). If I open up a new window (for instance Nautilus) it is still so that I can't move it around.

I got this response in the Terminal.

Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing composite options...done
Initializing opengl options...done
Initializing imgjpeg options...done
Initializing decor options...done
Initializing staticswitcher options...done
Initializing zoom options...done
Initializing animation options...done
Initializing vpswitch options...done
Initializing wobbly options...done
Initializing fade options...done
Initializing cube options...done
Initializing rotate options...done
Setting Update "fullscreen_visual_bell"
Setting Update "unfold_key"
Setting Update "rotate_flip_left_edge"

and then it just stopped...?

---

### Post by Quackers on 2011-05-21
Hmm, try quitting the terminal and rebooting. See if any error messages present themselves at startup.

---

### Post by Rasa1111 on 2011-05-21
Do you have Ubuntu Tweak installed?

If so,
There is a "desktop recovery" tool.
Ive had to use it 3 different times now for different mess ups like yours , and every time it's restored me back to working order. 

That's the only thing I can think of at the moment..
Sorry man.

 It looks like this~ 
[ATTACH]192777[/ATTACH]

On the first time, you will not have any "backups"..
But that is Ok.
It will just restore things back to default when you click "Recover"

Then once you have a working desktop again, and setup how you want,
Then go back to Tweak and add a "backup" , so you have it next time, just in case there is a next time. 

Hope this can help..
but if not.. Im sure it'll get figured out here, no worries.

Good luck man.

---

### Post by SwingKid on 2011-05-21
> **Quackers said:**
> Hmm, try quitting the terminal and rebooting. See if any error messages present themselves at startup.


Not really anything. Shutter (which I have it made to open at startup) goes through some check-up everytime for updates, I don't know why though, didn't do that before. My status bars (I have two, one bigger in the bottom and the smaller one in the top) have some graphical problems at startup. I have them on transparent but they get all black, but after I right-click on them choosing properties and press first Solid and then back to transparent again it works fine. Don't know why this is though ...:confused:

---

### Post by SwingKid on 2011-05-21
It is ok..but I could not find Ubuntu Tweak in Ubuntu Software Center? What is it called like? Should I be able to find it there? If it is already installed..where in what menu do I seek for it?

---

### Post by Quackers on 2011-05-21
Is your desktop now working in other respects?
Do windows have their borders? Do they have the maximise/minimise/close buttons? Can you move windows around now?

---

### Post by SwingKid on 2011-05-21
> **Quackers said:**
> Is your desktop now working in other respects?
Do windows have their borders? Do they have the maximise/minimise/close buttons? Can you move windows around now?

At first when I first fixed with this program "CompizConfig Settings Manager" and when I clicked in Ubuntu Unity preferences all my borders and buttons disappeared. I was able to restore them, but not the "moving windows around"- function.

---

### Post by Quackers on 2011-05-21
Ok, if you look in CCSM there is a setting for that called "move windows" I think.

---

### Post by SwingKid on 2011-05-21
> **Quackers said:**
> Ok, if you look in CCSM there is a setting for that called "move windows" I think.

I'm on it :S but I can't find the right one :( there is one section called Window Management but I fail to understand which one it is I want to go for.

---

### Post by Quackers on 2011-05-21
Window Management > Move Window

---

### Post by SwingKid on 2011-05-21
Ok..fixed!! Thank you so much!
Now when this is fixed:

all my keyboard shortcuts are gone. I can't even scroll between open programs (Shift+Alt before)...how do I get them back?

---

### Post by Rasa1111 on 2011-05-21
> **SwingKid said:**
> It is ok..but I could not find Ubuntu Tweak in Ubuntu Software Center? What is it called like? Should I be able to find it there? If it is already installed..where in what menu do I seek for it?

If you still want it, 

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Click the "download now" button, 
and once it downloads, it will either open in software center by itself (depending on your settings), or just double click the .deb file once it downloads, and it will open in software center, then just click install, like usual.

edit: glad you got it fixed!

Not sure about your shortcuts, sorry.

---

### Post by SwingKid on 2011-05-21
Yea tweak sounds like a great program. I am installing it now. Thanks :)

---

### Post by Rasa1111 on 2011-05-21
no problem.
 it is a great program. 
One of the first few I always install after a fresh ubuntu install. =-)

---

### Post by SwingKid on 2011-05-21
I give up. There are just too many things which are ****** UP with this newest update, Unity. When I log in to Ubuntu Classic, both my status bars in the bottom and in the top have some weird graphical problem and they are not at all transparent, but look like barred windows...my shortcuts don't work either except the one I use for opening Nautilus and I have lost the ability to use more than just one desktop. What is seriously wrong? Are there anyone else with similar problems in the 11.04 edition? Please let me know, and please do help me with downgrading to 10.10 again. How am I able to do that? I miss it so much! But will I miss out on some updates then or what? :S

---

### Post by Rasa1111 on 2011-05-21
> **SwingKid said:**
> I give up. There are just too many things which are ****** UP with this newest update, Unity. When I log in to Ubuntu Classic, both my status bars in the bottom and in the top have some weird graphical problem and they are not at all transparent, but look like barred windows...my shortcuts don't work either except the one I use for opening Nautilus and I have lost the ability to use more than just one desktop. What is seriously wrong? Are there anyone else with similar problems in the 11.04 edition? Please let me know, and please do help me with downgrading to 10.10 again. How am I able to do that? I miss it so much! But will I miss out on some updates then or what? :S

 Sorry you're experiencing some of the many bugs that still reside in 11.04. 
I believe that's what all this is.. just bugs that havent been worked out yet.

I have also noticed quite a few, but they are always temporary and last only a short time. 
There are bug reports for them.. So i guess we just wait. (or learn how to fix them ourselves) :lol: 

So yeah, you're not alone in experiencing random, different bugs in 11.04
Ive been using it over a month, and Im finding that, even as well as it works..
its still not stable enough to use as my main install/OS. 

Glad i kept 10.10 on its own partition., 

If you want to go back to 10.10., you have to backup all the files you want to save,
and re-install 10.10,   then move your files back once it's installed. 

 There is no "downgrade".
Just have to reinstall it.

good luck

---

### Post by SwingKid on 2011-05-21
For me, the biggest problem is that they dropped Gnome. But the bugs are extremely irritating. I guess I have to re-install every single program as well now, and take back-ups on all my bookmarks...sucks so hard!

---

### Post by Rasa1111 on 2011-05-21
> **SwingKid said:**
> For me, the biggest problem is that they dropped Gnome. But the bugs are extremely irritating. I guess I have to re-install every single program as well now, and take back-ups on all my bookmarks...sucks so hard!


 Naw you don't have to reinstall every program, 
You can use a couple simple commands to make a list of, and reinstall all of your packages!

> The first step is to use dpkg to generate the list of installed packages.


```
sudo dpkg --get-selections > installed-software
```You now have a list of installed software within the file installed-software.
When  you install a fresh OS you can restore the package list as follows.   Copy your backed up installed-software file to your fresh system and  execute the following commands:

```

sudo dpkg --set-selections < installed-software
sudo apt-get -y update
sudo apt-get dselect-upgrade
```All of your apt packages have been restored!:)

The first command will create a file in your Home folder, called "Installed software"
Save that file to a flash drive or somewhere before you reinstall.

after you reinstall, copy that same file back into your new Home folder.

Then run the last 3 commands.

[http://www.cpuug.org/index.php?topic=219.0](http://www.cpuug.org/index.php?topic=219.0)
[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

 Bookmarks are easy to import/export also. 
Do you know how?

---

### Post by SwingKid on 2011-05-21
Yea I know how to manage that! Thank you so much for your help.
Will this mean that I won't take part of important updates in the future from Ubuntu because I refuse using this stupid Compiz instead of Gnome- system, 10.10?

---

### Post by Rasa1111 on 2011-05-21
> **SwingKid said:**
> Yea I know how to manage that! Thank you so much for your help.
Will this mean that I won't take part of important updates in the future from Ubuntu because I refuse using this stupid Compiz instead of Gnome- system, 10.10?

 No problem. 

 No you will continue to get important updates for 10.10 for another year. No worries. 
You just wont take part in the "latest and greatest" features. Which as you've seen.. is not really a huge deal anyway. 
But you'll still get important security (and program/software) updates and stuff for 1 more year.

---

### Post by SwingKid on 2011-05-21
1 year more, eh. And then what? :)

---

### Post by SwingKid on 2011-05-22
Hey now I have a new installation. But I don't know for sure where to put the file? In the File system- folder in Nautilus or what?

Edit: I fixed it! Thanks heaps for all your help, Rasa!

---

### Post by Rasa1111 on 2011-05-22
> **SwingKid said:**
> Hey now I have a new installation. But I don't know for sure where to put the file? In the File system- folder in Nautilus or what?

Edit: I fixed it! Thanks heaps for all your help, Rasa!


 Niice! good job!
No problem. <3  :popcorn:

---

### Post by georgegerm on 2011-05-24
i must admit i do not like this unity at all. back to the old stuff.
changes and improvements are needed. i do not have the feeling i am in control as before in ubuntu. i hope they go back when gnome 3 comes in. call me old fashion and not very expirienced. but i simply do not like the feel and looks of it. i do understand the project concept. but its just a differnt flavor of ubu. not a new release to me.
i am glad the smaller ubu brother mint has not gone unity. and i hope they stay the course (gnome). libre was a good idea for sure. i hope mint adopts it and gets out of o. office and sun.
maybe a matter of taste, i do not know.
to me its a flop. but i say again TO ME!
but i will agree for some it may be great and in the future, we shall see.
thumbs down for it not being a stand alone ubu distro.
packs like avant, docky and others, gave ubu a great solutions to eye candy and ease of use. i would have gone for an improved version of one these and made the rest of ubu better. for one thunderbird in evolution out. gwenview improved for ubu, or even gthumbs. so much could have been redirected to improvement instead of unity. it should have been unity one and ubu 11 code name ???.

---

