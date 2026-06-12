---
title: "tricking old GRUB to load GRUB2"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by gmoore777 on 2010-06-08
So I have an MBR that is Grub legacy,(from HardyHeron) and I cannot edit/upgrade this MBR. (I won't get into the reasons, other than I will mention SafeBoot).

I have a new encrypted LucidLynx Linux installation on partition 4 and an unencrypted /boot partition on partition #3.

When I boot up, I get the "Error 15" Grub error, which is expected
as Grub legacy is looking for /boot/grub/stage2 
or something like that
and /boot/grub/stage2 does not exist in my GRUB2 installation in /boot/grub.

I thought if I could make a link from the GRUB2 binary of interest to /boot/grub/stage2, then maybe the GRUB legacy would
be tricked into loading the GRUB2 binary.

So the question is, what is the binary of interest in the GRUB2 installation that is the main binary?

---

### Post by darkdragn on 2010-06-08
Drop by here and search for Chainload First... maybe you could make this permanent.
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)


Edit: From HowtoForge
[http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04)

[IMG]http://images.howtoforge.com/images/grub2_ubuntu_9.04/8.png[/IMG]
[IMG]http://images.howtoforge.com/images/grub2_ubuntu_9.04/5.png[/IMG]

---

### Post by darkod on 2010-06-08
To chainload to grub2 you have to have it installed somewhere. Do you have it installed anywhere?

---

### Post by oldfred on 2010-06-08
You will have to install grub2 to the partition which it does not like due to blocklists, but you can use --force to make it install.

But if you cannot reinstall your grub legacy it may not even point to the correct partition to chainboot.

---

### Post by gmoore777 on 2010-06-08
I will look into that link about chain loading.

Yes, I have GRUB2 installed in partition #3, which is just
a boot partition.

Yes, one could say that i have GRUB legacy installed in the MBR.
(that I can't edit due to reasons that I will not go into)

But you do understand what I'm asking about, creating
a link in the partition #3, like this:
    sudo ln -s /boot/grub/linux.mod /boot/grub/stage2

So that when "stage1" which is in the MBR tries to find and load
my trojan horse /boot/grub/stage2, it will really be loading
/boot/grub/linux.mod.

But i don't know which .mod file is the right one, assuming,
that this makes sense.

---

### Post by darkdragn on 2010-06-08
If the howtoforge site is right, then you should be able to work with some commands similar to 

root (hd0,2)
kernel /boot/grub/core.img

If you want to you could build a skeleton menu.lst, and have the only boot option be the above... with little or no delay time. You might not even notice that it's requiring to be chainloaded... worth a try, huh? ^_^

Having said so you would have to find some way to re-install legacy grub, with grub2 right next to it... I'm sorry if I'm just complicating things, >_<.

---

### Post by at0msk on 2010-06-08
> **gmoore777 said:**
> I will look into that link about chain loading.

Yes, I have GRUB2 installed in partition #3, which is just
a boot partition.

Yes, one could say that i have GRUB legacy installed in the MBR.
(that I can't edit due to reasons that I will not go into)

But you do understand what I'm asking about, creating
a link in the partition #3, like this:
    sudo ln -s /boot/grub/linux.mod /boot/grub/stage2

So that when "stage1" which is in the MBR tries to find and load
my trojan horse /boot/grub/stage2, it will really be loading
/boot/grub/linux.mod.

But i don't know which .mod file is the right one, assuming,
that this makes sense.

This may sound really bad but have you used the good ol' "trial and error" approach with the .mod files available?

---

### Post by darkdragn on 2010-06-08
Well... if you'd like, to avoid some of this headache, you could boot the live cd, mount your root partition, and chroot into it. Then follow the instructions at the following to revert to grub legacy... if you are still hellbent on grub2 you could then boot your os, and if you attempt an install from command line (ensure you purged your previous grub2 install) It will automatically do the chainloading instance for you to 'try' grub2... and you could just never change it out, ^_^ lol.


[https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy](https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy)

---

### Post by darkod on 2010-06-08
If you have grub2 on part #3, like one of the posters already said, you should be able in grub1 to simply use something like:

title Grub2
root (hd0,2)
chainloader +1

However, if booting your grub1 from the MBR complains about the stage2 file, that's only grub1 related, I wouldn't say it has anything to do with grub2.

You mentioned you have /boot but didn't clarify if you had it earlier for grub1 too. If you tried to use the same /boot partition that would definitely mix things up.

---

### Post by gmoore777 on 2010-06-08
thank you for those replies.

So I booted up LiveCD, mounted my partition #3, which is the
/boot LucidLynx/GRUB2 partition, I cd'ed into the /grub directory, and then
I `scp`-ed my grub directory from a HardyHeron machine, right into
this grub directory. 

I edited the menu.lst file with
the minimal entry. (not sure if core.img is the correct choice, but it's a moot point)

I rebooted, and I get the same:
    Starting operating system
    GRUB Loading stage1.5
    GRUB loading, please wait…
    Error 15

It doesn't say which file it can't find.

So either I didn't copy all the necessary grub1 files, (there's only 13 of them) or 
the grub1 files are being loaded, and it's the next file that
it can't find,
or the stage1 MBR (which I can't edit) is looking in the wrong partition. (but it should be the same 3rd partition as always
existed before and after this re-install of Linux.) (starting boundary is the same)

I can't tell if I'm getting closer to the solution.

---

### Post by darkod on 2010-06-08
Sorry, are you getting this error only when trying to boot the chainloaded grub2, or the grub1 menu doesn't show at all instead you have this error?

I'm very confused, the error is about grub1 files, what has grub2 or core.img has to do with it?

PS. I think your grub1 boot is broken, you are looking at the wrong place.

---

### Post by gmoore777 on 2010-06-08
going astray here....
In regards to your suggestion with:
  title Grub2
  root (hd0,2)
  chainloader +1

How would Grub1 handle this correctly, meaning how
would it know what to load since it doesn't know
about the new binary names in GRUB2 yet?

---

### Post by darkod on 2010-06-08
That's the point, it doesn't need to know anything. The same way windows loads, the chainloader +1 command says: continue booting the bootloader found there.

You just point it to correct partition, the chainloader +1 command activates the bootloader there, in your case grub2. No exact file names, nothing needed. For windows do you specify the exact boot file name?

---

### Post by darkod on 2010-06-08
PS. Of course, for the above to work, both grub1 and grub2 have to work properly, no missing files, no errors, etc...

---

### Post by gmoore777 on 2010-06-08
I believe it is the "stage1" binary found in the MBR that is giving me the error 15.
Cause I believe it is looking for one of the *stage1_5 or stage2 binary in partition #3 and those files are not there.
(but they are there now, cause I just put them there.)
If I can get past this initial problem, then I can move to the next problem.
Partition #3, is my /boot partition of my LucidLynx installation.
The root / parition is on partition #4 and is encrypted.
Dell Utility partition is partition #1
a SafeBooted Windows partition is on partition #2.

---

### Post by gmoore777 on 2010-06-08
if that chainloader does not look for file names, then
it must load up the first N bytes of that partition.
If that's true, then I'm screwed, in the sense of just
copying the 13 Grub 1 files to my /boot partition.
(cause those files certainly won't be neatly placed in the first N bytes)

---

### Post by darkod on 2010-06-08
I don't know how exactly you installed Lucid. For what you planned, I believe the correct procedure would be:

1. Install Lucid the way you like, at the end tell grub2 to install to /dev/sda3, the partition.

2. Boot your Hardy and in menu.lst add the mentioned entry.

Depending what you did to make this work, you know better than us what is where and how to sort it. We are here for assistance if needed.

You could run the boot info script but I have no idea how it handles encrypted partitions.

If you suspect grub1 is broken, in fact it looks broken, you can always reinstall it on the MBR of /dev/sda using your Hardy disc. Need instructions?

PS. You said "13 grub1 files to my /boot partition". The /boot partition from Lucid should have remained how it is originally, you just chainload to it.

---

### Post by gmoore777 on 2010-06-08
ok, here's the whole story....

machine received from Dell, 
 partition #1  - Dell Utility Partition.

Our IT group installed Windows on it.
 partition #2 - Windows XP

I installed HardyHeron on it.
 partition #3 - HardyHeron (NOT encrypted)
 partition #4 &5 - HardyHeron swap partition
So machine is dual boot, with a Grub 1 MBR, which
would load stage1_5 or whatever  from partition #3.

Our IT group, then encrypts the Windows partition with SafeBoot.
This clearly encrypts Windows partition #2, 
and overwrites the MBR with a SafeBoot bootloader. 
I believe it squirrels away the original MBR somewhere 
secret and encrypted.
So now when machine reboots, the SafeBoot bootloader loads,
prompt user for a passphrase, loads some de-encryption utility,
then the Grub Menu from partition#3 loads, 
and user can choose to load HardyHeron
or Windows (by chainloading to partition #2)
So far so good.

I then with a trusty LucidLynx disk in hand, delete partition
#3, #4, #5, all HardyHeron related.
With the Alternate CD, I install LucidLynx as an encrypted volume in partition #4&#5, and the unencrypted /boot partition in partition #3. 
GRUB2 is installed in partition#3.

This is the current state.

So when machine reboots, the SafeBoot loader in the MBR loads, 
prompts for the SafeBoot passphrase, then finds the squirrelled-away old MBR, loads the stage1 Grub1 bootloader,
and I get the "Error 15".

I had assumed that the stage1 loader was looking for a "filename"
in partition #3, particularly one of the *stage1_5 or stage2 binaries. If it is merely loading up the first N bytes of partition #3, then that is where my understanding starts to get weak and can see that the only solution is to "install" Legacy Grub to partition #3, rather than to "copy" files manually.
"Installing" must ensure that the first N bytes of partition #3
has something of interest there.

So installing Legacy Grub to partition #3 could be a solution.

But I really want to use Grub2 in the /boot partition, since
any maintenance that I do for all the machines will be the same
and I won't have a one-off.

I have my last resort, which is to have the IT group, un-SafeBoot
the MBR and Windows partition #2. This should restore the MBR that it squirrelled away before and restore it. At that point, booting up still won't work, cause it's still the Legacy Grub in the MBR. At that point, I can install Grub2 to the MBR and it should find its mate in partition #3, whether its by file name or the first N bytes.

---

### Post by darkod on 2010-06-08
OK, the error 15 is perfectly normal, you wiped out the grub1 files.
You can't just do that and expect to pick up grub2 just because it's in part #3 again. :)

I have limited knowledge, but according to me what you are trying is impossible.

---

### Post by gmoore777 on 2010-06-08
Getting closer...

So I was thinking, my Grub legacy MBR does not know about ext4 yet: only fat, ntfs, ext3.

So with a liveCD, I mounted then copied all my files off of the /boot partition#3 to another machine, then

I ran gparted and reformatted partition #3 to be ext3 rather than ext4.

I then remounted that partition and copied all the files back.
These files are both the GRUB2 files that were installed via the LucidLynx installtion process, and my manually copied GRUB 1 files
I got from a HardyHeron machine.

Rebooted.

No longer "Error 15", I get my Title bar that I edited in my /boot/grub/menu.lst file.

So I just proved, to myself, that the stage1 binary in the MBR
is looking for files, by name, and not loading up the first N bytes of partition #3.

In my menu.lst, I have used the other gentleman's suggestion (which is same info in [http://en.gentoo-wiki.com/wiki/Grub2](http://en.gentoo-wiki.com/wiki/Grub2)) of:

    kernel /grub/core.img

but that gave me a black screen with one line at the top:

    , bss=0x0Starting up ...

That's all. Anyone know how to load Grub 2 via this "kernel" line in menu.lst?

(/grub is the right directory, as this /boot partition
 will get mounted as /boot once all of this gets working. Meaning
when I mount this partition, cd to it, and do an ls, I am "in" the boot directory at that time. All I see is the grub directory and all the images.
I did have to create a /boot directory and then a /boot/grub directory in this partition, and copied all the Grub 1 files from another computer to it since that is, evidently, what is hardcoded in the Grub Legacy stage1 binary in the MBR.)

---

### Post by darkod on 2010-06-08
Because part #3 was where grub1 boot files were originally, it repaired the error 15. But it still doesn't seem possible to boot grub2 like this.

Like you mentioned in your previous post, isn't it a better solution to talk to your IT dept, un-SafeBoot the disk, install grub2 from Lucid properly on the MBR, and SafeBoot the disk again?

Just like they did after you installed Hardy.

---

### Post by oldfred on 2010-06-08
I forced grub2 into sdc7 and chainbooted to it, when I was testing Karmic 7 or 98 months ago. This was my old grub menu listing stanza to grub2 in sdc7.

title       Ubuntu 9.10 Karmic alpha/beta @ sdc7
root        (hd2,6)
chainloader +1

---

### Post by darkod on 2010-06-08
> **oldfred said:**
> I forced grub2 into sdc7 and chainbooted to it, when I was testing Karmic 7 or 98 months ago. This was my old grub menu listing stanza to grub2 in sdc7.

title       Ubuntu 9.10 Karmic alpha/beta @ sdc7
root        (hd2,6)
chainloader +1

But the thing is I believe neither grub1 nor grub2 are installed correctly in this case. Your suggestion would be fine otherwise.

You have much more experience with grub than me, look in post #18 what the OP did exactly.

In short, deleted the Hardy partitions, installed Lucid in place, and expects the grub1 code on the MBR (that can't be changed because of SafeBoot) to just pick up grub2 and start booting with it. I don't see a way for that to work.

---

### Post by gmoore777 on 2010-06-08
darkod:
I don't expect it to just work, as I said in posting #1, 
when I got Error 15, it was expected.

I don't expect, but hope, that I can get what I have to 
work with some fiddling around.

Going to IT to un-SafeBoot it, then to SafeBoot it again,
can take over a day, once they begin working on it, etc.

I'm looking for a slick 5 minute solution for now and
in the future.
Yeah, it may take several days up front to find that 5 minute solution, and yes I'm also hoping the solution is acceptable
such that I'm not screwing myself in the future when updates for Grub2 come down, etc. 


Hey oldfred,
so in your chainloading example, do you know how Grub 1, the stage2 binary, knows how to load a Grub2 partition? Meaning,
how does Grub 1 know that /boot/grub/core.img is the thing to load since Grub2 came into existence after Grub 1?
I can see the reverse. I can see a Grub2 partition chainload to a Grub1 partition.

---

### Post by oldfred on 2010-06-09
Chainloading does not have to know about where it is going. 
Old grub just tossed it over the fence and expected it to work (continue booting). It is the same with all grub to windows as grub chainboots to the windows code in the windows PBR or boot sector. With grub2 in the PBR or boot sector you just transfer booting to that code.

Grub2 has added modules that now do some checking and then may recover where once old grub transfered and it did not work it usually just crashed.

---

### Post by darkod on 2010-06-09
If you edit the menu.lst with:

title Grub2
root (hd0,2)
chainloader +1

or

title Grub2
root (hd0,2)
chainloader /grub/core.img

What does it say?

---

### Post by gmoore777 on 2010-06-09
---------------------------------------------
title Dell Utility Partition
root (hd0,0)
chainloader +1

Starting up ...
Disk Error

(this is expected)

---------------------------------------------
title Windows SafeBooted Partition
root (hd0,1)
chainloader +1

Windows XP boots up.

This is good for me, cause I believe this can't be
un-SafeBooted if Windows doesn't boot up.

---------------------------------------------
title /boot partition
root (hd0,2)
chainloader +1

Starting up ...
Disk error

I presume that the Grub1 "stage2" binary,
which is the thing that is running while reading
menu.lst
cannot find its predetermined binary in partition#3.
That predetermined binary is either found via file name
or the first N bytes in partition #3.
---------------------------------------------
title LucidLynx encrypted volume
root (hd0,3)
chainloader +1

Starting up ...

No other message. This is expected.

---------------------------------------------
title /boot partition
root (hd0,2)
chainloader /grub/core.img

Error 13: Invalid or unsupported executable format
Press any key to continue.

Pressing any key puts me back into the menu.lst display.
---------------------------------------------
title /boot partition
root (hd0,2)
chainloader /boot/grub/core.img

Error 13: Invalid or unsupported executable format
Press any key to continue.

Pressing any key puts me back into the menu.lst display.
---------------------------------------------

---

### Post by darkod on 2010-06-09
I just thought of something. Do you need to chainload to grub2 at all?

Not sure how it will work because of the encrypted Lucid, but what about:

title Lucid
root (hd0,2)
kernel /grub/linux-image-blabla
initrd /grub/blabla

Shouldn't you be supposed to be able to start any linux from any grub? If I'm not mistaken, with separate /boot partition the kernels are there.

---

### Post by gmoore777 on 2010-06-09
I looked at my grub.cfg and took that information and shoved it in my
menu.lst file per your suggestion.

Success!!: My encrypted partition, partition #4 booted asking me for my passphrase.

My /boot partition #3 didn't get mounted when Linux booted up:
    "The disk drive for /boot is not ready yet or not present."
     "Hit S to skip,...."

I fixed that problem by editing the /etc/fstab, changing ext4 to ext3
(from my previous reformatting that partition #3) and adding the new UUID
for that partition (by running `ls -l /dev/disk/by-uuid`)

So I don't (ideally) like the fact that I would have to manually
maintain the /boot/boot/grub/menu.lst file with the current kernel
version all the time and that I the whole Grub 2 installation is
not being used at all, except for my peaking at grub.cfg from time
to time to see what I should put in menu.lst.

I'm glad that I can boot Windows with the chainloader command
in menu.lst. Cause I can decide whether to unSafeBoot the Windows
partition, install Grub2 on MBR, then SafeBoot Windows.

I may delete my /boot and encrypted partition and start all over again,
cause it seems that I should have been able to either chainload successfully from menu.lst to partition #3 (Grub 2), or to "kernel /grub/core.img" successfully from menu.lst.
I may have corrupted the first 512 bytes of partition #3's boot sector
by running the wrong grub-install or a failed grub-install during all my fiddling and maybe that is preventing the glue to work correctly, not to mention I reformatted that partition to get it from ext4 to ext3.
Those 2 options are ideal, cause that would be the glue to use
a Grub1 MBR, to load a Grub1 menu.lst, which then would load Grub2.
successfully.
I understand this isn't supported, but if it worked, it would be
a 5 minute solution to copy the 13 Grub1 files from an older installation
then create a small menu.lst file with one chainloader command.

Thanks for all your help.

I will post once more on my final resolution.

---

### Post by gmoore777 on 2010-06-09
This is what I have done.

I booted up LiveCD, ran GParted, and deleted my LucidLynx installation
which consisted of partition #3,4,5.

I'm left with partition #1, a Dell utility partition.
and partition #2, a SafeBooted Windows partition.

The MBR has a SafeBooted bootloader. Can't edit this.
The SafeBoot bootloader will load the original MBR that 
existed when SafeBoot was installed. That MBR is a Grub 1 bootloader
installed by a no longer existent HardyHeron installation, and it
wants to find Grub 1's stage2 file in partition #3.

Hence, using GParted on LiveCD, I created a 255 MB partition #3, 
of format ext3. (not ext4 as Grub1 bootloader don't know about
that format yet). 
I am calling this partition, my "Grub1 partition".
It needs to be the 3rd partition and it needs to be ext3.
(due to the eventual MBR that gets loaded, see above)

I mounted this new partition #3, 
    `sudo mount -t ext3 /dev/sda3 /mnt`
Created a directory, 
    `sudo mkdir -p /mnt/boot/grub`
I then copied the 13  Grub1 files from a HardyHeron /boot/grub directory
to /mnt/boot/grub via a memory stick.
I edited /mnt/boot/grub/menu.lst to have:
    title  Windows on partition #2
    root (hd0,1)
    chainloader +1

    title Linux on partition #5
    root (hd0,4)
    chainloader +1

I then, using the LucidLynx Alternate CD, installed encrypted Linux.
Partition #5 being the unencrypted /boot partition, 
and partition #6 being the encrypted / root partition.

I rebooted, I see the Grub1 menu displayed and I can
choose to boot up the Windows or Linux installations.

Done. Success.

---

### Post by oldfred on 2010-06-09
I was not sure you could put back the partition and have the old grub in the MBR find it correctly. Glad you got it working.

If you want to document how you are booting. I run this before I make any changes just to know what is where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

