---
title: "[SOLVED] What is it with my hard drives?"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by embolalia1187 on 2008-09-02
I suppose we'll go with the full story.
Back in May, my Windows PC gave me the click of death: Hard drive failure. So I pulled a hard drive from an old work computer (old as in Win98-era), and installed Ubuntu 64-bit. It worked amazingly for just long enough for me to get everything working just the way I wanted. Then it stopped seeing the hard drive when I turned on the computer (no boot disk found, it said). It would still see the old drive if I hooked it up (for clarity, it was not hooked up when I was running under Linux. I tried disconnecting the Linux drive and connecting the WinXP drive; it would see it but only boot partly, since the drive was bad). I assume from this that it was just that the hard drive had somehow failed. (and yes, I made sure it was properly plugged in first)

So I ordered a part from Amazon to put my old Linux laptop HD in, and turned on the computer. It saw it, got partway through the boot, and crashed. Then I remembered that this was 64-bit, and the laptop was 32. (I assume this is why it crashed) So I pulled out the disk I'd used a few months before to install Linux on this computer, put it in, and tried to install.

Then it told me that my hard drive was bad, or that my CD drive was bad, or that I should move to a cooler location. I was in an air conditioned room at about 73. I tried swapping out the CD drive for another one. Same message. I tried multiple times to install, allways with the same message, and I think generally at either 26% or 76%, (or something else) I can't remember. Oh, and the CD had been burned on the same drive that was first trying to read it, so speed shouldn't have been a problem.

So after I admitted defeat, I threw the computer in a closet. Come today, my father replaces his computer in his office, as well as that of one of his employees. I take both home in hopes of putting Linux on one. Some quick specs: comp 1 has a Pentium 3 @500MHz, and 384MB of RAM, among other things, and had been running XP. Comp 2 has an AMD Duron @1300MHz. I swapped a RAM chip from the first to give it 400-odd MB of RAM. (Now you see why they were replaced). Anyway, when I tried the first (before taking out the RAM), it gave me a ton of lines of errors, something about devices not working, I don't know. I figured it wasn't worth bothering with, so I pulled out a RAM chip to give comp 2 enough to run the live CD. And I did, ran the installer, and got the exact same error message that I'd been getting on the 64-bit computer I talked about in the first paragraph, at 26% installation every time. This hard drive had been working not five hours before under XP. The 32-bit CD had been burned maybe a few weeks before in anticipation (and to use the higher-speed 'net at work).

So what gives? What are the chances that every single one of these hard drives would fail so quickly, or that both installer disks would be bad in the same way (without having checksum problems)?

Both disks were Ubuntu 8.04LTS, desktop edition.
I much prefer Linux to Windoze, especially Vista. And so with the impending XP blackout coming soon (our techies say they can get it until January, I think), we're trying to find alternatives. And since the office computers are used for Internet access and as text-only terminals to a Unix server, Linux is the perfect option. In theory.

Thanks in advance.

---

### Post by Shazaam on 2008-09-02
So you are trying to install Ubuntu on the Duron machine and it hangs at 26%? I would say that its not a drive problem. Have you tried the "Alternate Install" version yet? People who have problems installing the regular version of Ubuntu have good luck with that.
You might want to update the bios and replace the motherboard battery on the Duron if you get it working.
As for the other drives yes, there could have been a problem with them. Other things could have been the culprit too. Bad house wiring/voltage spikes, low/dead motherboard battery, defective motherboards, buggy bios, loose/bad cables, etc.

---

### Post by embolalia1187 on 2008-09-03
Well, I tried the alternate on the Duron, to no avail, even with a new battery. I tried again on the 64-bit computer, with the live disk, got to 94%, and got a click of death. So I put a new hard drive in it, tried again, and am now posting from a brand new installation of Ubuntu! w00t!:)

So, my problem never actually got solved, but it decided to work on one computer, and that's good enough for me.

But to the person who inevitably finds this via search later: try alternate install CDs, and make sure to check the checksums before you burn, and again on the burned disk. 

Anyway, thanks for the help!

---

