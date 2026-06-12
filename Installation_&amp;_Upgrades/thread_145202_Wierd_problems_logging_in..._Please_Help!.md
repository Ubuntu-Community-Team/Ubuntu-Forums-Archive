---
title: "Wierd problems logging in... Please Help!"
date: 2006-03-15
forum: Installation &amp; Upgrades
---

### Post by alcapwn on 2006-03-15
Hello,

I just recently decided to try linux for the first time and I heard that ubuntu was a good distro to begin with so I went ahead and downloaded the iso and burnt it to cd.  The installation went along fine except that I use a wireless network and my card did not show up the primary network devices.  Is this a problem?  I just told ubuntu to continue without the automatic DHCP setup.

On to the real problem.  The rest of the installation went on without a hitch and the glorious ubuntu login screen comes.  I go to log in and it goes to the gnome deskotp but all that is there is a brown background and distorted strip of pixels int he middle of the screen.  I have no idea what is wrong but I was thinking it would have something to do my graphics card.  The ubuntu live cd does the same thing everytime.

I am dual booting on the same hdd as windows xp professional and installing 

My system specs-
AMD dual core 3500 64 bit
ASUS a8n mb
2gb ram
evga 7800gt

Thanks a lot!
Josh

---

### Post by aggiechemist on 2006-03-15
I have never seen this, but I think one guess might be changing some monitor settings. I'm curious whether or not changing thre resolution or refresh rate fixes /changes the problem (try System -> Preferences -> Screen Resolution). 

If that does no good, list your video card and someone might be able to help.

I assume nothing like this has ever happened in Windows, right?

---

### Post by alcapwn on 2006-03-15
Yea nothing like this ever happened in windows.  As soon as I log into ubuntu this happens and I can do nothing.

I have a nVidia geforce 7800gt by eVGA.  I just recently purchased a samsung 930b lcd that is still hooked up in analog until I can get my new dvi cables.  Could that have something to do with it?

---

### Post by klahjn on 2006-03-15
There really shouldn't be a problem.  Few questions though. 
**First**, are you using the 32bit (x86) or the 64bit?  Athlon 64 X2 should use the 64-bit, but it still has x86 nativity so you should be able to run both.

**Second**, what speed did you burn the disc on?  It sounds dumb, but i've had problems where the disc was burned too fast and have had some problems with it booting or installing because of it.  

Any further information would definitely be helpful.  Also, if you are having problems with the live disc, the install disc will probably also give you the same problems.  I don't see any problems with the hardware you have, but you may just have the one configuration that they haven't accounted for.  Has anyone else had any success with the Athlon 64 X2?

---

### Post by alcapwn on 2006-03-16
Yea, I am trying to use the 64 bit version of the OS.  I have tried to separate CDs.  One was mailed to me by shipit, the official cd, the other i downloaded and burnt at 20x.  Both the factory live cd and the install from the factory install cd had the same problem.  The one I burnt does the same thing.

I have the athlon dual core 3500 64bit proc.

During the installation, when I pick the resolution for Xserver what should I pick?  I just picked the native resolution of my monitor.

---

### Post by aggiechemist on 2006-03-16
I would say the native resolution should work, so this is thoroughly odd. You should be able to change it with the prefernces menu (system -> preferences -> screen resolution), as well as the refresh rate. I don't think you'll need to go into the Xorg.conf to do it.

---

### Post by alcapwn on 2006-03-16
> You should be able to change it with the prefernces menu (system -> preferences -> screen resolution), as well as the refresh rate. I don't think you'll need to go into the Xorg.conf to do it.

Do you mean in ubuntu?  I cant do anything in the OS, as soon as I log in this occurs.  I just got my dvi cables for my monitor and it still happened so that wasnt the problem.

Any more ideas?

---

### Post by alcapwn on 2006-03-17
bump

---

### Post by aggiechemist on 2006-03-17
Oh, sorry. I thought you had the panel at the top. Let me see if I can walk you through trying something different using the terminal:

Press Ctrl+Alt+F1 to get to the terminal screen and then log in there. Hopefully that display will look fine.

You can always press CtrlAltF7 to get back to the GUI.

Once there, type

cd /etc/X11

I tend to back up the good copy of things by typing something like 

sudo cp /etc/X11/xorg.conf /etc/X11/xork.bak

With it backed up, you can go edit the file:

sudo nano xorg.conf

and type your password.

Scroll down this file to the monitor section. You can use the arrows to go and change things around.

Try altering the numbers for resolution and bit depth and refresh rate. Make sure that is leans toward the native numbers first, but then maybe try other stuff. Press ctrl+X to exit and save.

Then just go back to the GUI (ctrl alt f7) and restart it (ctrl alt bkspc). With any luck, things should have changed. 

To go back and put the backed up file back in, it should jsut be

sudo cp /etc/X11/xorg.bak /etc/X11/xorg.conf


Good luck, hope this helps.

---

