---
title: "VNC keyboard issue"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by csogilvie on 2010-10-13
I just upgraded to 10.10 today on my web-server.  I normally access it remotely via VNC through a SSH tunnel.

Unfortunately now whenever I'm trying to type something involving the letter 'd' all the windows minimize.  Capitol 'D' is not an issue.

I remember when I upgraded to 10.04 there was a similar odd behaviour for both the letters m and s which was resolved by adding the following code to my vnc xstartup file:

export XKL_XMODMAP_DISABLE=1

I tried removing this line and restarting my VNC server with no success.  'd' still causes minimization of all the windows on my desktop.

I'm running vnc4server.

Access from the console is not plagued with this issue.  (But it is tedious having to call in for a server vault visit!) 

Anybody have any thoughts/ideas on how to resolve this annoying bug?  

As far as my server goes, the upgrade went without a hitch except for this one.  Try typing sudo a few times when your moving web folders around in /var/www and see how annoying this bug is!

I've tried VNC clients on different platforms to eliminate that issue.  I did also try the native GNOME VNC server to the console and that works fine too, but console VNC is not an option since this machine lives in a server vault...  It is secure, but having an open session is not the way you do things!


Somebody please help!

---

### Post by ArcherB on 2010-10-14
I am having the exact same problem  It's become a real pain to have to "copy" the letter D and then paste it whenever I need to type it in.

I have found that the keyboard combo "Windows-Logo"+d will have the same effect.  It's almost as if VNC considers the logo key constantly depressed, except that only seems to affect the 'd' key.

The problem is the same when connecting from both Windows and other Linux boxes.

---

### Post by danhend on 2010-10-15
I am also having this issue, and it is a real pain.  I found that there is a bug filed under launchpad, #655886, labeled "Remote access to vncserver keyboard mapping".  So hasn't there been anyone that has solved this issue?

---

### Post by ksuxtc on 2010-10-15
I ran into this same problem today.

As a work-around:

System->Preferences->Keyboard Shortcuts

Scroll down to "Hide all normal windows and set focus to the desktop", click to highlight, and hit the backspace key to set the shortcut to "Disabled".

I am not sure why this is defaulting to the "d" key, but it certainly is a nuisance.

---

### Post by csogilvie on 2010-10-15
That trick didn't work for me.  It still minimizes everything.

---

### Post by danhend on 2010-10-15
It DID work for me.  Thanks!  I figured it must be some keyboard shortcut default, but I really didn't know where to look.  Whoo whee!!

-Dan

---

### Post by csogilvie on 2010-10-15
I tried it again and set it to something, then set it to something else, then back to disabled.

Now it does work!  PHEW!

Thanks for the kludge.

---

### Post by marfie on 2010-10-21
This was very annoying for a while. It only seemed to happen on screens through VNC that were not the main desktop ie. :1 :2 screens etc.

To get the fix to work I had to make sure the shortcut stayed as showing "Disabled" and I restarted VNC.

Sorted.

---

### Post by ArcherB on 2010-10-29
> **ksuxtc said:**
> I ran into this same problem today.

As a work-around:

System->Preferences->Keyboard Shortcuts

Scroll down to "Hide all normal windows and set focus to the desktop", click to highlight, and hit the backspace key to set the shortcut to "Disabled".

I am not sure why this is defaulting to the "d" key, but it certainly is a nuisance.

It worked for me... sorta.

I don't have a "Keyboard Shortcuts" under System->Preferences.  I had to go System->Control Center->Keyboard Shortcuts.  After that, the instructions were spot on.

Changes did not take effect until after I restarted the VNC session.

Thanx for the tip!

---

### Post by KiwiDude69 on 2010-11-03
Worked a treat but had to kill VnC Server first... Thanks dude!

---

### Post by ericab on 2010-11-03
had the same issue here, and System->Control Center->Keyboard Shortcuts worked for me !

it was driving me nuts.

---

### Post by jebblue on 2010-12-11
Thanks ksuxtc, worked nice find.

---

### Post by Danny Darko on 2011-03-26
Just found this thread as I had the same issue, thanks for the information guys!

I changed the shortcut to Ctrl+Alt+D (this is the gnome default I believe, certainly is on my Solaris 11 box) and didn't have to restart VNC.

Thanks again!

---

### Post by EW2012 on 2012-11-30
> **ksuxtc said:**
> I ran into this same problem today.
 
As a work-around:
 
System->Preferences->Keyboard Shortcuts
 
Scroll down to "Hide all normal windows and set focus to the desktop", click to highlight, and hit the backspace key to set the shortcut to "Disabled".
 
I am not sure why this is defaulting to the "d" key, but it certainly is a nuisance.
 
 
Hi, 
I just installed vnc viewer on my window machine and encountered the same problem.  but I have trouble to locate system->Preferences... could tell me where to find it?
thanks,

---

