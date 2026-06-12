---
title: "Partial 10.04 installation. Please help"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by soadrocks79 on 2010-06-19
Mid-upgrade my update manager just closed down and said that the upgrade was finished with some errors and so i rebooted the system and it didn't start up properly and froze at the loading screen. I went into recovery and tried several times to repair broken packages. I think it worked becausse now when i start ubuntu up it opens up into a terminal adn im not sure if its a driver error, and if it is how to fix it, or if there is a larger underlying problem.

---

### Post by darkod on 2010-06-19
If you get the boot menu and can select the recovery entry, use it and if asked select option like Root with Networking to give you root permissions and internet, if possible.

Once the command prompt loads, usually to continue failed upgrade you would:

dpkg --configure -a

---

### Post by soadrocks79 on 2010-06-19
thanks you very much, im going to try it right now

---

### Post by soadrocks79 on 2010-06-19
ok i tried it and i got a message saying the process was halted because there were too many errors.

---

### Post by darkod on 2010-06-19
Uhhh...sorry, this is beyond me it seems.

This is why I hate upgrades. I have separate /home partition to keep my personal data and settings, and just do clean install when I want a new version.

Upgrades seem to be too unstable, especially if doing them every 6 months.

---

### Post by soadrocks79 on 2010-06-19
do you have any idea of how i can get rid of it and then reinstall it. that would be very helpful

---

### Post by darkod on 2010-06-19
You can always reinstall especially if you have no data to save from it.

Just start the installer and use Manual Partitioning to tell it to use the root partition as mount point /, and the swap partition as swap area.

That's it.

---

### Post by soadrocks79 on 2010-06-19
could u elaborate on how to do it. I'm not sure what to do. I'm not very experienced with the ubuntu coding because i haven't really had any of these problems before.

---

### Post by darkod on 2010-06-19
In the installer in step 4 you select Manual Partitioning. That will show you list of the partitions on the disk.

Except the windows ntfs partition and maybe another ntfs partition, you should have at least two uubntu partitions. A larger ext4 root partition and smaller swap partition.

Just click on the root partition and then the button Change at bottom. Set it to be used as ext4 again, tick the format box, and set mount point /.

Then select the swap partition, and set it to be used as swap area. There are no format and mount option for swap.

That should be enough. In that case it will install over the current install.

Or if you are using only ubuntu taking the whole hdd, in step 4 you can simply use the Erase and use whole disk option.

---

