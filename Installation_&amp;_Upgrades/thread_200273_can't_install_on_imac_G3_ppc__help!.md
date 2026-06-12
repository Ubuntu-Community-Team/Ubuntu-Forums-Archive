---
title: "can't install on imac G3 ppc :: help!"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by plasmafusion on 2006-06-20
hay all :)
i recently acquired a g3 imac desktop (the all in one desktop variety with the slot loading cdr drive...350MHz 128MB RAM) and have been trying to install ubuntu 6.06 with NO success.
this is my first mac so i'm pretty unfamiliar with such things. i'm trying to replace os 9.2.2 not dual boot.
the only way i can get the thing to boot from cd is to hit the reset button on the side whilst holding "c". this actually gets to the yaboot prompt but 400 "c"s appear and then it hangs so that i can't delete them or type any commands. this happens regardless of how long i keep the "c" key pressed.
i've also tried using bootx but when i choose the "linux" option from the bootx app the imac sort of shuts down but the power button remains illuminated.
any help on this would be greatly appreciated as i'd love to replace os 9.2 with the lovely ubuntu (or kunbuntu) like i have on my laptop.

---

### Post by linear on 2006-06-20
1. Will the iMac boot from other CDs?
2. Do you know the CD to be good? (Compare MD5sum of iso vs. what is posted at the download site.)
3. Try burning the CD at a slow speed (4x or less).
4. After the startup chime, hold down the Option key. You should get a display screen with a choice of boot disks.
 
By the way, the iMac G3's usually require some tweaking of xorg.conf. You can find details in the Mac/PPC forum.

---

### Post by plasmafusion on 2006-06-20
thanks for the reply linear :)
i've only tried to boot the mac using 2 different cds...ubuntu 6.06 ppc & kunbuntu 6.06 ppc (the checksums are fine for both) as i don't have the original mac os disk to try. it obviously boots from cd slightly as i can see the yaboot prompt...just can't do anything with it.
the keyboard i'm using is just a regular usb pc keyboard so i don't think it has an "option" key...then again i could be wrong because as i said above i don't really have a clue about macs :( so is there an equivalent combination of keys to press that replicate the option key?
thanks again for getting back to me. i can see this little machine has lots of potential and would love to give it a new lease of life.

---

### Post by linear on 2006-06-20
[quote=plasmafusion]the keyboard i'm using is just a regular usb pc keyboard so i don't think it has an "option" key[/quote]

Try "alt" - may or may not work. If the keyboard is plugged into a hub, try it direct instead.
Also worth trying a Breezy CD.

---

### Post by plasmafusion on 2006-06-21
hey :)
already tried the "alt" key i'm afraid.
am downloading good ol' breezy now and will try it after work tonight.
cheers

---

### Post by plasmafusion on 2006-06-23
took me a while to try out your suggestions linear.
still suffering from the same problem i'm afraid :(
i got to the boot disk prompt showing the hard disk and the boot cd (breezy) but when i click on the cd i get to the ubuntu boot prompt but the cursor doesn't flash and i can't type anything or even hit "enter".
i'm at a total loss here

---

### Post by linear on 2006-06-23
With Breezy, where exactly are you getting stuck? Do you get a series of messages, then an Ubuntu logo with more messages, then a black screen? Or do you not get that far?
 
If the first, can you get to a shell? (ctrl-alt-F1, may take a couple of tries)
 
If this is the case, you need to edit /etc/X11/xorg.conf as detailed here:
 
[http://www.ubuntuforums.org/showpost.php?p=1102644&postcount=4]("http://www.ubuntuforums.org/showpost.php?p=1102644&postcount=4")
 
If you don't get that far, then I'm stumped too. Suggest you repost in the Mac/PPC forum: [http://www.ubuntuforums.org/forumdisplay.php?f=133]("http://www.ubuntuforums.org/forumdisplay.php?f=133")

---

### Post by plasmafusion on 2006-06-23
hello again linear.
glad you caught sight of this thread as no-one else seems able to provide any input ;)
the breezy (or dapper for that matter) boot falls at the first hurdle. i get to the first prompt (where you would enter any additional boot options or just press enter to install) and get no further.  as i said above the usual blinking cursor is frozen so that the machine doesn't respond to any keyboard input and i need to do a hard reboot to quit it.
i may start a thread in the ppc forum (when i first joined i thought this one was more appropriate) and thanks for all the suggestions.

---

