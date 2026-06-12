---
title: "Windows install with linux on the HD: help"
date: 2005-11-20
forum: Installation &amp; Upgrades
---

### Post by juantxorena on 2005-11-20
Greetings.

I'm not sure if I can ask this kind of question in these forums, but I don't know where to ask.

I have 2 HDs, both connected to IDE 1. Breezy is installed on HD on master. I want to install ruindows XP pro on the HD on slave-IDE 1. When I try to install, The installer says that he must write some archives on the first HD, so he won't install anything. I tried to ruin MBR with the utility fixmbr on the windows installer, but he keeps saying that he can't install anything.

Maybe if I change the HD position in the IDE channel I could install ruindows, after then I will revert the HD position, but I don't know if that would work.

Any help? Please?

---

### Post by pompeyjohn on 2005-11-20
I think that is an XP feature. How about... 

disconnect the master (ubuntu drive)
install onto the slave xp drive (I think a slave drive can stand alone if not - use the cd/dvd drive)
then reconnect the xp drive
edit Grub on the master drive to include the new OS

That should work.... I think. Please dont have a go at me though, if it doesnt. I am just trying to help. I am not responsible for your data etc etc....

Or, you could use an extended mbr program such as bootit which would create an mbr for each os if you want. Really though, you'd be best sticking with grub as it is free and I am fairly confident it can boot a partition regardless of which drive it is on.

hope that helps

---

### Post by Hairy_Palms on 2005-11-20
yes unplug the ubuntu hard disk then install windows as normal. then once its installed plug the ubuntu hard disk back in and open /boot/grub/menu.lst then add a section at the bottem of the file that says
> title Winbloze
    map (hd0) (hd1) 
    map (hd1) (hd0) 
    rootnoverify (hd0,1) 
    chainloader +1 
    makeactive
then you will be able to choose ubuntu or windows from the grub boot screen.

---

### Post by juantxorena on 2005-11-20
I installed windoze on the master HD (I've changed the HDs phisically), and Ubuntu is on the slave HD. But I would like to have Ubuntu in master, I don't like the idea of linux being a slave of windows.

Next week I have some time, so I'll try those things. I will remove the linux HD while installing ruindows, then I will conect linux HD as master and windows as slave, reinstall grub and modify, if necessary, /etc/fstab and /boot/grub/menu.lst using live CD.

Thanks for help.

---

### Post by pompeyjohn on 2005-11-20
I am happy to hear that you have sorted out the situation, and have a working installation of Ubuntu.

When it comes to Master/Slave settings you might want to consider the following. 

In terms of hardware,... before IDE came along, you could only connect one device connected to one port on the motherboard. This was quite restrictive. Then IDE came along, and was such an improvement that with it you could easily connect two devices to the same port. 

Now, though there was a problem - how do you tell the devices apart? So they called one Master and one Slave. 

That **really** is the only difference between them. The master device can run no faster than the slave device. And in hardware terms, the master has no 'authority' over the slave device.

Software wise... one OS can not be 'the master' of another OS. In the situation you described both OS are treated as equal by the hardware, and neither has power over the other. 

When a computer boots up it checks something called the MBR (master boot record) which is a little bit of information which tells it.... on which disk and partition the operating system is.

So you can think of the MBR as seperate to your hard disks and the whole master/slave situation.

One of the options when you install Ubuntu is to install a bit of code called Grub to the MBR. If you do Grub then can boot any OS from and partition. It is quite clever! So even if your master drive is running Windows, it is Linux that gets it going ;) 

I hope I have not confused you or explained things badly/incorrectly. I think you have done the right thing in swapping the HD's around physically and installing windows to the master HD. If you are happy with the disk sizes, then I would leave things as they are. There is no real performance gain or benefit to swapping them round. Whichever way they are, if you have Grub in the MBR then both are being run by Linux :D 

Hope that helps,

---

### Post by juantxorena on 2005-11-20
Thanks for the background info. When I talked about windows being the master of linux I said it in a metaphorical way. I know that both SO will work properly. But I don't use windows for months ago, I just keep it "just in case". Because of that, I prefer to have windows in the slave HD, because the day I decide to throw windows away, it will be lot easier, without modifying partition tables, reinstaling grub and the like.

---

