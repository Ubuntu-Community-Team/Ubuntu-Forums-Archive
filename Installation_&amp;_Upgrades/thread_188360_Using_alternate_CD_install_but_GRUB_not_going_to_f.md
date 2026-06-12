---
title: "Using alternate CD install but GRUB not going to floppy"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by gene0915 on 2006-06-04
I downloaded the "alternate install CD" to get more control over one particular feature.... installing GRUB to a floppy disk.

I have a WinXP system. Drives C: and D: are IDE drives which I pull the power cable from when installing Linux distros to totally avoid ANYTHING from damaging them. Once the install of Linux is finished on my slave 40 gig test drive, I shut the PC off, reconnect the power cables to C: and D: and mount them as read only NTFS drives and no probs.

Ubuntu is one of the only distros that sets the refresh rate correctly on my monitor so I think I'll stick with it but I'm having MAJOR problems with GRUB. I have followed ALL the guides on this site about the DD command to create a 512 byte file so I can let Windows very own bootloader do everything but this results in a crash when I select Kubuntu. Yes, I used hdc1 in the command and no luck. I even played with GAG but when I selected my Linux partition (yes, I selected the primary boot partition) and tried booting, it said it couldn't find the boot sector?!? (Gag appears to be poorly written)

With Ubuntu 5.10, what I want to do worked perfectly. (I was able to EASILY select the floppy disk as a target to install GRUB to). BUT, using the "alternate install CD" for Kubuntu 6.06, it just steam rolls right through the GRUB stuff. If I select "Go Back" in the bottom left corner after the install is finished and right before the final reboot, I scroll up to the "Install GRUB..." setting and it only talks about forcing it to the hard disk. Why is the installer not giving me the option to install GRUB to the floppy?

Can somebody give me EXPLICIT directions on getting the alternate install CD to give me the option of clearly/easily installing GRUB to the floppy? (I want my computer to boot Kubuntu when the GRUB floppy is in the drive and straight to Windows when there is no floppy disk in the drive.)

Thanks!

---

### Post by confused57 on 2006-06-04
I realize you are wanting to use a boot floppy to load Linux, but this is how I have my system set up, if you want to consider another option:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by rcarring on 2006-06-04
I guess an alternative is the virtual hard disk method. I can understand your reluctance to expose your favorite operating system to Linux, as some of the early distros back to 98 were particularly casual in that regard. 


One thought if you are pulling the c and d drives then connecting them up when you have linux installed, isn't that going to foul up grub's menu anyway, as all the ide devices are going to change position.

---

### Post by gene0915 on 2006-06-04
[QUOTE=rcarring]I guess an alternative is the virtual hard disk method. I can understand your reluctance to expose your favorite operating system to Linux, as some of the early distros back to 98 were particularly casual in that regard. 


One thought if you are pulling the c and d drives then connecting them up when you have linux installed, isn't that going to foul up grub's menu anyway, as all the ide devices are going to change position.[/QUOTE]

Pulling the cables....installing 5.10....plugging the drives back in, I was able to install GRUB to the floppy and it worked perfectly! I think the installer in 6.06 is broke. At least for the "alternate CD" it is. It won't let you change the target for GRUB.

---

### Post by gene0915 on 2006-06-04
[QUOTE=confused57]I realize you are wanting to use a boot floppy to load Linux, but this is how I have my system set up, if you want to consider another option:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)[/QUOTE]

Read your post when I was needing help earlier this evening before I posted and no luck for me.

---

