---
title: "Grub Not Updating?"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by PJs Ronin on 2013-02-15
I decided to get involved with Ubuntu 13.04 so I built a development computer and partitioned it so I could test several Linux variants.  I ended up with this:

[img]https://lh6.googleusercontent.com/mvC3BHRAGUQvJe_5y-0YStJFL-4g4Be36b8PfVGeUM1Xd6C9SPeirEFHpx9-46CCxHnpXro7vP7cEQJ1oGMrct3Lb3awwss4cmH-9l5orrRvhcyqYuX8EX1A[/img]

I was quiet happy starting with 12.04, then moving to 12.10 and then to 13.04 all the while watching Grub automatically update so that at boot time I was given the option of which variety I wanted to boot into.

Today, I was going through each distribution performing some updates, and doing some research at the same time, and in what I can only describe as a moment of abject stupidity I did a sudo upgrade-grub (at least I think that's what I did).   The next time I rebooted, I got this:

[img]https://lh6.googleusercontent.com/VylMhatxc6vciUwmJOFW-XUefAdrlG5tkZex_mSVARDtG57iUsMjbIf1jMszvZqNZZwfHokKYCYuYX3_oFj66UTmnw3lpsVOK_J6Ts1i1q8g8mVHRo0lEiZI[/img]
The first five lines are as I expect with the exception that 12.04 now seems to be the lead instead of 13.04.   The remaining 6 lines seem to be trying to do the right thing but are outputting generic text instead of scanned results... or so I'm thinking.

If I select one of the later options the correct dist loads so at least Grub is pointing to the right area.   What I want is for Grub to list the distributions in chrono order and without the '--class ubuntu' words.

Any suggestions?

Edit:   I've tried to 'sudo update-grub' from all of the partitions but trhe Grub text on boot never seems to change.

---

### Post by deadflowr on 2013-02-15
What OS do you want to boot at the top of list in grub?

Personally, I follow the grub2 customization wiki and make custom menus.

[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")

But, normally when grub gets an update or something and a secondary OS sets up as the grub I run:

```
sudo grub-install /dev/sda
```

And it resets it as I like it.
But this normally only happens when I do a fresh install of my secondary OS.

I make a custom mneu so that I don't have to run update-grub every time another OS gets a kernel update as the custom menu boots into the latest kernel automagically.

---

### Post by oldfred on 2013-02-15
Only one install can be in the MBR and it is the first in the grub menu. A sudo update-grub should just refresh the grub menu.

But each new install will install its copy of grub to the MBR and then be first in menu. 

You can boot your main working install and from that easily reinstall grub2's boot loader to the MBR with:
If drive is sda:
       sudo grub-install /dev/sda

But if installing from a liveCD or another install you have to mount grub first.

But with each install of an operating system, grub remembers where to reinstall. So a major update to that system may reinstall that system's grub to the MBR.

In every install:
       #To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

    You can uncheck with spacebar all locations and then grub will not reinstall.
       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Better to manage grub yourself once you get more than one or two installs.
       
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

I also have many installs in my sdc drive, but have several MBRs to play with. I use 25GB for / (root) including /home but have all data in one NTFS data partition and one Linux formatted partition and link my data folders back into /home.

to keep track of things best to learn about bootinfoscript which I run from command line to document my system and now Boot-Repair which adds even more info.
       
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

   Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

    I also have several flash drives and manually install grub to them. Then I can add my own boot stanza to boot an install on my hard drive if need be.

---

### Post by PJs Ronin on 2013-02-16
@ oldfred and deadflowr,

Thank you for the great info... there is some brilliant stuff there for a noob like me. 

I also managed to track down 'boot-repair' from this thread [http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917) which has got me sorted out 95%.

Thanks again for the assist, much appreciated.

Edit: sudo grub-install /dev/sda  this cleaned things up slicker than, well pretty damn slick.

---

