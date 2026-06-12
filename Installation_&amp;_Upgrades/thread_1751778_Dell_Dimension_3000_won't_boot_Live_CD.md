---
title: "Dell Dimension 3000 won't boot Live CD"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by GregHill1950 on 2011-05-07
I have a Dimension 3000 with 2GB RAM, a 500 GB disk with two, 250 GB partitions, one for XP and one for Linux. The machine has a 1 GB Ethernet expansion card to replace the 10/100 MB integrated Ethernet card. The BIOS was upgraded to A03, the latest  version.

My initial attempt to boot the Live CD of Kubuntu 10.04.2 32-bit desktop left me with a blank screen, the CD-ROM drive stopped and the hard disk light on. I used the power button reset to re-gain control of the machine.

On the next try, I removed the "quiet splash --" from the end of the boot options, and the machine got much further, but did much complaining about sr0 which I believe is a reference to a software RAM drive.

I went through the BIOS setup screen (hit F2 on boot to access) and under "Integrated devices:Network Interface controller" I turned off the built in network interface since the machine is using the plug-in card mentioned above. I also put the floppy disk drive at the end of the "Boot sequence" parameter.

I rebooted again with the same deletion of the "quiet splash --" from the end of the boot options and the boot took me to the desktop!

Alas, when I tried to install 10.04.2 from the desktop, the installation died at the 15% point with "[Errno 5] Input/output error". The included explanation pointed at problems with either the hard drive (brand new in my case) or the CD-ROM drive or the CD itself. I'm too tired right now to pursue this further, but I will try burning a new CD at a lower speed as suggested by the error's help information.

I'm also still concerned about the earlier complaints about sr0. It is conceivable that the problem with copying the files to the hard disk could relate to problems with a RAM buffer that is used in the copying process. I mention this to remind myself to pursue that as a possible culprit if re-burning the CD doesn't help.

---

### Post by mörgæs on 2011-05-07
Have you tried booting from USB?

---

### Post by GregHill1950 on 2011-05-08
I haven't tried booting from the USB. But I have made some progress.

Before I went to sleep, I rebooted the Linux CD and ran the memory test. I let it run for over 15 hours/11 passes and it found no errors.

I re-burned the CD at the slowest speed that InfraRecorder would allow me to specify: 1 times. Although InfraRecorder started at 1 times, it very quickly raised the speed on its own to about 20 times.

When I re-booted using that CD, I used the "Check CD" function on the Linux boot menu to verify the CD. It took awhile, but the CD checked clean.

When I then booted it as a "try Kubuntu" with "quiet splash --" removed from the boot string, I noticed that all of the sr0 complaints that I had earlier seen were gone to the degree that I could read the messages as they flew by.

I was able to boot into the Kubuntu desktop, so I tried to install from there. I got past the 15% point, so I'm assuming that the CD was busted before. However, when I got to the 93% point, the installation threw an error message regarding dpkg not being able to correctly install linux-headers-2.6.32-28-generic. I looked in /var/log/syslog for more details and one of those messages indicated that there was not enough device space, although it did not say which device. I find this puzzling since I gave the installer over 250 GB of disk for the various Linux partitions.

As an aside, I have noticed that each time I go through the installation process that the the installation disk partitioner is never satisfied with the layout of the partitions and always makes one or more changes. That doesn't seem right to me, and I now have about 10 subpartitions in the Linux portion of the disk. I wonder if some of those partitions are now such a small percentage of the disk that perhaps that's the cause of the "device has insufficient space" problem.

After copying all of the information in the error message, I let the installer continue and it seemed to complete. However, once I rebooted, I was unable to log in with my credentials, and when I tried to reboot into XP, that also failed because XP couldn't find <Windows root>\system32\hal.dll. So, until I fix something, the computer is a brick.

I have to say that I hate M$, but it has been 10 years or more since I've had this kind of trouble installing a M$ OS. If Linux is ever going to overtake M$, Linux is going to have to have a less fragile installation procedure.  I want to get some real work done, and wasting the better part of a week reading Linux docs just to install it is not my idea of either a good or productive time.

---

### Post by Quackers on 2011-05-08
I believe sr0 errors refer to the cd drive. not ram.
Have you checked the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Did you use the "check for errors" facility on the cd?

These are the basic starting points for troubleshooting.

---

### Post by mörgæs on 2011-05-08
I can't help with the Windows error, but for the rest you could try:

- disabling floppydrive in BIOS
- deleting all Ubuntu partitions
- install using the alternate ISO

More ideas here:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by GregHill1950 on 2011-05-09
> **Quackers said:**
> I believe sr0 errors refer to the cd drive. not ram. 

Thanks for correcting my guess. It was hard to tell from the error messages which device it was.

> **Quackers said:**
> 
Have you checked the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Did you use the "check for errors" facility on the cd?

These are the basic starting points for troubleshooting.

As I said in my last post, I checked the CD and it verified 100%. Based on results, I believe that the first CD I burned must not have been correct. I did not bother to spend the time to verify that belief by checking the first CD for errors since I now have a known good CD.

I failed to mention that I tested the MD5sum on the .iso, but I guess that would be implied by the fact that the CD did verify.

---

### Post by GregHill1950 on 2011-05-09
Thanks for your suggestions, morgaes.

I am currently re-installing XP using a disk image. I re-initialized the disk first which wiped out all of the Linux partitions as well as the XP partition. I'm operating on the theory that the Linux disk partitioner chopping up the Linux partition so many times is perhaps at the root of the remaining Linux problem.

I'll try to install 10.04.2 again with "quiet splash --" removed and see if I get a good result. If I don't, I'll try using the alternate CD.

I read through your 8 step guide twice and found some information that may be helpful. Since I'm now able to boot to the Live CD and since I'm doing a clean install with no existing applications, many of your steps are fortunately unnecessary in my situation.

Thanks again. I'll update this thread again when I know more.

---

### Post by GregHill1950 on 2011-05-09
After re-installing the XP disk image, I discovered that the MBR was corrupted and that I could not run XP. I could see by means of the disk partitioning software that I used to re-initialize the disk that the restore operation had put the image on the disk, so I decided to fix the MBR by installing Linux which would overwrite the MBR with Grub and give me a way to select XP.

Since I believe that a major problem was the way that the installation partitioner chopped my Linux partition up into too many pieces, I left the hard disk partitioned as a single, Windows partition. Previously, I had tried to "help" the installer by creating a separate Linux partition; I think that only confused the installation partitioner.

I booted the Live CD and selected the "Try Kubuntu" option with the boot parameters modified to remove the "quiet splash --" options from the end of the parameters. I was taken to the desktop. I clicked on the "Install Kubuntu" link shown on the desktop.

When entering the Linux installer, I remembered that one of the error messages I had seen during an earlier installation attempt had said something about an out-of-date installer being a potential problem source. So, I clicked on the "update the installer" link and was surprised to see the installer be updated. It had never occurred to me that an LTS image would not be completely updated to begin with, so I'm glad that I tried updating. I cannot say whether or not this helped, but I think it probably did.

When the installer got to the disk partitioning step, the proposed partition change was to take the back "half" of the single Windows partition and turn it into a Kubuntu partition. That looked more "sane" to me than any of the partition arrangements proposed during my previous installation attempts.

The installation completed without a problem, and when I rebooted the machine, Grub did offer an option to boot XP which I selected and XP did boot. (XP automatically ran CHKDSK to verify the filesystem, rebooted and came up without further problems.)

I rebooted again and selected Linux which came up, accepted my credentials and went to the Linux desktop.

Now that I've got a working Linux system, here's a list of what I believe were the significant actions to getting Linux installed on my Dimension 3000:

1. Verified the .iso file using MD5sum.

2. Used the slowest write speed that my image burner supported, and verified the burned CD using the tool provided on the Live CD.

3. Verified that the BIOS settings reflected the actual hardware state of the machine.

In my case, I turned off the integrated Ethernet function since I was using an Ethernet expansion card. Had I been using an expansion video card, I would have turned off the integrated video function as well.

4. When setting up the disk, I started with a single Windows partition and let the Linux installer handle the creation of the Linux partition.

5. Changed the boot parameters to remove "quiet splash --".

6. Selected "Try Ubuntu" repeatedly as I was trying to figure out the above setup until I was able to boot to the desktop.

7. Once I got to the desktop, I used the "Install Kubuntu" link that was provided on the desktop.

8. Clicked "update the installer" on the first page of the Linux installer.

Thanks again to morgaes and Quackers for their assistance!

---

### Post by Quackers on 2011-05-09
Glad you got things working.
Step 4 however might not go so well with Vista or Windows 7 installed. They don't like their C: partition being resized by tools other than Windows tools and a defragmentation should always be performed first (even with a new system).
In fact, your XP system demanded a chkdsk be run before it would boot.

---

### Post by mörgæs on 2011-05-09
Good, please mark the thread 'solved'.

---

