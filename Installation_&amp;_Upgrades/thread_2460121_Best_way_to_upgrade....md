---
title: "Best way to upgrade..."
date: 2021-04-02
forum: Installation &amp; Upgrades
---

### Post by pengyou2 on 2021-04-02
I have an ASUS mobo with an i5 now, 16gb of ram and 2 hd - an ssd and mechanical with Ubuntu 18.  I want to add m2 memory to it and make it the system disk.  I also want to add 2 more video cards and more hard drives and a second network port.  What is the best way to stop (unwind, power down, etc) the present system so that I don't lock up the 2 hdd in the system?  Not talking about electricity.  A couple of years ago, an old mobo died, and I had trouble accessing the hard drives that were connected to that system after I got a new mobo.

---

### Post by grahammechanical on 2021-04-03
In my opinion, electricity has everything to do with what you are trying to do. 

1) Make one change at a time and test to see if the motherboard UEFI settings utility recognises the change and if the OS still loads and recognises the change. Make all the changes at once and you will have difficulty locating the changed component that is causing the problem. Start with upgrading the memory.

2) Shutdown the operating system in the normal way but remember that electricity is still going to the motherboard. There should be an LED built into the motherboard that indicates that the board still has power going to it. There should be an on/off switch on the back of the power supply unit (PSU).

3) Take all necessary precautions against the transference of static electricity from your hands and clothes to the electrical components, especially the memory sticks. If I was answering this question two days ago I would have recommended wearing a full length rubber diving suit complete with flippers. Although I was born on 1st April I try not to be an April's fool. :)

4) I suggest adding the additional drives before adding the additional video cards. Again test that each drive is recognised by both the UEFI setting utility and the OS before adding the next drive.

5) The new video cards will surely need drivers. So, it is at this point that the OS may mess up. If the OS is presently using a proprietary video driver then revert to using an open source video driver. Again, install one additional video card at a time and test to see if it is recognised by both UEFI and OS. Is the present video card built into the motherboard? You may need to use the UEFI settings utility to disable an inbuilt video card so as to use the additional video card.

6) Be prepared to reinstall the OS at any point and after all new components are added. The OS boot loader should be able to recognise the drive with the operating system on from its UUID (Universally Unique Identifier). So, changing the SATA connector location should not cause a problem. But remember, in Linux a drive connected to SATA1 becomes sda. Change the SATA connector and we change how the OS labels the drive. The UEFI settings utility will give any drive on SATA1 the boot priority. 

7) Become familiar with what we can do from Ubuntu's Recovery menu. We access recovery mode from the Grub boot menu when we select Advanced options for Ubuntu and select a Linux kernel with recovery mode. We can do useful stuff from recovery mode.

Well, that is me finished. I cannot think of any more precautions that I would take. 

P.S. If the OS is older than the new video cards it may be that the Linux firmware (drivers) in that version of Ubuntu does not have drivers for those video cards. This may be reason enough to upgrade to a newer version of Ubuntu.

Regards

---

### Post by TheFu on 2021-04-03
m2 isn't memory. It is storage, yes?

Do only 1 change at a time.  With more devices, you'll likely need more power from the power supply. If the video cards need extra power, average PSUs wouldn't be able to support more than 1.

As for dealing with booting disks and mounting them, that's all about the fstab and how the settings in that file are configured.  Most of the time, UUIDs should be used for all mounts, but sometimes that isn't the real-world situation.  You'll need to modify that for the new drive and especially for new boot storage.

Good backup and recovery plans can handle completely new hardware.  Do yours?  If not, I think that's the best solution - develop a backup and restore process that isn't tied to any existing hardware.  If you work backwards from the final outcome, through the restore process, and finally to the backup solution which provides everything necessary for the restore to be successful, then you'll be much better off.
[LIST]
[*]My simple backups: [https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) (not exactly what I do, but very close)
[*]My restore process: [https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
[/LIST]

Ninja'd by  grahammechanical!

---

### Post by pengyou2 on 2021-04-05
Thank you VERY much!  Extremely helpful!  Can the OS be installed on the M2?

---

### Post by TheFu on 2021-04-05
> **pengyou2 said:**
> Thank you VERY much!  Extremely helpful!  Can the OS be installed on the M2?

Probably, but there are some odd situations between SSD firmware, BIOS, EFI, and motherboards where it doesn't always work.  I've never seen that myself, but there are occasional reports of failure, especially with EFI + NVMe storage.  m.2 is just a physical interface. 
There are other considerations too.  For example, I have a Micron 1100 SATA m.2 SSD. It fits into a slot on the motherboard and there is a BIOS setting to force that slot to be SATA.  On my desk, I have a Samsung 970 EVO NVMe m.2 SSD.  It fits into another slot on the motherboard which can only hold NVMe m.2 storage.  I specifically picked the 970 EVO for well-known quality, endurance, and standards.  I looked at other NVMe with other branding - some with names I've never heard about, but much less expensive.  I did a little research and found they didn't publish endurance numbers. I contacted Customer Support and asked for the detailed specs - which didn't include endurance numbers.  Saving $30, but not having a standard specification for all quality SSDs just wasn't worth it to me.  No more looking at Phaser SSDs again (don't actually remember the name anymore).

So the answer comes down to, "it will probably work, but you'll not know until you try."

---

