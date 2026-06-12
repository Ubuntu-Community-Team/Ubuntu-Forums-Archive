---
title: "How do I Install Runes of Avalon?"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by treeclimber on 2007-09-24
I am a newbie to Ubuntu.  I purchased a Dell laptop to learn all about it and have been very satisfied.  I taught myself how to install Realplayer and how to convert a .rpm file to a .deb file. but now I have a file I can't figure out how to install.  I downloaded Runes of Avalon demo and I can't figure out how to install it.  I don't know what type of file it is, first of all.  It ends with "install" and when I look at its properties, it just says it's an executable file.  I already knew that!  I have looked in all the usual places for a solution to this, but I can't find out how to install it.  All I find are other Ubuntu users who have installed it "easily" and really enjoy the game.  Can anybody help me?

---

### Post by LinuxGamer on 2007-09-24
Did you try double clicking it? :)

---

### Post by treeclimber on 2007-09-27
That was the first thing I did.  All that did is to try to open it as though it is a photo file with gThumb Image Viewer.  .  I tried right clicking it. That opened up Archive manager as a choice.  But that was a dead end.  It's suppose to be able to install using Synaptic Package Manager, but I Can't figure out how to use it.  Any help would be appreciated.

---

### Post by neowampyre on 2007-09-28
Be careful with an old games, like Rune, Rune of Avalon, etc.! I have  the full version of Rune, and I can't install it, becouse this old games written to an old kernel-version.
You have to read the README first in the package of the game, but I'm not sure, Rune of Avalon will run on your machine.
Use Google, there are solutions on the web, but I didn't try those yet.

---

### Post by neowampyre on 2007-09-28
I'll write the method of the installation:
I suspect, you have an .ISO file, right?
First, you have to mount it (like under Windows, in Virtual Daemon Manager) to somewhere on your machine.
Open the terminal, and type: sudo mount -o loop -t iso9660 Runeofavalon.iso/mnt/

Then type your password to execute the mounting.

I don't know, what is the correct name of your .iso file, maybe Runeofavalon.iso. if it's not, type the correct .iso name to the place of the file's name.
Now, you have a mounted image file in the /mnt/ library.
NOTE: if you want to unmount the file, type to the terminal: sudo umount /mnt/

I suspect, after that, you have a setup.sh file in the /mnt/ directory. Open the terminal again, and type: cd /mnt/
(cd means: change directory), so you are in the /mnt/ directory. Type: sudo sh setup.sh to run the setup.
Add your password, and the installer will run.

---

### Post by neowampyre on 2007-09-28
Omg, I was wrong, you haven't an .Iso.... :(

---

### Post by glynallinson on 2007-09-28
I have full version of Runes of Avalon, and noticed that double clicking didn't work.  
Try ticking the " Allow _e_xecuting file as program" option in properties of the file.

From Runes of Avalon Site -
Linux version has been tested on Ubuntu 7.04 and Debian. Works best with hardware accelerated OpenGL. May need gcc-3.3 libraries.

---

### Post by treeclimber on 2007-09-29
Well, I tried clicking the " Allow executing file as program" option under properties and it didn't do anything different.  I seem to have other games on here that run using OpenGL and they work fine.  I have done an online search looking for a solution.  I did that before I turned to the forum.  If anybody has been successful, let me know. Thanks!

---

### Post by mairapontes on 2007-10-02
I  had the same problem as you: my install archive did nothing when I clicked it...
Then I looked at its properties, and ticked the option that makes it run as an executable file, double-clicked the file and voilà! I'm playing runes of avalon :)
Good luck to you!

---

### Post by treeclimber on 2007-10-09
I already clicked on the run as executable file under properties and then double clicked it.  Nothing at all happens.  What program are you using to open the executable file with?  Thanks!

---

