---
title: "Clone installation before upgrade"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by coady on 2007-04-23
Before I upgrade Ubuntu from Edgy to Feisty I want to clone the current installation to a new partition. If anything goes wrong with the upgrade I will still have a bootable version of Edgy on separate partition. Why not just install Feisty to an empty partition and keep the existing installation of Edgy? I have a terrible chipset with integrated video drive (VIA Technologies VM800 which requires the UniChrome Pro IGP driver) which is not supported by Ubuntu and I don't really want to have to rebuild the drivers and edit the config files. Also, the cloning strategy has other uses in the long run.

 Here is the situation:
(1) I have a spare partition formatted to ext3.
(2) I have separate partitions for '/data' and '/home'
(3) I use 'tar' to do regular (incremental) backup dumps to an external hard drive, keeping all permissions intact, and excluding '/sys', '/proc', etc., and create a bzip compressed archive.

The question is what steps do I need to take to clone the existing installation of Edgy to bootable state on the empty partition?

My best guess is:
(1) Extract an archive (containing a full copy of my current Edgy installation) to the spare partition.
(2) Boot with a LiveCD (e.g. Knoppix) and edit the '/etc/fstab' to point to the correct partitions such as the cloned Edgy partiton, '/data', and '/home'.
(3) Edit any symbolic links that may be broken or pointing to the wrong partition.
(4) Manually edit the '/boot/grub/menu.lst' to add the cloned Edgy partition.
(5) Then reboot and I should be able to choose between the cloned Edgy and the original.

Will this (outlined above) work? Any advice on this would be greatly appreciated. I have used commerical imaging software in the past before moving to Ubuntu, but since I started using Linux I realised I could simply use 'tar', '-dd', or 'rsync' to copy/backup instead of making disk images. Any other alternative strategies for cloning Ubuntu to a spare partition would also be welcome.

Thanks,
coady

---

### Post by zvacet on 2007-04-23
What I´m going to tell you is not clone,but something else.If you have Edgy Cd(in case something going wrong) download APTonCD [http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/") This tool will save all your var/cache/apt/archives and that is place where all your dowloads and updates are.This is solution:if something bad happpened you reinstall Edgy and with aptoncd put all yours updates and downloads you made with synaptic or apt-get back in  var/cache/apt/archives.This is just an option.

---

### Post by coady on 2007-04-24
Thanks for the reply. I am aware of 'APTonCD' (which is an excellent suggestion :) ), and I also use the command ```
~$ dpkg --get-selections > 'filename.list'
``` It is then possible to use "cat" to import all the packages in the list, the difference being that one would need an internet connection rather than having the packages locally.

However, I would still like to know if my outline of cloning Edgy (in my earlier post) would, in principle, work?

Thanks again,
coady

---

### Post by coady on 2007-05-03
I can now confirm that the method outlined at the top of this thread works without any trouble. I used 'tar' to copy/clone my existing Ubuntu 6.10 installation from one partition to another partition (exactly the same size) on the same laptop. All that needs to be done when the archive is extracted is to recreate the folders that where excluded, and to edit the '/etc/fstab' and add some new lines to the existing '/boot/grub/menu.lst'. The big advantage of this method for backing up, copying, or cloning, is the availabililty of incremental backups. I have not tried this method for cloning an installation to different hardware, or computer. I can also confirm that 'dd' works to clone the same Ubuntu installation, but I have not tested this as extensively as the 'tar' method.

---

### Post by psusi on 2007-05-03
Yep, you got it all right... except the need for a livecd.  Your original post said you would edit fstab from a livecd, but there is no need... just edit it after you untar it.  

As for dd, you don't want to use that unless the source and destination partitions are exactly the same size.  If the destination is smaller, you won't copy the whole thing and will clobber the partition.  If the destination is larger, you waste the extra space.

---

### Post by coady on 2007-05-04
Yes, thanks. You are right about the LiveCD (just a habit I guess). Also, with 'dd' there is a way to copy to partitions of different sizes, but it is a bit more complex and while 'dd' is extremely powerful there is also plenty of room to make disastrous mistakes when unfamiliar with the commands. Check out this [_[COLOR="Blue"]link[/COLOR]_]("http://www.linuxquestions.org/questions/showthread.php?t=362506") for an excellent summary of the 'dd' command. The simple option is probably to use 'PartImage', but using 'tar' and 'dd' is particularly useful in enabling new linux users to learn about linux and experiement without blowing away your whole OS (that is unless you mess up a command and delete your good OS, and then ask yourself why you never tested your backup procedure... yes, we have all done such 'bone head' things.)

coady

---

### Post by Jose Catre-Vandis on 2007-05-04
I use Partimage to perform this function, which again just requires an fstab edit after restoring the image to a new partition. Download a copy of SystemRescueCD. There is a good howto on the forum on what to do. Though I do like your approach :-)

---

### Post by coady on 2007-05-04
Actually, sometime ago I had problems getting the SystemRescueCD (a much earlier release than current) to boot on my system. I am  rather a strong supporter of Knoppix and the most recent releases have a version of Partimage, but it should not make a difference I guess.
coady

---

