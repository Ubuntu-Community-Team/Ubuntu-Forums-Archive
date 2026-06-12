---
title: "Stuck in grub"
date: 2020-12-01
forum: Installation &amp; Upgrades
---

### Post by terraclast on 2020-12-01
I was using a Win 10/Ubuntu 20.04 dual boot. I was having a lot of trouble installing wifi drivers in 20.04 and a friend suggested I remove 20.04 and revert to 18.04. 
I deleted the partition and recovered it to my Win partition and when I went to do the bootrec /fixmbr I found myself in grub and have only the faintest idea of what’s going on.
I surfed around and tried a couple things but nothing worked. 
From what I’ve read, the Ubuntu partition was the master boot, because it was the last os I installed. 
Additionally, I do not have a Win 10 disk or stick because it’s what came with the computer and didn’t realize this would happen if I “just remove the dual booted os” and therefore didn’t think it necessary to create a recovery image. I do have the boot sticks for both 20.04 and 18.04. If I can’t get back the Win boot, that stinks but I’ll live just find with an Ubuntu box, though that would be disappointing. 
Any help would be greatly appreciated. 
Thanks in advance

---

### Post by CelticWarrior on 2020-12-01
Welcome.

Reverting to a previous release is, generally speaking, bad advice.

You should have asked here about the WiFi drivers.

In any case installing a different release could and should have been done using the same partitions. > [COLOR=#000000]I deleted the partition and recovered it to my Win partition[/COLOR] Why exactly? And what comes next is even worse: "[COLOR=#000000]bootrec /fixmbr" is applicable ONLY to old BIOS installs. Any new computer with Windows preinstalled is UEFI and installed in UEFI mode since 2012 and Windows 8. I would say then that "only the faintest idea" is an exaggeration.

> [/COLOR][COLOR=#000000]From what I&#8217;ve read, the Ubuntu partition was the master boot, because it was the last os I installed.[/COLOR]
[COLOR=#000000]
If you think so you've been reading old stuff, applicable to BIOS, NOT applicable to UEFI.

> [/COLOR][COLOR=#000000]I do not have a Win 10 disk[/COLOR][COLOR=#000000]
That's the least of your problems. You can make a Windows installation pretty much the same way you do for Ubuntu. Very easy to do from any Windows computer, just follow the instructions at Microsoft's download page and yes, you should have one when performing such alterations as installing another OS, just in case you need repairs and whatnot.

That said, you may still be able to boot Windows. Open UEFI settings > Boot and try selecting "Windows bootloader manager" instead of Ubuntu. If Windows is fine in spite of what you did it should boot directly. 

Helping you with the WiFi would have been very likely a trivial thing to do. Now, after mistakes pilling one previous mistakes, it'll be way harder, but we can try.
In order to understand where exactly you are now you can boot a live session, 18.04 or 20.04 doesn't matter which one, with internet connection - if the WiFi doesn't work use a LAN cable temporarily or USB tethering from your phone - and then [/COLOR]https://help.ubuntu.com/community/Boot-Repair follow the 2nd option instructions. Do NOT apply any fix for the moment, just "create a bootinfo summary" and post here the results.

[COLOR=#000000]Meanwhile go make your Windows media in case you need to repair or reinstall Windows.
 [/COLOR]

---

### Post by terraclast on 2020-12-01
I greatly appreciate your reply. 
When I say bios, I didn’t necessarily mean bios, but was using the term for its general meaning.  I’m able to get into and around there. 
The above post is the first post I made in this forum and, as it goes without saying I’m quite new here and to having to dive deeper into Ubuntu or Linux more generally, I was a little intimidated to join if I could help it, regarding asking for wifi help. But yes, you’re absolutely right, I should have asked about the driver help and now I’m in much deeper trouble. I am here now and I’m really to learn and atone for my mistakes. 
I don’t have a cable long enough to reach my router, which is why I needed wifi in the first place and setting up in the room with the router isn’t really an option. 
I don’t have tethering/internet sharing enabled on my phone plan, so that’s tough, too. 
I will work to make a windows bootable stick, seeing how to boot a live session, read and learn from the link you gave me, and learn about creating a bootinfo summary. 

I sincerely thank you for taking the time and energy to point me in the right direction. I really am in this to learn above everything else. So again, thanks.

---

### Post by oldfred on 2020-12-01
Some basics.
Always have good backups. With Ubuntu your data & configuration is more important as system reinstall is relatively easy.
If you do not have good backups, your data is not considered as important. Drives/systems do fail and then what do you do?

Have repair recovery or live installer for current version of every operating system you have.

Understand difference between UEFI & BIOS. 
Many vendors still call UEFI as BIOS. But Microsoft has required vendors to install Windows in UEFI boot mode on gpt partitioned drives since Windows 8 released in 2012.
Possibly too much info & many links on UEFI in link in my signature. Also Acronyms at end of link for terms you may not understand & links for more info.

So not be afraid of terminal. But be sure of  source so you do not get some dangerous rm (delete) command.
Most of us may post commands that should be copy & pasted as typos can cause issues. 
Reason for terminal is there are many flavors with different gui and then doing it graphically is different in every flavor. But terminal is the same.

---

### Post by terraclast on 2020-12-01
Thank you, oldfred. I’ve started reading your linked post and will proceed to go through the whole thread, though it might take a bit.

---

### Post by terraclast on 2020-12-02
After studying and thinking about the issue and the loaf of a breadcrumb that was left that was repeatedly mentioning UEFI.  I went back in and was able to boot into Windows from there.  I will continue to work my way through oldfred's signature link, though, you're right, that is a lot of information, and I don't understand much of it.  So much to learn.  

I really want to thank both of you for your time and knowledge.  I really is appreciated.

---

### Post by Impavidus on 2020-12-02
> **terraclast said:**
> 
I don’t have tethering/internet sharing enabled on my phone plan, so that’s tough, too. 

I don't know about phone plans in your part of the world, but on bad days, when my laptop has trouble connecting to wifi, I hook up my phone to my computer and access wifi via my phone, which has a slightly better wifi receiver. No need for any mobile data and no need for the phone company to know about it.

---

### Post by oldfred on 2020-12-02
A lot of my link is on specific issues and/or specific brands of systems. Those you can skip or skim read just to have an idea about if you run across something similar.
For example if you do not have nVidia, you can skip all the info on nVidia video issues.

---

### Post by terraclast on 2020-12-02
Heh, I had to read several of the parts a couple times and I was still left scratching my head.  That being said, I learned a couple things and will definitely come back to your thread, probably over and over, as time permits.  Thanks again!!!

---

