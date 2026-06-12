---
title: "Clean install"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by Rich J on 2012-01-27
Hi and apologies if this is the wrong place to post my question!

I have been a Windows user since Win95 and am currently running Vista SP2.  Recently I decided to move over to Linux (for many reasons) and have been evaluating Ubuntu 11.10, installed on the Vista machine via WUBI.  v11.10 is very different to what I'm used to but searching these forums and elsewhere tells me that there will be one or another Linux distro that I will be able to get along with!

My question is - my Vista version is an OEM pre-installed copy so I have no installation disks should things go wrong.  (I do have a recovery disk)  If I wanted to do a completely clean install of Ubuntu would the installation 'take' in regard to the motherboard?  My query is in relation to a post I spotted about Windows OEM machines somehow having an 'imprinted' motherboard chipset that would only allow Windows installation files thus preventing a fresh install of another o/s.  Is this so and, if so, is there a method by which the chipset could be cleared/flashed to overcome this?  

My computer is up to spec and well capable of running any Linux distro - Ubuntu runs very well alongside Vista (but not the other way around!) but I prefer to have just the one o/s on the machine.  Windows has proven to be very temperamental, especially in the boot/shutdown area with a lot of BSOD's for no apparent reason - insofar as it usually boots at the second attempt with no problem!

Any advice or pointers to relevant guides/documentation would be appreciated!

Thanks in advance

Rich J

---

### Post by 2F4U on 2012-01-27
I haven't heard anything about OEM machines forcing you into a particular OS. I've installed Linux on several OEM machines which used to run Windows without any problems.
Did you try to run a liveCD? It would be nearest to doing an installation since it would boot Ubuntu without booting Windows before.

---

### Post by darkod on 2012-01-27
I don't think you have anything to worry about except one MAIN thing: making unpartitioned space for ubuntu.
Usually your hdd belongs to windows, either on a single or two (three) partitions. You need to shrink or delete a partition to create unpartitioned space for ubuntu.

Usually it would be shrink. Windows doesn't like to be shrinked with the ubuntu installer which is exactly what would happen if you start the install, select install side by side, and use the slider to specify how much space to "cut" from windows.

Instead, shrink it with windows Disk Management. Open the application, select the partitions you want to shrink and resize it. Restart vista few times because it will want to do disk checks after it's been resized. Make sure it reboots few times, and it can boot fine.

Only then start the ubuntu install and it will use the unpartitioned space you created (DO NOT create any partition into that space from windows, ubuntu doesn't install on ntfs!!!).

Also, in Disk Management take a good look at your partitions layout and plan your disk. If you already have 4 primary partitions existing, you can't create a fifth partition even after creating unpartitioned space. At maximum you can have 3 primary partitions for this to work.

---

### Post by oldfred on 2012-01-27
There is nothing wrong with dual boot, if you have the space on your hard drive. I still have my XP installed but rarely use it. In fact I hate to use it now as updates/reboots take forever.

I would make sure your data is backed up. Then I might make a full image copy of Vista that you could restore. Is your recovery disk just the Windows repairCD or the Vendor restore image of the hard drive?

Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

If moving from wubi:

Uninstall wubi:
[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Megaptera on 2012-01-27
Hi Rich J,
Is it perhaps this issue with Windows 8 that you've heard about (quote)"An interesting story doing the rounds that, at first glance, looks like FUD, but it&#8217;s not. Microsoft could indeed use the fact that Windows 8-compliant PCs must replace the BIOS with the more modern UEFI, and this could be used to lock Linux (and even previous versions of Windows) out from new PCs." From such places as: 
[http://www.zdnet.com/blog/hardware/yes-uefi-secure-boot-could-lock-out-linux-from-windows-8-pcs/14897](http://www.zdnet.com/blog/hardware/yes-uefi-secure-boot-could-lock-out-linux-from-windows-8-pcs/14897)

and this (quote) "Ultimately, there&#8217;s no valid reason for Microsoft locking Linux out of the UEFI firmware, and so it won&#8217;t. In doing so it would spark the most monumental antitrust lawsuit possible, and it&#8217;s incredibly unlikely that Microsoft cares that much about the 1 or 2% of users who install Linux on a Windows PC."
From: [http://www.extremetech.com/computing/96909-microsoft-could-lock-out-linux-on-windows-8-pcs-but-it-wont](http://www.extremetech.com/computing/96909-microsoft-could-lock-out-linux-on-windows-8-pcs-but-it-wont)

---

### Post by Rich J on 2012-01-28
Hi Guys and thanks to everyone for their replies!  I'll try and answer all your points if I can...................

I've read that MS support for Vista ends in 2012 and have no desire to (yet again) upgrade to a new o/s so I've given Ubuntu a try.  At present I'm not sure if Ubuntu is the right distro for me as v11.10 with Unity seems hard work for any newbie to Linux?  I installed Gnome which has helped a little but maybe Mint might be more user-friendly?  No matter.......

I ran Ubuntu as a live CD, liked it and decided to try dual-boot.  For some reason it wouldn't install correctly (no Grub for instance) so I went the WUBI route and got the disto on, also using a 3rd party partition manager to shrink the drive.  This set-up works reasonably well - Ubuntu gives no problems - but from time to time Vista throws up a BSOD, usually after installing updates.  One issue for me is the constant need to update Vista to patch security (tho this will end soon anyway) and the attendant problems that now surface when I do, along with the fact of running 2 o/ses means that information gets fragmented - 2 email clients for example - where finding relevant info becomes a pain!  Which o/s do I boot into to find what I want?!  A small thing but very irritating to a tidy mind!  (My wife reckons I'm borderline autistic - I just like things to be NEAT!)  My better half is very technophobic and struggles even with Vista so any move to unfamiliar territory is daunting for her!  I'm slowly bringing her round............!  

I take your point, Oldfred, about dual-boot but I would prefer just the one o/s - for me that removes any issues outlined above and also saves me having to make a perfectly good computer redundant.  I'm sure that if I simply changed over then all would be well (as long as I put my wife's familiar software on - she uses Firefox and Thunderbird quite happily as it is!).  Btw my recovery disk was made from the vendor copy already on the machine.

Thanks again guys for putting my mind at rest, I'll investigate all the links you've provided and see how I go from there.  Sorry it turned into my life story...........:)

Rich

---

### Post by dino99 on 2012-01-28
Unity is the default choice when installing, but then you can install gnome-session-fallback to get the "classic" gnome look & feel :) and purge all the related unity packages if you dont want/need/like it.

---

### Post by oldfred on 2012-01-28
I originally has issues trying to learn Ubuntu and all the book marks were in Firefox & emails in Thunderbird in XP. My wife had me rebooting into XP all the time. Then I learned to create a shared (then FAT now NTFS) partition and put the profiles into the shared. Then we were able to sometimes use XP for old stuff, but lots of the day-to-day needs were also in Ubuntu.

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

I also copy the entire profiles to my portable (which also is dual boot) in a shared NTFS partition and have the same email & bookmarks history on the portable.

---

