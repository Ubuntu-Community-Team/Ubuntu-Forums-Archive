---
title: "A little reluctant to install Ubuntu again"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by rockinruler on 2011-03-04
Hello everyone,

This is my first post here.

So the thing is, I'd installed Win7+Ubuntu 10.4 on my desktop earlier, which was upgraded to 10.10 later and was working fine for a couple of days, and then one day out of the blue, when I wanted to boot to Windows, it wouldn't boot. Started giving me some error.

So I inserted the Win 7 disk and repaired the bootloader from DOS. 

Now, the Win 7 bootloader had become the default one and the Ubuntu option there wouldn't work and give me this error :
> Windows failed to start. A recent hardware or software change might be the cause. To fix this problem :

1. Insert your windows installation disc and restart your computer
2. Choose your language settings and then click next
3. Repair your computer


File : \ubuntu\winboot\wubildr.mbr

Status : 0xc0000225

Info : The select entry could not be loaded because the application is missing or corrupt.

I tried various things from the internet to fix it, but all in vain. Finally had to format the ubuntu partition and get the entry out of windows's bootloader


Now I've got a new laptop with Win 7 preloaded, and I'm considering installing Ubuntu on it too, but I'm a tad reluctant because of my prior experience, and numerous other problems that I see on the forums that people keep having with their dual boot systems.
[U]
So just wanted to ask this one thing, are such problems with a dual boot setup very frequent and common, even for the gurus over here, or it's us, the laymen who screw it up unintentionally?[/U]

PS : Thanks for looking, and sorry for the rambling - just wanted to be definitive about my reluctance :)

---

### Post by ~!geek!~ on 2011-03-04
While upgrading ubuntu,  few people have had problems. No comments about that. 
But there should not be any problem with having a dual boot system. 
**One important note:** New laptops generally come with pre-loaded os. Either the company provide a dvd to reinstall system back or they provide you with a separate partition and suggest you to make a disk to recover your system back to the state the company provided you with. First thing first, follow it. 
Once you have "the disk", you should not worry about System crash because you can revert back whenever you want. 
I hope it helps.

BTW, if you are having dell laptop with windows pre-installed on it, first thing, create the disk to recover your system already provided by them and second, please remove some softwares provided by dell like dell backup etc. They become unhappy when something like grub try to control the system.

---

### Post by coffeecat on 2011-03-04
Yours was not a conventional dual-boot installation of Ubuntu and you did not have a dedicated Ubuntu partition. You had a Wubi installation which is quite a different matter. Wubi is a way of trying out Ubuntu by creating a *virtual* partition for Ubuntu within the Windows C: partition. See these two links for more:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29)

Most people do not have problems with conventional dual-boots. Don't go by the frequency of threads where people post problems. After all, people without problems do not start help threads! :)

If you want to try a proper dual-boot with your new machine, just ask and people will help.

The broken Wubi in the desktop should be easily fixed and I'll see if I can find a link for you. You experienced difficulty in finding relevant information because of the confusion between wubi and a conventional dual-boot. I guess most of the stuff you found was for a dual-boot and that would have been quite bewildering.

---

### Post by Rubi1200 on 2011-03-04
Hi and welcome to the forums rockinruler :)

coffeecat asked me to jump in and offer some solutions, but first we need some information about the current state of the system.

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Next, if you used the default options when installing Wubi, please check if the following files are at the root of the C drive; wubildr and wubildr.mbr

Thanks.

---

### Post by rockinruler on 2011-03-04
Geek, I own an Acer laptop. And I've already burnt the recovery discs. Thanks for the heads up though :)

Coffeecat, I'm not entirely sure, but I think I did have a separate installation on a different partition. Correct me if I'm wrong, when you install Ubuntu using Wubi, after the installation the default bootloader stays the Windows's one, but as I mentioned, after the installation the Linux bootloader would initially come up.
> 
After all, people without problems do not start help threads! 

Golden words! =D>

Rubi, thank you :) And I really appreciate the help, but as I said, I had to format my partition and removed the Ubuntu entry from my bootloader too.

All of your replies have been reassuring, thanks for that. I'll make a new partition on my laptop and install Ubuntu again whenever I find the time.
Thanks for looking in guys. I look forward to learn a lot of things from these forums :)

---

### Post by Rubi1200 on 2011-03-04
If you ever need help, this is the place to come to.

Good luck :)

---

