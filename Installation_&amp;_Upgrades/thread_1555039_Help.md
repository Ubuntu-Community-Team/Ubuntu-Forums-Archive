---
title: "Help"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by Awaiskhan on 2010-08-17
i recenly installed ubuntu 10.04 and theres a bug so i want to reinstall win 7 but my pc wont boot up the cd at start up so i tried to run the setup.exe file and ubuntu cant open it so how will i install win

i have tried wine to open the setup but i get and error

---

### Post by Rubi1200 on 2010-08-17
> **Awaiskhan said:**
> i recenly installed ubuntu 10.04 and theres a bug so i want to reinstall win 7 but my pc wont boot up the cd at start up so i tried to run the setup.exe file and ubuntu cant open it so how will i install win

i have tried wine to open the setup but i get and error
Did you install Ubuntu to the hard-drive or with Wubi?

Do you want to get rid of Ubuntu completely and then reinstall Windows (this is how I understand your post)?

You cannot use Ubuntu to open .exe files in the way you want and WINE will not help you either.

If you want, you could use an Ubuntu CD (or any live distro that has a partitioning tool) to boot the computer, delete the Ubuntu partitions, and prepare the drive to reinstall Windows.

---

### Post by tommcd on 2010-08-17
> **Awaiskhan said:**
> i recenly installed ubuntu 10.04 and theres a bug so i want to reinstall win 7 but my pc wont boot up the cd at start up ...
If you are trying to reinstall Windows from a Windows install CD or DVD, make sure the computer's BIOS is set to boot from the CDROM drive as *the first boot device*. You should then be able to boot from the Windows CD and (regrettably!!) reinstall Windows.

Just out of curiosity, what is this "bug" that is causing you to give up on Ubuntu so soon? Please describe the problem in as much detail as you can. Perhaps we can help you fix it.
What computer are you running Ubuntu on?

And welcome to the Ubuntu forums!

---

### Post by Awaiskhan on 2010-08-17
> **Rubi1200 said:**
> Did you install Ubuntu to the hard-drive or with Wubi?

Do you want to get rid of Ubuntu completely and then reinstall Windows (this is how I understand your post)?

You cannot use Ubuntu to open .exe files in the way you want and WINE will not help you either.

If you want, you could use an Ubuntu CD (or any live distro that has a partitioning tool) to boot the computer, delete the Ubuntu partitions, and prepare the drive to reinstall Windows.

how do i reinstall windows when the cd and a usb wont boot at start i have changed bios but still not working

---

### Post by Awaiskhan on 2010-08-17
> **tommcd said:**
> If you are trying to reinstall Windows from a Windows install CD or DVD, make sure the computer's BIOS is set to boot from the CDROM drive as *the first boot device*. You should then be able to boot from the Windows CD and (regrettably!!) reinstall Windows.

Just out of curiosity, what is this "bug" that is causing you to give up on Ubuntu so soon? Please describe the problem in as much detail as you can. Perhaps we can help you fix it.
What computer are you running Ubuntu on?

And welcome to the Ubuntu forums!

the bug is as follows-

randomly when iam using the pc i get a black screen and the last thing i see is checking battery state then it disappears and reappears forever but it sounds like my monitor is trying to change resolution it keeps makin clicking sounds while the bug is doin it thing

---

### Post by pricetech on 2010-08-17
If you can't boot to CD, then how did you install Ubuntu ??  What kind of computer are we working with here ??  It might help if we know more.

Generically speaking, you just need to boot to either a CD/DVD or USB drive with the OS you want to install on it.  Your Windows 7 disk should boot.

---

### Post by rakiim on 2010-08-17
hello, i have a problem with my laptop...I installed ubuntu and when I opened it appears that
error: no such device: c631ca9c-94e9-44c7-a0f9-f2ca5e33d9bf
grub rescue>

What can I do to not appears? I do not recognize any optical drive a CD or DVD


thank you.

---

### Post by Rubi1200 on 2010-08-17
> **rakiim said:**
> hello, i have a problem with my laptop...I installed ubuntu and when I opened it appears that
error: no such device: c631ca9c-94e9-44c7-a0f9-f2ca5e33d9bf
grub rescue>

What can I do to not appears? I do not recognize any optical drive a CD or DVD


thank you.
Hi rakiim and welcome to the forums.

You really need to start your own thread because your problem is quite different than the one being dealt with here.

Thanks :-)

---

### Post by Awaiskhan on 2010-08-17
> **pricetech said:**
> If you can't boot to CD, then how did you install Ubuntu ??  What kind of computer are we working with here ??  It might help if we know more.

Generically speaking, you just need to boot to either a CD/DVD or USB drive with the OS you want to install on it.  Your Windows 7 disk should boot.

its like this i installed ubuntu from a cd i got delivered before i had ubuntu i had win 7 which i upgraded from a usb from xp yes with me so far and i have the win 7 files on my hardrive and usb but my pc wont install at start up from it

---

### Post by deadalus.globalnode on 2010-08-17
Is the windows 7 disk an upgrade version or a full version. You may have to install xp before you can "install" 7.

---

### Post by Rubi1200 on 2010-08-17
> **Awaiskhan said:**
> its like this i installed ubuntu from a cd i got delivered before i had ubuntu i had win 7 which i upgraded from a usb from xp yes with me so far and i have the win 7 files on my hardrive and usb but my pc wont install at start up from it
If you were able to use the Ubuntu CD before, why not use it again? But this time instead of choosing to install, pick the option to try Ubuntu without making changes.

Then, you could go to System > Administration > GParted and take a screenshot of your setup to post back here.

Personally, I don't understand how a CD drive works one minute and then the next it won't :confused:

---

### Post by Awaiskhan on 2010-08-17
> **Awaiskhan said:**
> its like this i installed ubuntu from a cd i got delivered before i had ubuntu i had win 7 which i upgraded from a usb from xp yes with me so far and i have the win 7 files on my hardrive and usb but my pc wont install at start up from it

i discovered a program in admin called start up disk creator but thats only for installing a newer version of ubuntu so is there a program like that to install a different os

---

### Post by Awaiskhan on 2010-08-17
> **Rubi1200 said:**
> If you were able to use the Ubuntu CD before, why not use it again? But this time instead of choosing to install, pick the option to try Ubuntu without making changes.

Then, you could go to System > Administration > GParted and take a screenshot of your setup to post back here.

Personally, I don't understand how a CD drive works one minute and then the next it won't :confused:

no iam installin win 7 from a usb not cd

---

### Post by Rubi1200 on 2010-08-17
Did you see the post by deadalus.globalnode?

So, you are in Ubuntu right now?

If yes, please go to Applications > Accessories > Terminal and post the output of
```
sudo fdisk -l
``` (lowercase L not 1)

---

### Post by tommcd on 2010-08-17
> **Awaiskhan said:**
> the bug is as follows-

randomly wen iam using the pc i get a black screen and the last thing i see is checking battery state then it disappears and reappears forever ... 
1. What graphics card do you have? And, as I asked before, what kind of computer is this??? What are your hardware specs???
> **Awaiskhan said:**
> 
but it sounds like my monitor is trying to change resolution it keeps makin clicking sounds while the bug is doin it thing
I don't know what that means. Is there supposed to be a complete sentence in there somewhere? What is making the "clicking sounds"?
Please try to write coherent, complete, and punctuated sentences if you can. Your posts are difficult to decipher.

---

### Post by Awaiskhan on 2010-08-18
> **deadalus.globalnode said:**
> Is the windows 7 disk an upgrade version or a full version. You may have to install xp before you can "install" 7.

it the full 3gb installation

---

### Post by Awaiskhan on 2010-08-18
> **Rubi1200 said:**
> Did you see the post by deadalus.globalnode?

So, you are in Ubuntu right now?

If yes, please go to Applications > Accessories > Terminal and post the output of
```
sudo fdisk -l
``` (lowercase L not 1)

this is what i got 


Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004db9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2411    19357687+  83  Linux
/dev/sda2            2411        4866    19723265    5  Extended
/dev/sda5            4775        4866      731136   82  Linux swap / Solaris
/dev/sda6            2411        4687    18282496   83  Linux
/dev/sda7            4687        4774      704512   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Awaiskhan on 2010-08-18
my specs are

Hp pavilion A309.uk
256MB RAM
Intel celeron processer 2.4Ghz
Intel 82845 graphics controller
up to 64MB shared video memory
40GB HDD

---

### Post by Awaiskhan on 2010-08-18
what files and folder does start up disk creator use because i was wondering if you could copy the win 7 iso into its directery and trick it to startin the iso at start up is this possible

---

### Post by Awaiskhan on 2010-08-18
?

---

