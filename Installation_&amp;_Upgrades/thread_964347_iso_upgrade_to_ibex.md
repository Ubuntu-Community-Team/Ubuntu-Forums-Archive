---
title: "iso upgrade to ibex"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by brownbear on 2008-10-30
I have this file: ubuntu-8.10-desktop-i386.iso

This mounts my disk.
```
sudo mount -o loop /home/harsha/Desktop/ubuntu-8.10-desktop-i386.iso /media/cdrom0/
```

I then do this:
```
apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
harsha@Sinclair:~/Desktop$
```
I press enter..
```
Mounting CD-ROM...
Identifying.. [ac20a1ac35626cb607897968f3dd2440-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Found label 'Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)'
This disc is called: 
'Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)'
Copying package lists...gpgv: Signature made Wed 29 Oct 2008 23:24:11 GMT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
W: Skipping non-exisiting file /cdrom/dists/intrepid/main/binary-i386/Packages
W: Skipping non-exisiting file /cdrom/dists/intrepid/restricted/binary-i386/Packages
E: Could not open file /var/lib/apt/lists/Ubuntu%208.10%20%5fIntrepid%20Ibex%5f%20-%20Release%20i386%20(20081029.5)_dists_intrepid_Release - open (13 Permission denied)
E: Could not open file /var/lib/apt/lists/Ubuntu%208.10%20%5fIntrepid%20Ibex%5f%20-%20Release%20i386%20(20081029.5)_dists_intrepid_Release.gpg - open (13 Permission denied)

```

What should I do?

I should have posted that I'm on 8.04 (Hardy Heron).

---

### Post by meganox on 2008-10-31
**sudo** apt-cdrom add?

---

### Post by brownbear on 2008-10-31
Once mounted, if I try the same command with sudo I get this.```
harsha@Sinclair:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
E: Failed to mount the cdrom.
```

Any other ideas?

---

### Post by meganox on 2008-10-31
```
sudo apt-cdrom -m -d=/cdrom add
```The /cdrom mount point is meant for auto-mounted physical CDs, to mount ISOs you should probably use either /mnt or create /media/iso or some other mount point, although it won't matter much in this case, as long as you don't insert a cd in the drive :)

apt-cdrom is designed to work with several CDs I guess, as it mounts and unmounts them automatically, not much use if you have mounted an ISO and not a physical CD.  Use the -m flag to prevent this behaviour.

The -d option specifies the mount point explicitly and may help avoid confusion.

I ran this with the -n flag which prevents changes to sources.list and it seemed OK.  I'm oing to try to upgrade using this method, let me know how it goes with you.

Edit:  By the way, all the official guides tell you to use the alternate CD if you're going to install by any other method than the LiveCD installer.

---

### Post by brownbear on 2008-10-31
I downloaded it again and installed it through the software updater thing.

---

### Post by parsim on 2008-10-31
Look: [handy guide to upgrading from an ISO](http://help.ubuntu.com/community/IntrepidUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD).

There's no mention of using "apt-cdrom"... and as meganox said, you need the Alternate ISO. But this is the method I've used for years, since I'm on a bandwidth-capped internet plan and can get the ISO from a local mirror.

---

### Post by meganox on 2008-11-03
Well it worked for me using the Alternate CD.  First set of updates were a bit odd, got the "Partial Uprade" message, and apt seemed not to be seeing some of the repos.  I had to enable restricted through the Add/Remove menu, for example, even though it was in sources.list.  Seems to be working better now.

---

