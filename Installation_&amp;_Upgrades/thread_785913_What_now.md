---
title: "What now?"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by tori on 2008-05-07
I'm sure this question has been asked before, but I didn't know how to search for it.

I'm almost done with the installation process, my username on Ubuntu is "tori." So it asks for my username and pass, which I entered, and it took fine. 

Now it says "tori@tori:~s"

Cursor.

What do I do?

---

### Post by Pumalite on 2008-05-07
You must have installed the Server Edition. If you want a GUI:
sudo apt-get install ubuntu-desktop

---

### Post by NightwishFan on 2008-05-07
What method did you use to install? If you have a graphical enviroment try:
```
startx
```
or
```
sudo startx
```

!!! first do:
```
 sudo apt-get update
```
!!!

If no gui install xorg and a wm or a de.
```
sudo apt-get install ubuntu-desktop
```
or replace with kubuntu xubuntu kde-core etc, if you want wm, try:
```
sudo apt-get install xorg fluxbox
```
replace fluxbox with something like icewm or jwm if you so choose.

---

### Post by tori on 2008-05-07
"startx = "this program is currently not installed" or some crap like that. 

"sudo startx = "(sudo) startx tori password"
I enter my password. 
"command not found."

What the **** is this??

---

### Post by NightwishFan on 2008-05-07
You installed with cli system then correct? You do not have a gui yet, I will help walk you through. Do you want Ubuntu? or what?

---

### Post by tori on 2008-05-07
Here's the problem - my XP server is gone gone gone. I tried to do some bit of trickery with BartPE and now that's the only thing that will load. Is it possible to access the graphical interface with this thing loaded on my computer? and how? 


I'm using ubuntu because XP died and I don't have the disk, and I have no i386 files. If that's what you're asking.

I'm trying all of these codes but nothing is working..... unable to blah blah..... nos such command....

I just put the CD in with my BIOS changed to "start with CD." Know what I mean?

---

### Post by Pumalite on 2008-05-07
Just run my command. If you have already finished your installation of a Server and you want a Desktop.

---

### Post by tori on 2008-05-07
I installed the desktop version. Pumalite - your command gets "couldn't find package."

---

### Post by NightwishFan on 2008-05-07
```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

Perhaps you have no network connected.

(very sorry for my overwhelming mess of commands, perhaps i should have asked more than just post the whole shebang ;])

---

### Post by Pumalite on 2008-05-07
Boot your Live CD and post from the Terminal:
sudo fdisk -l

---

### Post by tori on 2008-05-07
you're right - I don't have a network. When it asked me to manually install my network (because it couldn't find mine) I opted not to. Because as far as I know I don't have one....

I SWEAR I have the desktop version......

those new commands get "unable to lock." 

I don't know what a terminal is.

---

### Post by NightwishFan on 2008-05-07
You need a network that is the way you connect to the internet. It does not nessecarily mean a "local" network. I am not sure how to configure from CLI although I am sure someone else can help. Then just run the commands puma gave.

---

### Post by Pumalite on 2008-05-07
Better reinstall wired to the Internet. Configure your wireless later.

---

### Post by tori on 2008-05-07
so I need to be troubleshooting my network setup. For some reason it couldn't recognize it, started asking all sorts of questions like my DHCP hostname, domain name, etc....Stuff I can't figure out, since I didn't set up the wireless router.


Thanks for being so patient guys, keep it coming...

---

### Post by Pumalite on 2008-05-07
Connect to the Internet through a router that provides you DHCP upon boot with a dynamic IP.

---

### Post by tori on 2008-05-07
I can't buy a new router...

---

### Post by Pumalite on 2008-05-07
How are you connectingf to the Internet.

---

### Post by tori on 2008-05-07
What do you mean? I have wireless going to a router that was set up by the people that live in this house. Not by me. But I asked them about all this DHCP nonsense and they said they had no idea.

---

### Post by Pumalite on 2008-05-07
I doubt that you are gfoing to be able to configure your wireless card during the installation. Find a place where you can be wired to the Internet.

---

### Post by fixitdude on 2008-05-07
What happens when you boot the live CD (meaning boot the ubuntu installer CD), there are graphical menus that will allow you to set up a wireless connection, if your wireless card (or whatever you have) is supported that is.

The reason I ask (and I am trying to be very, very basic here) is to see if this version of ubuntu supports your wireless setup easily.

If not, then you need to try to get directly wired using a ethernet cable directly to the back of your router (as Pumalite has suggested). Directly wiring to a network makes things a lot easier while you try to do an install. You should be able to set up your wireless later on with better drivers etc...

It's nice you are choosing Ubuntu, you will learn a lot and be very happy you did in the long run.

EDIT: You should have a graphical interface (GUI) after you boot the CD and also after you do a full install. If not you may not have the correct install CD, you are looking for the "alternate" install CD as your best choice.

[http://ubuntu-releases.wallawalla.edu/hardy/ubuntu-8.04-alternate-i386.iso](http://ubuntu-releases.wallawalla.edu/hardy/ubuntu-8.04-alternate-i386.iso)

But the desktop one should be OK for newer machines:

[http://ubuntu-releases.wallawalla.edu/hardy/ubuntu-8.04-server-i386.iso](http://ubuntu-releases.wallawalla.edu/hardy/ubuntu-8.04-server-i386.iso)

And like Pumalite said, it may be a bit of a pain to get your wireless working from a command line (or terminal - means the same thing, where you type in commands, just like the old days).

You could see what:

ifconfig -a

Says, looking for a "wlan0" to see if your card is there.

And try:

wl status

Just to see what it says about you being on the wireless network.

Having fun yet?

And if I remember right, it was:

wl scan

(then wait a bit)

wl scanresults

(and it shows you a list of all the wireless stations in range, pick yours)

wl join (enter your network name here and wait a bit)

It's been a while, but you can do a wl status again to see if it worked, then try:

ping yahoo.com

To see if it worked.

In case you are still reading this far down and want to learn, DHCP is where your computer asks the router information like IP address and network info so you don't have to enter all that information in yourself.

There's lots of info on the net about this stuff, but really you should be in a graphical environment where there are GUI tools for this sort of stuff.

---

