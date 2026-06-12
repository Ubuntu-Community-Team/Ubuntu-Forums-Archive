---
title: "How to Completely remove Windows and Replace with Ubuntu ???"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by AbangBoltok on 2011-05-10
I currently have Ubuntu on different partition hard drive with Windows 7.
Now I want to Install Ubuntu and replace Windows 7.

my question is, what's the best way to Install Ubuntu and replace Windows 7, and also remove the current Ubuntu OS. so I will only use 1 Ubuntu.?

thanks.

---

### Post by oldfred on 2011-05-10
If you have nothing you want to save the standard install to the full disk will erase everything and just give you / (root) and swap partitions.

But you should back up all your data. Have you made a lot of configuration settings in /home or have data in /home that you want to save? If so be sure to back up /home. If /home is already a separate partition you can reuse it in you new install, but then have to use manual install (Natty calls it something else).

Have you installed a lot of applications and want to easily reinstall those? You can make a list from your current install and reinstall.

Are you 100% sure you do not want windows? We find many who want to reinstall windows as they have that one application they have to have and nothing works for them as well in Linux. 

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by grahammechanical on 2011-05-10
May I put your question a little differently? What is the easiest way to destroy all your documents and data files? Answer: Run a live CD and tell the installer to installed Ubuntu using the entire disc. I think that this answer will give you what you asked for but not what you want. Right?

a1) Backup all your important data.

a2) Delete the Windows 7 partitions. There must surely be more than one. This will create unallocated space.

a3) Expand the Ubuntu partition into the unallocated space. Use the same Ubuntu installation.

b1) Back up your data.

b2) run the live CD and tell the installer program to create a 20Gb partition and give it a mount point of / mark the partition to be formatted as ext3 or ext4. Your choice.

b3) tell the installer to use the rest of the disc as a mount point of /home. Again chose the format.

This will install a fresh Ubuntu installation.

Others may have some more suggestions.

Regards.

---

### Post by underquark on 2011-05-10
Remember when backing up data - it's not just the contents of "My Documents"; it's your e-mails, contacts etc. too.  Also , some people use a password manager or let their browser remember all their passwords for various different sites.  So, copy all your important files, copy your Outlook .pst (or whatever) files, make a list of your passwords (and then eat them, for security reasons).

---

### Post by AbangBoltok on 2011-05-10
thanks guys, I dont need Windows 7. i do more programming stuff for uni.
and in the last 6 months I only use Windows approximately 1-2 hours every week. and I've never updated my windows since then.

@grahammechanical, thanks. really helpful, but i think i have to explain more.
my HDD:
1 - Currently Windows 7 (I want fresh Ubuntu here)
2 - Currently Installed with Ubuntu 10.10
3 - No OS, just storage.

when installing ubuntu, there always a session when the installer scan for the entire HDD to check whether there is another OS installed. in Ubuntu 11.04 installation, if I select "Erase Disk and Install Ubuntu" does it mean that it will format all other HDD or just the HDD that I will choose (HDD with windows7) ?
if it's going to format all HDD's it's good, that's what I want. If it's only formatting 1 HDD, what's the best way to uninstall Ubuntu 10.10 on the other HDD?

thanks.

---

### Post by oldfred on 2011-05-11
It only formats the drive you select to install to, if using the automatic install.

You can use gparted from liveCD to erase or reformat partitions.

I still suggest creating partitions in advance and using manual install. If you have more than one drive it will automatically install grub2's boot loader to the MBR of sda as that is normally what most users boot with.  You also only get / (root) & swap. It is much better to have another partition for /home and keep system partition smaller for efficiency and future reinstalls.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

