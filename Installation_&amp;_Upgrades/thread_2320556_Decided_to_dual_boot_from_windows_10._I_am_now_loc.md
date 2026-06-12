---
title: "Decided to dual boot from windows 10. I am now locked out."
date: 2016-04-15
forum: Installation &amp; Upgrades
---

### Post by TheHybrid on 2016-04-15
So, basically overnight I decided "You know what? I want to try to dualboot Ubuntu." And now I'm stuck. I'm tired now, and distressed, because I feel like I'm going to have to do a total format of my HDD and lose EVERYTHING that I have, because I just can't figure this **** out. So, I have two HDD's, one is 1000 gigabyes, the other 500 gigabytes. I Took about 30 gigs from my 500 gig HDD< and installed linux onto it. I could of sworn, that when I did this, I told it to install the grub/mbr/whatever onto the 500 gig HDD, but apparantly it didn't do that, or I messed up. Now, I can't boot into windows, and I even tried repairing it using boot-repair and it did nothing. When I select my 1000 gig hard-drive, it just boots me into linux. When I select the HDD where linux is installed, it just boots me into linux. I don't know what to do, and I just simply want to get back into windows so I can work on a fix there, since I am more familiar with that OS.

---

### Post by yancek on 2016-04-15
You have not indicated which version of windows you are using.
You have not indicated which version of Ubuntu you are using.
You have not posted any information on the hardware.
You did not post a link to the boot repair output.  There is an option to "Create BootInfo Summary".  Run it again and post a link to it here and someone should be able to point you in the right direction.

If you have windows 8 or newer, the most likely scenario is that it was installed using UEFI/GPT and you installed Ubuntu MBR/GPT.  These conflict and the result is what you see.  For a basic understanding, see the link below.

  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2016-04-15
But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by oldos2er on 2016-04-15
> **yancek said:**
> You have not indicated which version of windows you are using.

Windows 10 is shown in the thread title; I agree that we need much more info to be able to help.

> **TheHybrid said:**
>  just simply want to get back into windows so I can work on a fix there, since I am more familiar with that OS.

What kind of fix are you looking for, simply getting rid of Ubuntu and going back to all Windows? Or maintaining a dual boot system?

---

### Post by Bucky Ball on 2016-04-15
Don't panic ... yet. This may be simpler to get out of with some help than you're imagining. Post the output of the bootinfo script that Boot Repair creates, as requested, and all will be revealed. ;)

---

### Post by TheHybrid on 2016-04-15
> **oldfred said:**
> But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Here you go [http://paste.ubuntu.com/15854295/](http://paste.ubuntu.com/15854295/)

> **oldos2er said:**
> Windows 10 is shown in the thread title; I agree that we need much more info to be able to help.



What kind of fix are you looking for, simply getting rid of Ubuntu and going back to all Windows? Or maintaining a dual boot system?
I'm looking to keep both OS's if possible, but I will resort to whatever is necessary to get back into my windows. I have a TB of data that I can not back up fully if I need to format. I don't see how it is revelent, but I have a core i5 4670k, 8 gigs of ram, a rad 280x, two HDD's, one is one TB, the other is 500 gigs. That's all I got for you, and that the mother board is asrock.

> **Bucky Ball said:**
> Don't panic ... yet. This may be simpler to get out of with some help than you're imagining. Post the output of the bootinfo script that Boot Repair creates, as requested, and all will be revealed. ;)
And here you go too [http://paste.ubuntu.com/15854295/](http://paste.ubuntu.com/15854295/) it would be cool if I got this resolved ^^

---

### Post by yancek on 2016-04-15
Boot Ubuntu, open a terminal and run:  sudo update-grub

There is no windows entry in the grub.cfg boot menu file.  A windows system is usually detected if you have the windows drive plugged in, not sure what happened here.

---

### Post by TheHybrid on 2016-04-15
When I did this, all I got was this;
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.

---

### Post by TheHybrid on 2016-04-15
I'm going to guess from the lack of replies I'm basically ****ed. Is there anyway I could just at least restore the original windows 10 mbr? I know it would lock me out of linux, but it's better then losing everything I have.

---

### Post by LukeMorrison on 2016-04-15
With all due respect, I think you need to give this forum a bit more time to work.  In the meantime, take a look at these links and if you are unsure, ask questions first:

[http://askubuntu.com/questions/207663/cannot-update-grub-with-paramters-on-live-usb](http://askubuntu.com/questions/207663/cannot-update-grub-with-paramters-on-live-usb)
[http://askubuntu.com/questions/254491/failed-to-get-canonical-path-of-cow](http://askubuntu.com/questions/254491/failed-to-get-canonical-path-of-cow)

---

### Post by oldfred on 2016-04-15
/cow is copy on write or live installer. 
If you can boot into your install on sdb from BIOS run the sudo update-grub from that.

And with multiple drives do not run any auto fix from Boot-Repair. It installs grub to the MBR of every drive. You want to keep your Windows boot loader on sda, and set BIOS to boot grub from sdb. But grub only boots working Windows, so occasionally you may need to go into BIOS or one time boot key like f10 or f12 and directly boot Windows. Or may even need a Windows repair flash drive.

You can use Boot-Repair's advanced mode to choose Windows and install a Windows type boot loader (syslinux) to MBR of Windows drive. Or use Windows repair flash drive to restore a Windows boot loader to sda. Then confirm Windows boots, is not hibernated nor needs chkdsk. Then grub from you install should find it and the menu entry in grub should work when from BIOS booting Ubuntu drive.

---

### Post by TheHybrid on 2016-04-15
> **oldfred said:**
> /cow is copy on write or live installer. 
If you can boot into your install on sdb from BIOS run the sudo update-grub from that.

And with multiple drives do not run any auto fix from Boot-Repair. It installs grub to the MBR of every drive. You want to keep your Windows boot loader on sda, and set BIOS to boot grub from sdb. But grub only boots working Windows, so occasionally you may need to go into BIOS or one time boot key like f10 or f12 and directly boot Windows. Or may even need a Windows repair flash drive.

You can use Boot-Repair's advanced mode to choose Windows and install a Windows type boot loader (syslinux) to MBR of Windows drive. Or use Windows repair flash drive to restore a Windows boot loader to sda. Then confirm Windows boots, is not hibernated nor needs chkdsk. Then grub from you install should find it and the menu entry in grub should work when from BIOS booting Ubuntu drive.

I tried what you said, and used the command when I was in my main install of ubuntu, rebooted, saw windows 10 as an option. Thank you.
Sorry everyone for getting a little freaked out, I was just annoyed and scared I wouldn't be able to access windows anymore.

Thank you all for your help, I think I'll be keeping Ubuntu as a dual-boot, and experiement with it some more later. Now, how do I add a solved thing to this thread?

---

### Post by yancek on 2016-04-15
I'm not sure why you tried to update-grub from your DVD.  You can do that but it is more complex than that single command.   You had indicated in your initial post that you had no problem booting Ubuntu from the hard drive so I don't know why you tried to run it from the DVD.  In the future, if you are unsure ask.

---

### Post by TheHybrid on 2016-04-15
> **yancek said:**
> I'm not sure why you tried to update-grub from your DVD.  You can do that but it is more complex than that single command.   You had indicated in your initial post that you had no problem booting Ubuntu from the hard drive so I don't know why you tried to run it from the DVD.  In the future, if you are unsure ask.

Well, I wasn't really sure what the command did, but now I see that it searches for other OS's that it can boot into (I think?) If I would of known that, I would of known to run it in the main os.

---

### Post by Bucky Ball on 2016-04-15
Glad it's fixed. Please see the first link in my signature at the bottom of this post for how to mark the thread as solved. Enjoy the ride. ;)

(PS: Unless there was some major wipe out of the Windows partitions when you installed Ubuntu, it would always have been a matter of booting to a live session (boot from the Ubuntu install media and 'Try Ubuntu'), then copying the files from your internal drive to an external drive for backup. Very little chance all was lost. ;))

---

### Post by yancek on 2016-04-15
Yes, well it just searches for other operating systems and adds them to the boot menu for Grub which is a text file located in the /boot/grub directory.  In case you run into a situation in the future where you need to reinstall or update Grub and can't boot the installed system, the link below shows a number of methods to do that and might be worth bookmarking until you are more familiar with Grub.

 [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

