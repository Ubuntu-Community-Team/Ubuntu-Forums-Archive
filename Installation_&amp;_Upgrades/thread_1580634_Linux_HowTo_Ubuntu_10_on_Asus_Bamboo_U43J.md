---
title: "Linux HowTo: Ubuntu 10 on Asus Bamboo U43J"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by mrinal2k1 on 2010-09-23
In this post, here is an account of the Ubuntu 10 install on the new [Asus Bamboo U43J]("http://www.amazon.com/gp/product/B003V4AK4I/ref=pd_lpo_k2_dp_sr_1?pf_rd_p=486539851&pf_rd_s=lpo-top-stripe-1&pf_rd_t=201&pf_rd_i=B001EWE6FI&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=00KX2GF3PVC3QWYGSG8K").
For more Linux HowTos, visit my blog [http://timedigit.blogspot.com](http://timedigit.blogspot.com)

First some specs:
.64 Bit Intel i5 duo core processor
.4GB of RAM
.500 GB Hard Disk
.NVIDIA Optimus video card
.Intel 802.11 b+g+n wireless

OS - Ubuntu 10.04 LTS 64 Bit (on dvd)
Note: The laptop comes with a Default Windows 7 Home Edition factory  installed. I want Ubuntu to be installed alongside Windows & dual  boot.

First repartition the Hard drive. Very easy to do:
1-Pop Ubuntu install disc in the optic drive & reboot
2-On Bios choose - "Boot from Optical Disc"
3-On the initial Ubuntu screen, choose "Test Ubuntu without Install" (we  will do so in the subsequent steps, right now only repartition disk)
4-Once inside Ubuntu, choose : System > Administration > GParted
5-On the GParted screen, resize the existing Windows partition to a  smaller size. This is where we will install Ubuntu. In my case I reduced  the Windows partition from 500GB to 200GB, freeing up 300GB for Ubuntu.
Thats it, once all the above are completed, you can reboot from the DVD  to actually install Ubuntu in the newly created free space.
Note: In the step 5 above, dont forget to "Apply the changes" after resizing the partitions.

Actual Ubuntu Install:
1-Reboot using the Ubuntu Install disc.
2-On the initial Ubuntu screen, choose "Install Ubuntu". Click next.
3-Follow onscreen instructions until you reach the "Disk Configuration"  screen. Here select the partition that you freed up in GParted (see step  #5 above). This is where Ubuntu will be installed.
4-On the following screens, specify other details like default username, root password, timezone, etc.
5-Finally on the "Start Install Ubuntu" screen, review the configuration and click "Start Install"
And Thats it. The install is self driven and in 15-20 minutes, it is  completed. It prompts to remove the install disc from optic drive and  reboot.
After the reboot, the Grub Bootloader screen shows up that allows you to  choose between the Operating Systems to boot (in my case Windows or  Ubuntu). Ubuntu is the default.

Extra notes:
The install process is fairly simple. The folks at Canonical have made the Ubuntu Linux install very simple and quick. Kudos.
All of my features and functionalities of my Asus Bamboo work well with  Ubuntu. Some extra software like Flashplayer or the GNU equivalents  might need to be installed. This will allow you to view proprietary  format videos on YouTube etc. Other than that everything works normally.
I installed Skype and tested it out. In next post, we will see the quick way to install Skype on Ubuntu 10.

---

For more Linux HowTos, visit my blog [http://timedigit.blogspot.com]("http://timedigit.blogspot.com/")

---

### Post by mörgæs on 2010-09-24
Thanks. If you mark the post 'solved', there is better chance that people will find it.

---

### Post by cosmodemonictel on 2010-12-25
I'm interested in doing a clean wipe of all the factory Asus/windows settings and installing only ubuntu studio (possibly dual boot Studio and Mint or studio and regular ubuntu). 

However, I'm worried about doing this because the U43J comes stock with a hidden partition (I think about 40gbs) that holds the file system for a windows recovery. If I were to screw up the linux OS I'd have nothing to revert back to. Any suggestions?

Thanks again in advanced. Can't tell you how much better I feel knowing you have the same machine as me.

---

### Post by cbrunos on 2011-01-01
Hello,
quick question, how much autonomy do you have under ubuntu? What type of battery do you have? A 4-cell?

I'm asking because I have 4 hours battery lifetime, and I think I have a 4 cell battery, and I might buy a 6-cell one.

---

### Post by rosencrantz on 2011-01-29
Actually, there are quite a few issues with this model, especially with the hybrid graphics and hibernation.
However, arbrandes has summed up a number of workarounds in this excellent thread: [http://ubuntuforums.org/showthread.php?t=1615564]("http://ubuntuforums.org/showthread.php?t=1615564")
No hope of getting the hybrid graphics to work properly at the moment, though.

---

