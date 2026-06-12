---
title: "GRUB doesn't start, computer keeps restarting (XP and ubuntu 9.04 dual boot)"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by fahadghani on 2009-12-20
Hi
Please help me with a problem with dual boot: Windows XP and Ubuntu 9.04 on separate HD partitions. I installed Ubuntu after XP and have three partitions: /boot, /root and swap (dont know if we even need that anymore, i last used linux during the Fedora Core 3 release :???:)

It was working fine for about 2 months before booting into windows started creating issues. Whenever i log into XP, somehow GRUB gets corrupted or something so that when i restart the laptop, it displays "Grub 1.5 loading..." and restarts again. This seems to go on in an infinite loop, restarting the machine again and again trying to load grub.

When I re-install grub, everything is fine (I am able to see the Grub menu of ubuntu and windows and able to boot into both) until i boot into XP. XP works absolutely fine w/o any hiccups but the same problem resurfaces when i shut it down (or hibernate) and restart the machine: the same infinite loop. And I hv to re-install the grub again. 
Somehow, logging into windows is corrupting Grub. 

I am using a Dell vostro 1520:

[LIST]
[*]3GB DDR2 800MHZ 2 DIMM Vostro
[*]250GB 7200RPM SATA Hard Drive
[*]WINDOWS XP PRO SP3
[*]Intel Core 2 Duo Processor
[/LIST]
In case this is a specific hardware issue, which I don't think it is (i could be wrong though :confused:)

Please also find attached the **RESULTS.txt** file (using the Boot info script in this thread: [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)). This file was generated through Live session of ubuntu after the last grub corruption. 

I have seen a few similar threads in the forums but there doesn't seem to be a proper answer (i might have missed it somewhere perhaps). Please help!

Thanks for help!!

---

### Post by phillw on 2009-12-20
> **fahadghani said:**
> Hi
Please help me with a problem with dual boot: Windows XP and Ubuntu 9.04 on separate HD partitions. I installed Ubuntu after XP and have three partitions: /boot, /root and swap (dont know if we even need that anymore, i last used linux during the Fedora Core 3 release :???:)

It was working fine for about 2 months before booting into windows started creating issues. Whenever i log into XP, somehow GRUB gets corrupted or something so that when i restart the laptop, it displays "Grub 1.5 loading..." and restarts again. This seems to go on in an infinite loop, restarting the machine again and again trying to load grub.

When I re-install grub, everything is fine (I am able to see the Grub menu of ubuntu and windows and able to boot into both) until i boot into XP. XP works absolutely fine w/o any hiccups but the same problem resurfaces when i shut it down (or hibernate) and restart the machine: the same infinite loop. And I hv to re-install the grub again. 
Somehow, logging into windows is corrupting Grub. 

I am using a Dell vostro 1520:

[LIST]
[*]3GB DDR2 800MHZ 2 DIMM Vostro
[*]250GB 7200RPM SATA Hard Drive
[*]WINDOWS XP PRO SP3
[*]Intel Core 2 Duo Processor
[/LIST]
In case this is a specific hardware issue, which I don't think it is (i could be wrong though :confused:)

Please also find attached the **RESULTS.txt** file (using the Boot info script in this thread: [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)). This file was generated through Live session of ubuntu after the last grub corruption. 

I have seen a few similar threads in the forums but there doesn't seem to be a proper answer (i might have missed it somewhere perhaps). Please help!

Thanks for help!!

Hi,

Firstly, reset your Grub as detailed here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You'll be on grub legacy.

Then boot a couple of times into Ubuntu and check it works okay.

Then boot a couple of times into Win.

Then try Ubuntu again - I'm betting it will fail. If that is the case - it is a known problem caused by stuff in the windows system breaking the rules and over-writing the MBR.
Now, this should NOT affect grub legacy, but it sounds like it is.

The solution is a bit of detective work - but, let's see if that is the issue for you.

regards,

Phill.

---

### Post by fahadghani on 2009-12-20
Hi Phill
Thanks for the reply. Does legacy GRUB mean GRUB 1.5? I am using ubuntu 9.04, which uses grub 1.5. I have installed grub this way about 3-4 times. So, this doesn't seem to be working. =/ However, i m going to try it again and be back in a few minutes. :)

---

### Post by phillw on 2009-12-20
There are only two grubs ...  0.97 (called Grub Legacy) and 1.97 (called Grub 2)

Issuing ```

grub-install -v
``` Will let you know for certain which you are on.
 If you are running 9.04, then you'll be on Grub Legacy

Regards,

Phill.

---

### Post by darkod on 2009-12-20
> **fahadghani said:**
> Hi Phill
Thanks for the reply. Does legacy GRUB mean GRUB 1.5? I am using ubuntu 9.04, which uses grub 1.5. I have installed grub this way about 3-4 times. So, this doesn't seem to be working. =/ However, i m going to try it again and be back in a few minutes. :)

That's Grub Stage 1.5, not Grub 1.5. That just means it's stopped becuse it can't find the grub config files to continue with. If you are using 9.04 than you have grub legacy, or grub1, or officially named grub 0.97. Call it what you want. :)

I think Phill is right. This is probably the issue where utilities made by Dell or HP are overwriting part of your hdd MBR which corrupts grub. You said it yourself, it's happening when you boot XP only.

---

### Post by fahadghani on 2009-12-20
hmm... there is an entry when i run the fdisk command:

/dev/sda1               1           5       40131   de  Dell Utility

and the boot partition is:
/dev/sda2   *           6       27582   221511455    7  HPFS/NTFS

is it possible tht this utility is causing probs?
but this issue did not crop up for the first month or two though. I m not sure how the problem started. But it's true: xp is creating issues. :(

so, what is the solution? 
I need xp for some programs (as usual) else wud hv removed it totally.

Regards
fahad

---

### Post by eakron on 2009-12-21
This is an identical issue to what I'm having on my Dell Vostro 1320 with Windows 7 (formerly Vista).

On any kind of restart or shut down the MBR is corrupted and can't load GRUB2 anymore.

I am reluctant to remove the Dell utilities, but that's what I need to do?

I was considering using a Wubi install instead, even with the reduced hard drive I/O speed. That would leave the Windows MBR right? And whatever is randomly rewriting parts of the MBR without even looking at it first, can keep doing it.

---

### Post by darkod on 2009-12-21
I have always built my custom PC so I can't comment on these Dell utilities. But if you know what they are, I guess you can decide whether you need them or not. Also the manual might have information about the utilities.
Personally I hate those utility and recovery partitions.

---

### Post by fahadghani on 2009-12-22
I found a thread on the ubuntu forum archives: 
[http://ubuntuforums.org/showthread.php?t=476940]("http://ubuntuforums.org/showthread.php?t=476940")
It basically tells u to remove the files which end in 1_5 from the /boot/grub directory. They are the grub stage 1.5 files and removing them forces grub to link to grub stage 2 directly w/o going through stage 1.5 

I tried it and it works. I am not sure if it is a temporary fix and the problem comes up again, but it is working perfectly fine right now. (i suspect it is temporary)
I will post my 'findings' (permanent or temp) after a few days!
If someone already knows about it, please let us know.

Thanks darkod and phill!

---

### Post by presence1960 on 2009-12-22
```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		ddd437b8-62ac-421c-8f84-feac263bc072
kernel		/vmlinuz-2.6.28-15-generic root=UUID=4b48a520-cb81-45fe-a1ff-bd8032bfa993 ro quiet splash [COLOR="Red"]i8042.reset i8042.nomux i8042.nopnp i8042.noloop[/COLOR]
initrd		/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		ddd437b8-62ac-421c-8f84-feac263bc072
kernel		/vmlinuz-2.6.28-15-generic root=UUID=4b48a520-cb81-45fe-a1ff-bd8032bfa993 ro  single
initrd		/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		ddd437b8-62ac-421c-8f84-feac263bc072
kernel		/vmlinuz-2.6.28-11-generic root=UUID=4b48a520-cb81-45fe-a1ff-bd8032bfa993 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		ddd437b8-62ac-421c-8f84-feac263bc072
kernel		/vmlinuz-2.6.28-11-generic root=UUID=4b48a520-cb81-45fe-a1ff-bd8032bfa993 ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		ddd437b8-62ac-421c-8f84-feac263bc072
kernel		/memtest86+.bin
quiet
```
get rid of the red in your first kernel stanza!
I have seen on here where certain manufacturer's machines have software which writes to the MBR. If I remember correctly Dell is one. I have to go back and see if I can find those threads.

---

### Post by fahadghani on 2009-12-22
the red part is for letting ubuntu detect my laptop's keyboard! I found that solution after browsing through these forums. There are just too many issues with Dell Vostro and ubuntu (or Dell in general :roll: ), but it sure is a great OS! 
The temporary fix that i talked about is working fine for the time being. Let us see how long it lasts (will post back on the thread). Meanwhile, it will be great if I could get to know what windows/dell program is causing this issue.
Thanks a lot!!

---

### Post by jackubun on 2009-12-31
I had the exact problem. By the method of [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) Phillw provided, I fixed the problem. 
I love to use Ubuntu, but the bugs make my hearts broken again and again.
I really hope Ubuntu could be more stable.

BTW, I remember what happened before this problem. I am using dual system. Before I installed some program on Win XP, everything was going well. But just after I installed them, the grub loading error came out and the system kept rebooting. I think the installations in XP changed grub in linux. I can't understand this.

---

### Post by antrozous812 on 2010-04-25
I know this post is a few months old, but I was wondering if the original poster had his problem fixed, as I encounter the same difficulties. 
I have installed Windows XP and Ubuntu 9.10 on a same hard drive (2 partitions). When Grub starts, and when I make my choice, My computer restarts and I have to select my choice of OS once more before it decides to load. 

I have created a thread here: 
[http://ubuntuforums.org/showthread.php?t=1459914](http://ubuntuforums.org/showthread.php?t=1459914)

But unfortunately, until now, nothing has worked for now. Checked the GRUB and did all kinds of hardware test; all good.

Thank you, 
Chris.

---

### Post by bean123 on 2010-04-25
The reason for this issue is that some program write information at the beginning of disk, which overwrites the grub loader. One way to solve it is to use BURG loader:

[http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)

BURG has an alternative install mode that uses only one sector, for example:

```

burg-install --alt /dev/sda

```

BTW, this wiki page shows some common issue and the solution:

[http://code.google.com/p/burg/wiki/Troubleshooting](http://code.google.com/p/burg/wiki/Troubleshooting)

---

