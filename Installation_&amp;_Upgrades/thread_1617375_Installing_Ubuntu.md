---
title: "Installing Ubuntu"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by gilligan on 2010-11-09
Hi there,
Before I ask my question, I'd like to start from something else. I tried to install the 2 last versions of Ubuntu and I was S.O.L. My only way to have the 10.10 version installed, is to install the 09.04 and then upgrade online to the latest version. Why? No idea.

Now here is my problem:
I have Win7 on one IDE HDD and I'm trying to install Ubuntu on a SATA HDD. The thing is Ubuntu detects the IDE HDD but not the SATA HDD. The IDE is set as the master in the BIOS. What might be the problem?

Thanks for your help.

---

### Post by gilligan on 2010-11-10
Hi,
Is there any body out there!! Can we get some help! I asked a question 5 days ago and still didn't get any answer from anybody. Or shall I just forget this ubuntu and stick with windows!

---

### Post by TBABill on 2010-11-10
gilligan, if I may offer a bit of friendly suggestion, it may be best to just bump your thread to move it up the list so others may be more likely to see it than to threaten to go back to Windows because nobody helped. It is likely nobody that has read it has the knowledge on the particular subject to assist with your specific issue. I am unable to assist because I have never used a dual drive Ubuntu configuration with Win 7 on one and Ubuntu on the other. 
 
Those who get the most assistance are generally those who are polite, considerate and open to the ideas and suggestions others post. Hopefully you will get some good responses soon, but keep in mind the users here are just like you, unpaid and here to research, learn or assist when able. 
 
Sorry I can't help with the actual problem you are experiencing.

---

### Post by sikander3786 on 2010-11-10
Hi.

Please be patient with your threads :-) Threads now a days get a response by an hour or two as there are many volunteers around. Ubuntu community is growing every second :-) Sad you didn't get one.

Can you please list your Hardware specs? How many sata controllers are there?

What happened with 10.10 and 10.04? Did you try the LiveCDs? Where did they get stuck?

---

### Post by gilligan on 2010-11-10
Hi TBABILL,
Thanks a lot for your message and I do appreciate it. You know, sometimes it happens to be carried away. You're right, just be patient and keep posting until may be someday I'll get the chance to get the help. I didn't mean to be mean or something like that.
Have a wonderful day.
Gilligan.

---

### Post by bobbob1016 on 2010-11-10
> **gilligan said:**
> Hi there,
Before I ask my question, I'd like to start from something else. I tried to install the 2 last versions of Ubuntu and I was S.O.L. My only way to have the 10.10 version installed, is to install the 09.04 and then upgrade online to the latest version. Why? No idea.

Now here is my problem:
I have Win7 on one IDE HDD and I'm trying to install Ubuntu on a SATA HDD. The thing is Ubuntu detects the IDE HDD but not the SATA HDD. The IDE is set as the master in the BIOS. What might be the problem?

Thanks for your help.

I have Win 7 on an ide drive, and Ubuntu on a sata drive, and everything shows up fine.  The ide drive is the master drive as well.  Is the sata drive on a card or the motherboard?  If you're installing Ubuntu along-side Win 7, you can probably set the sata drive as the master because Ubuntu will probably be installing GRUB as your boot loader.

Also, why do you have to go from 9.04 to 10.10?  There shouldn't be any need for that, 10.10 installed much much much easier than 9.04 (I do fresh installs instead of upgrades, been using only Ubuntu since 6.06, I tried 5.10 as well).

Btw, I was about to close the page until I read TBABill's comment.

---

### Post by GokulR on 2010-11-10
Try once by removing the IDE HDD and install Ubuntu, if it detects (it should) then there is problem with MASTER/SLAVE. You can set the SATA HDD to master and enjoy Ubuntu.

---

### Post by gilligan on 2010-11-10
Hi sikander,
Thanks a lot for your message. Sorry I got carried away. Not worth it. I really do like this Ubuntu community.
Here are the specs of my hardware:

MoBo: Intel D945GNT
RAM: 4 GB
4 SATA controlers
1 IDE controler
Primary Master: 250 GB IDE (With Windows 7)
SATA: 160 GB (for Ubuntu)

On the menu of the live CD, I chose Install Ubuntu, but it does nothing. It goes to the Ubuntu desktop. Then from there, I double click on Install Ubuntu (still from the live CD). When it gets to the HDD, the only HDD detected is the IDE where Windows 7 is installed. It does not detect the SATA HDD intended for Ubuntu.

Now the problem with 10.04 and 10.10 is every time I try to install them, I get this error message:

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs.


There is no way for me to install 10.04 and 10.10 without installing 9.04 and then upgrade from there.

Message for GokulR. Sata HDDs do not have master or slave settings as only one HDD can be connected to the controller.

Thanks all for you help.
Gilligan

---

### Post by sikander3786 on 2010-11-10
Please check the MD5SUM of the downlaoded image being used for installation.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the sums match, check the disc for defects or try burning a new disc at the lowest possible speeds.

It would be worthy to try some boot options as well.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

And what if you set the Sata HDD as master drive as already mentioned above? Did you try it that way? Does Ubuntu detect it then?

---

### Post by gilligan on 2010-11-10
I just set the SATA HDD as the master boot, I get the same thing. Only the IDE is detected.
Attached is a snapshot of the install screen.
Thanks for your help.
Gilligan

---

### Post by sikander3786 on 2010-11-10
> **gilligan said:**
> I just set the SATA HDD as the master boot, I get the same thing. Only the IDE is detected.
Attached is a snapshot of the install screen.
Thanks for your help.
Gilligan
Well. I hope it is detecting both the HDDs :P

Please post the output of

```
sudo fdisk -l
```

from terminal. Applications > Accessories > Terminal.

---

### Post by gilligan on 2010-11-11
Here is the output of sudo fdisk -l
-----------------------------
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb6bfbf66

Device     Boot     Start     End     Blocks     Id     System
/dev/sdal   *        1        13      102400     7      HPFS/NTFS
Partition1 does not end on cylinder boundary.
/dev/sdal2           13       30402   244093952  7      HPFS/NTFS

Disk /dev/sdb: 80.0 BG, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
Disk /dev/sdb doesn't contain a valid partition table.
------------------------------------------

Looks like it shows the 2 HDDs (250 GB with Win 7 and 80GB intended for Ubuntu).

---

### Post by sikander3786 on 2010-11-11
It is detecting your 2nd drive as an 80 GB drive whereas you mentioned it is 160GB, right? I think there is another problem.

> Disk /dev/sdb doesn't contain a valid partition table.

Are you able to mount this drive in Windows without any problems? I suggest you to download the diagnostic tools from manufacturer's website and check your HDD thoroughly.

If you select "Specify partitions manually (advanced)", do you see your 2nd HDD, even if it is listed as an 80GB drive?

---

### Post by gilligan on 2010-11-11
Sorry, I forgot to mention. I replaced the 160 GB HDD with a 80 GB.
Yes, I am able to mount the drive in Windows. Diagnostic tools is an other option. As for the "Specify partitions manually", it shows only the Win7 HDD.

---

### Post by Bearly Able on 2010-11-11
This is probably a daft suggestion, but if you check the "Erase and use the entire disc" radio button, does the drop-down menu become active and let you choose the correct drive?  Just a thought.

---

