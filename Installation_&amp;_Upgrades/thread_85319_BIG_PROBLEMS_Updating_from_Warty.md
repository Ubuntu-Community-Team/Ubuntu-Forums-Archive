---
title: "BIG PROBLEMS Updating from Warty"
date: 2005-11-02
forum: Installation &amp; Upgrades
---

### Post by ExemplarUbuntu on 2005-11-02
I've just been trying to update from Warty via Synaptic. All seemed to
go quite well and then the desktop crashed and I did a shutdown via
the root terminal window.

When re-booted, X11 fails to start leaving just a cli shell.

It seems that the file pointed to by /etc/X11 no longer exists.
I tried starting XFree86 but that reports font problems and exits,
suggesting I run apt-get.

How can I recover from this without wiping my system ?

This is the first time I have tried to update Ubuntu so I am less than
impressed.

---

### Post by ExemplarUbuntu on 2005-11-02
Quick update:

running XFree86 returns an error about a missing fixed font.

>startx

fails saying /etc/X11/X is not excutable
and then says the  network is unreachable errno 101

>apt-get -f install

reports 3 errors about Locale files being missing
and then fails trying to overwrite /etc/X11/xkb/rules/xfre86.xml
which I have renamed to attempt to get around the error but it
hasn't worked !

other apt-get command fail due to dependencies.

Is there way to get the Hoary update to rollback or install
properly ?

---

### Post by ExemplarUbuntu on 2005-11-02
More info, my help anyone else with the same problem.

After repeatedly running apt-get -f install and restarting the box it
finally started removing and then installing lots of packages.
I then had to do an apt-get udate.

startx still didn't work but the install of the xserver packages that it
recommended actually worked.

I then installed the font package that was mentioned in the log, this
had previously failed to install also.

After that, running startx opens a grey screen with mouse but nothing
else forcing me to reboot the hard way.

Some progress but not sure what to do next with a lack of any messages
or output.

---

### Post by ExemplarUbuntu on 2005-11-03
Sorry to keep answering my own thread but it does mean I am trying
to fix my problems.

I realised that X is starting but Gnome isn't. I found another thread that
suggested:

>sudo apt-get install gdm

This installed some more packages and when rebooted I was presented
with the graphical login screen. I thought it had worked but when I
logged in it just shows a brown screen with the mouse pointer.

So I tried:
>sudo apt-get --reinstall install gdm

and restarted.

Looking at the gdm log file it gives one FATAL error about a missing
kernel module "via".

I think I am getting near to fixing this but my vconsoles have stopped
working which is proving to be a nuisance.

Using the emergency cli from the Login screen I was able to reinstall
Nautilus and start it manually.

This opens a file manager and shows the desktop icons but there is no
menubar and no toolbar. Logging in again doesn't start the desktop
just the drab brown screen of death again.

Where should I look to find out what is going wrong ?

---

### Post by ExemplarUbuntu on 2005-11-03
Problem solved I hope. Vconsoles started working again which helped.

I noticed that the cli said it was running Warty but when I looked at
/etc/apt/source.list it referred to hoary in just one line.

I took a chance and commented that line and added two new ones that
pointed to hoary main restricted and hoary-updates main restricted.

Running apt-get -f install
this removed and installed lots of packages as did an update
Things like OpenOffice and loads more stuff that I don't need on this
box.

When I toggled across to the gui console the splash screen had appeared
and very slowly the various module icons appeared. The the splash vanished
and the brown screen appeared. It all ran very slowly but the white menu-
bars and then the icons appeared :-)

I am a bit worried about running synaptic or the new updater function
because I think the entries in sources.list probably aren't perfect.

What should they be for a simple hoary installation ?

---

### Post by Abd-al-Karim on 2005-11-03
[QUOTE=ExemplarUbuntu]
What should they be for a simple hoary installation ?[/QUOTE]

I'd like to know that too. BTW I have been having similar problems to those that you described (you can view my story [here](http://www.ubuntuforums.org/showthread.php?p=459214#post459214) if you like) seems like a lot of people have run into this. Someone filed a bug [here](https://bugzilla.ubuntu.com/show_bug.cgi?id=13264#add_comment) maybe you want to add your story there. I have been working hard to fix this and I see my only solution will be to force ronconfigure and install which will however remove a lot of packages so I don't wanna try that just yet I'm still looking for other solutions. I also found other threads on people with similar locale/X problems are myabe you can find some info there: 

[http://www.ubuntuforums.org/showthread.php?p=428872](http://www.ubuntuforums.org/showthread.php?p=428872)
[http://www.ubuntuforums.org/showthread.php?t=83315](http://www.ubuntuforums.org/showthread.php?t=83315) 
[http://www.ubuntuforums.org/showthread.php?t=84622](http://www.ubuntuforums.org/showthread.php?t=84622)
[http://www.ubuntuforums.org/showthread.php?t=67209](http://www.ubuntuforums.org/showthread.php?t=67209)

---

### Post by ExemplarUbuntu on 2005-11-04
I did a lot of searching for solution to this and somehow I didn't find your
thread.

I had nearly all the same errors as you, Locales, ntp but not the firewall.

When I was running apt-get install and update it did remove and
reinstall lots of packages. I get the feeling that the initial update didn't
successfully complete.

Also it seems that there is a change in X and Gnome versions.

Repeatedly running apt-get -f install and restarting the box eventually
got things moving in the right direction. Once X will start you can
ctrl-alt-F1 into the console and work on Gnome or Gnome2.

I think it may all just come down to which packages didn't get installed
when the initial update falls over leaving the system in limbo.

Peter

---

### Post by bursto22 on 2005-12-04
I agree after trying to update from warty Im having the same problem that seems to have rison from a poor initial update im now trying to trouble shoot it on a windows box through a putty shell

---

