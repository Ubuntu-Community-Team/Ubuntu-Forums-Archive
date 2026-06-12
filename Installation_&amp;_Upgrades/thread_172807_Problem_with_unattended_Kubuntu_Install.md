---
title: "Problem with unattended Kubuntu Install"
date: 2006-05-09
forum: Installation &amp; Upgrades
---

### Post by Alatariel on 2006-05-09
Hello community,

first thing: I'm new to (k)ubuntu and I've never used Debian. So many things about the installation routines have been new to me and maybe I miss sth very simple :-)

At school we started a project. We have to create an unattended WinXP and an unattend Linux Setup.

Because of Gentoo's very long compile times and because wie don't like SuSe (especially Yast) we have chosen Kubuntu (Breezy 5.10).

First we did with a Kickstart config (works great) but as we tried to script in some additional packages, we've had problems with the network connection.
After that we came to a preseed File.

We created one, changed isolinux.cfg, put the preseed file on the cd and created a new md5sum.txt
After creating a new iso and burning it all on CD we tried to boot up the system. So far, no bigger problems:

But now we get an error after CD detection:

```
hw-detect: Missing modules 'ide-mod (Linux IDE driver), ide-probe (Linux IDE probe driver), ide-detect (Linux IDE detection)
cdrom-detect: Searching for Ubuntu installation media...
cdrom-detect: CDROM-mount succeeded: device=/dev/cdroms/cdrom0
cdrom-detect: The available CD ist not a Ubuntu CD!
```

After that install simply stops.

What have I forgotten? Can some of you guys please help me? :-)

Used sources:
[CustomizationHowTo](https://wiki.ubuntu.com/InstallCDCustomizationHowTo)
[Preseeding](ftp://ftp.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/apcs01.htm)l
[Partman Docs](http://d-i.alioth.debian.org/svn/debian-installer/installer/doc/devel/partman-auto-recipe.txt)
[My Preseed File](http://alatariel.gmxhome.de/extras.seed)

---

### Post by Alatariel on 2006-05-14
*bump*

Anything unclear?
Or does simply nobody know, how I correctly remaster this installation CD? :-)

---

### Post by jonoinsa on 2006-05-26
Experienced the same problem as you:

on [http://syslinux.zytor.com/iso.php](http://syslinux.zytor.com/iso.php) it says:

How Can I Make a Bootable CD With ISOLINUX? }

    Make sure you have a recent enough version of mkisofs. I recommend mkisofs 1.13 (distributed with cdrecord 1.9), but 1.12 might work as well (not tested.)

    To create an image, create a directory called "isolinux" (or, if you prefer, "boot/isolinux") underneath the root directory of your ISO image master file tree. Copy isolinux.bin, a config file called "isolinux.cfg" (see syslinux.doc for details on the configuration file), and all necessary files (kernels, initrd, display files, etc.) into this directory, then use the following command to create your ISO image (add additional options as appropriate, such as -J or -R):

        mkisofs -o output.iso \
           -b isolinux/isolinux.bin -c isolinux/boot.cat \
           -no-emul-boot -boot-load-size 4 -boot-info-table \
           root-of-iso-tree

    (If you named the directory boot/isolinux that should of course be -b boot/isolinux/isolinux.bin -c boot/isolinux/boot.cat.)

    ISOLINUX resolves pathnames the following way:

        * A pathname consists of names separated by slashes, Unix-style.
        * A leading slash means it searches from the root directory; otherwise the search is from the isolinux directory (think of this as the "current directory".)
        * . and .. in pathname searches are not supported.
        * The maximum length of any pathname is 255 characters. 

    Note that ISOLINUX only uses the "plain" ISO 9660 filenames, i.e. it does not support Rock Ridge or Joliet filenames. It can still be used on a disk which uses Rock Ridge and/or Joliet extensions, of course. Under Linux, you can verify the plain filenames by mounting with the "-o norock,nojoliet" option to the mount command. Note, however, that ISOLINUX does support "long" (level 2) ISO 9660 plain filenames, so if compatibility with short-names-only operating systems like MS-DOS is not an issue, you can use the "-l" or "-iso-level 2" option to mkisofs to generate long (up to 31 characters) plain filenames.

    ISOLINUX does not support discontiguous files, interleaved mode, or logical block and sector sizes other than 2048. This should normally not be a problem.

    ISOLINUX is by default built in two versions, one version with extra debugging messages enabled. If you are having problems with ISOLINUX, I would greatly appreciate if you could try out the debugging version (isolinux-debug.bin) and let me know what it reports.

    NOTE: ISOLINUX will search for the config file directory in the order /boot/isolinux, /isolinux, /. The first directory that exists is used, even if it contains no files. Therefore, please make sure that these directories don't exist if you don't want ISOLINUX to use them. 

My working solution:

pwd: rsynced files off my install cd to here:

/home/jonathan/Desktop/UbuntuAltered

ls -ltr
total 1259584
dr-xr-xr-x   19 root  wheel           646 May 25 14:17 LXFCD74a

changed isolinux.cfg file and added a seed file.

Then did:

sudo mkisofs -v -r -iso-level 3 -ldots -o my-ubuntu2.iso -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table LXFCD74a/.

After that my cd worked :)

HTH.

Jono

---

### Post by Alatariel on 2006-05-27
Many thanks :-)

Seems to be one forgotten mkisofs option. You use some other, than those given in the wiki.

It works fine now.

---

### Post by jonoinsa on 2006-05-29
Kewl, glad it worked :)

---

