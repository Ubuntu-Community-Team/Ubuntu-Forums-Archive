---
title: "Uncompressing Linux... Ok, booting the kernel"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by xjosie729 on 2006-08-19
I booted from the Ubuntu cd, and everything was okay until it goes to a black screen with "uncompressing Linux... Ok, booting the kernel" at the top. It does not do anything afterwards. It just stays at that page.

---

### Post by zxee on 2006-08-19
Ubuntu may be hanging up on hardware detection. Take a look at the boot options from the start screen where you normally either wait or hit enter press F1. You could also try typing, at that start screen, noapic <enter>
there are other boot options too but see if that helps.

---

### Post by xjosie729 on 2006-08-19
Also, I tried it on another computer, and everything was fine.

---

### Post by sleeperknight on 2006-08-19
yeah I'm also having the same problem, just built a new computer and I'm trying to dual boot with xp and ubuntu,  got a core 2 duo e6600 getting the same problems as him, uncompressing Linux... Ok, booting the kernel then nothing.](*,) ps, im using the new P965 mobo

---

### Post by xjosie729 on 2006-08-20
> **sleeperknight said:**
> yeah I'm also having the same problem, just built a new computer and I'm trying to dual boot with xp and ubuntu,  got a core 2 duo e6600 getting the same problems as him, uncompressing Linux... Ok, booting the kernel then nothing.](*,) ps, im using the new P965 mobo
I was installing on a laptop... It's a pretty old one. Bought it used a few years ago.

---

### Post by Fr@nKy on 2006-08-21
This issue is pissing me of really! I'm trying to use Ubuntu since its 6.06 release on June and I can't because of Issue. It seems that Ubuntu hates newer systems. I know that this is planned to be fix on 6.10 (Edgy Eft) but for god sake devs should gave us a workaround till then. :(

And yes I tried Alternate Install CD (RC) and it doesn't work either.

---

### Post by Asterione on 2006-08-21
Hi,
I had the same problem. I installed ubuntu server version on an old machine, on a drive connected to a new ultra ata controller. In order to have linux booting, I had to disable the motherboard's ide controller, where the cdrom was connected to. Lower cdrom boot priority didn't work for me.
Hope this helps.

---

### Post by Fr@nKy on 2006-08-21
I'm cursed to use Windows XP and later this year Vista. I just hope Edgy solves this :P Well I'll buy a new PC next summer like I always do every 2/3 years.

---

### Post by xjosie729 on 2006-08-21
> **Asterione said:**
> Hi,
I had the same problem. I installed ubuntu server version on an old machine, on a drive connected to a new ultra ata controller. In order to have linux booting, I had to disable the motherboard's ide controller, where the cdrom was connected to. Lower cdrom boot priority didn't work for me.
Hope this helps.
can you explain how to disable the motherboard's ide controller?

Thanks.

---

### Post by Asterione on 2006-08-21
> **xjosie729 said:**
> can you explain how to disable the motherboard's ide controller?

Thanks.

I disabled it in the bios / advanced settings, and moved the cdrom to the second master ide channel of the pci controller. 
It seems that drive enumeration is different from installation to booting. hda in installation was my pci ide controller, but perhaps on booting, hda is the first motherboard ide controlled, that must be disabled, to allow booting.

---

### Post by chakra_dude on 2006-08-22
got the same problem with my box

---

### Post by Big Fish on 2006-08-22
This just happened to me on my main machine. :frown:

---

### Post by chakra_dude on 2006-08-22
Is there really another way to install Dapper? but i'm not giving up :)

---

### Post by Big Fish on 2006-08-22
I just got it to work by switching the DVD drive out with another one and it works fine now! :D

---

### Post by KarlOng on 2006-08-22
I've had the same problem.  Stalls at either booting the kernel, or mounting root.  My newbish solution is to try unplugging USB devices.  If that fails, I had just hit the reset switch on my PC over and over again until it eventually gets past and I get the Live CD desktop.

---

### Post by Rizla on 2006-08-31
I'll reiterate whateverone else said.  Im having the same problem.  I just built a new computer, did a fresh install of XP prior to installing ubuntu and was ready to go.  I booted it up.  Brought up the main splash screen.  Selected the first option (dont remember exactly which).  then.. uncompressing Linux.. and it hung.


I thought i burned the iso wrong, but i tried it on an IBM T43 laptop and it booted right into the liveCD no problem.  Do you think the issue is with my CD drive?  i've got another I can try if thats the case.  I'll keep you posted on my progress.

BTW, i've been really itching to get my hands into Linux and specifically ubunutu.  I built a new pc jsut for the occasion, but this issue is really bumming me out.  if I swap drives out and it still doest work.  i dunno what im gonna do. 

Alas, Im still stuck with windows for the time being..:(

EDIT:  That wasnt exactly the same issue I was having.  The error i get is:

Uncompressing Linux.. invalid compressed format (err=2)

Thats what lead me to believe it was a problem with the CD i burned, but the fact that I was able to get into the LiveCD on another computer proved that theory wrong.  Im using an old 46x plain vanilla cd rom.  Im thinking this could be the culprit for some reason.  I have it setup as on the secondary IDE bus as the master device, if that matters (doubt it).

---

### Post by Rizla on 2006-09-01
Alright.. i'm still stuck.  I swapped out the drive and still having the same error: invalid compressed format (err:2)

I've been scouring the forums for previous posts on this issue, but nothing seems to be working thus far.

Once i get the splash screen up.  I hit F6 and have tried the following things:

1.) boot=
2.) acpi=off
3.) live acpi=off

I did a memory test and it came back 100% (took forever.. 30+ minutes)

Here's some info on my pc that i built.
CPU: intel P4 2.93Ghz
RAM: Kingston 1024MB PC3200 DDR 400Mhz
Mobo: Biostar P4M800M7A Socket 775
HD1: Seagate 80GB IDE (set as primary Master)
HD2: Seagate 120GB SATA set as primary sata drive
CD: Generic 46x cd drive

Any help guys.  Please. Pretty Please.  At least respond to the thread..  Im strugglin here.  Newbie in distress.

---

### Post by Rizla on 2006-09-01
Update:

I tried doing a cd test.  THis is what i got:

crc error

--system halted.

Does this mean the cd is bunk?  I dont see how i could be, because like i said i got the live cd working on another computer.

---

### Post by KarlOng on 2006-09-01
Did everyone try disabling Legacy USB support in your BIOS?
I've set mine to disabled, and am now able to get past the hangups.

Ubuntu is now running OK for me.  The dummy 6.06 64bit install didn't like being installed on a slave drive, so I had to swap the drives and install Ubuntu on the master.

---

### Post by Rizla on 2006-09-01
No I didnt try that.  Im not even sure my motherboard allows me to disable legacy usb, but i'll dig further into the settings.  Its still new to me so i havent explored all the options.

To further eliminate the possibilities of a bad cd.  I went out and bought Beginning Ubuntu Linux from Novice to professional because it came with the full version.  I paid 40 bucks just to "buy" the cd.  I asked B&N if i could return the book and cd if it didnt work for me, they said all i could do is exchange it because it has something to do with copy write protection.  I told the lady that this was OSS, but she got a puzzled look on her face and said I could talk to the manager if i wanted to..  Alas, i bought the book, tried to boot.  Still no luck.  Although the error i was getting with that cd was a kernel panic error..

I thought it might be my ram, but like i said earlier i did the memory test.

still lost.

---

### Post by spartas on 2006-09-01
Same problem here guys.  I hope this gets cleared up before too much longer.  I've got the "Uncompressing Linux...Ok, booting the kernel." text on the screen.

I'm running this on a brand new core 2 duo machine with 1Gb RAM and a 965P based board.  I was hoping this would have gone smoother, but I think I will try running Fedora or some other linux on it until Ubuntu will boot and install on it properly.

I am unable to even run the CD test because it hangs on that same error message, but the MD5Sum is correct.  Also, this happens with either the 64- or 32-bit install.

---

### Post by Gossie on 2006-09-02
Hi everybody,

Also I think I have a new machine:

Processor:    AMD Athlon 64 3800+ (2,4GHz)
Mobo:         ASUS A8N-E (socket 939) with nVidia nForce4 chipset
RAM:          2x 512MB DDR400 (PC3200) V-Data (Dual Channel)
HDD:          Seagate 80GB, 7200RPM (IDE)
DVD-RW:       LG 16x
Video:        ASUS EN6200LE, 64MB
Sound:        onboard

The pc was hanging at the message 'Booting the kernel.' I waited half an hour, tried again.

The suggestionss made by KarlOng and zxee
* disable legacy usb
* type 'live: noapic'
didn't work



But the Alternate cd is working for me! At least, it passed the 'Booting the kernel' and now I'm really installing! 

You can download the Alternate cd from [www.ubuntu.com/download](www.ubuntu.com/download)

Cheers, Gossie

---

### Post by Gossie on 2006-09-02
PS: The message didn't say Uncompressing Linux... ok.'
But: 'Decompressing Linux... done.'

---

### Post by spartas on 2006-09-02
Okay, so I tried out fedora and it's the same story.  Okay, so I could bypass the cdrom detection using the boot parameters all-generic-ide and irqpoll.  This had no effect using the Ubuntu installer.

It seems the only way to get the install process to complete is to install Gentoo, use a USB cdrom drive, or install onto the drive in another machine, and hope that it will boot (which is probably what I'll end up doing).

It would be nice if there was an experimental debian-based distro we could use, knowing full well that things will break; with the updated kernel that we need to be able to load Linux on.  Currently I don't have a copy of XP for that new machine, I've tried my beta copy of Vista, and even that fails too (Blue screen of death with a STOP error code and an error/memory location code).

---

### Post by Gossie on 2006-09-02
Well, the alternate cd gave a lot of errors. It was two steps forward, one step backward. I repeated every step in the process that went wrong., until it went ok. But then in the end it went wrong a lot of times, then I rebooted the installation cd totally. In the end, after a few hours of repeating it completed the installation, but after rebooting I only had a shell and no graphical user interface. So then I rebooted the Dapper alternate installation cd but I got a lot of errors again, no matter if I chose the AMD64-kernel or the AMD-generic-kernel or the 2.*.*-2.*.* kernel. 

But luckily there was the Breezy Badger cd! So now I have a working computer!

Thanks and goodnight.

---

### Post by fireboxtester on 2006-09-02
I made a wiki page to put all of the information about this issue in one place:
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

As you can see it's a pretty major issue.  There are already 3 bugs and at least 9 forum threads regarding this.  Hopefully we can get this fixed for Edgy.  (I'm going to test Knot 2 later tonight)

---

### Post by Rizla on 2006-09-02
Here's another update.

I finally got breezy badger installed.  I had to install the server version and then do the updates manually.  Im in the process of upgrading to dapper drake as we speak.  Then i can really start playing around and converting to linux fulltime.

You will def see more of me around.

---

