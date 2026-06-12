---
title: "X-Server Error"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by matthews_406 on 2007-09-09
Before I begin, I have looked at the other threads but they don't really help me much...

So my problem.
I get a black screen after Ubuntu is done loading the orange bar.
I can hear the sound but the log-in screen is not there.

I found out that when you press alt-ctr-f1, it brings me to a text log in.
Here I can log-in and I tried to

"startx"

it gives me this.

Fatal Server Error:
Server is already active for display 0. If this server is no longer running, remove /tmp/.x0-lock and start again.

Xlib: connection to "0.0" refused by server.
Xlib: Invalid MIT-Magic-cookie-1 key
giving up

x init: Unable to connect to x server
x init: no such process (errno 3): server error.
----------------------------------------------------------------------------

So, does anyone have any suggestions?

Graphics card I have is: Nvidia 8600 GT


I am using a library comp atm, if no help is posted, I going back to vista.

---

### Post by merlinus on 2007-09-09
Is "I am going back to vista" a threat?:

:)

After logging in, at the command line, try this:

```

sudo dpkg-reconfigure xserver-xorg

```You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```or reboot.

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

---

### Post by matthews_406 on 2007-09-10
I have a GUI....just not on my internal monitor, I get a display when I attach a external monitor...


Xserver is runing on server 1, but I want it to go to server 0...how do I do this? The everything works...it just not nice dragging a extra display to class with a laptop... might as well have bought a desktop.

---

### Post by matthews_406 on 2007-09-10
> **merlinus said:**
> Is "I am going back to vista" a threat?:

:)


no, that was just an attempt to get help quicker :P

---

### Post by jimbob on 2007-09-10
I take it this problem exists on a laptop?  What is its make and model number?

Most laptops have a hardware mechanism to switch between internal and external displays; some combination of Fn+Fx where x is one of the numeric function keys.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by jimbob on 2007-09-10
I'm thinking you need the right driver for your Nvidia 8600GT.  Check post #2 in this thread for ways to get it:

[http://ubuntuforums.org/showthread.php?p=3343183#post3343183](http://ubuntuforums.org/showthread.php?p=3343183#post3343183)
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

