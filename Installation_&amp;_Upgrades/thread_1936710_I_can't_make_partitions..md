---
title: "I can't make partitions."
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by dsman on 2012-03-06
Hey guys,I have problem with ubuntu installation.
I want to make dual-boot install,but when I start with installation and I reach the step with partitions there are no partitions,just clear...
Please help! =(

Youtube video:[http://www.youtube.com/watch?v=BFCqUaTD6rg](http://www.youtube.com/watch?v=BFCqUaTD6rg)

---

### Post by sikander3786 on 2012-03-06
Hi and welcome to the forums! :)

Please press the <super> (Windows logo key) and search for 'Terminal' and open it. Now run this command:

```
sudo fdisk -l
```

Please copy&paste the outputs here so we can have a look.

The problem most probably is being caused because your HDD is formatted "Dynamic disk" in Windows which is a Microsoft proprietary thing and doesn't work with Linux. However, there are some workarounds which we can offer once we see those outputs.

---

### Post by darkod on 2012-03-06
It might be that the disk was used in raid before and has meta data remains. Ubuntu can see this and doesn't show the partitions list.

If you ARE NOT running raid right now, you can boot with the ubuntu cd in live mode and in terminal do:
sudo dmraid -E -r /dev/sda

Confirm to remove the meta data. It should work after that.

---

### Post by dsman on 2012-03-09
Here are my outputs from "sudo fdisk -l"

---

### Post by darkod on 2012-03-09
Did you try the dmraid command mentioned in post #3?

---

### Post by dsman on 2012-03-09
Darko what will happen if i delete my meta that?
Is meta data important?

---

### Post by darkod on 2012-03-09
It is only important if you are running raid in your system. You seem to have only one hdd so it's impossible to run raid.

If your disk has been used in raid before, the ubuntu installer ignores the disk/partitions until you delete the raid meta data remains. Windows ignores it, but ubuntu doesn't.

---

### Post by dsman on 2012-03-10
Thank you,darko!
I deleted meta data and partitions showed,but after i made manually swap and "/" root partition I installed ubuntu.After installation i restarted my computer and I got this error "no such partition
grub rescue>"
I deleted ubuntu partitions,but I still have the same error 
Now i can't even start my windows 7.
Please,help!

---

### Post by sikander3786 on 2012-03-10
That doesn't sound good at all. Please be patient and remember that this has nothing to do with the removal of Raid meta-data.

Probably Grub wasn't installed correctly. Or you somehow didn't install it to its preferred location.

Whatever it was, now we need you to boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here:

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

No need to panic, your Windows 7 install will be there hopefully and also the Ubuntu one probably. The only thing you lose is some time, and also some effort. ;)

After we see the outputs of that script, we can give you easy instructions to re-install the bootloader whether the Windows one or Grub.

---

### Post by darkod on 2012-03-10
You shouldn't have deleted the root partition. In situation where you get grub error, don't panic and try to solve it first.

Deleting the ubuntu partitions will definitely break grub2 even further since it depends on configuration files which are on the root partition. Now they are gone.

You can try installing ubuntu once more into the same unpartitioned space (if you really deleted it) and if grub still gives you an error run the boot info script as suggested and post the results. It will show more details.

If nothing of this works, don't worry, there is still an easy way to make win7 boot. Don't worry about win7, lets make your dual boot work.

---

### Post by dsman on 2012-03-10
I fix the problem with the grub error.I'm in windows 7 now,but I still want to multi boot windows 7 and ubuntu without grub errors -.-
Maybe is my mistake I made 1 swap partition and one "/" root and I installed ubuntu in root partiton,do I need to make boot partition or what I need to do =(

---

### Post by darkod on 2012-03-10
No, root and swap is enough. You can make a separate /home partition to host your Home folders but that is option too. If you don't create it it will be on root.

The minimum it needs is root + swap. And make sure you write the bootloader (grub2) to the MBR of the disk, for example /dev/sda. There shouldn't be a number in it, a number means partition, not the MBR.

There are cases when it doesn't install grub2 correctly but in that case you can try adding it later.

---

### Post by dsman on 2012-03-10
So I need to write "/dev/sda bootloader (grub2)" in terminal?

---

### Post by darkod on 2012-03-10
> **dsman said:**
> So I need to write "/dev/sda bootloader (grub2)" in terminal?

No, I was talking when installing using the manual option (Something Else). In that case under the list of disks/partitions you have a drop down menu to select where to install the bootloader. If you are installing with the manual method make sure you select /dev/sda and not a partition.

If you use any of the auto methods it installs on a MBR by default.

In case it still doesn't install correctly, you can reinstall it to the MBR manually but it first depends why it didn't install. So, instead of speculating, do the ubuntu install again and only if it doesn't work we will investigate.

---

### Post by dsman on 2012-03-10
Hi,darko i made everything u said,but still doesn't work.
I got the error again "no such partition
grub rescue"
Is there a way to add grub manually?

---

### Post by darkod on 2012-03-10
You can add grub, but this sounds like an error where it can't find a certain partition. Look at the no such partition error and write down the last 5-6 characters of the long entry it says it can't find (that is a UUID value).

Then boot into live mode again, and you can check the UUIDs in terminal with:
sudo blkid

Does that UUID exist on the disk or not?

---

### Post by dsman on 2012-03-10
Darko the error is just:
error:no such partition
grub rescue>

---

### Post by darkod on 2012-03-10
Hmm, strange. Lets get more details. Follow the link in my signature, run the boot info script and post the results as explained there. You can do all that from live mode.

That will show more details of the OSs and boot process.

---

### Post by dsman on 2012-03-10
I tried "sudo blkid" and this is what it shows.I will try Boot Info Script now.

---

### Post by dsman on 2012-03-11
This is the Result.txt from Boot Info Script. If you are with windows open it with Wordpad,because with notepad you can't see it.

---

### Post by darkod on 2012-03-11
Strange. The grub2 on the MBR is pointed to a totally different location. Boot into live mode and in terminal try:

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Restart and see if that helped.

---

### Post by dsman on 2012-03-11
I did it,but this doesn't help too =( 
Still same problem.

---

### Post by genyue on 2012-03-11
I have the **same problem**.
I'm currently running Windows 7 64bit.
I want to dual boot Windows 7 and Ubuntu, but I cannot install Ubuntu.

Here's the details:

1. Ubuntu installation cannot detect any partitions.
2. GParted cannot detect any partitions.
---- GParted has an error "Can't have overlapping partitions."
3. fdisk -l <-- It shows my partitions

My guess is either:
 there's some problem with my HDD
or Ubuntu (11.10) cannot detect HDD with many partitions (partitions with different sorts of filesystem).
I'm suspecting the latter.

And ***please take a look at the screenshot***.
It shows what I'm saying very clearly.

---

### Post by genyue on 2012-03-11
> **dsman said:**
> I did it,but this doesn't help too =( 
Still same problem.

dsman, how many partitions have you created in ur Windows HDD?

Is it three?

---

### Post by oldfred on 2012-03-11
@genyue
Please do not hijack someone else's thread. It sounds like if you have overlapping partitions you have a partition table error. Almost any systems that read partition table will not work until it is fixed.
Better to post terminal output than screen shot as I cannot make out details in fdisk. Use sudo fdisk -lu and post in new thread.

---

### Post by dsman on 2012-03-11
Do I need to have istalled ubuntu for outputs from "sudo fdisk -lu"?

---

### Post by darkod on 2012-03-11
> **dsman said:**
> Do I need to have istalled ubuntu for outputs from "sudo fdisk -lu"?

No, it works in live mode without installing anything. The command is included on the cd.

---

### Post by dsman on 2012-03-12
Here are my outputs from "sudo fdisk -lu".

---

### Post by jlh68 on 2012-03-12
Shrink those Windows partitions to free up space on your HD.  

[LIST]
[*]Then use your Ubuntu CD as a "live OS", and use the disk partitioner that is on the CD.  

[*]Alternative is to download SystemRescueDisk, and run as "live OS", use the application GParted on SysResDK.
[/LIST]

---

### Post by dsman on 2012-03-14
I still can't find solution of my problem =(

---

### Post by dsman on 2012-03-17
Any ideas guys?
After i install ubuntu i get following error "no such partition grub rescue>
Please help =/

---

### Post by oldfred on 2012-03-17
Boot script was suggested before so we can see your entire configuration.

This is an easy way to run boot info script.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

