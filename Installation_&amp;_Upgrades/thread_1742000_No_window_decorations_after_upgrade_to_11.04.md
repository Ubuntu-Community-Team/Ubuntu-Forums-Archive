---
title: "No window decorations after upgrade to 11.04"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Wickk on 2011-04-28
I upgraded to 11.04 this morning, and I just flat out have zero window decorations which is a serious problem. This pretty much means that where windows happen to spawn is where they're stuck as I cannot move them ( aside from chrome which has its own I believe. )

This happens in Unity and  Gnome-panel, fluxbox remains unaffected. I've completely removed, reinstalled unity and compiz several times now. That's not the problem. I've tried pointing the window decorator to /usr/bin/gtk-window-decorator but I might as well be shouting at a wall for all thats doing.

running unity --reset is have zero results as well. 

If it matters at all my video card is an ATI HD Radeon 4650, and yes I've uninstalled the proprietary driver and reinstalled it ( I get the same results with the open source driver ). Also if it makes any difference I'm running 64 bit.

---

### Post by Hedgehog1 on 2011-04-28
Please user the Ubuntu Software Center and install:

**Compiz Window Decoration Library**

*The window decoration library is responsible for drawing the window borders and title bar of windows managed by Compiz. It is used by window decorators like gtk-window-decorator and kde-window-decorator.*


***The Hedge***

:KS

---

### Post by Wickk on 2011-04-28
Searching for it in software center yields no results, however I can find it via synaptic in which cases its already installed. A complete removal and reinstall again gives no change

---

### Post by Hedgehog1 on 2011-04-28
> **Wickk said:**
> Searching for it in software center yields no results, however I can find it via synaptic in which cases its already installed. A complete removal and reinstall again gives no change

Well darn - it was **SUCH** a good idea, too.

I am tapped out on this - perhaps others will know the secret?


***The 'pondering' Hedge***

:KS

---

### Post by mafitzpatrick on 2011-04-28
Have you accidentally installed a preview of Natty +1? After merging window decorations into the top panel this release, the next logical step in the quest for 'minimum screen real estate' must be to get rid of them completely? I'm waiting for Natty +2 where they get rid of the windows too ;)

Now to try help...

Is the CompizConfig Settings Manager installed by default? Hit the Ubuntu button type in 'Compiz' and it should come up. If not install it from the Software Centre. Run it (Ubuntu button -> 'Compiz' -> click it) then in the panel that comes up scroll down and find 'Window Decoration' under 'Effects'. Is the plugin activated? It should be.

Hope this helps

---

### Post by Wickk on 2011-04-28
> **Hedgehog1 said:**
> Well darn - it was **SUCH** a good idea, too. 

I even got myself all excited!

---

### Post by Wickk on 2011-04-28
> **mafitzpatrick said:**
> Have you accidentally installed a preview of Natty +1? After merging window decorations into the top panel this release, the next logical step in the quest for 'minimum screen real estate' must be to get rid of them completely? I'm waiting for Natty +2 where they get rid of the windows too ;)

Now to try help...

Is the CompizConfig Settings Manager installed by default? Hit the Ubuntu button type in 'Compiz' and it should come up. If not install it from the Software Centre. Run it (Ubuntu button -> 'Compiz' -> click it) then in the panel that comes up scroll down and find 'Window Decoration' under 'Effects'. Is the plugin activated? It should be.

Hope this helps

Yeah CCSM is installed, and the Window Decoration plugin is activated.

---

### Post by mafitzpatrick on 2011-04-28
System Settings -> Appearance -> Theme is Ambiance installed and selected?* Perhaps the theme got messed up on install/upgrade, try a few others and see if anything comes to life. Checked the themes are installed (package named 'light-themes')?

Can you tell I'm out of ideas yet? :(

[* On that point, mine has 'Custom' selected - can someone who has done a fresh install confirm that's right? ]

---

### Post by Wickk on 2011-04-28
Yeah regardless of what theme I use I get the same issue, I might just back up and do a fresh install :(

---

### Post by hawthornso23 on 2011-04-28
Open the window decoration plugin and look down towards the bottom where it says which windows will be decorated. Make sure it says `all'.

By the way, you can live without window decorations. It is a lot of screen to waste on three buttons. I've done away with them completely (on my machine the setting says `none') and use compiz plugins to open/close windows and throw them around the screen.

---

### Post by Wickk on 2011-04-28
> **hawthornso23 said:**
> 
By the way, you can live without window decorations. It is a lot of screen to waste on three buttons. I've done away with them completely (on my machine the setting says `none') and use compiz plugins to open/close windows and throw them around the screen.
Thats my main issue with this, as it is right now chrome is the only window I can resize/move to where I want it on my screen.

---

### Post by hawthornso23 on 2011-04-29
> **Wickk said:**
> Thats my main issue with this, as it is right now chrome is the only window I can resize/move to where I want it on my screen.

Look under window management in the compiz config settings manager. Activate the `move' and `resize' plugins and assign mouse shortcuts to them. There are also some useful settings hiding under `general'. In particular the window menu, maximise, minimise and close actions can be found and assigned there. And activate a couple of switchers - the ring switcher and shift switcher are both good. 

With a bit of thought as to which key/mouse settings to use you can set something up so you'll never miss the titlebar. I use the `windows' key in combination with other stuff for all my windows actions which makes it easy to remember.

---

### Post by aquamaster on 2011-04-29
i have this same problem i cant enable windows decorations because then my unity intrface disappears even throught thats enabled

---

### Post by bscoder on 2011-04-29
Enabling the Window Decorations plugin in CCSM was the fix for me, but I had already jettisoned the seemingly useless Unity by that time. (By switching to Unubtu Classic mode on the login screen.) Maybe the Unity window decorations have problems with compiz?

edit: Ok, sorry! Unity isn't really useless. I just thought it was because I couldn't get my sftp gtk bookmarks to work and they're important to me, but I've since found a solution to that.

---

### Post by Wickk on 2011-04-29
I'm just giving up for now and sticking with fluxbox. I can get by with using ctrl, super, and alt to resize and movie my windows, but thats feels like a giant step back. I've installed, reinstalled, reconfigured compiz and CCSM and no dice. Maybe I'll try again in a few weeks.

---

### Post by MugOTea on 2011-04-29
I'm hoping there'll be an update in short order to fix it, or at least give us an option. I can get by without window decorations but it makes my desktop feel scruffy not having borders and titles on pop-up windows and dialogs.
Has any one else experienced a unstable topbar too? It crashes when changing compiz settings or pulling chrome from a maximized state.

I have to admit, the updated firefox, and unity combination work well when FF is maximized and being able to pin tabs... it's not all bad.

---

### Post by SecretCode on 2011-04-29
In 10.10 (and earlier versions) I occasionally found Compiz would lose window decorations. To fix this I always installed **fusion-icon** (runs in the notification area) and selected "Reload Window Manager" from its right-click menu. Not tested this in Unity yet, though.

---

### Post by magnificent on 2011-04-29
I've got compiz fusion icon installed but it doesn't seem to do anything.  What I do have is a maximise minimise and close icon when a window is full.  They are not in any theme I have chosen and disappear when the window is not full size?
The rest of compiz works fine, I can grab windows, resize them and throw them all over the cube.  Miss the eye candy from emerald though.

---

### Post by MugOTea on 2011-04-29
The more I use it the more I really miss my window decorations but I'm determined to try unity...

Any Ubuntu gurus out there with any more suggestions??? please...

Can OP add some tags to his post to see if it gets more attention? ;)

---

### Post by Wickk on 2011-04-29
> **MugOTea said:**
> 
Can OP add some tags to his post to see if it gets more attention? ;)

Done.

 I'm not really watching this thread anymore however. If something good comes out of it then well all the better but for the most part like I said previously I'm remaining happy with fluxbox

---

### Post by MugOTea on 2011-04-30
FIXED MINE!! :KS

I just resolved this issue on my laptop, I'll share here and hope it works for anyone left watching the thread:

I was using Emerald themes before the upgrade, some people were saying their themes weren't working and they were told that Unity didn't fully support Emerald, or xml themes yet... so I thought stop using Emerald with unity for now.

1/ Open teminal
2/ Type: cd ~/.config/compiz
3/ Type: gedit compiz-manager
4/ Make sure it only says - USE_EMERALD="no"
5/ Save the file, and log off, and on again!

And I got my close restore and minimize buttons back, it looks nice again!

Hope this helps someone!

:guitar:

---

### Post by bponder on 2011-05-02
> **MugOTea said:**
> FIXED MINE!! :KS

I just resolved this issue on my laptop, I'll share here and hope it works for anyone left watching the thread:

I was using Emerald themes before the upgrade, some people were saying their themes weren't working and they were told that Unity didn't fully support Emerald, or xml themes yet... so I thought stop using Emerald with unity for now.

1/ Open teminal
2/ Type: cd ~/.config/compiz
3/ Type: gedit compiz-manager
4/ Make sure it only says - USE_EMERALD="no"
5/ Save the file, and log off, and on again!

And I got my close restore and minimize buttons back, it looks nice again!

Hope this helps someone!

:guitar:

I don't have a "compiz" directory under .config, only a compiz-1, and then a directory underneath that called compizconfig.  Creating a file called compiz-manager underneath compiz-1 did nothing.

I'm having to boot into Ubuntu Classic (no effects) as a workaround right now.

---

### Post by maberib on 2011-05-04
> **bponder said:**
> I don't have a "compiz" directory under .config, only a compiz-1, and then a directory underneath that called compizconfig.  Creating a file called compiz-manager underneath compiz-1 did nothing.

I'm having to boot into Ubuntu Classic (no effects) as a workaround right now.

Me neither.

What did work for me:
1. Open up a terminal ( if you can't do so, right click on the desktop, click "create launcher", name:"terminal", command "gnome-terminal", then hit "OK" and use the newly created shortcut on your desktop)
2. In the terminal type and run "compiz --replace"

This loaded the sidebar and the made window decorations work.  Once Unity loads, one can make this a bit more of a permanent solution by: 
1. clicking on the Ubuntu Icon at the top left
2. Searching for "settings"
3. Choosing "system settings"
4. Clicking on "startup applications"
5. Clicking "add"
6. Name:  anything you want. Maybe "unity fix"
7. Command: "compiz --replace"

Hopefully this helps someone!

---

### Post by ted_rmt on 2011-05-06
Tore my hair out over the Compiz settings and learned a bunch. I had this same problem along with several others.

Problem is Unity will stop drawing or the Windows decorations will stop drawing almost any time you change settings in Unity or whenever there is a conflict with Unity.

Almost all will redraw if you relog, except the Windows decorations.

Before you try a radical fix, go into the CompizConfiguration Settings Manager (CCSM) and [COLOR=Blue]just disable and re-enable the Windows decoration[/COLOR]. If you don't get the Max/min/close border trim back right away (I did) try relog then.

Recently got all my CCSM effects working in Unity with the help or this site offered to us on another thread about Natty and Compiz :

[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/)

The GUI option to fix the cube by disabling the auto manage plugins in CCSM/Preferences (read the article) may help with Windows decoration as well.

In general:
1) Expect nasty, loss of menu bars and unity disappearing when you make big changes in CCSM. 
2) Be patient. When you make a CCSM change, wait 5 seconds or so to enable a change. Toggling something on and off quickly will give you a false negative when you troubleshoot.
3) Click the top right corner of the screen, even if you cannot see the unity top menu bar. Under the shutdown options, you will see a systems settings option that opens a control center with all preference and administration apps
4) If you lose the whole GUI with nothing but the desktop, plug in a flashdrive and open the mounted folder, then navigate back to file system\\usr\share\applications and reopen the CompizConfig Settings Manager from there.

---

