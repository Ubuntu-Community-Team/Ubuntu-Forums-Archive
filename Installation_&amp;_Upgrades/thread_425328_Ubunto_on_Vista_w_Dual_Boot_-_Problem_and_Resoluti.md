---
title: "Ubunto on Vista w/ Dual Boot - Problem and Resolution"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by widomenhardt on 2007-04-27
My son has a Vista dual core machine, and I thought that I'd put Ubuntu on it so I could use it as a server from my office when he's at school. And if I need it, he could be playing his on-line games in Firefox (actually, not, because I failed miserably to install Java so he could play runescape on Firefox/Ubuntu, but that's another story).

I had recently installed Ubuntu 6.10 as dual-boot on an XP machine in our kitchen and that works very well (after some issues with the graphics card, where garlik42 on this forum helped me out, thanks).

So I put the Ubunto CD in, and it did not give me the automatic repartitioning option - just reformat and manually repartition. This is a Dell machine, and it already had 3 partitions (one of them has the recovery on it, I guess). So I added another partition, but wait... you need 2 (swap and /), so I added an extended partition, and within it, those two. Then I let the installer do its work - 160GB disk, so it took a but of time, but all seemed to go well, and Ubuntu works... except for that it is really not all that fast - it's actually slower than a vmware virtual machine with debian that I run hosted on an XP machine with lesser hardware. I need to check whether Ubuntu takes advantage of the dual core or not.

Anyway, all was well until my son came back to play a game and wanted to boot to Vista. It complained, and suggested some sort of repair operation, and when I agreed, it went away... for hours.... overnight... nothing happened. My son was in tears, and went around shouting I HATE UBUNTU !!! I HATE UBUNTU !!! Not only can he not play his games, it's his birthday tomorrow (11th), and his grandfather's present is a new PC game!

I reverted to on-board graphics, and I had the same behavior. There were three disks that came with the Dell box. One was a pretty cool hardware test utitilities DVD, and I ran through many of those, all was fine. There was a Vista recoveryDVD, and it would boot from there, but quickly go to the good old black screen, and sit there.  For reasons unknown there was also a Vista upgrade DVD, and it would boot from there, and go to the black screen, again without return. Nothing worked.

Then I popped an old XP Upgrade CD in there, because I had used its repair facility once before. This got me a step further - it never got to repair, just to the stop screen with error code 0x0000007B. 

There is a Microsoft knowledge base about it. One of the suggestions was to put the drive into another computer. So I did, and of course at first the computer didn't recognize the drive at all, apparently this SATA thing had to be enabled in the bios of the other computer, but when I started it up after that, Windows (XP in this case) started chkdsk on it, and repaired some stuff, and I could read the drive fine. I then put it back into the other computer, and now Vista and Ubuntu both boot and work as advertised. 

I am not sure there is a lesson here - Ubuntu is great and free, but it definitely still requires some doing - the two times I tried a dual boot install so far (which allows me to recklessly generalize) resulted in problems that even a smart but non-engineering person like my wife would not have been able to handle.

Most important, though, my son will actually have a Happy Birthday !!!  :) 

Wido

---

### Post by steveneddy on 2007-04-28
Not knowing that much about these new Vista machines and the screwy BIOS installed, can someone elaborate on why this solution worked and how to install Ubuntu as a dual boot option on a Vista Preinstalled PC?

I have a couple of friends and one neighbor that are interested in the solution to these questions.

-SE

---

