---
title: "Grub error: grub_term_highlight_color not found"
date: 2015-10-04
forum: Installation &amp; Upgrades
---

### Post by Qarlo on 2015-10-04
While upgrading an old Ubuntu installation on an old laptop, when the system restarted, it ended up on the grub rescue screen displaying the error ```
grub_term_highlight_color not found
```

Looking around I found several guides, but none of them worked or I missed something.
First of all, from a Mac, I created a bootable USB drive with Ubuntu, then with boot-repair and finally with SuperGrub. I'm not really sure how to use them, the last two in particular, but I tried to follow the instructions from [this guide]("http://ubuntuforums.org/showthread.php?t=1599293").
So, the situation is like this: normally, with the ls command, I see a list of hd0 partitions. I identified the one with Ubuntu on it as the third, so: (hd0,msdos3), or just (hd0,3). When I try to boot from the USB drive, I end up anyway on the grub rescue, but with ls I also see two hd1 partitions. The thing is that I can't access them, because it says "unknown filesystem".

I follow the guide and I get to the step 3. Now, running the command ```
insmod linux
``` gives me the same error again: grub_term_highlight_color not found. But I went on with the other commands anyway. After this step, I can actually ls the (hd1,1) partition. Not really, though, it just gives another error: Failure reading sector 0x7866 from hd1.

I thought it was a problem of the usb drive, but I tried with two different drives and the error is the same.

Is there anything else I can do? Can you help me fix this?

Thank you.

---

### Post by yancek on 2015-10-04
Which version of Ubuntu did you have installed and which version did you try to upgrade to?
If you have the boot repair utility on a flash drive and can boot it, you should see an option to Create BootInfo Summary.  If so, select that and get the output file and post it or a link to it here.

---

### Post by oldfred on 2015-10-04
Is it this bug?

 Ubuntu 14.04 Update breaks grub, resulting in "error: symbol 'grub_term_highlight_color' not found" 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
You need to chroot &   use dpkg-reconfigure grub-pc instead of grub-install directly, so that the system knows that it needs to run grub-install on that drive the next time grub is upgraded.

You may be able to use Boot-Repair's advanced mode and the full uninstall/reinstall of grub.

---

### Post by Qarlo on 2015-10-04
> **oldfred said:**
> Is it this bug?

 Ubuntu 14.04 Update breaks grub, resulting in "error: symbol 'grub_term_highlight_color' not found" 
[URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977"]https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977
[/URL]

Well, the error is the same, but as I said I can't boot to anything else. I tried booting Ubuntu from the usb drive, but it loads anyway the grub rescue prompt. From the rescue prompt I can't run any command beside ls or set, apparently.

It's not even necessary for me to keep the old operating system or the data, but I can't go past that screen.

---

### Post by oldfred on 2015-10-04
Well then your USB drive is not booting. 
There can be many issues with USB boot drives. 
But not sure if a Mac creates a system usable on a older system. Mac are now all UEFI based.

Other issues  can be was ISO confirmed to be correct with md5sum?
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
Were these flash drives one's you have used before?
Some brands work better than others.
       
  Installation/FromUSBStick - with lots of details on various USB drive issues by  sudodus
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

    
Some systems only boot from one USB port, or only from a USB2 port. Have you tried other ports?

Some systems need you to specifically turn on USB boot is allowed in BIOS/UEFI.

Some systems get locked up and just need a full cold boot. Or power down, remove battery, hold power switch for several seconds and then reboot, immediately pressing correct key to get into BIOS or one time boot key like f10 or f12. 

Some do not boot USB entries in BIOS, but correct entry in BIOS is really hard drive and under hard drive is USB flash drive.

---

### Post by Qarlo on 2015-10-05
> **oldfred said:**
> Well then your USB drive is not booting. 
There can be many issues with USB boot drives. 
But not sure if a Mac creates a system usable on a older system. Mac are now all UEFI based.


Apparently the problem was with Mac. I did the same procedure on Windows, this morning, and I managed to make it boot with boot repair and fixing it. So, for future reference, is there no way to make the same with a Mac, now? I mean, a bootable drive compatible with older laptops?

---

