---
title: "trouble getting jolicloud/ubuntu to work on my triple boot hackintosh"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by teklife on 2010-11-12
greetings, and pardon the intrusion if this is the wrong place to post this. i am having trouble with a jolicloud install, and since joli IS ubuntu based, i figured this might be a good place to post this. 

i have a dell mini 10v which was triple booting mac os x 10.6, windows 7 ultimate, and ubuntu netbook remix 9.10 wonderfully. i 

i decided to switch it up a little, and resized the windows and UNR partitions to 2 of equal size, to install jolicloud, and mint 10 rc, or ubuntu 10.10. 

i have created a multiboot usb drive with jolicloud, & the others [http://liveusb.info/MultiBoot-v3/inst](http://liveusb.info/MultiBoot-v3/inst)... and followed these directions: 

"choose ext3 or ext4 format as you please with a mount point of /. Resize that partiton smaller by 2 to 4gbs for a swap area and choose forward. The next pane to pay attention to is 7 i believe where it asks where to install grub click advanced. Make sure to choose sda3 or whatever partition you installled jolicloud. Thats it reboot pull out usb when it tells you too and when chameleon boots up hit the space bar to toggle between os's." 

the install went smoothly, however, when i reboot, there is now an error message that says "operating system not found" this happened earlier in the day, and i was able to get the mac os side back by reinstalling the NBI(netbookinstaller)/chameleon bootloader, but not the jolicloud. the partitions are invisible on the mac side. 

i then tried to install ubuntu 10.10, which worked and i was able to boot into. the grub bootloader screen listed jolicloud and ubuntu 10.10. 

10.10 was bootable, but still could not boot up joli. 

this was in the same partition i assume, because i then installed mint 10rc into the other partition, and then the grub bootloader listed mint 10rc, ubu 10.10, and joli. 

os x partition was listed as well, both 32 bit and 64 bit, but would not boot:( 

mint 10 rc, based on ubuntu, would boot, but could not install the wireless drivers which popped up to be activated(i have no access to ethernet). 

for some reason, ubuntu didn't have this problem, and the wireless worked fine out the box, therefore, activating the wireless drivers worked(i assume these driver are downloaded from an online source). my wireless card worked fine under the jolicloud live usb btw, which was sweet. 

so now, of the 4 os's installed, only ubuntu 1010 booting and working with wireless. 

re-install NBI and chameleon again. mac is back, all the linux's lost:( 

i try again to reinstall joli. this time formatting the partition that ubu1010 and joli were on, and again, following instructions above. formatted ext4 with 3gb swap (4+GB for os), selecting the proper sda on step 7, etc. 

install finishes, and, "operating system not found" again. what am i doing wrong here? is there a certain order to install these systems? i am grateful for any help.

---

### Post by lemming465 on 2010-11-13
It sounds like you are have a dispute over which OS owns the MBR (first disk sector).  I'm not sure what the answer would be in your case.  Traditionally I've done my multiboot systems with either grub from Ubuntu or EasyBCD from windows to control the OS selection, and then made sure that each OS installs its secondary boot loader to its own partition.  The directions you quote are in line with that. But I don't know if the jolicloud and OS/X will cooperate.

---

### Post by teklife on 2010-11-17
thanks lemming. i was never able to get jolicloud to work on this netbook, and eventually gave up, even tho i would very much like to play with it. i will give it another go when my woman arrives with her lenovo s10-3t (who comes up with these stupid names?), which is a multi-touch tablet/netbook. 

i now have the netbook triple booting osx.6, ubu 10.10, and pinguy os 10.10

these 3 os's all boot fine, but sadly the 2 linux os's don't work that well. wireless issues with both.

how different is jolicloud under the hood that the 2 that work fine are both ubuntu, but not joli?

---

