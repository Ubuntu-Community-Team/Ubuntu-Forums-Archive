---
title: "Working install from other PC doesn't work on my PC"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by rosshildick3d on 2014-03-06
I had windows 8. I dont like how user friendly it is (the irony...)  I uninstalled it. I installed xubuntu as its similar to what we use at work. It didn't work for some reason... I tried installing it on my friend's PC (convinced that the instillation file was broken, somehow)
and it worked o_O

So now I have a good, working version of xubuntu on my hard drive (internal) which I have brought back to my (now OS-less) PC and I get taken to the following screen:

Filesystem unkown,
entering rescue mode
grub> _

(Ive seen the root/prefix fix online, and it does nothing)
and If I turn it off and take that same hard drive back to my friend's PC, it works fine.



So here's what I'm asking:
a) why doesnt the install work on mine in the first place.
B) why doen't a working install from another PC work on mine?



Thanks you intelligent bunch of peoples.

---

### Post by rosshildick3d on 2014-03-06
Something else worth mentioning... I also get an error about unable to find root/ or something too D:

AND... when I try to go onto the live session (try ubuntu) from the installer CD, It loads up, but my keyboard and mouse are unresponsive.

---

### Post by Bashing-om on 2014-03-06
rosshildick3d; Hello ,

Well, like this: Windows8 equals UEFI equals a "hard row to hoe" to get it to recognize/accept a different operating system.
I hope these links shed a bit of light on the situation and promote a means to get xubuntu recognized:
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Maybe you can reset your BIOS to a leagacy mode ?

With no regret I say I have no Windows8/UEFI experience, so all I can do is give you some pointers.
But do let us know how it goes, additional help from those who do know will be pending.

is a little bit
[INDENT][INDENT]better than nothing ?
[/INDENT][/INDENT]

---

### Post by rosshildick3d on 2014-03-06
Thank you for that, but it doesn't really shed any light at all. Maybe its probably my extreme ignorance but none of that seems at all relevant. (its definitely me.) but I and completely uninstalled windows and the hard drive is blank so surely it doesnt matter if I installed with eufi or not?

---

### Post by Bashing-om on 2014-03-06
rosshildick3d; UHMMM,

Yeah IT do matter, UEFI is the replacement/augmentation for the traditional BIOS .. UEFI is embedded to the motherboard.
Now, there are lots of hoops and jumps one must make, and every manufacturer makes us jump through different hoops just to install an operating system. Sometimes, I have observed, it is a real challenge just to find the hoop the manufacturer wants us to jump through.

Maybe something like this will apply:
[http://distrowatch.com/weekly.php?issue=20121126#qa](http://distrowatch.com/weekly.php?issue=20121126#qa)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

time marches on
[INDENT]things do get better
[INDENT][INDENT][INDENT]gotta make the adjustment
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by rosshildick3d on 2014-03-06
ah thanks - makes things a lot clearer in my head... kindda... but I have tried both types and neither work.

I managed to get boot loader installed and running (which didn;t fix anything) using the live session (try ubuntu) thing which gave my this link: [http://paste.ubuntu.com/7046765/](http://paste.ubuntu.com/7046765/)

---

### Post by Bashing-om on 2014-03-06
rosshildick3d; Welp;

I too am playing catch up on UEFI, there is bunches that I do not know, and perhaps what I think I know is wrong.
So, here goes next:
UEFI also equals GPT partitioning - I think - Such that instead of the traditional msdos ( no relation to Micro Soft) partitioning with a Master Boot Record to control the boot process; GPT uses EFI and must have a small separate boot partition to contain the boot code. Now, GPT is the way to go as it does have many advantages over MBR. So ultimately what ya want is the system booting in UEFI mode from the UEFI setting, and install 'buntu in UEFI mode also. I have not done it so I am poking in the dark here.
IF the system is set up to boot in UEFI mode, - I think - the install Wizard will pick that up and automagically install in UEFI mode ? In this instance - I think - the installer will make up that efi boot partition, and install the 'buntu operating system, And everyone will be happy.

As you can take that hard drive to another box, and it boots fine -> I bet ya 'buntu is installed in MBR mode, and your system you want 'buntu on is in UEFI .. the two are non-compatible booting methods.

So in my humblest of opinions - in the long term - you set your machine up in UEFI mode and (RE-)install 'buntu. 
Aside: the boot screen is different between EFI/MBR boot methods. MBR's screen has the stick figure and keyboad emblems at the bottom of the screen, EFI is textual.

With all the above said, I welcome anyone's input to correct and/or alter my thinking.

[INDENT][INDENT]it is all 
[INDENT][INDENT]a process of learning
[/INDENT][/INDENT][/INDENT][/INDENT]

---

