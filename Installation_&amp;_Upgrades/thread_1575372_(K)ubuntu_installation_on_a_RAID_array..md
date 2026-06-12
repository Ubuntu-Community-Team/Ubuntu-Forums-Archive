---
title: "(K)ubuntu installation on a RAID array."
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by menchi on 2010-09-15
Hello!

I have a stripe array of two 500GB harddisks, created with the bios-like program that comes with the motherboard (intel raid controller maybe) the motherboard is Gigabyte GA-EP35-DS3R. Windows XP (with the appropriate drivers) and Windows 7 see the array as one whole unpartitioned disk and install just as usual. However, when I install Kubuntu, the part manager sees the array, sees the windows' partitions, can create its own, but after the installation begins, a window pops up saying that the setup cannot create the ext3 partition. Anyone had this problem?

---

### Post by ronparent on 2010-09-15
Also known a 'fakeraid' (works fine anyway). The problem may be that the Ubuntu installer partition manager doesn't see a raid. This was an early problem with 10.04 and I've lost track of whether or not ot was fixed with 10/04.1. In any event use win 7 partitioner to shrink the partition to leave whatever space you want to allocate to Ubuntu as unpartitioned space.
Then boot the Ubuntu cd to a live session. Open a terminal and install a program called kpartx.

sudo apt-get install kpartx

Then, unless it has been changed, 10.04 installer will not create a raid partition. So at this point open the Ubuntu partitioner called gparted and create an extended partition for the entire unallocated space. Then create a formated ext4 partition within the extended for installing Ubuntu 10.04 to. You might as well create a swap space as well. Then within the same live cd session start the installer. When you get to step 4 of 7, select manual partitioning. In the next screen (now step 5 of 8) you will select and hit change the partition you formatted, designate an ext4 format, make sure the check block for format remains unchecked, and select '/' as the mount point (very important), and, close the change window. Designate the swap. Now hit forward. When you get to the step 8 of 8 window, hit the advanced button and select the first raid choice you are offered (in place of sda) and you are naw ready to proceed with the install! Now you will probably complete the install without error. If you get a grub fatal error, post and I'll tell you how to fix. 

If this all sounds more formidable than you were planning on, it is. It will probably be much easier with 10.10. But your best not to try that before it is formally released. I'll be happy to help where I can.

---

### Post by menchi on 2010-09-16
Thank you for the friendly and complete reply!
I'll try this as soon as I finish posting this, I'll probably create a primary parttion and place "/boot" there (because I'm using Truecrypt system disk encr for this test installation). So, the knack is to install kpartx and create and format the desired partitions using gparted and then just USE them within the installer.. sounds fairly easy. Brb 1h for results!

---

### Post by menchi on 2010-09-16
Ok, I got a GRUB error:

Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 524, in <module>
    main(oem_config)
  File "/usr/lib/ubiquity/bin/ubiquity", line 509, in main
    install(args[0], query=options.query)
  File "/usr/lib/ubiquity/bin/ubiquity", line 242, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/kde_ui.py", line 460, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/kde_ui.py", line 863, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 2566, in <module>
    install.run()
  File "/usr/share/ubiquity/install.py", line 418, in run
    self.configure_bootloader()
  File "/usr/share/ubiquity/install.py", line 1681, in configure_bootloader
    self.db.input('critical', bootdev)
  File "/usr/lib/python2.6/dist-packages/debconf.py", line 65, in <lambda>
    lambda *args, **kw: self.command(command, *args, **kw))
  File "/usr/lib/python2.6/dist-packages/debconf.py", line 86, in command
    status = int(status)
ValueError: invalid literal for int() with base 10: ''

---

