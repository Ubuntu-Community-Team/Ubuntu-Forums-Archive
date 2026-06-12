---
title: "Installing Ubuntu 6.10 Edgy on pre-partitioned drive"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by iHateWindows on 2007-03-12
This is the first time I've attempted to use Ubuntu.  Here's what I've got going on.  I just dropped a 250Gb HD into the Compaq in my signature as a companion to the 30Gb HD it already had.  I used System Rescue CD and GPartEd.  I created an extended partition with 15 logical partitions inside (after finding out that PCLinuxOS, openSuSE, Fedora and Ubuntu want 3 partitions each).  I have 3 partitions set aside for Ubuntu: 2Gb, 20Gb, and 25Gb.  The 2Gb will be the swap, 20Gb will be for / (root), and 25Gb for /home.  I get into the installation to the point where it wants me to assign the partitions for Ubuntu (I choose manual partitioning) and when I assign those 3 partitions, it tells me that I have no root partition.  I have even gone so far as assigning a partition for each of the various mount points (/var, /usr, etc), but it still kicks it back at me saying that I have no root partition.  I plan on installing Xandros on the primary partition on the 30Gb drive.

At this point, I have successfully installed PCLinuxOS, openSuSE, and Fedora.  Still working on Sabayon, and I plan on installing Xandros last.  I'm hoping that Xandros will detect all the other installs and allow me to update LILO to reflect that.  If not, I am prepared to use GAG on it to get the job done.

Also, if you've suggestions on whether I can use one swap partition for all 6 distros, I'd like to hear it.  I'd also like to know whether you think I should just allow each distro to write its own bootloader (knowing that GRUB and LILO aren't really compatible).  I haven't allowed them to do so thus far figuring that either Xandros' LILO install will either pick up the other 5 installs or I will have to use GAG.

Thanks for taking the time to read this and giving me your suggestions.

---

### Post by Kateikyoushi on 2007-03-12
You do not need 6 swap partitions for 6 linux distros unless you want to hibernate them when you switch to another one, could use the same.

---

### Post by rsambuca on 2007-03-12
Yeah, I just use one swap for everything.

As far as the "no root filesystem", it is an error with the ubuntu ubiquity installer not recognizing pre-existing partitions sometimes.  There is a workaround [[COLOR="Red"]here[/COLOR]]("http://www.ubuntuforums.org/showpost.php?p=1700787&postcount=29")

---

### Post by iHateWindows on 2007-03-12
Thanks for the info.  Now, I'll go back and throw out everything I've done to this point and re-partition the drive.  I've bookmarked the link you gave me so that I don't lose that info, which I am sure I'll need when I next attempt to install Ubuntu.  I'll let you know how it goes, tho.  Thanks again for the help!

---

### Post by iHateWindows on 2007-03-12
Well, that worked great.  I re-partitioned the drive & set up just one 4Gb swap file (figured I might as well be generous since I only have 280Gb to work with) and gave the extra 2Gb to the 25Gb /home partitions for each distro.  I followed the directions in the other post and installing was a snap!  I booted into Ubuntu and played around, made the the taskbars transparent (having 2 is freaky).  I'll mess with it some more later and attempt to find the "Run" command's equivalent in Ubuntu.

I appreciate the help!

---

### Post by Kateikyoushi on 2007-03-13
Applications > system tools > terminal can be used as run.

---

### Post by iHateWindows on 2007-03-17
Just wanted to say "Thanks" to everyone.  I got everything installed and working right and learned a lot of things along the way.  Once I figured out the syntax for telling Ubuntu where to install the bootloader, I was done.  I got 5 Linuxes installed and bootable, but Sabayon will be a no-go for me since it doesn't have a driver for my graphics card (KYRO Prophet 3d 4500).  So, I'll just check that out on this laptop of mine, instead.  That's what I get for picking devices from an obscure manufacturer long ago.  I'm glad that I asked whether each distro needed its own swap file.  That saved me a lot of space!  Plus, I've already been able to pass on some of what I learned on the Xandros forum.

I'm looking forward to when Feisty Fawn is no longer testing and has been declared stable.  I've read some good things around lately and I'm excited to test drive the new version.

So, thank you very, VERY much for all your help.  I'll try to lurk around and help where I can as I learn about Ubuntu.

--------------------------------
Desktop PC
1.0Ghz CPU, 640Mb RAM, 30Gb & 250Gb HDDs
Multi-booting: Xandros, Ubuntu, PCLinuxOS, Fedora, and openSUSE

---

