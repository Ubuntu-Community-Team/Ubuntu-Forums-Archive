---
title: "GRUB Error: out of disk. Cannot boot default entries."
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by anthony62490 on 2010-07-04
I just installed ubuntu 9.10 two days ago. I was having some trouble getting it to run, so I edited /boot/grub/grub.cfg as follows:
```
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,1)
[COLOR="Red"]search --no-floppy --fs-uuid --set 6c1ea016-c372-470b-8045-cb1ede515ab8[/COLOR]
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6c1ea016-c372-470b-8045-cb1ede515ab8 ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
}
```

turned into this:
```
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,1)
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6c1ea016-c372-470b-8045-cb1ede515ab8 ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
}
```

So after that was done, I set up my system to its normal settings. Downloaded NVidia drivers. (reboot) Set up Compiz. Mass downloaded all of my previous packages. (reboot) Transferred my old files from an old HD to the new one. Compiled Amarok1.4 and IDLE3.5. Factoring in interruptions, this took the better part of a whole day to finish. 

So now, after setting everything up (and rebooting several times), I am told that I can't boot up again. I get the following error message:
```
error: out of disk
failed to boot default entries

also, it very briefly gave me another message immediately befor the "out of disk": message:

Error: no such disk 6c1ea016-c372-470b-8045-cb1ede515ab8
```



SO, anybody have any ideas? Need any more info?
I am using a 20GB ExcelStor HD now if it makes a difference. Everything else should be in my sig.

---

### Post by darkod on 2010-07-04
Don't play with editing grub.cfg, there is probably a reason that's not recommended.

Start the computer and if you are getting a boot menu, highlight the ubuntu entry but don't hot Enter. Hit 'e' instead. It will show the boot lines. Delete the line starting with search and hit Ctrl+X to boot.

If you don't get a boot menu, after BIOS is done start hitting Shift to get the boot menu. Then do as above.

If deleting the search line made it boot successfully, do the procedure described here to make the fix permanent:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by anthony62490 on 2010-07-04
Darko,
I've done all of this and I am having no luck. Pressing Shift at any time during the boot does nothing. I still get the same error message. "error: out of disk ; failed to boot default entries" I discovered that pressing Esc lets me choose which device to boot on the fly (which is interesting, but not very helpful).

I even booted from a live CD so that I could change grub.cfg back to normal, but that doesn't seem to change anything.

---

### Post by oldfred on 2010-07-05
I think you have to hold shift key down from BIOS until menu appears, not just press it once or twice.

Did you plug in any USB devices beyond keyboard and mouse. Leave a CD in tray or any other change to system?

---

### Post by anthony62490 on 2010-07-05
> **oldfred said:**
> I think you have to hold shift key down from BIOS until menu appears, not just press it once or twice.

Okay, thanks. Holding down Shift let me get into the GRUB menu. I tinkered around with the script and found a way to get it to boot. I got it to work by deleting the following lines:

```
1. [COLOR="Red"]recordfail=1[/COLOR]
2. [COLOR="Red"]if [ -n ${have_grubenv} ]; then save_env recordfail; fi[/COLOR]
3. set quiet=1
4. insmod ext2
5. set root=(hd0,1)
6. [COLOR="Red"]search --no-floppy --fs-uuid --set 6c1ea016-c372-470b-8045-cb1ede515ab8[/COLOR]
7. linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6c1ea016-c372-470b-8045-cb1ede515ab8 ro quiet splash
8. initrd /boot/initrd.img-2.6.31-14-generic
```

If I only delete lines 1 and 2, I get a message to the effect of:
```
Error: no such disk 6c1ea016-c372-470b-8045-cb1ede515ab8
```

and if I only delete line 6, I get my good friend:
```
error: out of disk
failed to boot default entries
press any key to continue:
```

It appears to work just fine as long as those three lines are gone, but I'm not sure if its safe for me to be running the system under these circumstances.

> Did you plug in any USB devices beyond keyboard and mouse. Leave a CD in tray or any other change to system?
The only thing plugged in besides the mouse and keyboard is an MP3 player, but that hasn't been moved for a few days. I guess it can't hurt to try rebooting after removing the MP3?

---

### Post by darkod on 2010-07-05
If I'm not mistaken, you said this message started to appear only after you started changing things in grub.cfg manually.

I would run update-grub to create a new grub.cfg, and then use the link I posted in the last post to disable the search line. See if that will make it boot normally.

If not, you will need to investigate further, but lets see what that does first.

---

### Post by anthony62490 on 2010-07-05
Okay, this is interesting. Running "sudo update-grub" gives the following response.
```
anthony@anthony-desktop:~$ sudo update-grub
[sudo] password for anthony: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.10 (9.10) on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

done
anthony@anthony-desktop:~$ 
```


Also, the computer waited a good long time after I edited grub.cfg to start giving me problems. That's the main reason I am so confused here. I would think that if it was a really bad idea to edit grub.cfg, it might tell me immediately if I had made a mistake.
> So after [editing grub.cfg], I set up my system to its normal settings. Downloaded NVidia drivers. (reboot) Set up Compiz. Mass downloaded all of my previous packages. (reboot) Transferred my old files from an old HD to the new one. Compiled Amarok1.4 and IDLE3.5. Factoring in interruptions, this took the better part of a whole day to finish.

---

### Post by darkod on 2010-07-05
I understand your point, but I'm trying to eliminate possibilities.

If you don't have a device for sdb in device.map, create new with:

sudo grub-mkdevicemap
sudo update-grub

In fact, maybe only this will sort it out. Maybe the sdb missing an entry in device.map is the problem. But why wouldn't it have en entry for it, did you add a disk after the install?

If it still complains about the search line you have the already mentioned link how to disable it.

---

### Post by darkod on 2010-07-05
PS. I'm starting to think your disks somehow changed their names sda to sdb. It reports 9.10 found on sdb1 which doesn't have an entry in device.map, but you never mentioned having two installs.

If your single root partition somehow from sda1 became sdb1, and there is no grub drive for sdb, of course it can't boot it, hence the messages "failed to boot default entries".

---

### Post by anthony62490 on 2010-07-05
> In fact, maybe only this will sort it out. Maybe the sdb missing an entry in device.map is the problem. But why wouldn't it have en entry for it, did you add a disk after the install?Yeah, I added my old HDD after the install was over in order to transfer all of the old files. Should I avoid doing that?

-----

Huh. I reset the pc to see if grub-update actually did anything at all. It definitely did something. Now I can't get to the GRUB menu with or without holding Shift. Aside from using a live CD, the only thing I can get is a GRUB command line that I have never used before.
```
GNU GRUB version #.##(###k Lower/#######K upper memory)
[Minimal BASH-like line editing is supported
For the first world, TAB lists possible command completions.Anywhere else TAB lists the possible completions of a device/filename]
grub>
```


Also, this might make things a bit clearer; here are the contents of device.map:
Shouldn't this file have two lines?
```
(hd0)	/dev/sda
```

BTW Darko, thanks for your help. I really appreciate it.

---

### Post by darkod on 2010-07-05
> **anthony62490 said:**
> Yeah, I added my old HDD after the install was over in order to transfer all of the old files. Should I avoid doing that?


Yes and no.

Your situation is precisely why I rarely recommend unplugging disks.

Yes, it sounds like a good idea to keep your old disk disconnected and the data safe. But even if it was connected, it was safe as long as you are careful and install ubuntu to the new disk. There is no way to install on the wrong disk, if you know at least a little about what you are doing.

On the other hand, you can never know how things will go with connecting disks later.

If your both disks were connected during install, ubuntu and grub would have made all the correct settings. Like this, we have to chase them around now.

And when it reported a wrong device.map file you shouldn't have restarted before running the command to create a new one.

Try this:
Power down and disconnect the older disk. Leave just the new install. If you boot, will it boot OK?

Second question: are both of your disks sata or ide, or a mix?

---

### Post by anthony62490 on 2010-07-05
Both drives are IDE.

Okay, reset the pc and disconnected the old drive. It does not appear to do anything. I continue to get the grub command line. 
Isn't this exactly what should be happening? I updated grub without updating device.map, so I would imagine that that's what is causing this. 
Could I just change device.map to say 
"(hd0)	/dev/sdb"
or 
"(hd0)	/dev/sdb1"

---

### Post by darkod on 2010-07-05
For IDE disks, check this:

1. Make sure the jumper settings are correct if you are using them. If the disks are on the same cable and you use CS, plug the new disk at the end, the old at the middle of the cable.

2. If using separate cables, plug the new disk in the primary port and as Master, the old disk in the secondary port as Master or Slave.

That should make the new disk sda and the old sdb hopefully.

As for changing the device.map, did you plan to do this from live mode (because you can't boot)? What the device map should say depends on whether your new disk is sda or sdb, because it needs to be hd0. You should be able to check that from live mode with:

sudo fdisk -l

If the new disk is sdb, the map should be changed to something like:

(hd0) /dev/sdb
(hd1) /dev/sda

---

### Post by anthony62490 on 2010-07-05
Okay, I put both HDDs on the same cable and they are both set to CS. The new drive is at the end of the cable and the old drive is in the middle.

terminal output:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20008035328 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55aa55aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2325    18675531   83  Linux
/dev/sda2            2326        2432      859477+   5  Extended
/dev/sda5            2326        2432      859446   82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4812    38652358+  83  Linux
/dev/sdb2            4813        4998     1494045    5  Extended
/dev/sdb5            4813        4998     1494013+  82  Linux swap / Solaris
```

---

### Post by darkod on 2010-07-05
Your new disk, the 20GB is sda. It doesn't boot like this too? Still the same error?

If yes, we can try chroot and to update the grub configuration.

---

### Post by anthony62490 on 2010-07-05
The answer is Yes. I still get the same error. Honestly, I didn't change much. The only thing that changed was that the 40GB HDD was changed from Master to CS. The 20GB was already set to CS, which I imagine sets it as Master.

---

### Post by oldfred on 2010-07-05
Is your cable the newer cable select type with 80 wires and three different color connectors or the older 40 wire cable.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by anthony62490 on 2010-07-05
It's a 40 wire cable

---

### Post by anthony62490 on 2010-07-05
Okay, changing the 20GB HDD to Master only seems to have made things worse. Neither the GRUB menu or command line comes up. The BIOS begins its procedures and when it is detecting the Masters and Slaves, the Primary Master (20GB) never shows up. I've look at the CMOS to see if I could make it autodetect the HDD, but I got nowhere. Funny thing is, the Maxtor 40GB HDD popped right up as the Primary Slave.

---

### Post by darkod on 2010-07-05
With every further post it sounds like hardware problem. I have to go back to what I said about never unplugging hardware when installing an OS, it needs to know what you have.
If the two disks can't work together, you would have noticed that even before installing ubuntu on the 20GB.

Double check the jumper settings, or try finding another cable and use them on the different channels. In that case use the 20GB on the primary channel, because you want that to be the primary disk.

You have to make the hardware work first, only after that we can start discussing ubuntu. :)

---

### Post by anthony62490 on 2010-07-05
It's not necessary to have the second HDD. It wasn't plugged in when I installed Ubuntu and it doesn't have to be present now. What if I unplugged the 40GB and set the 20GB back to Cable Select?

---

### Post by anthony62490 on 2010-07-05
Removed the 40GB HDD, set the 20GB to Cable Select and rebooted. It worked. Eventually. It took a good five minutes to get moving, but I am back in familiar territory for now. 

ran "sudo grub-mkdevicemap" and now device.map says:
```
(fd0)	/dev/fd0
(hd0)	/dev/sda
```

---

### Post by darkod on 2010-07-05
That is correct device.map with one disk present. The problem begins when connecting the other disk too because the 20GB becomes /dev/sdb, if it gets detected correctly at all.

The 20GB needs to remain primary master and I think in that case it will remain /dev/sda even with the 40GB connected too.

But you have to make them work so that the 20GB is Primary Master and the other disk either Primary Slave or Secondary Master/Slave.

In that situation I think it should still work fine, even without updating the device.map.

---

### Post by anthony62490 on 2010-07-05
okay, so grub has been updated and it turned up no errors (at least from the Terminal). 

So if I want to get the 40GB drive back, I need to plug it back in and make sure it is recognised as either primary slave or secondary master/slave, right?

If my guess is correct, the only complaint I should get is the one about the search line. I'll need to check, but I need to get to work. I'll be back in about 6-7 hours. Thanks again for your help.

---

### Post by anthony62490 on 2010-07-06
Im back, and I experienced no difficulties booting up. I didn't even get the No Such Disk error. I'll try to add the second disk later.

So my biggest problem was that I added another HDD after installing the operating system? I'll keep that in mind for the future.

So I guess it is fixed? Thanks a lot, man. You sure handled this without too much trouble. Where did you learn all of this?

---

### Post by Pegel03 on 2012-03-19
Hopefully adding some weight to this thread, Darkod #2 message was a lifesaver for me!

> If deleting the search line made it boot successfully, do the procedure described here to make the fix permanent:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search")

Despite boot-repair and boot_info_script (ok, didn't ask for help).
Ubuntu 11.10 finally ran with the search line from grub.cnf removed.

---

