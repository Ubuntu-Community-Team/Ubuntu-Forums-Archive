---
title: "Install Always Fails"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by blokus2006 on 2006-06-04
I have a mac mini with OS X 10.4.6 installed on the hard drive inside the mini. The mac mini is power pc based.

I am trying to install ubuntu 6.06 from the live cd on an empty external 250GB external hard drive. Every time i try to install I either get the error that it cant create a file system or it says it failed to install the boot loader. Can anyone please help?

---

### Post by blokus2006 on 2006-06-04
Please help me!!!!!!

Im dying for help!!!!!!!!

---

### Post by blokus2006 on 2006-06-04
Help me please!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by llamakc on 2006-06-04
Run GParted first.

---

### Post by blokus2006 on 2006-06-04
[QUOTE=llamakc]Run GParted first.[/QUOTE]
Is that the program to make the partition?

---

### Post by llamakc on 2006-06-04
Description: partition editor for GNOME
 It is a graphical editor which uses libparted to detect and manipulate
 devices and partition tables while several (optional) filesystem tools
 provide support for filesystems not included in libparted. These optional
 packages will be detected at runtime.
 It currently supports ext2, ext3, Reiser3, FAT, NTFS, XFS, JFS, HFS and
 Linux swap.

---

### Post by blokus2006 on 2006-06-04
Do i make a swap partition and a normal one?
It wont let me because "it says at least on operation was applied to a busy device"
What should i do?

---

### Post by llamakc on 2006-06-04
Are you following the Ubuntu-Mac install howto?

---

### Post by blokus2006 on 2006-06-04
Where is that? Can you please send me a link to it?

---

### Post by llamakc on 2006-06-04
[https://wiki.ubuntu.com/Installation/PowerPC](https://wiki.ubuntu.com/Installation/PowerPC)

This is a PPC mini, right?

---

### Post by blokus2006 on 2006-06-04
[QUOTE=llamakc]Are you following the Ubuntu-Mac install howto?[/QUOTE]
yes it is

---

### Post by llamakc on 2006-06-04
Good luck. Keep us posted.

---

### Post by blokus2006 on 2006-06-04
Ok. I chose the drive i wanted to install on (my external drive). I then chose to erase the whole disk and to install, just like the guide said. When it starts to install, it fails at 5% and says that it failed to create a file system.

What should I do?

---

### Post by blokus2006 on 2006-06-05
Please help me!!!!!!

---

### Post by blokus2006 on 2006-06-05
[QUOTE=blokus2006]Ok. I chose the drive i wanted to install on (my external drive). I then chose to erase the whole disk and to install, just like the guide said. When it starts to install, it fails at 5% and says that it failed to create a file system.

What should I do?[/QUOTE]



Why isn't anyone helping me!!!!!!

](*,)

---

### Post by llamakc on 2006-06-05
You should give more information and less exclamation points.

Refresh our memory: is this an external HD, how is it connected? Is it currently partitioned or formatted, and if so, with what scheme/filesystems?

Have you looked in the PPC forum here for installing to an external drive? Do you intend to continue booting into OSX?

You could easily just boot the LiveCD and use fdisk on the external drive, and after that create your ext3 partition. Now, the installer won't goof up.

Frankly, sounds like you want to use the alternate install CD.

When it is failing on you, you can use the key-combo ctrl-alt-F2 or ctrl-alt-F3 to see the output on the terminal. Some of that information may be useful.

Also, I forget if you have to hold down Open-Mac key when doing that key combo on PPC. You may have to do that.

Lastly, this IS a FireWire external drive, right?

A search of the forums brought this:

[http://ubuntuforums.org/showthread.php?t=132444&highlight=ppc+install+external](http://ubuntuforums.org/showthread.php?t=132444&highlight=ppc+install+external)

Is there any reason you don't want to install to the HD inside the Mini?

---

### Post by llamakc on 2006-06-05
[quote=blokus2006]Why isn't anyone helping me!!!!!!

](*,)[/quote]

Nobody here is required to help you at all. We're volunteering. You can help yourself by having patience.

---

### Post by blokus2006 on 2006-06-05
It is an external drive connected by USB. I did not partition the drive at all because I just want Ubuntu on the whole disk. 

I intend to have a choice to either boot into OS X or into Ubuntu.

I am using the desktop install CD.

I don't want to install onto the drive inside the mini because i intend to leave OS X there.

---

### Post by llamakc on 2006-06-05
[http://www.ubuntuforums.org/showthread.php?p=498516](http://www.ubuntuforums.org/showthread.php?p=498516)

Looks like a lot of work. Too bad you didn't get a FireWire drive.

If you would read the PPC Howto you could easily have them on the same disk inside the mini.

Personally I would boot back into OSX, format the external drive to HFS+, drag all of my important stuff (documents, songs, video, pics, whatever) over to the external. 

Next I would REINSTALL OSX but this tiime follow the howtos for dual booting OSX & any Debian-based Linux.

Now you'll have no problems with the installer and all of your goodies will be safe on the external.

Other than that, I can be of no more help to you. Sorry.

---

### Post by blokus2006 on 2006-06-05
The installer won't goof up at all right?


And can you help me find a guide for dual booting os x and ubuntu on the same drive?

---

### Post by llamakc on 2006-06-05
No offense but the goofs are more likely to be from rushing through the directions.

I'm not prepared to give you a step-by-step on how to do this. Find the appropriate howto's on the Net for dual booting OSX and Ubuntu.

Caveat Emptor from there.

---

### Post by llamakc on 2006-06-05
[http://www.philroche.net/archives/osx-and-ubuntu-dual-boot/](http://www.philroche.net/archives/osx-and-ubuntu-dual-boot/)

See? A simple google gave up the goods. Good luck and good night.

---

