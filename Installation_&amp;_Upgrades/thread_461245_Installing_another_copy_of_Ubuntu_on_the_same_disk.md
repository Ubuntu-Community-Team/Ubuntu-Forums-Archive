---
title: "Installing another copy of Ubuntu on the same disk!"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by boom2k1 on 2007-06-01
*I am not a Ubuntu guru.

I am now using Ubuntu 5.04 on a 4.8GB disk partition. The reason I want to install a fresh copy of Ubuntu is because 1. disk space and 2. quite a few things screwed up. However, it is still very usable and I have invested huge amount of time just getting every hardware to work (ie. having some scripts to gett the unsupported SiS laptop) video card to be able to display 1680x1050 on my external monitor while the laptop screen is off.).

Anyways, that means I won't want to screw up this copy of ubuntu unless I can replicate everything on a freshly installed Ubuntu 7.04.

My partitions are as follows:
/dev/hda10 /documents vfat 2.0GB
/dev/hda2 /windows ntfs 18.6GB
/dev/hda5 /storage ext3 9.6GB
/dev/hda7 ext3 / 4.8GB
/dev/hda8 ext3 /home 1.4GB

Would it be possible for me to install 7.04 on hda5?  (i can transfer everything in /storage to an external disk)?
How would I do that?

Below are some of my concerns:
1. would I be destroying the boot loader that let me choose which OS to run when the computer starts? (and also how could I modify that screen?)
2. would i be able to install another copy of ubuntu on that 9.6gb?
3. could i also use /home to share those customized settings? (what is /home anyways?)
4. HOW WOULD I UNINSTALL THE OLD 5.04 WHEN 7.04 WORKS PERFECTLY (without killing the bootloader)?

Thanks.

---

### Post by hartz on 2007-06-01
Now THIS is an interesting question.

You will discover that dual-booting multiple intelligent operating systems is a total pleasure.  Especially because they properly understand one another's file systems.

To answer your concerns:
1.  You are indeed likely to destroy the existing bootloader, but don't worry about it, you will just get a new one, and this would probably be preferred, see point nr 4 below.  I do not know whether the Ubuntu installer will intelligently handle existing grub config files, eg by finding and importing any existing menu.lst files, but I am sure that you will still be able to boot into each Ubuntu instance because Ubuntu will add them all to the menu.

If you have never customized the boot loader menu, then you don't need to worry about this at all.  Customizing it is done by means of a file stored in /boot/grub/menu.lst

The grub program is (usually) installed into the master boot record.  This program contains a reference to where on which partition to find its menu.lst file.  After it has been "overwritten" it will use the menu.lst file in your new Ubuntu installation, unless you deliberately create a /boot file system, which you can share between Ubuntu installations.  This will have advantages and disadvantages.  Note:  This may not be true for Vista.  I know nothing about Vista.

2. Yes.

3. Yes.

/home is where your user directories are kept.  Sharing it between installations will go a long way to having your desktop environment kept in sync between the different operating systems.

There is some risk that programs, which keep their user profiles/preferences in your home directory, may have different versions running in the different Ubuntu installations, and these can sometimes have conflicting/incompatible ways of using config files.  This will however affect only the individal affected program.

I recommend sharing /home.  However there is one gotcha:  The UIDs (User ID numbers) in your /etc/passwd file must be synchronized between the different Ubuntu installations ... at least for the users who actually do log in and own files and/or directories in the shared file system(s)

[COLOR="Red"]When installing the new Ubuntu version, check the Format column on the manual disk partitioning section.  There will be a K for KEEP next to partitions which are not to be formatted.[/COLOR]

4. This is one very good reason why you would want to have Grub get re-installed during the upgrade.  With a "new" grub, you can just delete the old installations without worrying about them.  In this situation, to uninstall the old release, you simply remove it's entry from the /boot/grub/menu.lst file and reformat the file systems which are specific to it.  Obviously you will not reformat any shared file systems.

I noticed that you do not have a dedicated swap partition.  If you had one, it could be perfectly shared between the instalations

/var can also be shared.

/ and /usr and /opt can not easily be shared, at least not in their entirety - these contain many libraries and program files and are version-sensitive.

Good luck!

---

