---
title: "Lost boot up"
date: 2013-08-07
forum: Installation &amp; Upgrades
---

### Post by Berry Greene on 2013-08-07
Hello. I have been operating a very succesful UBUNTU/Windows dual boot  system on which UBUNTU has now failed. The UBUNTU boot goes a fair way but will  not complete. There is a 50Gb partition for UBUNTU and 200Gb partition  for Windows XP - which still runs OK.
I think I need to re-instal but get scared off at the point where "No  root file system defined - correct this from partitioning menu" appears.  Yes I have a live disc and the installation can be started after booting  with it.
I am getting very scared of ruining my Windows installation. It's not  just a question of backing up the data, which I have done. Some of the programs are an  absolute pain to re-install if Windows has to be re-loaded. Can you  please help me?

Extra info:- The UBUNTU OS starts to boot up after selection in the  dual-boot menu and many pages of information scroll on the screen. However, it  always freezes at the same point seemingly waiting for something. I have  tried all the options in the recovery menu but same result.
I would much prefer to just replace the current installation.  However, I must be missing something as I don't see that route on offer. How do I do that? As  an aside - and believe me I don't want to complicate things anymore  than they are already, - I never did have a swap partition for UBUNTU.  Perhaps I should find that original version disc...? At the moment I have here a  version 10.10 live disc that I've been using. Is that OK or should I  download the very latest version and make me an ISO (live) disc to boot  from?[IMG]http://ubuntuforums.org/images/icons/icon5.png[/IMG]

Regards, Berry Greene

---

### Post by ubfan1 on 2013-08-07
You definitely need a more current release -- Ubuntu 12.04.2 for long term support (soon 12.04.3 Oct.?).  I'd suggest a swap partition to allow better handling of high memory conditions -- the problem is if you already have 4 primary partitions (the max for msdos partition type).  Then you'd need to backup the Ubuntu partition, delete it, make an extended partition with the space, and then add logical parititions for swap and root.  There might be an issue if your Windows partition is after the extended partition, not sure.

---

### Post by grahammechanical on 2013-08-07
Ubuntu 10.10 reached End of Life sometime around May 2012. If you are going to re-install you should use the latest Long Term Support release (12.04.02 LTS). There is still about 4 years support left for it.

Run the live session and select Install Ubuntu and you will be given options. Select Something Else. Do not select Erase the entire disk or Install alongside. 

You will come to a partitioning screen. You need to identify the partition that Ubuntu is on. Select that partition and click on Change.

In the next dialog box you need to select a file system. So, in the drop down menu of Use As change Do not Use to Ext4. You do not need to change the partition size. You may get a message about it taking some to to change the partition size. And worry about it as I do because you have not changed the partition size. So, ignore that message. I do.

Do not tick the Format box unless you have backed up all your data. In fact back up your data before you start this.

You now need to define a file system or set a mount point for the installation. There is a drop down menu. Select mount point /   That is it. You have now defined a file system and the installation can proceed. So long as you do not go anywhere near any of the Windows partitions you will not mess them up.

This guide is for an old version of Ubuntu but it does have images of the Installation Type sceen where we select a partition and click the change button and also the dialog box that then appears. The image is out of date but notice the Use As and the Mount Point panels. From the drop down menus select Ext4 and / as shown in the picture.

[http://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=5&ved=0CE0QFjAE&url=http%3A%2F%2Fwww.techspot.com%2Fcommunity%2Ftopics%2Fstep-by-step-beginners-guide-to-installing-ubuntu-11-10.172128%2F&ei=tXYCUuL7FonW0QWItoCYBA&usg=AFQjCNHZOZxNCGayoB8JoSM_yhNfx25cLQ&bvm=bv.50310824,d.d2k](http://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=5&ved=0CE0QFjAE&url=http%3A%2F%2Fwww.techspot.com%2Fcommunity%2Ftopics%2Fstep-by-step-beginners-guide-to-installing-ubuntu-11-10.172128%2F&ei=tXYCUuL7FonW0QWItoCYBA&usg=AFQjCNHZOZxNCGayoB8JoSM_yhNfx25cLQ&bvm=bv.50310824,d.d2k)

Regards.

---

### Post by Berry Greene on 2013-08-09
Thanks so much for all that trouble sir! I have downloaded 12.04.2 and made ISO disc OK. Will follow the procedure as outlined.

---

### Post by Berry Greene on 2013-08-09
Hello grahammechanical.

Well I did all you said having got up very early so to do. All went well but installation did not complete. "Busy" wheel displayed for over 30m and in the end I considered it stuck. Fortunately Windows booted OK but now cannot see the Ext4 filesystem and does not report the partition like it used to. I wondered if the installation needs that swap partition, (it does warn you it might), and so I set to try and find how I do that. Can't!! Spent next 3hrs trying - looking up my notes, scanning the internet. Now I'm done with it for the moment. 
Except to say this:- Somewhat as an aside when I load the UBUNTU live disc it all boots up OK but I cannot close it down or restart the PC - unless I re-power the lot! It stays until then demanding sign in details of Username & Password that I have never given to this distro and don't know anyway!
So just to finish - how long should a typical installation take? --- AND what is meant by a PRIMARY Partition?
I thank you for your knowledge & forbearance for which we usually say "Ta!" 
Berry G

---

### Post by ubfan1 on 2013-08-09
Normally, a hard disk installation takes about 20-40 minutes, with slide shows and progress bars, so you see what's happening.  A primary partition is one of only four allowed in the msdos type of partitioning.  If you need more partitions, you need to make one of the primary partitions an extended partition, into which you can then add Logical partitions (many of them allowed, 128?).  The gotcha is when you already have 4 primaries in use.  You can shrink one, but then you cannot make another partition with the free space!   Just a messy process -- backup the shrunk partition, delete it, add an extended partition with all the free space, add a (shrunk) logical to hold the original stuff, then add logicals for swap, root, etc in the remaining free space.

---

