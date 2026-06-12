---
title: "No Boot Loader"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by cthulhuxxx on 2010-02-19
I don't even know where to begin...but here it goes...

I have a setup with 2 160GB SSDs in RAID0. I have Windows 7 (64bit) installed on the array. W7 has a 200MB partition installed as a boot partition I guess. So there are 2 partition taken up right away. I shrunk the volume to leave about half (150~GB) unallocated.

I first used the alternate CD (64bit) to manually partition. I thought I needed it to see the RAID. It already saw my partitions as if they were on a single drive.

So I went through every scenario with the partitions:
with /boot
without /boot
with /swap
without /swap
with /home
without /home

I know that /home isn't necessary and neither is /swap. When I use the alternate CD, I keep getting to the same point...it gets to the point where it needs to install grub. But it wont install it. It just keeps looping back to the menu to choose "Install Grub...", and I keep choosing it and getting looped back. So I try to choose the LILO option, same thing. I try to choose "Continue Installation", and get the same problem. I even tried to choose not to install a boot loader, and it wont accept that either. So I abort the installation, and delete the volume and start again.

I also used the vanilla 9.10 64-bit Ubuntu CD, I go through the partitioning steps (/boot and /). It goes through the install with no problem. I restart, and no boot loader. In windows I see the 200MB /boot partition and / partition I made.

So........

???

---

### Post by 1337-h4xx0r on 2010-02-19
Seems like you cannot boot eh? I have a solution for you. I had the same problem a while ago. So if you cannot boot, heres what to do.

1.) Boot up your Ubuntu LIVE CD
2.) Goto GParted and delete your linux partions
3.) Restart the Computer
4.) Boot up your Windows Reinstallation DVD. In this case i will be using 7 as an example
5.) When it asks, select "r" or repair.
6.)choose command prompt
7.) type in: bootrec.exe /fixmbr
8.)Restart computer

this process does delete GRUB loader and any linux files you may have. it does NOT delete Windows or any files. It just takes the Windows boot loader and overwrites the GRUB loader. You will not be able to retreive lost linux files.

-hope this helps

---

### Post by cthulhuxxx on 2010-02-19
No, I can boot into Windows just fine. I am in Windows right now. I look in Disk Management and see the partitions I made when installing with the Live CD. So there are 4 partitions (W7 boot, W7, Ubuntu boot, Ubuntu). I restart and it goes straight to Windows, no boot loader. No Grub.

---

### Post by cthulhuxxx on 2010-02-19
Although, now when I look at the percentages in Disk Management, the two Ubuntu partitions are 100% available. So now it seems that it didn't even install. ???

---

### Post by cthulhuxxx on 2010-02-20
Any help on this?

I have enough room on the disc/array. Ubuntu is seeing it as 1 drive with the unallocated space to install on. I assign a partition for /boot, and one for /. Yet when it comes to install grub, it won't install. It just keeps giving me the option to install grub. I tell it to do it, and it just loops back after a quick attempt. I even tried to choose the LILO option, Continue with Installation, Continue without Boot Loader. As stated from the original post, I tried installing with a /boot partition, without, with a /swap partition, without, with a /home partition, without. I've even gone so far as to install on a 3rd hard drive on my computer which is completely empty, not in RAID, and still get the boot loader install problem. Again, this is using the alternate CD (I thought I needed for the RAID set up).

---

### Post by darkod on 2010-02-20
You shouldn't have any problems installing it on a third drive. Strange.
Anyway, you are right, the guides say you're supposed to use the alternate disc for RAID installs.

But because it doesn't work for you, you can try with the standard desktop cd too. Follow this guide, in the content you can see LiveCD Installation under 3.1.2. With few tweaks at the start which make the standard cd see the fakeraid, you should be able to install this way too.

Hope it helps. As for windows saying the partitions are empty don't forget windows can't read linux filesystems. Windows will not be able to tell you how much of the linux partitions you have used. I guess it did get installed, only grub didn't.

In that case, try to adjust the procedure in this article, start with the first steps to make the array visible, skip the step 8 about the actual install, and continue with step 9 to add grub. I think it should work.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by cthulhuxxx on 2010-02-20
When I start either the alternate or vanilla install, neither of them are seeing the drives as separate drives in a RAID configuration, both versions are seeing them as one continuous disk, which leads me wonder if my RAID is a hardware RAID. I just assumed it was a software RAID as my last one was. On my previous rig with RAID, the vanilla install (Live CD) was seeing the two separate drives, this new rig I got is not showing up as two.

---

### Post by darkod on 2010-02-20
You might be right but those fakeraid instructions should be good for hardware raid too. At the end of the day, fakeraid also should first create the array and show a single device to the OS.

Give it a shot. As I said, I think you have ubuntu installed, so just use part of the steps to make the live cd see the raid (9.10 could be seeing it even without any additional steps) and then the steps to install grub.

---

### Post by cthulhuxxx on 2010-02-20
So how do I get into the installed version?
Can I reach it through the Live CD?
If I boot up with the vanilla Live CD; do I choose to "Try.."?
Once I'm in; how do I know?
If I'm in; do any of the changes I'm making while inside of the Live CD take effect on the installed?

So many questions, for such a minor problem.
I really appreciate your time.
And let's say that I can get the boot loader going;, do I really need a /boot partition?
Or could I reserve that final partition for /swap?
I'm good either way.

---

### Post by darkod on 2010-02-20
First of all, have in mind that those fakeraid instructions are for 9.04 and 9.10 has the difference that it already has the dmraid package included. So the first few steps after you boot with Try Ubuntu that are to install dmraid I think are not necessary at all if using a 9.10 live cd.
I would start with step 5 first, checking if you can see the array from the live desktop:

ls -l /dev/mapper/

If that gives you the name of the array as a result, you can already see it. Write down the array name as you'll need to use it.

You should already have partitions created and ubuntu installed so you could skip steps 6,7 and 8.

So then you could continue from step 9 to mount the root partition and install grub. Note that when trying to mount in

sudo mount /dev/mapper/isw_beeaakeeaa_five[COLOR=Red]5 [/COLOR]/target/

the number 5 is the root partition. Change that number in the command depending what is your root partition. So, you use the array name that the ls command returned above, and at the end you add a number for a specific partition.

Also take into account when reaching the commands to install grub that this is written for 9.04 and grub1. I can only assume how to change the commands to install grub2 but you already know your root partition so it should be easy.
Instead of

find /boot/grub/stage1
root (hdX,Y)
setup (hdX)

You can probably just do

sudo grub-install --root-directory=/target/ /dev/mapper/arrayname_nonumberatend

---

### Post by cthulhuxxx on 2010-02-20
Wow! All of that is sooo advanced. I barely have a clue what all of that is. I'll have to study that and try and figure out what it means...to a point. My brain hurts just re-reading it. I'm still very much a novice to linux. I'm definitely a GUI person. Command line is still pretty over my head. But I wonder how much I actually need to understand vs how much I just need to plug in variables. Either way.....ugh!!!

---

### Post by darkod on 2010-02-20
It's not so advanced as it looks. :)
If you already went through the alternate installer, that's not GUI too. And I'm far from an expert myself even if it looks that way. I just wish I had a second hdd to play with all this in raid. That's how you learn.

---

