---
title: "GAG will not boot my Dapper."
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by robsss on 2006-06-08
GAG boot loader doesn't seem to want to run my Dapper.
For some reason GRUB will do it just fine, the grub that is installed with 6.06.
 
In GAG, I go to add a new operating system, go through the steps.  My Ubuntu partition is on a 2nd hard drive.  Gag will boot to windows just fine, but will not boot to Dapper.  I'll admit, I'm new to Linux/Dapper and the only way I have to recover from this problem is just to reinstall 6.06.  
GAG spits out an error that says something like "no bootsector" or something.

GRUB seems to load Dapper fine, but GAG keeps having an issue.
Is there something I am missing?

Any help would be greatly appreciated, thanks ahead of time.

---

### Post by trout_256 on 2006-06-17
I have the same problem.

Windows 2000 on 1st HD, Ubuntu Dapper on 2nd.

After the initial Dapper install, everything works fine until you boot into Windows 2000 the SECOND time, then the computer endlessly loops through the BIOS screen, but never boots Windows or anything else.

So I have tried various boot managers with absolutely no success. GAG says "no bootsector" or something very close to that. GAG will boot Windows 2000 just fine, but not Ubuntu.

Anyone know how to solve this?

---

### Post by Herman on 2006-06-17
Well if you want to use GAG Boot Manager to boot Ubuntu or any other Linux you need to install a bootloader to your first sector of your Linux partition. Windows already has a bootloader installed in its first sector.

To install a bootloader in the first sector of a Linux partition, you first need to find out what partition number exactly is used to designate your Linux partition by using the command: > sudo fdisk -lu or a similar command. 

This is easiest to do when you have already got Ubuntu running. If that's not possible, from another Linux system and if you don't have another hard disk installed Linux and can't boot Ubuntu at all to begin with, you can do this from a Live CD. The 'Rescue a Broken system' option on the 'alternate CD' installer will also give you a terminal for this.
When you know what partition you are aiming for, type (from a liveCD)
> sudo grub-install /dev/hda2 Where /dev/hda2 is your Ubuntu partition.

Normally, if you plan to boot with GAG, you would be installing with the 'alternate CD', which provides the option of installing a bootloader to the first sector of the Linux partition during the install, [*click here*]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location") to see.
You would need to have your GAG Boot Manager CD or floppy disk ready before your install for that.

I hope that helps, any more trouble please ask again and I'll elaborate more.
Regards, Herman :D

---

### Post by trout_256 on 2006-06-17
Herman,

It worked like a charm! Your instructions were perfect. Thanks so much!

Really, the only reason I even still use Windows 2000 is for printing and scanning. The MFC unit I have (a Canon unit) is not supported by Linux for printing or scanning. As soon as I can afford to buy another Multifunction unit, I am going to drop Windows entirely. I can hardly wait ;-)

What is this "alternate cd"?

---

### Post by Herman on 2006-06-17
trout_256, :D Okay! I'm happy to be able to make someone else happy! I know what you man about having to dual boot for a while because you need Windows for some reason or another. I was a Windows user not so long ago too. Now I just keep it for historical purposes- sentiment perhaps? When I buy my next new computer someday, I'll have one custom made and not have it com with Windows at all. I should be able to afford a computer with twice the hardware value with the money I'll save on unwanted software. :D 
> What is this "alternate cd"? There two different kinds of installers/partitioners that you can install Ubuntu with. 

The newest one is called the **'Desktop' CD**, (or .iso), and that's the one that runs with the operating system in the LiveCD so you can try it out and make sure you like Ubuntu first. Then you click the desktop 'install' icon to begin your install. The installer is more 'graphical', and features GParted for its partitioning. The main advantage initially is that it's easier for new people to use than the more traditional text based installer. Here on the forums yesterday a discussion ([*Click here)*]("http://www.ubuntuforums.org/showthread.php?t=195800&highlight=herman") caused me to think the graphical 'Desktop' installer might have other advantages too. I think it might be convenient to use GParted to *move* Windows towards the end of the disk after resizing it smaller. That way Ubuntu can be installed at the beginning, or outside edge of the disk where there might be a speed advantage. Aysiu has a great website to explain how use the 'Desktop CD' with the graphical installer. [*Click here*]("http://www.psychocats.net/ubuntu/windowstoubuntu.html").

The **'Alternate CD'** is the more traditional text based installer for people who want to have more options and choices available to them during the install. It may be used for performing ordinary installs, but it is really good for those who want to have a special or customised install. There are lots more choices available, but the problem was most new users found it confusing because they didn't know what they were doing. That's why I made a website for it, to guide people through. Now anybody can use the 'Alternate CD' install with, but the majority use the 'Desktop CD now. 
The 'Alternate CD' is more for those who have special requirements or who know what they are doing. Being able to choose where you would like the bootloader's IPL installed and even which bootloader you would like is one of the extra choices offered by the 'Alternate CD'.
If you would like to visit my website and see illustrated examples of Ubuntu 'Dapper Drake' being installed, click one of my signature links at the bottom of this post.
The installs themselves are now updated from 'Breezy' to 'Dapper' version, but there are still a couple of other pages I'm working on. Actually, I'm always working on it so I guess it doesn't matter. Please feel free to pass on links to others if you think anything there might help someone in some way.
All the best! Regards, Herman :D

---

