---
title: "First time installing problem, Ubuntu 10.04, 64bit, dual screen setup, 4k WD disk"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by AgentLinux on 2010-06-20
I have tried installing "ubuntu-10.04-desktop-amd64.iso" several time, but I am stuck and want to try get some helpful feedback on this problem.

Checking iso install file against MD5sum show identical hash, with the hash listed on ubuntu website for this particular iso file.

**Expectations:** To boot up my machine and pressing F11 on boot to get to selecting DVD rom as boot device, then all should have gone well from there.

**Problems:**
After I select the DVD rom as the boot device, to continue the boot process, I see a Ubuntu screen of sorts, then I see another more prominent Ubuntu screen with 5 white/red dots on it, which seem to indicate something loading. However it all seem to end with either a blinking cursor on a black screen, or simply a black screen. Even after several minutes pass, there is no change.

However, on my second attempt earlier on when I tried installing from the iso file on a prepared USB drive, I did somehow managed to get to see an install menu, and it first froze after clicking next on stage 3 I think, which was the keyboard settings, prior to stage 4 which I think is the harddrive space configurations. What happened was that I pressed Esc key I think, and voila I managed to exit the frozen start menu, and ended in the ubuntu desktop which seem to work ok. I do not remember if I manged to exit this desktop environment in a proper way.

On my machine, I have a new Western Digital 1.5 TB Green EARS drive (4k sectors, emulated as 512B in windows), but this is simply on the machine and was not intended for installing linux on it. I wonder if simply having this 4k harddrive might have interfered with the Ubuntu install.

Unknown if BIOS need updating. Afaik, there doesn't seem to me, to be any clear indications at the motherboard manufacturers website that a BIOS upgrade might be needed, though there are some upgrades available. Seen here on this webpage: [http://www.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=1&prod_no=1212](http://www.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=1&prod_no=1212)

**System:**
• MSI P35 Platinum, (revision 1.2, iirc)
• Intel Quad Q6600 processor, safely overcloced and running stable at 3.4 GHz.
• 8 GB ddr2 ram, no overclock
• ATI Radeon 5850 
• Western Digital Raptor 74 GB, 10.000 rpm
• Western Digital Caviar 500 GB, 7200 rpm
• Western Digital Green 1.5 TB, EARS, 5400-7200 rpm (4k disk!, but not used for linux)
• A couple of USB2 external harddrives connected as well.
• DVD rom drive (fairly new)
• Dual screen setup, I tried having one and both screens connected on install.

• Current OS = windows Vista 64bit

---

### Post by AgentLinux on 2010-06-20
SOLVED

I have now managed to install Ubuntu 10.04 LTS. Without really knowing for sure why it worked this time around, I suspect it had to do with the following:

1) Disconnecting second monitor, having computer turned off
2) Re-connecting the first monitor to the upper DVI slot on my gfx card.
3) On boot, booting from DVD rom, pressing the arrow keys while booting from DVD rom, to get to see the install menu.

---
Where is my Ubuntu os installed? I have no idea. And I cannot even tell from browsing the drives inside Ubuntu. I guess it was installed on on either my 74 GB raptor or 500 GB caviar disk.

I suspect I have to install the proper ATI drivers, to get to connect my second monitor, given my experience with how it works on Windows. I guess I could simply try adding the second monitor though.

I now have a boot manager, which I apparantly can use for booting into the new Linux, or the older Vista install. I have not yet tried booting into the older Vista install, but it looks like it shouldn't cause a problem.

I found the install menu for Ubuntu rather awkward. Lacking information for me as a novice to know where Ubuntu would be installed. Apparantly it turned out ok, but as I said, I do not know what disk it ended up on.

---
Apparantly, I can view files on NTFS partitions from all my drives, which is very nice.
Having a 4k Western Digital Green drive on my system did not cause any issue, and I can browse though the stuff on that disk.

---
I found it odd that the system window showed one of the four processor cores to run at 100% when doing nothing at the desktop, which it never did on windows vista. I do not trust that core to be running at 100%, and don't know how to verify that one core is actually running at 100%.
Edit: I installed Ubuntu 10.04 anew, this time on the harddrive I wanted it on in the first place, and now I have normal cpu usage levels.

---

### Post by AgentLinux on 2010-06-20
Update: Using the disk management tool, I now see that I managed to install Ubuntu on the wrong harddrive. It apparantly ended up on my WD 4k drive, however I have had no problems.

On boot, it seems like I have to press the keyboard while booting to get to use the boot loader. Else I end up with a blinking cursor.

---

