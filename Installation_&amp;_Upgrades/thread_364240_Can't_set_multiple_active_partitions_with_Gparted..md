---
title: "Can't set multiple active partitions with Gparted."
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by Thunderpunk on 2007-02-18
Hi all,  after reading about Microsoft's Premium Content protection in Vista I was so disgusted with what MS is doing that I decided to learn Linux. As a new user there are plenty of help files out there but I am stuck and could really use some help. 

The problem is that the Gparted utility on the latest System Rescue CD will only allow one active partition per physical drive. If I flag the EXT3 partition to boot then the NTFS boot flag is dropped and vice-versa. It's irritating as all get out. I need to activate my NTFS Windows partition and the EXT3 Ubuntu partition so that both OS's will load. Right now it's either or. If I flag EXT3 as bootable then I can't boot to the Windows Loader which I chose to use instead of Grub. Any suggestions? I downloaded version 2.19 of the System Rescue disc that contains QtParted but it won't mount my SATA DVD drive.

My system specs
Intel e6700 Core 2 Duo overclocked to 3.75Ghz.
4GB Corsair DDR2 RAM
2X Maxtor 500GB SATA 7500RPM HDD
1 Western Digital 300GB IDE HDD
1 Plextor SATA DVD-RW+ 
EVGA 8800GTX GPU
EVGA NForce 680i Mainboard
Creative X-Fi Gamer sound card

---

### Post by Herman on 2007-02-18
You will be better off to give up using the Windows bootloader and learn how to use Grub instead. You won't need more than one boot flag with Grub because Grub can shift the bootable flag around the partition table automatically for you with it's makeactive command.
You can do lots of other neat things with Grub too, just check the Grub Page in one of my signature links. Grub's a lot more fun than Windows bootloader. It's much easier to dual boot with too, or even multiple boot. It's made with that type of idea in mind.
If you are scared, you can back up your MBR first, so you can restore it again later if you don't like Grub. [Click Here for that]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd").

---

