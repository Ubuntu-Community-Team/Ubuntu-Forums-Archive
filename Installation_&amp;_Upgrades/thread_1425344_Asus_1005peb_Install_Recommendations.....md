---
title: "Asus 1005peb Install Recommendations...."
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by MacKai on 2010-03-09
I'm picking up a Asus 1005peb tomorrow and I'm looking for Install Recommendations... 

I under stand there have been some issues with the keyboard and touch pad.... what is the currant wisdom here? Just install, then do the normal update process with a reboot... is the fix I read last.... 

But mostly I am wondering about which .ISO to install... I have all but cut the cord with Windows, (the sole remaining reason to keep windows is that I travel around for work giving presentations and Ubuntu doesn't like some projectors, I don't have time usually to fight with it so I just do the presentation with windows and be done with it)  every thing else I do in Ubuntu.

So.. I would like to install with Wubi.... But I see that the “net book remix”  doesn't use Wubi....

the normal .ISO doesn't support “some net book features” like the Atom processor etc.. I see that I could install the normal desktop .ISO with Wubi and then install the Net book packages.... 

but to make it more complicated the Atom processor is a 64 bit chip. So should  I install the 64 bit  with Wubi and then the net book packages?


Has anyone used any of these options to Wubi on to a 64 bit net book? Or a different option? 

MacKai

---

### Post by emoguitarist06 on 2010-04-06
I just bought the Asus 1005peb from bestbuy today and this is what I did.

1. Turned on computer and setup windows 7 starter
2. Made an empty partition (start>rightclick mycomputer>manage>disk management>shrink windows 7)
3. Turned off computer and restarted and booted in bios (f2) & disabled quick boot option and put Ubuntu USB as primary boot option
4. Exited bios and ran Ubuntu 9.10 32-Bit (Desktop Edition NOT UNR) and installed in "Largest Continuous Space"
5. Shut off Computer

What works.... EVERYTHING! I even kept the Express Gate. So technically I have 3 OS installed, Windows 7 Starter, Express Gate, and Ubuntu 9.10

I do not recommend Wubi because it installs within Windows which means if Windows gets a virus or some blue screen of death problem than Ubuntu wouldn't work. I highly recommend giving Ubuntu it's own partion

Grub let's you choose to boot into either Ubuntu or Windows

Hope This Helps

---

