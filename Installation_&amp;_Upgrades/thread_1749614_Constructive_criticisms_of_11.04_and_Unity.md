---
title: "Constructive criticisms of 11.04 and Unity"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by ted_rmt on 2011-05-04
Upgraded to Natty Narwhal 11.04 and tried to keep an open mind, but after hours of frustration I have decided to post some of the issues that will make me downgrade to 10.10 or maybe back to 10.04.

1) Cannot enable visual effects. Might just be 11.04 misbehaving with my nVidia driver. Tried with Unity and without it. Tried in Ubuntu classic section. Uninstalled the driver and reinstalled. It says it is activated but is not being used. I had always assumed that activated meant it WAS being used. Makes me second guess everything I do in Compiz. I had screaming cool effects happening in gnome in 10.10 but now those are all dead.

2) Unity does not let me include folders in the side pane on the left. Seems as though not all applications can go there either. Drag one to the left and . . . denied. It bounces back to the dash. Not sure what the rules are. No more time left to find out.

3) Unity dashboard Files and Folders/Recent documents. Turned on by default logs all documents you view and you cannot clear the recent document history. It will show files there even if you rename them to make them hidden files.

4) Dashboard cannot be resized as far as I can see. Always takes up the whole workspace.

5) Unity load time is slow. Intel atom 1.7 GHz processor with the nVidia ION gpu and 2 Gig of DDR2 800 (I think) RAM. 

6)Side pane comes out of autohide whenever I try to hit the back arrow in Firefox 4 - like all  the time! Had to go to View/Toolbars/Customise and add a divider two spaces and another divider to keep the button clear of the side pane to keep it from interfering whenever I want to use the mouse to go back apage

7) And the most annoying. The window side bar auto hides. This means you have to play mouse footsy every time you need to scroll up and down. If you use a trackball mouse (as I do) rather than a wheel mouse, knowing exactly where (not approximately where) the side scroll bar is is important. Fortunately firefox did not adopt this. Perhaps there is a way to turn the auto hiding scrollbar off in Compiz (CCSM) but I have spent many hours looking for it and it is not obvious.

---

### Post by geoffm on 2011-05-04
I agree. Here are the major drawbacks for me:

**Windows List**
I like to be able to see instantly at all time which apps are running on my current workspace. There doesn't seem to be a convenient way to do that, i.e. a decent substitute to the windows list applet.
ALT W seems to ignore the windows that are minimized !?! (there should be an option, at least)

I think there is some kind of way that the launchers show they have open program windows in the sidebar, but it is very suble and unintuitive. Some of them have a red or blue background color, some have arrows on the left or right side. I don't know what that means. also not all the apps have a launcher icon, so this definitely doesn't count as a suitable replacement for windows list.

**Panel customization**
What if I want to add menu item options for an app, such as "open address book" and "compose new message" menus for thunderbird?
What about applets for the panel? I like to have a temperature monitor applet, as well as cpu and network monitors, and I really needed that Inhibit applet.

---

### Post by ted_rmt on 2011-05-04
Replying to my own thread because I have fixes for those who want to give Unity a fair test. The theme of the first post is about problems that I could not work around. This post is about some for which I found solutions.

1) Toning down that distracting panel on the left. If you read English you have to track left to read a new line. Big colorful icons are distracting. Click the application icon in the Launcher (the annoying panel that we want to fix) Find the CompizConfig Settings manual and drag it to the launcher to make it handy. Now open CCSM and click the word Unity to change its settings. DO NOT DISABLE UNITY. Choose the experimental tab and shrink the icons down. You can also turn off the backlighting to give the icons in the launcher a much more unified appearance.

2) Emergency file access. If you accidentally turn Unity off and have no folders on the desktop you will be faced with your wallpaper and no means of accessing anything. Insert a flashdrive. When it mounts, open the folder and navigate back to user/shared/applications, where you will find the compiz configuration settings manager. Open it and enable Unity.

3) No panel, don't despair. Click the power down icon and note the System Settings option. It opens a pretty menu similar to Linux Mint, with all the Administrator and Preference options grouped in a nice Control Centre.
Note: Sometimes Unity's integrated top bar will not redraw after toggling things in CCSM. There is a chance that power down icon is still in the extreme upper right of your screen, you just can't see it.

4) Any window with a function along the left hand side. Resize the window and get it away from the Launcher. If this is a frequent problem, try using CCSM again and change Unity properties to disable auto hide. There is also an option to only show the launcher when you bring the cursor to the extreme upper left, if that woks for you.

I am through with Unity. I don't think it is so bad but to me it seems more suited for a cell phone or gadget GUI than a desktop. It is resource heavy, as gnome3 will be, and I am all about low power computing and having a seamless interface that moves fast. In future I may have to make the switch to another ubuntu distro and learn how to tack an older gnome session onto it or something, but I have no idea how to do that and it means more time and study.

If ubuntu keeps adding annoying gui changes that interfere with my productivity, it might be more time/cost effective to make the switch to Linux Mint.

---

### Post by ted_rmt on 2011-05-04
Reply to geoffm:

There is a small white arrow that appears in the launcher icon when a process is running. It is true this is very subtle.
However, if you turn backlighting off in CCSM/Unity then the backlight will be visible when the process is running which is MUCH less subtle.

This is still not as nice as seeing a collective list with titles for folders and files you have open. Multitasking becomes much more difficult.

In general, I see Unity, gnome3 and for that matter Windows 7 going in the wrong direction, sacrificing customisation for glitz. There is just no reason I can think of why I should involve graphics acceleration in the simplest processes. Unnecessary  demand on system resources. Not a surprise from Microsquash but odd for a Linux distro.

Finding applications on the Dash is much less efficient than seeing them all at the same time in a list dropping down (or rising up) from a panel, and why not have the ability to put your launchers anywhere on the screen where they are most convenient for you. Too rigid. Simple fixes like the ability to resize the Dash or move the Launcher would be welcome.

---

### Post by ted_rmt on 2011-05-04
> **geoffm said:**
> 

**Panel customization**
What if I want to add menu item options for an app, such as "open address book" and "compose new message" menus for thunderbird?
What about applets for the panel? I like to have a temperature monitor applet, as well as cpu and network monitors, and I really needed that Inhibit applet.


You can create and drag launchers to the panel and they will work. However, you cannot change their appearance so they all look like the generic gnome springboard launcher icon. 

You can click on the appearance tab when you are making the launcher and select another .png file for it like you could in gnome, but when you drag it to the launcher the appearance reverts back.  As a result, having many custom launchers on the launcher panel will get confusing unless someone introduces a way of changing their appearance.

---

### Post by Frogs Hair on 2011-05-04
I used a dock in 10.04 and 10,10 and there  some things that I also   apply to Unity , when you open an application  and the icon appears on the panel , right click  the icon and select keep in launcher.

Another thing I did was add the control center or system setting as it is called in Unity to the dock/ panel allowing access to all the items on the system and administration menu .

I never stored folders on my dock or kept the window t list installed  so I can't offer any suggestions . On the Unity panel  there is the home folder and files and folders which offer me plenty of access to folders .

---

### Post by Paqman on 2011-05-05
> **geoffm said:**
> I really needed that Inhibit applet.

So did I. Luckily however there's [Caffeine]("https://launchpad.net/~caffeine-developers/+archive/ppa"), which is even better than the old inhibit applet, as it can automatically inhibit sleep when certain programs are running.

---

### Post by ted_rmt on 2011-05-08
Well here is something that is working well for me.

Ubuntu classic session in 11.04. Can't activate compiz effects at all. With Firefox 4 and no Compiz effects functionality, all my flash videos are stable. That was becoming a more and more pervasive problem in my 10.10 install as Adobe kept mucking around. No more ghost images of videos on all my icons.

Ubuntu session (with Unity) now works after a workaround published online linked here on OMG! Ubuntu!:

[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/)

That gets your cube working again. Other Compiz effects will work in Unity normally, like animations for opening and closing windows and painting fire on the screen.

Had to do a rethink and embrace the notion of using different sessions for different mindsets.

Now when I want stability for gaming and the kind of functionality I get from a personally customisable desktop, I log in to the ubuntu classic session. (The cool 3D sphere did not increase my productivity)

When I want cool effects, they are now used in the Unity session. Something that I like about Unity now is that when I click on something that is already open on the unity launcher, it flips the cube when reopening the window. Very slick.

Still hate the dashboard. Not being able to customise files and folders makes it useless as a tool for finding anything.
Favourite folders? Whose favourite folders? 

The dashboard apps needs the option of removing the list of apps available for download as well. Too much like advertising. Nice for people who want it, but extremely annoying if you don't.

Lots of potential in the apps and files and folders menus for the launcher. Just needs a little bit of customisability.

---

