---
title: "Need to press power button twice to start ubuntu"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by J Caffrey on 2009-10-20
Hi Guys and Gals,
                Bear with me on this one and I'll try to explain.I have a Medion laptop (MD 96640) 3 gig ram 320 gb hd.I started using ubuntu at Hardy Heron with varying degrees of success progressively clean installing the newer versions as they arrived.I am now running 9.10 beta.This problem has been present with all versions.Right here goes:I shut down ubuntu completely,later on when starting up I push the power button and the machine begins to start before I even get to post there's an audiable "pop" from the computer and it switches off.If its on battery it remains off,if its plugged into the mains it does the "pop" thing,switches off and then after about 3-4 seconds starts up perfectly.If I'm on battery the next push of the power button starts everything normally.I have a tri-boot set up with XP and W7.If I power down from either of the windows installations the startup is perfect.:confused:

---

### Post by running_rabbit07 on 2009-10-20
I would almost recomend not starting ubuntu on that system until someone offers a good fix. It sounds like there is a major problem with how the OS controls the power supply during shutdown, or something along those lines.

---

### Post by philinux on 2009-10-20
Likely related to this. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201)
Have a look at the duplicates too.

I get loud thud on shutdown from my woofer.

[http://ubuntuforums.org/showthread.php?t=1289240&highlight=powersave](http://ubuntuforums.org/showthread.php?t=1289240&highlight=powersave)
See post 5.

---

### Post by J Caffrey on 2009-10-20
I think running_rabbit07 is on the right track.The "pop" doesn't seem to come from the speakers but more from the side of the computer and seems to be related to the control of the power.I'm a bit worried now in case I'm doing damage.

---

### Post by philinux on 2009-10-20
Just reread your post. Stick with windows for now.

---

### Post by J Caffrey on 2009-10-20
Oh no,not death by windows!! Back to av updating,defragging files...blah blah.Has anyone got a suggestion?Philinux what do you think is happening?

---

### Post by philinux on 2009-10-20
> before I even get to post there's an audiable "pop" from the computer 

This is before any os is loaded then?

---

### Post by J Caffrey on 2009-10-21
Yes I don't even get to the post screen.

---

### Post by KrazyPenguin on 2009-10-21
Have you tried other flavours of linux , eh???

Puppy linux is good for older hardware, and quite speedy.
It's a little harder to setup, but once you do the whole o/s is booted into ram and it just flies.

I'm not trying to push you away from ubuntu, but maybe trying a few different distros may be your answer.
(since we dont want damage to your computer and we don't want you going back to that "other" o/s)

Good luck!!!!

:guitar:

---

### Post by J Caffrey on 2009-10-21
Another thing I noticed.After using Part Magic in the default setting(load into ram and eject disc) when I exit and start later on I get the very same problem.Does that help anybody?

---

### Post by psyke83 on 2009-10-21
> **KrazyPenguin said:**
> Have you tried other flavours of linux , eh???

Puppy linux is good for older hardware, and quite speedy.
It's a little harder to setup, but once you do the whole o/s is booted into ram and it just flies.

I'm not trying to push you away from ubuntu, but maybe trying a few different distros may be your answer.

Good luck!!!!

:guitar:

How is a one-year old, Core2Duo laptop with 3GB ram considered old, by any stretch of the imagination? Your answer has no relevance to the poster's original question.

J Caffrey,

This could be an ACPI issue that only affects Linux. Have you updated to the latest BIOS?

Visit: [http://www.medion.co.uk/](http://www.medion.co.uk/)

Click "Drivers & Updates" and choose your laptop model. There's a recent BIOS update listed (1.0J, 27/8/2009).

You may want to check your kernel log for any errors or warnings, too:

```
$ dmesg | grep -i error
$ dmesg | grep -i warn
```

---

### Post by psyke83 on 2009-10-21
> **J Caffrey said:**
> Another thing I noticed.After using Part Magic in the default setting(load into ram and eject disc) when I exit and start later on I get the very same problem.Does that help anybody?

If you use Partition Magic and then reboot into XP or 7, does it spontaneously shut down, or is it still a problem that only happens with Ubuntu?

This sounds like a BIOS issue to me. The next time you boot (under the condition that you expect it to shut itself off), try to boot into Ubuntu's recovery menu instead, and try to look at the kernel log for any useful information.

You should also reset your BIOS settings (after updating to the latest version).

P.S. I don't recommend that you use Partition Magic, it's caused problems for me in the past when dealing with drives with Linux partitions (corrupted partition tables). GParted is superior - it's on the Ubuntu Live CD and there's also a GParted Live CD available from their website.

---

### Post by scokem on 2009-10-21
OMG - someone who has the exact same laptop as me!  Nice bit of kit isn't it :)

Now - down to business, the issue you have described is something that I've noticed since the very beginning of owning mine and it doesn't just happen when using Ubuntu - I dual boot  with Vista and it just seems to randomly happen at times, even before I had set up dual booting.  Annoying as it is, I don't believe it's software related but more of a hardware issue that I've never managed to figure out.  I was gonna take mine back but I decided to live with it in the end - it is only a minor issue after all.

Sorry I couldn't bring good news, but be sure to post anything you manage to find out.

---

### Post by psyke83 on 2009-10-21
> **scokem said:**
> OMG - someone who has the exact same laptop as me!  Nice bit of kit isn't it :)

Now - down to business, the issue you have described is something that I've noticed since the very beginning of owning mine and it doesn't just happen when using Ubuntu - I dual boot  with Vista and it just seems to randomly happen at times, even before I had set up dual booting.  Annoying as it is, I don't believe it's software related but more of a hardware issue that I've never managed to figure out.  I was gonna take mine back but I decided to live with it in the end - it is only a minor issue after all.

Sorry I couldn't bring good news, but be sure to post anything you manage to find out.

Have you tried the latest BIOS, though?

---

### Post by scokem on 2009-10-21
> **psyke83 said:**
> Have you tried the latest BIOS, though?

Nope.  Never been one for doing BIOS updates.  I've just checked and saw that they've got a new version available though:

27.08.2009 - Version: 1.0J    (Mine is currently version 1.0E)

The only person I've known to do a BIOS update was my bro (ckempo) on one of his laptops because he was experiencing a known problem which was fixed in the update and when he did it, part of his keyboard stopped working and he had to do a full reboot which luckily resolved the issue but it's scared me away from wanting to do it in case I brick my hardware.

How about you guys - have you ever done it and experienced issues and would you recommend doing it?

---

### Post by VMC on 2009-10-21
> **scokem said:**
> Nope.  Never been one for doing BIOS updates.  I've just checked and saw that they've got a new version available though:

27.08.2009 - Version: 1.0J    (Mine is currently version 1.0E)

The only person I've known to do a BIOS update was my bro (ckempo) on one of his laptops because he was experiencing a known problem which was fixed in the update and when he did it, part of his keyboard stopped working and he had to do a full reboot which luckily resolved the issue but it's scared me away from wanting to do it in case I brick my hardware.

How about you guys - have you ever done it and experienced issues and would you recommend doing it?

I've updated all my computers BIOS. Laptop, desktop, optical drive firmware. No problems at all. The only concern would be power failure right in the middle of flashing. If you live in an area that has power issues, be aware - battery backup.

---

### Post by vade on 2009-10-21
If the machine doesn't even post, then it can't be Ubuntu at fault there. Ubuntu kicks in at the point when the BIOS turns execution to the grub bootloader - which happens only after the POST, not before or during POST. Of course I might be horribly wrong about this if your laptop's BIOS design is something I've never encountered before.

But it sure makes things odd that Windows boots fine. Must be coincidence. Or then I'm wrong about the whole thing.

Edit: Oops, you never said that Windows boots fine.

---

### Post by psyke83 on 2009-10-21
Well, the original poster said that Windows boots/reboots fine, but the problem occurs for scokem in Windows as well.

This seems pretty obvious to be an BIOS/ACPI issue. If the hardware itself isn't faulty, then only a BIOS update will fix the issue.

---

### Post by mrboojive on 2009-10-21
> **VMC said:**
> I've updated all my computers BIOS. Laptop, desktop, optical drive firmware. No problems at all. The only concern would be power failure right in the middle of flashing. If you live in an area that has power issues, be aware - battery backup.

+1. I've updated the BIOS on several computers and never had any problems. In your situation, I would go ahead and do the update.

---

### Post by J Caffrey on 2009-10-21
Oh God,Bios updates really scare me.I don't mind messing with partitions bootloaders etc...At least being a laptop I won't have to worry about power outages will give it a look tomorrow.Its a lovely computer...don't want to bugger it up.

---

### Post by J Caffrey on 2009-10-22
I had a look at the bios update and the instructions say to run the exe from the vista os.Only problem with this is that I removed vista and have W7 rc1 and XP.Would it be ok to run the exe from either of these os's?

---

### Post by psyke83 on 2009-10-22
> **J Caffrey said:**
> I had a look at the bios update and the instructions say to run the exe from the vista os.Only problem with this is that I removed vista and have W7 rc1 and XP.Would it be ok to run the exe from either of these os's?

The instructions say Vista because your laptop probably does not officially support XP, and of course, Windows 7 didn't yet exist. I'm fairly sure that either OS will work fine (though you may need to execute with administrator privileges in 7).

Take extra care when updating the BIOS, of course. Don't interrupt the updating progress, ensure the power supply is connected and the battery inserted and charged.

You seem anxious about updating the BIOS for fear of damaging your laptop. It's not exactly working perfectly at the moment, is it? Check if your warranty is still in date before proceeding, perhaps. Most warranties will cover bad BIOS flashes, I'm sure.

---

### Post by J Caffrey on 2009-10-22
Here's the latest,I've updated the bios which went without a hitch but unfortunately the problem is still with me.Any more ideas? This is the result of the two terminal commands. The ACPI Warning might shed some light.
john@john-laptop:~$ dmesg | grep -i error
[   18.708607] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[  296.555147] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
john@john-laptop:~$ dmesg | grep -i warn
[    1.268842] ACPI Warning: \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer 20090521 nspredef-940
[   10.904042] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.

---

### Post by psyke83 on 2009-10-22
Take a look here: [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

Note that those instructions are for GRUB1. 

For GRUB2, you can edit /etc/default/grub and add any boot options to this line:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Afterwards, run:
```
$ sudo update-grub
```

Alternatively, when you reboot, pressing the "e" key while the kernel line is highlighted, add the parameter, and press "ctrl + x" to boot.

---

