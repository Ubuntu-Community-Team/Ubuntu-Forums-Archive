---
title: "new Karmic install - can't get into safe mode w/ nvidia 9600"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jeebustrain on 2009-10-25
I know I've done this before, but for the life of me I can't remember how to fix it. I tried rebuilding my OpenSUSE 11.1 desktop w/ the new RC build of Ubuntu Studio 9.10. I know from reading there are issues w/ the built-in Nvidia driver. I boot it up, it blows past grub and get the splash screen fine, but when it's supposed to go to the login, it just goes to a black screen (monitor still on). I've been trying to search like mad to figure out how I can force the grub menu to show up so I could pick safe mode (or some other terminal). I tried to SSH into the box from another machine, but apparently that isn't set up all the way yet. 

Is there a key combination that I could use upon bootup (like F8 for windows) that I could force up the grub menu? I've been rebooting over and over and trying different random things and I got it to show up once, but it didn't actually let me pick anything. 

This is terribly frustrating because this is completely out of the box and there were absolutely no configuration options like this in the installer. I also remember having this exact problem trying 9.04 and 8.10 but I don't remember what I did. I'm coming from the OpenSUSE side of things where there are a million different options like that.

---

### Post by pbrane on 2009-10-25
You can try going to one of the VTs (Ctrl+Alt+F1, for instance) and edit your /etc/X11/xorg.conf file as root.
Set your driver to vesa:

Section "Device"
	Identifier	"Configured Video Device"
	Driver  "vesa"
EndSection

then you can try (re)installing the nvidia driver.

---

### Post by jeebustrain on 2009-10-25
thanks. Actually I forgot to mention. That was actually one of the first things I tried, along with ctrl+alt+backspace to see if I could kill X. It just sits there and nothing happens no matter what key combination I try.

---

### Post by jeebustrain on 2009-10-25
bump?

---

### Post by jeebustrain on 2009-10-25
ok, so I managed to get in using the install DVD, choosing "rescue a broken system" and choosing to mount my main partition. 

Now I'm in the filesystem and I went into /boot/ and it's completely empty. What I'd like to do is edit the grub menu so it will boot cli (runlevel 3?) or get into safe mode. Is the timeout value in the grub config? I don't think I'm going to be able to actually fix the nvidia driver from where I am now

---

### Post by jeebustrain on 2009-10-25
I just took a look in /etc/X11 and there's no xorg.conf in there.

---

### Post by jeebustrain on 2009-10-26
no ideas? This always seems to happen whenever I try to build an Ubuntu machine w/ an Nvidia GPU. It's part of the reason I keep going back to OpenSUSE because at least then I am able to get in to fix it manually.

---

### Post by jeebustrain on 2009-10-27
I tried installing regular Ubuntu Karmic and managed to get to the grub menu by holding down both shift keys. Unfortunately though, the whole thing would freeze up whenever I even tried to move the arrow key to tell it what I wanted to do (on the menu right after grub).

I ended up fixing the problem by reinstalling Ubuntu Studio after I managed to find the "command line only" option on the setup page. It put basically just the kernel and some core device drivers on disk. After the install I had to manually install X, gnome, the nvidia drivers, and everything else via CLI, but at least the stupid thing worked after that. 

Does everyone have these sorts of Nvidia probs? Or is it just me?

---

