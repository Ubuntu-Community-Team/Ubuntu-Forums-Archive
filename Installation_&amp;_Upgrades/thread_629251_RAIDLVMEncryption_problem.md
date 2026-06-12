---
title: "RAID/LVM/Encryption problem"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by palpitations on 2007-12-02
Hey everyone...  I've been trying out Linux & BSD for a few years, but haven't been too involved...  Recently I had my hard drives split 50/50 Linux/Windows - but when I went to reformat, and Windows blue screened on me during the install, I decided I had enough of that nonsense and went 100% Linux :)

Actually, it irritated me so much that I made a script to run "sudo dd if=/dev/urandom of=/dev/sda" 7 times over.  That's more work than the DoD does to wipe top secret info.  I figured since I had a few days away, I'd use it wisely and make sure there wasn't even a trace - not a single bit - of Windows left over on my machine.  It's nice to not be tainted anymore :D  

Unfortunately, I'm having a problem with my Ubuntu install as well...  I know I could get it done and be off and running, but I don't want just a simple, standard install.  I'm looking to do a RAID-0, with everything but /boot encrypted.

Using the alternate install CD, here's what I did, and what my problem was:

#1 - Created 250MB partitions on each drive, set them to "physical volume for RAID"

#2 - Set the raid volume to use Ext3, /boot, made it bootable, etc.

#3 - Set the rest of the space as physical volume for RAID.

#4 - Set the RAID volume to "physical volume for encryption"

#5 - Set the encrypted RAID volume to use LVM

#6 - Made root, home, and swap volumes under that encrypted LVM.

As far as I can tell, that should just work...  And it does for everything but swap.  When I get to dealing with swap, I get the error message "Your attempt to mount a file system with type swap in Encrypted volume (md1_crypt) at none failed."

I've searched all over, and I'm at a loss.  Anyone out there who might be able to fill me in on this one?  Chances are I just missed something simple, but in any case, it's driving me nuts!

Thanks for your help everyone.

---

### Post by siouzi on 2007-12-02
That's strange, since I've got exactly the same setup but with raid1! First I tried just encrypted raid and encountered the swap bug. It's some bug in the installer with raid installations that prevents the swap activation. The solution is to set the space intended for swap to "do not use" and then later activate it - somehow...

Being lazy I really couldn't figure out how to do that and then tried to see if LVM on encrypted raid would allow swap during install. To my surprise, it worked.

In my setup, I created md0 for boot and md1 for all the rest.
- partition md1 raid to be physical volume for encryption
- partition the encrypted volume (md1_crypt) to be physical volume for LVM
- create LVM group and create logical volumes for root, swap and home
- set the / root and /home logical volumes to ext3 and set swap volume as swap.
- set the md0 raid to /boot, ext3, format yes.

Finish partitioning and then the install goes smoothly to the end. The only difference I see is raid0 vs raid1 and can't see that you've missed anything.

The installer seems to be glitchy and shows things like the encrypted device is not active, then displays the partition list like the md1 device is not even in use etc... Just don't go trying to set them as encrypted and lvm again because they are OK.


There is one serious boot preventing bug with encrypted raid1 and possibly with raid0 which you must be aware of. At the end of the install when the cd ejected, hit ALT+F2 and activate the console. Take a look at /target/etc/crypttab and see if it's empty (md1_crypt not in there). If so, here's the fix [http://wiki.debian.org/DebianInstaller/RAIDvsCrypto]("http://wiki.debian.org/DebianInstaller/RAIDvsCrypto").

---

### Post by palpitations on 2007-12-03
Interesting...  I actually meant RAID-1, not sure why I put down RAID-0.  So it sounds like I did exactly the same thing you did, and ended up not having it work out.  The only thing that sounds different is choice in file systems for /home.

I'll keep trying.  Thanks for the tip on the that last bug.  If I can get there far, I'll be sure to keep it in mind.

---

### Post by thinkpad19 on 2007-12-04
If your going to use software raid plus LVM. I siguest you use hardware raid then LVM...

---

### Post by palpitations on 2007-12-04
Still no luck.  Tried installing without a swap drive at all, got a little further, but ended up having problems installing the boot loader.  *shrug*

I'm not too concerned about it though - I could happily run this computer off of a LiveCD and get by just fine.  I was just looking to try something new, and I'm sure it'll get sorted out in time.  For now I'm going to go ahead and test out Hardy on one drive, and use the other to test out some things with OpenBSD and Squid - I need to learn more about those for an upcoming project anyway.

Thanks for the advice - having a community like this, where you can ask a question and get a real, in depth answer - that's one of the things I love about F/OSS.  It may not have solved my specific issue in this case, but at least people care enough to try, and that says a lot.  Take care :)

---

### Post by Moso on 2008-04-23
Hi everbody! :)

I want to install Ubuntu 7.10 with RAID 1 and full disk encryption.  I have searched the forum and Google and none of the tips I have found made it work.

I am using the alternate CD to do a text install.

The option "Guided - use entire disk and set up encrypted LVM" works great but without RAID 1.

Using manual partition I can do RAID 1 work but without disk encryption.

My HDs have 40GB.  I want to create a 500 MB partition to use with "/boot", a 1.7 GB partition for swap and the rest (37.8 GB) use for "/".

First I created the three partitions on the two HDs with "use as physical volume for RAID".  Then I configured the RAID.  Then I use two RAID devices (md1 and md2) to set up encrypted volumes.

When all is done I get the error: "The attempt to mount a file system with the type swap in Encrypted volume (md1_crypt) at none failed."

---

Today I tried with Ubuntu 8.04 RC and same bug still there...

:P

---

