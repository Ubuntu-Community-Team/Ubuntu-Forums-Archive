---
title: "Startup Hangs"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by PRocker267 on 2006-08-16
Hello all, i have posted about this problem here before but i gave up since i didn't get any help, but I'm hoping this time i might get this fixed, but anyways, i tired installing Ubuntu 6.06 and installation goes very nice ( I installed from the alternate CD ).  But when i reboot into the new instllation, the PC completelly freezes after it starts Gome Display Manager.  I have found that if i remove my PCI Video card and try again (just using my onboard) it starts up perfectlly.  I get the same exact problem on the LiveCD.  I have looked in my BIOS and i found the setting for the pirmary display device, i have it set to my PCI card (Which is an nVidia Geforce MX 5200)  But i still get the same resault,  I was told that if i copy the xconfig file or somthing like that from a working distrobution to the ubuntu installation, this would stop the PC from locking up when it starts GDM, will that work? because the only distro that i can get working uses KDM,  But if this will work, how can i stop GDM from starting up and then edit xconfig from the command line.  I tried PCLinuxOS and i get the same problem but i was able to stop KDM from starting and i used the "Video" command to select what video card to use. Does ubuntu have a feature like this?  I really want to use Ubuntu but i dont want to have to get rid of my good video card.  From what i have seen, i seem to be the only person on earth with this problem.  I hope someone can help [-o<

---

### Post by encompass on 2006-08-16
We need to know what your video card is.  If it is an ATI I have had that error before....  switch to the vesa driver...
```
sudo dpkg-reconfigure xserver-xorg
```
press enter for all the defaults until you get to the part where you select your driver.... select vesa.  That should get your graphics back.
But this may not be your problem... you haven't told us the hardware that is giving you the problems.
And many people with integrated cards have this problem.  I did.

---

### Post by PRocker267 on 2006-08-16
Yes, sorry, My onboard is an Intel 82810E, and my PCI is an nVidia GeForce FX 5200, my computer is really old, not sure how old but it came with Windows ME, if its any help i have a Compaq Presario "Internet PC" ( not sure why they would make a PC soley for internet ).. Model is 5BW250.  I have looked on my motherboard and the only jumper settings there is is for the CMOS, so i can't disable my onboard this way.

---

### Post by encompass on 2006-08-16
Well, I haven't seen a computer yet that you can't set the pci to go first.  I have your card too.  Just not your mainboard.
Check the bios and find out if you can't fix that.
If you have the 5200 you should be able to use the driver install I found here... [http://ubuntuforums.org/showthread.php?t=139264&highlight=envy+script](http://ubuntuforums.org/showthread.php?t=139264&highlight=envy+script)
you need to run it from the console.
It will download and set just about everything up for you.  If it doesn't work... then it didn't detect that you have a pci card.  I and I can help you with that.  I just don't have that computer with the geforce right now... it is getting the HD replaced. But none the less.  This should fix your issue.
Thanks for asking your question.

---

### Post by PRocker267 on 2006-08-16
Encompass, thanks so much for your help, i have looked countless times in the BIOS and i only found that one setting and that still didnt work, But as for that driver, theres just one small problem, In order for me to get ubuntu working without locking up i have to remove the PCI card, So the driver will not detect a PCI card that is not there, and i think it could be a life risking attempt to insert the card after the PC boots.  If there is a way to install that driver without the card being present at the moment that we can give that a try;) , thanks a lot for the help and a speedy reply!:mrgreen:

---

### Post by encompass on 2006-08-16
KEEP YOUR CARD IN THERE.
Oh yes of course!
You can press escape durring the bootup and drop to a console. You will see a count down... that is when you press escape.  Try running dpkg-reconfigure xserver-xorg
select everything you can as default except for your driver... select vesa.  Reboot.  If that works you have your graphical... if not... try this... when the screen goes blank... press ctr alt F1 and see if you get to a login screen
that is your text screen.  If you can get there.. I willgive you the command to get the envy script with out a browser.
BTW.. Instant message me and I can help you more too. ¶:

---

### Post by PRocker267 on 2006-08-16
Hmm, i didnt know you could press esc, i tried ctrl alt F1 before and it didnt do a damn thing, but i will give this a try, and it if it dont work i found somthing on a wiki that has my exact problem :D
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

### Post by Eykonic on 2006-08-16
I have the same problem you describe in trying to install 6.06 with Matrox vdeo card. Any suggestions?

---

### Post by PRocker267 on 2006-08-16
Eykonic, 
I'm about to give Emcompass' idea a try and see if that works, if it does i'll be sure to let you know, wish me (And you) luck :-D

---

### Post by Eykonic on 2006-08-16
I tried CtrlAltF1 and got a result back:
"ACPI   Unable to locate RSDP"   ???

---

### Post by PRocker267 on 2006-08-16
Well sorry for the delay, when i was installing ubuntu again i accidentlly selected the wrong thing and i erased my whole hard drive 8-[  So now i have to install XP first then ubuntu again... oh well.:-k

---

### Post by PRocker267 on 2006-08-16
Encompass,
I have installed ubuntu now and i tried pressing Esc during startup and it didn't do anything at all, it just proceeded to start GDM and then i was froze at a black screen.  I'm gonna try that wiki entry i found and see if that does any good.

---

### Post by PRocker267 on 2006-08-16
Success!  The wiki page worked!  I got ubuntu working on my nvidia card now with out a problem! Thank you so much for your help Encompass i really appreciate it!:D :D :D

---

