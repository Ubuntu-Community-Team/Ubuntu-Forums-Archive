---
title: "Problem Installing from USB-Install software &amp; ubuntu only recognize USB partitions"
date: 2018-01-02
forum: Installation &amp; Upgrades
---

### Post by atofarenji on 2018-01-02
Hi Everyone, 

Neewwbe here needing help.  I want to install on a Lenovo Yoga laptop/tablet 520-14lKB running under windows 10, a Linux partition alongside windows 10.

I tried different distributions (Ubuntu 14.04, 16.04, Mint Cinamon 18.03...) and same issue happen every time. The Ubuntu installer doest let me choose the type of installation and don't recognize my Hard drive partition to install the distribution into it. Only recognizes the usb stick.

Followed the below steps :

- Create a new partition on my Hard drive
- Get an USb stick formated
- Install the distro downloaded on Ubuntu torrent page
- Create bootable USB with Win32 
- Boot the computer on the USB stick - First issue : there is a error message in blue : [COLOR=#0000ff]system doesn't have any USB boot option. [/COLOR]I press Ok, and it launch anyway Ubuntu. The image works fine, i can use various Ubuntu software but installation doesnt. 
- when I launch install process, I NEVER get the install type options (Install alongside windows 10, erase Windows, something else...) 
- Arrive anyway in installation type window with the partition to select and I can only see the USB stick, no one of my Hard drive free partition nore windows partition appears.

Quick info about the computer :

- Bios type : UEFI
- System type : 64 bits 
- Fast launch of windows is turned OFF


Appreciate your help.

---

### Post by cmcanulty on 2018-01-02
It may be that you resized and or created the new partition from the live distro. Do the partitioning from windows. Go to computer-manage and create the new partition and make it ntfs. Then when you go to install ubuntu you can make it ext4 or whatever you choose.

---

### Post by atofarenji on 2018-01-02
Hi & thanks cmcanulty
I had done the partition from Windows & in NTFS, any partition (included this new empty nore nore basic C: one was appearing still). 

Anyway I Found a solution meanwhile after some more researches. Its probably adventurous but it works now. 
It look like my SATA mode wasn't in AHCI mode, so I changed it to this set up, and then it just worked fine. 
The only problem is that when i boot the computer, I need to enter the bios everytime and adjust the SATA mode to the OS i want to boot into (Windows/IRE or Mint/AHCI). I hope its safe way

Thanks again

---

### Post by cmcanulty on 2018-01-02
are you hitting f10 after editing bios to save changes? also read this to pick which to boot into, good luck


  	
	
Does a Windows Boot Manager menu appear, or a GRUB menu appear for you at boot time? If not, hold down the LEFT SHIFT key from cold boot and a GRUB menu should appear. You can select which OS to boot from there. If you'd like to make Windows the default OS, you can edit /etc/default/grub and change the line GRUB_DEFAULT=0 changing the 0 to a 1 or 2 or 3. Let us know if you need more help. Cheers, Al &#8211; heynnema Sep 1 '16 at 18:06

---

