---
title: "Should I get a tablet pc and load it with Ubuntu?"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by Swarms on 2007-06-07
Hello I am a fairly new user to Ubuntu and linux in general.
I go to school and always hated paper+pen as an awful way of taking notes. Then I thought, I got a great desktop pc which I run wow over wine perfectly, I do all the internet surfing there too, but I could use a laptop for this other school purpose.

What I would like is a tablet pc, keyboard not needed really, its only purpose is I can write notes with a pen, and transfer it to my desktop for further processing.

I watched a demo of Windows XP Tablet Edition, but I take a certain pride in using Ubuntu because I enjoy the stability a lot more.

But is Feisty ready for using with tablet pc's? Or should I use MS?

Maybe you even know a good tablet which one of you got good experiences with?

Thanks in advance!

---

### Post by votetrev on 2007-06-07
I dual boot mine with a small xp partition and the rest of my tablet is ubuntu.  I don't ever use windows and am working on installing wine to install the few apps of mine left that i didnt find ported.

---

### Post by Swarms on 2007-06-08
> **votetrev said:**
> I dual boot mine with a small xp partition and the rest of my tablet is ubuntu.  I don't ever use windows and am working on installing wine to install the few apps of mine left that i didnt find ported.

And does your pen work?

---

### Post by Woody@N87 on 2007-06-09
If I may jump in here, I have an older HP tablet (TC1100) that I'd like to load Ubuntu on. It doesn't have a CD drive and  I can't seem to get it to boot from a USB drive.  The option is in the boot sequence at start-up but it didn't do anything.  (NO OS error message)   I put the contents of a feisty fawn disk on a USB thumb drive for this purpose. Are there other files that might have to be added to do this?  I've never loaded Ubuntu from a thumb drive and wondered if there was some trick to it.
  Thanks

---

### Post by francisco_athens on 2007-06-09
To get it to boot from the USB drive, you should try cold boot and enter the bios configuration.  you will have to see if the device shows up under the harddrives section and move its priority up.  That worked for me. 
The tc1100 make a great Ubuntu machine.  

some helpful links:
[http://wiki.linuxquestions.org/wiki/Tc1100](http://wiki.linuxquestions.org/wiki/Tc1100) <--kind of dated, but good reference
[http://wiki.linuxquestions.org/wiki/Tablet_PC](http://wiki.linuxquestions.org/wiki/Tablet_PC) <--list of nice apps (esp for Gnome)
[http://www.extremetech.com/article2/0,1697,2132602,00.asp](http://www.extremetech.com/article2/0,1697,2132602,00.asp) - intense Ubuntu installation tweaking guide
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2) - another ubuntu on usb guide.

Francisco

> **Woody@N87 said:**
> If I may jump in here, I have an older HP tablet (TC1100) that I'd like to load Ubuntu on. It doesn't have a CD drive and  I can't seem to get it to boot from a USB drive.  The option is in the boot sequence at start-up but it didn't do anything.  (NO OS error message)   I put the contents of a feisty fawn disk on a USB thumb drive for this purpose. Are there other files that might have to be added to do this?  I've never loaded Ubuntu from a thumb drive and wondered if there was some trick to it.
  Thanks

---

### Post by ishtob on 2007-06-11
I am using a TC1100 with just Ubuntu 7.04 right now. and it works great.
you'll need to edit the xorg.conf to get the right click to work, and if you want to have floating right click, a script that sets it at startup.

rotation works very well too, but also takes a bit setup. as for the wireless card. It worked out of the box :)

---

### Post by Mark Phelps on 2007-06-11
Isn't anyone going to answer the pen question???  I have a tablet PC and am interested in the same question.  

Unless Ubuntu, through some combination of apps and drivers, can support pen-based functions (e.g., writing, annotating, drawing, editing), it's useless on a Tablet PC -- which then becomes nothing more than a lightweight laptop with a rotatable screen.

---

### Post by K0LO on 2007-06-11
Mark:

I'm runing Kubuntu 7.04 on an IBM X41T Tablet PC. Yes, the pen is supported. It functions as a mouse with left and right-clicks with any app. If you want to draw, sketch, or write with the pen you need applications that are pen-aware. I am currently using Jarnal, which is an open-source Java-based sketching program similar to Windows Journal. There's also Gournal, which should blend in nicely with Ubuntu's Gnome environment.

However, as best I can tell, there is no killer tablet app similar to Microsoft's OneNote on Windows and very little support for ink in most Linux applications, but that may change with time.

If you do get a tablet, download ksudoku if you like Sudoku games. It is rather fun to play with a pen, although not as sophisticated as the Windows Sudoku games that let you directly write numbers in the squares with the pen.

---

### Post by francisco_athens on 2007-06-11
Tablets are fun, but PLEASE do lots of research - active versus passive touch (some have combo) maybe get a cheap used one on ebay.  New ones can be expensive for the feature that matter.

---

### Post by bcw on 2007-06-12
My tablets are slates, and I'm comfortable taking them out without a keyboard or mouse.  I can do just about anything I want with them (with the screen lock caveat below).

I have Kubuntu & Xubuntu running on my Fujitsu ST5032D and ST3400 respectively.  I have these features:
[LIST]
[*]Pen input (left, middle, and right button click)
[*]Handwriting recognition
[*]On-screen keyboard entry
[*]Screen rotation
[*]Suspend & Hibernate
[/LIST]
I have posted about the setup for the [[COLOR=GREEN]_ST3400_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=456110"), and after I've tested the new setup of Feisty on the ST5032D, I'll post that too.  Most of the setup is not specific to these models - I've done most of it on IBM Transnote as well, so you can apply it to other tablets.

I haven't tried Voice Recognition yet, and I can't comment on the state of that.  The handwriting recognition is from the xstroke package.  It does not work with cursive script writing, but does well with printing, although I've had to clean up my printing.  I've used a Palm OS PDA for years, and I have no problem using the Graffiti character strokes with xstroke, and many regular characters work as well - for instance, a small 'a' is recognized as written on paper if I remember to keep the down-stroke vertical.

I do not do extensive note taking, but I can operate almost all of the computer from the stylus.

The screensaver/lock packages do not provide any way to put an on-screen keyboard up for activation, so I've disabled screen locking.  I think this is a priority, as many Universities are mandating tablets now, so we  (Linux) had better catch up.  But I log in via an on-screen keyboard with the stylus.

I use the XVkbd on-screen keyboard, and I've tweaked the 'fitaly' layout to get me access to all the extra punctuation used in coding, PgUp/Down, etc.  I read recommendations for the 'onboard' keyboard, but haven't tried customizing it yet.  The 'fitaly' layout (with practice, just like with writing or typing) can exceed handwriting speeds and approach typing speeds - I settled on that as I can get that layout for PDAs and phones, too.  Practice, practice, practice...

I used VMware's free tool to extract the original Tablet XP install on the 5032D to a VM before installing Kubuntu, and I use that in VMware Player (proprietary, but available for no money).  The Windows handwriting recognition and voice input work just fine that way, so I can use any Windows Tablet programs too.  (The program I want it for - FranklinCovey's PlanPlus - runs on .NET, so won't run on WINE or Crossover Office).

I am planning to create an analogous package to PlanPlus in Java, so I can ditch that too.  No schedule yet, though.

Jarnal, Xournal, and Gournal all provide note-taking on Linux, and Jarnal allows annotation of other documents (it's the only one I know much about).  I believe there are others.

The fingerprint scanner and SD card reader on my ST5032D have no drivers in Linux yet.  There are projects, but I'm not following them closely yet.  Other machines have working drivers for everything.  I do have drivers for all the buttons around the tablet - PgUp/Down, Up/Down, ENTER, etc.

If you insist on cursive handwriting, and/or want delayed recognition, the Linux apps don't exist yet.  I do get all that in the VMware session of Tablet XP, but don't need it for most uses.  In my PlanPlus replacement, I'm going to put in delayed recognition, but it would still be of 'xstroke' typ character writing for now.  I can take handwritten notes directly in Jarnal in Linux - they just won't be recognized later as text.  I expect someone will take up the cursive/delayed handwriting app challenge soon.

Cheers,
Bret

---

### Post by Woody@N87 on 2007-06-21
Wireless worked out of the box! i'm jealous, mine will not do anything and seems to be powered down.  i tried the gui under administraotr-network and several teminal attempts to power up the card to no avail.  Any ideas or suggestions2
   i'm going to the sites listed by the other poster now to check on it, other than the wireless i'm very happy with the way the tablet is working.

> **ishtob said:**
> I am using a TC1100 with just Ubuntu 7.04 right now. and it works great.
you'll need to edit the xorg.conf to get the right click to work, and if you want to have floating right click, a script that sets it at startup.

rotation works very well too, but also takes a bit setup. as for the wireless card. It worked out of the box :)

---

