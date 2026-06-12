---
title: "Advice on Inspiron 14z (5423), dual booting."
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by ivanbgp on 2013-01-19
Hello, here's my situation.

I recently got this dell, because i managed to burn my 4 year old reliable laptop's mother board. :(

Well the thing is that this new computer came with some new "features" that make the preinstalled W8 run ¿nicer?:
-UEFI compatible bios
-GPT partitioned hard drive
-a 32Gb SSD for fast booting and HDD cache. (Both HD's were in some pseudo RAID configuration in order to use Intel Rapid Storage Technology to speed the system up)

The first thing i did was downgrading to W7 because of compatibility problems. Apparently i did it wrong since i couldn't get to format the disks with the RAID configuration necessary to use iRST. BTW to do this i set the bios to AHCI mode, and partitioned again as GPT.

Now to the point:
I'm trying to install to install ubuntu 12.10 . It's been troublesome since the beginning, it didnt boot the Live USB where [this]("http://ubuntuforums.org/showthread.php?t=2097509") was helpful.
Then a black screen appeared after i tried to "Try ubuntu" from the usb. That was solved by setting nomodeset to enter the installer as descibed [here]("http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it").

Now, i got to this point:

[CENTER][ATTACH]230291[/ATTACH] [/CENTER]
 
Where it does not recognize the windows already installed. 
I left an empty HDD partition when installing windows. If i set a manual partition (my approach is the following):
[CENTER][ATTACH]230290[/ATTACH]

[LEFT]will grub be able to recognize the windows installation?
[Here]("https://help.ubuntu.com/community/DiskSpace") it says that it is required an EFI partition (beacuse i am using UEFI mode), during windows installation, it made itself this partition:

[CENTER][ATTACH]230293[/ATTACH]

[LEFT]Should i create a new one?.

Finally the advice part :-k
I realized that i could just reinstall windows in legacy mode instead of UEFI and using MBR instead of GPT, and install ubuntu on "auto-pilot". Is the easiest way the best?
That way iSRT wont work, and the SSD will be just another drive (on wich i could install ubuntu). 

But i wanted to do it the way that im doing it because i feel it would be a waste not to use those annoying but maybe useful "features" that the pc comes with. 

Thanks in advance. And please excuse (and correct) my english it is not my native languaje.
[/LEFT]
[/CENTER]
[/LEFT]
 [/CENTER]

---

### Post by ivanbgp on 2013-01-19
I went ahead and did what i said above.(I got kind of impatient :C )
I created those new partitions and installed ubuntu on UEFI successfully. So there was no need to re-install windows on BIOS Legacy mode or use MBR partitioning. That was a good thing.

There happened some things that i was not expecting from this installation. First I was expecting Grub to manage the start-up. It didn't happen. Apparently that's what the UEFI is doing right now on the bios and that was what the EFI boot partition was for. I didn't created a new EFI partition I just left the one windows created when installed. So, to change an OS on start up i have to press F12 and there i can select between windows or ubuntu, I can set the default from BIOS settings using F2.

Ok, no GRUB or LILO it feels kind of awkward. I found the following article usefull. 

HERE IT's A BETTER REFERENCE THAN MINE TO MAKE A DUAL BOOT ON EFI (At least he does know what he's doing):

[http://askubuntu.com/questions/226969/how-do-i-create-a-multiboot-environment-using-lvm-for-your-buntu-operating-syst/226982#226982]("http://askubuntu.com/questions/226969/how-do-i-create-a-multiboot-environment-using-lvm-for-your-buntu-operating-syst/226982#226982")

Before doing this i tried to read a lot, for not messing up my system or at least do the less re-installations possible, but still this was not the result i was expecting and i should have been more informed on the EFI system and what it does. I believe i didnt mess up because of pure luck and really skilled engineers (thanks) that design stuff to be dumb(like me) proof.


The other thing: I didn't formatted the SSD, and installed Ubuntu on the empty space i left on the HDD with the hope I could use Intel Rapid Storage Technology in the future. Well after installation i started on W7 and run the iRST setup. This was what the result:

[CENTER][ATTACH]230319[/ATTACH][/CENTER]

It looks like it is working. But i don't really notice any performance improvement. It also appears to be missing the "accelerate" tab. I have found that it is because another intel driver is missing (or i couldn't get to install it) because i did not set up RAID before installing Windows.

I believe this thread is over.

If anyone wants to extend on what i did (Explaining what happened). Or knows how EFI works. Or if iRST is really usefull or should i get rid of it. Feel free to do so. Thanks, and again excuse my English.

---

