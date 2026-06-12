---
title: "Inst stops after X Windows fails to copy/install"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by Cafargo on 2007-09-05
Greetings.

Early on in the intallation operation of Ubuntu 7.0.4 desktop, the operation stops, as a message box appears indicating that X Windows cannot be installed or copied (I'll have to run the inst again and jot down the exact error). I have to abort the installation by quiting out. I'm attempting to install Ubuntu on my old P2 box, Intel se440bx motherboard, 192mb RAM, with 2 maxtor disks, enough disk space. There's an unreliable version of XP pro running on my box which I suspect might also be unstable, which I'd like to clean off my machine. 

Anyway, if anyone can point me in the right direction with this issue, I'd be very greatful. 

Thank you, and best.
C.

---

### Post by Pumalite on 2007-09-05
With your memory>Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by Cafargo on 2007-09-05
Thx Pumalite. I'll give it another stab.

Cheers.
C.

---

### Post by Pumalite on 2007-09-05
You are welcome. Good luck!

---

### Post by jlombs on 2007-09-05
I am getting the same issue.

I have an old PII - 266, 128 MB of RAM, 6.4 GB HD, 4 MB video card

I have tried to install Kubuntu 5.10, Ubuntu 6.06, Xubuntu 7.04 - I have tried the alternate installs for both.  It seems to keep freezing at the same spot.

I can get DSL to install, but I really don't like the look and i think it is hard to use (I want to give the system away), I also got Zenwalk to install but it didn't pick up the network and I kind just got disgusted.  

Any suggestions?

---

### Post by Pumalite on 2007-09-05
Are you sure you have a Video Card and not 'Integrated Video'? If the latter, it would reduce your options to Zenwalk or DSL.
It could also be a matter or cofiguring your xorg file. Could you give more details of your problem with the Xubuntu Alternate?

---

### Post by jlombs on 2007-09-05
First - Thank you for responding so quickly. 
It is a PCI video card - not embedded in the MB (the computer is a gateway G6-266)

I will pop in the xubuntu install disk again to see what it does.

It seems like any debian based install has issues - I ripped everything out except the video card because i don't have any spare pci video cards anymore and it doesn't seem to help.  I also moved it around to different PCI slots to see if it was an IRQ conflict.

---

### Post by Pumalite on 2007-09-05
Give me a link to your PC, so I can check better the hardware or be more specific. Also, when you installed with the Xubuntu alternate did you get to the end and on reboot you ended up without screen?

---

### Post by jlombs on 2007-09-05
It freezes after the it detects new hardware (it goes 100% and then nothing)

---

### Post by jlombs on 2007-09-05
[http://support.gateway.com/support/srt/docs.asp?sn=0007548952](http://support.gateway.com/support/srt/docs.asp?sn=0007548952)

---

### Post by Pumalite on 2007-09-05
Well, I think you are stuck with a smaller distro. Unless Merlin, who is around has a better idea

---

### Post by merlinus on 2007-09-05
With 32MB RAM, you will probably not do too well with any current linux distro, especially in terms of running applications.

Check the specs for DamnSmallLinux and puppy linux via google.

-merlin

---

### Post by jlombs on 2007-09-05
Once again, thanks for the quick replies guys

Merlin - the system has 128 MB (just an FYI)

I don't think DSL is too easy on a beginner of computers (I had some trouble getting around and the file system is very rough).  

Any suggestions on a better smaller distro?

---

### Post by merlinus on 2007-09-05
OK on the RAM. I simply looked at the webpage link you provided, and it seemed to state 32MB.

You might check out this info:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

-merlin

---

### Post by jlombs on 2007-09-06
Thanks Merlin - I will try this when I get home from work.
~ Joey

---

### Post by Cafargo on 2007-09-06
Hello All.

It's great to see your feedback. This takes back to my old softimage tech support years. In any evet, as was the case with jlombs, I still stall roughly at the same spot with 'xunbuntu' desktop installer. My video card is an old dpi Oxygen 202 (from the precambrian age); might have an impact, but I'm not sure?  I jotted down the message that appears in the 'error' box though:

"Failed to start the X server (your graphical interface). It is likely that it is not set-up correctly. Would you like to view the X server output to diagnose the problemÉ  .yes.   .no.  "

Whe I choose 'yes', another box appears with version info. and the like, which was too long to jot down, but I did retain this line to the effect of installing or loading " the latest version of the module loader"? 

And again, I had to quit out.

Any more thoughts about this issue?

Many many thanks!!!
Best.
C.

---

### Post by merlinus on 2007-09-06
You might try this:

Ctrl-Alt-F1 to get to prompt

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```

-merlin

---

### Post by Cafargo on 2007-09-06
Thx Merlin.

Though I'm not sure from where or at which point I type the cmds? Is it once I quit the message window, which takes me back to the install prompt (which I saw on my last attempt), then I type the 1st cmd? Sorry, linux install is new to me.

Best.
C.

---

### Post by merlinus on 2007-09-06
Try it when you first get the error message.  If that does not work, you could try typing in the command at the install prompt.

-merlin

---

### Post by Cafargo on 2007-09-06
Okay, ignore my last post. I'm going through the list of Q and As right now. 

mega thx.
 keep you posted.
C.

---

### Post by Cafargo on 2007-09-06
Hello O illuminated ones.

Well, still no luck. After I running the cmd, the xserver reconfig cannot configure the driver. Would there a way for me to install a linux compatible driver for my DPI Oxy. card before running the ubuntu installation, or before reconfiguring the xserver voodoo thing?  Is that too naive a thought? The other thing I noticed, don't know if this is normal, but after I did choose the vesa driver you suggested, at one point later in the confog operation, a PC.2.1.0 driver gets configured, but this operation seems to last for hours, as I only noticed a few dashes gone from the startus bar. So, I'm confused about this process, as I'm not even sure the configuration of the driver is occurring at all. The final result being that the driver cannot be found or configured? Boy, Im getting my money's worth. But, I love it. It's fascinating.

What next?

Molto-Thanks.
C.

---

### Post by Cafargo on 2007-09-06
I think that perhaps I should upgrade to a more recent grfx card. Methinks that this may be the reason behind my woes. After doing a perfunctory search for any sort of linu base drv for my old klunker of a card, I didn't find anything. Well, I guess it's ebay shopping time for me now.

Many thx for all for you input. :)
Best.
C.

---

### Post by jlombs on 2007-09-19
Hey sorry I didn't come back sooner....
The striped network install didn't work either.  I could have sworn I got 6.06 to install on that machine.  I popped out a different video card - still the same issue.  

I am at a loss....

Also if anyone is around.  I have two old HP LH Pro servers I was looking to donate as well.  The bios is funky and I need a boot disk.  Is there a xubuntu boot floppy?  
(Or should I try just installing Ub 6.06 server on them?)

I tried to create the smartboot disks - that didn't go so well.

---

### Post by Pumalite on 2007-09-19
[http://ubuntuforums.org/showthread.php?t=538208](http://ubuntuforums.org/showthread.php?t=538208)

[https://help.ubuntu.com/community/Sm...28smartboot%29](https://help.ubuntu.com/community/Sm...28smartboot%29)

Or to make the SBM floppy on a linux machine, you want to copy the 'sbm.bin' (~1.4MB) file from the '/install' dir on the ubuntu CD:
Quote:
sudo mkfs.msdos /dev/fd0
cd /dev/cdrom0/install
sudo dd if=sbm.bin of=/dev/fd0
cmp sbm.bin /dev/fd0 (-->checks for errors)

---

### Post by jlombs on 2007-09-19
Thanks Pumalite
My issue is that my linux laptop doesn't have a floppy 
Following the instructions for the windows disk... the image file is no longer there.  I should have rephrased.

Does someone have an image of a xubuntu floppy i can snag

---

