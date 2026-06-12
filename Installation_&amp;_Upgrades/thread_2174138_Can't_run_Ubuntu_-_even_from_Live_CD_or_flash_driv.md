---
title: "Can't run Ubuntu - even from Live CD or flash drive"
date: 2013-09-13
forum: Installation &amp; Upgrades
---

### Post by andrewkirk on 2013-09-13
My PC is set up to dual boot Windows XP and two versions of Ubuntu - 10.04 and 12.04 32 bit.
Recently both the Ubuntu versions stopped working. It starts booting but then at about the point that I think the X server starts, it freezes on a gray screen with the mouse pointer frozen in the middle of it.

I thought I'd try reinstalling 13.04 over one of them to fix it and made a LiveCD flash drive, but when I boot using that it just freezes on a blank screen. I assume that the fact it also freezes in that case means it can't be anything corrupt in my installed versions or the hard disk.

Windows still works OK but is a bit unreliable and it always asks me if I want to install the latest software updates when I log off, no matter how many times I say yes. That suggests to me that there is some fault occurring at logoff time that prevents proper installation of those updates (usually Windows only asks that question every few weeks). 

So my tentative theory is that there's some hardware problem that Windows manages to work around, suffering only a few problems, while it brings any version of Ubuntu crashing down. I can run the command line in failsafe mode without trouble, but I can't get it to even run failsafe graphics

I attach the Xorg.failsafe.log file that was written when I tried to boot up in failsafe mode on one of my installed Ubundtu versions. It says something about there being no screens. If it were only crashing on that version I'd try removing all my xorg.conf files and detting the Xserver to reconfigure from scratch. but the LiveCD version should be doing that and it still crashes.

I would really appreciate any suggestions. If I can work out what the hardware problem is, I can buy a new bit and fix it. If it turns out to be software instead then maybe I can fix that if I can find out what it is.

Thank you.

---

### Post by sudodus on 2013-09-13
You might be right that the graphics chip is failing. But it is worth trying a few things before giving up.

If the computer is old, 13.04 might not have good graphics drivers for it. If you really want to test if the graphics works in a fresh system, try to boot 10.04 LTS or 12.04 LTS from a live CD/DVD/USB drive.

- Please specify the computer, or at least cpu, ram (size) and graphics chip/card. It makes it easier to give good advice.

- What graphics driver are you using?

- Have you installed any wifi card? Any other hardware or proprietary driver that might interfere with the graphics?

- And finally: What about the Windows XP updates? What happens if you don't wait till log off, but try to perform the updates manually while logged in?

---

### Post by andrewkirk on 2013-09-13
The PC has CPU Intel Dual CPU 3.00 GHz; 3GB RAM; NVidia GEforce 210 Graphics Card.

The graphics card is new. I bought it to replace a previous NVidia card, thinking it might fix the problem, which had been going on before the card switch. It didn't fix it.

I think the Ubuntu drivers being used are the NVidia proprietary ones that can be loaded through the Ubuntu admin menus. But I can't really check that because I can't boot up the installed versions of Ubuntu.

There are no wifi cards and no onboard wifi (it's a fairly old desktop). I can't think of any other unusual hardware drivers in place. The setup is really pretty straightforward, with no tweaks.

Thanks for the suggestions about trying an old Ubuntu Live CD and trying the Windows updates while logged on. I'll try them both and see if they give me any clues.

---

### Post by andrewkirk on 2013-09-13
I tried the Windows update and got the message saying the following couldn't be installed. It doesn't sound very important, or very illuminating about the hardware, unfortunately:

[INDENT]Security Update for Microsoft .NET Framework 1.1 SP1 on Windows XP, Windows Vista, and Windows Server 2008 x86 (KB2833941)[/INDENT]

---

### Post by sudodus on 2013-09-13
I see. I was too quick to blame the graphics card. It might be something else related to the graphics in the chain all the way to the screen. Have you tested the physical connections (remove and re-connect the card, the cables etc)?

I'm awaiting the results from your test with the old Ubuntu CD.

The problem with Windows update is probably unrelated (but we can not be sure).

---

### Post by grahammechanical on 2013-09-13
I have the Nvidia GT220 (210) and it runs Ubuntu 13.04 very well. In fact I am at this moment running 13.10 using xmir without any problems. But then again I am using the Nouveau open source video driver. I stopped using Nvidia drivers more than ayear ago. I found them too buggy.

Can you get a Grub boot menu and select Recovery Mode>Resume? That may get you to a desktop using Nouveau. As regards the live session you might try loading it with one of the F6 options such as nomodeset. Or even a combination of the F6 options. I have had to do that in the past when testing Ubuntu ISO images.

With problems like this some have recommended making sure that all the components are seated properly. It could be issues related to overheating. Perhaps through dust and fluff.

Regards.

---

### Post by VMC on 2013-09-13
The Xorg log file looks ok, try looking at both "/var/log/kern.log" and "/var/log/syslog" for any errors. You can paste them back here as you did with the Xorg log file.

---

### Post by andrewkirk on 2013-09-14
> **VMC said:**
> The Xorg log file looks ok, try looking at both "/var/log/kern.log" and "/var/log/syslog" for any errors. You can paste them back here as you did with the Xorg log file.Thank you. I attach the two files. I couldn't understand most of what's in there, but there was one interesting line in the syslog file: "nvidia: module license 'NVIDIA' taints kernel." A tainted kernel sounds bad.

Hmmm. It won't upload the logs as attachments because they exceed the limit of 19.5KB. So instead I've uploaded them to Google Drive and put links to them:

[kern.log file]("https://docs.google.com/document/d/1KZx6FTGldzx0J-P7NFe-mZSdzQGxVvvh6pWlom-2Ph4/edit?usp=sharing")
[syslog file]("https://docs.google.com/document/d/1gzS6gxkaTQQBLBdH4IkXuNfg9E9HpfGxUHxYQH4aOl8/edit?usp=sharing")

---

### Post by Bucky Ball on 2013-09-14
*Thread moved to **Installation & Upgrades**.*

---

### Post by VMC on 2013-09-15
That "tainted" message is just informational. You had a disk failed message, but I guessing that's from an improper shutdown because later it reported recovered the journal. Nothing else stands out. How about dmesg? 

Try running bootinfoscript(see my blue link). Just to see what partitions and boot info is reported.

---

### Post by coldraven on 2013-09-15
The Windows problem is a bug.
[http://www.theregister.co.uk/2013/09/13/microsoft_reissues_september_patches_after_user_complaints/](http://www.theregister.co.uk/2013/09/13/microsoft_reissues_september_patches_after_user_complaints/)

---

