---
title: "Need urgent help dual booting"
date: 2017-07-17
forum: Installation &amp; Upgrades
---

### Post by impair on 2017-07-17
Before I post my problem I will post my specs so everyone can have a better understanding of what's going on. 




Specs:


Operating System
	Windows 10 Home 64-bit
CPU
	Intel Core i7 @ 4.20GHz	
	Kaby Lake 14nm Technology
RAM
	32.0GB Dual-Channel Unknown @ 1149MHz (15-15-15-35)
Motherboard
	MSI Z270 GAMING M5 (MS-7A78) (U3E1)	
Graphics
	VG248 (1920x1080@60Hz)
	VG248 (1920x1080@60Hz)
	3071MB NVIDIA GeForce GTX 1080 Ti 
Storage
	465GB Samsung SSD 850 EVO 500GB (SSD)	
	1863GB Intel Optane+1.8TBSSD (SSD)	





Okay so lets begin this , its gonna be alot of explaining and questions. So I been wanting to Dual-Boot my pc to do a csgo thing I been working on. So I decided to test it on my laptop at first and it went EXTREMELY well other than my laptop being pure **** and having the worst specs ever just a 1TB HDD  so Ubuntu installed perfectly and its all good. Now I tried to do it on my desktop but It did NOT work. I followed the steps I saw for what to do with an SSD not too much different from a regular HDD. I booted up my flashed USB and Clicked install and it said "Unknown Chipset". I searched alot of fixes and found the nomodeset ones and none of that worked, all it did was erase the "Unknown Chipset" error and replace it with a error finding the launch code or something like that i dont remember because by then i was walking out of my room to blow off some steam xD. It then booted me to the Ubuntu home screen where i can click "Install Ubuntu" on the desktop and when i did it froze everything and this kept happening. This was on Version 16.04.2 , Then I went ahead and I tried the same method on 17.04 but instead when i clicked install NOTHING happened just an endless black screen.  So now im stuck and i REALLY NEED for this to work on my desktop. Thanks for anyone and everyone who helps me with this in my time of need. xD

Update: After doing a Nomode it loaded up to the test Ubuntu but i click install and it wont pick up on any of my SSD's only my USB's BUT it will pick up my External HDD that i use for Ubuntu on my Laptop. IDK what to do. [IMG]https://gyazo.com/6edf7da46cc84ee5b93a090fc0ec3f34[/IMG]

---

### Post by Bucky Ball on 2017-07-18
You are using 'Something Else' and manually partitioning? I don't remember exactly, but in the top right hand corner of that GUI, is there a drop-down menu which allows you to select the SSD? This is the case in Gparted and the partitioner in the installer may be the same. As I say, don't remember exactly, but have a check. :-k

---

### Post by vasa1 on 2017-07-18
> **impair said:**
> Update: After doing a Nomode it loaded up to the test Ubuntu but i click install and it wont pick up on any of my SSD's only my USB's BUT it will pick up my External HDD that i use for Ubuntu on my Laptop. IDK what to do. [IMG]https://gyazo.com/6edf7da46cc84ee5b93a090fc0ec3f34[/IMG]Please use the forum's attachment facility to upload images. It's activated by clicking on the paperclip icon. If you don't see this icon, click on "Go Advanced" below the posting area and you'll then see it.

Sites such as this *gyazo* one you've used are ad-infested :)

---

### Post by oldfred on 2017-07-18
Are any of your SSDs, the newer NVMe devices?
They often need firmware updates to be seen correctly.
Post this if now you have live installer working in live mode from terminal.
```
sudo parted -l
```

The newer 270 should be similar to the 170.
 MSI Z170M Intel i7 6700 GTX 980TI 16.10 does not work, 16.04 does
[https://ubuntuforums.org/showthread.php?t=2357641](https://ubuntuforums.org/showthread.php?t=2357641)

---

### Post by impair on 2017-07-18
NO no one is understanding my problem... The installer is NOT working! I

Does anyone have Skype or Twitter than is very educated in Ubuntu so we can instant message! Someone please.

---

### Post by oldfred on 2017-07-18
Are you able to boot live installer. Using nomodeset if required.

Do have have UEFI secure boot off in UEFI?
Do you have fast boot off in UEFI?
Do you have all drives set to AHCI mode, not RAID nor IDE, not some sort of Intel SRT type settings.
Some have turned off nVidia card in UEFI (maybe GPU settings?) and used Intel video/connector to install, then added nVidia driver & reset to use nVidia card. You could try that.
Some motherboards have settings to enable a drive, are they all enabled?

I do not have a MSI card, so just suggesting common issues. 
I do have an Asus X97 and a Gigabyte Z170, both were similar, but called some settings different things and Asus required a lot of settings changes in UEFI, the Gigabyte only some changes.

---

### Post by oldfred on 2017-07-18
If Windows does not boot with AHCI, then you need to install AHCI drivers into Windows before changing setting to AHCI from RAID.
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)
[https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html](https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html)

---

