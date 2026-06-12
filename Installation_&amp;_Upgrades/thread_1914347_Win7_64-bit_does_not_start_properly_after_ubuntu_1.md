---
title: "Win7 64-bit does not start properly after ubuntu 10.04 is installed"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by firatoter on 2012-01-24
SORRY FOR THE LONG POST, BUT PLEASE READ & HELP!!

Hello,

I am a win7 64-bit user and yesterday I wanted to try Ubuntu. Since 10.04 32-bit version is indicated as a more stable one, I chose that and burnt the installation file to a cd. Before the installation, I checked out the forums about side-by-side / duel booth installation tips and guides and it was indicated that disk partitioning is a bit of problem, so before the installation, I went to "disk manager" from windows and reshaped a completely empty disk of "380 GB which was primary" as "230 GB primary" and "150 GB unallocated". Then I put in my cd then rebooted and started the installation process. In the installation steps, I chose the option "use the longest continuous free space" and that option showed me the "150 GB unallocated space" to be the installation area, which I have created beforehand. (In the step, that area was showed as not exactly 150GB but 157GB, however I did not care; it may help if it is an important information about my problem). Then I accepted that option and Ubuntu was installed.

Up to here, there seems to be no problem. My computer is ASUS NX90SN, which is a very recent model with Nvidia GT 540M, which I still can not make it work properly. Ubuntu simply does not recognize it. However such hardware recognition and driver malfunction issues are not my main problem.

Up to here may help you to advise me properly, so included everything I find important.

So lets start the main problem: 

I tried Ubuntu a little while, was dissapointed due to driver issues and then decided to boot back to windows, so I restarted. From the boot menu, I chose "Windows Vista" option because there are no other option that can be related to my real win7 os. 

Then a screen comes up with a loading bar and an indication "Windows files are loading" and then original Win7 starting takes place. However after the screen which is black, where win7 logo is shining, my windows desktop takes place with nothing on it, no login screen is displayed at the first place. The desktop shows nothing on it except the wallpaper, which is the default wallpaper when I first bought my computer, not the final one before installing ubuntu, and resolution is set to a very low one, which I understand from the very big cursor size. Then, after a few seconds on the empty desktop, computer restarts automatically. I tried several times and it happened all the time. 

I created a Recovery Disk from another computer that have also a 64-bit windows. Then I booted from CD, chose "repair startup", it reparied but nothing changed. Then using command prompt from the recovery table, I entered "bootsect /nt60 ALL" command without quotations in order to restore the windows 7 booter, and it did it successfully, however nothing changed again.

To say so, I tried a bit of things, but my problem still exists. W&#304;ndows boots, but not successfully and restarts from an empty desktop, which I shouldn't see without passing the login screen at the first place.

So please help me, I read tons of articles, forum entries etc. but couldn't find a proper answer for me. 

Also if you inform me about the best version of Ubuntu for my ASUS NX90SN I would be very pleased, which will be able to recognize my hardware and find proper drivers for them properly functioning.

Thanks to everyone!!

---

### Post by nipunshakya on 2012-01-24
In my view, i think the problem may be installing a 32-bit architecture alongside a 64-bit architecture.
Also there has been reported issues with latest NVIDIA graphics card not being able to function well in ubuntu, but i don't know about windows. 

A quick question...did u reboot to windows after u shrunk the disk space from 380 to 230 gb? i assume positively that you did that, because thats important for windows to realize that it is comfortable with the recent partitions you have made, and act accordingly to it..so did u reboot to windows after rearranging your partitions?

---

### Post by firatoter on 2012-01-24
Thanks for your attention,

I did not boot after the partitioning I guess. What may be the problem?

---

### Post by nipunshakya on 2012-01-24
After you make changes to the way windows has partitioned your machine(like you did by shrinking the spaces), a next reboot runs a check disk by windows on startup, to again reallocate the partitions that are modified, and acts accordingly. Though you were successful to install ubuntu and use it, windows still was not able to properly adjust itself to the environment you created in it. So basically i found those issues with your system as i mentioned earlier:
a. You did a 64-bit and 32-bit installation side by side
b. Your windows didn't adjust itself after the partitions....

Well, when i first migrated from windows to dual-boot machine, i had same issue...I didn't know about this forum back then, and so ended up with a reformat of both OSs. 
I dont suggest you to do the same as i did,but i think you need to make a grub repair once.Try that and see if you succeed. Goodluck

Regards,WinuxUser

---

### Post by firatoter on 2012-01-24
Something amazing happened! I don't know how it happened, but I restarted from Ubuntu because of an update and on the boot screen, I finally saw a "Windows 7" option below the "Vista" Option and chose that. Then a "Disk Repair" screen appeared that checked my both hard drives and found no problem. Then Windows 7 successfully booted, no file missing,and partitioning seem to be done perfectly.

The "Computer Management -> Disc Management" shows the partitioned space for Ubuntu in two parts: one is 140GB and other is 6GB both primary and all parts are healthy. 

So, now I am in Windows 7 with no problem with new questions in my mind:

1- Why do I have a "Windows Vista" option in the boot menu, even Vista is not installed?

2- Why instantly "Windows 7" option showed itself?

3- Is the booting problem solved, or may I encounter another one from now on while booting to Windows 7 or Ubuntu?

4- Will it be better to uninstall Ubuntu now and install Wubi or something, or my computer has managed to work them side-by-side from now on?

5- Is there any version better than 10.04 for my laptop, which is new, at which I can find a running driver for my Nvidia GT 540M with Optimus technology?

That's all for now. Thanks for your help!

---

### Post by nipunshakya on 2012-01-24
> **firatoter said:**
> Something amazing happened! I don't know how it happened, but I restarted from Ubuntu because of an update and on the boot screen, I finally saw a "Windows 7" option below the "Vista" Option and chose that. Then a "Disk Repair" screen appeared that checked my both hard drives and found no problem. Then Windows 7 successfully booted, no file missing,and partitioning seem to be done perfectly.

The "Computer Management -> Disc Management" shows the partitioned space for Ubuntu in two parts: one is 140GB and other is 6GB both primary and all parts are healthy. 

So, now I am in Windows 7 with no problem with new questions in my mind:

1- Why do I have a "Windows Vista" option in the boot menu, even Vista is not installed?

2- Why instantly "Windows 7" option showed itself?

3- Is the booting problem solved, or may I encounter another one from now on while booting to Windows 7 or Ubuntu?

4- Will it be better to uninstall Ubuntu now and install Wubi or something, or my computer has managed to work them side-by-side from now on?

5- Is there any version better than 10.04 for my laptop, which is new, at which I can find a running driver for my Nvidia GT 540M with Optimus technology?

That's all for now. Thanks for your help!
your answers:
1- Thats because your grub might be out of date and the update in ubuntu fixed it.
2- The update in ubuntu might have updated the grub too and that caused addition of the real entry(windows 7 ) to the grub menu.Thats why i had said u earlier to update your grub and fix it. :)
3- For the time being, your problem of startup is fixed.
4- I don't recommend ubuntu as wubi installation Following are the limitations of wubi as from wikipaedia:
Compared with a regular installation, a Wubi installation faces some  limitations. Hibernation is not supported and the filesystem is more  vulnerable to [hard reboots]("http://en.wikipedia.org/wiki/Rebooting_%28computing%29#Hard_reboot").  Also, if the Windows drive is unmounted uncleanly (Windows crash, power  failure, etc.), Ubuntu will not be able to mount the Windows drive and  boot until Windows has successfully booted and shut down. If the Windows  system cannot be booted after the crash, the user also cannot boot  Ubuntu.
 Performance related to hard-disk access is also slightly slower, more  so if the disk image file is fragmented, on a Wubi install compared to a  normal one
So i don't advice wubi.
5-there is a stable version of ubuntu 12.04 which is goin to be released in april. i recommend you wait for it. When it releases, u surely can make a fresh installation of it. Till then learn more on current ubuntu. Many people have reported issues of NVIDIA graphics too, some solved and some unsolved.

Glad that ubuntu's update saved your day. 

Happy Linuxing
Regards,WinuxUser

---

### Post by firatoter on 2012-01-24
Thanks for your additional information. 

Yes, the broblem seems to be a Grub malfunctioning and the update of it may have solved the issue. 

I am going with BumbleBee 3.0 to solve the Nvidia Issue. Download link is below:

"https://wiki.ubuntu.com/Bumblebee"

It may solve the graphic issues, since it is created especially for Optimus technology.

Thanks for everything! Have a nice day.

---

### Post by nipunshakya on 2012-01-24
U too have a nice day...Goodluck with your graphics issue. Hope it gets solved.Goodluck

Regards,WinuxUser

---

