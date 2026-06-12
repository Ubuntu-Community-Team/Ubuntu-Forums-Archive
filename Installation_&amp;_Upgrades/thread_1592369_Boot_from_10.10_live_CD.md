---
title: "Boot from 10.10 live CD"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by Tanargbob on 2010-10-10
Please be gentle with me as I am not very computer literate.
I run a PC with a AMD X2 5200, 4 Gb DDR2 ram, Nvidia 9800GTX and two SATA hard drives (160GB Win 7, and 250 GB Ubuntu 9.10 64 bit.) and a SATA DVD drive.
I never went for Ubuntu 10.04 because I had read about dual boot problems that I don't thing I am clever enough to sort out!
I have just downloaded 10.10 64 bit and burned a CD to boot the machine to as a live CD. The machine had no problems booting a live CD in the past.
I did not even get to see 10.10 as it came up with the following:
([I]initramfs) mount: mounting /devloop) on //filesystem.squashfs failed: Input/output error
Cannot mount /dev/loop0 (/cdrom/casper/filesystem/squashfs) on //filesystem/squashfs.
[/I]Now call me thick, but should I know what that means?

---

### Post by Rubi1200 on 2010-10-10
Definitely not thick!! 

Here are some things to try first:
1. check the MD5SUM of the image: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
2. burn the .iso image at the lowest possible speed
3. if the CD starts correctly, select the option to check for defects (I think that is what it says either that or integrity)
4. try a different CD

I don't see a problem with your specifications and find it hard to believe that might be the problem other than the fact that I seem to recall that SATA drives can be an issue.

---

### Post by sikander3786 on 2010-10-10
Rubi has got some suggestion in the above post. Rule out the MD5SUM and disc defect possibility.

Also, you've got 2 hard drives, are you using a Raid setup? I've seen that error a few times with that.

Which mother board specifically? How many SATA controllers are there on the board?

---

### Post by Tanargbob on 2010-10-10
Well, I never thought that I could use the terminal!
I followed the instructions to check the CD and it came up with "md5sum: ./casper/filesystem.squashfs: Input/output error
./casper/filesystem.squashfs: FAILED open or read
md5sum: WARNING: 1 of 209 listed files could not be read"
Looks like I should do another download and burn another CD.
Thank you very much for the help, much appreciated.

---

### Post by Rubi1200 on 2010-10-10
You are more than welcome :)

Keep us informed and remember there is always someone here willing to try and help.

---

### Post by Tanargbob on 2010-10-10
I am loving this, I have now installed md5deep and compared the .iso file to the Cd and got this:
[I]****@****-desktop:~/Desktop$ sh hashcdrom.sh ubuntu-10.10-desktop-amd64.iso /dev/cdrom
/usr/bin/md5deep
checksum for input image: 89ea042d36e6a91ab6e98a1020ec3082                
checksum for output disk: 7bd73b6cf706b945f377e022f70966f0                
verification failed![/I]
So it seems to be the burning that has gone wrong.
I will attach an old IDE CD writer in the morning and try again.
I have learned more this evening than I have as a user over the past year!
Thanks again.

---

### Post by Tanargbob on 2010-10-10
> **sikander3786 said:**
> Rubi has got some suggestion in the above post. Rule out the MD5SUM and disc defect possibility.

Also, you've got 2 hard drives, are you using a Raid setup? I've seen that error a few times with that.

Which mother board specifically? How many SATA controllers are there on the board?

No raid setup - I don't know how to do that  :(
There are 4 SATA sockets on the board and it is a K9N neo ver3, that is what it says on the board anyway. I think it is a duff CD as in my last post.

---

### Post by sikander3786 on 2010-10-10
> **Tanargbob said:**
> No raid setup - I don't know how to do that  :(
There are 4 SATA sockets on the board and it is a K9N neo ver3, that is what it says on the board anyway. I think it is a duff CD as in my last post.
Yes it might be. You can also create a USB startup disk and use it for installation.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Tanargbob on 2010-10-10
OK, hope I am not boring anyone here. 
I have burned two more CDs from the .iso file and got the same failure as in post #6.
I am now downloading the .iso file again and will see what happens with that.
The wife is calling me to come to bed as it is now 23:20 hrs here in France.
Will keep updating this thread.

---

### Post by sikander3786 on 2010-10-10
> I am now downloading the .iso file again and will see what happens with that.

You should have checked the MD5SUM of the image itself as Rubi suggested in his above post.

> The wife is calling me to come to bed as it is now 23:20 hrs here in France.

It is 2:30 here in Pakistan but my wife is already sleeping hopeless ;-)

---

### Post by oldfred on 2010-10-10
There was also a syslinux bug that may be related, something about an extra ui in command line:

[http://ubuntuforums.org/showthread.php?t=1589852](http://ubuntuforums.org/showthread.php?t=1589852)
Maverick images burned to usb key on lucid fail to boot - different syslinux version 
ui in /isolinux/isolinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
[http://ubuntuforums.org/showthread.php?t=1582446](http://ubuntuforums.org/showthread.php?t=1582446)

---

### Post by Tanargbob on 2010-10-10
> **sikander3786 said:**
> You should have checked the MD5SUM of the image itself as Rubi suggested in his above post.



It is 2:30 here in Pakistan but my wife is already sleeping hopeless ;-)

OK Sikander, missed that in my excitement to try and use the terminal. I have now verified that the .iso image did not have the correct MD5 check number as is posted on the internet. I have downloaded it again and now have the correct one.
Will burn it again in the morning and see what happens.
Thanks once again for the help.

---

### Post by Tanargbob on 2010-10-11
OK, tried the CD this morning and it boots.
Thanks for taking the time to help me on this without making me feel like an idiot. 
Now to back up my existing system to install 10.10 and to get it all working with the dual boot. I am sure that I'll be back with more questions.

---

