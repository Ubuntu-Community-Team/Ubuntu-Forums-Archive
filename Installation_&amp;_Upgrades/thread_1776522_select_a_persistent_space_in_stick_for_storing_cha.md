---
title: "select a persistent space in stick for storing changes"
date: 2011-06-06
forum: Installation &amp; Upgrades
---

### Post by lse123 on 2011-06-06
what is this during usb installation ubuntu 11.04:
"select a persistent space in stick for storing changes"?

changes mean additional content, or upgrades including personal additional files added to stick or...?

---

### Post by lse123 on 2011-06-08
PLEASE ANSWER ASAP : WHAT IS THIS ALLOCATED USB STICK SPACE FOR EXACTLY?

I want install now...

---

### Post by astrobob.tk on 2011-06-08
> **lse123 said:**
> what is this during usb installation ubuntu 11.04:
"select a persistent space in stick for storing changes"?

changes mean additional content, or upgrades including personal additional files added to stick or...?

I remember installing Ubuntu 10.04 on my 8GB usb & needed space to store my own files within the system. i.e.; when am using the live usb & working on something, i want it to save it.

So its the space you want to keep empty (from Ubuntu files) to store your own files when working in the live session.

check the following threads for more details:

[http://ubuntuforums.org/showthread.php?t=1512856](http://ubuntuforums.org/showthread.php?t=1512856)
[http://ubuntuforums.org/showthread.php?t=1446347](http://ubuntuforums.org/showthread.php?t=1446347) (read this first)

As for installing packages, Ubuntu will install them on the allocated space for the filesystem (i.e.; the root /). If there's no more space, I think it will warn you; never faced this yet. Your files will be in the
/Home

Hope this helps.

By the way, how are you installing ? I personally used "Startup Disk Creator" from the already installed Ubuntu which i am now working from. You can find it under Main Menu > System >  Administration

good luck

---

### Post by lse123 on 2011-06-08
I will install via small program[referred from ubuntu site] in windows...

You mean this space is for my ubuntu files. if needed upgrade is used all the _other_ space,...

this is correct?

---

### Post by astrobob.tk on 2011-06-08
> **lse123 said:**
> I will install via small program[referred from ubuntu site] in windows...


Well i never tried it on Windows. I suggest that if you already have an Ubuntu disc, boot in live mode & use the default Startup disc creator.

> 
You mean this space is for my ubuntu files. if needed upgrade is used all the _other_ space,...

this is correct?

Not ubuntu files, but your personal files like: documents created in OOo or maybe some music files or duno, whatever files & documents u wish to keep. These will be located under your /Home directory/folder where there are Documents, Downloads, Images, etc... folders.

If you upgrade or install new packages/software, they will take space from the root folder: / (called the Filesystem).

The "persistent" option you where asked for is the space you want to keep empty for your "personal" files & documents.

Anyways, check the following pages for official documentation:

[https://help.ubuntu.com/community/Installation/FromUSBStick#From](https://help.ubuntu.com/community/Installation/FromUSBStick#From) Windows

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Installing](https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Installing) Ubuntu on USB drive using Windows

Hope this helps

---

### Post by lse123 on 2011-06-10
you mean if I run linux from stick, and install Skype or Upgrade to 11.10...is the same s saving a document in stick, take stick space from this declared space?

---

### Post by astrobob.tk on 2011-06-11
> **lse123 said:**
> you mean if I run linux from stick, and install Skype or Upgrade to 11.10...is the same s saving a document in stick, take stick space from this declared space?

let me clear it up a bit, I hope:

**/** <-> is the root directory (folder): in this software & system files are set. In case you install new software the files go in here. In my case, I have a 23GB root & though i have lots of software, it only used 12/23 GB.

**/Home** <-> this is your "home" directory (folder). In this, you find user folders. For example, if your user login is bob, you will find a directory called bob. If there are other users, you will find directories for them too, in their names. If a computer has more than one user, it is best to separate their files, right ? Here, /home comes in handy.

Now, under each user name, say bob, you will find the users files. You will find:

Documents (folder)
Downloads (folder)
Desktop (folder
Music (folder)
....

These will contain you folders & files.

In either case, that is, saving files & documents OR installing new software & updating/upgrading, the space is taken from the USB.
As explained, the software & updates/upgrades will be installed in **/** (root) not the **/home**.& of course the size of the stick.

Example: I use a Knoppix 6.5 on a 8GB flash. I made it like this:

4 GB: for Knoppix root (**/**)
4 GB: for my files & doc's (i.e.; **/home**)
-------

If you check out your own system now, you will see that the size of **/** & **/home** are different.

I hope this helps.

In case it doesn't, the following surely will:

[https://help.ubuntu.com/8.04/installation-guide/i386/partition-sizing.html](https://help.ubuntu.com/8.04/installation-guide/i386/partition-sizing.html)
[https://help.ubuntu.com/8.04/installation-guide/i386/directory-tree.html](https://help.ubuntu.com/8.04/installation-guide/i386/directory-tree.html)
[https://help.ubuntu.com/8.04/installation-guide/i386/directory-tree.html](https://help.ubuntu.com/8.04/installation-guide/i386/directory-tree.html)
& this thread on "Partitioning Basics": [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

