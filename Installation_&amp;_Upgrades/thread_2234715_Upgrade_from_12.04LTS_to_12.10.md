---
title: "Upgrade from 12.04LTS to 12.10"
date: 2014-07-16
forum: Installation &amp; Upgrades
---

### Post by oakridge on 2014-07-16
Today I have had a message to say that I should have upgraded before 16 July.

I have changed the Update Manager to notify me on Any New Version which was not the default and a message has come up inviting me to upgrade to 12.10.  This results in the message:

Failed to fetch
Fetching the upgrade failed.  There may be a network problem

As there is quite a lot of software installed and this is a dual boot machine with Windows 7 I really do not want to do a re-install.

Any advice would be gratefully received.

Malcolm

---

### Post by slickymaster on 2014-07-16
First things first, Ubuntu 12.10 is EOL since May 16, 2014

You can upgrade to 14.04, which is also a LTS version. First make sure that you are fully up-to-date. Double check by opening the Update Manager application from the dash and installing all updates listed.

When that’s done, open a terminal window and run the following command```
sudo update-manager -d
```When prompted, enter your user password.

The Update Manager application will open after a few seconds with a prompt to upgrade.

---

### Post by oldfred on 2014-07-16
I have 12.04 not the updated Enablement stack. That does not require changes.

 So is it announcing the update a bit early?
The 12.04.2 and later may need updates since they are based on various newer kernels (HWE) and need updating to the newest. Or if not updated, all other software will be supported, but things may get out of sync.

 Info on updates to LTS Enablement stacks
[http://ubuntuforums.org/showthread.php?t=2234693&p=13074774#post13074774](http://ubuntuforums.org/showthread.php?t=2234693&p=13074774#post13074774)
[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by oakridge on 2014-07-16
Entering:

sudo update-manager -d

Generates this message:

WARNING:root:nothing unsupported running 0 (0)
Error in function pulse
TypeError: pulse() takes exactly 1 argument (2 given)
Error in function pulse
TypeError: pulse() takes exactly 1 argument (2 given)
Error in function pulse
TypeError: pulse() takes exactly 1 argument (2 given)
Error in function pulse
TypeError: pulse() takes exactly 1 argument (2 given)
Error in function pulse
TypeError: pulse() takes exactly 1 argument (2 given)
Error in function pulse
TypeError: pulse() takes exactly 1 argument (2 given)
WARNING:root:file 'quantal.tar.gz.gpg' missing
oakridge@oakridge-dual:~$ 

Malcolm

---

### Post by oakridge on 2014-07-17
We seem to have come to a stop here, so...

Ubuntu is installed as a dual-boot machine with Windows 7.  Startup is controlled by Ubuntu.  They are installed on a 2TB HD with each OS having 100GB and the rest being a shared data drive.  Now if i were to do a re-install with the current LTS - 14.04 I think - would this install smoothly into its alloted partition without wrecking everything else?

Malcolm

---

### Post by grahammechanical on 2014-07-17
May I make a point. Wait a bit. Make sure that software sources>updates is set to notify you of the next LTS release and when 14.04.1 is released you will be notified that it is ready. And that will be July 24th. Those who upgraded as soon as 14.04 was released had problems. And now for this:

> [COLOR=#000000]if i were to do a re-install with the current LTS - 14.04 I think - would this install smoothly into its alloted partition without wrecking everything else?[/COLOR]

That mostly depends on you. We use the Something Else option and we tell the installer to put 14.04 into the partition that 12.04 is in. But it will over write all the data in the partition. Do, you know how to use the Something Else option?

Back up all important data. Remember, the installer defaults to installing Grub into the MBR/UEFI of sda. Do you want this. If not make sure you direct the installer to put Grub into sdb.

Regards.

---

### Post by oldfred on 2014-07-17
Also suggest wait. 

And only use Something Else to reinstall if you elect to do that. 

The installer currently has a bug and erases Windows with most if not all the auto install options. It may say overwrite Ubuntu but overwrites entire hard drive.
Something Else where you totally control partitions and uses is the only safe way to reinstall currently.

---

### Post by oakridge on 2014-07-19
Thank you all for your help.

So the answer is - wait, at least until 24 July.

This is the second dual boot machine we have built (my wife does the building because she can see what she is doing and I do the software because...) so I had to jump quite a few hoops to make it happen.

I will see what notifications come through and act accordingly, no doubt needing to come back to you.

Malcolm

---

