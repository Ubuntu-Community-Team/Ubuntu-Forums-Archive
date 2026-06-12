---
title: "Installation problems!"
date: 2006-05-22
forum: Installation &amp; Upgrades
---

### Post by cocotu on 2006-05-22
Hi guys, I'm trying to install Ubutu on my PC which I have already WinXP and Fedora.  I want to install Ubuntu over the fedora partition. I already formatted the Fedora partition to ext3 using Partition Magic.  When I'm doing the intallation I get to the point of Partitioning and I select the ext3 partition but nothing happens I can not get over that point and when I press continue I'm taken to a menu of the installation steps.  I select the next step but it takes me back to the same "partition section".  I did a CD integrity check and everything is OK.  Is there like a graphical interface way to install Ubutu.  I have install Fedora, Red Hat, SuSe with no problems because they have a really simple GUI for installation in which I just make a few clicks and everything works!  I'm a newbie, please any type of help will be great!

Thanks

---

### Post by Fass on 2006-05-22
The liveCDs for Dapper have a graphical installation method, if you need it. You can find them here: [http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)

Don't worry about the beta status. Dapper is stable and is a couple of weeks from final, so there's actually no reason to install Breezy this late.

---

### Post by cocotu on 2006-05-22
Thanks, but this appears to be for the more experienced Linux user. I don't really understand what is "Dapper Drake" According to the link you gave me this is still in testing: 

"Note: This is still an alpha release. Do not install it on production machines. The final stable version will be released in June of 2006."

I'm a newbie looking for something simpler.  I have install Fedora, Red Hat and SuSe in the past with no problems.  I feel comfuse with this installation method.  Currently I have WinXP and Fedora in the same HD.  Can I intall Ubuntu on the Fedora's partition or should I first format Fedora's partition as free space (I formatted it as ext3) and intall ubuntu there???

Thanks for the help

---

### Post by Irony on 2006-05-22
From the live CD;

[PHP]sudo mkfs.ext3 /dev/hda3

sudo mount /dev/hda3 /mnt/hda3_Ubuntu
sudo mount /dev/hda5 /mnt/hda5_ExFedora

sudo cp -ax /mnt/hda3_Ubuntu/. /mnt/hda5_ExFedora/.[/PHP]

You'll have to make the directories first;

[PHP]sudo mkdir /mnt/hda3_Ubuntu
sudo mkdir /mnt/hda5_ExFedora[/PHP]

Thus you copy your current Ubuntu from it current partition into the new partition.

Oops ignore that - just install to the free space in this example hda5.

---

### Post by cocotu on 2006-05-23
I already messed everything up last night!! I formatted the Fedora partition in order to install Ubuntu that part went OK! But later I got a message saying that "Cannot find Ubutu Mirror". Right now I don't have the exact message but what I understood from that is that I needed to be connected to the Internet in order to continue the installation.  That sucks! Right now I don't have Internet, how can I continue the installation??
Now that I formatted the Fedora's partition I cannot boot my system and all I get is:

grub>

Is there a command to boot the system, right now I only have WinXP since the Fedora partition is gone.

Thanks,

---

### Post by confused57 on 2006-05-23
If you have the Windows install CD, you could boot up your computer with the CD inserted, then go into "Recovery" mode, then enter "fixmbr" which should restore your Windows mbr.  You should then be able to boot into Windows.

If you don't have the Windows install CD, see this link:

[http://www.ubuntuforums.org/showthread.php?t=180607](http://www.ubuntuforums.org/showthread.php?t=180607)

---

### Post by cocotu on 2006-05-30
Got the installation running! I just continued installing ubuntu and I found an option that enables you to detect the .iso in your hard drive and run it from there.  This installation is very confusing, Ubuntu team please lets make an installation that is sequential and maybe with an GUI for newbies like me.  I had to go back to the menu and guess what choice to use.  

Thanks!!!

---

