---
title: "Converting from Windows 7.."
date: 2012-08-22
forum: Installation &amp; Upgrades
---

### Post by pyrokinetic on 2012-08-22
Hi there, 

I am attempting, for possibly the hundredth time, to install a variant of linux (Ubuntu) onto my computer (Compaq Presario C57) and I'm having a lot of difficulty. 

First thing I did was shrink my windows partition to free up some space, which now appears as 'Unallocated Space' with a black stripe across it in Disk Management. 

After firing up the Ubuntu 12.04 LTS installer from a flash drive I try to install onto the 30gb of unallocated space I have. Unfortunately this is where I hit a brick wall. It shows my 'System' partition. my Windows files (Windows folder and everything typically you'd see in a C:\ drive on Windows) a 'Recovery' partition, and an 'HP Tools' partition.....but sadly my unallocated space is nowhere to be found?

So I thought....fine, I'll just resize my windows partition from within the installer and get my free space that way. Nope. Every time I try it some kind of error pops up about not being able to write to the device. After the error message is cancelled out I can't do anything apart from restart and try again.

I decided, at this stage, to go onto the Ubuntu IRC channel on freenode.net (I think that's what it's called?) and was advised to try the alternate install CD to see if that helped at all. This also failed while trying to boot, giving some error about not being able to read a file or something.....when clicking 'yes' to try reading again the same message would pop up.

Basically.....I've no idea how the hell to proceed. I last logged into this site in 2006 (according to my little login thing in the top right) ....And what was I doing then? Looking for answers for more issues I've had with Ubuntu and other linux variants. I KNOW linux is powerful and I KNOW a lot can be done with it, just wish it was actually....oh.....I don't know........EASY TO INSTALL... :\ I simply don't believe I'm the only person on Earth to have these kind of issues.

---

### Post by MARP1961 on 2012-08-22
You can only have up to 4 Primary Partitions on a hard drive. If you want to keep Windows 7 and have Ubuntu you may need to delete another partition and incorporate it into the unallocated space ready to reformat. The 'HP Tools' partition probably contains nothing essential.

---

### Post by MARP1961 on 2012-08-22
Have you tried booting and installing Ubuntu 12.04 from a CD or DVD instead of USB? I have had strange issues from USB installs.

---

### Post by mastablasta on 2012-08-22
> **MARP1961 said:**
> Have you tried booting and installing Ubuntu 12.04 from a CD or DVD instead of USB? I have had strange issues from USB installs.
 
 
i think you were correct the first time. OP already has 4 primary and needs to remove one (Hp_tools - backup and delete the partition...).

---

### Post by pyrokinetic on 2012-08-22
> **MARP1961 said:**
> You can only have up to 4 Primary Partitions on a hard drive. If you want to keep Windows 7 and have Ubuntu you may need to delete another partition and incorporate it into the unallocated space ready to reformat. The 'HP Tools' partition probably contains nothing essential.

I wondered if this could have something to do with it. I removed the partition so it now shows up as 'Unallocated Space' along with another 30gb partition. It made no difference when I tried to install Ubuntu again.

However I also noticed that after removing the partition I still have it's old drive letter in when I go to 'Computer', trying to access it just gives me an 'Access Denied' error.

Another interesting thing I noticed is if I try opening gparted while 'trying out' Ubuntu it lists my Recovery partition and the 'unallocated space' as one partiton. I figured this out because the size of the Recovery partition is much bigger in linux and equals to the size of the HP Tools partition, the ACTUAL Recovery partition and the other 30gb I had of unallocated space.

Just wondering if maybe that gave you any thoughts? I don't want to remove my Recovery partition in case I ABSOLUTELY have to. 

I haven't tried installing it from an actual CD/DVD yet, just USB but I'm willing to try.

Also....I thought I should mention that my C and Recovery partitions (and my unallocated space) are all on a Dynamic disk. I've tried converting it back to a Basic disk with EaseUS software but received an error that it could cause data loss if I continue. I'm at a loss as to how to continue without completely reformatting everything. There MUST be a way around this.

---

### Post by MARP1961 on 2012-08-22
Is this Recovery Partition needed? If you can still use the Windows 7 installation, why don't you just burn yourself Windows 7 Recovery Disks? I'm sure you can do this. Check this first and burn and check these disks before deleting the recovery partition.

---

### Post by pyrokinetic on 2012-08-22
> **MARP1961 said:**
> Is this Recovery Partition needed? If you can still use the Windows 7 installation, why don't you just burn yourself Windows 7 Recovery Disks? I'm sure you can do this. Check this first and burn and check these disks before deleting the recovery partition.

I've got the Recovery side sorted. Now when I boot into the Ubuntu installer I get 4 'partitions', this isn't the exact amounts but close enough.

(These were all under the heading sda I believe. Sorry if that's already obvious but as you can tell I'm not quite a linux pro yet!)

sda1 - 1mb
sda2 - 208mb
sda3 - 440GB
sda4 - 51GB

When I look through Disk Management in Windows it only shows 3 partitions, labelled "SYSTEM" ...."C:".....and "Unallocated"

I'm guessing the other partition I saw in Ubuntu, the first one with only 1mb, has something to do with the 'SYSTEM' partition? If so that would mean that I'm using my 51GB 'Unallocated' partition for Ubuntu (sda4)...question is...now what? do I select it and then let it do it's thing? not quite sure how to progress.....some assistance would be great.

Big thanks for the help thus far.

---

### Post by darkod on 2012-08-22
If the disk is still Dynamic, DO NOT continue!

Dynamic disk is MS format and ubuntu can't understand it properly. It will never work OK, you can only mess it up.

Not sure what the error meant when you tried to convert it to Basic, but dual boot with linux can be achieved only on Basic disk if I have got it right.

There have been cases here when it looked like it managed to install on dynamic, but never worked, so don't do it. It can only create problems.

You need to find a way to go back to Basic. Usually the EaseUS was a good tool to do that.

---

### Post by pyrokinetic on 2012-08-22
> **darkod said:**
> If the disk is still Dynamic, DO NOT continue!

Dynamic disk is MS format and ubuntu can't understand it properly. It will never work OK, you can only mess it up.

Not sure what the error meant when you tried to convert it to Basic, but dual boot with linux can be achieved only on Basic disk if I have got it right.

There have been cases here when it looked like it managed to install on dynamic, but never worked, so don't do it. It can only create problems.

You need to find a way to go back to Basic. Usually the EaseUS was a good tool to do that.

Despite the warning I'd been given in EaseUS I decided to press on and have it convert back to Basic for me, knowing full well I'd quite possibly lose all my data on reboot, and....

IT WORKED! I've now got a Basic disk :D Also...when I go into the Ubuntu installer I now have 51gb of 'free space'!!! 

How do I proceed from here? This is the closest I've ever been to actually installing Ubuntu! So happy! :D

---

### Post by pyrokinetic on 2012-08-22
I decided I was being impatient and thought I should give the install another try. I followed the following guide. [http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/) which helped me install it. Thus far everything seems to work perfectly and I thank everyone SO much for their help in getting me on the right track. I will change this to 'SOLVED' to help any newbies but I figured I should also summarise what I did;

Step 1 - Resized my Windows partition from within Windows 7.
Step 2 - Somehow after resizing my partition I managed to make my partition 'Dynamic' - If you encounter the same problem then DO NOT PROCEED until you have converted your Dynamic disk to a Basic disk. I used a program called EaseUS Partition Manager (or something along those lines. I'm sure someone will know the exact name but a google search will also help) - I also recommend backing up any important data BEFORE using this program. It claims to change Dynamic disks to Basics disks without any data loss, I never lost any data but it MAY not be the case for you.
Step 3 - Assuming you have some unallocated space, on a Basic disk, you can go ahead with the installer and if you have 'free space' showing in the installer then FOLLOW THE INSTRUCTIONS ON THE WEBSITE. If you DON'T have free space showing at this point then perhaps come back here for more answers.
Step 4 - Install as directed by the tutorial, there is another step involving setting up a bootloader which MUST be followed in order for this to work. 

GOOD LUCK!

---

