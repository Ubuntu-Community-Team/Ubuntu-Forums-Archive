---
title: "USB Computer"
date: 2020-04-19
forum: Installation &amp; Upgrades
---

### Post by Smallwheels on 2020-04-19
I have an Acer Laptop dual booted with Windows and Ubuntu Budgie. Mostly I use Budgie. The other is just there for specific programs. Budgie has gone nuts lately and I want to get a different OS but not wipe the drive and kill Windows 10, because I don't have the license number for it. The Acer came with it. I know how to create a USB iso file for live versions of GNU/Linux. What I would like to do is put the next OS onto an external drive and just run the OS there. The laptop would just be the hardware with the processor. This way the drive within the machine would remain unaltered.

In the live version of the iso file there is the choice to run the OS as a live version or to install it. I don't recall ever seeing the choice to install the OS on other drives during that process. It just automatically decides to put it onto the internal drive. How do I go about doing this? If I have the iso on a little thumb drive plugged in and add an external SSD through a different USB port, and have the internal drive running, will I be shown a choice of on which drive to install the OS? Whenever booting the machine I'll just press F12 to get the screen to select which drive to run. Any instructions from people who have done this before are welcome. Thank you.

---

### Post by sudodus on 2020-04-19
If you are able/willing to unplug the internal drive, you can install Ubuntu into an external drive. When there is no other drive connected (except the live drive alias install drive), the external drive will be target for the installation including the bootloader. This is explained and described at the following link,

[An installed system in an external drive (including the bootloader) ](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312)

There are also several links by C.S.Cameron here at the Ubuntu Forums and at AskUbuntu that describe such systems (and how to make them).

---

### Post by CatKiller on 2020-04-19
> **Smallwheels said:**
> I want to get a different OS but not wipe the drive and kill Windows 10, because I don't have the license number for it. The Acer came with it. 

I don't use Windows, and haven't for a very long time, but I understand that it's possible to extract the licence key from a Windows installation. It would be useful to do that, regardless of what you do with other OSes, in case of hardware failure and the like.

---

### Post by CelticWarrior on 2020-04-19
Not the best strategy. Managing an externally installed Linux is harder and prone to file corruption.
Any preinstalled Windows 8 or newer does NOT require serial number in a reinstallation if you have to go that route but obviously not even that is necessary. All preinstalled Windows since 2012 are in UEFI mode which have great advantages especially in dual-booting. For starters, even if Ubuntu (Grub) craps out completely you can always boot Windows directly by changing the boot order in UEFI > Boot settings. 

> In the live version of the iso file there is the choice to run the OS as  a live version or to install it. I don't recall ever seeing the choice  to install the OS on other drives during that process. It just  automatically decides to put it onto the internal drive.
No, there's the "something else" option that let's users to select exactly where to install it. You would use that option to entirely replace the current installation with other but reusing the same partitions (or different partitions if that'w what you want but it shouldn't be).

In a nutshell, you need to know UEFI and its requirements, have installation media and know what your doing. Then you can easily reinstall one or both OSes. OTOH, you WILL REGRET it if you try what you've asked for.

We can help you correcting the current installation (probably) and even reinstall it safely without touching the other OS (Windows) if necessary. We can also help with what you think is a solution (we already did) but that ISN'T what you should do, obviously.

---

### Post by CelticWarrior on 2020-04-19
> **CatKiller said:**
> I don't use Windows, and haven't for a very long time, but I understand that it's possible to extract the licence key from a Windows installation. It would be useful to do that, regardless of what you do with other OSes, in case of hardware failure and the like.

Yes, it should be possible but it's a moot point anyway. Since Windows 8 and UEFI the license is saved in EEPROM and it's no longer needed for reinstallation, just click to proceed when asked, it'll install the same way and activate fine afterwards.

Retrieving a OEM license makes little to no sense because those aren't transferable to a new hardware. And if a retail license (not the case here) users should know it because it's printed on something and had to be typed in at some time. Reactivating Windows in such situation should be possible but I think it has limits too but with a retail license users should be able to call Microsoft and request reactivation if it fails for some reason.

---

### Post by dragonfly41 on 2020-04-19
I have followed a path similar to what the OP proposes. That is, installing Ubuntu 18.04 in an external SSD (Crucial 1TB).
The internal hard drive in my Dell 3268 contains Windows 10 (oem installation which came with Dell purchase) and some time ago I shrunk the internal partition to add Ubuntu 16.04 (now outdated). Dell 3268 tower does come with extra slots for SSD's but my initial attack was to purchase a StartTech USB 3.0 docking bay for placing my SSD.  If the host machine does not have USB 3.0 then performance might suffer in running external Ubuntu but right now I see no performance penalty.  I can add a second SSD to the docking bay for cloning/backup.
The point to remember is to use GParted in a LiveUSB to first partition the external SSD before installing Ubuntu. I created a first partition /dev/sdb1 which is 500MB in size with boot flags enabled and mounted at /boot/efi.  The next partition /dev/sdb2 holds Ubuntu root mounted at /.   I created another partition ntfs formated to hold some Windows files but that is optional when (rarely) sharing data sets between Windows and Ubuntu. Finally I installed rEFInd as my preferred boot loader and this is installed in /dev/sdb1.

In essence I have a triple boot configuration (in fact I can boot up yet another old hard drive in USB container to make it a quad boot).  But the idea of leaving Windows well alone and running Ubuntu in external devices works well for me (plus rEFInd / Rod Smith documents).

---

### Post by Smallwheels on 2020-04-19
Dragonfly41, have you done such a setup recently to know if it would still work? New versions of all of the Ubuntu based distros are due this month. It would be good to make this happen in April.

The reason to save Windoz is because I don't have the licence key; also I want to switch the slow HDD to an SSD using a recovery disc. That will happen later. 
CelticWarrior, is it true that if I installed a new SSD in the machine that I wouldn't be allowed to put my Windoz OS on it? Would Carbon Copy get around that or is there a hardware barrier to making it work?

If a tower computer has numerous drives and can boot any one drive, it seems like a laptop should be able to boot an external drive. USB C and even USB 3.1 are much faster than older connections. I've got GPartEd and about three different iso burners. I had to try three to get my last iso to be bootable. I had to turn off Secure Boot too.

I barely understand what I'm doing here, but I can follow instructions to the letter. Sudodus I will study the links you posted. I have never taken apart a laptop. This Acer Aspire One has regular Philips screws on the back with a couple of panels. They probably lead to the battery and other hardware. I hope the drive is under one of them. If it's just RAM then perhaps I'll go the software route. 

I see the Linux Live Creator does what I want done, sort of. It makes a persistent OS on an external drive but it only works on Windoz. 

I'll do some exploring in my hardware and in the thread that has some instructions about doing this. If I'm successful or if it fails I'll reply to this thread. It might be awhile. I need to research and then decide which external SSD to order and then buy it. Maybe I should start with a cheap thumb drive to see how well it works. Then buy a high quality larger SSD.

One more question. If I unplug the internal HDD properly and later reinstall it, will it operate as it did previously without any special BIOS or other tweaks?

---

### Post by kurt18947 on 2020-04-19
Does Acer have maintenance/repair manuals online for your model machine? If so, that should tell you where the various components are located. I have a Thinkpad and it's one screw to remove the hard drive. I've had dual boot for several years and for the most part it's been trouble free using GRUB as the bootloader. The only problem I can recall is a Windows update overwriting GRUB so could boot Windows only. I was able to restore GRUB using [URL="https://sourceforge.net/p/boot-repair/home/Home/"]boot-repair. 

  	 	 	 	  [/URL] It wouldn&#8217;t be the worst idea to create a Windows restore flash drive. That way if anything happens to your Windows install you should be able to restore it keeping settings.
  [URL="https://sourceforge.net/p/boot-repair/home/Home/"]
[/URL]

---

### Post by CelticWarrior on 2020-04-19
> CelticWarrior, is it true that if I installed a new SSD in the machine  that I wouldn't be allowed to put my Windoz OS on it? Would Carbon Copy  get around that or is there a hardware barrier to making it work?

No, the opposite is true as I already explained. As long as you don't change the motherboard you can change everything else as many times as you want and **reinstall Windows as many times as you want and NEVER need the serial**, the serial is stored in hardware (motherboard). In the step where the installer asks for it there's a small line "I don't have the serial key" or something like that, clicking on it the installation proceeds and then as soon as it detects an internet connection it activates perfectly. With UEFI and Windows 8 or newer you don't need it, period. That's why you no longer see the stickers with the license key in any computer sold with Windows 8 or newer.

> If a tower computer has numerous drives and can boot any one drive, it  seems like a laptop should be able to boot an external drive. USB C and  even USB 3.1 are much faster than older connections. I've got GPartEd  and about three different iso burners. I had to try three to get my last  iso to be bootable. I had to turn off Secure Boot too.
And they surely can boot a fully installed LINUX OS from external drives. Windows can't because Microsoft says so (they want to sell you the more expensive versions, the ones that allow "Windows To Go" which is sort of a "portable Windows" but then it isn't??).
**However, just because you can doesn't mean you should! **And you really really really have no need for that: Most likely **your current Ubuntu-Budgie is salvageable** and if not it surely **can be reinstalled safely** or any other Ubuntu instead. Why add more complexity?

> I barely understand what I'm doing here, but I can follow instructions to the letter.
That part I've figured out since the beginning, sorry to say. **That's why I strongly disagree with all my colleagues replying in this thread that are acritically validating your intentions instead of telling you the two simple truths I've repeated here about Windows and Ubuntu.** There a HUGE difference between WE doing it and YOU doing it even with the most detailed instructions ever written. It's a trivial thing for any of us commenting here, we've done it multiple times (at least I did), but we all had to learn from experience and by making mistakes (and we all learned the value of good backups the hard way). Can you afford mistakes? I think you can't. So here's my suggestion: Post a thread explaining in detail what is your current problem with Ubuntu-Budgie. If we can't solve the problem I promise I will give you precise and SAFE instructions for reinstallation, leaving your Windows untouched.

Anything else is insane and you'll regret it in one way or another while becoming increasingly frustrated with Linux. This last message is as much for you as it is for the old timers that already commented.

---

### Post by C.S.Cameron on 2020-04-19
Installing to a new internal SSD is a good idea, 120GB should be large enough.
Main thing is to install with your installer drive booted in the same mode your Windows boots in, Either BIOS or UEFI.
Unplug your Windows drive before proceeding and you can't go wrong.
After installation, plug in your Windows drive, boot the Ubuntu SSD and in Terminal run "sudo update-grub" to put Windows on your GRUB boot menu.
If you decide to remove the SSD, the computer will be the same as before.

---

