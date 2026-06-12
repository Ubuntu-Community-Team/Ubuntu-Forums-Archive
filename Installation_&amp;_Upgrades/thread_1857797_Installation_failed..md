---
title: "Installation failed."
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by pojr on 2011-10-11
Hi. I'm a long-time supporter ever since Ubuntu 8. I'm returning so that I can use Ubuntu for my Netbook.

For a while, my Netbook had Windows XP as the OS, which was fine, but it was hard to manage with only 8 GB of free space. As a result, I attempted to delete a bunch of files, and I guess I somehow stopped Windows XP from functioning properly. Not sure how it happened, but I decided it was for the best, because Ubuntu was probably the better option for a computer with only 8 GB of hard drive space.

I installed using the USB method. I got a flash drive, followed the installation directions, popped it in my Netbook, and dual-booted it. Next thing I know, I was running Ubuntu on my Netbook. I managed to connect to the Internet, and everything was going well, until I decided to install Ubuntu as my primary OS.

First it asked for language, I picked English. Then there were three green checkboxes: 4.4 GB requirement, Internet access, and wall charger plug-in. From there, I continued until I reached "Allocate drive space," and that's where I started having problems.

Here's the error message I got:

> No file root system is defined.

Please correct this from the partitioning menu.

What's up with that? Does it have anything to do with Windows XP possibly being corrupted? I attached a file below for everyone to see, if that helps. Thanks in return.

---

### Post by Quackers on 2011-10-11
Did you use the manual partitioning option?
If so, you need to select the mount point for the root system, which is " / " from the drop-down box in the partitioning window.

---

### Post by pojr on 2011-10-11
> **Quackers said:**
> Did you use the manual partitioning option?
If so, you need to select the mount point for the root system, which is " / " from the drop-down box in the partitioning window.

Manual partitioning. Hate to say it, but I have no clue what that means. Not sure what partitioning in general means, which is odd because I installed Ubuntu 8 long ago without any problem.

If you're wondering about the drop-down box that is shown in the image, there was only one available option: **/dev/sdb/**

Sorry for my lack of knowledge.

---

### Post by Quackers on 2011-10-11
No the drop-down box shown in your screenshot is for the installation of grub. Yours shows /dev/sdb which is interesting enough, as the default is /dev/sda

When you installed Ubuntu which option did you use - ie "install alongside" or "use the whole drive" or "manual partitioning" or "something else".

Which version of Ubuntu have you installed?

---

### Post by pojr on 2011-10-11
> **Quackers said:**
> When you installed Ubuntu which option did you use - ie "install alongside" or "use the whole drive" or "manual partitioning" or "something else".

I saw those four options on the [**Ubuntu download page**](http://www.ubuntu.com/download/ubuntu/download), but for some reason those options were not there when I attempted to install. Instead, I got the page I posted, unless of course I 'm at the wrong screen or something. I really hope I don't have to install all of this over again.


> **Quackers said:**
> Which version of Ubuntu have you installed?

11.04

---

### Post by Quackers on 2011-10-11
The window shown in your screenshot should be populated with the details of your current partition layout.
As these details are not shown it is possible that your current partition table is corrupt. Or it could be that the drive is empty.

---

### Post by pojr on 2011-10-11
> **Quackers said:**
> The window shown in your screenshot should be populated with the details of your current partition layout.
As these details are not shown it is possible that your current partition table is corrupt. Or it could be that the drive is empty.

I don't think the H drive is empty. What should I do to solve this problem? Should I repeat the entire Ubuntu installation process, all the way from square one when I first downloaded the ISO file?

---

### Post by Quackers on 2011-10-11
Are you currently posting from an Ubuntu live session on the affected computer or from a different computer?

In short it appears that the installation has not started yet.

---

### Post by pojr on 2011-10-11
> **Quackers said:**
> Are you currently posting from an Ubuntu live session on the affected computer or from a different computer?

Different computer. There's a Firefox tab on the Ubuntu desktop, but it won't open when I click it.


> **Quackers said:**
> In short it appears that the installation has not started yet.

Not sure what you mean. There was an "Install Ubuntu 11.04" icon on the desktop, and that's where I'm getting this error.

---

### Post by Quackers on 2011-10-11
Clicking on the install Ubuntu icon starts the installation process. So far the process has got to the partitioning stage, but evidently it's not finding your partitions.
On the affected computer can you quit the installation and open a terminal and post the output of ```
sudo fdisk -lu
``` please.

---

### Post by pojr on 2011-10-11
> **Quackers said:**
> On the affected computer can you quit the installation and open a terminal and post the output of ```
sudo fdisk -lu
```

Here's what I got as a result:

---

### Post by pojr on 2011-10-12
I tried to download the ISO file on another computer, and repeated the entire process over again in hopes that the computer would actually work this time. No dice, I still had the exact same problems as before.

Considering this issue was still intact, I decided to try it on my Mom's computer, it ran a whole lot better. I booted it, clicked "Install Ubuntu 11.04" and went from there. Here are screenshots:


**Welcome page**
[http://imgh.us/398_Screenshot.png](http://imgh.us/398_Screenshot.png)

**Preparing to install Ubuntu**
[http://imgh.us/Screenshot2.png](http://imgh.us/Screenshot2.png)

**And most importantly, the allocate drive space page**
[http://imgh.us/Screenshot3.png](http://imgh.us/Screenshot3.png)


It looks like it was successful. Not only that, but the Internet connected right away. Now lets check out my Netbook:


**Welcome page**
[http://imgh.us/Screenshotn.png](http://imgh.us/Screenshotn.png)

**Preparing to install Ubuntu**
[http://imgh.us/Screenshotn2.png](http://imgh.us/Screenshotn2.png)

**Allocate drive space page**
[http://imgh.us/Screenshotn3.png](http://imgh.us/Screenshotn3.png)


The very last step was completely different, as you can see. Therefore, it's likely that the reason that Ubuntu won't function is because of the Netbook itself, not the USB.

---

### Post by 23dornot23d on 2011-10-12
Its possible the drive information is not being read correctly .....

have you tried running gparted just to see if it shows the drive properly .....

do a screenshot of sda and sdb  ....... if you get gparted to work .....

sudo apt-get install gparted

find gparted in the dash and run it .....

There is also the Bootinfoscript ..... if you run it - will give detailed information for
people to inspect ..... 

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by pojr on 2011-10-12
I attached the results of bootinfoscript below. It appears that sda doesn't have a corresponding hard drive, or something like that. Check it out.

---

### Post by Hakunka-Matata on 2011-10-13
Yes indeed.  What happened to sda? 
 +1 on 23dornot23d's suggestion for gparted. 
 What does gparted show?

---

### Post by pojr on 2011-10-13
> **Hakunka-Matata said:**
> Yes indeed.  What happened to sda? 
 +1 on 23dornot23d's suggestion for gparted. 
 What does gparted show?


I'll post a picture later. At the moment, my friend has it. He's pretty good with Ubuntu and even he is stumped. He tried formatting the hard drive, but it gave him an error message. He has his own flash drive with Ubuntu on it, so he's going to try it on that, but chances are it's going to fail.

---

### Post by Quackers on 2011-10-13
Check in the bios to see whether that hard drive is recognised. It's looking dodgy:-( (or possibly the connection is bad?)

---

### Post by pojr on 2011-10-22
Thanks for the help. I figured out how to fix it, I ended up replacing the SSD, and it installed perfectly after that.

---

### Post by Quackers on 2011-10-22
Aha! A drive problem then. Glad to hear you got things sorted out :-)

---

