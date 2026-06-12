---
title: "[SOLVED] Cannot re-install Gutsy?!"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by geekygirl on 2007-12-30
Gday,

After much reading and searching I have not yet been able to find a decent answer to my issue with a re-install of Gutsy. 

System Specs:

Intel Core 2 Duo 2.4GHz CPU
Gigabyte GA-P965-DS3P(Pro) Mobo
3.0GHz GEIL 800MHz RAM
Seagate SATAII 160G HDD 
Evga 8800GTS KO ACS3 320M GPU

I have just replaced the old HDD which had the previous install of Gutsy on it which displayed some rather interesting issues - an installation of WOW with Wine that used a copied folder runs perfectly on my A8JS laptop yet I get error messages of the game being a corrupt install and the Blizzard repairer suggesting a re-install (even though exact same install folder is being used on said laptop with no worries!). Ok that was the start of the woes..

When a re-install of WoW failed to rectify the problem I opted for a fresh install of Gutsy. I am using the Ship-It CD's not downloaded ones either and have tried a couple of copies all with the same result!

Firstly I boot into the Live CD no drama's, I then have a look in Computer and see my HDD sitting there mounted and awaiting usage, I can even browse the files on the HDD through the Live CD. Now when I try to run the installer everything runs nicely until the installation gets to "Scanning Devices" with Gparted. It just hangs here...I walked away for nearly 20 minutes and it was still hanging!

So the HDD is recognized and mounted...yet it hangs on GParted?.....

Next thing I did was start to play around with the hardware side of things - I discovered I had 1G stick of dodgy RAM so have since replaced that with another one and let MemTestx86 run - and there were no errors. I have unplugged and replugged all hardware (had to do some cable management anyways!) I have now got a brand new HDD sitting in the PC..yet it still hangs....

I have run fdisk and this is the output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81fd81fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156286976    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

so the disc is recognized. But yet each time it hangs on install - yet on the previous install of Gutsy everything worked well...hmmm

The only thing that has changed in that time was the system was previously overclocked and therefore I had played inside the BIOS...could there be a setting in the BIOS that is causing this issue? I read briefly before someone mentioned about the floppy disk causing issues with Gparted? (I do not have a floppy disc on the PC) Could changing the settings in BIOS solve this dilemma?

For interests sake I have reinstalled Vista Home Premium which didn't miss a beat..*sigh* lol and subsequent checks of the HDD surface and sectors has revealed no errors....:confused:

Sorry for the long post but I figure the more info I can tell about my problem the more it might help someone to assist me in finding an answer!

Thanks in advance :-D

---

### Post by geekygirl on 2007-12-30
Ok well thanks if you had a read...I have solved my little problem...seems the issue lies within the BIOS - inside the Floppy had been enabled when I had reset the BIOS and Gparted was hanging because it was looking for a Floppy rather then just heading straight for the HDD..

Guess it also helps to think out aloud sometimes :-D

---

