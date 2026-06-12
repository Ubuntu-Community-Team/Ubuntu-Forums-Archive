---
title: "Unusual hard drive issue"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by johnno56 on 2010-06-17
I have 3 sata hard drives and one ide hard drive. Ubuntu will not boot.

I have ubuntu 9.10 on a 80gb sata; 200gb sata for storage; an 80gb IDE with Windows XP. (note: not a dual boot system) I select my OS via BIOS.

Here is my problem.

I purchased a 1TB sata (2 x 500gb partitions) and plugged it into the 3rd of 4 sata sockets on my mobo. Restarted my PC with Windows and all is fine. Restarted PC with Ubuntu. Grub executed ok and thats where is stops. Blank screen with no movement from the PC at all. Unplugged the 200gb sata (trial and error time...) and it started with Ubuntu just fine.

My question is; Is there a limit to the number of sata/IDE drives the Ubuntu can cope with or is it the total sizes of all the drives?

Sorry if my question seems too noobish, but that's where I am at.

Regards

J

---

### Post by darkod on 2010-06-17
You should plug all the disks in and run the boot info script from my signature. You can do it from live mode if you can't start ubuntu. Post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

That will show more info what is going on during the boot.

---

### Post by johnno56 on 2010-06-17
Darko,

Thank you for replying so quickly.

All drives (3 x sata and 1 x IDE) plugged in.
Booted via Live cd.
Executed script.

(hopefully I have attached the result file correctly)

regards

J

---

### Post by darkod on 2010-06-17
All looks fine except:

1. You said in the first post you have ubuntu on 80GB sata. The script says it's on 200GB sata. The only 80GB is the XP one.

2. Connecting the new 1TB between them it seems interfered with the order of the disks. Removing the storage 200GB sata moves them up by one. Try this test:

Switch the mobo ports of the 1TB with the 200GB with ubuntu on it (not the storage one). Put the 200GB in a port before the 1TB. It's now after it it seems.

I'm still not sure if it counts them from sata0 towards sata3 ports, but this will be a good test.

Otherwise all is fine.

---

### Post by johnno56 on 2010-06-18
Darko,

My mistake for the confusion. Sorry.

So, in effect, you are suggesting that the drives be in size order with the smallest (80gb) in first sata socket; the 200gb in the second etc and the IDE drive stays put?

Ok. I will try that configuration and let you know. Could be in the next 5-6 hours.

Thanks for the assist.

Regards

J

---

### Post by darkod on 2010-06-18
> **johnno56 said:**
> Darko,

My mistake for the confusion. Sorry.

So, in effect, you are suggesting that the drives be in size order with the smallest (80gb) in first sata socket; the 200gb in the second etc and the IDE drive stays put?

Ok. I will try that configuration and let you know. Could be in the next 5-6 hours.

Thanks for the assist.

Regards

J

What I am suggesting is to try make the ubuntu disk third in a row, because in the grub.cfg it says root=/dev/sdc1. So it needs to be the third disk, /dev/sdc. Usually grub.cfg would work with the UUID and you wouldn't have this problem. I don't know why your grub.cfg uses root=/dev/sdc1.

If you are sure XP is on the IDE disk, it's reported as /dev/sda. So that means the IDE disk is reported as first.

Out of the other three sata disks, the ubuntu needs to be second, so it can be third in total. So just plug them in the board in a way that the ubuntu disk is second out of the three sata disks.

And see if it works fine that way.

---

### Post by johnno56 on 2010-06-18
Darko,

I have gone thru my drives with a fine toothed comb. This is how they are set up. 80gb IDE has Ubuntu; 80gb SATA has XP; 200gb SATA is for general storage; 1tb SATA (2 x 500gb) for general storage.

I have tried all sata drives in all sata socket combinations and still no boot.

What I have noticed is, that if I remove any drive and reboot, it starts up. I am having a sneaking suspicion that my 680watt power supply, may not be able to cope with the extra drive. (Just a thought)

Here is a better thought. What if I go back to running with Ubuntu ONLY and scrap the Windblows drive.... I have had very few problems with Ubuntu. Very reliable and easy to use....

Thoughts?

regards

J

---

### Post by darkod on 2010-06-18
You can. :)

It's still confusing though. Look at the results file in the top half where the drives with the partitions are listed. It shows one 80GB, two 200GB and one 1TB. Different from what your comb procedure says. :)

What about booting ubuntu and running:

sudo update-grub

However you have to disconnect one disk to allow you to go into ubuntu, so it kind of beats the point. But you could try.

And did you try plugging them in the board ports that way so that the ubuntu disk is second in order out of the three sata disks? For example:

80GB ide, is ide
200GB sata storage, in sata0
80GB ubuntu sata, in sata1
1TB sata storage, in sata2

---

### Post by darkod on 2010-06-18
Scratch that, I think I figured it out. In your first post you said XP is on the IDE. In your last post, you said ubuntu is on the IDE.

If ubuntu is on the IDE, it seems BIOS is counting the sata disks first, then the ide. So by adding another sata disk you made the ubuntu disk from number 3 to number 4.

And regardless how you organize the sata disks, as long as there are three of them, the ide disk will be number 4.

That's why it's working as soon as you unplug one sata. The ide disk becomes number 3 again.

Makes sense?

---

### Post by johnno56 on 2010-06-18
Darko,

I do not mean to drag this out too long....

Although I use Ubuntu and Windows, I do not have them setup as dual boot.

In the past I have had problems with dual boot and the MBR being destroyed. I now boot and manually select which system to swap over to. In BIOS I have Ubuntu or Windows as the Primary master drive. I have been using this method for the past 2 years. A little extra work, but I am happy with it.

The problem started when I added the 1TB sata a few days ago. With all 4 drives connected, Ubuntu will not get past grub. I will try the grub update and get back to you.

Regards

J

---

### Post by confused57 on 2010-06-19
> **johnno56 said:**
> Darko,

I do not mean to drag this out too long....

Although I use Ubuntu and Windows, I do not have them setup as dual boot.

In the past I have had problems with dual boot and the MBR being destroyed. I now boot and manually select which system to swap over to. In BIOS I have Ubuntu or Windows as the Primary master drive. I have been using this method for the past 2 years. A little extra work, but I am happy with it.

The problem started when I added the 1TB sata a few days ago. With all 4 drives connected, Ubuntu will not get past grub. I will try the grub update and get back to you.

Regards

J

You might try to do a temporary edit to grub by pressing "e"(with the first option highlighted), then change your root line from sdc1 to sdd1, then press ctrl+x to boot.

I'm not that familiar with grub2, but if this works, Darko can tell you how to make it permanent or possibly enable UUID for root.

---

### Post by johnno56 on 2010-06-19
Confused57,

Powered down. Reconnected my Windblows drive. (All 4 drives connected) Made the modification that you suggested. Ubuntu booted ok. All 4 drives are visible. You said that this change was temporary? I am all ears on how to fix this...

regards

J

---

### Post by darkod on 2010-06-19
> **johnno56 said:**
> Confused57,

Powered down. Reconnected my Windblows drive. (All 4 drives connected) Made the modification that you suggested. Ubuntu booted ok. All 4 drives are visible. You said that this change was temporary? I am all ears on how to fix this...

regards

J

Unfortunately I can't answer that right away, because I don't know how you made it to work by device name and not UUID. Were you doing any procedures for grub2 not to work with UUID?

Your situation is precisely why grub2 is using the UUID approach, which remain the same even if other disks are added/removed. But your grub2 is working with the device name and after adding a new disk the ubuntu partition name was changed for sdc1 to sdd1.

I guess the first thing to try after you have booted successfully with all 4 disks connected, is still:

sudo update-grub

The situation is different from when you tried it earlier because now all 4 disks are there. Hopefully it will figure out the change itself.

Let us know if it worked. Run update-grub and try to boot ubuntu without editing the line to change sdc1 to sdd1.

---

### Post by johnno56 on 2010-06-19
Darko,

To perform the update-grub successfully, I will first have to boot with the temporary fix first. I will let you know how this works.

I can assure you that I have not done anything with grub or uuid. I installed Ubuntu on the 80gb IDE drive. (no other drives connected - a bit paranoid about destroying the MBR's) Once installed, connected the 80gb sata and the 200gb sata. Rebooted. Voila!

I think the only time I messed with grub was way back during Ubuntu 6.04.

If this fix does not work then I suppose I can return to Ubuntu as my only OS. (could be a blessing in disguise)

In either case, I want to thank you guys for all you help. It is certainly appreciated by this noob.

regards

J

---

