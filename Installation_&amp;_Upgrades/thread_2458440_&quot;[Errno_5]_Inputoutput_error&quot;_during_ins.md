---
title: "&quot;[Errno 5] Input/output error&quot; during installation"
date: 2021-02-24
forum: Installation &amp; Upgrades
---

### Post by draxdomax on 2021-02-24
I've spent 5 hours browsing the web for this, trying out things... I am out of ideas...

New Clevo laptop with NVMe. This model is sold elsewhere with Ubuntu pre-installed. So, I believe the model is somewhat supported.

1] Downloaded '20.04.2.0 LTS' from ubuntu.com
2] Verified download: "ubuntu-20.04.2.0-desktop-amd64.iso: OK"
3] Created bootable USB stick with that ISO using Rufus. USB boots fine and loads installer (GUI, not terminal)

Installer passes "checking disk" and lets me through the installation options wizard dialogues.
While the screen says "almost finished copying files", I get: "[Errno 5] Input/output error"

~ Tried different USB sticks. All my disk-on-keys are quality brands bought from reputable retailers and used carefuly
~ Tried different USB ports
~ Wanted to test my RAM but memtest86+ is not available in grub
~ Wanted to test my SSD SMART but that option was grayed-out in Disks
~ Instead of SMART from GUI, ran the 'smartctl -a ___' command on all my devices: "No Errors Logged"

I have a "magical gut feeling" that nothing is wrong with ISO/USB/RAM/SSD... Could it be some BIOS setting that Ubuntu does not support?

Any ideas what could be wrong? What to try?

---

### Post by CelticWarrior on 2021-02-24
Does it have Windows?

---

### Post by draxdomax on 2021-02-24
It came with a non-registered "for testing" windows, which the Ubuntu installer removed.
Now, I am stuck with no OS...

---

### Post by CelticWarrior on 2021-02-24
Are you selecting to "erase and install.." or did you partitioned in advance? If so, did you created the EFI partition?

---

### Post by draxdomax on 2021-02-24
"Erase disk and install Ubuntu".

Now, that you mention it, I think the first time I tried, GParted gave an error.

Does this mean that the "Erase disk..." still keeps some "state" of the disk?

How to really obliterate everything and start from absolute zero?

---

### Post by tea for one on 2021-02-24
> **draxdomax said:**
> How to really obliterate everything and start from absolute zero?

After you have booted into the live session:-

Open gparted > Device > Create partition Table > Select gpt

---

### Post by Impavidus on 2021-02-24
To start from absolute zero, you could write zeros to the drive. Typically, just the first megabyte should suffice. That will destroy partition table etc. and stop any confusion gparted or the installer might have. Then create a fresh partition table.

Have you actually executed the smart test? smartctl -a displays the result of the last test. To execute the test, use```
sudo smartctl -t [test] [device]
```where [test] is the test you want to run (I always run the long test, taking about an hour on my hardware) and [device] the device you want to test. See```
man smartctl
```for details.

---

### Post by draxdomax on 2021-02-24
OK Guys I am out of the woods!

What did it for me is super crazy: I am trying all sorts and finally gave up and just tried a REGULAR way, while taking screenshots to... I don't know, maybe bother someone at work about this :)
While taking screenshots, I fumbled the wifi password and the installer proceeded without internet ("download updates" was disabled)

Installation proceeded without problems. 

I didn't stop there!

I went through another installation cycle, got the internet on - bam, errno 5!

Tried again, without internet - no problems :)

---

### Post by draxdomax on 2021-02-24
Thanks for all your time and valuable advice!
It turned out to be something different but without your support, I wouldn't even have bothered so much and I would have given up a long time ago!

---

### Post by ActionParsnip on 2021-02-24
Please mark as solved if the issue is gone

---

### Post by draxdomax on 2021-02-25
Sorry, I tried to do that. Couldn't find the way. I even searched "sol" in the whole web page of both reading and editing...

---

### Post by draxdomax on 2021-02-25
ah, there's an "advanced" editing stage, which is kinda the same as regular editing, only with the things you actually want, hidden :)

---

