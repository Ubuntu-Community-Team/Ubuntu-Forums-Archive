---
title: "Ctrl-A closes synaptic???"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Vermind on 2008-10-30
Hello,
On my Ubuntu 8.04 laptop, when I press Ctrl-A in order to select all in synaptic, the program exits. If I have changes not applied yet, it does ask me if I want to quit. Selecting all does not happen. It would seem that Ctrl-A does the same thing as Ctrl-Q for me in synaptic. This also happened in some other apps, such as the Hugin panorama creator (trying to select all images) This was on my 8.04 64-bit desktop machine.

This happens both under compiz and metacity, so I guess it is not a keyboard shortcut problem.

Any ideas?

---

### Post by roger_1960 on 2008-10-30
Hi

Sounds like you may have installed the wrong keyboard?  AZERTY instead of QWERTY??

But with 2nd thoughts , you would have noticed that..........

---

### Post by Vermind on 2008-10-30
Hi,
very funny.
Yeah, I might have noticed that :). 
I can type all letters normally.
If I use xev to record keyboard events, the keycodes of a and q differ, and the state + keycode when control is pressed with these keys also differ. Ctrl-a works as expected in firefox, gedit, and all other applications, EXCEPT synaptic.

xev | grep key:

When ctrl-a is pressed:
```
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    state 0x4, keycode 38 (keysym 0x61, a), same_screen YES,
    state 0x4, keycode 38 (keysym 0x61, a), same_screen YES,
```
And when ctrl-q is pressed:
```
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    state 0x4, keycode 24 (keysym 0x71, q), same_screen YES,
    state 0x4, keycode 24 (keysym 0x71, q), same_screen YES,
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
```

(The number of lines may differ, depending on how long you hold ctrl, a or q, and in which order you release the keys)

So, as all of the keys, control, a, and q, function as expected, I am wondering what can cause this... I didn't find anything about synaptic in gconf.
The issue occurs both in user-mode synaptic and sudo synaptic.

---

### Post by dodongo on 2008-11-23
I'm suffering from the same problem.  Could it be that this is just some very unusual / vestigial keybinding in the code?  Ctrl+A is a very standard shortcut for Select All, and may possibly be specified as a standard in some HIG document or another, for all I know.

Any interest in opening a Launchpad bug about this?  I've learned to work around it, but finding this thread reminds me that it's a very unexpected user experience to have this interaction.

---

### Post by Vermind on 2008-11-24
What is interesting is that on my 64-bit Intrepid desktop, Ctrl-A does not close synaptic. On my 32-bit Intrepid laptop, it does.

However, on a new user on the same laptop, synaptic does not misbehave. It would appear I have messed up my settings somehow. I wonder if it's under .gnome2 or .gconf or somewhere else...

---

### Post by dodongo on 2008-11-24
> **Vermind said:**
> What is interesting is that on my 64-bit Intrepid desktop, Ctrl-A does not close synaptic. On my 32-bit Intrepid laptop, it does.

However, on a new user on the same laptop, synaptic does not misbehave. It would appear I have messed up my settings somehow. I wonder if it's under .gnome2 or .gconf or somewhere else...

What a tangled web we weave, huh? :)  It's getting late here on the west coast of the US, but I will take a look at things tomorrow and see if I can't find more details.  Will reply here if I find anything.  I checked ~/.synaptic today and it was not helpful in the least.

---

### Post by Vermind on 2008-11-24
Yeah,
I deleted root's dotfiles and directories to see if that helps, but no, these shortcut "settings" come from my user somehow. While doing that I noticed .synaptic, and saw some colours and fonts and options there, but nothing related to keybindings.

Will try a move-away of .gnome2 and .gconf next.

Results:
it's under .gconf.
I did something like this:
```
mv .gconf .gconf-temp
# now logout and login again (see default ubuntu background and other settings)
# check that synaptic now works properly with Ctrl-A.
# if all is ok, let's try to restore our settings:
cd .gconf-temp; cp -r apps desktop GNOME system ../gconf/.
```
I had a file called %gconf-tree.xml which I left out of .gconf.
Some of my settings were lost, things such as gnome-power-manager preferences, fonts, theme selection. I am setting those again manually.

------

A few weeks later, I decided to make a new user and set the config manually, since i.e. SCIM didn't activate as per my xinput settings even though everything was set properly, logging out didnt happen until I logged out twice, and other assorted weird behaviour. Unfortunately, the new user seems to suffer from this synaptic issue ???, even though the gconf directory was auto-created for the user and I did not import my old settings. I find this weird...

---

### Post by Vermind on 2009-01-28
Hi, 
I have an easy solution finally, which all readers might not like:
I read this recently:
[Ctrl-Q selects all]("http://weblog.savanne.be/157-bizarro-bugs-ctrl-q-for-select-all") And I had French and Finnish keyboard defined on my laptop. Removing French keyboard makes Ctrl-A work properly. Even DEFINING an Azerty and Qwerty keyboard in Gnome keyboard preferences makes Ctrl-A and Ctrl-Q mess up in Gnome.

---

### Post by dodongo on 2009-01-28
> **Vermind said:**
> Hi, 
I have an easy solution finally, which all readers might not like:
I read this recently:
[Ctrl-Q selects all]("http://weblog.savanne.be/157-bizarro-bugs-ctrl-q-for-select-all") And I had French and Finnish keyboard defined on my laptop. Removing French keyboard makes Ctrl-A work properly. Even DEFINING an Azerty and Qwerty keyboard in Gnome keyboard preferences makes Ctrl-A and Ctrl-Q mess up in Gnome.

Mon Dieu ;)  Est-ce qu'il y a un bug pour Gnome?

(My God.   Is there a bug for Gnome?

(I think.  Never was very good at French.  But I do indeed have that layout active.))

Oh, indeed there is.  Thanks for posting :)

---

### Post by Vermind on 2009-01-28
I consider this "solved" now, since people know about the bug and my solution is to remove the layout; i dont use it so often.
Any idea why I cannot mark this thread solved? Any idea why I can't thank anyone lately?

---

### Post by Cope57 on 2009-01-28
_List of all global short cuts in Synaptic Package Manager:_
	

Reload the list of known packages		
Ctrl+R

Open the package search dialog
Ctrl+F
					
Open the properties dialog for the selected packag
Ctrl+O

Mark the selected package(s) for installation
Ctrl+I

Mark the selected package(s) for upgrade
Ctrl+U

Mark the selected package(s) for removal
Delete

Mark the selected package(s) for complete removal (Debian only)
Shift+Delete
					
Unmark any changes to the selected package(s)
Ctrl+N
					
Mark all possible upgrades
Ctrl+G
					
Force the installation of a specific version of the package
Ctrl+E
					
Undo the last status change to a package and to the therefor required dependencies
Ctrl+Z
					
Redo the last reverted status change to a package and to the therefor required dependencies
Shift+Ctrl+Z
					
Apply all marked changes
Ctrl+P
					
Quit Synaptic Package Manager
Ctrl+Q
					
Show the manual of Synaptic Package Manager
F1

Sorry, I just do not see how it closed it. Unless you changed the keybind settings, or the keyboard type is not correct in the System > Preferences > Keyboard > Keyboard Preferences > Keyboard model.

If all else fails, go to System > Preferences > Keyboard shortcuts and disable or reconfigure it.

---

### Post by Vermind on 2009-01-29
> Sorry, I just do not see how it closed it. Unless you changed the keybind settings, or the keyboard type is not correct in the System > Preferences > Keyboard > Keyboard Preferences > Keyboard model.

If all else fails, go to System > Preferences > Keyboard shortcuts and disable or reconfigure it. 

> 
DEFINING an Azerty and Qwerty keyboard in Gnome keyboard preferences makes Ctrl-A and Ctrl-Q mess up in Gnome.

If You want to try this bug out, follow these steps:
[LIST=1]
[*]Go to System > Preferences > Keyboard > Layouts
[*]Assuming Your default layout is US or some other QWERTY layout, add a French (The default is AZERTY) keyboard layout, but do not activate it.
[*]Go to Synaptic and try Ctrl-A and Ctrl-Q. Either Ctrl-A quits or Ctrl-Q selects all, depending on program & order of keyb layouts.
[/LIST]

This is mentioned here: [Ctrl-q for select all]("http://weblog.savanne.be/157-bizarro-bugs-ctrl-q-for-select-all") and is in gnome bugzilla as [Bug 162726]("http://bugzilla.gnome.org/show_bug.cgi?id=162726").

---

