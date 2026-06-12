---
title: "need help with 12.04 install"
date: 2012-10-25
forum: Installation &amp; Upgrades
---

### Post by d1weeb on 2012-10-25
Hello,

I am trying to install 12.04 from a disk I purchased through linuxidentity magazine ubuntu 12.04.
I have a number of questions.
1. I how can I tell if the install finished, the who are you screen is the last screen I see?
2. If unbuntu did get installed I can't get it to boot from disk, even trying some of the suggestions in this forum?
3. I can't edit the grub file, and don't know why it is write protected?

Lets start with these questions.
Mainboard: MSI 760GM-E51 8MG
ATI Radeon HD3000 on board
1 1 TB SATA drive - used to be windows, stopped working, overwritten with ubuntu
1 2 TB SATA drive - with little data on the drive.

I have run the memory test, and the disk test with no errors.

I can boot from the DVD.

d1weeb - obvious noob.....

---

### Post by snowpine on 2012-10-25
Welcome to the forums!

(edit: whoops, I failed basic reading comprehension, apologies!)

---

### Post by vandorjw on 2012-10-25
Since you have 2 hard-disks, make sure you are trying to boot from the correct one.
In the bios, there is usually an option to set boot priority.

--DVD
--HDD
--Boot from LAN/Ethernet

EDIT: Does F11 allow to select individual disks? or can you select harddisk vs DVD?

---

### Post by d1weeb on 2012-10-25
I have been using F11 to control the boots. I have not set it up in the BIOS yet since I can't get it to boot up correctly.

---

### Post by 2F4U on 2012-10-25
> 1. I how can I tell if the install finished, the who are you screen is the last screen I see?

When the installer is finished it will ask you to reboot.

> I have not set it up in the BIOS yet since I can't get it to boot up correctly.

Do you get any error message? If yes, please post it or a screen shot.

---

### Post by d1weeb on 2012-10-25
I do not get that message unless I choose to shut down the DVD version of the OS that is up and running.

I do not see nay error messages, all I have is blinking cursor.

---

### Post by d1weeb on 2012-10-25
The install process never asks me to reboot. When I shut down the DVD boot instance, I do see a message to remove the DVD, and continue with a reboot.

I do not see nay error messages, all I have is a blinking cursor.

---

### Post by howefield on 2012-10-25
> **d1weeb said:**
> I how can I tell if the install finished, the who are you screen is the last screen I see?

The last dialogue when install is complete should ask you whether you want to restart or continue.

Did you complete the "who are you" screens, seems that this is the part where you set your user details, eg name and password ect, install won't complete without this being done.

---

### Post by snowpine on 2012-10-25
A question that I honestly do not know the answer to:

Is the Ubuntu DVD from linuxidentity magazine the same as "regular" Ubuntu or is it something different? Does it have the same installer and steps/screens or it different/customized in some way?

---

### Post by vandorjw on 2012-10-25
Please have a look at this website, and tell us if the installation process looks the same.

[http://www.debianadmin.com/ubuntu-12-04-precise-installation-screenshots.html](http://www.debianadmin.com/ubuntu-12-04-precise-installation-screenshots.html)

and if it differs anywhere, let us know that as well.

**the screen-shots are not in order, on their website, but they are tagged/numbered**

The order they should be in is...

[http://www.debianadmin.com/wp-content/gallery/12-04int/ubuntu1.png](http://www.debianadmin.com/wp-content/gallery/12-04int/ubuntu1.png)
[http://www.debianadmin.com/wp-content/gallery/12-04int/ubuntu2.png](http://www.debianadmin.com/wp-content/gallery/12-04int/ubuntu2.png)
[http://www.debianadmin.com/wp-content/gallery/12-04int/ubuntu3.png](http://www.debianadmin.com/wp-content/gallery/12-04int/ubuntu3.png)
[http://www.debianadmin.com/wp-content/gallery/12-04int/ubuntu4.png](http://www.debianadmin.com/wp-content/gallery/12-04int/ubuntu4.png)
[http://www.debianadmin.com/wp-content/gallery/12-04int/ubuntu5.png](http://www.debianadmin.com/wp-content/gallery/12-04int/ubuntu5.png)
[http://www.debianadmin.com/wp-content/gallery/12-04int/ubuntu6.png](http://www.debianadmin.com/wp-content/gallery/12-04int/ubuntu6.png)

**you know the installation process completed when you see this one**
[http://www.debianadmin.com/wp-content/gallery/12-04int/ubuntu18.png](http://www.debianadmin.com/wp-content/gallery/12-04int/ubuntu18.png)

---

### Post by snowpine on 2012-10-25
Very helpful link, vandorjw! :)

---

### Post by d1weeb on 2012-10-25
I boot from the DVD, and unbuntu is then up and running, So I know that it can run on the box, I have internet through Firefox. One of the 4 icons on the desktop is install unbuntu. 

I never see screen 1, but do see screens 2 through 7, never see screens 8 or 9. I have tried a number of times including the last time where I used the F6 key to change to noquit nosplash, and turn on nomdest.

If I reboot from the DVD, I can see the drives and the folders/data loaded on the drive(s).

---

### Post by d1weeb on 2012-10-25
I am allowed to select either hard drive, the CD/DVD, or any of the 6 USB devices.


Can any one help?

---

### Post by vandorjw on 2012-10-25
Hey d1weeb, 

I was away for most of today.

Not seeing screen1 is fine, and not seeing 8 or 9 is fine as well. Those just advertise features of Ubuntu while waiting for the installation process to complete.

When going throught the install process, did you ever see ***screenshot-18?*** If you did not, then something has gone wrong during the install process.
If you did see this message, then everything installed correctly, (hopefully) and the problem is finding which hard-drive to boot from.

Also, on Screenshot4, when there should be a drop-down menu asking you which device you wish to install ubuntu on, I hope you are selecting one of your hard drives?


When you **restart your computer without the dvd** in the dvd-drive, what does your computer do?
Do you see a grub-menu? or does your computer say...

[COLOR="DarkOrange"]"Boot Device not found"[/COLOR]

---

### Post by d1weeb on 2012-10-26
I never saw screen shot 18. On at least one of my attempts I left the copying files screen up over night trying to make sure that all the data was copied. I did check the download updates check box.

Also in the current install I am not able to edit the /etc/default/grub file. It is only accessible by root, do I need to run a chmod command to change the privileges?

can I Burn a new install disc from the DVD booted version unbuntu?

Still lots of questions. 

I think the issue is the video drivers for the onboard ATI Radeon HD3000, does this seem correct? and would not using the nomodeset fix that?

No grub menu (even hitting the the shift key), nor do I see a message "Boot Device not found".


Still a n00b - d1weeb

---

### Post by Bucky Ball on 2012-10-26
*Thread moved to **Installation & Upgrades***

---

### Post by Bucky Ball on 2012-10-26
You need to be root to edit that, or most other, files in the terminal. Not a permissions things. You don't want to change permissions on that file anyhow.

---

### Post by d1weeb on 2012-10-28
Okay, so what do I need to do to get a working system booting from the hard drive. I am at a total loss, the install never finished, and the boot from disk brings me a blinking cursor?

---

### Post by vandorjw on 2012-10-28
This is what I would do in your case.

Open your computer and disconnect the 2TB sata drive. (Just remove the power going to it.)

Restart the installation from the beggining and don't do anything special.
Do not check, download updates. This can be done once we have a working system.

If you don't see the message screenshot 18 within 45minutes, then go here
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) and download the 64bit version of Ubuntu 12.04

Once the install does finish, before you hook your 2tb data drive back on, run
cat /etc/fstab just to make sure you see something like

```

UUID=23413asdf

```

and not 
```

[COLOR="Red"]#[/COLOR]UUID = asdfa23ea

```

The red '#' being bad if it is in front of UUID
[COLOR="DarkRed"]
I doubt the issue is with the ATI Radeon HD3000 because it is part of the R600 family, and as you can see here [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature), the R600/R700 family is almost working perfectly.[/COLOR]

The one thing that puzzles me is if you don't see grub, and you dont see, [COLOR="Red"]"Boot Device not found, please insert installation media and press any key to continue"[/COLOR], what does the computer do?
Do you instead see a black screen with a blinking white underscore in the top left corner?

---

### Post by snowpine on 2012-10-28
I think you may be onto something with your ATI Radeon theory. unfortunately I am not familiar with this hardware myself so I'd encourage you to follow some of the expert advice on these forums other than my own. :)

If that approach dead-ends, something you might try is to download the Ubuntu installer from here: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

And check md5sum of download: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

This will eliminate from the troubleshooting equation the possible variable that your linuxidentity magazine disk is somehow corrupt/defective. 

Also it can be fun to "distro hop" which means to try multiple options from distrowatch.com until you find one that "just works" flawlessly on your hardware. :)

---

### Post by d1weeb on 2012-10-28
Vandorjw

OK I will try that later today I hope.  I only see a flashing cursor in the upper left hand corner.

I am running AMD Phenom II CPU, is this the problem? Do I need the AMD version of ubuntu?

Snowpine,

It appears that I don't have access to my DVD drive at the present time, even though that is what I am booting from currently. What would be the easiest way to get a new version of unbuntu. Can I boot from an ISO file on a thumb drive?

---

### Post by Bucky Ball on 2012-10-28
AMD64 is for ALL 64bit machines, AMD and Intel. i386 32bit is for ALL 32bit machines.

If you have a 64bit processor you should be using the AMD64bit install.

---

### Post by d1weeb on 2012-10-29
I have a DVD from a magazine (ubuntu 12.04) that has both the 32 bit, and the 64 bit install on it, one on each side, is there an easy way to tell which is which if it were mislabeled?

---

### Post by d1weeb on 2012-11-03
OK I still need help.
Here is what I have done.
1. I have disconnected the second hard drive.
2. I have downloaded a new AMD64 ISO file, burnt a CD.
3. Tested teh disc dive again, no errors detected.

I still can't get any version get load past the "who are you" screen. 

I have tried at least 6 times. with different DVD's/CD's I have 2 CD's 1 burnt at high speed. One burnt at the lowest speed the machine I used could go.
 
I desperately need some guidance, but don't even know where to start.

Can some one help?

---

### Post by vandorjw on 2012-11-03
Alright, welcome to the world of frustration. By now, everything should already have been working under normal circumstances. You are unlucky.

I find it odd that the system just silently fails, without error messages.
One this website: [http://www.memtest86.com/](http://www.memtest86.com/) there is an ISO you should burn to disk to check your RAM.

The RAM check will take a solid hour or 2, just walk away, it'll do it multiple times if you let it keep going.

A while ago, I installed Ubuntu to a much older computer. The motherboard was a GA-8SIMLP rev2.1, and it just would not finish the install. RAM was fine, video card was fine, and I swaped multiple hard drives.
Eventually, I put one of the hard drives into another tower I had, and installed Ubuntu using that machine, and that time, the install finished without problems and worked like a charm.

So I took the hard drive out of the newer machine, and put with the older motherboard. That is when I discovered the IDE ports were broken.(I am not sure anymore how I tested this)

Computer components wear down and break overtime. If you have another computer desktop, you can install ubuntu using it. Just make sure to disconnect the hard drives, and put your own in.
Then, when and if the installation finishes, you can take the hard drives, and stick them back into your own computer.

If it still does not boot, then I recommend you get really angry. (I usually do)
Obtain a copy of windows, (anything, ranging from XP to win8 should do fine) and see it that installs.

PS: Ubuntu is not the only linux OS.

[http://www.debian.org/](http://www.debian.org/)

the ISO you would want is [http://cdimage.debian.org/cdimage/wheezy_di_beta3/amd64/iso-cd/debian-wheezy-DI-b3-amd64-netinst.iso](http://cdimage.debian.org/cdimage/wheezy_di_beta3/amd64/iso-cd/debian-wheezy-DI-b3-amd64-netinst.iso)

---

### Post by vandorjw on 2012-11-03
> **d1weeb said:**
> I have a DVD from a magazine (ubuntu 12.04) that has both the 32 bit, and the 64 bit install on it, one on each side, is there an easy way to tell which is which if it were mislabeled?

Yes, insert into a computer that you know is only 32bit machine. whichever side it boots from is the 32 bit side.

There is no way to know what is on a CD/DVD by looking at it with our eyes. 

If your computer is 64bit AMD, then it can read both 32 and 64 bit.
If it started a live desktop, press alt-F2 and type gnome-terminal

then type:

uname -a

if the output contains "x86_64" is is 64 bit

---

### Post by d1weeb on 2012-11-03
Sorry for all the time I took up, I had previously tried to install with out a password. The first time I use a password during the install, everything went normally. This is a home machine with multiple users. I will be looking into installing multiple users

Thanks for the help and pointers. I hope that this will help some one else

d1weeb.

---

### Post by Bucky Ball on 2012-11-04
Yep, that did waste a lot of time. Should have mentioned the password in the first post and we could have solved the issue very quickly as that is easily explained and executed. The main user (administrator/root) sets up user accounts for other users. *You need to install Ubuntu first* as you've consequently discovered. 

Glad it's solved but please try and include all important details in future. ;)

---

### Post by d1weeb on 2012-11-05
Yeah,
Again sorry, did not know taking an option that was presented was not a valid choice. Seems like  there was a mistake made. This is coming from a 32 year programmer......

Again sorry for the waste of time, just hope some else does not make the same mistake.

---

### Post by vandorjw on 2012-11-05
Glad to hear you solved the mystery. I didn't know that not setting a password was even possible. I'm going to look into this some more.

Dont worry about the time taken. I enjoy learning amd the best way to do so is by trying to solve other people's problems.

---

