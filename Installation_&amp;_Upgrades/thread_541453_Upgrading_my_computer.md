---
title: "Upgrading my computer"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by Carolyn62 on 2007-09-02
Hello,
I hope I am in the right forum for this question.

I am upgrading my computer with a new motherboard, processor, memory, graphics card, SATA drive, and case.

Hmmmm, let me start over. I am having a new computer built and want to reuse my 40Gb IDE linux drive, and old 60Gb IDE windows drive (it will be reformatted to be used as a scrap drive for another program) after mirroring it to the new SATA drive. It now boots into GRUB and works well.

The new motherboard has 2 IDE connectors. 1 of which will be used for the optical drive (DVD) and hopefully the 2nd will be with the 60Gb scrap drive with the 40Gb linux drive daisy chained to it.

My question is this: Will it work? Will the SATA drive boot into Grub and find the linux Drive?

Thank You,
Carolyn

P.S. My OS is Win XP pro and I use Ubuntu Dapper 6.01

---

### Post by logos34 on 2007-09-02
I'm not sure how Dapper (over a year old now) is going to respond to all that new hardware.  At the very least you may have to fiddle with the networking and install new graphics driver/reconfigure X server.  I wouldn't count on this setup working 'out of the box', but then again I've seen stranger things happen...I'd seriously consider a fresh install of Feisty.

If you stick with dapper:

You have to manually install grub to the sata drive and edit your boot files to reflect the new locations.

If you are imaging the XP pro partition from the 60GB drive to the new sata, you might want to also install the windows bootloader (via the recovery console on the XP cd) on that drive before you write grub to it, just to make sure everything works ok before you do anything else.  When you are satisfied XP boots and works ok in its new environment, [use the ubuntu live cd to overwrite the windows bootloader on sata drive]("http://ubuntuforums.org/showthread.php?t=224351").  You also need [edit your grub config files]("http://users.bigpond.net.au/hermanzone/p15.htm") to point to the new locations.   After this is done you should be able to boot to grub on the sata drive and from there choose either windows or linux.

Remember to put the ubuntu IDE drive on primary master and the old windows IDE drive primary slave.  

Post back if you have any more questions.

---

