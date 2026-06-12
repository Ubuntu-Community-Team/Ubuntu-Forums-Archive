---
title: "My experience: Kubuntu 8.04/KDE4 on an IBM Thinkpad X41"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by Jonathan Harford on 2008-06-22
My Thinkpad has no CD drive, so I google some black magic to make my USB stick resemble a Kubuntu 8.04 / KDE4 install CD.

The partitioner is very confusing. Trying to shrink the Windows partition results in an error (OH MY GOD THANK GOD THE MACHINE WAS STILL BOOTABLE AFTERWARDS). I decide just to wipe the Windows partition but leave the Windows Recovery partition Just In Case. Installation is a breeze.

I chose the name "Spielford" when I installed. At the login screen, I type in "Spielford", then enter the password I had chosen. Doesn't let me in. I try again, making especially sure I'm getting the password right. No dice. Am I going to have to reinstall just to change my password? Finally, I click "Spielford" on the menu on the left side of the window. My username changes to "spielford", and my password works. If Kubuntu is going to change all usernames to lower case internally, it needs to let users know!

Wireless works with no futzing! My eyes tear up with joy. But KNetworkManager has a habit of stealing focus for a password when I'm typing.

In order to tweak my initial setup, I want to edit GRUB's menu.lst and my xorg.conf file. On the command-line, I try "sudo kate /etc/X11/xorg.conf", but get "sudo: kate: command not found". Huh? "kate" on its own works (though it spits error messages to the console during the 5 seconds it takes to boot). I realize that this is a "path variable" issue... and since I don't know how to find out where kate lives, I'm stuck. (I eventually learn both where kate resides and about "nano".) Is there a KDE-approved way of editing config files?

Is there a good lightweight (but GUI) text editor around? Along the lines of Windows' metapad?

I successfully get the tablet to work (though it does take some effort), and ArtRage runs on WINE beautifully, once I find gdiplus.dll floating on the internet. This makes me so happy.

I set the bottom panel to "Tiny". The bottom few pixels of the panel get cut off, appearing at the top of my screen. This is almost ignorable, except the K menu now comes down from the top.

I download a zip file to my desktop. I'm used to 7-zip on my Windows system, so when I right-click it, I hope that there'll be an option to extract it to the directory it's in (the Desktop). No dice. So, okay, I click it and Ark pops up. There are two files inside, and I'm only interested in one of them, so I click drag it to the desktop. It doesn't work. I open up Dolphin, and try to click and drag my file into my home directory. Also doesn't work -- I have to use the "Extract" button in Ark, I guess. I extract my file to the desktop, then try dragging it into an open directory in Dolphin. Nothing happens! Eventually I open the Desktop directory in Dolphin to access the file. Lesson learned: don't use the Desktop for anything but application launchers and widgets.

Now I want to delete the zip file from my Desktop. I right-click, but there's no "Delete" or "Send to Trash". "Remove this Icon"? I give it a shot. Later, in Dolphin, I find it still in my "Desktop" directory.

I use Add/Remove Programs to install gimp, firefox, and Kubuntu Restricted Extras. Every time I tick a box to install a package, Adept stops responding for four seconds (but does not let me know). So I'll tick a box, think it hasn't ticked, and tick it a few more times. This results in twenty seconds of watching the tickmark appear and disappear.

Can I hide some of these fonts? I like that I can see webpages in Farsi, but I am never going to format any text I type in "Haramain" or "Sindbad".

Now that I've got ArtRage running, I'd like to add it to my KMenu. I go into Applications > Graphics and right-click, hoping for an "Add Shortcut" or something. No menu pops up. Well, I'll put a shortcut on the Desktop -- then maybe I can drag it into the K menu. I right-click the desktop. I can... add a widget? I guess that's what I want? And one of the widgets is "Icon". Okay, I'm getting somewhere. I take a look at its properties. The only thing it looks like I can do with it is change its name, not what program it points to.

Oh, now my K menu has a "Lost & Found" menu, with a bunch of Wine files, including a link to ArtRage that I find I can put on the Desktop and in my favorites menu. I can't seem to put ArtRage in the "Graphics" menu... or do anything else with the items in the Lost & Found menu, though. How do I edit my K menu?

---

