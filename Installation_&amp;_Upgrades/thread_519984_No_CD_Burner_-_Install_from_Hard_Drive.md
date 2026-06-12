---
title: "No CD Burner - Install from Hard Drive"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by wegoulet on 2007-08-07
I no longer have a CD Burner that works but I want to install ubuntu 7.04

I have successfully d/l 'Feisty Fawn' and the checksum matches what is on 
the web site.

History

hda = 50+ gb divided into three partitions

	1.) HTFS partition is hidden and contains the core HP installation of 
	Windows XP, etc.
	
	2.) Second partition is NTFS and contains my c:\windows and all 
	other programs, etc.
	
	3.) Third partition is NTFS and contains my archive files plus email,
	dowloads, etc.
	
hdb = 9+ gb (I called it NewOS)

	I reserved the entire hard drive for ubuntu.
	
	It is currently formated NTFS but want to install ext3 for linux so that
	I can get the elongated file structure.
	
Being unable to burn image to CD leaves me with the desire to expand the image 
to my archives partition and install ubuntu to hdb.

Can this be done?

If yes, how can it be accomplished?

If no, then I will wait the six to ten weeks for the install CD and go from there.

---

### Post by logos34 on 2007-08-07
Here's your solution:
[https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%2Ffromwindows%29](https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%2Ffromwindows%29)

You can use either the netboot approach or download the [URL="http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso"]alternate install .iso.
[/URL]
> "Note: If you can't/don't want to burn a cd you can also mount the iso with a program like Daemon Tools or Alcohol 120%"

---

### Post by wegoulet on 2007-08-07
I should have been more specific in the original post.

I downloaded the alternate-install.iso

I can't burn the image to CD because my burner is broke. It won't right!

---

### Post by logos34 on 2007-08-07
You don't need to burn it to CD--read my post above.  Read the link I gave you.

---

