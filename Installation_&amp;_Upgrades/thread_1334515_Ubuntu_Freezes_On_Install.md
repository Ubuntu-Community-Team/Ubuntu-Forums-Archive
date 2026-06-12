---
title: "Ubuntu Freezes On Install"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by NoOneRuleZ on 2009-11-22
I have tried the following and they all give me the same error:

[LIST=1]
[*]Live CD
[*]Install (Normal Mode)
[*]Install from Windows
[/LIST]
I have tried the following and it has worked:

[LIST=1]
[*]The installation of Ubuntu on a virtual machine.
[/LIST]
This is the error:

[LIST=1]
[*]I insert the DVD into my DVD drive.
[*]I select Install.
[*]The logo (that fades in and fades out) appears.
[*]After some time, the logo disappears, and I get a lot of white text.
[*]The following appears: "Starting remaining crypto disks..."
[*]The computer appears to freeze.
[*]The DVD drive stops reading the DVD.
[/LIST]
I used the same DVD for the Virtual Machine, so there is nothing wrong with the DVD.

Here is my PC Specifications

CPU: Intel Pentium 4 HT 2.80 GHZ
RAM: 4 GB
GFX Card: ATI 4650
[]("http://pastie.org/710291.txt")

---

### Post by NoOneRuleZ on 2009-11-22
Whoa. To the third page already? :(

---

### Post by NoOneRuleZ on 2009-11-27
Amg. Someone help plawks. :(

---

### Post by NoOneRuleZ on 2009-12-03
*Feels forgotten.

---

### Post by NoOneRuleZ on 2009-12-09
*Gives up all hope of fixing this problem.

---

### Post by NoOneRuleZ on 2009-12-14
*Wonders if he can get to the second page alone.

---

### Post by NoOneRuleZ on 2009-12-28
Oh, that's real nice. Excellent support Ubuntu!

---

### Post by Urhungry on 2009-12-28
I'm having a similar problem, but mine dosent even start the install. I can't get any help either.

---

### Post by avtolle on 2009-12-28
If either or both are trying to install on an encrypted drive, it is my memory that the alternate install iso needs to be used.

---

### Post by jSalv on 2009-12-28
Please:

Ensure that your DVD-drive is 4x speed or higher (one can assume that nowadays anyways...),
That your HD is not set up to AHCI mode, and if it is, set it to IDE mode (I had to do this),
In your BIOS, that a password is not required upon boot/start-up, this may be a cause for freezing upon accessing the HD.

Other things you may consider trying, however I doubt have anything to do (merely for performance, freezings):
De-fragging your hard-drive,
De-fragmenting it,
Unplugging external USB devices/jacks,
Going offline (unplugging ethernet cables/wireless adapter/wireless card/putting off the wireless interruptor in your comp),
Running anti-virus software.

If any of that works, hooray. If they don't, sorry!

---

### Post by Urhungry on 2009-12-28
Never mind I fixed my problem, it was just being extrmely slow.

---

### Post by NoOneRuleZ on 2010-01-08
> **avtolle said:**
> If either or both are trying to install on an encrypted drive, it is my memory that the alternate install iso needs to be used.

Nope, it's not an encrypted install. :| I'll try the alternate install, but for some reason, I have a feeling it won't help.

> **jSalv said:**
> Please:

Ensure that your DVD-drive is 4x speed or higher (one can assume that nowadays anyways...),
That your HD is not set up to AHCI mode, and if it is, set it to IDE mode (I had to do this),
In your BIOS, that a password is not required upon boot/start-up, this may be a cause for freezing upon accessing the HD.

Other things you may consider trying, however I doubt have anything to do (merely for performance, freezings):
De-fragging your hard-drive,
De-fragmenting it,
Unplugging external USB devices/jacks,
Going offline (unplugging ethernet cables/wireless adapter/wireless card/putting off the wireless interruptor in your comp),
Running anti-virus software.

If any of that works, hooray. If they don't, sorry!

Yes, my DVD-drive has a write speed of 12x, and a read speed of 48x. I will try your other suggestions.

EDIT: Other suggestions didn't work either. :/

---

### Post by Greg17 on 2010-01-09
Hej

I have exactly the same problem as described in the first post. This happens wether the hard drive on which I wan to install Ubuntu is plugged or not.

I tried to install Fedora as well, and the problem seems to be the same (freeze when the logo is on during loading)

It would be great if someone could help!!

---

### Post by Greg17 on 2010-01-09
Same thng with Linux Mint, and when trying with Ubuntu 9.04, it blocked on the first graphic screen, with the arrow in the iddle which doesn't move with the mouse.

Still no ideas???

---

### Post by NoOneRuleZ on 2010-01-10
I think I have found the culprit. I looked at my BIOS configuration, and I believe this may have something to do with it:

[quote=BIOS]
Primary Master: -
Primary Slave: DVD Drive
Secondary Master: -
Secondary Slave: Hard drive
Tertiary Master: -
Tertiary Slave: -
[/quote]

FYI, I get the same problem with all Linux distributions.

---

### Post by Greg17 on 2010-01-10
Ok, I solved it: I read somewhere on this forum about someone having the same problem (very deep in the pages!!) 
He removed his Wireless card and it worked, so I did the same and I could boot Mint live (but then I installed Ubuntu)

Hope it can help...

---

### Post by NoOneRuleZ on 2010-01-10
> **Greg17 said:**
> Ok, I solved it: I read somewhere on this forum about someone having the same problem (very deep in the pages!!) 
He removed his Wireless card and it worked, so I did the same and I could boot Mint live (but then I installed Ubuntu)

Hope it can help...

:O! Wireless card, eh? Hmm... Actually, I did install one recently... I'll check and see if it works.

EDIT: I removed it, and it worked! Thank you!

---

### Post by NoOneRuleZ on 2010-03-14
Well, now, I want to use the Internet while booting into Linux. Any ideas why the loading screen freezes while starting Linux? The wireless card works perfectly in Windows, so I don't believe it's a hardware conflict.

It's a Zonet ZEW1605 PCI wireless card.

---

### Post by ElRonHubbard on 2010-06-27
I am having a similar problem with a realtek Zonet ZEW1605 wireless card. I installed this card and driver and it worked once and then when i started my computer again, it froze during boot. If I remove the PCI card it starts normally. SOMEONE HELP i need this wireless card.

---

