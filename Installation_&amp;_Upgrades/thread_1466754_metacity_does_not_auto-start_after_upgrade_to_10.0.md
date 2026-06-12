---
title: "metacity does not auto-start after upgrade to 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Iskan Der on 2010-04-30
Hello, everyone.

I've just upgraded Ubuntu 9.10 to 10.04 on my eeePC. Everything seems to be fine so far except one thing: metacity does not want to start automatically, so I have to run **metacity --replace** each time after login.
I've removed Compiz installed previously and set window manager to **/usr/bin/metacity** using **gconf-editor**, but still Ubuntu starts without window manager running.
As a workaround I've enabled session state saving, so metacity now starts together with my other applications, however I would like to find a prettier solution. Any help will be appreciated.

---

### Post by My Sam on 2010-04-30
I have the same problem.

After I installed, the window borders (metacity) and the gnome panel were not appearing.

I got the gnome panel to come back by 

rm -Rf .gnome .gnome2 .gconf .gconfd .metacity

and I can get the window borders to appear by running

metacity & 

but it's always broken on login.


I think this has to do with the fact that I had compiz installed with some custom settings, I uninstalled it and set the default and current window_manager settings in the gconf-editor to 'metacity' but still does not work on startup.

---

### Post by ifsteinm on 2010-04-30
Cheers,
I had the same issue here.
I've made a workaround adding metacity as a session app. Go to System --> Preferences --> Session Apps and add /usr/bin/metacity.

That's it

---

### Post by peterpan7191 on 2010-05-01
mind helping around the package names..
i find that there is no 'session apps' in my preferences ..??
how to install it.. ?
n ya im having the same problem of metacity missing

---

### Post by Hilko on 2010-05-02
+1 having the same problem too. No metacity after upgrade to 10.04. So therefore this is the worst upgrade I've ever seen in the past four years.

Also my computer crashed while upgrading.

Terrible upgrade

---

### Post by Dareth on 2010-05-02
I had a similar problem when I upgraded my / partition yesterday. I have never had good luck upgrading Ubuntu, but most of my problems were solved when I backed everything up and did a clean install; though it was sort of annoying. I'm guessing these issues are caused by incompatible settings between the two releases? After the clean install, I set up everything the way I had it in Karmic and now Lucid is fine.

---

### Post by ifsteinm on 2010-05-04
Hi all,

Sorry about the wrong name used before, my system is running in portuguese. But, this "solution" works

go to System->Preferences->Session. On tab "Startup Programs", click the "Add" button and type in "Metacity" as the Name and "/usr/bin/metacity" as the command to run the application.  

By doing this, metacity will be automatically started with your session.


Cheers!

---

### Post by Kochin on 2010-05-06
There seem to be a few possible causes that make metacity not to start after login. I experienced this problem after upgraded Ubuntu Netbook Remix 9.10 to UNE 10.04 final and cleaned out some stale packages.

To find out what happened, you can turn on the debug mode for gnome-session by modifying the line
[INDENT]exec $STARTUP[/INDENT]
in **/etc/X11/Xsession.d/99x11-common_start** to
[INDENT]exec $STARTUP *--debug*[/INDENT]
Then logout and login again, and search the file **~/.xsession-errors** for 'Phase WINDOW_MANAGER'. Read the lines below it to see what happened when gnome-session tried to start metacity. It may also be useful to search for 'metacity' in that file.

In my case, I found a line stating
[INDENT]app /org/gnome/SessionManager/App29 is disabled by Hidden[/INDENT]
It turned out the /org/gnome/SessionManager/App29 was actually read from **/home/<user>/.local/share/applications/metacity.desktop**, and in that file there existed a line
[INDENT]Hidden=true[/INDENT]

Since there is a system-wide metacity.desktop located in **/usr/share/applications**, I simply deleted the one in **~/.local/share/applications** so that gnome-session can read it instead. Logout and login again. Metacity started up nicely without any problem.

Don't forget to remove the *--debug* parameter after you are done with debugging.

---

### Post by benplanet on 2010-05-06
I have the same problem... 

> Since there is a system-wide metacity.desktop located in /usr/share/applications, I simply deleted the one in ~/.local/share/applications so that gnome-session can read it instead. Logout and login again. Metacity started up nicely without any problem.

I don't see anything pertaining to metacity in ~/.local/share/applications


help?

---

### Post by Kochin on 2010-05-07
> **benplanet said:**
> I don't see anything pertaining to metacity in ~/.local/share/applications
Did you turn on --debug and look into .xsession-errors? Debugging messages logged in that file may give you some hints what happened during gnome-session start-up. My .xsession-errors shows the directories searched for metacity.desktop:
```
gnome-session[18334]: DEBUG(+): main: /desktop/gnome/session/required_components/windowmanager looking for component: 'metaci
ty'
gnome-session[18334]: DEBUG(+): GsmUtil: Looking for file 'metacity.desktop'
gnome-session[18334]: DEBUG(+): GsmUtil: Looking in '**[COLOR="Blue"]/home/<user>/.local/share/applications[/COLOR]**'
gnome-session[18334]: DEBUG(+): GsmUtil: Looking in '**[COLOR="Blue"]/usr/share/gnome/applications[/COLOR]**'
gnome-session[18334]: DEBUG(+): GsmUtil: Looking in '**[COLOR="Blue"]/usr/local/share/applications[/COLOR]**'
gnome-session[18334]: DEBUG(+): GsmUtil: Looking in '**[COLOR="Blue"]/usr/share/applications[/COLOR]**'
gnome-session[18334]: DEBUG(+): GsmUtil: found in XDG app dirs: '/usr/share/applications/metacity.desktop'
gnome-session[18334]: DEBUG(+): GsmManager: read /usr/share/applications/metacity.desktop
gnome-session[18334]: DEBUG(+): GsmStore: Adding object id /org/gnome/SessionManager/App30 to store

```
Of course, the cause of your problem may be different to mine. By turning on --debug and looking into .xsession-errors may help you determine the cause.

---

### Post by My Sam on 2010-05-07
I had compiz installed before the upgrade.

I am getting this error message

> 
gnome-session[11386]: DEBUG(+): GsmManager: starting phase WINDOW_MANAGER

gnome-session[11386]: DEBUG(+): Starting app: /org/gnome/SessionManager/App4
gnome-session[11386]: DEBUG(+): GsmAutostartApp: starting 10d3d23d86a874318d126772136930164900000020350022.desktop: command=/usr/bin/compiz.real --sm-client-id 10d3d23d86a874318d126772136930164900000020350022 --ignore-desktop-hints move resize place decoration animation ccp startup-id=10d3d23d86a874318d126772136930164900000020350022
gnome-session[11386]: WARNING: Could not launch application '10d3d23d86a874318d126772136930164900000020350022.desktop': Unable to start application: Failed to execute child process "/usr/bin/compiz.real" (No such file or directory)
gnome-session[11386]: DEBUG(+): GsmManager: ending phase WINDOW_MANAGER
but, I cannot find out how to change it from compiz(which I uninstalled) to metacity...

---

### Post by gshendrick on 2010-05-08
.

---

### Post by Kochin on 2010-05-08
> **My Sam said:**
> I had compiz installed before the upgrade.

I am getting this error message

but, I cannot find out how to change it from compiz(which I uninstalled) to metacity...
Open a **Terminal** window, and run **gconf-editor**.

In the left pane, select **desktop -> gnome -> applications -> window_manager**. Then, change the values for both '**current**' and '**default**' to '**/usr/bin/metacity**'. Next, in the left pane, select **desktop -> gnome -> session -> required_components**. Make sure the value for '**windowmanager**' is '**metacity**'.
Logout and login again (or restart) to see whether it works.

By the way, before you get this problem fixed, you can open a **Terminal** window and run **metacity --replace &** to have the window manager started.

---

### Post by Bobulous on 2010-05-12
Is there any difference in these instructions for someone trying to get Compiz to autostart (other than changing the path to /usr/bin/compiz and the window_manager name to compiz) because I can get window decorations to reappear by running "compiz --replace &", but these settings in gconf don't seem to do that automatically.

---

### Post by Kochin on 2010-05-13
> **Bobulous said:**
> Is there any difference in these instructions for someone trying to get Compiz to autostart (other than changing the path to /usr/bin/compiz and the window_manager name to compiz) because I can get window decorations to reappear by running "compiz --replace &", but these settings in gconf don't seem to do that automatically.
Is there any error message in your **.xsession-errors** file?

I checked the .xsession-errors on my other netbook running compiz, and found only the **windowmanager** setting with a value '**compiz**' in the **desktop -> gnome -> session -> required_components** is required to autostart compiz as the window manager.

If that still doesn't work, try to find clues from **.xsession-errors**. Of course, all these assume you are using **gnome-session** as the session manager.

---

### Post by johntash on 2010-05-13
> **Kochin said:**
> Open a **Terminal** window, and run **gconf-editor**.

In the left pane, select **desktop -> gnome -> applications -> window_manager**. Then, change the values for both '**current**' and '**default**' to '**/usr/bin/metacity**'. Next, in the left pane, select **desktop -> gnome -> session -> required_components**. Make sure the value for '**windowmanager**' is '**metacity**'.
Logout and login again (or restart) to see whether it works.

By the way, before you get this problem fixed, you can open a **Terminal** window and run **metacity --replace &** to have the window manager started.

Thanks Kochin.  I had completely forgot I had compiz running(without special effects) before I upgraded.   This solved my problem I was having though similar to the OPs.

---

### Post by benplanet on 2010-05-14
I gave up on the issue... actually the lucid upgrade did some damage to my otherwise perfect Karmic system, (graphics drivers and compiz were main issues) 

so i just reverted to a clean install :(

---

### Post by clappr on 2010-05-14
I believe I have found an interim solution.  I went to my /home/username/  folder and selected view, view hidden files.  I looked for suspect dot files and one by one I renamed them with a 1 in the name.  For example .local has been renamed .1local  

You can also add *old* to the name.  Essentially I am isolating these files.  Turns out the problem lies withing the .local folder.  Once renamed *.1local* I rebooted.  All my window compositing problems go away.  Now I am still fairly amateur with Linux.  Perhaps someone with more skill can isolate the problem within .local  

So call this one Solved from my view.  I am enjoying the new distro.

---

### Post by clappr on 2010-05-15
Have narrowed the problem down to .local/shared/applications

An educated guess would tell me that within this folder the top suspects are Metacity, Compiz, or Window manager.


Copy everything else to the new .local folder and you are back in business kids...

---

### Post by Marais on 2010-05-15
Found a fix for the windows manager bug in Linux Lucid 10.04 (just updated today and had the same problem).

Easiest fix is to download and install Compiz 

Then in System-Preferences-Startup Manager
add a new startup program
add this in the command line (second box)
compiz --replace --sm-disable --ignore-desktop-hints ccp --loose-binding --indirect-rendering

save and logout then login to test if it works

---

### Post by Chuchaqui on 2010-05-17
That really isn't so much a fix as much as a workaround I think.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/572617/](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/572617/)

---

### Post by Marais on 2010-05-18
> **Chuchaqui said:**
> That really isn't so much a fix as much as a workaround I think.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/572617/](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/572617/)


As they used to say in the Budweiser commercial
"True True":)

---

### Post by mpscheidt on 2010-05-22
Following Kochin's debugging tip, in my case the problem was that a previously saved gnome session, which was inherited from Ubuntu 9.10, tried to run /usr/bin/compiz.real, which however does not exist.

The solution was to remove all saved gnome sessions by:
```
rm .config/gnome-session/saved-session/*
```

On next login, everything was fine.

Cheers,
Markus

---

### Post by Chuchaqui on 2010-05-22
> **mpscheidt said:**
> Following Kochin's debugging tip, in my case the problem was that a previously saved gnome session, which was inherited from Ubuntu 9.10, tried to run /usr/bin/compiz.real, which however does not exist.

The solution was to remove all saved gnome sessions by:
```
rm .config/gnome-session/saved-session/*
```

On next login, everything was fine.

Cheers,
Markus

Yeah that didn't work. Though it did remove an application that would start on startup even though I had it removed so thanks! lol.

**Edit**
I looked at my xsession-errors and played around with my .compiz/session and somehow fixed it. :s

**Edit[2]**
Apparently it only fixed it for one boot? FML -.- (It has returned)

---

### Post by The-REV on 2010-05-23
Folks, want help on video problem. I was running just fine my Karmic and upgraded to Lucid. All appears O.K. But after reboot all applications started appears minimized at left, top, without decoration. I tried all tips found in forums and nothing! Then I formatted my HDD, installed Lucid by CD and the same problem occurs. I returned to Karmic, installed VMWare, tried both Lucid and Isadora Linux Mint on VMW Workstation and the problem cannot be solved. I was thinking that the problem is a metacity bug:  but no - the problem is the video resolution.  I'm using a Gigabyte mobo with onboard videocard and all other OS installed here runs just fine in all video resolutions.
Entering <compiz replace> and <metacity --replace>  I found a error messages as follows:
macarlo@macarlo-desktop ~/Desktop $ compiz --replace
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
**
metacity:ERROR:core/prefs.c:2495:meta_prefs_get_workspace_name: assertion failed: (workspace_names[i] != NULL)
Aborted
macarlo@macarlo-desktop ~/Desktop $

macarlo@macarlo-desktop ~/Desktop $ metacity --replace
**
metacity:ERROR:core/prefs.c:2495:meta_prefs_get_workspace_name: assertion failed: (workspace_names[i] != NULL)

After these steps I discovered that te problem is: my videocard for Lucid only support 800x600 and I've reconfigured to 1200x1024...

My videocard spec:
*-display
description: VGA compatible controller
product: 82G33/G31 Express Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 10
width: 32 bits
clock: 33MHz
capabilities: msi pm bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:27 memory:e1200000-e127ffff ioport:e000(size= memory:d0000000-dfffffff(prefetchable) memory:e1000000-e10fffff

Karmic, Jaunty etc and all other OS runs fine in all resolutions with this Intel onboard videocard but Lucid not. Only in 800x600 windows manager runs normally. Purge nvidia and reinstall nvidia current does not solve the problem. How can I do to fix this?! Can anyone in this forum help me?

---

### Post by geodanny on 2010-07-04
I too am having issues with metacity not starting up when I login. 

.xsession-errors shows this error:
```
Window manager warning: Failed to read saved session file /home/danny/.config/metacity/sessions/10748d29317a0ac3c127828284810146100000013710001.ms: Failed to open file '/home/danny/.config/metacity/sessions/10748d29317a0ac3c127828284810146100000013710001.ms': No such file or directory
```

Anyway to create the file metacity is looking for?


And when I start metacity (metacity --replace) this error shows up: 
```
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4400085 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
```

Like others, I've tried other things on the thread. 
The gconf-editor settings all use metacity rather than compiz.

Update: I gave up. New accounts do not have this problem. So, I created a new account on my machine, moved all files over, along with select hidden files (i.e. .mozilla, .evolution) and changed all the permissions (chown and chgrp) to my new user. It was a pain but much better than waiting for a fix. According to the various bug fixes and troubleshooting discussions, there is something in one of the hidden config files that is causing the bug. Nobody seems to know what it is yet.

---

### Post by rex:) on 2010-07-22
I made all this suggestions and also made a search for metacity.desktop I found it also in the ~/.config/autostart folder with this line
 X-GNOME-Autostart-enabled=false
I changed to 
 X-GNOME-Autostart-enabled=true
That solved my case.

---

### Post by pagarbuk on 2010-07-24
I think I have a similar problem, but I'm not sure.  On startup, lucid sometimes boots to a command line login.  Is this probably a problem with metacity?  In any case, what can I do to either make lucid always launch the GUI or to do that myself from the command-line?

---

### Post by itzco on 2010-07-30
> **Kochin said:**
> There seem to be a few possible causes that make metacity not to start after login. I experienced this problem after upgraded Ubuntu Netbook Remix 9.10 to UNE 10.04 final and cleaned out some stale packages.

To find out what happened, you can turn on the debug mode for gnome-session by modifying the line
[INDENT]exec $STARTUP[/INDENT]
in **/etc/X11/Xsession.d/99x11-common_start** to
[INDENT]exec $STARTUP *--debug*[/INDENT]
Then logout and login again, and search the file **~/.xsession-errors** for 'Phase WINDOW_MANAGER'. Read the lines below it to see what happened when gnome-session tried to start metacity. It may also be useful to search for 'metacity' in that file.

In my case, I found a line stating
[INDENT]app /org/gnome/SessionManager/App29 is disabled by Hidden[/INDENT]
It turned out the /org/gnome/SessionManager/App29 was actually read from **/home/<user>/.local/share/applications/metacity.desktop**, and in that file there existed a line
[INDENT]Hidden=true[/INDENT]

Since there is a system-wide metacity.desktop located in **/usr/share/applications**, I simply deleted the one in **~/.local/share/applications** so that gnome-session can read it instead. Logout and login again. Metacity started up nicely without any problem.

Don't forget to remove the *--debug* parameter after you are done with debugging.
Kochin

Thank you very much!, your solution worked perfectly! Been searching for this for some weeks now!

---

### Post by walkerpett on 2010-08-07
I was having this same problem so I took the advice to look in ~/.xsession-errors. I discovered that my gnome session had compiz as a required component, but because I had uninstalled compiz, no window manager was being loaded.  So in gconf-editor I changed desktop/gnome/session/required_components/window_manager to metacity and now metacity starts on login.

---

### Post by dinesh2n on 2010-08-26
Hi 
In my case my all workspaces scrambled. They could not be switched each other. only one workspace seemed to be open. My cross/maximize/minimize buttons had also disappeared. Later on when I click on workspace with "preferences" it ziggles too much and does not follow your instructions.

Removing ".gconf" and logout login solved my problem. This may be the gconf which is holding the current style of one's workspaces/behavior of other applications. 
Note : After doing that  I needed to reconfigure evolution and some other changes on the other places so that I could come in my earlier type of behavior. 

dinesh

---

### Post by tmvstkp on 2011-05-20
The following fixed my Metacity startup issues.

I upgrade from 9.04 to 10.04 LTS.  After a few months Metacity on my user account stopped working. The other users having no issues.  Started running metacity from xterm so I have managed windows.

Fixed it by deleting /home/<UNAME>/.local/share/applications/metacity.desktop

Now works fine.  If this doesn't work for you then I suggest going down the --debug route.

---

