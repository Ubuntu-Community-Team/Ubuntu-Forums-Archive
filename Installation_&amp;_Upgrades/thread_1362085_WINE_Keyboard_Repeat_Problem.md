---
title: "WINE Keyboard Repeat Problem"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by JM-STIX on 2009-12-22
First off, I'm new.

I am another computer guy that is trying to use WINE on Ubuntu.  Even though I have been researching how to fix the keyboard repeat problem I still don't know what to do.

I did find this [**Problem with 9.04, keyboard key repeat, Wine and City of Heroes.**]("http://ubuntuforums.org/showthread.php?t=1146254")

The auto22.txt file provided by Joe222 caught my attention and I don't even know how to use it.  I am asking for help on how to use the file to fix my problem or for any other ways to fix my problem.

Thank You,
JM-STIX

---

### Post by JM-STIX on 2009-12-22
Rise Thread

---

### Post by JM-STIX on 2009-12-23
I managed to find another way to fix my problem.

I discovereda difference between Windows and Linux.  When holding a key down, Windows sends a single keydown event and Linux sends constant streams of keydown events/

I fixed the problem by typing the flowing in the Terminal:

```
xset r off
```The first time I typed it in the Terminal there were constant streams of the [Enter] key being pressed, I assume.  I then closed the Terminal and typed the code in again without the error.

To fix the problem with this code, it takes either one or two tries.

---

### Post by concertedrxn on 2009-12-26
I've seen the same strange behavior of the phantom repeating enter key when turning off the key repeat behavior.  The xset command does it just about every time in Jaunty.  However, the following is supposed to be the command line equivalent to unchecking "Key presses repeat when key is held down" in System->Preferences->Keyboard (a.k.a. "Keyboard Preferences" or gnome-keyboard-properties).

```
gconftool -t bool -s /desktop/gnome/peripherals/keyboard/repeat false
```

(Replace "false" with "true" to turn key repeats back on.)

Under Jaunty, the gconftool command also occasionally caused the same phantom repeating enter key problem when evoked from a command line, but so far I haven't seen the problem when using it in a script.  However, under Karmic gconftool causes the phantom repeating enter key almost every time, including when called from a script.  So now I'm looking for another solution to the problem.

---

### Post by JM-STIX on 2009-12-26
That is interesting.  However, I am currently using Karmic right now.

That does provide me useful information for the future.

---

### Post by concertedrxn on 2009-12-26
Well, after a little more searching I found this: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/367136]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/367136")

A Gnome plugin is responsible for the repeating enter key problem, but you can disable it by doing the following before disabling keyboard autorepeat:

```
gconftool -t bool -s /apps/gnome_settings_daemon/plugins/a11y-keyboard/active false
```

I have found that issuing this command is all that's necessary to stop the repeating enter key problem.  You do not need to execute the command with sudo or restart your gdm session.

Of course, this is a workaround for a bug affecting a workaround.  The main problem, however, is being worked on.  You can read more about it here [http://bugs.winehq.org/show_bug.cgi?id=18296]("http://bugs.winehq.org/show_bug.cgi?id=18296") and here [http://bugs.freedesktop.org/show_bug.cgi?id=22515]("http://bugs.freedesktop.org/show_bug.cgi?id=22515").

---

### Post by JM-STIX on 2009-12-27
So this is for permanently disabling the keyboard autorepeat?

> **concertedrxn said:**
> Well, after a little more searching I found this: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/367136](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/367136)

A Gnome plugin is responsible for the repeating enter key problem, but you can disable it by doing the following before disabling keyboard autorepeat:

```
gconftool -t bool -s /apps/gnome_settings_daemon/plugins/a11y-keyboard/active false
```I have found that issuing this command is all that's necessary to stop the repeating enter key problem.  You do not need to execute the command with sudo or restart your gdm session.

Of course, this is a workaround for a bug affecting a workaround.  The main problem, however, is being worked on.  You can read more about it here [http://bugs.winehq.org/show_bug.cgi?id=18296](http://bugs.winehq.org/show_bug.cgi?id=18296) and here [http://bugs.freedesktop.org/show_bug.cgi?id=22515](http://bugs.freedesktop.org/show_bug.cgi?id=22515).

---

### Post by concertedrxn on 2009-12-28
Well, if you want to permanently disable auto key repeat, you don't have to go to the command line to do so.  Just use System->Preferences->Keyboard and un-check "Key presses repeat when key is held down" on the General tab.  Key repeat will stay off until you decide you want it back and re-check the option.  I only used the commands to write a script to automatically disable key repeat (and compiz 3D desktop effects) and launch a Windows game in Wine.  When the game is finished the script turns the key repeat back on again (along with compiz).  

My only problem was with the enter key repeating when turning off the key repeat function from the command line or from within a script.  The command I shared above works around that problem by turning off the plugin that apparently causes the repeating-enter-key bug.  I also use that command again replacing "false" with "true" just to set things back to default after the game is done.  You can leave it set to false if you don't need the [a11y-keyboard]("http://www.linuxfoundation.org/collaborate/workgroups/accessibility") plugin's functionality, though.

---

### Post by JM-STIX on 2009-12-28
Alright.  Thank you for this information.

---

### Post by purplerhino on 2010-01-04
> **concertedrxn said:**
>   I only used the commands to write a script to automatically disable key repeat (and compiz 3D desktop effects) and launch a Windows game in Wine.  When the game is finished the script turns the key repeat back on again (along with compiz).  


I was just thinking about writing a script that does that.  Would you be so kind to post yours and save me the effort?  :D

---

### Post by osarusan on 2010-01-14
I was having problems in wine too -- keyboard repeating was causing games to run really slow when using the keyboard to move around. Simply disabling keyboard repeat in the gnome keyboard preferences solved the problem. The a11y-keyboard trick also works for me. Both of them are less-than-ideal, though, as they disable keyboard repeating in all apps... It's certainly a useful feature to have when typing.

It's a big nuisance to have to constantly turn repeating keys off and on every time I want to play a game or type. Hopefully this bug will get fixed soon...

---

### Post by T.J. on 2010-04-02
> 
It's a big nuisance to have to constantly turn repeating keys off and on every time I want to play a game or type. Hopefully this bug will get fixed soon...

As far as I know, this is a longstanding problem that has lasted for years.  I could be wrong in my assessment, but the Gnome settings daemon appears to ignore the state of the keyboard as set by X11, and re-enables repeat even if it has been explicitly disabled by X11. This is not a problem under KDE or any other Unix desktop that I know of, so it is specifically a Gnome bug.  In my opinion, don't count on the Gnome Project fixing it upstream anytime soon.  

I've ran across it before with older versions of Gnome. It's literally been in there for years, so I'm sure they know about it.  


I'd simply switch off keyboard repeat when you are using Wine, etc - or switch to another desktop. KDE is much more "Wine friendly" and compatible with non-Gnome apps, again in my opinion.

---

### Post by Endless_Nameless on 2010-11-19
I don't know if the problem is the same (it seems it is not), but my computer has a strange behaviour in 2 games, that I bought in the (fantastic great) HUmble Indie Bundle, Gish and Aquaria. 

I don't know if both use common libraries (probably) but I have one problem that make them unplayable: in both the movement is locked to the left and nothing can make it stop. The other games that use same keyboard settings for movement (Overture and Lugaru) are fine.

Just to clarify: Whe game begins, the character keeps wlaking to the left. Any other key that I try seems to try to work, but is stoped by the overwhelming left movement. It is no related to a specific key, as I tried to change settings.

I tried to found information in (Saint) Google for this specifics games, with o success. 

Anyone here had any idea what is happening? Thank you before hand.

Regards!

---

