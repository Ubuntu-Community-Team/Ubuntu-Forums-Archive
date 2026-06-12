---
title: "how to REALLY erase grub?"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by winter7 on 2006-10-25
Here is the problem:

I had built a computer to run ubuntu on and play with.:D 
But my server died and the machine is now my new server.:( 

I moved the hard drive to another computer running XP, so that I can at least set up a dual boot. I used GParted livecd to delete the linux partition so I can reinstall it for the new computer:
The new configuration has:
ide 0 Master = Windows XP
ide 1 Master = will be Ubuntu
ide 1 Slave  = DVD RW

To my surprise I got a SMART error on hd2 on startup. I don't believe there is anything wrong with the drive, since I bought it about a month ago. So I pulled out everything except the ubuntu drive and set that as master:

ide 0 Master = ubuntu drive

This actually starts GRUB, which I thought would get erased when I deleted the partitions, but it does NOT give me the SMART error... so it looks like the mobo doesn't like the dual MBR.

Is there anyway to actually erase the MBR? Then I can do a proper install which will put GRUB on the Windows drive which is where it should be?

Thanks
-Dino

---

### Post by x64Jimbo on 2006-10-25
boot a livecd and run this command:
dd if=/dev/zero of=<device>
that should write zeroes to the drive, including the MBR. You could also use a windows setup disc and start a new install - it'll wipe out GRUB and replace it with the windows bootloader

---

### Post by winter7 on 2006-10-25
Thanks for the great tip!
I think writing zeroes should do niceley... I don't want to put another MBR on there, the only one I need is already on the XP drive and I will replace with GRUB once I can install ubuntu again.

Thanks again!
-Dino

---

### Post by Robert.Zapata on 2006-10-25
Also you can boot from a bootable floppy or CD with MS-DOS 6.2 and at the DOS prompt type:

fdisk /MBR

That will overwrite the Master Boot Record.

---

### Post by Bloodypriest on 2006-10-25
msdos 6.2 is a bit harsh. A Win98 bootdisk should do the trick and is much easier to find

---

### Post by gn2 on 2006-10-26
I would urge caution regarding over-writing the MBR with Grub. It simply isn't necessary.

Have you read this thread: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by x64Jimbo on 2006-10-26
Quite to the contrary, I have found that Grub takes care of me very well, and has never caused me any problems. I think this is one of those YMMV things.

---

### Post by gn2 on 2006-10-26
> **x64Jimbo said:**
> Quite to the contrary, I have found that Grub takes care of me very well, and has never caused me any problems. I think this is one of those YMMV things.

You are indeed a very fortunate individual, others aren't so.

What I suggest is simply a means of ensuring that there will be absolutely no chance of Grub totally fudging your Windows install.

There is no need to put your Windows install at risk, so why do so?

All a matter of personal preference of course, but a nice clean shiny MBR does it for me! :-D

---

### Post by x64Jimbo on 2006-10-26
You do know that installing Grub on your MBR has absolutely no chance of "fudging" your Windows install, right? None of the Windows OS is stored on the MBR, so if you do happen to foul something up with Grub, you can fixmbr quite easily with a Windows CD. You might THINK that you've lost your Windows install if Grub gets messed up, but it's still there, like a book without a cover. I have fouled up my Windows dual boot quite a few times by upgrading my linux kernel, which overwrites the menu.lst file, but a simple restore from my menu.lst_backup fixes it every time. Saying that Grub on MBR puts your Windows install at risk is FUD.

---

### Post by KStorm on 2006-10-26
> **x64Jimbo said:**
> Quite to the contrary, I have found that Grub takes care of me very well, and has never caused me any problems. I think this is one of those YMMV things.Yep...I've never had an issue with Grub that could not be traced back to user incompetence..:p

---

### Post by gn2 on 2006-10-27
> **x64Jimbo said:**
> You do know that installing Grub on your MBR has absolutely no chance of "fudging" your Windows install, right? None of the Windows OS is stored on the MBR, so if you do happen to foul something up with Grub, you can fixmbr quite easily with a Windows CD. You might THINK that you've lost your Windows install if Grub gets messed up, but it's still there, like a book without a cover. I have fouled up my Windows dual boot quite a few times by upgrading my linux kernel, which overwrites the menu.lst file, but a simple restore from my menu.lst_backup fixes it every time. Saying that Grub on MBR puts your Windows install at risk is FUD.

fixmbr doesn't always work. Fact.

You've just been lucky so far.

---

### Post by Herman on 2006-10-27
Here's how to fixmbr as well as another few alternative methods for anyone wanting to overwrite their IPL section of their MBR, if you can't get one one these to work, just try another. Anyone should be able to get fixmbr to work if they are applying it correctly though. 

fixmbr.......................................................................................................................................[GO]("http://www.users.bigpond.net.au/hermanzone/p18.htm#fixmbr")

fdisk /mbr.................................................................................................................................[GO]("http://www.users.bigpond.net.au/hermanzone/p18.htm#fdisk_mbr")

MbrFix.exe.................................................................................................................................[GO]("http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe")

dd command.............................................................................................................................[GO]("http://www.users.bigpond.net.au/hermanzone/p18.htm#dd_command")

Super Grub Disk ......................................................................................................................[GO]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Super_Grub_Disk_")

GAG Boot Manager...................................................................................................................[GO]("http://www.users.bigpond.net.au/hermanzone/p18.htm#GAG_Boot_Manager")

Luck has got nothng to do with it, skill and knowledge are the key.

Regards, Herman :D

---

### Post by gn2 on 2006-10-27
> **Herman said:**
> 
Luck has got nothng to do with it, skill and knowledge are the key.

Regards, Herman :D

I like to think so especially when I go fishing, luck when I blank, skill when I catch......:-D

---

### Post by x64Jimbo on 2006-10-27
If fixmbr doesn't work, it's because something else in your windows install got messed up. Or your hard disk is failing.

---

### Post by gn2 on 2006-10-28
> **KStorm said:**
> Yep...I've never had an issue with Grub that could not be traced back to user incompetence..:p

Nail hit nicely square on the head. Incompetent users won't have issues with Grub on their Windows hard drive if it just isn't there......

I include myself in that user category....:(

---

### Post by winter7 on 2006-10-28
Wow, didn't realize this would bring up so much controversy :o 

Remember this drive came from another computer. I wanted to erase GRUB from this particular hard drive for two reasons:

1. I was getting a SMART error when this drive was in the system (more on this later). BOTH drives had an MBR... so I wanted to elimate any source of confusion the system may have had. 

2. I didn't want Ubuntu install to be confused in having to deal with 2 MBRs... I wanted it to overwrite the Windows disk MBR so I could use GRUB as the boot manager.

Erasing the MBR on the second disk worked. However the SMART error did not go away, UNTIL I set the drive as a slave drive. I suspect it might be cable related and it wasn't happy being a master drive in the second position even if I don't use Cable Select.

In the end though this seems to have been pointless, since 6.06 won't boot at all, and 6.10 boots but can't see ANY drives at all, NO network, No sound. I even tried Kubuntu and that crashes after boot.
but that's another thread :-(

---

