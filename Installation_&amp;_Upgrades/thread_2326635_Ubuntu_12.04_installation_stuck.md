---
title: "Ubuntu 12.04 installation stuck"
date: 2016-06-03
forum: Installation &amp; Upgrades
---

### Post by tapasray on 2016-06-03
I tried to run 16.04 off a pen drive or install it on a 64 GB SD card in an Acer Aspire One netbook with 1 Gb RAM. This did not work, though the same pen drive worked on my office desktop.

So I decided to install 12.04 using a Wubi pack that I had already. The tar.gz downloaded, unpacked and the reboot request came up. When I did, I got a black screen with "grub>". Tab was mentioned. Hitting the Tab key brought up a list of "possible commands". I have tried out three or four that sounded reasonable under the circumstances. Got "filename expected" as output. "Boot" brought up "you need to load the kernel first." Guessing that meant the "linux" command, I used it only to get "filename expected". I have a picture of the screen that I wanted to upload, but am forced to use my tab for posting this and don't see any upload link in this version of the site.

This is a desperate situation. I have all my work in Windows 10 on the same machine and can't afford to lose it. Will really appreciate help. Thanks in advance.

PS: I was trying to install Ubuntu because this machine is slow with Win 10. But a slow computer is better than no computer, so I shall be happy to get out of the black screen and abandon the installation if that's the best option.

---

### Post by Bucky Ball on 2016-06-03
Just a note now the horse has bolted. Wubi hasn't been supported for quite some time and I wish you luck getting help with it here (although there are one or two people who still remember stuff about it around the place).

I'd suggest you try creating a regular Xubuntu install disk or USB, or perhaps try the SystemRescueCD, boot from that and transfer any files you want to keep to an external drive in the first instance. That way you know your data is safe.

Frankly, with 1Gb of RAM, Ubuntu 16.04 LTS would be fairly hopeless on that machine and doubtless any better than Windows. Xubuntu or Lubuntu may be an improvement, but the 1Gb of RAM would be why Win10 is running slowly also I'd think.

I'd suggest the same pen drive worked on another computer because you had adequate RAM or other compatible hardware. The reason 16.04 LTS wouldn't even boot on the problem machine would be related to hardware and probably worth working out what rather than regressing to 12.04, then down the black hole that is Wubi.

---

### Post by tapasray on 2016-06-03
Thanks, Bucky Ball. I see where I stand and it doesn't look good. I don't have a SystemRescueCD. I bought this machine on Amazon while in the USA in 2009 and whatever CD(s), etc. it might have come with ... don't remember if it came with any such thing ... must have got misplaced when I relocated.

Can I somehow get it to boot Win 10? Then I'll go back to Win 7.

I have found some instructions on Acer's support pages that looks promising. Trying it out, and will report back whichever way it goes.

---

### Post by Bucky Ball on 2016-06-03
Disks don't come with machines for Linux. You simply download what you need.

[SystemRescueCD]("http://www.sysresccd.org/SystemRescueCd_Homepage").

You also have the Ubuntu install disk and there's any number of bootable disks you can create to do this. Boot Repair, Gparted, etc. 

Again, I'd back up any valuable data before proceeding rather than ignoring and accidentally wiping it out with whatever you try next. If it's that valuable, I wouldn't ignore backing it up (preferably before launching into the install in the first instance in future). ;)

Sorry can't give you much help with your boot. No idea what Wubi does to the Windows bootloader, if anything.

---

### Post by tapasray on 2016-06-03
Thanks a lot for the link. I cant backup, because I have just that black screen with commands ... basically my wild guesses and the machine's contemptuous responses.

---

### Post by Bucky Ball on 2016-06-03
You boot from a CD or USB and drag the files from one hard drive to a safe one. You don't need to be able to boot in to the OS on the machine.

---

### Post by tapasray on 2016-06-03
Bucky Ball, thanks again for your help. Someone told me to power off, power on and use F11, etc. I was hesitant, as I had blacked out my primary laptop just the other day by powering off in the middle of diagnostics, which was stuck midway for some reason. Anyway, figuring I had nothing much to lose, i powered off and fortunately, didn't even need F11. Win 10 loaded without a hitch. Got rid of Ubuntu with Revo uninstaller - it showed up as an application in Revo. No more experiments with this machine.  Will install 16.04 on my primary laptop when I get it back from the technician after formating and re-installing Win 7.

---

### Post by Bucky Ball on 2016-06-03
Good news and thanks for marking as solved.

Good luck with the next instalment. Just remember to forget Wubi!

---

