---
title: "Windows7 dual boot troubles"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by pinbill on 2010-10-09
Hello All-

I just installed ubuntu on a windows7 toshiba laptop. When installing I chose to install ubunu side by side with windows7, both operating systems work fine, boot up well with no problems except the ubuntu desktop has 206mb of memory. How do I set it up so that I have more memory available for ubuntu than windows7? Thanks for any ideas, 

Bill

---

### Post by presence1960 on 2010-10-09
I believe you are using terms incorrectly...when you say memory you are probably referring to hard disk space. Let me know if that is the case. memory refers to RAM.

---

### Post by pinbill on 2010-10-09
yes, thanks for the correction I am referring to hard disc space. I would like to have the majority of space for ubuntu which will be my primary system. the hard disc has 500 gigs.

Thanks,

Bill

---

### Post by presence1960 on 2010-10-09
> **pinbill said:**
> yes, thanks for the correction I am referring to hard disc space. I would like to have the majority of space for ubuntu which will be my primary system. the hard disc has 500 gigs.

Thanks,

Bill

Ok, I need more info. 


Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by pinbill on 2010-10-09
I could not boot from installation cd, so I installed ubuntu from windows desktop using the file directly downloaded to my computer. I can get onto the installed ubuntu system and run that command but I can't do it from the boot cd. Also I am not able to connect to the internet in ubuntu only in windows, my wired connection is not working so I can't get the updates for my wireless. I am a mess, I hope you can help. Thanks for your time,

Bill

---

### Post by presence1960 on 2010-10-09
> **pinbill said:**
> I could not boot from installation cd, so I installed ubuntu from windows desktop using the file directly downloaded to my computer. I can get onto the installed ubuntu system and run that command but I can't do it from the boot cd.

Sorry pinbill. I know very little about wubi, which is the method you used to install ubuntu. 

I am quite adept at full dedicated installations of linux . I think it best for me to refrain and you should wait until someone who uses wubi comes along to help.

---

### Post by pinbill on 2010-10-09
In your opinion, would i be better off using a fully dedicated installation of ubuntu rather than wubi?

---

### Post by presence1960 on 2010-10-09
> **pinbill said:**
> In your opinion, would i be better off using a fully dedicated installation of ubuntu rather than wubi?

Either way will work. I prefer a dedicated installation of linux. bear in mind that my opinion may start a controversy- which is not my intention. My intention is to help you. If you find wubi easier then by all means go ahead and use it.

Should you opt to go with a dedicated install you will have to find out why you can't boot from CD/DVD, as you will have to do so in order to install, unless your machine is capable of booting from USB/Flash disks in which case you can make a bootable one of those.

Again my response is not intended to elicit a debate on whether wubi or a dedicated install is better. Just trying to help pinbill.

---

### Post by pinbill on 2010-10-09
Ok, I have decided to reinstall ubuntu from the cd, I have the cd ready to rock, but have no idea how to manually prepare the partitions, could someone help walk me through this. I am in over my head creating partitions and want to do it right. 


Thanks for all your help, 

Bill

---

### Post by Mark Phelps on 2010-10-10
> **pinbill said:**
> Ok, I have decided to reinstall ubuntu from the cd, I have the cd ready to rock, but have no idea how to manually prepare the partitions, could someone help walk me through this. I am in over my head creating partitions and want to do it right. 


Thanks for all your help, 

Bill

Do NOT, repeat NOT, use the Ubuntu installer to shrink the Win7 OS partition as that is asking for trouble.

BEFORE you do anything else, play it safe by launching the Win7 Backup feature and selecting the option to create and burn a Win7 Repair CD.  You will need this later if anything goes wrong during the dual-boot setup.

While in Win7, also use the Disk Management utility to shrink the OS partition down.  I would suggest shrinking it by 30GB (if you can) and do NOT format the resulting unallocated space. Leave it as is.

Then, boot into the Ubuntu CD, choose the "largest free space" option and allow it to format the space.

---

### Post by pinbill on 2010-10-10
Thanks for the reply, please excuse my lack of computer knowledge. I made a set of system recovery discs when I first set up the computer are they the same as a Win7 system repair disc?

 Also, when I shrink the OS partition, does that mean Windows will have 30GB to work with and then Ubuntu will have the remaining 450 something GB to use?

Thanks a lot for all the help,

Bill

---

### Post by pinbill on 2010-10-10
Win7 Repair Disc created! Starting to shrink Win7 partition.

---

### Post by wilee-nilee on 2010-10-10
I think they meant start with 30 gigs for Ubuntu, using the disc manager in W7. The disc manager will look at the partition first and then tell you how small it can be made. To have the disc manager look at the specific partition just right click on it and look at the drop down it is pretty straight forward.

You might post a snip/sceenshot of the disc manager or gparted the linux partitioner.

We posted at the same time it looks like your on your way.;)

---

### Post by pinbill on 2010-10-10
I don't know how to copy a picture that I can post, but here is the info

Disc0 465.76GB Online  

1.46GB Healthy (Active, Recovery Partition) 
c: 450.65GB NTFS Healthy (boot, page file, crash dump, primary partition)
2.33GB Healthy (primary partiton)
165 MB Healthy (primary partition)
11.15 Healthy (primary partition)   



The shrink C: window results were as follows:

Total size before shrink in MB  461465
Size of available shrink space in MB   217243
Enter amount of space to shrink in MB  217243
Total size after shrink in MB   244222


Any advice on where I should I go from here? What are all those other partitions for? Can I get rid of them?

Thanks,

Bill

---

### Post by wilee-nilee on 2010-10-10
Boot the live Ubuntu cd open gparted, go to take screenshot in accessories choose select area to grab run the cross diagonally across gparted and post the picture. 

If you don't know how to post the picture you start at the reply widow and click on the paperclip upload the image then the image is under the paperclip to add when clicked on.

W7 has a similar tool called snip or snippet it is in accessories, you want to know how to use them, for ease of travel.

Don't delete any partitions yet some may contain the recovery and booting files.

---

### Post by pinbill on 2010-10-10
Amazing, that snippet deal is great! I can take one of the ubuntu partition device also,

Bill

---

### Post by waznot on 2010-10-10
Hi pinbill
I am following how you go here as I have my eye on a Toshiba I want to buy. So could I ask what model you have, or the specs?

---

### Post by wilee-nilee on 2010-10-10
That is great, it is helpful for me to see the partitioner. I think presence1960 or Mark Phelps, who are both quite knowledgeable might be more helpful. There are other users as well.

It does look like you will have to remove one partition to get a extended in for Ubuntu. But you want to do this with help from someone who is familiar with what your set up is.

The picture you posted looks as though you haven't resized yet that is actually good if this is the case. The W7 disc manger will do that in about 3 minutes when you get your plan all set. If you have resized and the gparted picture looks different post that.

---

### Post by pinbill on 2010-10-10
Ok here is the info from the ubuntu partitioner. It looks like one partition is an old ubuntu installation. I am thinking I need to get rid of that, can I delete the windows vista loader partition also? Any suggestions would be great, thanks,
 
Bill

---

### Post by pinbill on 2010-10-10
it is a satalite a665 with the i3 processor

---

### Post by wilee-nilee on 2010-10-10
Actually that is the install partitioner don't use it for any resizing of W7.

This is gparted it is in the admin menu.
[ATTACH]171904[/ATTACH]

---

### Post by presence1960 on 2010-10-10
> **wilee-nilee said:**
> Actually that is the install partitioner don't use it for any resizing of W7.

This is gparted it is in the admin menu.
[ATTACH]171904[/ATTACH]

pinbill, boot the Live CD to the desktop then go System > Adminstration > gparted

---

### Post by fabs001 on 2010-10-10
hi every one, I’m trying to install the 10.10 but i made a few mistakes sooooo.... now i have installed the 10.10 but i don’t have any more a load menu at beginning it goes straigt to ubuntu the partition were w7 was still there, but maybe i killed the loader... im trying to reinstall the 10.10 but im not sure what is going wrong now i receive an erro saying  to specify the root file or something. is there any way of installing witout wiping w7 away need it for my iphone and some other sortware. i cant acces it now, i can see the files allrigh but not loading it.

---

### Post by presence1960 on 2010-10-10
> **fabs001 said:**
> hi every one, I’m trying to install the 10.10 but i made a few mistakes sooooo.... now i have installed the 10.10 but i don’t have any more a load menu at beginning it goes straigt to ubuntu the partition were w7 was still there, but maybe i killed the loader... im trying to reinstall the 10.10 but im not sure what is going wrong now i receive an erro saying  to specify the root file or something. is there any way of installing witout wiping w7 away need it for my iphone and some other sortware. i cant acces it now, i can see the files allrigh but not loading it.

It is suggested you start your own thread. Not for anything but it is easier to try to help one person at a time. it can get confusing to say the least, especially since your issues may be quite different than those we are dealing with in this thread.

---

### Post by fabs001 on 2010-10-10
yeah no prob thank you

---

### Post by wilee-nilee on 2010-10-10
> **fabs001 said:**
> hi every one, I’m trying to install the 10.10 but i made a few mistakes sooooo.... now i have installed the 10.10 but i don’t have any more a load menu at beginning it goes straigt to ubuntu the partition were w7 was still there, but maybe i killed the loader... im trying to reinstall the 10.10 but im not sure what is going wrong now i receive an erro saying  to specify the root file or something. is there any way of installing witout wiping w7 away need it for my iphone and some other sortware. i cant acces it now, i can see the files allrigh but not loading it.

You will need to start your own thread for the best help.;) Post the bootscript in my signature in your own thread, this will get things moving.

---

### Post by presence1960 on 2010-10-10
> **wilee-nilee said:**
> you will need to start your own thread for the best help.;) post the bootscript in my signature in your own thread, this will get things moving.

+1

---

### Post by pinbill on 2010-10-10
Alright, here we go. This is the snapshot from gparted.

---

### Post by wilee-nilee on 2010-10-11
You have several choices. First since you have Ubuntu installed and can boot into W7 shrink it=C accordingly from there with the W7 disc manager.

You then will have some open space, and it will be okay to leave the other W7 assoc partitions as is they are important.

So you can can either using gparted from the live cd after turning off the swap-right click swap partition and then swap off. You can either expand the extended then the logical and rebuild the swap to your liking, or just delete those Ubuntu partitions the extended, logical, and swap. Then just close gparted and install to the free space left. 

I would do the delete the Ubuntu partitions and reinstall, the expanding of the ones you have will take a little longer, but do what you feel comfortable with. If you expand them you will probably just have to reload grub2 to the mbr, and mount to boot Ubuntu to get the grub2 bootloader in order.

---

### Post by pinbill on 2010-10-12
ubuntu 10.4 installed and working good so far, although I could not get the wired connection to work in ubuntu, i tried to get it working in windows7 but couldn't get it working there either. I have no idea if the port is even good. i know this is the wrong forum location, but any ideas on how to get connected through eithernet.
 
Thanks again for all your help with this dual boot thing.....i'm psyched!

---

### Post by wilee-nilee on 2010-10-12
> **pinbill said:**
> ubuntu 10.4 installed and working good so far, although I could not get the wired connection to work in ubuntu, i tried to get it working in windows7 but couldn't get it working there either. I have no idea if the port is even good. i know this is the wrong forum location, but any ideas on how to get connected through eithernet.
 
Thanks again for all your help with this dual boot thing.....i'm psyched!

If your ethernet port has broken, mine did I got a ethernet to usb convertor for like 5$ US on Amazon.

It may be a driver is needed but both not working sounds like a bios update might be needed, or the port is broken, hard to say.

So I assume you have modified your partitions to have a larger Ubuntu.;)

---

### Post by pinbill on 2010-10-12
yes, i shrank windiows7 and installed ubuntu to the largerst free space, and it works well. thank you, 
 
do you know how to check to see if the ethernet port is busted, download bios, or check for drivers?
 
if it ends up being the port i can return the machine it is almost new,
 
thanks,
 
bill

---

### Post by wilee-nilee on 2010-10-12
> **pinbill said:**
> yes, i shrank windiows7 and installed ubuntu to the largerst free space, and it works well. thank you, 
 
do you know how to check to see if the ethernet port is busted, download bios, or check for drivers?
 
if it ends up being the port i can return the machine it is almost new,
 
thanks,
 
bill

My laptop with the broken ethernet port has a little light on each side in the plugin area, this is the light for transmitting the data. On one side of the port it is green the other yellow when plugged in. I figured out mine was broken due to having multiple computer and just using a known working ethernet cord that works on one computer then trying it in the other. The lights on the ethernet port I believe should both be green.

I would return it if needed, chances are though that adding Ubuntu a 3rd party might have the manufacturer flinch or balk so be prepared for just having W7 on it for repairs or service. With my acer netbook they wouldn't touch it due to a upgrade from XP to W7 and multiple open source setups. In order to get it fixed I had to reload the XP oem, I just left it broken as I have a usb converter.

---

