---
title: "How do you install Ubuntu/Grub to a USB external HD and make it bootable?"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by Robertar on 2006-11-06
Hi, I'm doing a research project for one of my classes here at my university.  We’re trying to see if it would be possible for each student to pay a one time fee to get an external USB hard drive they can take with them to help complete their IT classes here at the university and to use through out their career. It would be a lot cheaper than a laptop (since not all students can afford one). I chose to install Ubuntu, and it needs to be bootable wherever you go (ie. unplug from your laptop/desktop and go to another computer and have it boot from the USB drive), so I assume it needs grub on it.  And so I’m trying to write the instructions to be as simple as possible, and I thought the installer that comes with the Ubuntu Live CD (there's an "install" icon that appears on the desktop when you boot with the Ubuntu Live CD) is pretty straight forward without having to write any code in the terminal.

The problem is not installing Ubuntu, it's installing Grub.  Apparently, all the files go onto the external hard drive just fine, except no matter how I try to edit where it is to be installed, it always gives me an error when I go to boot from it.  The error is error 22.  I suppose I'm installing Grub wrong when I want it to go on the external hard drive.

Down below is a list of all the steps I take to install Ubuntu.  Hopefully someone can guide me in the right direction.

When you boot up to the Ubuntu desktop:
[LIST]
[*]I click on the "install" icon
[*]I choose English as my language, and click forward
[*]I choose Boise as my region, and click forward
[*]I choose a US keyboard for my layout, and click forward,
[*]I create my profile with name, password, ect, and click forward,
[*]I choose manual for my install method,
[*]I select the external hard drive from the pull down menu(listed as "/dev/sda"),
[*]I then right click in the unallocated field, and select "New",
[*]Then I make a primary ext3 parition with 25GB, and click add,
[*]Then I make another primary linux-swap partition with 2GB, and click add,
[*]I review what I've done and click forward,
[*]It asks me do I want to make changes, and I click apply,
[*]Then I click close on the results window,
[*]Then a window called "Prepare mount points" pops up and I make sure that only the root "/" is on "/dev/sda1" and the swap "swap" is on "/dev/sda2", and are both selected for reformatting,
[*]Then I click forward,
[*]Then a window called "Ready to Install" appears, and presents all of the operations that are about to be performed on the external hard drive.  Here's where it gets tricky.  There's a line here with a button that says "Install Grub on (hd0)."  I believe this is what I need to edit to tell the installer where to install Grub.  Trouble is, I don't know the syntax for telling it to install on the USB Drive, so it can become bootable.  If left as it is, (hd0), it gets installed on the local machine's hard drive, making a physical connection to the external hard drive required to boot anything at all on the local machine.  So that's where I think my trouble is.] (*,) 
[*]Then I click on install, and the Ubuntu goes through all the motions and installs on the external hard drive over the period of an hour and a half.  (this is probably because I'm installing to a USB external drive though)
[/LIST]
Theoretically, when you boot from the USB drive (either by editing your BIOS or selecing it from a Boot menu) from any machine that supports booting from USB, Grub (on the USB drive) should load Ubuntu from the USB drive.  But this is where it gives me error 22.

Well, its been rough, and I've tried installing it 6 different times now with no success.  And I've searched up and down different forums to no avail.  So if anyone knows anything about how to do this, please let me know.

If I must use the terminal, so be it, but I would really rather avoid it.  If you do use the terminal, be specific as to what you do, as other students who may not be familiar with Linux yet will be following what you put down.  Thanks in advance!

---

### Post by catlett on 2006-11-06
The issue is how easy you want to make this. The Alternate Install CD allows you to choose where to install grub. [http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/) (scroll down and you'll see the Alternate Install CD. You may want to download it and try it for yourself) The problem is the alternate install is text based (this gives you an idea of the text based installer. it says dual boot how to but it shows all the screenshots from the alternate cd. You may want to browse the site, Herman is very smart and made a great site) [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
With the alternate cd install, you can manually input where grub will install but the installer isn't as user friendly as the live cd.
You may want to investigate Puppy linux to get some ideas. [http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1) It is a minimalistic distro but it has some great features. It has utilities to install grub where you want and to make a usb thumb drive or external drive bootable. Not that Puppy is your choice but it may give you some ideas. The thing is Puppy is made to go on a usb device and ubuntu is not.

The alternate cd install is the easiest way to achieve it but it may not be the easiest install. I have one question. After you install Ubuntu to the usb device, does grub install to the mbr of the computer you ran the installer on? If it does, is that a problem for the students who are going to do this? Will they be doing this on an XP computer and they will loose windows bootloader? Secondly if it does install on the mbr and it allows you to boot to the usb drive, you can install grub from the command with ```
sudo grub-install /dev/???
``` Although that adds another step as well. You will have to tell them to boot into the distro and enter the grub install command from the terminal and to know the proper label for the usb device.

Actually now that I think of it, my 'how to' may work but it will add a complicated step to your process. The alternate with good instruictions may be a better bet. But to give you as many options as possible, this method restores grub when the mbr has been corrupted. It should install grub to your usb device after you install ubuntu to it. [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
I know this isn't clear cut but I am just brainstorming more then anything. Feel free to throw something back and hopefully we can work out a good method for you.

P.S. I woould recommend 6.06 over 6.10 Dapper, which is 6.06, is a more stable release. It is the one with long term support (LTS) whereas edgy and eventually feisty will be more cutting edge but may be a bit less stable. Just something to think of since the students will be keeping there entire college curriculum on it.

---

### Post by Robertar on 2006-11-06
Thanks for the info.  And to answer your question, while I'm using the graphical installer from the Live CD, towards the end it asks where I wanted grub installed at the window that says "Ready to Install."  If I leave the default destination as "(hd0)", grub does install to the mbr of the computer you ran the installer on.  (Most students here use Windows XP)  If that happens, they will only be able to boot when the USB drive is connected thru a USB port.  If they try to boot the local machine's OS, Grub will crash at bootup giving error 21, which I believe means that it can't find the disk with the Grub stage 2 on it.  However, if the USB drive is connected to the local machine, both the local OS and Ubuntu on the USB drive are accessable and bootable through Grub.

I can see how the Windows Bootloader can be restored my using the fix mbr command from the Recovery Console using a Windows XP CD.  But if they want, they can even leave it that way and choose to boot to the USB drive that way, but that would be there choice I guess.  But I don't see how they'd be able to boot on another computer, say a lab machine.

I've had it done sucessfully before.  I went to an Ubuntu Installation party 2 saturdays ago and I installed Grub over the local machine's MBR by accident.  They had a disc with them where I could fix my MBR, but before that, they booted off the Live CD, went to the terminal and did some fancy footwork to install grub onto the USB.  I asked them if there was any documenation on the web on what they did on the internet, and they said, "Oh yeah, it's all over the web."  So I didn't copy what they did down since I was in a hurry.  That was mistake number 1.  Then this passed weekend, I tried installing Windows XP on the unallocated partition left on the USB drive.  Mistake number 2.  It went right ahead and formatted the whole thing, even though it told me it was only working with the partition I selected... sigh.

If you can add anything else to it what I've said, that'd be great, and I'm going to look over all the links you've given me.  Hopefully I can find a solution soon.  Thanks again!

---

### Post by catlett on 2006-11-06
Sorry to leave you hanging a bit. Work caLLED.
Anyways, I would go with the alternate cd install method. Because the way you have it now, the mbr is over written on their xp machines. To get it back, you need to run the recovery console off of an xp install disk. Then you have to boot to a live cd and run the setup comand in grub. It would be far easier to just run the alternate install cd and put grub where you want it.
The other issue is they need to connect to copmputers that have the ability to boot to usb drives. I do not know your schools setup but I would think that would be an issue.
Even with the minimal distros that fit on a flash drive, you still have to boot to the usb port.

To run down your first method.
Run the live cd installer. Install to the usb but grub gets installed to the mbr of the host computer.
To put grub on the usb device, boot to ubuntu from the host computer and then enter the grub install command at the terminal [http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall)
```
sudo grub-install /dev/sda
```I used sda because that is what my usb is listed as but it may be different with your drives. There is another way to get grub on the drive (the how to I linked you to) but you don'y need it if you can boot to ubuntu from the host computer.
Last is fix the mbr of the host computer. Put in an XP install disk and run the recovery console.[http://www.geocities.com/kilian0072002/recconsole2.html](http://www.geocities.com/kilian0072002/recconsole2.html)


This may interest you as well. [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811) This is about loading breezy to a usb external drive. Breezy was replaced 7 months ago by dapper and of course edgy was released last month. I'm linking you to it for 2 reasons. One the breezy installer is the text based installer that is now the alternate cd and 2 just to give you something that walks you through a usb setup.

Try setting up your drive with the alternate cd, it isn't that hard. Just select the usb drive and let ubuntu take all of it. Then when grub comes up, it will allow you to enter the device/partition you want to install it to. It should be /dev/sda It will be much easier than using the live cd and then correcting both mbrs. Once you do it once, you will see how easy it is and you can guide the others. The alternate install cd would be my advice.

---

