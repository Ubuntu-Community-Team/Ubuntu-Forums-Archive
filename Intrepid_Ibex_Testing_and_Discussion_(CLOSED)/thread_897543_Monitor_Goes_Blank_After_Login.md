---
title: "Monitor Goes Blank After Login"
date: 2008-08-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by shafin on 2008-08-22
I just upgraded to alpha 4 from a perfectly running version of Hardy. From then on , I am unable to log on to my account, or any user account on my box. As soon as I log in, the monitor just turns off (i.e. there is no display so the monitor LED blinks, like in an idle state when the monitor is ON but the PC is not). And no input is accepted, ctrl-alt-bkspace does not work,alt-ctrl-del does'nt work,nothing. The only way to get out is the restart button on the CPU.

I am even unable to log into failsafe Gnome mode. Same thing happens. 

I've been able to log on to a terminal. trying to run metacity from there returns an error message concerning TCP/IP, DBus etc. Trying to run compiz --replace from there results in a hard restart of GDM and takes me to the login screen again.

Please tell me how I can get out of this mess. now I'm writing from Win XP and I desperately want to go back to land of freedom as early as possible.

I have Intel GMA950 graphics. And another big problem is I dont have any CD/DVD-ROM in that box,so any liveCD based solution wont work.

Thanks in advance.

---

### Post by LittleKoy on 2008-08-22
I have a similar problem:

- If I login using a normal session, since last update it tells me that GNOME Power Management is not installed correctly, then it appears the Wicd window asking for my root password, but it always tells me it's wrong. At the 3rd try, it disappear and leave me with the light-brown screen, and nothing happens

- If I use failsafe GNOME, it tells that it couldn't connect to session bus, and goes back to the login screen

---

### Post by Herman on 2008-08-22
:) I'm running Intrepid Ibex in an AMD64 computer and it was getting a glimpse of the gnome desktop for a second or so after login, but then it changes to a blank white screen with the mousse pointer in the middle.

The workaround for me was to press 'Ctrl'+'Alt'+'F1' to switch to a tty, login with my username and password, and install the icewm destop,
```
sudo apt-get install icewm
```Now I have rebooted, and before logging  in I clicked 'Options', Down in the left-hand corner of the login screen), and 'select session', IceWM Desktop'.

The IceWm desktop is very nice, I like it, and it will do what I need for the time being until developers have time to fix whatever's wrong and an update fixes my Gnome problem.

Mine was working fine until I installed a new ATI Radeon Sapphire HD 2400 Pro Video card. I'm  not sure if that has anything to do with the problem or if it's just a co-incidence that Gnome went out at the same time.
Hardy Heron loves the new video card, it fixed problems I was having watching videos with Movie Player.
I tried re-installing Intrepid Ibex Alpha3 and Gnome worked again until I updated my system, so I expect some future updates will probably clear the problem. Until then I'm happy with IceWm. :)

Maybe XFCE would be nice too.
```
sudo apt-get install xubuntu-desktop
``` I haven't tested it yet at the time of posting, but I expect XFCE will work also, (I hope).

UPDATE: XFCE desktop works even better than IcwMW, it seems as if the problem I have at the moment is  only with Gnome desktop.

UPDATE 2: Now my Gnome desktop is working again. :)

---

### Post by adult swim on 2008-08-22
i think this is an issue with the splash screen at startup.  from the grub menu, remove splash from the kernel you are booting and it should work.

---

### Post by Gina on 2008-08-23
I think it must be graphics related.  I have Intredpid booting fine on my present 4 machines except the splash doesn't work on some and I've removed splash to get the text logon.  This reports several errors as it zooms up the screen but this is not uncommon - I get some errors reported in Hardy but things seem to work.

I'm in the process of sorting out hardware bits for an even older desktop - an AMD K6-2 with 128MB RAM and either/both a 10GB and/or 8.6GB HD(s) depending on what works.  I seem to be having drive problems - both HD and CDROM/RW.  I have had that machine running Ubuntu in the past.

---

### Post by shafin on 2008-08-23
I tried the instructions in this page:
[https://help.ubuntu.com/community/DebuggingXAutoconfiguration](https://help.ubuntu.com/community/DebuggingXAutoconfiguration)

And somehow I ended up reconfiguring Xorg. then setting the driver to Vesa ended my problems. I now have a monitor with only 800x600 resolution but I think I can notch it up fairly easily.

Thanks for the effort.

Oh, And to Herman, I've installed IceWM, Nice lil thing :)

---

### Post by shafin on 2008-08-23
One little caveat, compiz wont run,when I tried compiz --replace &, GDM hard restarted. It gets more interesting because when I was having the problem, I removed compiz, the problem persisted. Now that I got over it, I reinstalled compiz. I'm really confused about compiz's role in the whole fiasco. 

So now I'm running without compiz. Please help to get compiz up and running.

Thanks

---

### Post by Stunts on 2008-08-23
Hi!
I'm testing Intrepid on a Gericom Laptop (P4@2.8Ghz, 740Mb RAM, Intel 845 chipset).
The live CD didn't do a normal boot. It would start X, play the login sound, display a black screen and that was it. I could still move my mouse, but that was it. I couldn't revert to tty1 either.
I installed using the install option. That one did work.
Now that it's install I can't boot into it. My screen gets turned off a while after starting X. I get the brown screen, no login sound and then it freezes in the same brown screen. I can still move my mouse, but can't revert to a tty.
Using the recovery mode, I can get into a root shell.
Typing "startx" will turn off my screen and freeze.
Typing "/etc/init.d/gdm start" will freeze at the brown screen.
I hope this gets solved. I think it might have to do with my graphics chipset. How can I revert to a VESA driver to test it?
Anyway, I'm going to try Kubuntu this time around. I'll report back with results when it's done. (still downloading)

---

### Post by Herman on 2008-08-23
:) I really don't know how mine was fixed, just luck I guess, I don't know if installing the other two desktops had anything to do with it or not. Clearly though, in my case it was not an Xserver problem, but probably some problem with Gnome desktop. At least it would seem that way. Maybe an update fixed it, I'm not sure, but mine's working fine. :)

I don't know very much about Xservers myself. 
The excellent link shafin provided seems worth studying, [DebuggingXAutoconfiguration]("https://help.ubuntu.com/community/DebuggingXAutoconfiguration") - Ubuntu Community Docs.

I have three more links that might also help someone, [Xorg in Ubuntu 8.04]("https://help.ubuntu.com/community/XORGHardy") - Ubuntu Community Docs[B]
[/B]
[Video]("https://help.ubuntu.com/community/Video") - Ubuntu Community Docs
[B]
[/B][How do i manually configure xorg.conf ?]("http://ubuntuforums.org/showthread.php?t=788765") - Ubuntu Web Forums
> i think this is an issue with the splash screen at startup. from the grub menu, remove splash from the kernel you are booting and it should work.
@ adult swim, thanks, that might help someone, mine was already fixed before I saw your post, but thanks for trying. :)

---

### Post by Stunts on 2008-08-23
Kubuntu 8.10 works...
I guess it's a gnome issue.
I'll look deeper into it after I get some sleep.
Thanks for your reply, btw.

---

### Post by Nullack on 2008-08-24
What bugs have you raise on these issues? What duplicates currently exist?

Do you have a list of issues you encounted?

---

### Post by shafin on 2008-08-24
So on Short,here is how I solved the problem:
On the Login screen, I pressed ctrl-alt-f1 to enter terminal,once there I issued sudo invoke-rc.d gdm stop to stop GDM and then  sudo nano /etc/X11/xorg.conf command. Then in the xorg.conf file , I added HorizSync 32 and VertRefresh 60 on two different lines under section monitor. Then I typed sudo invoke-rc.d gdm start to start GDm and then ctrl-alt bkspace to get to GDM. I was given the Xorg configuration dialog and chose Vesa driver. When I logged on,there was no problems but the resolution was 800x600. So I opened terminal and typed sudo displayconfig-gtk to configure the resolution.

This is as much for me as for you.:)

---

### Post by brickheadbs on 2008-09-28
There is a wide variety of similar issues in this thread...

Fresh install of 8.10 Alpha 6 AMD-64.  1st boot I looked for the ATI drivers to be offered like in Hardy... but says no driver is available.

When I changed my screen resolution to 1280x1024 @ 75hz (standard for me) I get Over Frequency warning on my display.

If I Ctrl+Alt+Backspace I go to the log in screen, Ctrl+Alt+F1 does nothing.

I rebooted into recovery mode and slected log into root.  Tryed the usual:
   sudo gedit /etc/X11/xorg.conf
Got the message (gedit:4643)  GTK-Warning **Cannot open Display**

Found no way to fix my config...

I reinstalled, tried 1024x768 @ 60hz, same thing.  Can get to the log in screen, but all the fonts are tiny.

Bug?

---

### Post by sdowney717 on 2008-09-28
actually I got a new ati x1300 pro card and tried it in hardy. All I could ever get was a white screen. So I upgraded to Ibex.
Took a lot of work, but it is running compiz on the free radeon driver.

It was trial and error all the way. System had mixed up drivers from Nvidia, radeon free and fglrx.

[http://ubuntuforums.org/showthread.php?t=930038](http://ubuntuforums.org/showthread.php?t=930038) was my thread and how it finally worked out.

I can say I was happy to get it finally working.
I never could get it to work under hardy with that video card.

FGLRX wont work with xorg 7.4 in Ibex or xserver 1.5 so you must use the free driver for now.

---

### Post by brickheadbs on 2008-09-28
Developers!  If you're listening: Work on display/driver problems!

If it wasn't for all of these, I think Ubuntu would take off.  I had trouble with my nVidia 6600GT, now I have integrated ATI graphics that work OK in Heron... problems in Ibex.

---

### Post by Greyed on 2008-09-28
> **brickheadbs said:**
> Developers!  If you're listening: Work on display/driver problems!

Tell that to the right people!  Tell that to nVidia/ATI, not Canonical!

---

