---
title: "First Ubuntu install--disk selection quirk"
date: 2017-04-22
forum: Installation &amp; Upgrades
---

### Post by vineyridge on 2017-04-22
This is my first actual try to install Ubuntu 16.04.LTS.  I've downloaded it, checked the Checksum and it's okay, burned it to disc, let it download all the updates and 3rd party software, and started the install.  That I have Windows XP, SP3 is recognized, and I am asked if I want to install Ubuntu as an OS option with XP.  I do.  I'm not terribly computer savvy, so installation is rather nerve wracking.

When I click the "with XP" option, I am taken to a page that shows only one of my four HDDs. It will show no others or nor does it allow me to change to another drive AFAIK.  The Ubuntu chosen drive is my external 1T drive, and I do not want to install to it.  I want to install to a partition on either my 250G C drive with 25 used Gs or my 450G D drive that has only 800 used MBs.  I'd prefer to install to the D drive, but save the 800 MBs, which means a partition.

I have Windows partitioning software and can easily create a new partition on either drive.  But do I need to do that?  How can I make Ubuntu install to a new partition on either the C or D drive?  I WILL NOT install it to my external drive.  I can disconnect the external drives and see which internal drive the installer chooses, or I can use the Other option on the install page.  Problem is that I have no idea how to use the Other option.

Can someone walk me through this?  (I've already looked at the installation instructions, and it doesn't seem to answer my question.

I've aborted the install to ask this question first.

---

### Post by Dennis N on 2017-04-22
If you need to modify any Windows partitions (like shrink them), it's recommended to do this first using Windows tools before booting the Ubuntu live media.

After starting Ubuntu live session and before starting the installer, I would use gparted (partition editor for Linux included on the live media) to prepare the location you have in mind with an ext4 partition. Don't use Windows tools to make the partiton.
 
Then start the installer. You can now select the partition to use for Ubuntu installation if you choose "Something Else" at the Installation Type screen.
On the next screen, Select the desired partition in the display, click "Change" and fill in the details requested.

Install can then proceed.

---

### Post by oldfred on 2017-04-22
Have you used all 4 primary partitions allowed with MBR(msdos) partitioning?
Do not use Windows to create more as it converts to dynamic from basic which is not compatible with Linux.
You have to convert one primary to an extended and then can have as many logical partitions as you want.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by vineyridge on 2017-04-22
My windows is XP,SP3 so I don't think I have UEFI.

ACK!  This is getting very complicated.  I do have 4 primary partitions in Windows.  

What I have done and can easily undo was to split my D drive into a 30G D drive and that also gave me a J partition with 440 G.  Then I deleted the J partition, which means that I now have 440G of "unallocated space", along with the 30G D drive on my sb2 physical drive.  Now I plan to back up my system drive (C), go to the Ubuntu Live session, and run gparted to create a partition just for Linux.  

 I have a separate external HD just for backups.  Can I use that for my Windows system backup instead of DVD backup?  

My partition software gives me the option to make a "Windows To Go" Media as well as a Bootable Disk.  I already have a Windows Rescue Media from my backup software on a flash drive, but it's old.  Should I create a new one?

Do I need to backup my 1T external drive, which is not my backup external drive.

Will that work?  

I'm sorry: I'm stupid.


I only install operating systems about once every five years or so, so everything I learned from before is long forgotten.  

Oh,  I have another question.  I have an ASUS motherboard with built-in  audio and video, but I have an NVIDIA GT 610 video card.  In the Live  session, I discovered that my video seems to work but the audio  doesn't.  I also have a pair of cheap Logitech laptop speakers for my  speakers, but my ASUS monitor also has speakers and there was no sound  at all.  How can I ensure that I have audio in the Ubuntu install?

---

### Post by oldfred on 2017-04-22
I am concerned if you used Windows tools to create partitions.
Did it change from basic to dynamic?

Always best to have good backups. But XP is obsolete.

You may need the nVidia driver to get sound to work or easily work.
But you can only install that from Ubuntu repository after install.

---

### Post by vineyridge on 2017-04-24
Well, I managed to get the partition thing sorted out with the unallocated space and gparted.   The installation took more than 5 hours with all the Hughesnet downloading that was required. I couldn't download much from the app store because I'm afraid I might have used up my data allowance on Hughesnet.  I've still got Windows and am dual booting.

Now I have questions about finding software comparable to my Windows software, i.e a good firewall, something equivalent to chkdsk, a cleaner like CCleaner, and a defragger (if the last two are needed).   

The interface is confusing because it's so unlike what I've been used to for twenty years.  Where would I find tutorials?

---

### Post by oldfred on 2017-04-24
With Windows I always had a firewall, with Linux I do not, and rely just on router.
You use fsck if you have used the ext2, ext3 or ext4 family of formats. Linux supports many others. But you cannot run chkdsk from Linux. If you keep a NTFS partition you need Windows or a Windows repair CD/flash drive.
see from terminal, q to exit
man fsck
man e2fsck

No defrag required. 
I do some housecleaning on occasion.

       [https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)
Do yourself a favor and avoid bleachbit. 
   Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) 
   RecoverLostDiskSpace
[URL="https://help.ubuntu.com/community/RecoverLostDiskSpace"]https://help.ubuntu.com/community/RecoverLostDiskSpace
[/URL]
 HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

 Caution deborphan will delete anything you manually installed. See comment: 
 Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)[URL="https://help.ubuntu.com/community/RecoverLostDiskSpace"]
[/URL]

---

### Post by vineyridge on 2017-04-24
This is very useful.  Thank you.  I shall read all the links very carefully.  

I'm still a cave dweller when computer stuff is concerned.  I don't use a wireless phone except in emergencies.  Everything that I have is direct wired;  I don't own a router.  What I am is very concerned about interception of wireless communications.  So no router.

I will be very unhappy connected to the internet with no firewall of any kind.

The reason for disk cleaning after every internet session is to be as sure as possible that I have no lurking bits of software that report to outsiders on what my computer does and where it has been.  Cookies are only one of many.  Because of this obsession, I'd like to make my ubuntu as secure as is reasonably possible for a non-computer person.  I have my Firefox set up for maximum security, but it seems that Chromium still has links to Google, a company that I despise and refuse to use unless I go through ixquick.  In fact, I was concerned when I did not find much private browsing available on the ubuntu version of Firefox.  

So I will be really uncomfortable without a firewall.  

What I think I will do is close this thread with problem solved, go to another forum (new to?) and ask how to make my computer as private as possible within Ubuntu.

Thank you all for your help.  At least I now have a working ubuntu on my computer.

---

### Post by yancek on 2017-04-24
The link below is to the Ubuntu Manual which you can download.

[https://ubuntu-manual.org/](https://ubuntu-manual.org/)

The online "Getting Started" Manual at the link below.

[http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/16.04/en_US/screen/Getting%20Started%20with%20Ubuntu%2016.04.pdf](http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/16.04/en_US/screen/Getting%20Started%20with%20Ubuntu%2016.04.pdf)

---

