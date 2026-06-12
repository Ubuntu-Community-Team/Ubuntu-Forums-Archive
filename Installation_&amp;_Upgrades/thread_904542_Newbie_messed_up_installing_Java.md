---
title: "Newbie messed up installing Java"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by JCS05Rubi on 2008-08-29
First of all, I am on Ubuntu Hardy from the box, on a newer HP CTO DV6000.

I have a problem, that hopefully one of you can fix.  I am a total newbie to linux, although I have managed to install a few things on my own looking through tutorials.  I was trying to get Aptana installed to make a website for my relatives all over the country to use.  Obviously, in order to get Aptana working I needed to get Java working.

I was following this tutorial ([http://jasonleveille.com/2008/05/installing-aptana-on-ubuntu-804/](http://jasonleveille.com/2008/05/installing-aptana-on-ubuntu-804/)) trying to get it working.

So, I did this in terminal:
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

and it did the install thing.  The terminal turned into a configuration screen for Java with an acceptance agreement that you would see in windows. I scrolled to the bottom, tried to click the OK thing, pressed enter, pressed "y" enter, nothing would happen.  Tried to press ESC and it would take me back to the terminal screen, than automatically pop the java agreement screen again.  I couldn't figure out how to accept the screen, so like an idiot, I just closed the terminal :(  Obviously Java did not finish installing.  If I type the same code in terminal again (sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts)  I get:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


:Sigh:  Is there any hope?  :)  Someone help a noob please ](*,)

---

### Post by kellemes on 2008-08-29
From a terminal window..
```
sudo dpkg --configure -a
```
After this do your install thing again..

Navigation in Java Configuration Screen (ncurses)..
Tab = Activate the next object (button, checkbox etc..).
Space = select or deselect a radio/checkbox
Enter = well.. enter.. (space may work too)

---

### Post by JCS05Rubi on 2008-08-30
I tried that myself when the error came up, thinking that was the logical solution but it didn't work. I must have miss typed something cause it worked this time, and the tips for the "config" screen worked great.  Thanks a lot.

---

### Post by nicolaary on 2008-08-30
to accept the agreement you should press q

---

### Post by nicolaary on 2008-08-30
```
sudo apt-get --reinstall install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

and than press q to confirm the agreement

---

