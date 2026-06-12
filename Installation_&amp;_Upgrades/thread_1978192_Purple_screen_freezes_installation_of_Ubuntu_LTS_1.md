---
title: "Purple screen freezes installation of Ubuntu LTS 12.0.4 on my HP Pavilion dv6-3016AX"
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by gilo75 on 2012-05-11
I tried to install for the first time Ubuntu on my HP Pavilion dv6-3016AX.

I was given Ubuntu 12.0.4 on a USB drive made bootable (note the same USB drive was used for another instalaltion which was successful. Also it is the 64bit version.)

I booted my laptop from the USB drive (Esc -> F9) and followed the wizard. After connecting to my wireless network I came to the selection of installation type to follow and for laziness I choose to "Install Ubuntu inside Windows 7". 
As soon as I hit forward my laptop reboots and loads the dual boot. After selecting Ubuntu and hitting the enter key, the laptop screen goes purple (with irregular vertical black stripes) and everything freezes including the installation.

The only thing I can do is to hold the power button and force the computer to shut-down.

I repeated this several times and every time it freezes and cannot complete the installation. I am reluctant in partitioning the drive manually as I fear it is an issue related to the graphics processor and the issue would reoccur.

Did anyone have the same problem? can anyone help?

Thanks

---

### Post by darkod on 2012-05-11
Don't plug in the usb stick while running windows.

Boot with the stick and select Try Ubuntu first. Does that load the desktop correctly?

If it still gets stuck, you can test if it's video driver issue. Boot with the stick and at the firsl purple screen hit Esc. That should show the older style main menu.

Hit F6 for advanced options. Select nomodeset. Select Try Ubuntu from the main menu.

Does that load the desktop correctly?

---

### Post by gilo75 on 2012-05-11
Thanks Darko.

Yes I didn't run the stick from windows but i booted from the stick.

I tried again and followed your advise , i selected Try Ubuntu and yes it does load the laptop correctly.

I guess I can exclude the video driver issue.

What could it be then? Could it just simply be that the USB drive got corrupted while making it bootable?

Is it worth downloading ubuntu again and make it bootable from a cd?

Thanks hips for your help

---

### Post by jadtech on 2012-05-11
if your first choice was ubuntu inside of windows you were trying to install  ubuntu as a windows program some of the issues could be a problem with windows its self ..

if you still want to install  ubuntu this way  that is all good how ever you might want to defrag windows and  run chkdsk a few times to try and and eliminate hard drive bad spots and such ..

also just to be sure is that a 64bit processor ??? you cant install 64bit image on a 32bit system ..

---

### Post by darkod on 2012-05-11
I would recommend a dual boot install over wubi anyway. The final decision is yours.

If you do decide to install a dual boot on separate partition, you have to take into account that HP usually ships laptops with all 4 primary partitions used. You will have to delete at least one (the HP_TOOLS for example) so that the ubuntu partitions can be created.

That would allow the ubuntu installer to create partitions but you still need space for them because now the whole disk is taken by windows. You will have to use windows Disk Management and shrink the windows partition for as much as you want to allocate to ubuntu. Do this only with Disk Management, it's better. DO NOT create any partitions for ubuntu from windows, leave the space as unpartitioned. Restart windows few times after that, sometimes it wants to do some checks after the shrink.

Only then boot with the usb and start the install. The installer will automatically use the free unallocated space.

Also, you might wanna consider creating a set of recovery DVDs and delete the recovery partition too. If you ever want to restore to factory state, you can use the DVDs. That way, not only that you delete one primary partition that you don't really need, more importantly you can use the space it takes which is approx 15-18GB instead of sitting there useless.

---

### Post by jadtech on 2012-05-11
my confusion is this   the spec claim this processor though it is dual core on lap tops as a cheap solution for speed and power control one core is deactivated   some say it is 64bit supported though does this make them 64bit machines or 32bit with 64bit suport

---

### Post by gilo75 on 2012-05-16
Sorry for theblate reply but tahnk you fornyour avdise.  I didn't realise that I was trying to install ubuntu within windows.... Now that makes kind of sense. i will definetely create a new partition and install ubuntu as dual boot. Thanks fro the tip with partitioning. I won't need to delete the current partitions as My hdd is big enough. I will create a new ext partition and use it. Hopefully ubuntu will recognise it automatically.
Cheers for your help.

---

### Post by darkod on 2012-05-16
No problem, just have in mind what I mentioned about the 4 partitions limit. If all 4 partitions are used up, it doesn't matter how much unallocated space you have on the disk, you can't create a 5th partition.

Open Disk Management in windows and it will show all partitions, unlike Computer which only shows some. So you might have more than you think. :)

---

