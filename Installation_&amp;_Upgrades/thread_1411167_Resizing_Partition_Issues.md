---
title: "Resizing Partition Issues"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by GaMz on 2010-02-19
I recently used a GParted CD to resize my partition with Vista installed on it in order to make room for another partition in which I installed Linux onto.

I, unfortunately, did not back up my data #-o

My Vista partition now does not show up in Grub and when I set it to just boot to the Vista install it will never boot and is stuck in a loop.

I tried using [_this_](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/) guide to try to get it back. 

My problem comes about halfway through this guide when I go to repair my Vista installation nothing shows up under installations.

I was wondering if anyone had any advice, because I would really like to get my data from the Vista partition. I guess if I'm SOL then at least I'll remember to backup my data next time..

---

### Post by darkod on 2010-02-19
Can you post the result of

sudo fdisk -l

and if there are more ntfs partitions tell me which is the vista system partition. I have an idea and can give you more info after I see the partitions.

---

### Post by GaMz on 2010-02-19
It's telling me that command isn't found. I'm using OpenSuse because that's the CD I had laying around if that matters.

Is there anything else I can run? I have a picture of the system information with the partitions shown though.

[[IMG]http://img63.imageshack.us/img63/7642/snapshot1y.th.png[/IMG]](http://img63.imageshack.us/i/snapshot1y.png/)

Here's a screenshot of me trying to run the command, maybe I'm doing something wrong.
[[IMG]http://img196.imageshack.us/img196/1151/snapshot2yj.th.png[/IMG]](http://img196.imageshack.us/i/snapshot2yj.png/)

---

### Post by darkod on 2010-02-19
I know which commands to run from ubuntu, but not sure if they are exactly same in suse. You are on ubuntu forum so I assumed you have ubuntu cd at least that you can run in live mode.

Otherwise the idea was:

1. Restore windows bootloader on the MBR of the hdd (not necessary but better). That will try to boot vista straight on boot.

2. Mark the vista ntfs partition as "dirty" so that windows will start the chkdsk check when trying to boot vista.

You do that in ubuntu by installing the package ntfsprogs and you can run:

ntfsfix /dev/sda1

That can't check it from ubuntu but it marks it as "dirty" and at next boot windows will run chkdsk.

That was my idea, if you can make it work from suse, no problem.

PS. You can do the above from ubuntu cd in live mode, no need to even install ubuntu. But you do need to have an ubuntu cd.

---

### Post by GaMz on 2010-02-19
I appreciate your help, I'll just do it in Ubuntu. I'll download it now and see what I can do. I'll post back after I have the LiveCD running and tried what you said.

Thanks a lot

---

### Post by darkod on 2010-02-19
Just a reminder, step 1 from above is not necessary if you can still select vista from your grub menu (yes, you said it doesn't work, it loops). But as long as you can select it, after executing that ntfsfix command it should make vista start the chkdsk check next time you select it.

If that doesn't work, there are ubuntu commands to install generic windows mbr on your hdd and as long as /dev/sda1 has a boot flag (whichyou can easily check in Gparted from ubuntu live mode and set the flag if it isn't there) it will try to boot vista.

But as a first try it's better that you keep suse grub on the mbr and just try starting vista from the grub menu and hopefully it will start the chkdsk as said above.

---

### Post by GaMz on 2010-02-19
Ok, so I'm running Ubuntu. I checked and made sure I had that package installed, and then I ran that command that you posted and this is what I got.

[[IMG]http://img716.imageshack.us/img716/2346/screenshotqe.th.png[/IMG]](http://img716.imageshack.us/i/screenshotqe.png/)

Before doing that I did not have Vista listed in Suse Grub, will that make it show up? 

If not how do I go about "restoring windows bootloader on the mbr of the hard drive"? Is that done through GParted by just making that partition flagged with 'boot'?

I'll try it again now that I've ran the ntfsfix, though. 

Thanks again.

---

### Post by darkod on 2010-02-19
You need to have the boot mark on /dev/sda1 because windows boot process depends on it. But that's half of the job.

From ubuntu live desktop, then you need to install generic mbr on /dev/sda which only calls the boot flag (that's why you need to have it):

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

It will issue some warnings but ignore them, that's expected.

Note that after this the computer should boot straight to vista, or at least try to which should trigger the chkdsk you prepared with ntfsfix.

Grub from suse on the hdd MBR will be gone, but as long as vista gets repaired, use your suse live mode to reinstall grub back on the mbr.

---

### Post by GaMz on 2010-02-19
I tried all that and it still keeps trying to boot but never does. 

Does it matter the order I did any of those things in, because I did ntfsfix before I restored the Windows bootloader.

Any other reasons why the chkdsk didn't automatically start? 

I also have an explanation point next to that partition in GParted, I assume that just means there was a problem with the resizing..but I figured I'd post it anyway-maybe it will help.

[[IMG]http://img684.imageshack.us/img684/2342/screenshottx.th.png[/IMG]](http://img684.imageshack.us/i/screenshottx.png/)

---

### Post by darkod on 2010-02-19
The order shouldn't matter but you could try running the sudo ntfsfix /dev/sda1 again.

Also, you can run chkdsk from vista install disc if you have one, but I don't know how, you would have to google for it.

---

### Post by GaMz on 2010-02-20
No luck with that, it won't let me CHKDSK because it is RAW data?

Since I only really need 1 folder from the other partition, I found [_this_](http://www.z-a-recovery.com/unformat-tutorial.htm) program - which seems to recover a folder to an external hard drive.

The only problem is I'm running Ubuntu and they only offer a .exe. 
1) Is there any Linux equivalent to this?
2) Is there a way I can get it running with Wine or something?
3) Any other ideas how I can just recover 1 file from this RAW data?

Thanks

---

