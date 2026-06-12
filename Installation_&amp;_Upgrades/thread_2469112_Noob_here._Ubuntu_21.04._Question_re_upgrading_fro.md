---
title: "Noob here. Ubuntu 21.04. Question re upgrading from ext4 to 21.10 and btrfs."
date: 2021-11-19
forum: Installation &amp; Upgrades
---

### Post by Advait on 2021-11-19
I&#8217;m currently using Ubuntu 21.04 with ext4 on an internal 2TB nvme drive (AMD Ryzen with no dual boot). I want to upgrade to 21.10 with btrfs. I&#8217;m assuming I need to totally wipe out 21.04 and do a clean install of 21.10 in order to go from ext4 to btrfs. If this assumption is wrong, let me know.

I&#8217;ll first do a Clonezilla clone of my main hard drive to an external drive (I've got Clonezilla installed on a USB stik). Also I&#8217;ll have multiple backups of all my user files (FeeFileSync and Restic). If you have suggestions re better ways to backup user files, let me know.

I&#8217;ll have Ubuntu 21.10 loaded onto a USB stick ready to install. I&#8217;ll select btrfs during the 21.10 install process.

What else do I need to do to help assure this upgrade goes smoothly? I&#8217;m a newbie and very much a beginner with Linux and very limited knowledge of the command line. What are the common problems that arise when doing this kind of upgrade?

(PS: I want to upgrade to btrfs cuz I&#8217;ve heard good things about btrfs fast snapshots and easy rollbacks. Also I'm an average user just browsing the web, checking email, working with some simple spreadsheets and not much else.)

---

### Post by guiverc on 2021-11-19
Also asked at [URL="https://askubuntu.com/questions/1376614/what-do-i-need-to-do-to-install-21-10-with-btrfs"]https://askubuntu.com/questions/1376614/what-do-i-need-to-do-to-install-21-10-with-btrfs

I'd have replied here if I'd have seen it first; less hassle of trying to fit what I was trying to say into a askubu comment...
[/URL]

---

### Post by MAFoElffen on 2021-11-19
With looking externally to another website...

I would say the fastest and easiest would be a new install to a new, clean installof where you want to be, with the filesystems and or file managers you want to be using, and migrate your applications and files to it.

That is just a thing... It is a proven methodology.

---

### Post by Advait on 2021-11-21
> **MAFoElffen said:**
> With looking externally to another website...

I would say the fastest and easiest would be a new install to a new, clean installof where you want to be, with the filesystems and or file managers you want to be using, and migrate your applications and files to it.

That is just a thing... It is a proven methodology.

After reading the comments here [https://askubuntu.com/questions/1376614/what-do-i-need-to-do-to-install-21-10-with-btrfs](https://askubuntu.com/questions/1376614/what-do-i-need-to-do-to-install-21-10-with-btrfs) it seems that btrfs snapshot and rollback features don't work on Ubuntu 21.10. And that Ubuntu 21.10 and btrfs don't play well together. I'm a noob so let me know if I'm misunderstanding the comments at the link. So right now it looks like btrfs is definitely not for a noob like me.

---

### Post by guiverc on 2021-11-21
It's not that the don't work; they'll work as well as other non-Ubuntu systems will once setup.

Some distributions assume *btrfs *and are thus automatically setup for that *file-system*, Ubuntu doesn't assume a *btrfs* format; it's just offered as an option for users that want it.

As I've said on *askubu*, I'd not recommend *btrfs* for a *newbie* using Ubuntu.   I've used it under openSuSE where yes the additional features were nice on occasion, but even then; the costs to me weren't worth it.

FYI:  I do believe I have a system here using *btrfs*, but I also have another where I purposely removed the *btrfs* replacing it with another *file-system* (*disk space issues; snapshots need space*). If I destroy a desktop system through *stupid mistake*, I believe I can have it re-installed & operational in ~20 minutes assuming I didn't destroy my data (just the OS itself), thus a re-install will wipe away the corrupted OS, re-install anew, then auto-re-install my *manually installed* packages during the installation process & ask to reboot & I'm back in operation. Later in the *development* cycle I'll use that technique to perform *upgrades* on a number of boxes for QA (*Quality Assurance*) purposes.

If you want to use it, you're welcome to. Many guides exist on setup; eg. [https://theduckchannel.github.io/post/2021/08/24/install-ubuntu-21.04-with-btrfs-+-snapper-+-grub-btrfs/](https://theduckchannel.github.io/post/2021/08/24/install-ubuntu-21.04-with-btrfs-+-snapper-+-grub-btrfs/) which may not be the best; I'm using it as an example. It's my opinion it's not the best strategy for a *newbie/noob*.

---

### Post by monkeybrain20122 on 2021-11-21
It is easiest to do a fresh install and choose btrfs (choose Advanced/manual during install, and you need to make a swap partition if you want to use suspense. Apparently suspense doesn't work with btrfs if uses a swap file)  There are conversion guides on the internet but they are complicated and I don't trust them (e.g btrfs-convert is removed from Debian because it is buggy even though many guides use it) I have btrfs on Ubuntu 21.04 and upgrade to 21.10, then use btrfs to restore back to 21.04 just to show that it worked.

---

