---
title: "Installer touching things it shouldn't?"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Oded on 2011-05-01
Hi,
I figured I'd set up a test partition to test the waters before jumping head on to a full upgrade.
I've created a new ext4 partition on my disk and marked it to be used as root for the install.
Halfway through the installation an error message pops up saying it can not unmount sda7 beacuse it's in use,
sda7 has nothing to do with the Natty install, it's the root partition of my main setup!
I then aborted, rebooted and everything was fine with my main system, obviously the Natty install didn't take.

So, can anyone explain this to me?

Thanks

---

### Post by Quackers on 2011-05-01
If you are installing 11.04 from a cd or usb there should be no partitions mounted at all.

---

### Post by Oded on 2011-05-01
> **Quackers said:**
> If you are installing 11.04 from a cd or usb there should be no partitions mounted at all.

Yeah, I know. 
That doesn't explain any of it though.

---

### Post by recluce on 2011-05-01
That happened to me when trying to install beta1 - and also marked the point I stopped testing. Apparently, the migration assistant, even though I had specified not to import anything, tried to mount any/each partition it could find, search for importable setting and tried to unmount afterwards, partly without success. Also, it left /target set to something useless (my 125 MB hidden Windows boot partition, to be precise).

Because of some partitions now mounted which shouldn't be, the installer crashed a few steps later.

---

### Post by Oded on 2011-05-01
> **recluce said:**
> tried to mount any/each partition it could find, search for importable setting and tried to unmount afterwards, partly without success.
Pretty weird this thing actually made it to the final...
Thanks for explaining!

---

