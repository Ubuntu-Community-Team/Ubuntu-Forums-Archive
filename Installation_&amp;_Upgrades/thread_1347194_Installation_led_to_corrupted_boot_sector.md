---
title: "Installation led to corrupted boot sector?"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by alexmoon on 2009-12-05
I'm not sure exactly what's gone wrong here.

I tried to install the latest version of Ubuntu using a USB. It got stuck a couple of times, which has happened before with no ill consequences, so I tried first going into the 'run live cd' option. It told me that there were 'many bad sectors' on my hard drive. 

When I went through the installation process, it got up to the part where it starts rewriting the partitions, and then froze for a very long time. 

I can't log into my old OS, which presumably has been deleted, and I can't install a new one (I've tried both Fedora and Ubuntu).

I've been trying to use TestDisk in SystemRescueCD in case there's a way to fix the corrupted boot sector (if that's the problem?) but am finding it a bit confusing.

I have two questions:
a) Any suggestions for how to fix this? and/or
b) Is this fixable or should I be looking for a new laptop?

---

### Post by presence1960 on 2009-12-05
First you want to see exactly what is on your machine before you try to proceed. I would do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Do not mount your partitions! You may destroy any chance of recovering your data if your partition table has been changed, so use the Live CD/USB!

---

### Post by alexmoon on 2009-12-06
Thank you for the response!

I can't actually get the Live Install to work. When I try with an Ubuntu livecd (on a USB), it hangs and then I just get streams of error messages. I tried with a Fedora livecd, and when I press "Boot" it tries to load then says:
"*ERROR* tried to remove a fb that we didn't own
Boot has failed, sleeping forever"

The only way I can get any workable terminal up is by using a SystemRescueCD livecd (on USB). Typing the line you suggested into the terminal on SystemRescue doesn't work because that file does not exist.

---

### Post by alexmoon on 2009-12-06
If it helps, when I run TestDisk using Deep Search on SystemRescue, it says:

"The harddisk (80 GB / 74 GiB) seems too small! (< 80 GB /74 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
Partition          Start    End   Size in sectors
Linux      1340      0       1     134881672 [/home]"

---

### Post by alexmoon on 2009-12-07
So, I think the problem was that my hard drive was broken. I've replaced it and got Jaunty working without problems (though Karmic has given me nothing but trouble).

---

