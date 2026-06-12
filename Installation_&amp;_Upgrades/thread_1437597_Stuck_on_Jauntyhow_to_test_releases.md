---
title: "Stuck on Jaunty/how to test releases?"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by pickarooney on 2010-03-24
First of all, I'm happy with Jaunty. It's very stable and everything works (except my webcam on my desktop) so I've no major issue. 

However, I've tried to upgrade to Karmic three times on the desktop and twice on the laptop and each time has been an unmitigated disaster.

- tv tuner: simply does not work on karmic, even after two days fo fiddling. In Jaunty it works out of the box
- sound: constantly cuts out
- flash playback: terrible, sound cuts out and/or video stops working 
- video: two days wasted on the laptop trying to get a working display with nvidia drivers, to no avail. Five mimnutes after reinstalling Jaunty I had it working.

No big deal, I didn't see anything new in Karmic in the short time I used it so I'm not missing out on much.

However, I'm now very reluctant to install any releases, from Lucid on, as I have no wish to waste days trying to get basic things to function. Lucid might be a perfect release, full of useful new additions and everything might work straight off the bat, (it might even allow a webcam and a tv card on the same machine!) but I have no way of knowing beforehand and no desire to smoke my system by testing.

I was thinking of using a LiveCD, but the problem there is that the nvidia drivers are not available so I can't test either the display or the tv card. If I install them, I need to reboot and then tvtime is lost - big-time Catch-22. 

I tried a virtual machine, but the situation is similar - graphics drivers don't seem to work properly on the VM. 

I could, I suppose, carve off a partition on my HD for a second xubuntu installatsion and run Lucid in test mode, but it seems like an awful lot of hassle and a waste of space. 

Ideally, I'd like some sort of rollback system whereby I could install Lucid, test for a couple of days and if it's as bad as Karmic then just hit a button and go back to Jaunty with a minimum of hassle. This really isn't feasible without a reformat though, and that's another few hours that I don't have wasted.

Has anyone come up with a decent solution for testing a release without compromising a working system?

---

### Post by Herman on 2010-03-24
:D
The dd command can be used to make a backup of an entire working operating system to a file in a different file system when the other file system is mounted.

It's usually worth the extra time to remove files and reduce the size of the partition before making the backup because the dd command even copies the empty space in your partition.

You would need to run these commands from a different operating system such as an operating system in a live CD or in a USB drive.

Backup
```
sudo dd if=/dev/sda1 of=/media/mountpoint/os.image bs=4096 conv=notrunc,noerror
```Restore
```
sudo dd if=/media/mountpoint/os.image of=/dev/sda1 bs=4096 conv=notrunc,noerror
```

---

### Post by Herman on 2010-03-24
You will need to restore GRUB to MBR after restoring an OS from a dd backup.
A file system check shouldn't be necessary but might be a good idea just to make sure.

---

### Post by coffeecat on 2010-03-24
Do have a rethink about setting up another partition to test out newer releases. It's a good way of not burning your boats when you come to move to a later version. For instance, on my main machine, I kept Jaunty going while I settled in Karmic. At the moment I have Jaunty, Karmic and Lucid Testing in adjacent partitions, and I still occasionally boot into Jaunty simply to have access to the last version of Handbrake that supported XViD and AVI. (I point the finger at the Handbrake people, not Ubuntu, for that little fiasco.)

Anyway.... I can answer one of your woes:

> **pickarooney said:**
> - tv tuner: simply does not work on karmic, even after two days fo fiddling. In Jaunty it works out of the box

Simple explanation, but I discovered it only recently. In Karmic they split the firmware for TV cards (and some other devices) into "linux-firmware" and "linux-firmware-nonfree" - presumably because of licensing issues. In Jaunty they all came in a default install. In a default install of Karmic (and Lucid as well) you only got "linux-firmware". Your TV card probably needs the nonfree firmware (my PCI Hauppage does) before it will work in Karmic.

---

### Post by pickarooney on 2010-03-25
> **Herman said:**
> :D
The dd command can be used to make a backup of an entire working operating system to a file in a different file system when the other file system is mounted.


Could be worth trying out. I'll have to see if I have enough space, but should probably be able to.

> **coffeecat said:**
> 
Simple explanation, but I discovered it only recently. In Karmic they split the firmware for TV cards (and some other devices) into "linux-firmware" and "linux-firmware-nonfree" - presumably because of licensing issues. In Jaunty they all came in a default install. In a default install of Karmic (and Lucid as well) you only got "linux-firmware". Your TV card probably needs the nonfree firmware (my PCI Hauppage does) before it will work in Karmic.

Wow... I would never have guessed that. I mean, literally never, it's like coming home and not finding your TV and getting a phone call a year later from an anonymous tipster that it's working fine, it's just been moved under a pile of old mattresses in the pool house. Thanks!

Canonical never ceases to amaze me with stunts like this...

---

### Post by mkvnmtr on 2010-03-25
An extra partition to try new releases is a good idea. One other thing I do is have my home on a seperate partition.That way if I need to reinstall I do not lose anything. It is just a matter of a quick reinstall of the root partition, update and reinstall my apps. Only takes about two hours on my old system. Also works for upgrades.

---

### Post by coffeecat on 2010-03-25
> **pickarooney said:**
> Wow... I would never have guessed that. I mean, literally never, it's like coming home and not finding your TV and getting a phone call a year later from an anonymous tipster that it's working fine, it's just been moved under a pile of old mattresses in the pool house. Thanks!

Canonical never ceases to amaze me with stunts like this...

Nicely put. :) But, personally, I wouldn't be so hard on Canonical/Ubuntu. The change was documented but, like a lot of documentation, it was buried inside the other zillion announcements and stuff. I should imagine some lawyers started doing some heavy breathing down Canonical's neck.

What never ceases to amaze me is the attitude of the hardware manufacturers who make life so difficult with their licensing of firmware. Don't they want people to use their products? Just consider the Broadcom wireless firmware situation. That causes a lot of grief to newbies to Linux. If Intel allows their firmware to be shipped with Linux, what's Broadcom's problem?

That was a rhetorical question. :wink:

---

### Post by pickarooney on 2010-10-30
Well, I finally decided to update once again now that Jaunty is no longer supported, but I'm still having the same problem getting the TV card to work even after installing the nonfree firmware.

---

