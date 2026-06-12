---
title: "DVD filenames converted to lowercase"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by SharpBlade on 2008-08-20
Hi there!
I have just installed Ubuntu 8.04 on my laptop (ACER Aspire 1692) which has been running MS Windows XP SP3 until now.  Before doing so, I backed up my data to a RW-DVD simply by copying the files and the directory structure directly to the DVD disk.  Ubuntu runs fine on the laptop but when I wanted to restore the data from the DVD disk, I came across a strange issue: all the filenames are seen in lowercase by Ubuntu (both from Nautilus and from the Linux command line) and accented characters are replaced by a weird character (question mark over a black diamond).  For the filenames containing at least one question mark over a black diamond, it is followed by the text "(invalid encoding)".  When I copied the files from the DVD to the hard disk, then the files on the hd are lowercase and include these strange characters.  I really would like to copy the filenames as they actually are, especially as when I insert the DVD in a machine running Mac OS/X or Windows all the filenames are correct: no weird characters to be seen and the capitalization is true to its original.
Is there a mount option to specify in order to display and copy the filenames accurately? 
Please note that when I import the DVD content into the Brasero DVD burning application (See the attached screenshot), the filenames are correct (right side of the screen) but when I browse the DVD content from Brasero, Nautilus or the command line, they are all in lowercase (left side of the screen).:confused:

It would be great to get some assistance.  Thanks in advance.

---

### Post by SharpBlade on 2008-08-21
I have tried to mount the DVD with the following options but have not been successful in sorting out the issue (all filename characters are converted to lowercase and accented characters are replaced by a question mark on top of a diamond)

(1) sudo mount -o norock,iocharset=utf8 /media/cdrom0/
(2) sudo mount -o iocharset=utf8 /media/cdrom0/
(3) sudo mount -o norock,iocharset=iso8859-15 /media/cdrom0/

Any idea out there to get around this issue?
Brasero is able to import the filenames correctly (see previous post) so there must be some parameter to provide to the mount command to read the directory structure accurately i.e. without lowercasing the filenames.

---

### Post by coffeecat on 2008-08-21
I know little about the details of character encoding, so I can't offer a technical explanation of what's gone wrong, only some practical suggestions.

The fact that Brasero reads your directory structure correctly (er - sometimes), but not Nautilus, suggests this could be a bug/defect in Nautilus, perhaps specifically with the DVD-RW filesystem, because I don't get this when copying files from Windows into an external USB hard drive. There were some bugs (now fixed) introduced into the 2.22 version of Nautilus, so this might be another. If Nautilus misreads the filenames, it's going to mis-copy them onto the HD. And goodness knows what's happening in the terminal.

Try installing one or more of the following alternative file managers and see if they cope any better. Thunar (the xfce file manager, but works in Gnome), Konqueror (kde - ditto) and Gnome-commander.

Alternatively, have you got an external USB drive? You could use the Mac (or even a Windows machine) to copy the files onto a USB drive, and then copy from the USB drive onto Ubuntu.

---

### Post by SharpBlade on 2008-08-21
Coffeecat,

Thanks for your input.  Good idea, I will try to copy from DVD to USB flash drive and then from USB flash drive to HDD.  Hopefully, this will work.

---

### Post by SharpBlade on 2008-08-22
As suggested by coffeecat: on a machine running MS Windows, I copied my files from the DVD to a USB FlashDrive .  Then, I plugged the USB FlashDrive in my laptop running Ubuntu... and all the filenames are now seen correctly by Ubuntu :KS
Until I finally find an actual solution to the problem, this can be workaround.

---

### Post by coffeecat on 2008-08-22
> **SharpBlade said:**
> Until I finally find an actual solution to the problem, this can be workaround.

It's an interesting finding. I don't suppose there are many people archiving to DVD-RW from Windows and then trying to restore into Ubuntu. Perhaps that's why I've never seen it mentioned on these forums before. I don't often boot into Windows, but I've got some spare DVD-RWs, and in a day or so I'll try copying a large directory tree with files using Windows and see what I get when I read the disc with Ubuntu. I've also got Gentoo (gnome), Zenworks (Xfce), Mandriva (KDE) and openSUSE scattered around my machines, so I'll see what I find with other distros/desktops/file-managers. I'll post back.

---

### Post by coffeecat on 2008-08-22
> **SharpBlade said:**
> Hi there!
I have just installed Ubuntu 8.04 on my laptop (ACER Aspire 1692) which has been running MS Windows XP SP3 until now.  Before doing so, I backed up my data to a RW-DVD simply by copying the files and the directory structure directly to the DVD disk.

The plot thickens. It was only when I had booted into Windows that I remembered that XP doesn't have native DVD writing ability - you have to use a third party application. Indeed, when I opened a Naut... er I mean Explorer (:wink:) window it told me solemnly that the DVD-RW I had inserted was a CD-RW. Ho hum.

Anyway - I burnt a whole load of personal data using Nero Express Essentials and chose to leave the session open for later burns. I'm now in Ubuntu and Nautilus is showing folder and filenames as they should be - no confusion between upper and lower case. However, I don't have any accented characters in my filenames so I couldn't test that.

Which leads to a question. What software did you use in Windows to burn the DVD? I wonder if there is a quirk in that which Mac OS can cope with but not Ubuntu.

Curioser and curioser.

---

### Post by SharpBlade on 2008-08-22
Under Ubuntu, I was finally able to get the filenames in mixed cases after mounting the DVD burner with the following command:
sudo mount -o norock,**map=o**,utf8 /media/cdrom

The map option can be assigned the following values, the default being map=normal:
 map=n[ormal] / map=o[ff] / map=a[corn]

So, now I have the filenames in mixed characters as I would expect but:
1) Each filename now terminates with the pair of characters **;1**
2) Accented characters are still replaced by a question mark.

Please note that under Ubuntu when I copied the files -the exact same files which I copied from the DVD to the FlashDisk- from the FlashDisk (FAT volume)to the HD, the following mounting options were automatically used by Ubuntu:
dmask=0077,**codepage=cp437**,iocharset=iso8859-1,shortname=mixed,utf8
But, option codepage is not available for ISO9660 volume and I have the feeling this could be the key to my problem.

Note: On Windows, I burnt the DVD using the pre-installed DVD burning software provided by ACER.  It is called **NTI CD&DVD-Maker**.

coffeecat, thanks again for your time looking into this issue.

---

### Post by cariboo on 2008-08-22
Just a note, linux does not deal at all with spaces and accented characters in the file name, it is window and apple that have to add extra encoding to deal with people that don't enter proper filenames.

Jim

---

### Post by SharpBlade on 2008-08-22
Jim,

When you install Ubuntu, it itself creates directories and files on the hdd whose names include capital letters and spaces e.g. user/Examples/Experience ubuntu.ogg.
I suppose you were only talking about the DVDs.

---

### Post by SharpBlade on 2008-08-25
Piece by piece I copy 6GB of data from my DVDs to a 1GB FlashDisk on a PC running MS Windows, and then from the FlashDisk to the harddisk of the laptop running Ubuntu...:eek:

---

