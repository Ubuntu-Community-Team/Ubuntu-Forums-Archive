---
title: "&quot;Whole Drive&quot; Encryption -- Any advice on where to start on this?"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by rattyboy on 2011-02-12
I have a dilema.

I want to encrypt ALL of the partitions which Ubuntu is using.  So, say I have /dev/sda1 for windows boot, /dev/sda2 for the rest of a windows install.  Now, /dev/sda5 (yes, extended) becomes /boot.  /dev/sda6 becomes /.

I have been digging for hours now trying to find a solution similar to what TrueCrypt does for Windows to use on my new Ubuntu partition.

So far I have come across these scenarios:

1. Not possible.
2. Just encrypt /home -- Ubuntu 10.1 has that capability.
3. Encrypt /home and swap.
4. Why do you want to encrypt?
5. Use pgp to encrypt what you want to encrypt.

None of these are real solutions.

Lets restate the problem.

One can be certain that they are protected if all of the linux partitions are encrypted.  That way, if the laptop goes missing (and it was off when it went missing), then without a passphrase then the data in all of the install is safe.

Any ideas?  I have heard about LUKs.  The install CD I recently downloaded did not have this as an option other than the ability to encrypt my home directory. LUKs is documented very, very poorly.  I would have a better shot at hacking some obscure portion of the Kernel.

I have also seen some links to documentation for older revs of Ubuntu which are not really relevant now.

Obviously with cryptography, only open sourced solutions are valid. :(  Help?

---

### Post by kn0w-b1nary on 2011-02-12
you have to use the alternate cd to use encrypted LVM.

then EncFS and Truecrypt are only redundancy, which is good.

Hope this helps!

---

### Post by rattyboy on 2011-02-12
> **kn0w-b1nary said:**
> you have to use the alternate cd to use encrypted LVM.

then EncFS and Truecrypt are only redundancy, which is good.

Hope this helps!

K -- kn0w-b1nary, I am going to try this.  8)

I will post back when done.

---

### Post by kn0w-b1nary on 2011-02-13
for easy EncFS, add the repos here:

[http://ubuntuforums.org/showthread.php?t=1492885](http://ubuntuforums.org/showthread.php?t=1492885)

then in terminal:
sudo apt-get install encfs-gui

i know it's the Ubuntu CE repos for Lucid, but it works on 10.10 and i only use it for that and dansguardian-gui.

Note: it creates a folder called "encrypted" so it's kinda obvious.

---

### Post by Megaptera on 2011-02-13
Some useful info here too I think:  [http://rationallyparanoid.com/articles/ubuntu-10-lts-security.html](http://rationallyparanoid.com/articles/ubuntu-10-lts-security.html)
"This is an installation guide for Ubuntu Desktop 10.04 LTS that will show you how to enable full disk encryption and confirm that it is working, how to check for and remove unnecessary network services and software, how to enable the firewall and view its rule set, and various security-related software that one may consider installing."

---

### Post by rattyboy on 2011-02-13
Wow.  It worked.

I got the Alternate Install CD from Ubuntu.com.
Then, I manually configured the drive as follows:

1.  Left /dev/sda1 (windows boot) and /dev/sda2 (windows system) alone.
2.  With the extra space on the drive, I created a 100 MiB partition, then created a volume group VGBOOT, then a logical volume LVBOOT.  Then, in weird menu-driven, confusing fashion, I finally figured out that I had to go to the "main" partitioning menu to specify it would be ext4/mount point /boot.
3.  Specified the next 30something gigs as "use for encryption".
4.  Created VGLOCAL using the encrypted partition.
5.  Created a swap and root logical volume.

Not exactly the easiest way to go about setting this up.  I had inadvertently tried various combinations of the above with no success.  Notes:

* you must not encrypt /boot (makes sense as the cryptography in this case is not managed by the boot loader as it is with truecrypt
* the above 5 steps are a bit of a pain.  I would love to try my hand at a new interface for partitioning / cryptography.  But I have 4 kids.  And a wife.  And a job.  And a 1.5 hour commute each way when I could do everything from a VPN connection.  That makes the blood pressure go up.
* The supporters and developers for ubunu rock (thanks to you guys on this thread).
* It would be nice to find a way to get around the whole "laptop on a hostile environment" problem.  But that's a matter for the academic folks and those of us who don't have commutes, jobs, etc.

Many thanks for the tip about the alternate cd. =)

And paranoid?  Me?  Of course!  I am mainly protecting against the threat of losing the machine (its a laptop).  The hostile network threat and the lack of physical protection threat would be nice to have a solution for, however the only place I have ever seen that is when I was working for the government and they had guards outside of a building to prevent and manage physical access.

But, as just mentioned, the real threat to most of us is not someone breaking into the house or breaking into the computer and stealing info.  Its losing the computer and having all those financial documents, phone numbers, etc.

I am so, so happy I jumped out of the 'window' finally and quit running Ubuntu in a VM and switched to running Windows in a VM (for the apps which won't run under wine).

---

### Post by rattyboy on 2011-02-13
> **Megaptera said:**
> Some useful info here too I think:  [http://rationallyparanoid.com/articles/ubuntu-10-lts-security.html](http://rationallyparanoid.com/articles/ubuntu-10-lts-security.html)
"This is an installation guide for Ubuntu Desktop 10.04 LTS that will show you how to enable full disk encryption and confirm that it is working, how to check for and remove unnecessary network services and software, how to enable the firewall and view its rule set, and various security-related software that one may consider installing."

A nice link there.  If you haven't noticed, I love crypto. =)

---

### Post by kn0w-b1nary on 2011-02-13
glad it's working, enjoy!

---

### Post by Megaptera on 2011-02-14
> **rattyboy said:**
> A nice link there.  If you haven't noticed, I love crypto. =)

You're welcome!

---

