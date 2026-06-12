---
title: "Laptop seem unable install or boot any flavor of linux"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by execrator777 on 2008-01-25
Ok, so I am relatively experienced and knoledgeable ubuntu user since Dapper. I recently ordered a brand new laptop from sager with a blank hard drive, with the intent to run gutsy + compiz, so it's pretty top of the line. Here are the specs:
Intel Core2Duo T7300 processor
 SiS968 core logic chipset
1gb ddr2 sodimm ram

*** Phoenix Bios rev 1.04 8mb SPI Flash ROM*** If i had known it came with this I never would have bought it

SiS M672 integrated video

i have more but i think thats all that is relevant.

So anyways, I'm using the 64 bit alternate install cd.  As soon as I begin the install, the familiar "Loading linux kernel" progress bar completes, and then gives the following message:

[28.053627] PCI: Cannot allocate resource region 0 of device 0000:00:09.0

And then nothing.....

I have also tried booting BackTrack 3 from usb, as well as 32 bit alternate install. Not a single successfull lnux boot. However, i installed bootleg vista, and everything is fully functional. Ugh. So any additional information you need about the laptop will have to be garneded using windows tools, which I unforunately have not maintained my knowledge on. Please, Please Help me!!! I'm having the sinking fear that This laptop is locked to vista, shich essentially makes it a $2000 paperweight for me.  Thanks!

---

### Post by Mikecore on 2008-01-25
> **execrator777 said:**
> Ok, so I am relatively experienced and knoledgeable ubuntu user since Dapper. I recently ordered a brand new laptop from sager with a blank hard drive, with the intent to run gutsy + compiz, so it's pretty top of the line. Here are the specs:
Intel Core2Duo T7300 processor
 SiS968 core logic chipset
1gb ddr2 sodimm ram

*** Phoenix Bios rev 1.04 8mb SPI Flash ROM*** If i had known it came with this I never would have bought it

SiS M672 integrated video

i have more but i think thats all that is relevant.

So anyways, I'm using the 64 bit alternate install cd.  As soon as I begin the install, the familiar "Loading linux kernel" progress bar completes, and then gives the following message:

[28.053627] PCI: Cannot allocate resource region 0 of device 0000:00:09.0

And then nothing.....

I have also tried booting BackTrack 3 from usb, as well as 32 bit alternate install. Not a single successfull lnux boot. However, i installed bootleg vista, and everything is fully functional. Ugh. So any additional information you need about the laptop will have to be garneded using windows tools, which I unforunately have not maintained my knowledge on. Please, Please Help me!!! I'm having the sinking fear that This laptop is locked to vista, shich essentially makes it a $2000 paperweight for me.  Thanks!

At this point is could be anything. there are several boot option you can try that disable things like ACPI, or  video options. At the very beginning of the boot process you 
can give these. Second I did have a problem with an HP laptop that was bad ( brand new out of the box  something to think about ). Third until you learn more about linux I would stay away from 64bit. try contacting the manufacture about a BIOS update that could help. It did for my HP laptop

---

