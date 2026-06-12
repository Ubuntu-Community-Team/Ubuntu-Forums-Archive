---
title: "Cannot load Ubuntu from Grub"
date: 2012-12-20
forum: Installation &amp; Upgrades
---

### Post by krisityfer on 2012-12-20
Before I begin, I must say I am very green when it comes to linux, bash and all this. So please go easy on me.

Basically when I try to load Ubuntu from the dual-boot screen, I get brought to a terminal with the following:

"GNU GRUB version 1.99-21ubuntu3

Minimal Bash-like line editing....

grub>"

This started after, upon loading windows, my filesystem was checked and certain files it deemed corrupt or whatever were deleted. I saw the word "orphan" a lot.

I have tried numerous solutions to get this to load Ubuntu for me but I am having no joy. Here are what I think are the important details:

[LIST]
[*]This is Ubuntu 12, though what version I am unsure
[*]It was installed using wubi. On windows, the folder C:/ubuntu/disks/grub/boot is empty.
[*]When I type "linux /boot/vmlinuz" and then press tab, no results are filled in. Apparently this is supposed to autocomplete my kernel.
[/LIST]

I'd really appreciate some help with this, as I have no idea what I am doing, and I don't want to **** up my computer too much. It'd be super if I could do this while retaining all the files on my Ubuntu account. Thanks in advance.

---

### Post by oldfred on 2012-12-20
Welcome to the forums.

I do not know wubi well, as I use full partitioned install.

Did you run chkdsk from Windows and it perhaps moved the wubi file into the  chkdsk folder?

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

    Missing root.disk
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

       How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

If you are finding you like Ubuntu, it may be time to change to a full partitioned install. 
       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)> 
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

There was a recent post that an empty grub folder is normal with the newer versions.

---

### Post by krisityfer on 2012-12-20
> **oldfred said:**
> 

       How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)


So I tried this and in doing so appear to have found the problem; none of the disks sda1 through sda5 contain any of the files my partitioned Ubuntu drive should. sda1 is practically empty, 2 is my C: drive, 3 doesn't exist, 4 seems like it should be Ubuntu but it doesn't contain /ubuntu in any way, and 5 is my D: drive. 

So does this mean that my ubuntu stuff is irretrievably lost? Because if so I might just give up the ghost and do a proper install.

---

### Post by oldfred on 2012-12-20
Normally you install wubi to the Windows c: "drive" or partition. One of the main advantages of wubi is that you do not have to partition and unpartition if you decide you do not like wubi/ubuntu.

Wubi uses just one large file root.disk in your NTFS partition.

---

### Post by bcbc on 2012-12-21
> **krisityfer said:**
> So I tried this and in doing so appear to have found the problem; none of the disks sda1 through sda5 contain any of the files my partitioned Ubuntu drive should. sda1 is practically empty, 2 is my C: drive, 3 doesn't exist, 4 seems like it should be Ubuntu but it doesn't contain /ubuntu in any way, and 5 is my D: drive. 

So does this mean that my ubuntu stuff is irretrievably lost? Because if so I might just give up the ghost and do a proper install.

Check in the \ubuntu\disks folder. Look for the root.disk. If it's not there, the chkdsk might have detected corruption and recovered it intact. See here for details: [http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted]("http://askubuntu.com/q/228709/14916")

If you can recover the root.disk you can at least recover your data, and at best migrate to a normal install from it.

---

