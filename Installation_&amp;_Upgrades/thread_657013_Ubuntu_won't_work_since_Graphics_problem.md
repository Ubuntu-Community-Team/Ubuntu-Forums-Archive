---
title: "Ubuntu won't work since Graphics problem"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by array22 on 2008-01-03
Hi, 

The hardware is: 
Dell Dimension 2350
2.0 GHz processor
512 MB RAM


I was running Ubuntu happily with no problems for a couple of months when ... 
the On-board graphics failed. 

I was getting only a blank screen, so I figured I would insert a PCI graphics card. 

The inserted card is a: 
Stealth 3D 2000 Pro 
2 MB
Made by Diamond Multimedia Systems


But when I insert the Ubuntu Live CD:
* It gets to the options screen, where you choose to run the CD, or check cd for defects, etc
* I choose the options to run the CD

Then there is the black screen, with the Ubuntu logo, and under it an orange Status bar. 

Every time, the status bar freezes, and it won't go any further! 


Then I got the idea of using the "Alternate CD". I went through the whoile installation, which worked fine. Then ... when the system needed to be re-booted after the install, it again froze on an orange status bar, and will go no further. 

It also freezes with the Live CD of Kubuntu, Xubuntu and FreeSpire. 

But, I can install and use Windows XP with absolutely no problem. :(

I need Ubuntu back!!

Any ideas? 

Is the PCI graphics card un-suitable? 
Is the malfunctioning On-board graphics interfering with it? 

Thanks.

---

### Post by chewearn on 2008-01-03
Is it possible to disable the onboard graphics via BIOS?

---

### Post by PmDematagoda on 2008-01-03
Can you boot Ubuntu through Recovery Mode? If that is the case then it is your new VGA card causing the problem, not the onboard VGA card since the onboard one is automatically disabled when a separate VGA card is used(This is true for most mainboards).

One more thing, are you sure that your "new" VGA card has only 2Mb of memory or is it a typo?

---

### Post by array22 on 2008-01-03
Thanks for the suggestions. 

Hi AstalaVista, 

In BIOS, there is one setting regarding graphics, with two settings: 
* Auto   (the default setting)
* On-Board

I previously set it to "On-Board" to see if that changed anything, and was a *Disater*. It stopped the PCI card from working, so I had no graphics at all. and needed to do a Hail Mary option ... Clear CMOS. Thankfully, I worked out how to do that. 

There doesn't appear to be any other BIOS setting to do with Graphics. 


Hi PmDematagoda, 

I am not sure how to do recovery mode?? 
Need to get info on that. 
Is it a command line thing? 

I do hope the problem is the new PCI card, as I can always get another one. 

Not a typo. I got the PCI card from eBay in a hurry, and it says 2MB on the label. 


Much appreciated. 
Any more suggestions would be great. 


From a snowy Northern Ireland, :)
Barry

---

### Post by PmDematagoda on 2008-01-03
Recovery Mode can be selected when you start the PC, do you see a sort of list when you start the PC? Such a list would look a little like this:-
```
Ubuntu 7.10
Ubuntu 7.10 (Recovery Mode)
Memory Test +86
```

You will need to select the Recovery Mode entry of Ubuntu to boot Ubuntu in Recovery Mode, keep in mind that no splashscreen will show up and the GUI will not start-up automatically.

---

### Post by dannyboy79 on 2008-01-03
sounds like your vid card is dieing or is dead. can you get your hands on a nvidia chipset pci graphics card  if you don't have a agp slot? If you've been working for months just fine, then don't reinstall, you'll lose everything. You just need to get your hardware straightened out.  can you try other livecd's? maybe puppy linux or dsl. that way you can get in and see if your grpahics card is working. if it is, then your xorg.conf just got borked and can be fixed from the livecd you're using (puppy or dsl). let us know.

---

### Post by Tuxtur on 2008-04-02
I just posted an answer to the same question here is the link to the answer. 
[http://tinyurl.com/37xofe](http://tinyurl.com/37xofe)

To sum it up a bit I think Dell 2350's cause kernel panics in most linux distros when a video card is added, I think it has something to do with the way hardware is detected and it finds both the onboard and the added card it freaks out and causes a kernel panic.

---

