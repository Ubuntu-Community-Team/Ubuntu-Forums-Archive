---
title: "Restore setting after 14,04 -&gt; 16.04 upgrade"
date: 2016-09-02
forum: Installation &amp; Upgrades
---

### Post by pcal on 2016-09-02
Hi guys,

My 14,04 system was set up in a way I believed would make future upgrades safe and simple. Apparently not...

I have / and /home in different partitions and believed that meant that all user settings and software would be untouched by the upgrade of the / partition with a new version.

I had 3 user accounts on 14.04,but only the main user account was recreated in 16.04. Also, most of the software installed over the last x years, and all the hardware settings have vanished- no printers, no scanner, virtualbox with my xp image for the odd driver that just won't work in linux, all my vpn connections, everything is gone from the os, but presumably still on the hard drive as the /home partition wasn't touched by the upgrade (assuming it did what it was told).

Desktop icons, and user files are all on the hard drive still, so I'm working on the assumption that things can be restored.

Is there a tool that does this, or do I need to hunt down the various systems and recreate them one by one? Would have kept using 14.04 if I'd realised this was going to be an issue as everything was running sweet. Why didn't this work as expected?

Any suggestions most welcome,

Regards,

Pcal

---

### Post by ajgreeny on 2016-09-02
Did you do an online upgrade using the upgrade manager or did you reinstall the OS using a live system?

If the latter, did you set the mountpoint for the partition that was /home previously as /home again during the installation's partition setup?

We need more detail about what you did and how you did it to be able to help you properly.

---

### Post by pcal on 2016-09-02
Apologies, it was quite late when I posted the original message last night (this morning), and I wasn't as sharp as I could have been...

Due to numerous failures in the past, I don't trust the on-line upgrade option and have only ever done upgrades from a live environment since. On this occasion, the .iso was burned to a dvd (as it wouldn't boot at all when I tried to do it from a usb stick). I selected the "Something Else" option and set /home and / mountpoints to the appropriate partitions - which I double checked in my partition manager before I started. Only the swap partition was formatted.

The installation ran as normal up until the last moment when it gave an error stating that "some" of the applications failed to be reinstalled and may have to be installed manually.

When I rebooted the system, as noted above, only the root user account had been created. All the network shares were missing (so etc/fstab was over-written), and all my vpn settings were erased (I have remote access to a number of different networks). So far as I can tell, none of the software that doesn't come with the distribution is installed, all my non-standard device drivers are missing...

Quite a bit of this is trivial, and can be easily recreated. Some of the rest of it though would be a royal pain to have to figure out how to do it again. In at least one case (a driver for a 3d printer) the manufacturer updated the driver beyond compatibility with my hardware and doesn't keep old versions (had that fight once before). I had a working version and disabled updates on it so I could keep my system working. Don't believe that version is procurable any more, so I really want to retrieve that software at the very least.

The /home partition does contain all the user accounts and their associated files, although I can't access them directly due to permission settings. I know I can cmod things to move them around, but will have to look up the information on how to do it again as it's been a long time since I had to do such things.

This is why I was hoping there may have been a tool that scans what is there and recreates the broken linkages or whatever it is that's required.

Again, sorry for the inappropriate brevity of my first post.

---

### Post by Bucky Ball on 2016-09-02
Did you disable any PPAs you added manually and remove any apps you installed manually?? Any third-party stuff that is not in the official Ubuntu/Canonical repositories will obviously not upgrade when you upgrade. Third-party stuff may be for a specific release and not designed to work on the newer one. Sounds like a possibility here.

Before doing any release upgrade it is advisable you try to get your install back to as 'vanilla' as you can, i.e. as close to a fresh install, as you can get it.

And hello from Adelaide! :)

---

### Post by pcal on 2016-09-02
The only PPA that had been removed related to the 3d Printer driver. Nothing else had been removed.

If there were one or two applications that stopped working, I'd happily put that down to version compatibility, but this is ALL of them, including all those in the standard repositories. Plus all the hardware settings and all the user accounts. It has to be more than just a different version.

I didn't do any special clean up, as I was under the (mistaken) impression that by not changing the /home partition all that stuff would be left untouched.

What do I need to do for the future to preserve applications when v18.04 comes around? Should I create another partition and set it as the mountpoint for /bin?

PS: Good to chat in the timezone :))

---

### Post by ajgreeny on 2016-09-03
> **pcal said:**
> I didn't do any special clean up, as I was under the (mistaken) impression that by not changing the /home partition all that stuff would be left untouched.
And so it would be as long as you set the /home mountpoint for the old home partition when you reinstalled.
If you did not do that which requires you to use the "Something Else" at partitioning stage, a new /home will have been made within the root partition.

I suspect all you need is to edit /etc/fstab to point the system to your old /home partition, as long as that partition is still in existence.

What is the output of command ```
mount
``` and then ```
sudo blkid -c /dev/null
``` which will help us to know what line to add to the fstab file.

---

### Post by pcal on 2016-09-05
> **ajgreeny said:**
> And so it would be as long as you set the /home mountpoint for the old home partition when you reinstalled.
If you did not do that which requires you to use the "Something Else" at partitioning stage, a new /home will have been made within the root partition.

You must have missed the bit in my second post where I said...

>   I selected the "Something Else" option and set /home and / mountpoints to the appropriate partitions 

I can confirm that the /home partition wasn't recreated inside the root partition. But thank you for the confirmation that this *should* have worked. I guess I'll just have to put it down to some sort of a glitch in the installation process.

I have subsequently recreated all the bits that didn't install correctly. Renamed the home folders for the user accounts that didn't reinstall, recreated the accounts then copy / chown'd the files into them so they are all back up again. With a bit of trial and error I even managed to get all the applications and drivers working again - so the system is up and running.

Still no idea why it failed...

Thanks anyway for helping.

---

### Post by Bucky Ball on 2016-09-05
And thanks anyway for posting your outcome and marking as solved. :)

Good news and glad it's all working again. :)

---

