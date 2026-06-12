---
title: "Boot Trouble"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by OutlandishKnight on 2011-12-19
I recently installed Ubuntu 11.10 (64 bit) on an HP DV9000 laptop. I've now decided I love Ubuntu and am pretty determined to migrate this laptop to it completely, but I've had a few teething troubles and a pretty annoying boot problem which is what I want to address here. The problem seems to be quite a common one, but it has a twist in my case compared to other examples I've found. 

It worked fine at first (I rebooted several times for various reasons with no trouble), but the problem started when I installing a load of updates (it wasn't connected to the internet at first install, so it didn't include any in the first place). Now, when I try to boot I get a purple screen. If I turn it off and on with the power button, I end up in Busybox with an initramfs prompt, and have to wait for a load of error messages (something about "killed process 9) before I can exit and get into the actual OS. After shutting down (through the OS rather than the power button) it starts from purple screen again next time.

As I say, I've already found that it's not uncommon, but none of the other fixes have worked for me. Here's the tricky part, though: it's still happening even after a clean reinstall. There was one difference between the two installations. The second time, I downloaded updates while installing in the hope they'd work properly that way, so that explains why the problem was there from the start this time. In theory, I could solve it by reinstalling again without them, but I don't much fancy having an OS I never dare install any updates for. 

My laptop's spec is: 

HP DV9655ea
160GB HDD (was originally 320GB in the form of two 160GB drives)
2GB RAM
Processor: AMD Turion 64 X2 Mobile Technology TL-60
Nvidia Geforce 8400M GS (I know this can be problematic with Ubuntu).

---

### Post by Mark Phelps on 2011-12-19
> **OutlandishKnight said:**
> ...but I don't much fancy having an OS I never dare install any updates for.

Understand your concern ... as there's no "system restore" capability that can get you a working system back.

Don't have a solution to the updates problem, but you should look into using Clonezilla to image off your Ubuntu install before making updates.

What can easily become hours of frustrating work can be changed into 10 minutes or less -- if you have a "before" image to restore.

---

### Post by oldfred on 2011-12-19
Did you install the nVidia driver that Ubuntu recommends, yet? If not from grub menu you need to add nomodeset.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
[COLOR=DarkRed]Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place[/COLOR]
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

---

### Post by OutlandishKnight on 2011-12-19
Thanks a lot to the both of you. I will try the nomodeset business tomorrow, and Clonezilla sounds like an incredibly useful precaution against any future problems. I definitely like Ubuntu on the whole, but this stuff has really made me miss Windows' system restore!

I did install the Nvidia drivers first time, but not since I did the clean reinstall. From some of the things I found while Googling, I even wondered at first if it was getting the drivers that caused the problem, but that now seems not to be the case. Anyway, I'll get them again, but via the other stuff you describe and see if that gets things running smoothly again.

---

### Post by OutlandishKnight on 2011-12-20
Alas. Early signs seemed good, but sadly I seem to have gotten nowhere so far. When I changed it to "nomodeset" it booted up without the need for Busybox, so that seemed to be an improvement. I got the Nvidia drivers, but the problem persisted so I changed it to nomodeset permanently. Since it bypassed busybox and the related error messages before, I thought this would at least give an improvement, but this time it's done nothing. Purple screen, reboot, busybox and signal 9 errors all the same.

Back to square one. Also, a couple of extra details I'm not sure how I was foolish enough to leave out yesterday:

When I turn it on, it spends ages just showing the HP logo before doing anything else. That applies to both the purple screen and the busybox when I've turned it off and on afterwards.

It goes to the grub menu every non-purple-screened time. I have to choose my OS from there, and then the whole thing with busybox and initramfs happens.

---

### Post by oldfred on 2011-12-20
Can you go into BIOS and see if it is showing memory correctly? Perhaps some other setting in BIOS, but laptops typically have few settings.

Have you run the memory test from the grub menu? Or perhaps  the BIOS is still looking for the other hard drive?

---

### Post by OutlandishKnight on 2011-12-20
All memory shows up in BIOS, and I've run the memtest an it gives a clean bill of health.

I don't think the BIOS can be searching for the other hard drive, as I booted a few times with just one before the problem turned up and there was no delay. Hanging on the logo only started when the other symptoms did.

---

### Post by oldfred on 2011-12-20
Did you reset BIOS to look for a floppy drive and you do not have one or some other device. 

If it is slow at BIOS it just about has to be hardware related somehow as BIOS knows nothing about what operating system is on the drive, it just jumps to the MBR to start the boot process. Someone once left a CD in drive and it was busy reading that before system worked.

If you can get into Ubuntu what does smart data on hard drive show? It is in Disk Utility, click on drive and on the right is smart status. All I know is it should be green, but it has lots of detail.

---

### Post by OutlandishKnight on 2011-12-21
Ah, well in that case I think I've got to the bottom of the BIOS part. By what I suppose must be just a big coincidence, at almost exactly the same time as the other problem turned up my optical drive stopped working. I haven't gotten around to replacing it yet because I've been preoccupied with the boot trouble. From what you say, I'm now presuming the BIOS part is because it's searching for that and not detecting it.

While I'd obviously still like to get the boot itself to go smoothly if possible, this is good news too. It will at least be rather more bearable if that bit can indeed be sorted separately in the meantime.

As for the HDD, all seems fine there. The Smart status is green, and everything in the smart data is either green or N/A.

---

### Post by OutlandishKnight on 2011-12-22
Update: My DVD Drive has randomly decided to start working again. Don't know how long it will last, but even if it stops again in five minutes it has allowed me to observe the following:

Doesn't hang at BIOS anymore (so presumably that was indeed the cause of that problem).

Didn't go through Busybox when I last booted up. Is it possible the initramfs error could also be down to failing to detect hardware?

It does, however, still go to the purple screen until I turn off and on, and then still goes to grub where I have to manually select the OS. So presumably those parts are still a seperate problem. Still, things are improving!

---

### Post by OutlandishKnight on 2011-12-22
Also, there's now an option at grub for "previous linux versions." That was there first tie, disappeared when I reinstalled with updates from the start, and has now suddenlyy turned up again. I did install a few more updates, so I'm guessing it's from that. Just thought I'd mention it as it's better to give a bit too much detail than too little with things like this.

---

### Post by OutlandishKnight on 2011-12-22
Update 2: Well this is interesting. Rebooted a couple of times and went absolutely fine. Then the DVD drive packed up again and the problem returned in full. Is it possible the whole thing could be down to the DVD drive not being detected? 

Because the problem coincided with the updates and manifested itself in the software, and I didn't even notice the drive had gone right away, I'd assumed it couldn't be a hardware issue. It now seems very likely I assumed wrong.

---

