---
title: "Help with installation and dual boot"
date: 2012-08-28
forum: Installation &amp; Upgrades
---

### Post by zohonie on 2012-08-28
[IMG]http://imageshack.us/photo/my-images/20/68982612.jpg/[/IMG]Hi,

Very new to the world of linux and needed to install it next to win xp.

I though I can do it alone with no help and I think I messed it up. I need to have a duel boot system that can helpfully allow for transfer the files between both partitions. I have a 750 gb hard drive and I want linux to occupy 150 of those.

So after I installed I dont have the option of either boot windows or linux. It goes directly to linux. Here is a screen shot of the partitions. Please help me!!

---

### Post by drmrgd on 2012-08-28
It seems the screenshot is missing from your post.  

Better, though, would be to run the Create Bootinfo Summary from the Boot Repair package:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

That will give us an idea of how you configured your system, and where the boot files are.  Then we can advise on how to get Windows to show up as a boot choice.

---

### Post by mattfrog on 2012-08-28
Hi zohonie, welcome to Ubuntu and the Ubuntu forums ):P

Don't fret - there's plenty of very knowledgeable people around here to help. 

Your screenshot didn't display correctly - you may want to upload it to imgur.com and edit your post with a link to the image.

Thanks ):P

---

### Post by zohonie on 2012-08-28
Hi, thanks for the assurances :)

Here is the link:

[http://paste.ubuntu.com/1172228/](http://paste.ubuntu.com/1172228/)

Looking forward to hearing from you.

---

### Post by drmrgd on 2012-08-28
In these cases I usually like to defer to forum user Oldfred as he is a master at OS dual booting.  However, the results of the Bootinfo Script suggest that there is no Windows partition there.  There does seem to be something going on,though, as I can't account for some hard drive space, and I see the warning about having a partition outside of the disk.  So, I'm thinking that the partition table may have become corrupted or was not done quite correctly.  How did you partition the disk in order to make space for Ubuntu?  

It would be better to wait for a response from Oldfred, or another a little more experienced before we move on.  At this point the Windows install may still be salvaged.

---

### Post by zohonie on 2012-08-28
I simply devided the total space (750gb) to 150 for linux and 600 for windows. I'm not sure if that answers your question.

---

### Post by oldfred on 2012-08-28
It is only showing a Linux partition. STOP using drive.

Use liveCD and download testdisk. It may find old partitions or deeper scan may find old files. It looks like Windows partition is gone? What did you use to create partitions and how did you install. The auto install to the entire drive warns you that it is erasing system.

[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by zohonie on 2012-08-29
Hi oldfred,

Thanks for pointing me to testdisk.

Im currently running a deeper scan and in the attached image you can see all the stuff that it found.

[http://imgur.com/bAoxW](http://imgur.com/bAoxW)

 I suspect that the windows partition is the 3rd one. What do you think?

Do you need the logfile from testdisk?

I did the partitioning initially from the livecd. I think what i did is I placed both linux and win xp in the small partition.  I suspect that the windows data is still available because the I got a message stating that the hard drive is almost full. 



How do you think I should proceed?

Thanks.

[IMG]http://imgur.com/bAoxW[/IMG]

---

### Post by oldfred on 2012-08-29
I do not know details of testdisk. You can upload screenshots with the paperclip icon in the edit panel above you message.

If testdisk is showing files and you have some you did not backup, copy those over.

---

### Post by zohonie on 2012-08-29
> **oldfred said:**
> I do not know details of testdisk. You can upload screenshots with the paperclip icon in the edit panel above you message.

If testdisk is showing files and you have some you did not backup, copy those over.


I uploaded the screen shot.

---

### Post by oldfred on 2012-08-29
I still do not fully understand the chs display of testdisk. Everything is LBA now and chs has not been used for years, but is still an underlying configuration. It looks like a combination of old partitions as they have overlapping starts & ends. If you know what your partitions were then you may have a better idea of what to recover.

---

### Post by doktorOblivion on 2012-08-29
Zohonie,
please append the contents of your /boot/grub/grub.cfg, in particular, the contents of this section:


### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdd1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root D70ABE376062C20B
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###


You should understand, os-prober is the shell script responsible for finding other bootable OSes on the system.  If it cannot, its for a reason.  Please append your ENTIRE FILE, not just this section, since I believe it is probably empty.

Thanks.

---

### Post by doktorOblivion on 2012-08-29
Oh, one last thing.  It might be helpful to install gparted, it will go out and understand any partitions and HDDs that you have installed on your system.  I have a dual boot system, this is what it finds.  You can related this to my last append with the os-prober output.

---

### Post by oldfred on 2012-08-29
@   	doktorOblivion
FYI, in post #4 is the output from Boot-Repairs Bootinfo. It runs bootinfoscript which you can also download separately and outputs all of the data you have asked for (but not graphical gparted output). It only showed a Linux partition and no Windows partitions.  We find bootinfoscript or Bootinfo extremely useful in understanding exactly how a system is configured.

---

