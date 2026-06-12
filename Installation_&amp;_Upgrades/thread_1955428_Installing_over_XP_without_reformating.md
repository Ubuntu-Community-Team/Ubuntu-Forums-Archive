---
title: "Installing over XP without reformating ?"
date: 2012-04-09
forum: Installation &amp; Upgrades
---

### Post by CallDon on 2012-04-09
I have a couple of laptops with XP that are about 6 years old.  I have never installed Ubuntu or Lubuntu but have used Ubuntu live from the CD.  

One is an Acer laptop.  The other is an EMachines M6809 but the CD drive is not working.  Both have really slowed down over the years.  I don't know if I want to try to re-install XP or just go with Ubuntu or Lubuntu to get some more fun-time out of both laptops.  I mention Lubuntu since some folks said it works well on older hardware.  

Q1) 
Is there a way to install Ubuntu or Lubuntu using the internet without a CD-drive?

Q2) 
Is it possible to install it so I can keep all the data/doc, etc files without completely reformatting the HDD?  

Or is it just better to save the data/docs and reformat and start from scratch??

---

### Post by CottonCandy on 2012-04-09
> **CallDon said:**
> IQ1) 
Is there a way to install Ubuntu or Lubuntu using the internet without a CD-drive?
The only way I know of to install using only internet is to install Ubuntu inside of Windows. [http://www.psychocats.net/ubuntu/virtualbox ]("http://www.psychocats.net/ubuntu/virtualbox")

You may want to consider making an install USB instead of CD. [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)  [http://www.psychocats.net/ubuntu/usb](http://www.psychocats.net/ubuntu/usb)

> **CallDon said:**
> Q2) 
Is it possible to install it so I can keep all the data/doc, etc files without completely reformatting the HDD?  

Or is it just better to save the data/docs and reformat and start from scratch??
I'm pretty sure whether you reinstall XP or install Ubuntu, you'd be installing over all existing data which means you would have to have a backup copy of your data to put on the new install. 
 
If there is data you don't want to lose, backup your files regularly no matter what OS you use.

---

### Post by oboedad55 on 2012-04-09
> **CottonCandy said:**
> The only way I know of to install using only internet is to install Ubuntu inside of Windows. [http://www.psychocats.net/ubuntu/virtualbox ]("http://www.psychocats.net/ubuntu/virtualbox")

You may want to consider making an install USB instead of CD. [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)  [http://www.psychocats.net/ubuntu/usb](http://www.psychocats.net/ubuntu/usb)


I'm pretty sure whether you reinstall XP or install Ubuntu, you'd be installing over all existing data which means you would have to have a backup copy of your data to put on the new install. 
 
If there is data you don't want to lose, backup your files regularly no matter what OS you use.

There is also the option of resizing the Windows partition and installing Ubuntu in the free space, thereby saving the data. Of course, as has been pointed out, it's wise to backup any data you can't afford to lose, especially as resizing partitions *can* result in data loss.

---

### Post by Cpierce on 2012-04-09
Copy the info you want to save to a USB drive, and then let the Ubuntu/Lubuntu install format the drive. 

If it is older hardware, Lubuntu would be my choice. It is a very nice lightweight OS

---

### Post by lukeiamyourfather on 2012-04-09
> **CallDon said:**
> 
Is there a way to install Ubuntu or Lubuntu using the internet without a CD-drive?


Ubuntu and other Linux distributions can be installed from a USB flash drive. There's also the option of using an external optical drive. There are USB connected optical drives for as low as $30 or even less if you look around.

> **CallDon said:**
> 
Is it possible to install it so I can keep all the data/doc, etc files without completely reformatting the HDD?


Sort of, but not like you're wanting. Linux uses different filesystems than Windows so the only way to keep the data would be to have two or more partitions and even then there's a chance the data could be wiped out.

> **CallDon said:**
> 
Or is it just better to save the data/docs and reformat and start from scratch??

Yes. A clean install is what I'd recommend. Especially if you don't plan to use Windows anymore.

---

### Post by CallDon on 2012-04-09
> **oboedad55 said:**
> There is also the option of resizing the Windows partition and installing Ubuntu in the free space, thereby saving the data. Of course, as has been pointed out, it's wise to backup any data you can't afford to lose, especially as resizing partitions *can* result in data loss.

It is an 80gb drive with over 30gb free since I dumped/saved a bunch of data a couple of months ago thinking that would speed it up. No such luck, it is still slower than molasses.  

Rather than keep it in the closet to waste away, I wanted to find some use for it.  As it is now with XP, I boot up the computer, then it swaps files and spins wheels for 15 to 30 minutes before I can actually use it for anything.  It is a real time-waster as it is now.

Thanks for the info.

D*

---

### Post by Mark Phelps on 2012-04-11
XP is basically NOT that bad ... results like that indicate other, serious, problems at work.

In contrast, I have an old Compaq XP-era laptop, with an 80GB drive, that I recently upgraded to Win7 and it just zips along.  So, just because it's old and the disk is small, does not mean the laptop should crawl.

One possibility is a failing hard drive -- especially in any laptop that is over 5 years old. Major slowdown in performance is common in such situations because sectors fail and the drive tries over and over to read a sector before giving up.

If the hard drive is failing, Linux is not going to fix that or improve on that in any way.

Also, would need to see the specs (processor, memory) to see if any current Ubuntu version would even install or run on the laptops.  Presuming the hard drives are OK, you may have to resort to using Lubuntu to get decent performance.

And, while I agree that shrinking the XP partition to make room for Ubuntu is a good start to dual-booting to retain XP, without being able to boot from CD, or from USB, you're not going to be able to boot into any utility that will allow you to do that.

---

### Post by CallDon on 2012-04-11
> **Mark Phelps said:**
> XP is basically NOT that bad ... results like that indicate other, serious, problems at work.

In contrast, I have an old Compaq XP-era laptop, with an 80GB drive, that I recently upgraded to Win7 and it just zips along.  So, just because it's old and the disk is small, does not mean the laptop should crawl.

One possibility is a failing hard drive -- especially in any laptop that is over 5 years old. Major slowdown in performance is common in such situations because sectors fail and the drive tries over and over to read a sector before giving up.


Also, would need to see the specs (processor, memory) to see if any current Ubuntu version would even install or run on the laptops.  Presuming the hard drives are OK, you may have to resort to using Lubuntu to get decent performance.

It is an eMachines M6809 laptop

Processor AMD Athlon 64 3200+ / 2.0 GHz
Cache L2 cache - 1.0 MB
64-bit Computing Yes
Front Side Bus 1600.0 MHz
Memory
RAM 512.0 MB
Max RAM Supported 512.0 MB
Technology DDR SDRAM
Speed 333.0 MHz / PC2700

For some reason, it has been running slow for several years.  I have several other laptops running XP, one running Vista that I'm upgrading and a netbook running Windows7  I have run all sorts of virus programs, scans, anti-malware, etc.  Like I said, I even emptied 50% of the HDD thinking it would help.  But it's still a slow mover when starting up or coming back to life from hibernating.  When I work on it, I may need to boot it three times to get it to a workable speed where I can accomplish something.  

My problem now is, I keep accumulating these computers. :p  I don't really have a use for all of them at this point.  Each one served it's purpose or is serving it now.  I used the eMachines for audio and video editing but now use a newer Sony Vaio Vista upgrading to Win7.  

So I thought i might put Ubuntu or Lubuntu on this one just for kicks, just to be different.  

Thanks for the comments.

D*

---

### Post by CottonCandy on 2012-04-12
I'm no tech genius, but with 512 MB of RAM I think it would have to be Lubuntu.   I guess it would be a good way to find out if your drive is failing. If Lubuntu takes 15 to 30 minutes to boot and get working once you've installed it then it may in fact be failing hard drive.

---

