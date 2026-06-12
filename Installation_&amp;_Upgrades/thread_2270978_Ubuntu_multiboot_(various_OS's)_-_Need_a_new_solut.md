---
title: "Ubuntu multiboot (various OS's) - Need a new solution"
date: 2015-03-26
forum: Installation &amp; Upgrades
---

### Post by LinuxAlexs on 2015-03-26
Hi

Right now I'm multibooting into multiple OS's.

I have three Windows OS's on one hard drive.
I have Ubuntu on a secondary hard drive.

I am using **Acronis OS Selector** which I wish to replace (and I'm certainly not replacing it with the default MS Windows solution).

The good thing about OS Selector is I could hide partitions from other OS's (so Windows is blissfully unaware) as well as as boot OS's on secondary hard drives.

Can somebody point be to the best method to do this with Ubuntu, please understand it's already installed. I don't mind looking at third party solutions either.
BTW I'm in the process of upgrading to the latest version of Ubuntu right now.

Thanks

Alex

---

### Post by oldfred on 2015-03-26
I assume you have BIOS installs.

Are all your Windows installs in primary partitions? If  so you can just boot from grub if you fix/repair each install to have its own boot files. But that only works if primary partitions as Windows only boots from a primary NTFS partition with the boot flag. It puts all installs in the one BCD in the partition with the boot flag. Then grub only finds one install to boot and from that install's BCD you can boot each Windows, but it is a two step process.

If already installed, move boot flag to anther primary partition and run Windows repairs to restore boot files to that partition.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)

---

### Post by LinuxAlexs on 2015-03-26
Hello oldfred

Yes BIOS.
All OS partitions appears primary although Ubuntu is on a the second disk (note I'm using a mirrored array).
I've checked with BCDEDIT and these windows installations do have their own standalone bootloaders, pretty certain.

Actually it looks like when I select Ubunu via Acronis OS it then moves to GRUB which boots Linux (check screenshots). I haven't tried booting Windows yet I would want to check how I can hide partitions before I do.

So I guess I need to do that, and then I need to move GRUB somewhere else ?


[IMG]http://s12.postimg.org/ibhpteyhp/linuxboot.jpg[/IMG]

Many thanks!

---

### Post by oldfred on 2015-03-26
Where do you want to hide partitions? If after you have booted in Ubuntu, you actually mount them in hidden locations, or mount read only.
It looks like grub2's os-prober has found all your other installs as it has added them to the menu.

Do not know about BIOS RAID or fakeRAID configurations.
       [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by LinuxAlexs on 2015-03-27
When an OS boots I want all the other OS partitions to be hidden from it.

I am assuming I have to change the MBR to point to Linux to get it to work now? Or should I make a dedicated partition? Having the boot on a secondary hard drive - um not sure it's a good idea or not... I have 141Mb FAT16 partition as you can see which currently contains the Acronis OS Selector software.

Cheers...

---

### Post by oldfred on 2015-03-27
RAID boots thru the MBR of the RAID not the MBR of the physical hard drive.

       Does not recommend "fakeRAID"
[http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/](http://aryklein.wordpress.com/2013/10/28/a-quick-guide-to-linux-software-raid/)
[https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID](https://raid.wiki.kernel.org/index.php/DDF_Fake_RAID)

If array0 and array1 are different, you may be able to install different boot loader, but not sure if then in BIOS you easily select like you do different hard drives? With hard drive, you install Windows boot loader to Windows drive sda, and install grub to Ubuntu drive sdb.

Example, change to your RAID device.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
"fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0
Hardware RAID drivers
[https://wiki.debian.org/LinuxRaidForAdmins](https://wiki.debian.org/LinuxRaidForAdmins)

---

### Post by Kenneth_Benson on 2015-03-27
If one of your Windows is 7 or greater, it uses the bcd to setup booting. Look on the net for EasyBCD, it makes a nice interface to setup multi-boots. (at least for me) ;)

---

### Post by LinuxAlexs on 2015-03-27
It was a while ago but I've already been through the fakeraid pain.

To be clear I have four hard drives leading to two mirrored arrays (check screen shot) so I think all is working correctly. Linux is only seeing the two arrays rather than 4 hard drives.

Just to be clear I don't want to use the MS solution to boot.

The question now is how to boot grub off a different partition (the first one perhaps, maybe wipe fat16) .. Can grub run standalone? I wonder if I can just... Move or copy it ... From the Linux partition...

And then there is the MBR...

---

### Post by oldfred on 2015-03-27
You should just be able to install grub to root of RAID.
Example in post #6 was a similar install of grub to a RAID MBR/root.

---

