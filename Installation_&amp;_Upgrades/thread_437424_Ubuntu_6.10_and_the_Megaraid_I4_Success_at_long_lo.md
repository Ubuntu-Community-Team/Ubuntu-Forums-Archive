---
title: "Ubuntu 6.10 and the Megaraid I4 Success at long long last."
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by slicksurf on 2007-05-08
This is continuation from this thread [http://ubuntuforums.org/showthread.php?t=352858&highlight=megaraid]("http://ubuntuforums.org/showthread.php?t=352858&highlight=megaraid")

I've post here as I have some success now and would like others to decypher why this method worked....

Well, I flashed the old megaraid firmware back into the card, and it got detected by ubuntu, but I forgot to setup a logical array needed to get the thing to work. So I set a single drive raid 0, and booted ubuntu. Guess what? It worked........ Ubuntu loaded it as single device /dev/sdb (sda is my sata boot drive) and even more interesting is that this is not using the legacy driver, but the megaraid_mbox module. So the next task is to setup a raid 5 array and see what comes up.
I now have 3 400gb drives in raid 5 configurarion set in the bios and verfied with the windows xp megaraid power user utility. Fingers were crossed and I rebooted into ubunto................
\\:D/ it worked!!!!! 800Gb /dev/sdb1 cool!
So I now have a Dell CERC card which is a Reflashed Megaraid i4 flashed with N661 firmware from LSI working as Raid 5 hardware array un Ubuntu 6.10. I'm glad I didn't give up. I must admit though its pretty slow in both windows and ubuntu ~ 6Mbytes/s anyone with any more info?
Next is an upgrade with another 400Gb drive to fill the card, and to get an ubuntu raid management console.

I hesitate to add that I take no responsibility over your data or your cards if you wish to try this, I'm just posting my findings, I'll test this setup more extensivly later on. 

Saim

---

### Post by bubba on 2007-05-15
So did you loose your raid config when you did this?  Also, where did you get your firmware.  I heard that going back a version on this card would cause it to loose support for large disks but it appears that is not the case.  

Here are my stats on the newest firmware:
# hdparm -Tt /dev/sda1

/dev/sda1:
 Timing cached reads:   752 MB in  2.00 seconds = 375.87 MB/sec
 Timing buffered disk reads:   46 MB in  2.00 seconds =  23.04 MB/sec

---

### Post by slicksurf on 2007-05-15
Hi,

Interesting command hdparm, it has some useful features, cheers for that. I'm not aware of any large disk problems, and my array has been working from when I last posted. However, I haven't stored huge amounts of data on it yet. What exactly was the size limitation?
The firmware I used is directly off the LSI website.
[http://www.lsi.com/files/support/rsa/N661.zip]("http://www.lsi.com/files/support/rsa/N661.zip")

Heres my stats from hdparm.
/dev/sdb1:
 Timing cached reads:   2988 MB in  2.00 seconds = 1493.98 MB/sec
 Timing buffered disk reads:  172 MB in  3.02 seconds =  56.88 MB/sec

Not really sure whats going on with the speeds, are these reading realistic. 
The only way I've confirmed everything is working is by reading and writing to the array in Windows and Ubuntu, and cross checking, but I need to dump a huge amount of data and pul the pug for a real test. The LSI management console in windows shows everything to be ok too, with each of the 400Gb drives acknowledged,and the logical array healthy..

Ubuntu's dmesg shows the following:-
[17179584.816000] scsi[2]: scanning scsi channel 1 [Phy 1] for non-raid devices
[17179587.812000] scsi[2]: scanning scsi channel 2 [Phy 2] for non-raid devices
[17179590.820000] scsi[2]: scanning scsi channel 3 [Phy 3] for non-raid devices
[17179590.824000] scsi[2]: scanning scsi channel 4 [virtual] for logical drives
[17179590.824000]   Vendor: MegaRAID  Model: LD 0 RAID5  763G  Rev: N661
[17179590.828000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179590.832000] SCSI device sdb: 1562836992 512-byte hdwr sectors (800173 MB)
[17179590.832000] sdb: Write Protect is off
[17179590.832000] sdb: Mode Sense: 00 00 00 00
[17179590.832000] sdb: asking for cache data failed
[17179590.832000] sdb: assuming drive cache: write through
[17179590.832000] SCSI device sdb: 1562836992 512-byte hdwr sectors (800173 MB)
[17179590.832000] sdb: Write Protect is off
[17179590.832000] sdb: Mode Sense: 00 00 00 00
[17179590.832000] sdb: asking for cache data failed
[17179590.832000] sdb: assuming drive cache: write through
[17179590.832000]  sdb: sdb1

Which is a lot more than I got with other firmware versions. Switching between Dell and LSI firmware was painless, not going to try the other way round.
The array wasn't initialized before the firmware degrade so I can't advise if data loss might occur.

It would be nice if anyone else who gave up on the megaraid would give it a go again with this new information, as it appears to be a very cheap very feature rich hardware raid card.

Saim

---

### Post by bubba on 2007-06-22
FWIW, You are correct.  I downgraded my firmware and it is detected out of the box with 7.04.  

ALSO, you can downgrade your firmware without losing your configured raid sets.  That being said, you need to make sure that before you downgrade, you include all possible drivers that megaraid might use (7.04 is using megaraid_mm and megaraid_mbox) because the old driver you were using (in my case megaraid from hoary) will not be the driver that will be used when you downgrade.  Your raid sets will remain intact after a downgrade, but you may not be able to boot because of not having the right megaraid driver.

Kudos for you figuring this out.  I'm actually giving up on hardware raid opting for a single drive for OS/Data and a drive for backuppc data and rsyncing of critical information.  That way I have backups of how things used to be and not just a mirror.

---

### Post by jaymode on 2007-06-27
Ok if I understand this correctly, the DELL version of this card will work in Feisty but I just need to downgrade the firmware to the LSI version?

---

### Post by Linuturk on 2007-09-13
I'm working on getting Ubuntu 7.04 server installed on a PowerEdge 650, with the same RAID controller. Any tips on flashing the bios? Do you have to flash from windows?

---

### Post by Linuturk on 2007-09-13
Turns out there was dust in the floppy drive, and it wouldn't read the disk right. After I got that fixed, I booted to the floppy, flashed the linked firmware, and the installer picked up perfectly. I had to leave before it finished formatting the drive. I'll update tomorrow.

---

### Post by d3ez on 2008-02-06
This appears to be an older post. I am currently trying to do the same. Ubuntu is great and I'd like to use it on this 1600sc that I'm using for my desktop. However, no drives as you guys have mentioned. I hear flashing the bios is what gets this working. However, how do I locate and old version of the bios to flash it with? I went to Dell for it but all they have is the newest, latest, and greatest.

Anyone have any links to it by chance?

---

### Post by d3ez on 2008-02-06
Sorry,
I missed the initial link way above. I had to make a few mods to my means of getting this done. Here is what I did:

1) download [http://mygrimoire.org/files/BCE66203.exe](http://mygrimoire.org/files/BCE66203.exe) (this is the dell CERC ATA 100 flash untility) I only used it to create the bootable disk.
2) download [http://mygrimoire.org/files/N661.zip](http://mygrimoire.org/files/N661.zip) (the same as provided above)
3) after creating the disk with BCE66203.exe replace the 622.rom file (on the floppy) with the 511GEN.rom file from the .zip file (both will not fit on a floppy :-/)
4) edit autoexec.bat so it reads: pflash 511GEN.rom
5) pop it into your 1600sc and reboot, follow the instructions, and reboot with Ubuntu disk

Worked like a charm for me. This is probably more difficult that creating a boot disk from just the .zip file, but I was having issues. Probably lack of sleep and not thinking straight, but the above works as well.

Cheers!
D

---

### Post by antidrugue on 2008-06-05
I confirm that the above mentioned method works perfectly for Ubuntu 8.04.

On a Dell PowerEdge 1600SC (with a CERC ATA/100 RAID controller), I did the following:

1) Downloaded the "floppy maker" from Dell: [http://ftp.us.dell.com/ide/BCE66203.exe](http://ftp.us.dell.com/ide/BCE66203.exe) (from which I generated the floppy to flash the firmware).

2) Downloaded the firmware (v.6.61) from LSI:
[http://www.lsi.com/files/support/rsa/N661.zip](http://www.lsi.com/files/support/rsa/N661.zip)

3) Replaced the firmware on the floppy (as explained in the post above -- replace the ROM file and modify autoexec.bat).

4) Flashed the controller firmware by booting from the floppy.

All data on the disks part of the RAID was left untouched and Ubuntu 8.04 now detects the disks automatically.

---

### Post by JAF0 on 2008-06-29
> **d3ez said:**
> Sorry,
I missed the initial link way above. I had to make a few mods to my means of getting this done. Here is what I did:

1) download [http://mygrimoire.org/files/BCE66203.exe](http://mygrimoire.org/files/BCE66203.exe) (this is the dell CERC ATA 100 flash untility) I only used it to create the bootable disk.
2) download [http://mygrimoire.org/files/N661.zip](http://mygrimoire.org/files/N661.zip) (the same as provided above)
3) after creating the disk with BCE66203.exe replace the 622.rom file (on the floppy) with the 511GEN.rom file from the .zip file (both will not fit on a floppy :-/)
4) edit autoexec.bat so it reads: pflash 511GEN.rom
5) pop it into your 1600sc and reboot, follow the instructions, and reboot with Ubuntu disk

Worked like a charm for me. This is probably more difficult that creating a boot disk from just the .zip file, but I was having issues. Probably lack of sleep and not thinking straight, but the above works as well.

Cheers!
D

Hello

Thanks for the fix for this problem, im tryin to get the files but the links are broken and lsi.com doesnt respond!
Can anyone mail me the files or put them somewhere so i can DL them?

Thanx

//JAF0

---

### Post by antidrugue on 2008-06-30
> **JAF0 said:**
> 
Can anyone mail me the files or put them somewhere so i can DL them?


Take a look at my previous post: I mentioned working links (directly from Dell and LSI websites) for both files you are looking for.

---

