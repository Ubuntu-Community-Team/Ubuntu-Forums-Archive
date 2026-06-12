---
title: "Can't install from 7.04 LiveCD - screen problem"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by MartynT on 2007-05-28
Hi 

I relatively new to Ubuntu but I have successfully installed 7.04 on one PC.  I'm now attempting to do the same on another.

The trouble is that during the install process ("What language ?", "What location ?" etc.) the dialog box is larger than my screen and so I am unable to see (and therefore click) the accept/OK buttons at the bottom of the dialog - they're below the bottom of the screen.

I've tried a few things.  Resizing the dialogs doesn't work.  The move edge/corner mouse pointer appears but the dialog doesn't resize.  Same deal via the top left menu.

I've tried changing the resolution of the screen, but my only options are 800x600 or 640x480 which is odd given the native resolution of my LCD is 1024x768.  It's as if the installer is aware of the screens capability and using that rather than the actual resolution being used.

Incidentally, there are several other screen drawing issues.  For example if I use 640x480 then the two menu bars (Apps, Places, System, etc.) appear at the top and bottom of the screen (as expected.)  But if I use 800x600 then the "top" of the screen (i.e. the Apps, Places, System menu bar) doesn't appear at the top of the monitor.  It's about 2 cms from the bottom, just below the bottom bar, separated my a black band.  These web pages also don't render properly, which is odd.

My system specs are 1G Athlon, 512M Ram, Voodoo 3, AOC  LM-500 LCD monitor.

Any trick of the trade suggestions on how I could convince my LiveCD to run in 1024x768, so that I can click the installers buttons :)

Thanks,
Martyn.

---

### Post by ugm6hr on 2007-05-28
Have you tried pressing tab to get to some of the buttons?  I think that works.  You should be able to sort the screen out after installation (hopefully).

Otherwise the Alternate CD should work.

I had a nightmare installing on my Dell Inspiron 5000e, where the 1400x1050 screen was running at 1024x768, but there were gaps in it, it seemed like it was mirrored in one vertical area, and the 3 separate vertical areas semmed to bleed into each other.  But I was able to move the dialog boxes around the screen so I could see what I was doing!  After installation, the screen was the same, but I edited /etc/X11/xorg.conf and sorted it out (by copying someone else's solution on this forum).

---

### Post by MartynT on 2007-05-28
I could try tabbing about, but that seems a bit random and will become annoying after the first few times that I've "pressed" the wrong thing.

I'll have a go with 6.06 and also have a poke round /etc/X11/xorg.conf and see if there's a MakeItWork=No option that I can change :p

I can't believe that the failure to resize is just a bug, rather than a display/driver issue.

If it is, where do I report it ?

I'll also put my 7.04 cy into my other (3rd) PC and see if the installer dialogs are resizable on that.

In the mean time, does anyone else have any suggestions ?

---

### Post by ugm6hr on 2007-05-28
It almost certainly is a display driver issue.  Essentially, Ubuntu believes your Graphics Card or Monitor can't support anything higher, so you have to tell it to.  Changing it is possible, I'm just not 100% certain you can do it with the LiveCD, *before installation*.  If you want to try, you can have a look at my edited xorg.conf for that Dell.

Look for my post here:
[http://ubuntuforums.org/showthread.php?t=447979&page=2](http://ubuntuforums.org/showthread.php?t=447979&page=2)

Essentially, all I did was add the resolution I wanted to the start of all the Section-Screen / Subsection-Display displays (so you would just add "1024x768" with the").  For that laptop, I had to edit the Section-Monitor refresh & sync ranges too (although I hope that won't be necessary for you).

After editing it, you have to restart the xserver, which I think requires you to log out and then back in.  But with the LiveCD, it may not work.  Sorry if it doesn't.  As I said, it may be easier for you to use the Alternate CD for installation.

---

### Post by Wherdgo on 2007-05-31
I had exactly this same resolution problem installing Feisty 7.04 from CD (downloaded/burned iso image), and at the same place (2nd install screen) as the other user above.

I had installed both Dapper and Edgy from download/iso/CD before without any problem, but something else has changed in this install, allowing me only 640x480 resolution.  This safe/default resolution usually isn't an issue at installation, as it's only temporary, but the first installation windows and buttons seem to have been created for a resolution beyond that "highly compatible" size.

Also, tabbing doesn't do crap, because the interactive location window demands that you click on something.
That means my installation off of CD is stuck at window #2, and I can proceed no further.  This can't be an isolated incident if the base installation windows were engineered at a non-resizable resolution larger than 640x480, which I'm guessing is their lowest common safe VGA resolution. 

Any ideas folks?

Spec for Toshiba Portege 7100 Laptop: PIII 500, 13.3" screeen, 128MB, 6GB HDD, Trident Cyber Blade e4-128 AGP on-board.

---

### Post by Wherdgo on 2007-05-31
Got a clue from another thread: [http://ubuntuforums.org/showthread.php?p=2755914#post2755914](http://ubuntuforums.org/showthread.php?p=2755914#post2755914)

I tried setting the resolution before install, no joy.  I tried installing in safe mode, no joy.

However the Alt-LMB (Alt key plus Left mouse button) trick did work for me, and allow me to move the dialog boxes around enough to see and execute the correct buttons.  Note that for me, I had to use the left button, and not the right. 

Also, just an aside, this glaring gaffe doesn't seem too particularly smart of a design decision choice by the engineers.  I expected better from really smart people who'd like to make some market share inroads on M$.  Making it tough for the masses to install your product sure ain't the answer. 

If this was designed to have inflexible dialog boxes larger than the lowest common denominator resolution, then it's just plain stupid.  There are mistakes, oversights, bugs, and stupidity.  This one is in the latter if by design.  At the VERY least Q/A should have caught this basic gem (at install?!?) setting up some older systems, eh?

---

### Post by MartynT on 2007-06-02
Hi Wherdgo,

thanks for the suggestion, the ALT LMB works for me.

I was also given another tip ... <ctrl><alt>+  This cycles through the different resolutions available.  This didn't solve my install/resize problem but it did rectify my 800x600 screen draw problem.  The top menu bar is now at the top of my screen.

I also had a look at /etc/X11/xorg.conf
everything looked ok.  It is possible to restart the xserver with <ctrl><alt>backspace

> **Wherdgo said:**
> Got a clue from another thread: [http://ubuntuforums.org/showthread.php?p=2755914#post2755914](http://ubuntuforums.org/showthread.php?p=2755914#post2755914)
this glaring gaffe doesn't seem too particularly smart of a design decision choice by the engineers.  I expected better from really smart people who'd like to make some market share inroads on M$.  Making it tough for the masses to install your product sure ain't the answer. 

If this was designed to have inflexible dialog boxes larger than the lowest common denominator resolution, then it's just plain stupid.  There are mistakes, oversights, bugs, and stupidity.  This one is in the latter if by design.  At the VERY least Q/A should have caught this basic gem (at install?!?) setting up some older systems, eh?

I agree that it frustrating when you run into problems like this, but I think we should be a little forgiving.  Stuff like this happens with software.  What would be less acceptable is if they didn't fix it and even worse if they fixed it and then re-introduced it.  But enough speculation.
To get this fixed we should raise it as a bug.  So how do I do that ?

Thanks again everyone for all your help.

Martyn.

---

### Post by darkwing|duck on 2007-06-02
I tried both tricks and got nowhere.  Anyone have any other ideas.  I can run through my specs if nessaccary but seems like this is a across the board type thing

---

### Post by Wherdgo on 2007-06-05
> **MartynT said:**
> 
I was also given another tip ... <ctrl><alt>+  This cycles through the different resolutions available.  This didn't solve my install/resize problem but it did rectify my 800x600 screen draw problem.
<snip>
I agree that it frustrating when you run into problems like this, but I think we should be a little forgiving.  Stuff like this happens with software.  
<snip>
To get this fixed we should raise it as a bug.  So how do I do that ?


1) The <ctrl><alt>+ tip didn't work at all for me.  I wasn't given any other resolution options.
During installation off CD, with a blank HDD, Feisty determined that my laptop could only support the safest 640x480 resolution, with no other options.

Notable here, is the fact that this exact same laptop had no problem of this sort with DapperDrake or EdgyEft.  The issue is new.

2) Yes, it's frustrating, and yes "stuff like this happens with software" but it's simply not an acceptible "oversight" to make a design choice of 640x480 as the failsafe minimum resolution, then design all of your initial installation dialogs larger than that.  Otherwise, everyone installing on older or un-identified/unsupported hardware winds up in this catch-22 during installation.

3) I'm looking for references on Launchpad to reference this as a problem, or report one: [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

---

### Post by Wherdgo on 2007-06-05
There is Bug #38442 reported on this at: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/38442](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/38442)

---

