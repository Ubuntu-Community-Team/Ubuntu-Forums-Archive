---
title: "New Dual Boot XP/ubuntu laptop install"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by uploadjoe on 2006-12-06
I just ordered a new laptop that comes with XP Home, but I have a copy of XP Pro that I plan on installing. Since I wiping the drive I really would like to dual boot XP and Ubuntu. A while a go I installed Fedora on my desktop, but I never forced myself to use it.

So anyway I am pretty much a n00b to linux and I am not exactly sure of the best method for installing two OS's from a blank HD. Are there any pitfalls to running Ubantu on a Laptop that I should know about it. I know Linux harware support is much improved since I first tried to install SuSe 6-7 years ago. The Fedora install was a snap once I got Grub installed and setup.

Anyway any help/suggestions would be appreciated.

-- Jeremy

---

### Post by loismustdie on 2006-12-06
i did the same thing with my dell e1505.  as soon as i got it, i used the gparted livecd to partition the drive from one 60g partition to 20g (windows), 2g (swap), 18g (ubuntu), and 20 (ntfs shared by ubuntu and windows).  

i really like the gparted livecd.  

specifics about your laptop (graphics card, wireless card, etc.) would be helpful.

---

### Post by uploadjoe on 2006-12-06
Oops sorry yeah I should have posted that info:

It's basically this [computer]("http://www.staples.com/webapp/wcs/stores/servlet/StaplesBTO?jspStoreDir=Staples&catalogId=10051&productId=154611&BTOSessionId=&cmArea=SEARCH&prodCatType=1&langId=-1&BTOModelId=LaptopCTO&BTORequestType=GetConfigurationFromSKU&BTOChoices=Choices&partNumber=664747&storeId=10001&ddkey=StaplesProductDisplay").

60g HD
512 RAM
1.86ghz Single Core processor

I like your drive layout... what is swap used for?

Is Gparted easy to use?

-- Jeremy

---

### Post by LeslieL on 2006-12-06
I've run several Linux distributions on my compaq laptop. It works best with Dapper. 
What I did was install Windows first. During Windows installation you have the opportunity to partition the disk; I used 1/4 of the disk for the Windows OS and programs, half the disk for documents, and 1/4 of the disk for Linux programs, etc. I made the Windows and documents partitions fat32 because they can be accessed by both Linux and Windows.
Once Windows was up and running I installed Ubuntu on the remaining space. That means you need to take control of part of the process and make sure Ubuntu doesn't wipe out the whole disk - it's quite easy if you follow the menus carefully. 
Linux distros all seem able to recognize and make allowances for Windows, automatically setting up the startup menu so you can choose to boot Windows or Linux. Windows can't do that for you, which is why you have to install it first. Windows also can't read Linux partitions, but Linux handles Windows formats fine. 

Good luck

---

### Post by pvegdahl on 2006-12-15
By now you have probably already set things up, but in case you haven't, I'll offer a few thoughts:

Laptops tend to have a bit more funky hardware than desktops, so expect a little bit more work getting things working. For example, it took some work to get widescreen resolutions working with my graphics card, and I had to blacklist a kernel module otherwise the brightness keys wouldn't work.

Power management setup may take a bit of tinkering before it works as well as it does with Windows. Again, some of this will be hardware specific. I had to add scripts that reclocked my video card based on whether I was on AC or battery.

Finally, there is a third party Ext2 driver for Windows XP ([http://www.fs-driver.org/)](http://www.fs-driver.org/)), so that's another option for a shared partition if you want to stay away from FAT32 (ancient) and NTFS (no production level Linux write support).

Good luck. I hope you enjoy and learn from the experience.

---

### Post by uploadjoe on 2006-12-15
Nope I haven't installed yet. I had to order my laptop and its just now on its way to me. I am excited to get everything installed. This weekend I am going to make sure I have all my CD's ready to go this weekend. The Laptop should be here Monday or Tuesday.

Thanks for the help guys I will let you know how it goes.

-- Jeremy

---

