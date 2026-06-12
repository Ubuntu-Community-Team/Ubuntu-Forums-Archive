---
title: "Boot-Repair doesn't find Ubuntu in Extended Partition?"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by 2CV67 on 2011-12-19
I installed Ubuntu 11.10 on my wife's netbook alongside Windows 7.
Because there were already several primary partitions, I had to put Ubuntu inside an extended partition, see GParted diagram attached.[IMG]http://i838.photobucket.com/albums/zz309/2CV67/netbookpartitions.png[/IMG]
I think this means Ubuntu kernels I need to boot to are in /dev/sda7 doesn't it?

Anyway, this all worked just fine & I was booting as first priority to W7 (for wife) with Grub screen to select Ubuntu for me.
Today, Ubuntu updated to a new kernel & Grub2 screwed things up - booting to memtest or whatever.

I am new to Grub2 - my main PC still has good old legacy grub & I know how to deal with menu.lst but not Grub2 on the new netbook.
So I rebooted to the grub screen, saw that it now showed (roughly):
- Ubuntu 3.0.0-14 generic
- Ubuntu 3.0.0-14 recovery
- Previous versions
- Memtest...
- Memtest...
- W7
- W7 recovery

I booted to Ubuntu & found /etc/default/grub where I noticed the line GRUB_DEFAULT=4.
Making a false assumption that 2 lines had been added above W7, I did gksu gedit /etc/default/grub & changed DEFAULT=4 to =6 & saved.
I was surprised to see a bunch or error messages, but went ahead with sudo update grub.

Trying to reboot, I found myself in Windows recovery & left as soon as I could.
Subsequent attempts at booting lead to "error: no such partition - grub rescue > _"
from which I can't escape.

After a lot of Googling, I found I could boot to the Live Ubuntu USB drive I used for the original installation, but can't get from there to the main Ubuntu file system to try to fix ...default/grub.
I ran sudo fdisk -l & was surprised to see it lists sda3 but none of the partitions inside (sda5/6/7/8).
I tried to mount Ubuntu with sudo mount/dev/sda3 /mnt but got error messages about needing to specify the file system type & can't get any further with that.

Then I tried installing Boot Repair & risked the "Recommended Repair" method.
After that, the netbook now boots straight to Windows (so my wife can get back to work - the main thing!) but I never see a grub screen or any way of getting Ubuntu.

The Boot Repair Report is at http:/paste.ubuntu.com/775525/ if that helps.

So - can anybody help me to either get the grub screen back or to mount my main Ubuntu drives from the live USB Ubuntu?

I have a couple-dozen Googled sites open at the moment, trying to help myself, but no luck so far!

Thanks for any suggestions!

---

### Post by oldfred on 2011-12-19
Boot script is not showing sda6 or sda7 which were your / (root) install & /home.

I might try testdisk to see if it can recover the missing partitions as script shows a large gap in the extended partition.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by darkod on 2011-12-19
Unfortunately the bloody win7 recovery probably messed things up. It usually starts to apply restore to factory layout when you start it. I hope it didn't get too far. I assume the partitions are not displayed correctly because of this.

In case you sort it out, maybe this can help you. The first thing I do after an ubuntu install is to change the order of the OSs being detected, so that ubuntu is last and adding new kernels doesn't move the other OSs.

To do this, I go into /etc/grub.d and make a copy of the 30_os-prober into 06_os-prober.

sudo cp 30_os-prober 06_os-prober

Then make the original one not executable, but that will keep it in the folder:
sudo chmod -x 30_os-prober

Run:
sudo update-grub

to make a new grub.cfg. Now windows will be first, and ubuntu last. In that case make the default system =0 in case your win7 is first in the list.

By the way, to make memtest go away from the menu but still be there in your system (how often do you run it?), you can make it not executable too:
sudo chmod -x 20_memtest86+

---

### Post by 2CV67 on 2011-12-21
Thanks very much for both those replies!

I have now read all about TestDisk (especially the excellent tutorial on the Dual-Boot site, which I hadn't visited for some years) & suspect it would be a good bet for trying to recover the partitions.
Sounds impressive!

Thinking about my situation though:
- My wife absolutely needs W7 for the next couple of weeks.
- My Ubuntu on that netbook was just sand-box stuff, playing with Unity etc - nothing vital.
- Ubuntu on my main PC is OK.
Then I think my best plan is to wait for a suitable lull in W7 activity, then make a new installation of Ubuntu on the netbook recreating the logical partitions.
That is probably a lower-risk scenario than playing with TestDisk, isn't it?

I will certainly try to rearrange the grub screen to put W7 at the top.
I have had it like that on my main PC for years (with Legacy Grub) but was hoping Grub2 would sort itself out without needing that kind of help...
Wonder whether Start-Up Manager or Grub Customiser will let me do that by GUI?

Is there any way I could prevent accidentally booting to Windows Recovery in case of future screw-ups? (I will have to tab through it every time I want to boot Ubuntu.)

I can't help wondering how Ubuntu can continue, shooting itself in the foot at every update, one way or another...

Thank goodness for this forum!

---

### Post by darkod on 2011-12-21
I don't use any grub customizer and I wouldn't know what to recommend. On thre other hand I don't have windows recovery partition either.

One thing you could do, is after the ubuntu install let it create the boot menu as normal. Then open the grub.cfg file and copy the menu entry for win7 to the 40_custom file. After that make the 30_os-prober not executable.

When you run update-grub it will not create entries for win7 and win7 recovery automatically, instead it will use the entry for win7 from 40_custom. There will be no entry for recovery.

In that case you will need to note down the difference between the entires that were in grub.cfg and you can boot the recovery if you need it by making one time adjustment in the win7 entry. If you ever need it.

For changing the order you can also rename the 40_custom into 06_custom.

---

### Post by oldfred on 2011-12-21
I think customizer has not been updated to work with grub 1.99 yet. So I would not recommend it. Follow Darko's suggestions and you will be fine.

---

### Post by 2CV67 on 2011-12-22
First of all, a big thank-you for the careful & detailed responses, whch I appreciate very much!

If I was in a hurry, I would execute them to the letter with gratitude. :)

As I explained previously, I am going to leave the netbook Windows-only for the next couple of weeks, so that gives me time to read a lot more about Grub2, SuperGrub Disks, GAG, Grub-Customizer etc.
As explained in my signature, I strongly prefer GUI where possible, & will try to go in that direction...

So what follows is not urgent:
I re-read the manual for my (wife's) Asus netbook & noted its built-in recovery system, activated by pressing F9 during boot (see screenshot):
[IMG]http://i838.photobucket.com/albums/zz309/2CV67/f9.jpg[/IMG]
If my memory is right, this is what I saw after mistakenly booting to Windows Recovery from Grub, and I exited there, without starting the Recovery procedure.
That prompts 2 questions:
1. If I didn't start recovery, what went wrong?
2. If that F9 system comes before Grub (I suppose?) then can I safely uncheck the "Windows Recovery" entry in Grub & rely on F9 if needed?

---

### Post by darkod on 2011-12-22
The thing is, maybe the partition is not deleted, just the entry in the partition table is corrupt or missing. Even though you didn't proceed with Restore I have no idea how starting the process can affect linux partitions especially since it seems windows based.

I believe you never tried the Testdisk option yet. You might as well be able to restore the root partition (the table entry) since the fdisk result in the script doesn't report the root partition as found but the start-end sectors of the other partitions seem OK. In these cases testdisk can usually retrieve the partition.

As I said, I don't use GUI just for arranging the boot menu, mainly because I do it only once and I don't need to install software that I will use only once.

In fact, your change in the DEFAULT value was the right way to go, but you didn't stop to count the order in the boot menu before doing it. You assumed it changed by 2, and in fact only one line Previous Versions was added.

There are many options, you should use the one that works best for you. As far as recovering ubuntu is concerned, to save you a new install, I think testdisk will do it.

---

