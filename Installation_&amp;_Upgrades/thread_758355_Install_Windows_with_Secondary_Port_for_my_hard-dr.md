---
title: "Install Windows with Secondary Port for my hard-drive ?"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by tunganet on 2008-04-17
Greetings, I am currently having problems installing Windows XP once again.

	Let me explain what is going on first.  A few years ago, when my computer had an unknown problem, I brought it to the store where I bought it from and fixed it because it was still in the 3-year-warranty period.  After a week weeks when I got it back and tried to boot it up at home, it failed to boot up so I brought it back to the store again.  They told me that the primary port for the hard-drive had been broken, but they said the computer would boot up as long as i use the secondary port.  So I was fine with that and took it home and ran Windows XP for a few months until it broke again.

	One thing though, when it broken down, I didn't bother going back to the store to install Windows XP again because that would cost $40 dollars since the warranty was over then.  So I did some researched and installed Linux (Ubuntu) onto my computer.  Nothing bad except that my kids could not enjoy their favourite online games as good as Windows.  Due to that, I eventually paid $40 dollars to get Windows installed onto it.

	So now, the problem is that when I try to boot up the Windows XP disk myself, it does not have any problem loading the CD, which brings me to the blue screen.  And after having a long wait for it to detect my hardware and stuff,  it asks me if I want to A)Install Windows  B) Repair Windows  C) Quit,  so obviously I choose to install Windows.  But right away, it tells me this message: 
"Setup did not find any hard disk drives installed in your computer.  

Make sure any hard disk drives are powered on and properly connected to your computer, and that any disk-related hardware configuration is correct. This may involve running a manufacturer-supplied diagnostic or setup program."

Setup cannot continue, to quit, press F2."

	I know it can be done because the store installed Windows XP on the same computer after I paid them, is there any help on how it could be done?

Thank you for your time.

---

### Post by Lantesh on 2008-04-18
There is no such thing as a "primary port" or "secondary port" on a hard drive.  A typical PC hard drive utilizes an IDE, SATA, or SCSI interface, but regardless of of what interface it uses there is only going to be one interface connection on it.  The other connection is for the power supply plug.

As far as why your hard drive is not detected during your installation process I can't say.  I would take the cover off of the case and make sure all your connections are tight.  Next boot the PC and try pressing F1 or the delete key.  You want to get into the system BIOS and make it's actually detecting the hard drive.  Other than that good luck.

---

### Post by tunganet on 2008-04-18
I am not good with computer terms.  But would it be much help if I snap a picture of the "port" that I am talking about so you guys can identify it?

---

### Post by Lantesh on 2008-04-18
You can if you want, but honestly all that is going to tell me is what kind of interface it has.  You will know that once you get booted up into your BIOS anyway.  That is what you really need to do, and see if the BIOS is detecting the hard drive.  If the Windows install can't see the hard drive it's either a bad physical connection...ie: could be loose, or the hard drive has gone bad, or the mother board has gone bad, or the BIOS has simply lost the information and you need to play with the settings.  Either way me looking at a picture is not going to help you much.

---

### Post by tunganet on 2008-04-18
I know it's the motherboard that has gone bad because the port is chipped off and I am using a "secondary" one, I guess that is why my computer fails to detect it.  But the problem is how do I make my computer detect it?

---

