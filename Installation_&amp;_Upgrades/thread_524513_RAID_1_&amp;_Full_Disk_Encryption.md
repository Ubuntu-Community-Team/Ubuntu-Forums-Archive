---
title: "RAID 1 &amp; Full Disk Encryption"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by dcotruta on 2007-08-13
This is really a two part question.

I'm rebuilding my Ubuntu installation, since I wanted full disk encryption. I looked in a lot of places, and the guide I followed was the one at [https://help.ubuntu.com/community/EncryptedFilesystemHowto8]("https://help.ubuntu.com/community/EncryptedFilesystemHowto8").

The first question is - is that a "good" tutorial? Does it yield a secure system? It certainly seems to have worked fine for me, and my read/write speed is good.

The second question is: are there any guides / pointers for getting a fully encrypted filesystem running on Ubuntu while using hardware or software RAID 1?

For example, there is a guide to software RAID 1 on OpenBSD at [http://geektechnique.org/projectlab/797/openbsd-encrypted-nas-howto]("http://geektechnique.org/projectlab/797/openbsd-encrypted-nas-howto"). That's the kind of help I'm looking for. 

I don't expect anyone to hand me the answer on a plate, but some guidance, especially where the quality and type of full disk encryption is concerned, would be greatly appreaciated.

---

### Post by ubunubu on 2007-10-22
greetings!

this is what i did and am so far pretty happy with results....essentially i referenced some instructions from a few other 'how-tos' 

this is pretty high level overview, but ultimately it's a pretty effortless way to install full encrypted root and swap, which could easily be modded to have full encrypted root, home, whatever really....

my target:   an old AMD XP2400 with 2.5GB RAM and 2x120GB PATA drives with the goal of full RAID 1 mirroring.

i opted for a server profile, text install from latest ubuntu gutsy.

i configured 3 raid partitions for 500MB boot ,117GB root and 2.5GB swap on each drive.

i then configured unencrypted raid boot...

i then set the 2.5GB swap partition as "do not use".  this is an easy workaround to the bug in gutsy's  text installer.

this is referenced to here:
[http://ubuntuforums.org/showthread.php?p=3551117]("http://ubuntuforums.org/showthread.php?p=3551117")

i then encrypted the raid 117GB partition....you can chop that up however you like, i just did a big 117GB /  and then continued the install.....

ignore the warnings about no swap space, skip all the install options:  DNS, LAMP, etc....that can be done later once it's working, and plus it saves time between failed installs.....:)

The link below details updating the /etc/crypttab so your raid1 root will boot nicely :)  instructions are from debian, but they worked  just fine for gutsy.  

after you reboot, if you get prompted for a password for you're root disk your golden! 

[http://wiki.debian.org/DebianInstaller/RAIDvsCrypto]("http://wiki.debian.org/DebianInstaller/RAIDvsCrypto")

Now one of the first orders of business is to get that swap working...

i referenced part 6 from the link below, except i used sudo to execute the commands and adjusted the hard drive for what my swap was....the commands themselves worked for gutsy just fine.

[http://ubuntuforums.org/showthread.php?t=120091]("http://ubuntuforums.org/showthread.php?t=120091")

afterwards, all that's left is getting some desktop action.....

# apt-get install ubuntu-desktop #kubuntu-desktop, or xubuntu-desktop

enjoy!

---

### Post by siouzi on 2007-11-25
Bump :(

Thanks to ubunubu's post I was able to get encrypted RAID1 working, *I think*, at least /proc/mdstat makes sense and boots fine with both disks attached. However a serious problem arose when I tried to test the raid _mirror_ setup by unplugging _either one of the drives_: password is not accepted.

```
Loading, please wait...
Setting up cryptographic volume md1_crypt (based on /dev/md1)
cryptsetup: cryptsetup failed, bad password or options?

...

ALERT! /dev/mapper/md1_crypt does not exist.

```

OK, how do I boot using one drive only? The closest answer I found was some bug: ["cryptsetup fails for dmraid device"]("https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/160083").

That did not help, only /dev/mapper/control exists and ```
cryptsetup -y create md1_crypt /dev/md1
Command failed: Not a block device
```

Help please :(

EDIT:

It seems the md devices are inactive. md0 is unencrypted /boot and md1 /root. I tried dpkg-reconfigure mdadm, but it didn't help.
```

(initramfs) mdadm --detail --scan
mdadm: CREATE user root not found
mdadm: CREATE group disk not found
mdadm: md device /dev/md0 does not appear to be active.
mdadm: md device /dev/md1 does not appear to be active.

```

---

### Post by siouzi on 2007-11-26
I shall reply to myself. It seems not being able to boot raid1 using only one disk is a common bug/problem in version 7.10. So when one encrypted raid1 drive is missing, you have to wait a few minutes for the BusyBox to appear (ALT+F1 to show console) and then in the initramfs-prompt enter:
```

# to start all md devices
mdadm -A -s

# to enter the passphrase. md1 and the md1_crypt are the same values
# you had to put in /target/etc/crypttab at the end of the install
cryptsetup luksOpen /dev/md1 md1_crypt

# continue to boot!
<hit CTRL+D>

```

After this you can boot with only one disk. I guess this could also be thought of as a feature: you immediately know a drive has failed to start up instead of having to read mail sent by mdadm.

---

### Post by ubunubu on 2007-11-29
wow awesome update siouzi :)

i was so happy with the RAID booting that i never intentionally broke it to 'verify' the mirror was working.

since my post, i was able to do the same type of install on an old PIII with 256mb of RAM....mmmm ubuntu!

now if my mirror breaks,  i'll know where to look!

thx 
ubunubu

---

