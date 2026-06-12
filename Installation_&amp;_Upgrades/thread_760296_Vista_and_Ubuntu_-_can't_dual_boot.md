---
title: "Vista and Ubuntu - can't dual boot"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by vixmusic01 on 2008-04-20
Please help.

Specs for the notebook are:
 
It is a dual-core AMD Turion 64×2 TL-52 803 MHz mobile technology chip (AMD K8 Processor), 32 bit operating system, ACPI mother board, NVIDIA GeForce Go 6100, 120 gig HD, bluetooth, SD card reader and DVD burner.

THe copy of Vista I have is a recovery disk from Asus.

If I install Ubuntu Vista does not boot.

If I install Vista it over rides everything and the notebook cannot load Grub. .

Complete story on my blog:

[http://livemorelightly.com/2008/04/20/ubuntu-and-notebook-ii/](http://livemorelightly.com/2008/04/20/ubuntu-and-notebook-ii/)


Thanks.

vixmusic01

---

### Post by Partyboi2 on 2008-04-20
If you install windows after ubuntu you will need to restore grub. See [here ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0")
I would also remove the 828.00 Kib swap using gparted on the live cd (System>Admin>Partition Editor) Also would move the unallocated space listed and use the resize/move option with gparted to move it to ubuntu partition and maybe increase the size of your swap (570mb) depending on how much ram you have onboard. (The amount should be approximate twice as much as the amount of ram you have, but I would suggest going no higher then 2 gig)

Or after option could be after you have installed vista use the ubuntu live cd and use the partition editor to delete the current ubuntu partitions then run the ubuntu installer again.

---

### Post by vixmusic01 on 2008-04-20
If I am going to re-install Vista - I can reformat the whole drive to be Windows and start again with my Ubuntu 7.10 install disk.

However, as soon as I install Ubuntu I am going to have the same problem with Vista not starting.

I think Vista should work as it is from grub, but it won't.

Any more ideas?

I am trying to make a Grub live disk now.

Is that the same as a Ubuntu Live disk?

Thanks.

Vixmusic01

---

### Post by Partyboi2 on 2008-04-20
When you say vista will not start is it appearing in the grub menu list (where you choose which operating system you want to boot into) when you boot your system? 
The super grub disk is very useful for solving many bootloader problems. [Here]("http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html#How_To_Use_Super_Grub_Disk") is a small howto

---

### Post by pietjanjaap on 2008-04-20
Install vista,
then make a empty partition for ubuntu(make vista disk smaller),
install all software for vista,
make a backup of vista, so that if you put it back it only cleans the vista partition(leaves ubuntu untouched),

Then install ubuntu.





burn supergrub on cd, with this you can reinstall grub.


Give a more accurate problem distription.

---

### Post by tommcd on 2008-04-20
You can use Vista's own partitioning tool to create free space for Ubuntu instead of using Ubuntu's partitioning utilty. Perhaps you could try that, and then install Ubuntu to the free space that you created:
[http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

---

### Post by vixmusic01 on 2008-04-20
When I start up the computer from the hard drive it gives me the options of starting 

Ubuntu, 
Ubuntu recovery, 
Vista(longhorn loader)
Vista (longhorn loader)
kernal 7.10
Kernal 7.10

It auto boots into Ubuntu after a couple of minutes, so this is not 100% accurate.

The Ubuntu works beautifully now. I hate to destroy it and I am sure that the VIsta files are all there.

I don't know why there is two entries for each OS.

I am going to try to get rid of the kernal (failed Ubuntu Studio install) with Gparted.
Of course if I am going to wipe the drive, why waste my time?
I have made a Live Gparted disk - just i case.

I did reinstall Vista after the failed install, then installed the working Ubuntu.

I think all the files required to run are there.

I will try again Sunday. I want this to work.

Thanks for the help.
Victoria

I will see if I can figure out the Super grub.

---

### Post by vixmusic01 on 2008-04-20
This morning I went into Ubuntu and deleted the swap drive at the end of the list of partitions using gparted. I also found out that the Home folder that Ubuntu sees belongs to the previous Ubuntu studio install as I did not have permission to save anything.

I wanted to take a photo of the giant ERROR message that I get when starting Vista so everyone could see that this is a really different problems.

I rebooted into Windows Vista (longhorn)  but now it is installing.

There is a small window called "Windows Setup"
---------------------------------

Windows Setup
Windows is now installing the following items:
Install the application

------------------------------  

Behind this small window is a listing of programs example:

C:\preload\touchpad>start /w C:\preload\patch\sleep.exe

Now Vista is starting up. 

This is so odd.

I didn't do anything except remove one swap drive.

I will now see how functional Vista is and if I can still boot into a working Ubuntu.

Thanks for the help.

Truth is stranger than fiction.
--------------------------------------------------------------

I still have the problem with the hard drive fragmentation and the Ubuntu studio kernal being on the drive and owning the home directory.

This is progress though.

vixmusic01

---

### Post by vixmusic01 on 2008-04-20
This post can be viewed on my blog also 

livemorelightly.com

After this post, I went back to see how Vista was installing and saw this screen.

See attachment #1

Ubuntu booted? 

Possible explanation: Vista restarted to install and the bootloader defaults to Ubuntu.

Check it out - it seems to still be working despite all of the Vista activity.

Back to a reboot and I chose the first listing of Vista - that is where all the installing was happening before.

See attachment #2

The giant ERROR screen

Possible explanation: This is some type of back-up archive and something happened before that is not happening now.

Reboot - I am getting really good at loosening the battery just enough ....

The second listing of Vista (longhorn) booted into the Vista Welcome screen.

See attachment #3

This is not the same boot-up that happened before. This one asks to set my language and password and makes me check the license agreement. (there is nothing on there against dual boot)

Now it seems that Vista will work.

I will be checking out the functionality now.

Thanks again for the help and for all those who don't want to bother going to my blog I have thumbnails attached. I still can't figure out how to embed them in the forum, but I hope this will assist in the diagnosis.

vixmusic01

---

### Post by tommcd on 2008-04-21
Vixmusic01,
I read the story on your blog.
Is the /home partition from Ubuntu Studio shared with Ubuntu, but you just can't write files to it? If that is the case you can get write permission for /home like this. From terminal (applications > accesories > terminal) do: "sudo chown -R your_username:users /home" If the home folder is named something else then change it accordingly.  For example, I would do "sudo chown -R tom:users /home" (without the quotes).

To delete the non-functioning Vista listing from the grub menu, do this. First, back up grub's menu.lst like this:
 "sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak"  Then edit the menu.lst file:
"gksudo gedit /boot/grub/menu.lst" (Use gksudo for graphical apps). Scroll down to the "Other Operating Systems" part at the end and delete the non-functioning Vista entry. If it is the first one on the list when you boot up then it will be the first one listed there. EDIT: Just make sure you delete the entry for Vista's recovery partition and not the entry that works to boot Vista. Then save and close the file. 

You can use Gparted live CD or Parted Magic to delete or reformat the Ubuntu Studio partition. You could also use fdisk or cfdisk from the terminal, but a live CD would be easier if you're not familiar with fdisk.
[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)
Just be sure to delete the right partition! To get a listing of your partitions, run "sudo fdisk -l" from terminal. (That is a lower case L, not a 1). 
Write back if you need more help.

---

### Post by vixmusic01 on 2008-04-24
Thanks Tommcd,

As I wrote in my blog - Truth is stranger than fiction.

After I used gparted inside Ubuntu to delete the extra swap drive at the end of the drive, Vista installed itself and only sees itself on the drive. It boots from the second listing in grub very well. 

I will try to fix the remaining problems left from the failed install of ubuntu studio. I found out from [http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/](http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/)

that I can delete the non-functioning kernal with synaptic. Then, as no kernal will be mounted, I think I can partition from inside Ubuntu to reclaim the space using gparted.

See attachments for before and after swap deletion.

I have also made a gparted live disk - but I will only use it as a last resort as I have the 2 OS working now and don't want to mess it up. I will try your suggestion about the home directory -- however the last sudo I tried was not sucessful and now I am locked out of my fonts folder on my desktop. I am trying to use tools because autopilot seems to work great in Linux and I really don't know what I am doing. I just have enough computer experience not to panic and trust that I will be able to fix it. 

The next task will be re-pointing the home directory. Then delete the non-functional kernal. Finally repartition the drive to reclaim unused space and the space formerly occupied by the kernel.

I think that once I delete the kernel I should be able to manage the partition with gparted inside Ubuntu because it won't be mounting and locked.

Do you see anything wrong with this procedure?

Thanks to everyone for the help and I will update with progress.

vixmusic01

---

### Post by lswest on 2008-04-24
try this: install Ubuntu, then install Vista, and then restore GRUB using the how-to i wrote (second line of my sig), should get it working, unless Vista (being as it's an OEM install) overwrites the ext3 partition too. (Sorry, i didn't read the whole story, i'm multi-tasking, just thought i'd post this idea).

---

### Post by vixmusic01 on 2008-04-24
Hi,

I'm back again. The chown command did not sudo .... :invalid group.

I copied the command exactly "sudo chown -R your_username:users /home".

I think it saw the final /home as a switch and in the help the switch is /u

I set up home as a partition because I read that you could easily update Ubuntu without loosing your settings. Ubuntustudio allowed me to set up the partitions, but the Gutsy install did everything auto. I thought it would over write instead of parallel install.

I will try again.

I am going to close this thread as Vista and Ubuntu boot now.
I will open another if I can't fix Ubuntu and reclaim my lost HD space.
Thanks to everyone for your help.

Do visit my blog for progress reports on producing a multi-media project in Ubuntu.

[www.livemorelightly.com](www.livemorelightly.com)

---

### Post by tommcd on 2008-04-25
> **vixmusic01 said:**
> Hi,

I'm back again. The chown command did not sudo .... :invalid group.

I copied the command exactly "sudo chown -R your_username:users /home".
I think it saw the final /home as a switch and in the help the switch is /u


The command needs to be modified according to your username and the name of your home directory. For example, my username is "tom" so I would do "sudo chown -R tom:users /home". Whatever your username is when you boot up and log into Ubuntu is what you will substitute for your_username in the command I gave you.
Are you able to sudo anything? If sudo is not working for you at all, then see this:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
It is normal for Windows not to recognize the linux partitions. When I boot XP it just shows my linux partitions as unknown file system, or something like that.
If those extra kernels you see are from the Ubuntu Studio partition you won't find them in synaptic in Ubuntu, but you can delete that partition with gparted. Be careful when removing kernels from synaptic. It is good to have at least 1 backup kernel. If your working kernel gets messed up you can boot the older kernel.
Which partition is Ubuntu's root? From the gparted screenshot on your blog it looks like /dev/sda7 is Ubuntu because the label is /, and /dev/sda6 is labeled ubuntu_os, so I guess that is Ubuntu Studio. Is that gparted from Ubuntu as you said in your post, or is it the gparted live CD? If /dev/sda6 is Ubuntu studio you should be able to delete it and enlarge your /home to claim that space since it is adjacent to /home on /dev/sda5.
The 2nd screenshot in your post is too small for me to see.

---

