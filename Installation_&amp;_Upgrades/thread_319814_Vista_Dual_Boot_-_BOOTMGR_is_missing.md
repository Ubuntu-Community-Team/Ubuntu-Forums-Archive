---
title: "Vista Dual Boot - BOOTMGR is missing"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by Pyrocuror on 2006-12-16
I've cruised through several other Vista dual boot threads, but none of the solutions seemed to work for me.

The long and short of it:

I'm trying to dual boot Dapper and Vista on two seperate SATA drives; two fresh installs.  Vista wasn't detected during the Dapper install apparently because of the new way it is loaded.  So I added an entry for Vista in grub, but I get "BOOTMGR is missing" when I select my Vista entry in the grub boot menu.

Dapper is on SATA0 (sda) and Vista on SATA1 (sdb).

Here is what menu.lst looks like for grub:
title Windows Vista
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

---

### Post by ramzai on 2007-01-03
Same problem here (except for that I have IDE, not SATA).

---

### Post by dkartik on 2007-01-29
I'm having the same issue, with an IDE drive.  I've got my Edgy install as my master hard drive, and the vista install set as it's slave.  I installed Vista first, then Ubuntu, so they're both practically brand new, but I can only get into Ubuntu right now.

---

### Post by ChrisCorben on 2007-02-03
Not a Ubuntu user, but I thought the following may be relevant.

I installed Fedora Core 6 on a brand new Dell e1505. When I set up grub, it offered the usual "other" for Vista. FC6 worked fine, but when I tried to boot Vista, it came up with the "BOOTMGR is missing" message and I got nowhere. 

But it turned out to be disgustingly simple! Vista boots from the C: drive as you'd expect, but the C: drive is actually /dev/sda3 - there are two smaller partitions defined prior to the one which ends up being drive C:. The first of these isn't a normal, formatted partition, but the second is (called Recovery) and Grub chose it (/dev/sda2) to try to boot. All I did was alter the /boot/grb/grub.conf file (it might be /boot/grub/menu.lst for you) so the line which read

rootnoverify (hd0,1)

now reads

rootnoverify (hd0,2)

and everything works as it should!

Hope this helps...

---

### Post by Herman on 2007-02-03
Has anyone tried [EasyBCD]("http://neosmart.net/dl.php?id=1")?
If so does it work well for you or if not what problems have you had?

Just interested. 

Regards, Herman :)

---

### Post by davidgarcin on 2007-02-09
I had the same problem with BOOTMGR being missing, but I found the solution.  When I installed Vista, I already had XP and Ubuntu set up on the same hard drive.  For some stupid reason, the Vista installer put bootmgr and c:\Boot on my XP partition (I guess maybe because it was (at the time) the first NTFS partition on the hard drive).

Of course, when I tried to boot the Vista partition from GRUB, it couldn't find bootmgr.  Once I discovered the problem, all I had to do was copy/paste the bootmgr and the Boot folder from the root of my XP partition to the root of my Vista partition, and everything worked fine.

Here's my menu.lst entry for Vista, if anyone's interested:
```
title 		Windows Vista
rootnoverify 	(hd0,0)
makeactive
chainloader 	+1
```

Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.  Hope that helps.

-Dave

---

### Post by scannerdarkly on 2007-02-10
try to move the positioning of your drives.  try to make your ubuntu drive your slave drive.  Then reinstall grub.

---

### Post by ramzai on 2007-04-02
Finally realized what my problem was.

My system before I installed Ubuntu:
hda: Windows XP
hdb: Windows Vista

For some reason Vista puts its boot manager, file called bootmgr on another partition that it's being installed to - in my case, it was WinXP partition on hda.

So, when I installed Ubuntu on hda wiping out WinXP, it wiped out bootmgr too. Moral: when you format ntfs/fat32 partition, look for bootmgr / other Vista stuff on this partition (this is another _really weird_ decision from MS).

Hope this helps.

---

### Post by davidgarcin on 2007-04-02
ramzai:  I really hope you didn't just find that out now... if you read my post above you'll see that I had the same discovery as you - just a month and a half earlier.

---

### Post by Herman on 2007-04-02
Thank you davidgarcin, for finding that out and sharing your knowledge and ramzai for confirming it. 
I'm afraid I was a little slow about this too. I have now added a link to this thread with a quote from davidgarcin to the [Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") error collection and troubleshooting  area under [[COLOR=#000000]Error messages from Windows.[/COLOR]]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors")
Your information might help people looking there too. I hope that's ok, let me know if it isn't or if you would like it edited in any way. Thanks again.

Regards, Herman :)

---

### Post by davidgarcin on 2007-04-02
yeah, that looks fine, Herman.  Glad I could help.
-Dave

---

### Post by ramzai on 2007-04-03
> **davidgarcin said:**
> ramzai:  I really hope you didn't just find that out now... if you read my post above you'll see that I had the same discovery as you - just a month and a half earlier.
I have a bad habit of forgetting to track my posts after a week or two after I have posted)) And another bad one, forgetting to look at other posts while posting what I think is 'finally solved'.

Thanks.

PS. Quite funny we have expressed the idea in almost the same words))

---

### Post by sorlok_reaves on 2007-05-16
This may be an old post, but there's an elegant solution, which I'll present for posterity:

Note that I installed Vista first (on partition 3) and then Ubuntu second (on partition 2). Therefore, the above comment of setting rootnoverify correctly is also necessary.

1) Restart with the Vista DVD and choose "Repair your computer". Windows will find itself, and restart.
2) Boot from the Vista DVD again and choose "Repair your computer" and then "Startup Repair". Vista will re-add the MBR to the *correct* partition this time, and restart.
3) Try reloading Vista from GRUB. It should work.

---

### Post by Computer Guru on 2007-05-16
An even nicer way:

Once Vista is up and running, just download and install [EasyBCD]("http://neosmart.net/dl.php?id=1") and select "Reinstall Vista MBR" from the Bootloader management. :)

You get the added benefit of [full Linux support]("http://neosmart.net/wiki/display/EBCD/Linux") too!

[IMG]http://neosmart.net/gallery/d/4958-1/Bootloader+Management.png[/IMG]

---

### Post by Encryptor on 2007-07-26
> **davidgarcin said:**
> 
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.  Hope that helps.

-Dave

In my case, I had a FAT16 partition at (hd0,0).
I installed Windows Vista on (hd2,1), which is the only NTFS partition.
I found that Vista's Boot folder had been installed on the FAT16 partition, even though it's not an NTFS partition.

I just had to adjust grub's menu.lst to boot from (hd0,0) and Vista is up and running.

---

### Post by MQMike on 2007-07-26
The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)
Uses EasyBCD

(Sorry,for some reason I didn't see some posts here (Computer Guru), but I'll leave this up anyway for reference.)

---

### Post by Seibikitei on 2007-10-07
> **sorlok_reaves said:**
> This may be an old post, but there's an elegant solution, which I'll present for posterity:

Note that I installed Vista first (on partition 3) and then Ubuntu second (on partition 2). Therefore, the above comment of setting rootnoverify correctly is also necessary.

1) Restart with the Vista DVD and choose "Repair your computer". Windows will find itself, and restart.
2) Boot from the Vista DVD again and choose "Repair your computer" and then "Startup Repair". Vista will re-add the MBR to the *correct* partition this time, and restart.
3) Try reloading Vista from GRUB. It should work.

I know this topic is a little old but I've run into the same problem.  I've tried this but the problem I'm having when running the Vista DVD is that Windows won't find itself.  It tells me to load driver for my haddisks which I do but even after loading them it still won't show up in the operating system list.  I hope I'm just having a brain fart and missing something pretty obvious.  Any ideas on what might be causing this or what other options there are for fixing the missing boot MGR thing?

If anyone needs more info let me know and will gladly provide.

---

