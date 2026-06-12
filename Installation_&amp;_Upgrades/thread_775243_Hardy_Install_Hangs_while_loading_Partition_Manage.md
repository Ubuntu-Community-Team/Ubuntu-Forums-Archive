---
title: "Hardy Install Hangs while loading Partition Manager"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by opaldraggy on 2008-04-29
I would appreciate help with my situation:

I am attempting to do an install of Hardy, but the install keeps hanging while trying to start up the partition manager. To double check the partition manager works, I loaded up the live CD, and ran GParted manually. I was able to create the necessary partitions.

However, when running Install from the liveCD, before it finishes loading, the partition manager hangs on "Detecting File Systems..."

I don't even know what to search for, in terms of helping myself. Any direction would be very appreciated.

Thank you!

---

### Post by overdrank on 2008-04-29
> **opaldraggy said:**
> I would appreciate help with my situation:

I am attempting to do an install of Hardy, but the install keeps hanging while trying to start up the partition manager. To double check the partition manager works, I loaded up the live CD, and ran GParted manually. I was able to create the necessary partitions.

However, when running Install from the liveCD, before it finishes loading, the partition manager hangs on "Detecting File Systems..."

I don't even know what to search for, in terms of helping myself. Any direction would be very appreciated.

Thank you!

Hi and welcome, have you checked the cd for errors and  
Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by opaldraggy on 2008-04-30
Thank you for the welcome, and the quick response.

The hash checks out, so the CD is (very likely) fine.

---

### Post by martrn on 2008-04-30
Firstly I would say, make sure you backup your system fully, before repartitioning your hard drive to ensure if anything happens then you have a backup copy of all your important data.

I personaly would download a copy of [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/") or other partitioning managing software to partition any or all of hard drives before you install hardy.  You would need to format the filesystem before installing any operating system, which can be done from the gparted CD.

Do not tell the live installer to re-partition the disks to use ntfs systems, because in effect you are again repartitiong the disk to use a different file system, and will loose any windows installation.

---

### Post by opaldraggy on 2008-04-30
It seems that a reboot managed to get this under control. Strange.
But thank you for your time.

---

### Post by opaldraggy on 2008-04-30
> **martrn said:**
> Firstly I would say, make sure you backup your system fully, before repartitioning your hard drive to ensure if anything happens then you have a backup copy of all your important data.

I personaly would download a copy of [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/") or other partitioning managing software to partition any or all of hard drives before you install hardy.  You would need to format the filesystem before installing any operating system, which can be done from the gparted CD.

Do not tell the live installer to re-partition the disks to use ntfs systems, because in effect you are again repartitiong the disk to use a different file system, and will loose any windows installation.

In conclusion: My problem was that I wasn't even getting to the part of the install process where I would be asked if I want to partition manually or automatically. As an alternative, I used GParted that came on the LiveCD -- but after partitioning, still couldn't get the install on the LiveCD to get past step 3 (Language, keyboard, time zone) -- and on to step 4, where it asks about automatic or manual partitioning.

After rebooting (and error checking -- which turned up no errors), the installer managed to go on to step 4 without a problem, and is currently going through the rest of the install process.

Thank you for your time.

---

### Post by ian320 on 2008-04-30
I am having a similar problem, and a reboot doesn't help. After selecting my keyboard layout and pressing Forward, the progress bar appears, goes all the way across while setting up the partition manager, and then disappears. It never actually goes to the partition manager screen, but just stays with the busy cursor on the keyboard layout screen.

Any ideas? I have restarted twice and still no luck.

Thanks!

---

### Post by martrn on 2008-04-30
> **ian320 said:**
> I am having a similar problem, and a reboot doesn't help. After selecting my keyboard layout and pressing Forward, the progress bar appears, goes all the way across while setting up the partition manager, and then disappears. It never actually goes to the partition manager screen, but just stays with the busy cursor on the keyboard layout screen. Any ideas? I have restarted twice and still no luck. Thanks!

It appears to be reading the disk badly.

Firstly have you cheked to see if the disk burnt correctly and the image MD5 sums check out.  If you are sure that this ok then.....

1.  [Visit https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

And boot the cd with acpi=off OR noacpi This is The Advanced Configuration and Power Interface (ACPI) which can do things like turn cd/dvd drives on or off, so turn it off to stop it if it locks up here.

And boot the cd with noapic, this disables the Advanced Programmable Interrupt Controller (APIC) which is a more intricate Programmable Interrupt Controller (PIC) containing a magnitude more outputs, much more complex priority schemas, and Advanced IRQ management.

Other than that you could download the alternative cd and installing ubuntu using the alternative CD.

---

### Post by ian320 on 2008-05-01
Thanks for the quick reply martrn.

As it turns out, I neglected to detach my external hard drive, and I believe scanning the 500gb behemoth was just slowing the process to a crawl. After removing it and restarting, it hung a bit at the same part, but went eventually after a minute or so and I was able to install completely.

---

