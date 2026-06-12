---
title: "Help with Dual-Booting Vista and Ubuntu Studio with Vista installed first"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by frank.zappa on 2007-10-11
Hello everybody, here's the situation.

When I had first gotten my laptop, pre-installed with Windows Vista Home Premium, I had tried dual-booting Vista with Ubuntu Studio 7.04, which I had downloaded before. I had no problems during the setup and I had chose to install the GRUB boot loader on the disk. I had finished the installation and then rebooted the computer. I first tried booting Vista, but GRUB couldn't find the boot files and said something like GRUB error 22, I think. Ubuntu Studio would boot but it would hang at the loading page - the page with all the cool colours. I then had to do a clean install of Vista and never tried to install Ubuntu again.

My first question is, is there a way I can dual-boot Vista and Ubuntu Studio, but choose not to install the GRUB boot loader? I currently have Vista dual booted with XP and for that I used a program called EasyBCD to add the Windows XP option to Vista's boot loader. The program also has options for adding Linux and  BSD OS's to the Vista boot loader. I actually just re-read the Linux part and it says "The boot loader must be installed to the bootsector of the partition!". It's also got another thing called NeoGrub and says "If you don't have Grub or LILO already installed to the bootsector, you can use the NeoGrub Loader to boot into Linux, SkyOS, or BSD from Windows."

My second question is about the swap partition that is needed for the Ubuntu install. I have a 200GB hard drive with 90GB for my Vista, 75GB NTFS partition that's just empty (used to be 90 but used 15GB for XP), and 15GB for XP. I keep the 75GB partition as either extra for my XP, if needed, or to temporarily store files for Vista. My computer has 2GB of RAM, but I'm not sure how much I should use for the swap file. And if someone could explain what the purpose of this is. I think last time I chose to install Ubuntu as a "logical drive" or something. 

I would appreciate if someone who is more than an average user could guide me in the right direction on how to dual boot these systems. Just a reminder, I want to be able to boot Linux from the Vista boot loader menu, and NOT use GRUB. I don't want to have to re-install Vista and restore 40GB of data - I don't even have an external hard drive, just CD's and DVD's so it's a huge pain.

Thanks a lot

p.s. Sorry for the length of the post, but I just want to be exact and try not to leave any room for mistakes.

---

### Post by logos34 on 2007-10-11
Since you already have 3 primary partitions (limit 4) you'll have to create an **extended** partition (out of space freed up after shrinking, say, the 75GB ntfs partition), and place / and /swap inside as **logical** partitions.  

With that amount of ram you'll probably never use the swap, but 1-2 GB should be fine.

[https://help.ubuntu.com/community/SwapFaq?highlight](https://help.ubuntu.com/community/SwapFaq?highlight)
[http://en.wikipedia.org/wiki/Swap_space](http://en.wikipedia.org/wiki/Swap_space)

If you use the ubuntu live cd, when you come to the **'Ready to Install'** screen, click on **'Advanced'** button lower right and tell Grub to install to the bootsector of the linux root partition (hd0,x), NOT the mbr (hd0).  So, for instance, if root is on the second logical partition inside the extended (i.e. sda6), then you would enter (hd0,5)--grub counts from 0 not 1.

Then add ubuntu to Vista boot menu using EasyBCD

---

### Post by frank.zappa on 2007-10-12
Wait, so you're saying I'm only allowed to have 4 partitions on my hard drive? And by extend, do you mean that I should shrink my 75GB partition into a, say maybe 15GB and then use that to install Ubuntu? I also can't remember, but do I have to make a seperate partition for the swap? Last time I think I allocated 512MB for the swap and,I'm not sure if it was because of this but Ubuntu Studio wouldn't even load the user screen, it would just hang after I chose to boot it using GRUB. 

Just to clear things up, I don't have Ubuntu, I have Ubuntu Studio - no live DvD, I can only boot into it and install it. Also, how would I install GRUB to the bootsector of the Linux root partition? Could you explain it exactly if I tell you my different partitions? 
I have a 8GB EISA Configuration (is this a partition?) It's only seen when I open Disk Management under Computer > Management.
C: ACER  90GB
D: DATA  75GB
G: XP       15GB
My E: and F: drives are my DvD-RW drives, F: is the virtual one

It would be very helpful if you could explain to me what to do according to my computer configuration, maybe then I'll understand better. 

Thanks a lot

---

### Post by logos34 on 2007-10-12
> **frank.zappa said:**
> Wait, so you're saying I'm only allowed to have 4 partitions on my hard drive? And by extend, do you mean that I should shrink my 75GB partition into a, say maybe 15GB and then use that to install Ubuntu? I also can't remember, but do I have to make a seperate partition for the swap? 

Yep, shrink D: Data 75 GB...15 GB is plenty for ubuntu.  Then turn that freed up space into an extended partition to hold the root and swap logical partitions.
Recommended swap: min. 256MB, up to 2 x your ram.  But for most people there's not much point in going over 1 GB. But if you'll be doing video editing then go for more, maybe ~2 GB. 

> 
Last time I think I allocated 512MB for the swap and,I'm not sure if it was because of this but Ubuntu Studio wouldn't even load the user screen, it would just hang after I chose to boot it using GRUB

I kind of doubt the swap was the issue.

>  Also, how would I install GRUB to the bootsector of the Linux root partition? Could you explain it exactly if I tell you my different partitions? 

If ubuntu studio then the install is identical to the text-mode alternate cd.

You'll be prompted toward the end whether you want to write Grub to MBR.  Select 'NO' and use '(hd0,x)', where x=root partition #

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
(-->scroll down to 'fig 64 ntfs')
[http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location](http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location)

[http://news.softpedia.com/news/How-to-Install-Ubuntu-Studio-54514.shtml](http://news.softpedia.com/news/How-to-Install-Ubuntu-Studio-54514.shtml)
[http://news.softpedia.com/images/reviews/large/ubuntustudio-large_026.png](http://news.softpedia.com/images/reviews/large/ubuntustudio-large_026.png)

> 
I have a 8GB EISA Configuration (is this a partition?) It's only seen when I open Disk Management under Computer > Management.

Not sure what that is...Post a screenshot

---

