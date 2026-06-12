---
title: "No boot device available"
date: 2016-02-12
forum: Installation &amp; Upgrades
---

### Post by rollinggrapes001 on 2016-02-12
Hey all,

Recently got a Dell Poweredge 2950 II (old, but free). Trying to get Ubuntu Server 15.10 set up on it, but after install, it will always give me the error "no boot device available." Currently using hardware raid with the perc5/i controller. I have 3 500GB HDDs running RAID5, and 2 1TB HDDs running RAID 0 (individual), so 2 RAID 0, 1 RAID5. Attempting to install on the RAID5 drives. Installation goes fine, on reboot, doesn't find a bootable device.

Ran through UbuntuLive and ran the boot-repair tool. Logs [here]("http://paste.ubuntu.com/15033798/").

I've ran through BIOS attempting to find any settings that might cause issues (i.e. fastboot or something), but I've been unable to find anything.

/sda and /sdb are both freshly wiped drives, and /sdc is the Ubuntu Server setup, with only Ubuntu Server.

Ideas?

---

### Post by rollinggrapes001 on 2016-02-15
Alright, lots done, but not a lot of progress.

Reformatted all my drives and re-setup RAID with the OS being set to drive 0 instead of 1 as it was before. After reinstalling the OS, I was a little worse off. Instead of it saying "no boot device detected", it instead just froze when trying to boot off of drive 0. I booted in to Ubuntu live, used sudo parted -l to ensure that all the drives were detected and had the MBR where it should be. On a hunch, I tried setting a boot flag to /sda1 (using sudo parted /dev/sda set 1 boot on), and unsurprisingly, it didn't do anything. I ran through boot-repair again ([logs]("http://paste.ubuntu.com/15088694/")), and I was able to get in to GRUB! Since Ubuntu was the only OS detected, I selected it, and, well, we're stuck again... It appears to freeze up. After selecting Ubuntu, my monitor will go into powersaving mode for a moment, then toggle back on, but it just displays a black screen. Nothing changes from that point on. Backlight on, powersaver doesn't kick in so it's getting a signal, but not a thing going on...

---

### Post by MAFoElffen on 2016-02-16
So you are using Dell 2950 Gen 2's? With the Perc Raid controllers? (I have 3 Dell PowerEdge 2900 Gen 3's) Which version of the Perc/5I Controller? (will show in the BIOS messages.) Check your bios version of the system BIOS and your firmware version of the Perc controller. It's worth the trouble to have them up-to-date.

So in the HBA Bios of the controller, after you setup your logical array's there's an option there to set your boot order... Are you setting that? Next in the System Bios, there is an option there on Boot order.

The as the BIOS messages come by, notice what it says after it inits the Perc controller and shows the table of your physical and logical drives.

Just for reference-- Three things that is strange with those... #1, that controller is cap'ed at 2 TB limit each drive. Will not recognize anything bigger. #2, If you give up on the RAID of that controller and want to do JBOD, that controller does not have a JBOD mode, But... To simulate/do JBOD with that controller, Just do single drive RAID 0's for each drive to pass the drives through. #3. Even though it has hot swap bays, the controller does not recognize a new drive until it goes through a boot sequence.

(Can you tell I love mine?)

I never had problems with mine, with using Ubuntu... but there are some peculiarities on how to set it up.

---

### Post by MAFoElffen on 2016-02-16
Saw the second post... 

As the BIOS messages end, press the left shift button repeatedly. When the Grub Boot menu shows, press the <E> key to enter an edit mode of the grub menu... Go down to the line that says "linux" and go to the end of that line. At the end of that line, append "radeon.modeset=0" without the quotation marks... Press the key combination <Cntrl><X> to boot...

the GPU is a Radeon Rage... and that boot option will sort out the VGA graphics mode for you. To add that to your grub menu:
```

sudo vim /etc/default/grub

```
Add it to the line that says
```

GRUB_CMDLINE_LINUX_DEFAULT=""

```
So it reads as 
```

GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeline=0"

```
Save and exit. Then to pick up the changes in Grub:
```

sudo update-grub

```
Then you should be good.Tell me how it goes.

---

### Post by rollinggrapes001 on 2016-02-16
Thanks for the ideas!

Booting to GRUB and then editing it to boot didn't work. However, going into advanced options, then recovery booting, then going from recovery -> resume boot, worked fine. I then used VIM to edit that line. It had originally had "quiet splash", but I modified it as requested to "radeon.modeline=0" and voila! It worked!!

Thanks for your help. You're a genius!

---

### Post by MAFoElffen on 2016-02-16
You are very welcome.

---

