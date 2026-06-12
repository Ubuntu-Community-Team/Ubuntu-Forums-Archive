---
title: "Running into a problem installing"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by rikguenther on 2007-07-27
Computer Specs

Dell Dimension B110
Intel Celeron D 2.5 Ghz Processor
512 MB 333 Mhz DDR RAM
256mb ATI Radeon 9250

Not the best, but whatever.  Anyways, the problem I'm having is i put in the live CD, it boots up and i hit install, it uppacks the files and all that jazz.  however, as soon as it gets to the point where it starts to boot x-server, the screen gets loaded with all sorts of nasty colors, much like when you kick the NES cartridge while the game is playing it gets all discolored.  yeah.

i heard somethign about configuring the xorg file or something... i have no idea how to do that.

so if you could help me with that i'd be thankful. 

also i heard that ATI cards dont work that well with linux, or dont have the best drivers.. idk

---

### Post by Ek0nomik on 2007-07-27
> **rikguenther said:**
> Computer Specs

Dell Dimension B110
Intel Celeron D 2.5 Ghz Processor
512 MB 333 Mhz DDR RAM
256mb ATI Radeon 9250

Not the best, but whatever.  Anyways, the problem I'm having is i put in the live CD, it boots up and i hit install, it uppacks the files and all that jazz.  however, as soon as it gets to the point where it starts to boot x-server, the screen gets loaded with all sorts of nasty colors, much like when you kick the NES cartridge while the game is playing it gets all discolored.  yeah.

i heard somethign about configuring the xorg file or something... i have no idea how to do that.

so if you could help me with that i'd be thankful. 

also i heard that ATI cards dont work that well with linux, or dont have the best drivers.. idk

I think I know what colors your talking about.  If nobody else appreciates the NES reference, let it be known that I adored it.

Back onto topic...

The problem is almost certainly your ATI video card.  I have run into the same problems.  I don't even like ATI to be honest, but I got both of my cards for free, so it's hard to complain.

I would try to install Ubuntu with the Alternate CD rather than the Live CD.  The Alternate CD is a text based installer, thus, it won't load the GUI.  You can install it from the Ubuntu website.  There is a check box below the the green 'Start Download' button.

Then you will want to install using the open source driver I believe.  I use the fglrx proprietary driver, but I don't think it supports your video card anymore.

I will see if I can find some more information on the open source driver.

---

### Post by rikguenther on 2007-07-27
thank you a lot, i havnet tried it yet but i plan on it as soon as i partition my computer to dual boot (so the family doesnt get all mad about WTF IS THIS WHERES MY INTERNET EXPLORER!

yes, my ATI card was the best i could get for the money i could spend on a regular PCI based graphics card.  Stupid low end Dell lol.

but what i was referring to with the cofigure my xorg file thing was there is some line of code you can put in that brings up a series of options that allow me to select my display driver, select teh modes for it, keyboard settings, all sorts of stuff.

i have no idea what the code was, but it was a longer one and it fixed everything when i was still using the onboard video graphics... which reminds me

it does the same thing with the standard Intel Extreme Graphics 2 that came onboard with the system, but do you think if i configured it to use that for the installation then i could download an update for my ATI card?

---

### Post by Ek0nomik on 2007-07-27
> **rikguenther said:**
> thank you a lot, i havnet tried it yet but i plan on it as soon as i partition my computer to dual boot (so the family doesnt get all mad about WTF IS THIS WHERES MY INTERNET EXPLORER!

yes, my ATI card was the best i could get for the money i could spend on a regular PCI based graphics card.  Stupid low end Dell lol.

but what i was referring to with the cofigure my xorg file thing was there is some line of code you can put in that brings up a series of options that allow me to select my display driver, select teh modes for it, keyboard settings, all sorts of stuff.

i have no idea what the code was, but it was a longer one and it fixed everything when i was still using the onboard video graphics... which reminds me

it does the same thing with the standard Intel Extreme Graphics 2 that came onboard with the system, but do you think if i configured it to use that for the installation then i could download an update for my ATI card?

The command probably was

```
dpkg-reconfigure xserver-xorg
```

which I don't think it going to solve your situation.  Your problem is getting video to begin with since you couldn't get boot into the Live CD.

---

### Post by rikguenther on 2007-07-27
> **Ek0nomik said:**
> The command probably was

```
dpkg-reconfigure xserver-xorg
```

which I don't think it going to solve your situation.  Your problem is getting video to begin with since you couldn't get boot into the Live CD.

ok well i think i isolated the problem.  remember how i mentioned the onboard graphics card?  well when i boot regular from the live cd, it tells me , right after the NES colors, that its trying to detect my lame intel extreme graphics card on a PCI port that doesnt exist, mind you this card is onboard and therefore shouldnt have any PCI affiliation.  then it goes to a terminal where i can put in the code.  so i run the xorg config stuff and set it to the right pci location with the ATI driver (figured that would be the safest route) and all the stupid keyboard setup and stuff.... but them im stuck.  because if i reboot the computer, it erases my memory and therefore wont have the changed xorg file.

what im gettting at is there some kind of way to boot the linux live cd from that point?  like some kind of code i can put in right after i change the xorg file?

OH and BTW and FYI i decided to use my newly acquired feisty fawn cd instead of my dapper and it WILL load if i boot with safe graphics.  i have no clue what that means, but i know it works and will let me install from there, however im afraid taht if i do that ill be stuck with no way to boot regular becasue of my video card.

---

### Post by Ek0nomik on 2007-07-27
> **rikguenther said:**
> ok well i think i isolated the problem.  remember how i mentioned the onboard graphics card?  well when i boot regular from the live cd, it tells me , right after the NES colors, that its trying to detect my lame intel extreme graphics card on a PCI port that doesnt exist, mind you this card is onboard and therefore shouldnt have any PCI affiliation.  then it goes to a terminal where i can put in the code.  so i run the xorg config stuff and set it to the right pci location with the ATI driver (figured that would be the safest route) and all the stupid keyboard setup and stuff.... but them im stuck.  because if i reboot the computer, it erases my memory and therefore wont have the changed xorg file.

what im gettting at is there some kind of way to boot the linux live cd from that point?  like some kind of code i can put in right after i change the xorg file?

OH and BTW and FYI i decided to use my newly acquired feisty fawn cd instead of my dapper and it WILL load if i boot with safe graphics.  i have no clue what that means, but i know it works and will let me install from there, however im afraid taht if i do that ill be stuck with no way to boot regular becasue of my video card.

Your computer will still boot, you will probably just get a command prompt screen.

You could also install with the Alternate CD as I mentioned before.  Not having a graphical interface isn't something to be afraid of.  :)

---

### Post by rikguenther on 2007-07-27
> **Ek0nomik said:**
> Your computer will still boot, you will probably just get a command prompt screen.

You could also install with the Alternate CD as I mentioned before.  Not having a graphical interface isn't something to be afraid of.  :)

true, but im in a shortage of blank cd's and am trying to preserve them as much as possible. 

I think what i'll do is just install Ubuntu in safe graphics mode, then when it boots GRUB i'll just pick to boot into recovery mode, adjust the xorg file and pray for the best.

---

