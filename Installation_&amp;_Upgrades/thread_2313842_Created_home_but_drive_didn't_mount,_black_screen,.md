---
title: "Created /home but drive didn't mount, black screen, alt-F2 works, can alt-ctrl-del"
date: 2016-02-16
forum: Installation &amp; Upgrades
---

### Post by FaultedGeologist on 2016-02-16
Lubuntu 15.04 Vivid Vervet - I followed the steps in the following Ubuntu topic to create a /home folder on an install that was unpartitioned.  Previous to doing this, I used Gparted to create the /swap and /sda3 partitions, but was unable to declare the /sda3 as /home.  I tried running the installer, changing the partition, and backing out of the something else page, but that didn't work either.

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I copied all the terminal commands, and everything went as planned until the last step under the Reboot or Remount section.  The sudo command didn't create the /home separate from the root / under the file tree.  I closed everything out and tried rebooting to see if that would trigger.  From there it seemed like the reboot was going good, then I got the cursor in the top left.  I tried alt-F2 after waiting patiently, and the screen reactivated from sleep but nothing reappeared.  I hit alt-ctrl-del to see what would happen and it rebooted.   The same thing happened.  Per my previous thread on the new kernel not working, it is booting correctly to the 0.15 kernel instead of the 0.49 kernel from the recent upgrade.  

I could reinstall since the OS is pretty fresh.  The only things on there are gparted, a kids game, and the upgrades.  I would rather learn how to address the problem and fix things.  I have booted to the live USB.  It shows both the root / and the /home partitions on the file folder viewer as 26gb volume and 171gb volume respectively, and it shows the user folder that I moved to what should be the /home mounted drive.

**I am unsure if this changes how I should have approached the instructions for creating the /home partition, but when I used Gparted from the live usb it created the intended /home partition as /mnt/sda3. **As stated above, I tried many different ways to create the /home folder before finding the linked instructions.

I keep making progress, then finding a way to botch things.  I have, with all the wonderful help, found my way out of all the issues.

---

### Post by sudodus on 2016-02-16
You need a line in the file **/etc/fstab** to mount the /home partition, and it should be an ext4 partition. That line should be similar to the line for the root partition / (but for the /home partition).

First you should make a backup copy of the file (just in case).

```
sudo cp -p /etc/fstab /etc/fstab.bak
```

Edit the file with elevated permissions for example with the editor nano.

```
sudo nano /etc/fstab
```

Reboot and it should work :-)

---

### Post by MAFoElffen on 2016-02-16
Why you have no GUI, is that X needs a users .Xauthority file to init the graphics, thus your blank/black screen. That file is located in root of the user's home directory. Also is .bashrc.

So in the meantime, to be able to make that change that sudodus is recommending, you need to be able to boot to a console. Easiest option is: Boot > As Bios messages are ending, start pressing the left shift key > At the Gub menu > select the Recovery option > when the recovery option menu displays, select "with networking" (to mount the filesystem) > Select drop to root prompt, to make your needed changes.

---

