---
title: "Installation died ... how do i roll back?"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by wizarddrummer on 2010-01-13
I have this worthless computer that I am using while I am trying to fix my other one. 

The computer I am using now for whatever reason, like picking a lottery number likes to either freeze or reboot for no reason that I can ascertain with any predictability.

I was in the middle of the Ubuntu install when my computer rebooted.

I have a 250GB HD and selected the 1st option side by side with XP. I slid the slider to give XP around 80GB and Ubuntu the rest.

The installation was going great (nice job on the installation program btw; I can tell lots of people worked very hard on this) and I was at the 85% mark when the computer decided to do its nasty little thing and rebooted. 

Does anyone know from the OS internals during the installation process what is happening at the last 15% of the install? I have not shut my machine down or changed the BIOS from booting with the CD. So at this moment that I am writing this I am not sure what has happened. I am hoping that it did not clobber the MBR. If I  can't get into  XP any more that would be less than enchanting.

The machine came back up and booted off the  CD and I proceeded to go through the installation process again to complete the installation process. 

Now its trying to install another copy of itself because it senses that there is two Operating Systems on my hard drive. This is understandable. How would the installation program know that the machine died. Much of the OS had been written already so the installer "sees" two OS's. 

Currently, I have a situation where I now have two smaller partitions; one used by XP and the other one that contains this incomplete installation (I am actually working within Ubuntu right now) and aother partition that is empty. 

Any ideas on how to fix this?

Do I have to get the XP disk and use fdisk delete the partition and start over or is there some really nifty utility in Ubuntu that can a) finish the install and b) reclaim the lost disk space.

Thanks in advance for your help.

---

### Post by gsmanners on 2010-01-13
Reinstalling is no big deal. Just use "Manual" mode in "Prepare disk space" and carefully reselect the partitions that you wanted to use in the first place.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

The disturbing thing is the spontaneous reboot at 85%. That sounds like something went haywire during hardware detection. Not saying it will keep happening, but it sounds like something that could recur.

---

### Post by tommcd on 2010-01-13
> **wizarddrummer said:**
> 
The installation was going great ... and I was at the 85% mark when the computer decided to do its nasty little thing and rebooted. 
Boot up the Ubuntu CD and run the option "check disc for defects" if you have not done so already. This will verify the integrity of the disk to make sure it is good.

If you reinstall Ubuntu, choose manual partitioning as Gsmanners said. For simplicity, just delete the 2 Ubuntu partitions the previous installs created. This will leave all the space you set aside for Ubuntu as unallocated space. Since you said you have a 250GB drive, and you allocated 80GB for XP and the rest (~170GB) for Ubuntu, you should create 3 partitions for Ubuntu using the manual partitioning method:
10-15GB root partition.
A 1GB swap partition. If you plan to use hibernation, then make swap 1-2x the amount of memory you have.
The rest for a separate /home partition. This will allow you to keep all your data on a separate partition, so if you reinstall Ubuntu all your data is safe.
See this for installing Ubuntu with a separate home partition:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by presence1960 on 2010-01-13
Don't rule out hardware causes for the reboots. Open up the case and make sure all your power connections are seated properly to your hardware & your motherboard & power supply.

I clean my case out every month. One time I must have hit the power cord from power supply to mobo and the connection at the mobo was not seated right. I experiemced spontaneous reboots. After ruling out everything else I cracked open my case and found the problem. It definitely is not a problem with Ubuntu because you said it always does this. At least that is my read on what you posted.

---

### Post by wizarddrummer on 2010-01-13
> **gsmanners said:**
> Reinstalling is no big deal. Just use "Manual" mode in "Prepare disk space" and carefully reselect the partitions that you wanted to use in the first place.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

The disturbing thing is the spontaneous reboot at 85%. That sounds like something went haywire during hardware detection. Not saying it will keep happening, but it sounds like something that could recur.

Oh, it definitely is hardware issue. It definitely is recurring. I just do not know what it is. 
It is too intermittent to even begin to pinpoint a precise, repeatable countdown to failure. I am almost 99 & 44/100ths percent sure it has nothing to do with the Linux installation program.

---

### Post by wizarddrummer on 2010-01-13
> **tommcd said:**
> Boot up the Ubuntu CD and run the option "check disc for defects" if you have not done so already. This will verify the integrity of the disk to make sure it is good.

If you reinstall Ubuntu, choose manual partitioning as Gsmanners said. For simplicity, just delete the 2 Ubuntu partitions the previous installs created. This will leave all the space you set aside for Ubuntu as unallocated space. Since you said you have a 250GB drive, and you allocated 80GB for XP and the rest (~170GB) for Ubuntu, you should create 3 partitions for Ubuntu using the manual partitioning method:
10-15GB root partition.
A 1GB swap partition. If you plan to use hibernation, then make swap 1-2x the amount of memory you have.
The rest for a separate /home partition. This will allow you to keep all your data on a separate partition, so if you reinstall Ubuntu all your data is safe.
See this for installing Ubuntu with a separate home partition:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

   Thanks for the reply.
  I will check, but I do not think that the disk has any errors.
   
  As I mentioned, in another response ... this machine does indeed have a hardware issue. This I now have confirmed.
   
  I thought that many of my problems were exacerbated by Windows Services. In Safe Mode I can operate longer but I still have a problem. The fact that the machine was "true to form" during the Linux install proves to me, without a doubt, it has nothing to do with Windows in any way.

EDIT:
I was able to use the Windows Disk Management to reconfigure the hard drive. It had the 80GB partition that it knew about for XP and a block of free space that was sandwiched between to other logical partitions.

That should simplify things a little.

---

### Post by wizarddrummer on 2010-01-13
> **presence1960 said:**
> Don't rule out hardware causes for the reboots. Open up the case and make sure all your power connections are seated properly to your hardware & your motherboard & power supply.

I clean my case out every month. One time I must have hit the power cord from power supply to mobo and the connection at the mobo was not seated right. I experienced spontaneous reboots. After ruling out everything else I cracked open my case and found the problem. It definitely is not a problem with Ubuntu because you said it always does this. At least that is my read on what you posted.

Thanks for the reply. That's a great habit (cleaning out the case each month)  On my gaming rig I cut some circular pieces of the fiberglass that is used for home air-cond. filtration and placed them on the outside of the case at each fan opening. The air flow is diminished only fractionally. I didn't notice any temperature problem overclocking the bejesus out of it.

Each week I would vacuum the dust I could see collecting on the outside. 


There is nothing to "rule" out here my friend. This machine has a problem, and hopefully, the man who sold it to me will rectify it this evening.

I can only guess at this point that i could be a faulty power supply because sometimes nothing happens when you press the power button, or the mother board has issues, or ATI graphics card is not happy, or the memory could be faulty. I'm leaning towards PS, mobo and vidcard or a combination.

I used to build gaming computers for a sideline business. Checking connections, cables and an overall inspection is the first thing I did when I got the machine. 

Not to mention swapping out some hard drives.

When you have testing equipment and replacement parts it's easy to diagnose a problem. This I can not do anymore.

---

