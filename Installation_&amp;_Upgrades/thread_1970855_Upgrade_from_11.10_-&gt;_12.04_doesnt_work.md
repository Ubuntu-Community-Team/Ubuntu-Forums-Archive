---
title: "Upgrade from 11.10 -&gt; 12.04 doesnt work"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by kape80 on 2012-05-01
Hi,

I upgraded my system to 12.04 a couple of days ago. And when the system boots up it is just blank, nothing happens. I dont know really in what way to start. Does anyone has any idea? I try booting up with another kernel at grub and then I can get part of the system back up, but not usable. 

It seems that the system totally freezes, I cannot hit ESC key to see what is happening. When the system should start it just freezes. Any ides?

Thanks

---

### Post by kc1di on 2012-05-01
Give us a little more information.
What type of Video Card does your machine use?

What type of install is it WUBI or regular?
Does the live cd work?

---

### Post by kape80 on 2012-05-01
> **kc1di said:**
> Give us a little more information.
What type of Video Card does your machine use?

What type of install is it WUBI or regular?
Does the live cd work?

Actually it doesnt get black, it gets the purple color all over the screen (11.10 colors). I made the upgrade from inside my running Ubuntu 11.10, so it should really work fine I think. And I dont have any special installation at all of what I can see. My videocard is ATI Radeon 9550, and I am running on a Gigabyte motherboard with AMD-64 bit CPU.

---

### Post by bcbc on 2012-05-02
Use the boot option 'nomodeset': [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Once booted go to additional-drivers and install a graphics driver, if one is available.

---

### Post by mejoe2 on 2012-05-02
I too am experiencing a similar issue.  Here is my boot-repair log: [http://paste.ubuntu.com/959090/](http://paste.ubuntu.com/959090/)

I noticed that even holding down the shift key while booting does not load GRUB. As the original poster, I upgraded from 11.10 to 12.04.

---

### Post by kape80 on 2012-05-03
> **bcbc said:**
> Use the boot option 'nomodeset': [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Once booted go to additional-drivers and install a graphics driver, if one is available.

I have tried this and it doesnt seem to work. The system wont boot at all. Do you know any other idea of what is bugging the system up?

---

### Post by kape80 on 2012-05-03
> **kape80 said:**
> I have tried this and it doesnt seem to work. The system wont boot at all. Do you know any other idea of what is bugging the system up?

I start to think this problem is caused by something else than the graphics part. I have an SSD-disc. 
And from the small logs I have seen in safemode start before everything stops responding, the system cant reach my harddrive (SSD) /dev/sdb1.
Any ideas around this?

---

### Post by BlastXng on 2012-05-03
> **kape80 said:**
> I start to think this problem is caused by something else than the graphics part. I have an SSD-disc. 
And from the small logs I have seen in safemode start before everything stops responding, the system cant reach my harddrive (SSD) /dev/sdb1.
Any ideas around this?

I would whole heartedly agree.. I was running 11.10 very well..

16GB RAM
ATI Radeon HD 6800
Quad Core AMD Phenom II Black Edition.

After the upgrade I reboot and I get just the splashscreen and the Ubuntu symbol.. Nothing ese.. I leave it like that for up to 10 minutes.. 

Tried recovery console. What a joke. It also locked.. 

I had a stable system and it ran great.. now I'm not sure how I'll get this corrected.. This has to be more that just a graphics card..:evil:

---

### Post by bcbc on 2012-05-04
[One of the upgrade guides]("http://askubuntu.com/questions/110477/how-do-i-upgrade-from-10-04-or-11-10-to-12-04") I saw recommended removing custom drivers prior to upgrading, and then reinstalling them afterwards. I can't really comment on this since I've never used custom graphics drivers. But it might be possible to do this after the fact.

---

### Post by zaentzpantz on 2012-05-04
My "upgrade" boots to the GRUB menu, shows the Ubuntu splash screen, then tells me "your screen, graphics card and other devices are not recognised" and gives me the command prompt on a black screen.
I've been with Ubuntu for a year (11.04, 11.10) and never had any trouble with the graphics (ATI Radeon H3000) or desktop.  
Reverting to earlier versions of Ubuntu via the GRUB choices gives the same problem. None of the shortcut keys make any change.
I've been forced to rely more and more on Windows XP since Ubuntu 11.10 was introduced and the printer stopped working. I use a lot of multimedia editing programmes and the Ubuntu programmes can't compete with the Windows ones (eg TMPGEnc), so this was the last straw. It's been an interesting 12 months with Ubuntu but not being a programming professional means that I need to revert to Windows just to get jobs done, and as from last night I now have an empty NTFS formatted partition instead of the EXT3 one and no sign of Ubuntu anywhere on the system. 
Relief!

---

### Post by KMJones1 on 2012-05-04
ME TOO!!
It has been a complete disaster upgrading from 11.10 to 12.04. It all downloaded and installed but on re-start I get Grub offering "Ubuntu with Linux 3.2.0.24-generic" or with recovery mode, and earlier versions. 
None of these work. 
Recovery mode shows "Cannot open root device "sda1"".
This sort of nonsense drives people back to Windows, which actually works!
Obviously the upgraded had not been properly tested for real people.
So I downloaded the ISO and that runs off the CD fine.

---

### Post by kape80 on 2012-05-04
> **KMJones1 said:**
> ME TOO!!
It has been a complete disaster upgrading from 11.10 to 12.04. It all downloaded and installed but on re-start I get Grub offering "Ubuntu with Linux 3.2.0.24-generic" or with recovery mode, and earlier versions. 
None of these work. 
Recovery mode shows "Cannot open root device "sda1"".
This sort of nonsense drives people back to Windows, which actually works!
Obviously the upgraded had not been properly tested for real people.
So I downloaded the ISO and that runs off the CD fine.

Okej, sounds interesting. Did your fresh install work fine you mean? Because it seems that I have the same problem as you, it wont find the root. If your install works fine after doing a fresh install I could give it a go to...

---

### Post by mörgæs on 2012-05-06
The short answer to many of these questions is: Don't upgrade, though the system encourages people to. Few people can comprehend how huge a task an upgrade is - just the number of changed packages and configuration files should make you doubt that it is doable.

If you're lucky and it works: Congratulations, problem solved. If it doesn't, go for a fresh install in stead of trying to troubleshoot.

---

### Post by mips on 2012-05-06
> **mörgæs said:**
> The short answer to many of these questions is: Don't upgrade, though the system encourages people to. Few people can comprehend how huge a task an upgrade is - just the number of changed packages and configuration files should make you doubt that it is doable.

If you're lucky and it works: Congratulations, problem solved. If it doesn't, go for a fresh install in stead of trying to troubleshoot.

+1

Actually need a sticky advising people of this and also recommending they rather use the alternate cd image.

There seems to be plenty problems related to people upgrading and also some with the ubiquity installer on the livecd and when people use the alternate cd they have success.

---

### Post by mörgæs on 2012-05-07
Thanks, but I already have a sticky in this forum.

Feel free to suggest, if parts of it need to be rewritten.

---

### Post by kape80 on 2012-05-13
I have now tried a fresh install, but now I directly end up in grub rescue mode. Any ideas?

Thanks

---

### Post by KMJones1 on 2012-05-13
I've now done a new install from the ISO file disk and all works fine.
The Grub thing seems unavoidable, but it offers a normal mode as well as the Rescue mode so I just hit Enter and it goes into the normal mode OK.

---

### Post by mörgæs on 2012-05-13
For Grub problems this thread is worth searching:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

