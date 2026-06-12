---
title: "Ubuntu on MS Virtual PC 2007"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by errolgreer on 2007-05-13
I tried to install Ubuntu 6.06 on Microsoft Virtual PC 2007. It installed, but the display format was so stretched horizontally that I could not read anything, so I was unable to click on anything to continue. I would be grateful for help on this. Many thanks, Errol Greer

---

### Post by starcraft.man on 2007-05-13
> **errolgreer said:**
> I tried to install Ubuntu 6.06 on Microsoft Virtual PC 2007. It installed, but the display format was so stretched horizontally that I could not read anything, so I was unable to click on anything to continue. I would be grateful for help on this. Many thanks, Errol Greer

A word of advice... try using VMware server/player, its a much better product than Microsoft Virtual PC, not to mention Virtual PC runs very slow in comparison, its just another in a long line of mediocre products MS has made. They are both listed [here,]("http://www.vmware.com/products/free_virtualization.html") try the player first, they are easily configured for basic running of Ubuntu :)

---

### Post by Wiebelhaus on 2007-05-13
> **starcraft.man said:**
> A word of advice... try using VMware server/player, its a much better product than Microsoft Virtual PC, not to mention Virtual PC runs very slow in comparison, its just another in a long line of mediocre products MS has made. They are both listed [here,]("http://www.vmware.com/products/free_virtualization.html") try the player first, they are easily configured for basic running of Ubuntu :)


/agree 100% , I've used all of these products extensively , i suggest VB but i would also suggest running Ubuntu as host....but that's just me.

---

### Post by chakkaradeep on 2007-05-13
> **errolgreer said:**
> I tried to install Ubuntu 6.06 on Microsoft Virtual PC 2007. It installed, but the display format was so stretched horizontally that I could not read anything, so I was unable to click on anything to continue. I would be grateful for help on this. Many thanks, Errol Greer

Microsoft products work good only with other Microsoft products :) 

So better switch to Vmware or Virtual Box

---

### Post by errolgreer on 2007-05-13
Thank you. I downloaded vmware player some time ago, but could not work out how to install ubuntu to it. It seems it wants a file already set up for the player ? Do I need an additional application to **create** the file vm player needs ? If so, which one, and most important **is it free ?** Thanks

---

### Post by fatty_chris on 2007-05-15
Use [[COLOR="RoyalBlue"]Easy VMX[/COLOR]]("http://www.easyvmx.com/") to create a machine.  I would recommend using Easy as opposed to Super Simple or Expert at first.  It asks you a couple of questions then gives you the file (when you click on the file name).  It works, and it's free.

---

### Post by gdrumm on 2007-05-24
Assuming that you don't want to use VMWare, how would you fix this issue?  I'm running VMWare Server, ESX Server, MSVPC, and MS Virtual Server on different machines.  I'd like to see how this works on MSVPC, if anyone's had any experience with it.  At the hardware emulation layer, this should theoretically work, no?

---

### Post by cknight725 on 2007-06-25
I had a similar problem with Virtual Server 2005. The fix is frustratingly simple:

1. Boot from Ubuntu’s install CD
2. Press F4, then choose “1024×768 16&#8243;
3. Then press F6, and at the end of the line add this: text vga=0×314

---

