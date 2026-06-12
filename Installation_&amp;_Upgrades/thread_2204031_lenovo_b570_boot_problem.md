---
title: "lenovo b570 boot problem"
date: 2014-02-06
forum: Installation &amp; Upgrades
---

### Post by shaone on 2014-02-06
Hello There,

I could use some Ubuntu help please!

After a number of attempts to install ubuntu in different ways on my windows Lenovo B570 I'm still left utterly stuck and unable to boot up into ubuntu, hopefully someone here can help me? Or point me to another linux based OS which does not have this issue with my setup?

Many thanks!

The details are as follows:

- Lenovo B570 (model: 1068)
- Windows 7 as main OS using easyBCD
- Partitions currently setup as per this article: [http://linux-powered.blogspot.co.uk/2011/09/dualboot-on-lenovo-b570-3-partitioning.html](http://linux-powered.blogspot.co.uk/2011/09/dualboot-on-lenovo-b570-3-partitioning.html)
- USB Ubuntu 13.10 install
- Installed onto windows DOS based MBR disk
- Wireless access works
- Using windows boot loader rather than installing GRUB to MBR of disk (as recommended in above article - note, all other articles I tried just left a total blank, this one at-least gets me a grub> prompt :)

Where I'm at thus far is this:

Though I do have ubuntu in windows boot menu now, if I click on it and start to boot up, it spits out some error messages (too fast to comprehend or note down, some hex stuff among it), and then lands me in a grub> command prompt within GRUB4DOS 0.4.5c, which I'm unfamiliar with being rather new to the platform.

Other things I have done/tried:

- Updated bios to lastest version, still do not see any boot legacy or ueif options as is suggested should happen, they're just not there in BIOS setting so not an option to change
- Tried boot repair, various different approaches and makes no difference
- Tried various different other installs, including formatting entire drive to GPT, those did not work either
- Tried clean install letting ubuntu do whatever it wanted no custom options or partitions and that did not work either

So rather perplexed and a little frustrated I have to say, and have done as much as I know to do with a system I'm unfamiliar with, any help to get me up and running with ubuntu would be greatly appreciated, or as I said any other Linux distro that can work with my setup would be fine too, thanks!

Sean

p.s. also aware of and have tried these avenues to no avail:

[https://help.ubuntu.com/community/forum/hardware/LenovoB570](https://help.ubuntu.com/community/forum/hardware/LenovoB570)
[http://ubuntuforums.org/showthread.php?t=2198237&highlight=lenovo+b570+boot+problem](http://ubuntuforums.org/showthread.php?t=2198237&highlight=lenovo+b570+boot+problem) (most of this is too dense for me to take in right now, would prefer a simpler solution if there is one)

---

### Post by oldfred on 2014-02-06
Best to see lots of detail.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by shaone on 2014-02-07
Thanks oldfred,

I had to run boot-repair again to get this info, now I have a new problem!

Now on reboot there is grub boot loader with one entry in it: ubuntu, which starts up as expected, but no windows 7?!
This is a humdinger of a problem as W7 is my main OS currently.

How do I go about getting W7 in the boot loader?

I suspect this happened because the check box for 'install grub into sda' in boot-repair could not be unselected, though I had selected 'install grub into separate boot partition' unselecting 'install into sda' could not be altered, it was/is fixed on, unlike in previous disk-repairs I've seen and used.

Boot info is as follows:
paste.ubuntu.com/6890319

Best wishes
Sean

---

### Post by oldfred on 2014-02-07
Part of the issue is that you have a BIOS/MBR install, but system is also UEFI and you booted Boot-Repair in UEFI mode. You need to be consistently booting in BIOS mode. UEFI/BIOS menu should give two choices to boot flash drives, one UEFI and the other not, but not always clear what it is.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
You always want the purple accessibility screen.

You also have dual video, which I do not know a lot about. You need to know which video mode it boots with. If you can set it in BIOS. If automatic it often is Intel which needs different boot parameters to boot than nVidia. If booting with nVidia you need nomodeset to get to low quality graphics until you install nVidia driver.

I do not know why os-prober did not find Windows. It looks like you have the boot files (and boot flag) in sda2, and your main install in sda5 which is a bit unusual. Normally Windows is in primary partitions. But the real requirement is that it can only boot from primary partitions or your sda2. If you deleted sda2, you could not directly boot Windows in sda5.

Do not install grub to PBR - partition boot sectors like you did with sda6. BIOS/MBR only boot from MBR of hard drive never from PBR.

You also have separate Linux /boot partition. With most desktops that is not required, but is ok. It just is one more partition to manage as you have to manually houseclean old kernels as they build up over time.

Your sda2 NTFS partition with the boot files is also getting full at 89%. Windows really slows at that point. Better to have 30% free in NTFS partitions. But main install is sda5, so not sure how Windows is configured. Normally the boot files are in a small 100MB boot partition that is hidden. Yoursda2 Windows boot is large, but main files are in sda5.

In your Ubuntu install run this again to see if it finds Windows.
sudo update-grub

If not it may need chkdsk from a Windows repair cd or flash drive. Grub only boots working Windows and Boot-Repair only fixes minor issues with Windows.

---

### Post by shaone on 2014-02-07
Thanks oldfred, sudo update-grub solved it!

Yes, there is a bit of house keeping to do for sure (thanks for your insights and tips). 

The good news is I can now get into both OS's through grub and have ubuntu up and running for practicing chops, I aim to transition from windows to Linux as a web developer as most of the CLI style packages seem to work much more easily natively without a whole bunch of tedious work arounds I find have to happen in W7, which is a whole other story.

For the record, the dual screen seems to be working well so far, not using the NVIDIA GeForce though but the intel onboard chip, as reading around support for the optimus setup seems rather shakey and vague.

Also, I have to say despite my initial struggle getting things setup on the Lenovo (will be purchasing next laptop carefully with Linux setup in mind) you have more than made up with it in terms of your awesome and fast support, sincere thanks for that oldfred!

All the best
Sean

---

### Post by oldfred on 2014-02-07
You are welcome, glad you got it working. :)

---

