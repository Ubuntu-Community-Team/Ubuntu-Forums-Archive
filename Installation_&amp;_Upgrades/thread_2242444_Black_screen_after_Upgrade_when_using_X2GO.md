---
title: "Black screen after Upgrade when using X2GO"
date: 2014-09-01
forum: Installation &amp; Upgrades
---

### Post by Elochai on 2014-09-01
I run a server in Montreal for hosting game servers. I do use the GUI of Gnome and the X2GO client for remote desktoping to it. I find it easier to work on my game servers through a GUI then the console and the GUI doesn't impact the performance of the game servers as the hardware is more then enough to support it. Other words I am looking to get my GUI back.

Server was 12.X.X and I allowed it to do the automatic update to 14.X.X. When logging into the server vi the X2GO client, I get a black screen. No icons, no background, no toolbars, nothing but black. I can log into SSH and everything is running. So I am guessing that something in the new update has either switched something off or has removed it 100%.


Anyone know what this issue is and how I can get my Gnome GUI working once more on X2GO.

---

### Post by TheFu on 2014-09-02
Is the gnome desktop (not gnome3) actually installed on the remote machine? The default GUI is Unity and that doesn't work well with remote desktops at all. That is an understatement.
I use a pure window manager setup - no DE at all.

It is probably easiest to use LXDE instead. This DE definitely does NOT require 3D accelerated GPU support. That is what we need for network remote desktops.

OTOH, I didn't switch to x2go until June and 14.04. Came from FreeNX. X2go is nice, but does have some different behaviors that aren't as nice.  Video and audio ARE excellent, however.

---

### Post by Elochai on 2014-09-02
I used to always use console on my game servers through SSH but GUI is much better for managing for me.

When I bought the server, I went with the host flavor of Ubuntu Desktop 12.04 "Precise Pangolin" LTS + x2go (64bits).

When I upgraded, I figured the settings of x2go and the desktop would be left alone. Now I can't get anything but a blank black screen. I'd like to just get it working again.

In x2go I use this command line: gnome-session --session=gnome-classic

I don't want to switch what I use for remote desktop, I very much like x2go. But right now with this issue, I fear I may have to downgrade / reinstall and start over again and run an outdated version of Ubuntu just to have it working again. I really hope it doesn't come to that and someone could tell me what to do to fix this issue.

---

### Post by TheFu on 2014-09-02
Every release of Ubuntu desktop changes the default desktop slightly. Remote desktop support is NOT a priority from what I've seen.  I don't use gnome, so I can't help with setting for that - are you certain - ABSOLUTELY CERTAIN - that deskop code is installed and not the 3D gnome3?

So - I tested the "gnome" session on a 14.04 remote desktop and saw the same result as you.  No window manager ... the session log said it was trying to do something with KDE - which I don't have installed.  I don't have gnome installed either.  

Also tried to use the XFCE4 desktop - which is NOT installed either - it connected and closed immediately.  So - I'm thinking some of the gnome libraries are there, but not the session management.

For fun, I told it to run a custom program - /usr/bin/xterm.  So - that did what was expected - it connected and an xterm was opened. No desktop, no window manager.  From there, I was able to start openbox and my normal environment happily.

So - now I created a custom startup with 
/usr/bin/openbox --config-file /home/thefu/.config/openbox/rc.xml

Worked perfectly.

Hope this helps you figure out the answer.

---

### Post by Elochai on 2014-09-02
How would I verify that gnome was correctly installed when it updated, I'm a noob to most of this stuff. Once I have a system working the way I need, I don't normally make changes to it. Matter a fact I was debating this update but figured it could have core updates to improve performance which would be good on resources.

---

### Post by TheFu on 2014-09-02
Google found this: [http://ubuntuhandbook.org/index.php/2014/04/install-gnome-classic-desktop-in-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/04/install-gnome-classic-desktop-in-ubuntu-14-04/)
I didn't try it or test it in anyway. There were other sets of instructions available too - from other reputable websites.

I don't usually screw with my desktops either, which is why using a pure WM is what I like best.  Much less bloat and less for Canonical to screw with.  Heck - I can still run the WM I used in 1996, fvwm. It works the same today as back then, which is both great and terrible. ;)

---

### Post by Elochai on 2014-09-03
I installed it but the issue is still there.

---

### Post by TheFu on 2014-09-03
What does the x2go log say on the client side?  Server side?

---

### Post by Elochai on 2014-09-06
> **TheFu said:**
> What does the x2go log say on the client side?  Server side?

Not to sure where I'd find logs too for X2GO but this is from the client during connecting:


```
Copyright (C) 2001, 2010 NoMachine.

See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '6608'.

Session: Starting session at 'Sat Sep  6 11:53:27 2014'.

Info: Connecting to remote host 'localhost:31001'.

Info: Connection to remote proxy 'localhost:31001' established.

Info: Connection with remote proxy completed.

Warning: Unrecognized session type 'unix-kde-depth_32'. Assuming agent session.

Warning: Failed to read data from the X auth command.

Warning: Generated a fake cookie for X authentication.

Info: Using ADSL link parameters 512/24/1/0.

Info: Using cache parameters 4/4096KB/8192KB/8192KB.

Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_32'.

Info: Using ZLIB data compression 1/1/32.

Info: Using ZLIB stream compression 4/4.

Info: No suitable cache file found.

Info: Forwarding X11 connections to display 'localhost:0'.

Session: Session started at 'Sat Sep  6 11:53:28 2014'.

Info: Established X server connection.

Info: Using shared memory parameters 0/0K.

```


Sorry for the late reply, my job gets really busy at times and I can be doing 3AM - 7PM shifts.

---

### Post by TheFu on 2014-09-06
> 
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_32'.

Huh? KDE?
R U running the session you want?  If the presets don't work, try manually doing it, as outlined previously.

---

### Post by Elochai on 2014-09-06
I have tried the sessions: 
Custom Desktop using command: gnome-session --session=gnome-classic (Which is the listing you see there with that '16m-jpeg-9' with session 'unix-kde-depth_32')

KDE (Which gives me an Error of Unable to Execute: startkde)

GNOME (Which gives me a black screen and a popup of system problem)

LXDE (Which gives me an Error of Unable to Execute: startlxde)

XFCE (Which gives me an Error of Unable to Execute: xfce4-session)

UNITY (Which gives me nothing but a black screen)

XDMCP (Which gives me a black screen)

I believe what you see there for '16m-jpeg-9' with session 'unix-kde-depth_32' is just the image quality but I am not 100% sure as I don't know to much about it.

---

### Post by TheFu on 2014-09-06
Have you tried the custom setting and specifying the exact path to the command?

Trying to run startlxde without having lxde installed should fail. Same for xfce4.

Try the custom solution.

---

### Post by Elochai on 2014-09-09
> **TheFu said:**
> Have you tried the custom setting and specifying the exact path to the command?

Trying to run startlxde without having lxde installed should fail. Same for xfce4.

Try the custom solution.

Well I do have lxde installed as I did install it after in hope of having some form of desktop. I don't know the command line to use for the custom settin. The one I used for gnome was provided with the linux installion from my server provider.

---

### Post by Elochai on 2014-09-14
Well it looks like no one knows how to fix this issue which leaves me with having to format the entire server and reinstall from the ground up.

---

### Post by tquinn10 on 2014-11-20
I am having the same problem. I was using nomachine and it was working great... until the upgrade. Post upgrade, it connects but just get a black screen. After exchanging about 15 emails with support, they told me to purchase a license for 4 users, for $125/year.

I then tried to use x2go after seeing good reviews, but I get the same problem.

I think the issue is with 14.04; did doing an entire install fix the problem?

---

### Post by jfernyhough on 2015-02-08
There's a bug here: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1251281](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1251281)

Solution for now: add eugenesan's PPA ([https://launchpad.net/~eugenesan/+archive/ubuntu/ppa](https://launchpad.net/~eugenesan/+archive/ubuntu/ppa))

---

