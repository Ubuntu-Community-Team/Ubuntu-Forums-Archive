---
title: "install/update/upgrade trouble with Kubuntu 6.06 Desktop"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by jck on 2006-10-27
Hi there.  I hope I am putting this in the right forum.  I've tried many of the things from the forum and wiki to no avail.  Hence, I think something went horribly wrong with Linux's auto config on my install.

I am having several issues with Kubuntu 6.06 Desktop installation.  I'm doing this all from memory, so please forgive me if I forget something.

I am not a Linux "newb", but I am rusty as heck as it's been coming up on 2 years since I even booted Linux.  So, I can't remember what all to run to troubleshoot, and what directories to find things like config files and such.

Okay...the scenario.  I know this is long-winded, but I want to give everything about the process of the last few days that I can remember.

First, I will give my system specs:
ASUS M2N32-SLi Deluxe Wireless Edition Motherboard
    -AMD64x2 4600+ overclocked to 2.7GHz
    -Realtek RTL8187L Wireless
    -ADI AD1988B SoundMAX audio
    -2 x MSI NX7900GT PCI-Ex16 video cards
    -Latest BIOS Update (0704, I think)
    -2GB PC2-6400 memory (passed Memtest86)
    -3 x 250GB Seagate 8MB HDs in RAID1 (striping)

I have 2 partitions which are NTFS (250GB each), and a 3rd which has:
    -16GB FAT32 file-sharing partition
    -11GB Linux Swap partition
    -200-something GB Linux main partition

I had Windows XP Professional x64 installed on my box already.  I added the 3rd drive, configured it into my array, partitioned it with the 16GB FAT32 area, then proceeded to install Kubuntu 6.06 Dapper Desktop.

First attempt, video issues.  So, I re-ran install with the "noapic noacpi resolution=800x600 text" options under the F5(?) and it seemed to install and detect everything great and setup my partitions and GRUB automatically to make my machine dual-boot as I wanted.

Once I got into the OS, I tried to install the nVidia package for Linux that I downloaded to no avail.  Since video was working, I didn't fret.  The audio configured perfectly.  Surround adjustments work and all.

However, my wireless was not working.  I checked ifconfig and iwconfig and everything looked okay.  I did dhclient and it said it couldn't find anything to give a DHCP.  I thought that since things were supposed to be wrapped into Kubuntu since 5.1(?) for WPA management, I would be able to find the tool to make my wireless (designated by install as **wlan0**) WPA, put in my shared key, and go on.

I tried using "Wireless Assistant" and the "Network Settings" window, but there was no WPA option.

I then tried putting my router down to WEP 128...then WEP 64...then no data encrytion at all.  For some reason, the Network Assistant nor Network Settings nor dhclient could get a recognition/connection to my router.  I even made sure the MAC address for my machine was fine in the router still.  I even made some changes to config files that were suggested in the forums and wiki to no avail either (even created one file...wpasupplicant.conf I think?  to try and put in the entry for WPA-PSK and WEP to try and get things to work).

I downloaded KNetworkManager, NetworkManager, and WPASupplicant in their .deb packages and tried to do the apt-get update, upgrade, and install stuff.  All I would get is that they were all the newest already and there were 0 updates, 0 removals, etc.

I tried using the Adept tool, but I could not get it to read in those packages.  I did get it to recognize the Kubuntu 6.10 Desktop using the "sudo apt-cdrom add" and add it to the packages I could install, but I did *not* install any of those through Adept.

I have tried some of the other "update" and upgrade" and command line things I've found here.  I even tried the instructions from the Ubuntu Wiki about how to upgrade from 6.06 to 6.10 using the CD.  Still, nothing happens right.

gksu, ld, and some other commands can't be found when I try to run them.  sudo and other core OS commands (ls, cd, mkdir ) work...but, other peripheral commands like ld, gksu and others I've tried would not work.  apt-get works, but when I do the "update" option it will tell me that it's already newest.  when I do "sudo apt-cdrom add" it will mount, detect, update the list, then *unmount* the CD.  doing a "sudo apt-get install <package>" I will get at the end this "E: can't find package..." or something to that effect.  Would not even work when I put the .deb file somewhere like /bin in my PATH env variable.

If someone will give me the exact diagnostic commands to run or the files to list, I will be glad to post the outputs here in an attempt to get my wireless working (even have the driver download from RealTek for the thing waiting) and my video card driver from nVidia to drive my video cards.

I would appreciate any help anyone can give me.  All I ask is you be patient, as I am not remembering everything I learned a few years ago and I am relearning how to use Linux again.

I am trying to get away from MS and more dependent on the penguin.

Thanks very much.  Cheers.  :)

---

### Post by jck on 2006-10-28
Wanted to give an update.

I have since yesterday installed several versions of Linux...none would automatically detect my card...except...Kubuntu 6.10 Alternate.

However after I saw it once in my list, I noticed under the KNetworkManager that it had no WPA listing.

I went out to console and did a "dpkg -i" on my wpasupplicant (0.5.4) and it seemed to go fine.  No errors.

When I rebooted, there is now no Realtek wireless network device. :( 

Does anyone have any idea why installing the wpasupplicant package would make the Ralink wireless device disappear from my network devices list?  Do I need to reinstall my network manager?

Thanks.

---

### Post by jck on 2006-10-29
another update:

I got the card to come on and stay in place, but now the card will not activate. No little light on the back of the NIC.

I ran iwpriv, iwconfig, ifconfig, etc., in a hope that someone would be able to help.  I would post it here, but I'm afraid that I can't get it inside a scroll window and would clog the forum.  Have it saved however, and would be glad to post it if someone can tell me how.

I'm willing to try anything.  My next step is to try the 98/ME driver rather than the x64 driver, as I read somewhere that someone had no luck with the x64 driver under ndiswrapper.

Would appreciate any help

Thanks.

---

