---
title: "dead drive?"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by smisnodrog on 2010-11-02
i think the hard drive is dead ? ! - I'm a complete ubuntu newbie, turning to linux after winxp dying and even after new install not booting up.


When  i run the live CD i've followed previous instructions re mounting the drive

 sudo fdisk-1 - get a list of specs of the drive
but
sudo mount etc doesn't make it consistently appear in places or the desktop. it did once yesterday, and i'vegot the data off the drive, but today it doesn't appear.

So now i've got the data i'm trying to install, selecting the 'install on entire disk' option.

the 1st install stopped at 5% with an error message along the lines of a bad drive. I'm afraid i didn't write it down.

Restarted, and this time the install has got to 53%, and i need to go to work.

Once (if) ubuntu installs ok, (i selected the complete disk option again) is there anything i should do to confirm the drive is going to be ok?

it is an 8 year old dell laptop, so maybe past its useby date?

---

### Post by sedawk on 2010-11-02
After booting the LiveCD open a terminal and then
run the command (every few seconds)
```

dmesg

```

If the disk is faulty you should see new messages at the
end of the file. Depending on the fault there can be
lots of repeated messages about communication with the
drive or read/write errors.

One possible test is to read in the whole disk once without
really changing any data. To do this open a 2nd terminal and
run 
[CODE]
dd if=/dev/sda of=/dev/null bs=512 
[CODE]
This will read everything from the input device (if=...) which
is disk /dev/sda and write the data to the output device (of=...)
which is the null device.
The parameter bs specifies the blocksize and 512 bytes is
the usual size of hard disks sectors, but it might be faster to
use bigger values there, e.g bs=4k or bs=1m or ...

As soon as the dd commands runs into trouble you will see this by running the dmesg command.

---

### Post by Rubi1200 on 2010-11-02
I think it would be easier to open a terminal and run ```
tail -F /var/log/dmesg
``` and leave it open. That way you can check and see what is added as it happens rather than running the whole log and scrolling to the bottom each time.

---

### Post by lkraemer on 2010-11-02
smisnodrog,
Power up your computer and go into the BIOS.  See if the Drive is 
recognized by the BIOS.  If it is, then it most likely is functional.

Next step is to determine the Manufacture and model of the Drive. 
Go to their website and download the Diagnostics.  Run their Diagnostics
on the drive, just DO NOT do the WRITE TEST for the drive.  If it passes
the Diagnostics then Their software claims the drive to be functional.

Next load Gparted, Or download the Gparted.ISO and run it from the LiveCD.
See if the partitions exist and everything looks normal.

Next boot up a Distro and actually mount the Drive and have a look at the
data on the Partitions.  At this point I'd suggest copying your data to
another drive.

lk

---

### Post by lkraemer on 2010-11-02
Dup????

---

### Post by smisnodrog on 2010-11-04
Thanks folks, have been out of touch  for couple of days, back to it now.
I have entered:
tail -F /var/log/dmesg
and it shows 10 lines of info, but i can't copy + paste it, not sure what is important. The last line is:

[    19.231054] platform radeon_cp0: firmware requesting radeon/R300_cp.bin

When i try to open firefox the icon at the top flashes, the swirly hourglasss thing appears, "starting firefox Web..." appears at the bottom, but then dissappears again.

The terminal screen doesn't change. and worryingly if the hard drive/fan are working, they are doing so silently.

---

