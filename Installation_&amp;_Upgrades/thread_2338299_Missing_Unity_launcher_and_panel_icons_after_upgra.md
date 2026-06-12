---
title: "Missing Unity launcher and panel icons after upgrade"
date: 2016-09-26
forum: Installation &amp; Upgrades
---

### Post by Gins on 2016-09-26
Suddenly my Ubuntu Desktop giving me problems.

Recently, I upgraded to 16.04 version of Ubuntu.

On the right corner, there are  a couple of symbols.

I think this is a standard.

I shutdown the computer clicking an icon on the right corner.

Now there are no icons on the right corner

So I can't shutdown the computer.

On the left side of the computer, I could see several icons or rather a bar; they include 'wordprocessor' , 'settings, 'shell', etc.

Now I don't see those lines of icons (bar) on the left side of the computer.

I get a completely empty screen.

**I can't shutdown the computer and I can't get my wordprocessor program**.

1) When I start the computer, it asks, as usual, the password.

2) Then I write the password and it accepts the password.

3) I get a screen without the right corner icons and the bar of the icons on the left side.

4) However, I found a way to get the browser.  I just right click on the desktop.

5) Then I get the option open terminal.

6) Afterwards, I write the words ' google-chrome-stable '

7)  I  can get the browser.

'**  I CANT SHUTDOWN THE COMPUTER BECAUSE THE LEFT CORNER ICONS ARE NOT THERE.
**  I CAN'T GET EITHER THE WORD PROCESSOR PROGRAM ICON OR TOOLS ICON BECAUSE THE RIGHT BAR IS MISSING.
** I BADLY NEED THE WORD PROCESSOR PROGRAM.
**  I JUST GET A EMPTY SCREEN.
**  FOR THE NAKED EYE, THIS LOOKS LIKE A PROBLEM OF SCREEN RESOLUTION.  I DON'T KNOW HOW TO FIX THE PROBLEM.

[COLOR=#FF0000]**  I NEED YOUR HELP. I SUDDENLY GOT THIS PROBLEM.

** I MUST GET THE RIGHT CORNER ICONS AND THE LEFT BAR ICONS.[/COLOR]

** PLEASE HELP ME.

...............................................................................................................................................................................................................................................
I can shutdown the computer using the following awkward method.
1. right click
2. open terminal
3. sudo shutdown -h
..................................................................

I wrote the following command on the terminal and got the message that it is not installed

inxi -F
..........................................................................
The program 'inxi' is currently not installed. To run 'inxi' please ask your administrator to install the package 'inxi'

---

### Post by ubfan1 on 2016-09-26
In the terminal, type 
unity-control-center display
and see if you need to reduce the resolution to what the monitor can show.  If you have a second monitor plugged in, maybe the panels are on it?  Anyway, unplug the second monitor before the next time you boot.

---

### Post by Gins on 2016-09-27
Thanks ubfan 1

It seems the resolution has nothing to do with this problem

xrandr -s 1024x768

The above command changes the resolution.

The above command works fine.

I tried with 800x600 , 1280x1024 etc.

I got big letters and small letters on the desktop.

The problem is I can't open my wordprocessor program.

Because the bar on the left side is no longer there.

I don't find the icons on the right corner. So I can't shutdown properly.

Ctrl + Tab combination is also dead. I can't change the windows.

What is the problem?

**The left bar is hidden and the right corner icons are hidden.**

Please help me.

...........................................................................................

unity-control-center display

The above command works fine.

However, I can easily change the resolution using ' xrandr ' command.

( I don't have a second monitor. Just a single computer and a monitor.)

---

### Post by ubfan1 on 2016-09-27
If you log in using the guest session, does the desktop look OK?  If so, the problem may be a local config file (file or directory starting with a dot) in your home directory.

---

### Post by Gins on 2016-09-27
Yes, guest session works fine.

You touched on an issue in my home directory.

Let me know how to fix it.

I appreciate your help.

............................................................................................
I
sudo apt-get install compizconfig-settings-manager

Then I ran it by doing this:

export DISPLAY=:0
ccsm

I found the Unity Plugin and I enabled it.

When the computer restarts, everything disappears.

**My computer worked fine. Suddenly I developed this problem. it is very strange,**

---

### Post by ubfan1 on 2016-09-27
I'd make a directory in your home like olddot, to allow you to move the dot directories off your home (so they cannot affect anything), but you can restore them if necessary.
Start with .cache
mv .cache olddot
and see if that fixes things.
If not , do .config, .compiz .gnome .gnome2, gnome2-private
Still no fix, move them all, so you start just like the guest session does.

---

### Post by zweiundzwei on 2016-09-28
I have exactly the same issue, also after an update earlier today.

Update: deleting .cache worked, thanks ubfan1! Something seems mildly different about the display now, can't put my finger on it... slightly changed system font maybe? Doesn't bother me particularly though.

Very odd.

---

### Post by Gins on 2016-09-30
Ubfan

Eureka!

The following command fixed the problem.
mv .cache olddot
Now everything works as usual.
What was the trick?
**I take my hat off for your for the great help**

I pray for God that this grave problem should never to come again.

---

### Post by x-manfred on 2016-10-05
Thank you!
"ubfan1 	 	 		[INDENT] 			 				Re: Missing Unity launcher and panel icons after upgrade
 			 			I'd make a directory in your home like olddot, to allow you to move  the dot directories off your home (so they cannot affect anything), but  you can restore them if necessary.
Start with .cache
mv .cache olddot
and see if that fixes things.
If not , do .config, .compiz .gnome .gnome2, gnome2-private
Still no fix, move them all, so you start just like the guest session does. 		" 

I have looked many hours for a solution. your tip has worked. :=)

gtx fred
[/INDENT]

---

### Post by x-manfred on 2016-10-05
Thank you!
"ubfan1 	 	 		[INDENT] 			 				Re: Missing Unity launcher and panel icons after upgrade
 			 			I'd make a directory in your home like olddot, to allow you to move  the dot directories off your home (so they cannot affect anything), but  you can restore them if necessary.
Start with .cache
mv .cache olddot
and see if that fixes things.
If not , do .config, .compiz .gnome .gnome2, gnome2-private
Still no fix, move them all, so you start just like the guest session does. 		" 

I have looked many hours for a solution. your tip has worked. :=)

gtx fred
[/INDENT]

---

### Post by x-manfred on 2016-10-05
Thank you!
"ubfan1 	 	 		[INDENT] 			 				Re: Missing Unity launcher and panel icons after upgrade
 			 			I'd make a directory in your home like olddot, to allow you to move  the dot directories off your home (so they cannot affect anything), but  you can restore them if necessary.
Start with .cache
mv .cache olddot
and see if that fixes things.
If not , do .config, .compiz .gnome .gnome2, gnome2-private
Still no fix, move them all, so you start just like the guest session does. 		" 

I have looked many hours for a solution. your tip has worked. :=)

gtx fred
[/INDENT]

---

### Post by elasys63 on 2016-10-05
I have this exact problem. One day i shutdown and then when i booted up, the launcher and window frames are now missing. The strange thing is, when i created a new account, the problem didn't appear in the new account but stayed in the old account. I tried restarting Unity through the terminal and also debugged and found that the debugger hanged on the panel switcher component.

---

