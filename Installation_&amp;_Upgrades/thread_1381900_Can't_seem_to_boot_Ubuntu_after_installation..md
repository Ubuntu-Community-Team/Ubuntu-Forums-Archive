---
title: "Can't seem to boot Ubuntu after installation."
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by Dweomer on 2010-01-15
Hello.

I recently took the step to not only build my own computer for the first time, but also try out Linux. I wanted to install Ubuntu as the first and only OS on the computer, mainly because it was cheap and it was supposed to be the easiest Linux distro for new users.

I built the computer, and it boots up fine with the Live CD I burned. The problem comes with my HDD and trying to install Ubuntu permanently. I'm using Karmic Koala, and the HDD is a couple years old, salvaged from my old computer. I tried all yesterday and the day before to get this problem solved on my own, but, well, I'm just out of ideas for new things to try.

The hard drive is a Seagate 160 GB that I used in my old windows computer. I formatted it and installed Ubuntu via the normal 'Install Ubuntu' icon on the desktop of the Live CD. The disk is displayed as 'Healthy' when I go to System > Administration > Disk Utility, and it appears the write was successful for the OS. However, after it restarted in the installation process, it went to a screen that said GRUB and the computer started beeping repeatedly. It did nothing else. I didn't know what GRUB was at the time, but have since found out. There was no listing to boot Linux and I'm not even dual booting so I shouldn't even need it. After subsequent attempts, using the boot menu to choose the hard drive with Ubuntu on it or choosing 'Boot from First Hard Disk' resulted in the message 'Reboot with valid boot drive or insert boot drive and press any key to continue.' Finally, after all these failures I went into the disk utility and checked the unchecked 'bootable' option. This attempt to boot resulted in a message that said something to the effect of 'Error reading boot drive' but I'm not sure the exact phrasing of it. This is my only operable HDD, unfortunately. Is there going to be a way to install Ubuntu and get myself going, or is there more pain ahead?

Thanks for reading my problem.

---

### Post by theozzlives on 2010-01-15
You NEED GRUB, that's your boot loader. Please elaborate a bit more on your system specs.

---

### Post by Dweomer on 2010-01-15
Okay, it's a really cheap barebones with a lot of the work done for me already so that if I had horribly screwed up, I'd have only been out a few hundred dollars.


MSI K9N6PGM2-V Socket AM2 mATX Motherboard

AMD Athlon x2 5000+ 3.2 GHz CPU

2 sticks of RAM, one of 1 GB the other of 2 GB. Both DDR2.

And then I've got a 1GB video card in, a CD drive, and a CD/DVD Write drive in, as well as the aforementioned 160 GB HDD.

I don't know a whole lot about computers, that's kind of why I chose to build a cheap one; so I could learn. During the process of trying all these different things with the HDD, I moved it from one place to another. Could that be complicating matters? I chose the HDD directly from the boot menu, but if that could also be my problem I want to rule everything out before I go out and shell $80 I don't have on a new HDD.

---

### Post by theozzlives on 2010-01-15
I'd say start by trying 1 stick of RAM, then the other to rule out bad RAM. It's not recommended to move a PC while it's running, cause of the possibility of HDI (Head Disk Interference), but I  don't think that's the case.

Oh, you need the boot flag on your boot partition, if you really removed it, use Gparted on the Live CD to put it back.

---

### Post by Dweomer on 2010-01-15
> **theozzlives said:**
> I'd say start by trying 1 stick of RAM, then the other to rule out bad RAM. It's not recommended to move a PC while it's running, cause of the possibility of HDI (Head Disk Interference), but I  don't think that's the case.

Oh, you need the boot flag on your boot partition, if you really removed it, use Gparted on the Live CD to put it back.

I can try the RAM thing, but I don't move the PC while it's running. I mean I had changed which SATA plug the HDD was connected to, taking it out and putting it back in a couple times while trying various solutions after the install didn't work. Also, the boot flag was already turned off. I turned it on.

---

### Post by Leppie on 2010-01-15
you don't really need the boot flag for ubuntu.
on my drive the windows partition has the boot flag, but grub is installed in the mbr looking for the config files in my linux partitions.
maybe your drive has some hardware issues? you could try to do some checks using images like the [Ultimate Boot CD]("http://www.ultimatebootcd.com/")

---

### Post by oldfred on 2010-01-15
Also check in BIOS that the hard drive is set up and visible. I have seen users who had the drive off in BIOS (whatever off is) and it worked in windows and older versions of Ubuntu, but the new grub2 seems to use the BIOS settings more.

If it is an older IDE make sure it is primary master. If 40 wire cable the jumpers must be set to master, if 80 wire with 3 color connectors the jumpers must be cable select and the drive plugged into the end connector to be master.

---

### Post by Dweomer on 2010-01-15
Okay. I just managed to reinstall Ubuntu, (had to manually erase the drive with the disk utility, it wouldn't let me reinstall with the installer before) and restarted without messing with my ram yet, thinking I could try the RAM afterwards if I still got the same error, but the install worked this time. I'm running off of a hard drive. Sort of an anti-climax, I guess, but it works.

Now, not really a trouble shooting issue, but I'm not really sure about the answer so I figure I'll ask while I've got the thread open. I have a CD of drivers that came with both my motherboard and my video card. Are these for Windows only? I don't want to screw up now that I've finally got to this point.

Thanks.

---

### Post by drs305 on 2010-01-15
Dweomer,

Welcome to Ubuntu.

Normally those drivers are for Windows. If there did happen to be Linux drivers, there are probably newer ones available online anyway. Let Ubuntu figure out what it needs. If you find something doesn't work as you expect, that is the time to start thinking about the driver issue. Until then, just enjoy Ubuntu!

---

### Post by oldfred on 2010-01-15
Ubuntu has all the drivers especially for older computers. The CD's are for windows computers. Sometimes there are issues with Video and Ethernet connections. If those worked from the liveCD and work now you are in business. (which they must be if you are on line with it)

Welcome to Ubuntu.

---

### Post by Dweomer on 2010-01-15
> **drs305 said:**
> Dweomer,

Welcome to Ubuntu.

Normally those drivers are for Windows. If there did happen to be Linux drivers, there are probably newer ones available online anyway. Let Ubuntu figure out what it needs. If you find something doesn't work as you expect, that is the time to start thinking about the driver issue. Until then, just enjoy Ubuntu!


Haha, okay, thanks. Marked as solved.

---

### Post by theozzlives on 2010-01-15
I just wanna say: I have that MSI Motherboard (only with a 2.9 GHz x 2) and everything works fine with Karmic. Glad you're up and running, and welcome to the FREE world of Open Source!

---

### Post by avalokitesvara on 2010-01-15
[SIZE=3]**I had a very similar problem and I am completely confused**[/SIZE]
 
[FONT=Times New Roman][SIZE=3]I have installed Ubuntu 9.10 Karmic on my Dell. Seemed to be OK. Rebooted, worked with it a bit, then shut it down and turned it off. When I turned it on, it started booting, but at some point there was a black screen and it didn’t go any further.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I inserted the CD, turned the computer off and then on. In the menu I’ve chose “Boot from the hard disk”. The GRUB menu appeared. I’ve chosen the recovery mode, which worked successfully. After that I again restarted the computer with the CD in, but this time I selected the normal mode. Worked perfectly. For a few days I was experimenting. The CD and then hard drive way worked, the normal way did not.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]One of my friends suggested that the problem was that the GRUB was not installed in MBR. Partially he was right. It was not there. We reinstalled Ubuntu and now when I tried to boot normal way (without CD) I did see the GRUB menu. But the problem remained. It still shows the black screen and it doesn’t go any further.[/SIZE][/FONT]

---

### Post by drs305 on 2010-01-15
> **avalokitesvara said:**
> We reinstalled Ubuntu and now when I tried to boot normal way (without CD) I did see the GRUB menu. But the problem remained. It still shows the black screen and it doesn&#8217;t go any further.[/SIZE][/FONT]

Just so we are clear, you make the selection in the Grub menu and then it hangs on a black screen after the selection?

Have you tried booting from the recovery mode option in the grub menu? If you don't see a recovery mode option in the Grub 2 menu, highlight the first entry, press "e", go to the "linux" line, cursor to the end. Remove "quiet splash" if they exist, add "single" and then CTRL-x. This should boot into the recovery mode.

Another alternative would be to try another kernel. If your menu doesn't show other kernels: at the Grub 2 menu, press "c". Then "ls (hd0,1)/boot/"  (or wherever your Ubuntu install is) and see what kernels are there. You could then try editing the first entry as above, but only change the kernel number in the "linux" and "initrd" lines, say from -18 to -16, if 16 is on your computer.

---

### Post by oldfred on 2010-01-15
I still think you ave an mbr problem. If you can use the CD to boot into your hard drive:

Try this first:
reinstall from working system - first find Ununtu drive: 
sudo fdisk -l 
if it's "/dev/sda"  then just run: 
sudo grub-install /dev/sda 
If that returns any errors run: 
grub-install --recheck /dev/sda 
Then: 
sudo update-grub

---

### Post by avalokitesvara on 2010-01-15
> **drs305 said:**
> Just so we are clear, you make the selection in the Grub menu and then it hangs on a black screen after the selection?
 Yes
> **drs305 said:**
> 
Have you tried booting from the recovery mode option in the grub menu? 
 Yes, and it works, which is even more confusing

---

### Post by theozzlives on 2010-01-15
try booting from the live CD, go to terminal and type (assuming your boot partition is sda1):
```
sudo -i
mount /dev/sda1 /mnt
grub-install --root-directory=/mnt/ /dev/sda
```

---

