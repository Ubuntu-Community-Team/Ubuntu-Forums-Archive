---
title: "why is my ubuntu more than 4GB?"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by DJTurboToJo on 2007-06-14
Hi there,

I started installing Ubuntu on my laptop maybe one year ago. After that I had several updates and recently I updated feisty. My root partition is only 5GB and it s going to be full soon. I uninstalled all games and some other stuff I personally dont need. However I never installed a lot unnecessary programs. I always used apt-get or the Add/Remove tool. So I guess the programs are automatically stored somewhere in root. Is that right?

So, I read about the minimum requirements and it says you should have around 2GB. So why is my Ubuntu so fat? I have three different types of kernels to choose from in the boot manager. What can I do? 

I tried to expand my ext3 partition. My primary partition is a huge NTFS one. The extended partition has an ext3, swap and FAT32 partition (in this order). So, I cut off 2GB of my NTFS partition but now I dont know how to expand my extended partition and also my ext3 partition. In Gparted everything is locked so I read I could try to do that with a Live CD. 

Once I tried with Partition Magic in Windows and when I was shifting my ext3 partition I run into trouble as my bootmanager didnt work afterwards. 

Any other suggestions folks?

Thanks,
DJTurboToJo

---

### Post by zvacet on 2007-06-15
> So I guess the programs are automatically stored somewhere in root.

In the var/cache/apt/archives 

You recived many updates and new version of programs in one year time and that is why your root is become big.You can solve this with 

```
sudo apt-get autoclean
```

This command will delete just old versions of programs,leaving newest one.

---

### Post by zero-9376 on 2007-06-15
All the .deb packages you get through apt/synaptic etc are stored in /var/cache/apt/archives i have 431 in there and thats just with a clean feisty plus updates.
You should also be able to remove kernels through synaptic just get rid of all but the latest if its working.
When you expand a partition like you said I think the UUID for the partition will change which explains why the system wouldnt boot afterwards, you might try changing the grub entry to point to root=/dev/hdX rather than root=UUID, or u can find the new uuid and reinstall grub with the live cd. 
With GParted you cant do anything to a partition if it is mounted which is why it shows the lock. If you use the livecd you will have better luck but for me Gparted/gnome/ubuntu always remounts the partition when it reads the table or something, to solve this i have a gnome-terminal open and sudo umount -a when the partition gets mounted. The partitions being automounted also stops operations from working but if you keep unmounting them it should be fine.

---

### Post by DJTurboToJo on 2007-06-15
thanks,

i did the autoremove and autoclean command and it cleaned 800MB. So now I've 1.6GB free that should be okay for a while.

Thank you guys,
TurboToJo

---

### Post by mikewhatever on 2007-06-15
What about the old kernels. Search in synaptic for 2.6.17, the number of Edgy's kernel.  If installed, you sure do not need them.

---

### Post by wpshooter on 2007-06-15
> **zvacet said:**
> In the var/cache/apt/archives 

You recived many updates and new version of programs in one year time and that is why your root is become big.You can solve this with 

```
sudo apt-get autoclean
```

This command will delete just old versions of programs,leaving newest one.

Is there some **GOOD** reason why they do not write a GUI for this function, so those of us that are not terminal line specialist, can do this without having to look for or ask about this command every time ?

Thanks.

---

### Post by stchman on 2007-06-15
> **DJTurboToJo said:**
> Hi there,

I started installing Ubuntu on my laptop maybe one year ago. After that I had several updates and recently I updated feisty. My root partition is only 5GB and it s going to be full soon. I uninstalled all games and some other stuff I personally dont need. However I never installed a lot unnecessary programs. I always used apt-get or the Add/Remove tool. So I guess the programs are automatically stored somewhere in root. Is that right?

So, I read about the minimum requirements and it says you should have around 2GB. So why is my Ubuntu so fat? I have three different types of kernels to choose from in the boot manager. What can I do? 

I tried to expand my ext3 partition. My primary partition is a huge NTFS one. The extended partition has an ext3, swap and FAT32 partition (in this order). So, I cut off 2GB of my NTFS partition but now I dont know how to expand my extended partition and also my ext3 partition. In Gparted everything is locked so I read I could try to do that with a Live CD. 

Once I tried with Partition Magic in Windows and when I was shifting my ext3 partition I run into trouble as my bootmanager didnt work afterwards. 

Any other suggestions folks?

Thanks,
DJTurboToJo

You gave an entire OS a whole 5G of hdd space?  You should have done 15G minumum.  WOW.  First boot up using the Ubuntu LiveCD.  Bring up gparted.  You will have to decrease the partition right next to your Ubuntu partition.  Once that is done increase the Ubuntu partition.  Hit apply and let it do its thing.  You may have to go into windows and run a defrag and a chkdsk /f on the partition you are decreasing.

---

### Post by merlinus on 2007-06-15
> **wpshooter said:**
> Is there some **GOOD** reason why they do not write a GUI for this function, so those of us that are not terminal line specialist, can do this without having to look for or ask about this command every time ?
.

Yeah.  So when your GUI dies, and your video card heads to the south pole to visit with the penguins, you will still be able to run your computer.

;)

-merlin

---

### Post by zvacet on 2007-06-15
> Is there some GOOD reason why they do not write a GUI for this function, so those of us that are not terminal line specialist, can do this without having to look for or ask about this command every time ?

Nobody is expert when begin to use new OS.Just take your time and you will feel comforteble with CLI.But now just applicstions<accessories>terminal and copy/paste command I posted to you.Hit Enter and that is all.

---

### Post by wpshooter on 2007-06-15
> **merlinus said:**
> Yeah.  So when your GUI dies, and your video card heads to the south pole to visit with the penguins, you will still be able to run your computer.

;)

-merlin

Back in the 1980s I used to run an old Unix system and practically everything was command line driven **BUT** this is **NOT** the 1980s anymore !!!

---

### Post by gimfred on 2007-07-01
> **wpshooter said:**
> Back in the 1980s I used to run an old Unix system and practically everything was command line driven **BUT** this is **NOT** the 1980s anymore !!!

True, and mostly the Command Line Interface (CLI) is not needed no matter what operating system is used. However, even (sic) MS Windows does not always recognise the complexity of monitors that is needed to use a graphical user interface. (I personally have had better luck with Linux in regards to GUI's utilising my hardware.) 

If the hardware is mis-recognised, then a CLI is required to repair the hardware configuration (assuming you do not have a Live CD, of course). Because a CLI is simpler/less hardware intensive, a CLI is virtually always possible assuming it is not a true hardware fault (if it is simply a badly configured system, for example). Linux has more potential for repair, as the GUI systems most often use the underlying CLI, preventing different data being stored. At worst, they only use the same configuration file, so rely on the same information. 

If you can get to a CLI in Linux, you have all the power of a GUI as well as greater functionality potentially due to the advanced CLI tools. When a similar problem happens in Windows, you had better hope the problem is solved with copy or delete commands, or it would probably be easier to just re-install.

(I'm to understand that IF you can use the Windows CLI to do $task, you have to keep using it to do the same task the GUI and CLI do not always use the same configuration files. This results in configuration fragmentation; a problem waiting to manifest. I could be mis-informed.)

The bottom line is, I would hate to be forced into a position where I could not get to a CLI unless the GUI was working, despite being essentially a solely GUI user. Thank goodness that we still have a 'fail-safe' mode. A computer can still be used without a GUI! If the computer control fails in a modern car, the car stops! (okay, much more complex but would be fantastic if you could turn off the computer control and the car would still drive you to the workshop)

---

### Post by Demz on 2007-07-01
> **wpshooter said:**
> Is there some **GOOD** reason why they do not write a GUI for this function, so those of us that are not terminal line specialist, can do this without having to look for or ask about this command every time ?

Thanks.
why are you using Linux if you cant handle a simple command line?

---

### Post by gimfred on 2007-07-01
come on, that was just unnecessary, just as the CLI is for a set-up machine. Most Windows users don't get how powerful the CLI is, making references to it alarming. Often the ```
CLI = complexity
``` to them, instead of ```
CLI = more options or do more at once.
```
The majority of the time, I use synaptic. It would be good if helpers started encouraging the nervous to use something like it. With a few well placed hints few people would be intimidated :)

---

