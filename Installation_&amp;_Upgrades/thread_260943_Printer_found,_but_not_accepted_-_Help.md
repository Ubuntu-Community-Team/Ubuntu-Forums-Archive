---
title: "Printer found, but not accepted - Help?"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by emarkay on 2006-09-19
I am doing this with Ubunto, running from the CD.

I have a HP PSC1350 "all in one".  Open Office does not see the printer, so I presume I need to "Add" it.  Adding a printer goes as follows:

Step 1
It finds 2 applicable drivers:
"hp psc 1300 series" AND "HP psc_1300_series" 
(why two of the same with only textural differences???)

Click on either and they go inverted (as being selected). Forward to step 2.
I see "Printer Driver" "manufacturer" is "HP", "Model" is "PSC 1300", and "driver" is "hpijs (recommended) HPLIP 0.9.7 (sugested)" and then a "install Driver" button.

Install driver says "Select a PPD file".  Um, OK, and playing around gives me nothing I can make sense of, but if I DO not hit the "install Driver button, I get Step 3, and Putting a description and a name and the hitting "Apply" sends me back to the printer window and the PSC printer still does not appear, and OpenOffice sees it not.

I am stuck and "HELP gives me this:
"4.3.6.&#8195;Printers
Some printers will be automatically detected by Ubuntu; for those that are not, choose System &#8594; Administration &#8594; Printing then choose Printer &#8594; Add Printer	and run the Printer Install Wizard. There are some printers that need further setup. Search the databases at LinuxPrinting.org or check the Ubuntu Wiki's Printer page for possible information on your printer."

I go ther eand I see:
"HP PSC 1300
Color inkjet printer, max. 1200x600 dpi, works Mostly 	
Recommended driver: hpijs (Home page, view PPD, download PPD)
Generic instructions for: CUPS, LPD, LPRng, PPR, PDQ, no spooler
Does not understand PCL as most other DeskJets/PSCs/OfficeJets, it uses the so-called "Lightweight Imaging Device Interface Language" (LIDIL), these printers are supported by the "hpijs" driver beginning from version 1.3. The driver supports resolutions only up to 600 dpi, head alignment settings stored in the printer are not made use of, so use a one-cartridge (CMY) printing mode in case of mis-alignments.
For basic printing functionality use the HPIJS driver . For advanced functionality such as printer status, maintenance features, scanning and photo card unload use the HPLIP driver (which includes HPIJS).
Copying works fine from the front panel.
User Notes
This printer driver works great with the PSC-1350 all in one."

So it looks like I need to install the driver - Wait a minute, Dave, Just a second.

...If I am running from the CD, where is it saving the printer info???  Is this a D'oh or really a problem?

THANKS!!!

---

### Post by frankelr on 2006-09-20
I.m pretty sure you can't setup a printer without installing Ubuntu.

Least that's the way it worked for me.  I found a blog which complain that Knoppix can do it, why not Ubuntu.

After install I easily set up both local and network printers


Bob

---

### Post by kristalsoldier on 2007-02-21
Actually, I am having exactly the same problem with my local Epson DX3850 printer. Ubuntu recognizes the printer and everything that 'frankelr' faces installing his HP also applies to the Epson.

So, is it the case that I cannot print without installing as emarkay suggests?

Thanks.

Ps.: I think this is the last problem I need to resolve before I actually install Ubuntu...umm...well maybe there is one more but that's not for this thread I guess!

---

### Post by kristalsoldier on 2007-02-23
OK. I ran 6.10 off a live CD and it found my printer. All's well!

But now there is a problem with the wireless, which worked fine with the 6.06 release!

If its not one thing, it's another! I'll look through the forum and post accordingly!

Thanks!

---

### Post by cweigle on 2007-04-01
I have just installed Ubuntu and yet I am seeing the same behavior as in the initial post - everything looks great until I hit the Apply button, and return to the printer utility only to find my printer (HP PSC 1401 all-in-one) still not listed there. I tried re-installing the cups files and still no go. Suggestions?

---

### Post by louieb on 2007-04-01
After you select the printer from the list, there are two buttons one **Install dirver** and the other **forward** if a driver is listed next to the **install driver ** button.  Then you click on the **forward** button. Its confusing, I want to click on the install driver button but thats not the way it works.

---

### Post by lasch on 2007-04-01
Having a similar problem as those mentioned above. However, I do have Ubuntu installe

---

### Post by lasch on 2007-04-01
Having a similar problem as those mentioned above. However, I do have Ubuntu installed. 

I am trying to install an HP Deskjet 1220C on LPT1. I can select the printer and it gives me a suggested driver, however when I hit the forward button, the printer is not installed. All the info I can come up with indicates that this printer should work. Any Ideas?

---

### Post by 11hjpphty76lkjj on 2007-04-03
> **lasch said:**
> Having a similar problem as those mentioned above. However, I do have Ubuntu installed. 

I am trying to install an HP Deskjet 1220C on LPT1. I can select the printer and it gives me a suggested driver, however when I hit the forward button, the printer is not installed. All the info I can come up with indicates that this printer should work. Any Ideas?

lasch, mind starting a new thread for this? Sounds like your problem is different.

Once you do run

```
lsmod | grep ppdev
```if you don't see ppdev

run 

```
sudo modprobe ppdev
```and try configuring your printer again.

If you continue to have problems please start a new thread and send me the link so i can respond.

A

---

