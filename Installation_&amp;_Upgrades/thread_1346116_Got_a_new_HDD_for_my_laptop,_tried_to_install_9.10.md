---
title: "Got a new HDD for my laptop, tried to install 9.10, cannot boot into Ubuntu"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by Ozmodiar on 2009-12-04
First off, let met apologize for my ignorance here...I'm fairly tech savvy...but Command Line has always been confusing to me, so I'm completely lost. 

My laptop's HDD died back in February.  When it died, I was short on cash, so my brother suggested I just install Ubuntu on one of my spare USB Drives, so I did.  I've been running it happily and have not looked back since.  

Now, my brother just bought me a new HDD for christmas, and decided to give it to me early, so I eagerly threw the HDD into my laptop, booted it up off the USB Drive, and proceeded to format the drive, thinking I could just copy all of my information from the USB Drive to the HDD thinking things would magically work. 

Obviously things did not go this way.  I tried formatting the hard drive again, booting into the Live CD, and installing from there...still cannot boot. So I tried installing directly from the Live CD...no dice. All said and done, I was up until 3AM this morning (I work at 8) trying to figure this out.  

Here's what I know so far.  When I boot off my USB Drive, I can see the USB Drive is mounted at:

/dev/sdb1 mounted at /.

and the new HDD is mounted at:

/dev/sda1 mounted at /media/b260c3e8-4b2e-4958-927c-b93dcc7d0f7e

When I try and start the laptop up without the USB Drive in, I get the error:

error: no such device b260c3e8-4b2e-4958-927c-b93dcc7d0f7e
press any key to continue

When I press a key, it obviously gives me the screen where I can select what kernel I want to load...but I cannot actually load anything. 

My questions to anyone willing to help are this:

1. How do I make Ubuntu 9.10 boot off my HDD instead of this USB Drive?

2. I want to experiment with a couple other versions of linux (such as gOS)...so what do I need to set up in advance to not screw over my Ubuntu install when I start experimenting?

I really appreciate the help!

---

### Post by misterbk on 2009-12-04
I think you may be running into one of the few downsides of the new way FSTab works.

A little background - 
It used to be if you shuffled your hard drive plugs around inside the case, the detection order of the hard drives would change and your system could get screwed because "sda" would suddenly become "sdb" or "sdc".

To fix this, we now have UUIDs in FSTab.  So instead of this old style of fstab:
```
/dev/sda6 /               ext3    relatime,errors=remount-ro 0       1
```

we now have this new style of fstab:
```
# /dev/sda6
UUID=c22d8199-e281-4cd6-a89a-43c661362cdb /               ext3    relatime,errors=remount-ro 0       1

```

Now that your system drive is mirrored to the laptop drive, the UUID has changed for your partitions, but FSTab hasn't been updated.

At least, I think that's your problem...  :-k

Unfortunately I can't remember the command for getting proper UUID values...  maybe try using the old style "/dev/sda1" line and see if that works?

---

### Post by Ozmodiar on 2009-12-04
Thank you for the reply...but I really have no idea what you're saying...hahaha. 

What do you mean "maybe try using the old style "/dev/sda1" line"?

---

### Post by darkod on 2009-12-04
Lets back up little bit. Unplug your usb hdd. You said you can't install like that on your new internal hdd. Why? Booting with the cd and selecting Install Ubuntu does what?

---

### Post by Ozmodiar on 2009-12-04
> **darkod said:**
> Lets back up little bit. Unplug your usb hdd. You said you can't install like that on your new internal hdd. Why? Booting with the cd and selecting Install Ubuntu does what?

I didn't explain myself very well...sorry.

When I first got the HDD, I shut my computer down, installed it, booted back up (from the USB Drive), formatted it, and tried to just copy every from the USB to the HDD. I now know that doesn't work. 

So, next I shut down, removed the USB, put in the Live CD, booted into the Live session, and attempted to install there.  The install ran successfully. I shut down, removed the CD and rebooted, to encounter this problem. 

Next, I tried to install a 3rd time by putting in the Live CD and just selecting "Install Ubuntu".  Again, the install ran successfully, I shut down, removed the CD, tried to boot and failed again.  

After this, I tried installing gOS, just to see if something else might work. I got the same result: Install ran and completed. I shut down, and couldn't boot. 

Last, I tried putting the CD in, selecting "Install Ubuntu" let it run one last time, restarted, and it failed again. 

It was now 3AM, I had to get up for work at 630AM, so I gave up, went to bed, went to work, and came home to post for help. 

Am I making sense now?

---

### Post by darkod on 2009-12-05
Is it possible that booting from usb hdd all that time you have removed the option in BIOS to boot from the internal hdd? Make sure BIOS is set to boot from internal hdd (of course, cd-rom has to be first to boot from the ubuntu cd).

After you make sure about that, boot once more with the ubuntu cd and try to install selecting Use Whole Disk (or similar) if you want to have only Ubuntu on the drive. That will wipe the whole drive (destroying any previous bad install) and install ubuntu, saving you the effort to format first and then install.
If it doesn't boot or work correctly after that, do NOT reinstall ubuntu or anything else right away. Look at the messages, post them here, try to troubleshoot it. You can always boot with the cd and have internet access and troubleshoot why the install on the internal hdd is not working. You don't have to plug the usb hdd back, not right away.
With all that reinstalling it just gets more confusing. Try to troubleshoot the problem first.

---

### Post by Dangerdj on 2009-12-10
Same problem here, I did reinstall using the entire HDD but still getting the "error: no such device" Press any key to continue... I press a key and it just keeps looping the same message. I'm fairly new to this.

---

### Post by efflandt on 2009-12-10
Check your BIOS settings (CMOS setup from computer splash screen before any operating system comes up).  Make sure that your BIOS is **not** set to protect the mbr (maybe grub is blocked from writing its mbr to the hard drive).

Install from CD with USB drive disconnected, and use Advanced mode for partition set up to format the partition(s) you are going to use.  That should make sure that nothing is lingering from the USB to hard drive copy over.  You can always copy what you need from the USB drive later.

---

### Post by oldfred on 2009-12-10
I think we need to see more detail on where you are at. Darko even has this in his signature as we often need more info:

Boot Info Script 0.39 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 

Instructions
  louieb's 
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
cd to directory saved to: 
chmod 755 boot_info_script039.sh 
sudo ./boot_info_script039.sh 
or as example if on desktop from liveCD download 
sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

---

