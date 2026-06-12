---
title: "[Ask] Dual-boot Ubuntu 12.10 with Linux Mint 13"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by crazyg4merz on 2012-10-28
I know this question has been asked so many times, but I don't know what should I do in my case with those tutorials available everywhere. This is how my current situation looks like:
Right now I'm using Linux Mint 13 Xfce installed with:
1. 500MB of /boot
2. 2GB of swap
3. 15GB of /
4. The rest of my space is /home with no space left in my hard drive

And I just got a Ubuntu 12.10 live CD from my friend, and I intended to install it alongside my Linux Mint. And I want to select something else in the installation process.
The question is:
1. I want to use the same /home partition for Ubuntu and Linux Mint with same user but different directory because I don't want my configuration files conflict with each other. For example my username is Budiman and I want a directory named /home/budiman-Ubuntu for Ubuntu and /home/budiman-LinuxMint for Linux Mint. How can I do that?
2. I read it somewhere said that I can share /boot and swap with multiple Distro, is it true?
3. How can I make another /root directory for Ubuntu since I don't have any space left in my hard drive? Can I resize the /home partition without losing my data? How can I do that if it's possible? Now I've used 10-20% of my /home partition.

I really hope somebody can help me with my question, if possible with a full tutorial starting from install with something else step until completion of the process. Thanks before :)

---

### Post by oldfred on 2012-10-28
Welcome to the forum.

Cannot exactly customize for your exact configuration.

I prefer to share data and not /home when using multiple installs. So I use oldfred and the same PW on all my home desktop installs. The only way I know the have two separate /home folders is to have separate logins. Login & /home folder name have to match as far as I know.

You can share swap if not hibernating nor have encryption. You cannot share /boot and for most desktops a separate partition for /boot is not required. Some systems do seem to have BIOS issues or grub has a bug with large / (root) partitions and then a separate /boot may be required.

Use gparted from liveCD, swap off may be necessary on swap & shrink /home. Is /home inside an extended partition or not. If not you may have to move partitions around as you will probably only be able to create more partitions inside an extended partition as logicals.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

---

### Post by crazyg4merz on 2012-10-28
Thanks for the answers :-) 
But I don't understand the links u have provided. Sorry I'm a newbie in Linux.

Does that mean all I have to do is installing my ubuntu with different username solve all my problem? Can I change my username again after installation?

So I have to make another /boot partition for ubuntu? Can I just shrink my linuxmint's /boot to half and mount that half as /boot for ubuntu?

I'll try that gparted stuffs later and will report again here :-)

---

### Post by oldfred on 2012-10-28
You cannot share /boot, files will overwrite each other and then you will have all sorts of version issues. Either leave /boot inside / or create a new separate /boot.

Same with /home. You can share the /home if you have different user names. But I find it a lot easier just to leave /home inside / and have all data in a separate data partition.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by crazyg4merz on 2012-10-29
Sorry, but your answers are too confusing for a newbie like me. Can u please show me step by step? I decided to install ubuntu with different /boot partition and same /home partition but different directory for each distro. Something like /home/linuxmint/budiman for linuxmint and /home/ubuntu/budiman for ubuntu. What should I do to firstly move my home directory to /home/linuxmint/budiman first on linuxmint before installing ubuntu. Then I will install ubuntu, set my username with budiman, then I will move my /home directory to /home/ubuntu/budiman again the same way I did with linuxmint. Please show me written here and not with link from other question because they are too confusing for newbie like me as they have different questions. Sorry for being too newbie to understand your too advanced answers. :-(

---

### Post by oldfred on 2012-10-29
But what you want will not work. 

You cannot use the same userid for two systems and keep them separate. Some have used the same /home and claim it works but you will get conflicts. Either use two separate /home or install with /home inside your root.

If you want to use same partition just use two different userids.

---

### Post by crazyg4merz on 2012-10-29
Okay then, I think I'll just use another username then.
But what if I use the answer mentioned here to change my home directory?
[http://superuser.com/questions/40450/how-does-one-change-users-home-directory-in-ubuntu-9-04]("http://superuser.com/questions/40450/how-does-one-change-users-home-directory-in-ubuntu-9-04")
Answer from David doing this command: "sudo usermod -d /path/to/new/home -m" will it work if I use it like "sudo usermod -d /home/linuxmint/budiman -m?"
Thanks for helping me so patiently :-)

---

### Post by mastablasta on 2012-10-29
probably but you will get conflicts.
 
what is the purpose of installing both systems? if you want mint desktop you could install just that.
 
dual booting is not basic, it requires advanced knowledge.

---

### Post by crazyg4merz on 2012-10-29
@mastabrasta Where will it be conflicts? What I know from searching everywhere said that conflicts will happen if I use the same home partition with same user because the configuration files of different version apps. But I intended to make the folder of each distro different. Will I also get conflicts?
I know the main difference of that two distros are only the desktop launcher, but I just want to try the newest ubuntu version and make it cooler and learning things :-)

---

### Post by crazyg4merz on 2012-10-29
Problems solved. I installed ubuntu with only /boot and /root partitions and use my desired same username. Thanks for your help guys. Although I didn't get my desired answer but I really appreciate your replies. Mod can now close this thread and I'll change the header to solved :-)

---

