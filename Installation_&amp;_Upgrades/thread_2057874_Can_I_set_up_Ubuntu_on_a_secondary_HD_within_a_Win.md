---
title: "Can I set up Ubuntu on a secondary HD within a Windows PC?"
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by timbo59 on 2012-09-14
I've touched on this elsewhere, but as it now seems necessary to go in a different direction I'll post here to follow up.

I have two PC's, one of which operates via Windows 7, the other an older unit in which I've been indulging my new passion for Ubuntu. I had an external Free Agent HD on which I'd backed up data for both, but after a recent clean install for the latest version of Ubuntu I ran into problems with the external drive as I was trying to put the data back - good lesson in having backup for your backup! The controller for the unit died on me (a common problem I've since been told) so I cracked open the case, removed the HD from it, and installed it in my Windows PC to verify that all was okay (my Ubuntu PC doesn't have room for a second HD so I couldn't put it there). 

The drive functions perfectly, but I have one BIG issue - a lot of the Ubuntu data stored on it won't get recognized by Windows, even though I'm not trying to open it in the Windows environment. All I've been trying to do is shift the data on to flash drives or DVD's in order to move it back to my Ubuntu PC, but because Windows is in the loop it's interfering with the process and sending out different error messages that the files are corrupted, no longer on the HD, the file names are too long, etc, etc - it's all BS, because I can take the same type of data from my updated Ubuntu PC, put it on a flash drive, stick it into the Windows PC, and up will pop the same error messages. So the data is still there on the HD, it's just that Windows 7 doesn't know how to deal with it and is having a fit.

I tried taking a different approach and linked the two computers this morning via our wireless network, thinking that this might be the way to bypass the problem. Nope. As soon as I tried transferring the data from the Windows PC to the Ubuntu PC via WinSCP, the same problems popped up with the files Windows doesn't like.

The data is too valuable to allow to slip away, so I'm trying to figure out another approach. I'm loath to put Ubuntu temporarily side by side with Windows 7 on the main HD in my Windows PC, because if I have issues trying to get it off the system it would take forever to re-tweak my PC. But can I put Ubuntu on the other HD that's now in my Windows PC, the one that came from the external unit that died on me? I don't know if you can boot two different operating systems from two different drives, on the same PC, but if I can it could solve my problem. I guess I'd have to look in my boot menu to see if it will allow booting from a second internal HD?

My other option (bear with me on this long post) is to take the existing HD out of my Ubuntu PC, stick in the problem HD that was used for backup, install Ubuntu on it without destroying the existing files, burn all the data I need to DVD's once it's installed, take it back out when complete, and put back the original HD. Then I can finally retrieve the data I need from the DVD's! Convoluted, but I think it would work?

Any thoughts, or should I just slash my wrists now?

---

### Post by Bucky Ball on 2012-09-14
I don't know how you are for cash but a really easy solution might be to buy an external hard drive dock, connect to the Ubuntu machine and shove the drive in. They're under AU$30 here in Australia. I have an eSATA/USB one for my laptop and a USB dual-dock for the other three machines.

This way you could use on either machine, if formatted in NTFS or FAT that is, and accumulate backup hard drives when required without having to buy the external cases too. ;)

How much data have you got to transfer? Even if you get the network going (Samba is your best bet) if you need to transfer in the Gbs you are going to be there some time ...

Good luck.

---

### Post by darkod on 2012-09-14
If you want to risk your data, keep trying to access linux filesystem with windows. :)

It all depends whether the partition is ntfs or linux type. Lots of the external disks, especially the network models, actually run a small linux inside them, so the partitions are linux.

How about this idea:
Plug the hdd into your windows PC (where you have the room for a hdd), but don't boot windows. Boot the computer with your ubuntu live cd (make one if you don't have it).

It should have no problems to see all the data, and you can copy it anywhere you want to (or have enough space). Burn DVDs, use usb sticks, another external usb hdd, what ever you like.

Just don't try to make windows see it since it's not ntfs usually.

In case the Free Agent was actually set up with linux software raid (common thing), you can also read it from ubuntu live mode but you need to add the mdadm package first. If this turns out true and you need help with that, just ask.

If the partition on the hdd really is ntfs, than the above can also work, linux is usually better reading ntfs partitions too. But in this case if windows was giving you read errors, it's very probable that not only the controller died, but that also part of the data is corrupt.

---

### Post by timbo59 on 2012-09-14
Just a quick post back while I'm digesting all of this. 

I'm virtually 99.99% sure the data hasn't been corrupted, and not just because of the test I did with the flash drive. I tried shifting some data across a few months ago, came up with identical issues, yet when I hooked the external drive back to the Ubuntu PC it read all the data without a hitch.

@ Bucky. Are you talking about an empty external HD case to slot the HD into, or something else? I tried hunting around for an empty unit this morning, but didn't have any luck. The only option seemed to buy one that already had a HD in it, rip the unit out, and put my one inside.

@Darkod. Okay, you lost me. Are you saying I can get Ubuntu up and running just from the install disk and transfer data onto my flashdrives? All without actually installing Ubuntu? I wasn't aware you could do that. I though the disk (which I do have) was basically just for installing the operating system?

---

### Post by oldfred on 2012-09-14
There are a lot of enclosures, many with different interfaces and hard drive sizes.

[http://www.newegg.com/Store/SubCategory.aspx?SubCategory=92&name=External-Enclosures](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=92&name=External-Enclosures)

I also like to have several USB flash drives. I have one with many ISOs installed as my boot, install  or repair systems flash drive. 
And I have another larger one - 16GB with a full install of Ubuntu in a 8GB partition with another 8GB for data.

---

### Post by darkod on 2012-09-14
Correct. When you boot with the cd it will present a menu with Try Ubuntu and Install Ubuntu.

The Try option will load a so called live desktop running from the cd without any changes to the hdd in the computer. No need to install it to copy data from disks.

---

### Post by timbo59 on 2012-09-14
Okay, kudos to Darkod. The suggestion to boot up from the disk and trial Ubuntu on my Windows PC worked like a charm. I got in, shifted a gigs worth of the Ubuntu data on to a flash drive, and everything, including the stuff Windows claimed was either unusable or unavailable, went on the stick. I double checked by transferring the flash drive to the Ubuntu PC and all the information was there.

So thanks a bunch. Same for everyone else who chimed in to offer advice. I was pulling my hair out trying to approach the problem from numerous angles, and it ended up that the easiest method proved the correct one. Given that I jumped straight into Ubuntu a few years ago via the fact I had a spare PC to play around with, I simply didn't notice at the time that the disk had a trial option, and of course since then I've just made regular updates and upgrades. 

So you learn something every day! 

Thanks again all!

---

### Post by Bucky Ball on 2012-09-14
No, not talking about an enclosure. I am talking about an empty hard drive dock. You supply the drive and you already have one.

**[http://www.lifehacker.com.au/2008/02/dock_your_old_drives_with_the_hard_drive_usb_dock-2/](http://www.lifehacker.com.au/2008/02/dock_your_old_drives_with_the_hard_drive_usb_dock-2/)**

---

