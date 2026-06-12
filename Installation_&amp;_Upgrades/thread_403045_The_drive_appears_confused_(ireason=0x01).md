---
title: "The drive appears confused (ireason=0x01)"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by senor_smile on 2007-04-06
I'm trying to just run ubuntu 6.06 livecd on a couple machines, and I'm getting essentially the same error on everyone of them when trying to load: 

hda: cdrom_pc_intr: The drive appears confused (ireason=0x01)
irq185: nobody cared (try booting with the "irqpoll" option)
handlers:
[<c0252040>] (ide_intr+0x0/0x200)
[<f88ba330>] (usb_hcd_irq+0x0/0x60[usbcore])
Disabling irq #185


This will keep repeating over and over and will never actually load the OS.  I tried it on two nearly identical machines.  specs:

MB: Asus p5ld2-vm
512 MB ram
3.2 GHZ Intel P4
80 GB HD (Sata)

I have been using ubuntu for a couple months on my laptop without a hitch, but I still am very basic in what I know, and I don't know what to troubleshoot to try getting the livecd, at a minimum, to run.  obviously, I'd like to run ubuntu on the machines, getting rid of Windows XP.  

Thanks for any help, in advance, that anyone can provide.

---

### Post by daynah on 2007-04-06
[I had this problem also!]("http://ubuntuforums.org/showthread.php?t=302516")

(psst mods... maybe you'll merge the threads? :) )

We all seemed to have an ASUS motherboard. Not sure if you do also, but whether you do if you don't, try what the other's did and...

1) Update your BIOS

2) Turn off SMART monitoring.

Now, I don't know how to do those things. I've never updated my BIOS and my motherboard doesn't have SMART monitoring. Silly fancy-pants people.

Now I can't say this'll work... Dad and I got an answer on this soon before Feisty was scheduled to come out, so we decided just to wait for feisty. But that seemed to be the earlier consensus.

Have fun and good luck! :)

PS, did it later say "nobody cares"? I thought that was the funniest part...

---

### Post by senor_smile on 2007-04-06
Yes, look at the whole error I posted.  It says, nobody cared.  How hilarious is that?  Anyway, smart monitoring is turned off and I already tried updating the rom bios.  They motherboard is about a year old and it the updater uflash.exe that I'm supposed to run from a dos disk gives an error saying it can't find the bios.  I would assume that the motherboard being so new, there wouldn't be significant updates to the bios.  ??????

I would really like to use ubuntu on these machines.  Surely someone knows what these errors mean.

---

