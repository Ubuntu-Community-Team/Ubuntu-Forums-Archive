---
title: "Is it possible at all to install Ubuntu on an ASUS P4P800-E Deluxe?"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2006-10-31
I have been trying in vain to install Ubuntu 6.0.6 (Dapper) on an PC based on the ASUS P4P800-E Deluxe motherboard.

This is an existing system that have been running Windows 2000 wonderfully (and still does). It has a single 160GB HDD connected via the so called UDMA7 (133 MB/s) - via a Promise 20387 (FastTrack 387) RAID controller.

The installation halts for some reason at a very early stage.
The CD is perfect (was used for successful installation on other PCs).

Anyone who knows the secret to the heart of this hardware?

Thanks!
Alex

---

### Post by DOD1951 on 2006-10-31
To clarify you have only 1 disk and on that disk is Windows 2000? What space is left on this disk? Are you intending to dual boot?

---

### Post by xp_newbie on 2006-10-31
> **DOD1951 said:**
> To clarify you have only 1 disk and on that disk is Windows 2000? What space is left on this disk? Are you intending to dual boot?

Yes, I have only one 160GB disk (SAMSUNG SP1614N). It is partitioned as follows (already partitioned, using PQMAGIC 8.01):

```
[FONT="Lucida Console"]===================================================================================
Partition Information for Disk 1:    152,625.3 Megabytes
Volume         PartType    Status    Size MB    PartSect  #   StartSect  TotalSects
===================================================================================
C:             NTFS        Pri,Boot 16,386.6           0  1          63  33,559,722
               Linux Ext3  Pri      78,858.1           0  2  33,559,785 161,501,445
               ExtendedX   Pri      57,380.6           0  3 195,061,230 117,515,475
               EPBR        Log       2,055.2        None -- 195,061,230   4,209,030
*:SWAPSPACE2   Linux Swap  Log       2,055.2 195,061,230  0 195,061,293   4,208,967
               Unallocated Log       2,047.3        None -- 199,270,260   4,192,965
               EPBR        Log      53,278.1 195,061,230  1 203,463,225 109,113,480
D:             NTFS        Log      53,278.0 203,463,225  0 203,463,288 109,113,417[/FONT]

```
To summarize: 16GB NTFS, 77GB Linux ext3, 2 GB swap.

In the meanwhile, I found [a post that claims a successful install of Ubuntu on this motherboard]("http://www.ubuntuforums.org/showthread.php?t=152180&highlight=P4P800-E+Deluxe"). However, when I tried the same exact thing, the installation hung just as previously (not to mention, that I don't really want to run the system in "compatible mode", but rather in "enhanced mode" - just as I do with Windows 2000).

And yes - I do intend to run the system in dual boot (just as I do with my Lenovo laptop).

Thanks!
Alex

---

### Post by xp_newbie on 2006-10-31
Update/Additional info:

I downloaded the latest & greatest Ubuntu 6.10 CD, thinking it might be able to cope with this hardware configuration. Unfortunately, it didn't succeed either. However, I did manage to copy by hand the error messages it generates:

[FONT="Courier New"]> irq 169: nobody cared (try booting with the irqpoll option)
handlers:
 [<c02528e0>] ide_intr + 0x0/0x1f0
 [<c02528e0>] ide_intr + 0x0/0x1f0
 [<f88fe830>] usb_hcd_irq + 0x0/0x60 [usbcore]
Disabling IRQ #169
[/FONT]
And later it comes up with a burst of a few identical lines of the form:

[FONT="Courier New"]> hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[/FONT]
Does this help to zero-in on the problem?

Thanks!
Alex

---

### Post by tormod on 2006-10-31
FWIW, you'll find something about Promise RAID trouble here:
[https://wiki.ubuntu.com/EdgyKnownIssues?action=recall&rev=33](https://wiki.ubuntu.com/EdgyKnownIssues?action=recall&rev=33)
(this issue was later removed from that page because the bug was not confirmed)

---

### Post by xp_newbie on 2006-11-01
Well, I managed to install Ubuntu 6.0.6 (Dapper) on this system and now it work beautifully, so the answer is **YES**. :)

The trick is pressing F6 at the first menu before Ubuntu boots, and appending the following boot option: irqpoll.

That's it.

I hope this will help somebody.

Alex

---

### Post by tormod on 2006-11-02
Maybe you can add your results to the Wiki, for instance here:
[https://wiki.ubuntu.com/HardwareSupportComponentsMotherboards](https://wiki.ubuntu.com/HardwareSupportComponentsMotherboards)

---

### Post by xp_newbie on 2006-11-02
> **tormod said:**
> Maybe you can add your results to the Wiki, for instance here:
[https://wiki.ubuntu.com/HardwareSupportComponentsMotherboards](https://wiki.ubuntu.com/HardwareSupportComponentsMotherboards)

Thanks for bringing this my attention. I didn't know about the existence of such Wiki.

I will wait however with posting my final results until I find out whether my "solution" is a real solution (i.e. using the hardware the way it was designed to be used optimally) or just some bandage that hides the real problem (lack of proper driver). The reason is that I have just discovered in my dmesg the following:

[FONT="Courier New"]> [17179569.184000] Kernel command line: root=/dev/sda3 ro quiet splash irqpoll
[17179569.184000] Misrouted IRQ fixup and polling support enabled
[17179569.184000] This may significantly impact system performance
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[/FONT]
And:
[FONT="Courier New"]> [17179579.472000] irq 177: nobody cared (try booting with the "irqpoll" option)
[17179579.472000]  [<c014fc8a>] __report_bad_irq+0x2a/0xa0
[17179579.472000]  [<c014fda7>] note_interrupt+0x87/0xf0
[17179579.472000]  [<c014f57d>] __do_IRQ+0xfd/0x110
[17179579.472000]  [<c0105c79>] do_IRQ+0x19/0x30
[17179579.472000]  [<c0103eb6>] common_interrupt+0x1a/0x20
[17179579.472000]  [<f88f44f4>] ehci_irq+0x34/0x1c0 [ehci_hcd]
[17179579.472000]  [<f891f1f9>] usb_hcd_irq+0x39/0x70 [usbcore]
[17179579.472000]  [<c014f44d>] handle_IRQ_event+0x3d/0x70
[17179579.472000]  [<c014f51d>] __do_IRQ+0x9d/0x110
[17179579.472000]  [<c0105c79>] do_IRQ+0x19/0x30
[17179579.472000]  [<c0103eb6>] common_interrupt+0x1a/0x20
[17179579.472000]  [<c03100e3>] _read_unlock+0x3/0x20
[17179579.472000]  [<c0184fc2>] path_lookup+0x82/0x170
[17179579.472000]  [<c0185403>] __user_walk+0x33/0x60
[17179579.472000]  [<c017ed2f>] vfs_stat+0x1f/0x60
[17179579.472000]  [<c017f458>] sys_stat64+0x18/0x40
[17179579.472000]  [<c017323c>] put_unused_fd+0x2c/0x60
[17179579.472000]  [<c01733b6>] do_sys_open+0xd6/0x100
[17179579.472000]  [<c0103471>] syscall_call+0x7/0xb
[17179579.472000] handlers:
[17179579.472000] [<c02737f0>] (ide_intr+0x0/0x1f0)
[17179579.472000] [<c02737f0>] (ide_intr+0x0/0x1f0)
[17179579.472000] Disabling IRQ #177
[/FONT]
Any idea what the quoted log snippet means?

Thanks,
Alex

---

### Post by choochy on 2006-11-02
I got the Live CD to boot...(have not tried to install yet).

I have a P4P800-E Deluxe and was having problems just booting from the Live CD. It would stall at "mounting file system" or something like that, very early. I finally got it to work with a very simple step:

Enter BIOS
Go to: Main/IDE Configuration/Onboard IDE Operate Mode 
Set it to "Compatible Mode" (mine was set to "Enhanced Mode")

I am brand new to Linux and have no idea what I'm doing or why that worked. I just know that I was very frustrated for a couple of days.

I really hope this helps.

---

### Post by xp_newbie on 2006-11-02
> **choochy said:**
> I got the Live CD to boot...(have not tried to install yet).

I have a P4P800-E Deluxe and was having problems just booting from the Live CD. It would stall at "mounting file system" or something like that, very early. I finally got it to work with a very simple step:

Enter BIOS
Go to: Main/IDE Configuration/Onboard IDE Operate Mode 
Set it to "Compatible Mode" (mine was set to "Enhanced Mode")


I was aware of [this solution]("http://ubuntuforums.org/showthread.php?t=152180&highlight=P4P800-E+compatible+enhanced") before I posted my request for help, but it is not really the solution for the problem, because it slows down your disk access considreably. Also, I am using this system as dual boot W2K/Ubuntu and I didn't want to loose what I already had for Windows (working perefectly).

 I could also switch my HDD to the regular ATA100 (UDMA6) IDE ports, but again, this means using my hardware in a manner that is less optimal than when running Windows 2000 on it. This is not why I decided to switch to Linux...

Thanks!
Alex

---

### Post by choochy on 2006-11-02
Oops, I missed that thread while I was searching the forums. And I just noticed you mentioned it above too.:redface:  Thanks.

I don't want to run my system at slower speeds either. If you do find the P4P800 answer, post it here please!

---

### Post by xp_newbie on 2006-11-03
Well, after realizing that this type of problem requires expretise such as the one kernel developer have, I posted my problem [in the linux.kernel newsgroup]("http://groups.google.com/group/linux.kernel/browse_frm/thread/9c4e5121e136e3ba/de6748b62e5165f4?&hl=en#de6748b62e5165f4").

I think I got them stumped, too. :confused: 

In the meanwhile I managed to find [this incredible post]("http://www.linuxquestions.org/questions/showthread.php?t=362780") which seems to suggest a solution for the problem. I have nothing against switching to Slackware. ;)

I hope however that there is a solution within Ubuntu.

Alex

---

### Post by illumin on 2006-11-12
Hi guys, first post here :) I too had this irq 169 and unable to mount rootfs problem but it was on a different motherboard, a ASUS P4C800-E. I managed to boot and install edgy using the irqpoll option as mentioned previously. I also had to add irqpoll to menu.lst in grub on the kernel im booting. My problem now is it takes too long to boot ubuntu as i have an older machine and it boots much quicker and doesnt have to use irqpoll to boot. Is there any other workaround that will increase performance?

Edit: I forgot to mention im not using RAID or the Promise controller. Im using the intel SATA and PATA connections.

---

### Post by xp_newbie on 2006-11-12
> **illumin said:**
> Is there any other workaround that will increase performance?

I am very stubborn. ;)
 
And I think I am onto something...

Something that will let me eat the cake and have it too. :) 

I will post the solution when I am 100% positive about the solution and when I can refer you to the tons of documentation I managed to accumulate in my quest to a perfect (or close-to-perfect) solution.

Stay tuned...

---

### Post by illumin on 2006-11-14
i await with baited breath :)

---

### Post by xp_newbie on 2006-11-18
> **illumin said:**
> i await with baited breath :)
OK - problem solved.

You can read all about it in the [linuxquestions.org hardware forum]("http://www.linuxquestions.org/questions/showthread.php?t=499811&page=3"), but for the benefit of having some backup I am copying my highights here:


[LIST]
[*]The ultimate solution is indeed change the ICH5 BIOS setting from [Enhanced] to [Compatible]. However, **this step by itself is not enough!!! **In fact, when I first encountered this problem, I quickly found postings in the Ubuntu newsgroups that suggested this solution, but when I tried it, the problem was not fixed. The reason is that... Ubuntu Linux needs to be **COMPLETELY REINSTALLED **in order for that change to have the desired effect. Once I re-installed, that was it. 

[*]Yes, I got full performance with this motherboard running Linux but... the system lost one DVD drive.  The DVDRW drive on the master of the 1st IDE channel and the CDRW drive on the slave of the the same 1st IDE channel work perfectly, but it seems that in [Compatible] mode, the 2nd IDE channel is no longer accessible. I guess that **this is a compromise I can live with**, but it may be helpful to note that even in that [Compatible] mode Windows 2000 continues to recognize that 3rd DVDR drive without any problem.

[*]I have no SATA drives in my system (and never had any). All I have is a single PATA HDD (operating at ATA-133 mode) and 3 IDE DVD/CD drives.[/LIST]

I hope this helps somebody.

Alex

---

### Post by Bill Gatz on 2006-11-19
See this thread, too.  And yes, read the whole thing...

[http://www.ubuntuforums.org/showthread.php?t=193283&highlight=dapper+1-3](http://www.ubuntuforums.org/showthread.php?t=193283&highlight=dapper+1-3)

I have the same mobo with an ATI graphics card.  There is a lot of discussion about the mobo settings and ATI/NVIDIA graphics cards.  My mobo would not allow compatible mode with any other setting combinations.  Mine seemed like they were related to other settings.  (ACPI and APIC)  But I think there is better information in that thread that will help a user of that motherboard.

---

