---
title: "Adding HDD For Windows"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by zuyx on 2009-12-13
Right now my computer is one HDD dedicated to (K)Ubuntu

I plan to take a HDD out of an older computer, that is running Windows XP. I plan to reformat it and reload XP onto it, so I can dual boot the two. 

Advice or anyone able to help on how to do this?

---

### Post by raymondh on 2009-12-14
> **zuyx said:**
> Right now my computer is one HDD dedicated to (K)Ubuntu

I plan to take a HDD out of an older computer, that is running Windows XP. I plan to reformat it and reload XP onto it, so I can dual boot the two. 

Advice or anyone able to help on how to do this?

Let's assume you have the 2nd HD installed in the main computer ....

1.  When you re-install XP,  it will overwrite the MBR of the HD (that is set to boot first in BIOS) with its' own bootloader.  If HD1 is set to boot first in BIOS, XP will overwrite the MBR of HD1. 

You have to re-install GRUB.  What and how depends on what version Kubuntu you are running (grub legacy or grub2)

2.  You can choose to load XP and it's bootloader on the same HD (the 2nd, spare).  To do that, one way is to disconnect the Ubuntu HD before installing XP.  

Your boot selection will now be from BIOS. 

Regards,

---

### Post by oldfred on 2009-12-14
Everything raymondh  says is correct but how easy it is to switch drives depends on whether you have Sata or Pata. Worst case is mixed as often the BIOS will not let you change order and pata defaults to first. Pata uses jumpers on the hard drive for master/slave or the newer cable select with the 80 wire cable and three color connectors. Middle connector is the slave. New motherboards that support Sata have BIOS settings to select which drive is first. System always boots from first drive in BIOS or first Master.

I like setting up systems with an operating system on each drive and that drive's MBR booting that operating system. Since grub can easily boot both I make Ubuntu the first drive and boot either from grub. But during the windows install the windows drive must be first or it will overwrite grub. So it somewhat depends on how easy it is to switch drives in your system.

---

### Post by stlsaint on 2009-12-14
in a nut shell to ride off what was said earlier...the most simple way would be to unplug the hdd that has kubuntu right now. then plug in xp hdd, format and install xp, then plug back in hdd with kubuntu and set it to boot first out of bios. Then simply add a stanza to menu.lst to see xp.
see signature for reference/procedures.

---

### Post by raymondh on 2009-12-14
> **oldfred said:**
>  Worst case is mixed as often the BIOS will not let you change order and pata defaults to first. .

Very true.  I forgot about the 'mixed PATA + SATA' dilemna.  

Thanks Oldfred :)

---

### Post by darkod on 2009-12-14
> **stlsaint said:**
> in a nut shell to ride off what was said earlier...the most simple way would be to unplug the hdd that has kubuntu right now. then plug in xp hdd, format and install xp, then plug back in hdd with kubuntu and set it to boot first out of bios. Then simply add a stanza to menu.lst to see xp.
see signature for reference/procedures.

To add to the discussion my humble opinion. Especially in mixed pata/sata cases it can lead to problems, possibly. What if the windows disk is forced to be first by BIOS always. Ubuntu and grub got installed labeling the ubuntu drive hd0, because it was only drive at the time. After adding the windows drive, if ubuntu drive is hd1, there goes your working grub.
And if one is not experienced in these matters, not an easy thing to troubleshoot at all. Sounds simple, just plugging the drives around. I always prefer: all hardware inside and happy with each other, then install OS (any OS).

---

