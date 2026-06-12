---
title: "Security Boot Fail screen on Acer Aspire E15"
date: 2017-01-13
forum: Installation &amp; Upgrades
---

### Post by seltaeb7 on 2017-01-13
Hello.

A few months ago I bought a new Acer Aspire E15 and wiped out the windows installation. I then proceeded to swap the internal hard disk (used a 240GD SSD) and installed ubuntu 16.04. Things went relatively smoothly, so much so that I do not remember much about the process other than letting the installer choose the [I guess standard] partitioning of the disk (1 small EFI,ESP partition, 1 big root partition [ext4], and a swap partition as big as RAM [8Gb].

Anyhow, things were working well enough for me to use the computer on a regular basis. However, after not touching the computer for about 3 weeks (winter break) I picked it up this past Monday to prepare some documents (google docs). While working on them, the updater told me about, well... updates and I proceeded to let it do its thing. After it was done it told me something about not being able to download all of the required packages; however, I didn't really pay attention to the actual one that failed to download and kept working on my google docs. Also, I got a pop up that prompted me whether I wanted to reboot at that moment, or at a later time. Given that I needed to finish my documents I chose the latter option.

Once I finished preparing the pdf versions of the docs I proceeded to reboot via ```
$sudo reboot
``` as I have done many times before. Only this time, a Security Boot Fail screen appears whenever the computer gets past the Acer screen that is presented when the computer powers on. After pressing enter I am presented with an error dialog that reads something along the lines of 

Boot Device Missing or Boot Failed.
Insert recovery media and Hit any key
Then Select 'Boot Manager' to choose a new Boot Device or to Boot Recovery Media.

After a little googling I plugged in my USB ubuntu live disk and installed boot-repair following the directions in [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

The 'recommended repair' option failed to restore access to my OS. I then tried 'purge grub' in advanced options with similar results. Finally, assuming that the reboot needed to be done because of a kernel upgrade, I tried the 'revert back to previous kernel' [or something like that] advanced option to no avail.

The URL address boot-repair reported back are

[paste2.org/D9ZzDPh5]("http://paste2.org/D9ZzDPh5") (recommended repair)
[paste2.org/sceE29dF]("http://paste2.org/sceE29dF") (purge grub)
[paste2.org/fwUmhggE]("http://paste2.org/fwUmhggE") (revert to previous kernel)

I can easily back up my data and attempt to reinstall Ubuntu, but I honestly want to avoid [if possible] the pain of having to configure the machine to my liking once again. If anybody can point me in the right direction I would truly appreciate it.

Best,

P.S. Sorry for such a long post.

---

### Post by oldfred on 2017-01-13
When you originally installed, did you set UEFI supervisory password and enable trust on the ubuntu/grub .efi files in the ESP - efi system partition from inside UEFI? You may have to reset if files changed?
Do you have newest UEFI from Acer. Older threads mention downgrading UEFI, but newer ones say upgrade to newest works.

 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 


 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
One of several with more details on trust:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)

---

