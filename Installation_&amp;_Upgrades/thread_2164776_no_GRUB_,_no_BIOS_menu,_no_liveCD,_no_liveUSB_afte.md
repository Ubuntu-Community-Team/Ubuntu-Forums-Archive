---
title: "no GRUB , no BIOS menu, no liveCD, no liveUSB after 12.04 installation"
date: 2013-08-01
forum: Installation &amp; Upgrades
---

### Post by imundzana on 2013-08-01
i installed 12.04 64bit on my brother's lenovo ideapad y480 about a year ago alongside win7, and everything seemed fine and he used it a lot. recently it became slow and unresponsive.
long story short(ish),  i re-installed 12.04 using the same partitions. on restart the grub was gone, so i used a SuperGRUB2 disk to start up in ubuntu and i was checking stuff out and noticed the extended partition was misaligned. not cool. so i wiped out the extended partition that had / and the swap and did a fresh install hoping that would fix the misalignment issue. after the install (but before restart) i checked disk utility again, and it didn't have the misalignment warning any more.  it did say there were "a few bad sectors"...but it said that before i started changing things.

at this point, not much is happening. when you push the power button, the lenovo screen comes up with "press F2 for setup" and "press F12 for boot device selection menu" 
   if i let it try to boot, without a liveUSB plugged in i get a black screen with the white _ in the top left. it's not even blinking;)
   if i press F2 for BIOS menu, i get the same black screen with the white _ in the top left.
   if i press F12, it does come up with the list of devices (EFI USB, SATA HDD, SATA ODD (Disk drive), USB HDD, and Network Boot). i have tried all those, with the 12.04 liveUSB which i have successfully used several times, and with a SuperGRUB2 disk and a Boot Repair 64bit disk.  
no matter which option i choose, it goes straight to a plain black screen, with no evidence that it's working on anything (such as read-sounds from the disk drive or blinking pendrive light)


i've been doing this for a while, but please feel free to talk to me (and explain things) like i'm a noob. i would appreciate anything i can learn from this experience, and if at all possible, i would especially love to get my brother's computer up and running before he leaves for college soon!
thanks!
-zac

---

### Post by TheFu on 2013-08-01
I'd assume bad hardware at this point. Bad disk controller, bad cable, bad HDD.  Try replacing each ... and be certain you have great backups!

---

### Post by oldfred on 2013-08-02
Bad alignment of the extended partition is not an issue as you do not write to it. It is a container for the logical partitions in it which normally are aligned. But if not an SSD or new hard drive with 4K sectors, alignment is not even an issue with any partition.

A few bad sectors could be hard drive failing. But you still should get into BIOS and still should be able to boot from a flash drive if it is bootable. But if you mis-installed and corrupted flash drive it may be an issue.

You can test hard drive by removing it and plugging it into another computer to see if you can read it, what Smart data from Disk Utility or Disks shows.

Sometimes just a full powerdown, remove battery & hold powerswitch to deplete any remaining power totally resets a BIOS that gets lost.

---

### Post by imundzana on 2013-08-02
@TheFu: that's no fun... thanks for the input though!

@oldfred: hmm, i didn't know that about extended/logical partition alignment. thanks!  the HHD is a 1TB "seagate st1000lm024 hn-m101mbb" and i believe it does have 4kb sectors, but i could be wrong. i will redo the liveUSB and check that out. i will also try testing the HDD in another computer. i did try the battery removal etc, but no change. 

thank you for your time and the quick replies! i'll keep you posted as the saga continues...

---

### Post by TheFu on 2013-08-02
Ah ... didn't see the "no BIOS" - could be that the BIOS battery is dead or something catastrophic - cracked motherboard, blown PSU, bad memory, and I've seen failing video cards cause really strange things too.  Are there any beeps from the machine before boot?  That was how old-school motherboards gave critical feedback.

Hopefully, it isn't anything too expensive. Pulling the BIOS battery and trying to boot should tell if that is the root cause. Just the settings won't be saved. If the machine is connected to the wall all the time, it might be just fine til a power spike. I dunno.

---

### Post by imundzana on 2013-08-02
ok, here's the latest: 
i pulled out the hard drive. with the hard drive out, i can access the BIOS menu, i can boot from a liveUSB and i can boot from a liveCD of Boot Repair.  
however, even if i put the hardrive back in after beginning to boot into one of those things, Gparted and Disk Utility don't see that it's there. i don't have another laptop with the same type of hard drive connector to run any tests on it.

the Boot Repair disk created this: [http://paste.ubuntu.com/5940958/](http://paste.ubuntu.com/5940958/) but like i said, the hard drive was in it's slot, but it wasn't reading it.

in the BIOS menu, i tried disabling EUFI and then i put the hard drive in again, but got the same problems as before (black screen)

so. that's what's up.

---

### Post by oldfred on 2013-08-02
If UEFI/BIOS does not see drive, then no system will see it, and then Boot-Repair cannot report anything.

If BIOS is not showing it I doubt that Disks or Disk Utility will read the Smart Status, but you may want to see it that shows anything.

---

