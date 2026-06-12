---
title: "Ubuntu and Xubuntu on same hard drive"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by ArtF10 on 2007-08-22
I am trying to install Xubuntu and Ubuntu distros on the same HD, separately. I have 

/dev/sda5 Xubuntu /home
/dev/sda6 Swap
/dev/sda7 Xubuntu /

I want:
/dev/sda8 Ubuntu /home
/dev/sda9 Ubuntu /

Here's my question:
If I install Ubuntu, would I just use / for /dev/sda9 and /home for /dev/sda8 to get it TOO to show up in the same Grub bootloader as Xubuntu...separate from Xubuntu ofcourse?:confused:

PS: I know I can get Xubuntu from Ubuntu, but I just want them separate.:)

---

### Post by mocoloco on 2007-08-22
I don't know if it would be different installing two Ubuntu-based distros, but I've currently got Ubuntu and PC LinuxOS, and PCLOS did NOT detect or add Ubuntu to my grub list.
I would suggest you save a backup copy of your /boot/grub/menu.lst.  I would hope Ubuntu would recognize it's brethren, but just in case...
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.bak
```

My understanding is grub needs to know which root partition to look in for the grub menu list.  If it's not obvious which partition it's looking in or if you just want to be sure, you can boot from a liveCD and follow the procedure from [*this thread*]("http://ubuntuforums.org/showthread.php?t=224351") to restore grub and make sure it uses say /dev/sda7 or whichever you want.

---

### Post by plucky on 2007-08-22
I have been trying this out on a spare system. When the install finishes , the last install becomes the default boot distro. The GRUB menu doesn't distinguish between the distros i.e tell you it is UBUNTU or XBUNTU, you need to remember which partition each distro is installed.

I installed Xbuntu FF, Ubuntu FF , Ubuntu Edgy all on seperate partitions. Also Windows XP on the same disk. They were all bootable from GRUB.

Because the partitions were EXT3 they all showed up on the DESKTOP of each distribution, so were accessible in both XBUNTU and UBUNTU.

Good luck...

---

### Post by ArtF10 on 2007-08-22
> **plucky said:**
> I have been trying this out on a spare system. When the install finishes , the last install becomes the default boot distro. The GRUB menu doesn't distinguish between the distros i.e tell you it is UBUNTU or XBUNTU, you need to remember which partition each distro is installed.

But they ALL do show up in the Grub menu right?  I just want to be sure that I won't have to restore grub and get nowhere.  I just want to be able to select between the two from the same grub menu at startup.

All I will be doing when installing Ubuntu is specifying which /dev/sda to use for / and /home of Ubuntu.  Will this be sufficient to bring them all up in the Grub menu at startup?  Or am I going to need other commands?

---

### Post by plucky on 2007-08-22
Yes they are all in the Grub menu, they are just not identified as UBUNTU and XBUNTU but it shows the drive partitions ie sda1,sda2 etc.

---

### Post by ArtF10 on 2007-08-23
I tried this:

/dev/hda5 Ubuntu /
/dev/hda6 swap
/dev/hda7 Ubuntu /home
/dev/hda8 XUbuntu /
/dev/hda9 XUbuntu /home

Right after after installing XUbuntu, I was asked to restart and I got the correct Grub menu.  I selected Ubuntu.  After loading half way, a black screen full of text showed up saying that my /home folder could not be located and may be missing.  It loaded the X server and brought me to the login screen before the message showed up AGAIN.

Is there a way for me to correct this used GParted and retry the dual boot?  What am I missing?

I would really appreciate the help as I have spent way too much time tearing my hair out with every possible combination, I could think of, of the above.

---

### Post by s3a on 2007-08-23
There is a terminal command that you can have both Ubuntu and Xubuntu in the same partition! When the login menu (menu where password and user name is asked) you click on options and choose which distro you want to use! All this sounds great but, unfortunately, I do not know the command, but, I just wanted to let you know there is the possibility!

---

### Post by ArtF10 on 2007-08-23
> **s3a said:**
> There is a terminal command that you can have both Ubuntu and Xubuntu in the same partition! When the login menu (menu where password and user name is asked) you click on options and choose which distro you want to use! All this sounds great but, unfortunately, I do not know the command, but, I just wanted to let you know there is the possibility!

I think you mean download Xubuntu-desktop...but I want 2 separate installations.  You know around 10 days ago I got it but was totally new and had no clue what I was clicking on.

This is what I used (ALL on the same hard drive):
/dev/hda1   ext3     
/dev/hda3   ext3   
dev/hda2                      extended                 5.22 GB
       dev/hda6               linux-swap               2.14 GB
       dev/hda5               linux-swap               3.08 GB

I only later found out that there is no need for 2 swap partitions so since then I have been trying **[SIZE="4"][COLOR="Red"]IN VAIN[/COLOR][/SIZE]** to get them working with 1 swap.  Furthermore, I have been using extended partitions since then as opposed to primary partitions which worked above.  What's even more confusing is how I managed to get hda5 **BELOW** hda6.  I just installed Ubuntu, used Gparted to shrink hda1 and installed Xubuntu **SOMEHOW** by "shrinking" an existing swap....is this even possible?  I don't mind taking another shot at this but the problem NOW is that I have a working Ubuntu and DON'T want to re-partition whereas back then I didn't care about losing an odd hour or two **TRYING AND FAILING**.

If anyone can give me some advice it would really help.  It all seems so easy in principle....yet I've run out of options.

---

### Post by s3a on 2007-08-24
> **ArtF10 said:**
> I think you mean download Xubuntu-desktop...but I want 2 separate installations.  You know around 10 days ago I got it but was totally new and had no clue what I was clicking on.

This is what I used (ALL on the same hard drive):
/dev/hda1   ext3     
/dev/hda3   ext3   
dev/hda2                      extended                 5.22 GB
       dev/hda6               linux-swap               2.14 GB
       dev/hda5               linux-swap               3.08 GB

I only later found out that there is no need for 2 swap partitions so since then I have been trying **[SIZE="4"][COLOR="Red"]IN VAIN[/COLOR][/SIZE]** to get them working with 1 swap.  Furthermore, I have been using extended partitions since then as opposed to primary partitions which worked above.  What's even more confusing is how I managed to get hda5 **BELOW** hda6.  I just installed Ubuntu, used Gparted to shrink hda1 and installed Xubuntu **SOMEHOW** by "shrinking" an existing swap....is this even possible?  I don't mind taking another shot at this but the problem NOW is that I have a working Ubuntu and DON'T want to re-partition whereas back then I didn't care about losing an odd hour or two **TRYING AND FAILING**.

If anyone can give me some advice it would really help.  It all seems so easy in principle....yet I've run out of options.
To my knowledge, that terminal code installs the xfce AND the apps of Xubuntu. Private message Ubuntu forums user "borris.morris", he should be able to help you as I heard that from him! If this code helps/helped you with your situation, post the code onto this thread.

Bassically, to my knowledge, you insert the Xubuntu CD and type a command and it installs it alongside your current distro.

---

### Post by ArtF10 on 2007-08-24
Sorry yeah, thath's what I meant....the xfce desktop and apps.  I've done that before and would like them totally separated this time.

Nonetheless, I will send Borris a mesage.

---

