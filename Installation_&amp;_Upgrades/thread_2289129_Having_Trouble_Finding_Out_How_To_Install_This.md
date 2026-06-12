---
title: "Having Trouble Finding Out How To Install This"
date: 2015-08-01
forum: Installation &amp; Upgrades
---

### Post by joey25 on 2015-08-01
Hello, I'll make this as quick as I can.
 I salvaged my old hard drive from another PC, and it's now working as a secondary hard drive. I'm looking into dual booting it with Ubuntu, and there's so many different tutorials for installing it, which all seem to have different outcomes, and even on the Ubuntu page, I found I was still having trouble doing what I wanted.

So basically, I don't want to make separate partitions on my primary hard drive, I want separate operating systems for the separate hard drives. I tried putting the ISO onto my flash drive, plugging it in, entering the BIOS and changing the priority, yet when I hit F10 to save and exit, it still rebooted into Windows on my primary hard drive, not the Ubuntu setup or anything. 
What I'm asking is to be walked through EVERYTHING as if I'm five years old, as everyone I've been able to ask about this has been using terms someone who knows Linux in and out would use, yet I've never used it, and want to learn a bit. It's just incredibly overwhelming, and I can't seem to even install the thing right! 
And no, I don't want the operating system to be on the flash drive, I'd like the actual secondary hard drive to be what boots it up. 
Thank you in advance!

---

### Post by TheFu on 2015-08-02
I started 2 prior replies, but decided to delete them.  This is my 3rd.

Welcome to these forums. Hopefully you will get most of what you need over the years here.

I think you are asking for too much help from this group of volunteers.  
> walked through EVERYTHING as if I'm five years old,
That is the issue for me. I want to help, but you need to help too by learning stuff you don't know.  If you are 5 yrs old, I wouldn't attempt to help at all with this. The mental capacity and vocabulary of a 5 yr old simply isn't up to the task, so it would be a waste of my time.

For the type of help you as requesting, that is best provided in-person. Find a local LUG, talk with those people, setup a time/place to get the help you want.  My home LUG has weekly meetings for this purpose.

There is another option. Reduce your expectations to match the current skills available.  

And there is another option - use virtualization. This works well enough if you have a reasonably modern CPU.  C2D or better will work fine provided you don't need high-end graphics. With virtualization, the risks involved with partitioning are removed.  I use virtual machines almost exclusively these days - actually my dialy desktop is a VM running in a private cloud available from anywhere in the world. It does all the things I need as a web developer and for normal office stuff.  Video playback over the network isn't great, but if it was running on the same machice, that wouldn't be much of an issue.

As you use Linux more and more, you will gain the skills to be more comfortable with it and you'll gain the vocabulary to better understand what all those other how-to guides are saying.

The last thing to grasp about running linux is that an OS install is not a permanent thing. There isn't some "license" that won't install later or will be lost.  You can install 1,000 times on 1 or 500 different machines, so after the partitioning is handled, practicing installations is available. Doing 5 installations will make you pretty comfortable at it.

Anyway, I truly hope this is helpful.   Better post this before I reread it and decide to deleted it too.

---

### Post by grahammechanical on 2015-08-02
You may find as I did that with a USB memory stick changing the boot priority in the BIOS is not enough. I have to go into the Boot section of the BIOS and there I see that the USB stick is being viewed as an external USB drive. And it was in this Boot section that I could direct the motherboard to look for an OS on the external USB memory stick/drive.

Actually, keeping Ubuntu and Windows on separate hard drives is a good idea. And it certainly simplfies the installing of Ubuntu. I do not do hand holding but I will layout the steps.

1) Get the Ubuntu ISO image burned to the USB stick and get the live session loading
2) Before installing Ubuntu disconnect the Windows drive
3) Install Ubuntu on the only drive left connected
4) Reconnect the Windows drive and load Ubuntu. You may have to change settings in the BIOS to do this.
5) When in Ubuntu open the terminal an run this command

```
sudo update-grub
```

Now when you start the computer you should get a Grub boot menu with options for both Ubuntu and Linux. And you can also use the BIOS to load from the Windows drive.

Regards

---

### Post by oldfred on 2015-08-02
For a new user you can just disconnect first hard drive and only have drive you want to install Ubuntu on plugged in. Then the auto install will install only to that drive. Plug Windows drive back in, be sure to use same SATA port or best first SATA port as Windows likes to be first.
Then set BIOS to boot from Ubuntu drive.
And in terminal run this to add Windows to grub's boot menu.
sudo udate-grub

More advanced is Something Else where you want more than just / (root) and swap and have to be careful to choose to install grub2's boot loader to the Ubuntu drive. All other auto install options install boot loader to first drive that is sda, or usually the Windows drive.

These sites all show in detail with screen shots the process of installing with Something Else. Anyone of them is probably all you should need, but sometimes different versions help explain it better.
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

### Post by TheFu on 2015-08-02
Unplugging the Windows drive - good idea.  There will be booting issues later, since I don't expect the OP to disconnect/reconnect the drives between different OS boots. Plus the BIOS boot will need to be picked.

Another option is to do this, but then get a small flash drive to have grub for the Linux boots.  Hummmm.

---

### Post by joey25 on 2015-08-02
I'm obviously not five, a bit foolish to think such a thing. 
I do apologize if I wasn't quite clear on what I was asking to be walked through as if I were that age. I didn't mean every little detail of Ubuntu, just how to install it as a dual boot using basic terminology, like grahammechanical did. I'll be able to understand basic usage as I begin to use the OS.

---

### Post by joey25 on 2015-08-02
Anyways, thank you all for your help. For the time being, I'll hold off on installing Ubuntu, as I just installed Windows 10, it'll be a bit less overwhelming once I've gotten used to my new main OS.

---

### Post by David_Hackenbracht on 2015-08-05
I am a first time user of Ubuntu. I too am doing an install.

Looking at the date on the post's here, I realize that they are old.
But (here is my point) I found all this information really useful, and I wanted to say THANKS !!! to all who replied.

Thanks,

David

---

