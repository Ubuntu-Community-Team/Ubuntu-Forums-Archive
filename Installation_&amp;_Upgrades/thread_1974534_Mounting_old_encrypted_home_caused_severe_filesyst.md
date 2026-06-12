---
title: "Mounting old encrypted home caused severe filesystem corruption"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by StiltonSandwich on 2012-05-06
Posting to share my experience here.

I had a (fully working) Kubuntu 11.10 installation (upgraded over time from previous versions).

Every now and again, when an OS upgrade comes around, I like to upgrade my hard drive and do a fresh installation rather than an upgrade, so I decided to do this for 12.04.

The installation went smoothly.

With the installation complete, I connected up my old hard drive using a USB adapter and proceeded to use ecryptfs-recover-private to mount the encrypted home directory and copy over my files.

But when I looked at the files, there was just a set of default empty folders (Pictures, Downloads, Music, etc.). Hmm. Puzzling. The same files as present in the home directory of the new installation (also encrypted). "Ah," I think. "Perhaps it's got confused.

So, I unmount and then remove the drive, then try again. Same thing. Then again - oh; the drive isn't mounting. Why's that then? I start to wonder if maybe loading two home directories at once isn't supported." 

So, I shut down and swap the drives back over, so I can boot into the old installation and copy the files over the other way around. Somehow I get a sinking feeling, so I close my eyes and cross my fingers. Opening them again, I see the error "GRUB error: unknown filesystem".

How could this possibly happen?! I wonder. I wasn't actively modifying the disk. The encrypted directory was mounted read-only and even so surely there is no way it could corrupt the file system.

So I boot back into a Live CD and examine the partitions. The main partition is labelled as "Unknown".

I find the utility TestDisk, which is able to find the filesystem and identify it, vaguely, as "Linux" (which I understood to mean ext2, ext3 or ext4). It cannot access any files on it and suggests it may be corrupted.

Eventually I bite the bullet and run fsck.ext4. It finds a ton of errors and I meekly accept its suggested solutions, as I have no other ideas. The result is an ext3 formatted partition with everything from the root in lost+found. Luckily, above that directory level, things are still named and identifiable. I thought ext4 was completely different to ext3, it worried me that it seemed to have somehow been "down-converted". If it wasn't for the fact I could see familiar file names flashing up, I would have thought it was reformatting to ext3 and wiping everything out.

I manage to piece some of it together; one folder looks like /etc, another, it seems, is /home/.ecryptfs/myuser/.Private, and so on. I found those default home directory folders from the new installation again mixed in with my encrypted files. How and why did it end up writing those onto the disk?!

It's no longer a bootable disk; I couldn't find any of the boot files. But thankfully and to much relief I was able to mount my encrypted home again, this time from the live CD, using ecryptfs-recover-private, and copy all my files onto the new disk.

Luckily the plan wasn't to copy everything across wholesale and replicate the entire set up down to the tiniest setting. That would defeat the object of a fresh installation. But I had been hoping to have access to the old install until I got the new one set up how I like it.

It's been a lesson to me. Most of the irreplaceable files (photos, etc) were backed up, but only oldeer ones. Recent files were only stored in two places by happy accident rather than conscious decisions, and it turned out I didn't know the password to access my main backup, because it was stored on the drive I couldn't access!

Not quite sure where this is going, so I'll stop now.

---

