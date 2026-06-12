---
title: "numlock key not on"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by inigmatus on 2007-04-22
I have just installed a fresh vanilla 7.04 Feisty Fawn and my first task:

to get the numlock key to be automatically turned on.

I followed [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_turn_on_Num_Lock_on_GNOME_startup](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_turn_on_Num_Lock_on_GNOME_startup)

and it didn't work:

The numlock key is on during boot, during GRUB, and turns off when Ubuntu is loading to the login prompt. However at the Ubuntu login prompt the numlock light turns on again, but when I hit enter to login, the numlock light turns off, and stays off. I have to manually turn it back on again - and its getting annoying.

I have a Gateway SK-9920 keyboard which has multimedia and internet keys on the top.


-------EDIT: Solution Found----------

I didn't have to do any of that fancy stuff on that link.

In fact, it's so simple, I fixed it and tested it myself so you too can do it.

I just did a brand new install of 7.04, and all one needs to do is this:

Since the universe repositories are already enabled, all one needs to do is:

> sudo aptitude install numlockx

This will install the numlockx program for use. Next you need to run the program, so type in terminal

> numlockx

and your numlock light should go on. All that remains is to have that program called every time Gnome starts up.

Simply go to System>Preferences>Sessions

and then click "New"

and in the dialog box that pops up enter in the following fields:

Name: Num Lock
Command: numlockx

then hit "Ok" and then "Close"

That's all there is to it! numlockx should run automatically at startup now and turn on your numlock and your light.

To test it out, simply hit Ctrl+Alt+Backspace to restart, or simply just restart your comp.

---

