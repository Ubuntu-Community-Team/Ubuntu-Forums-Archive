---
title: "Can not install ubuntu - gparted does not recognize 2 ssd drives - raid0"
date: 2017-05-21
forum: Installation &amp; Upgrades
---

### Post by darga33 on 2017-05-21
Hi, I have searched endlessly on how to resolve this. I have went to more than 100 different websites searching for everything under the moon on trying to figure this out. I hope someone can help.

I bought a new laptop for work: 
[ASUS ROG G701VO-CS74K Gaming Laptop Intel Core i7 6820HK  (2.70 GHz) 64 GB DDR4 Memory 1024GB NVMe SSD NVIDIA GeForce GTX 980 8 GB  GDDR5 17.3" - IPS Windows 10 Home 64-Bit]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834234146R")

I just want to install ubuntu on it. I don't want to return this laptop but I will have to if I can not get ubuntu installed on it. I wonder if the entire reason is because the company put the wrong description 1TB drive, but didn't say they were 2 500 GB drives in a raid format and now I can't install ubuntu.

         
[LIST]
[*]The BIOS shows two hard drives each 476.9GB 
[*]BIOS has them in a RAID0, and displays both of them but gparted live USB, and gparted in ubuntu live session, and ubuntu install does not show these two drives or the raid configuration so I can not install ubuntu. 
[*]I do not know if I have a raid controller hardware, or if it's a software raid, or if it is a fakeraid. (so I don't know if there is some raid management utility that I need to enter into other than the BIOS setup of the raid) 
[*]Does anyone know what I may be doing wrong? fdisk -l does not show the 2 drives, but it does show the USB drive that i put the bootable ubuntu ISO on. gparted also only shows the USB. 
[*]I tried turning legacy CSM (compatability support module) on and also off, but to no avail. Secure boot is disabled. I even tried deleting the raid0 config from the BIOS config (because it allows you to use a non raid config), although the SATA configuration BIOS entry forces you to use RAID (I saw some posts say you should switch it to ahci mode (i don't have that option) 
[*]I tried seeing if I could gain access to the drives using FREEDOS, and even DOS did not show the drives. The wierd thing is, the computer came preloaded with windows 10, so the drives themselves are not bad drives. I lost windows 10 once I tried changing the BIOS from RAID to non raid. (all data will be lost - are you sure you want to continue) -- and I said yes because I just want to install ubuntu on this machine. 
[*]In an effort to get windows 10 back (to go back one step) I tried installing windows 10 again using unetbootin with the win 10 ISO, but after the image was burned, during the install it said that the media was lacking a driver for either the USB drive (which the ISO was on) or the hard drive. So i'm not sure if I had a bad version of the windows install. I just want to install linux but I can not figure out how to recognize the drive so that I can run gparted on it. 
[*]I was thinking the reason the drive is not recognized is because maybe the USB has to boot in EFI mode, because maybe the EFI firmware must communicate with the raid to show it in the software. But I do not know how to force the machine to boot in EFI mode and then have the USB also run the installer in EFI mode other than turning (legacy CSM off) which I did. I even tried removing the BIOS raid and making the drives by themselves, that still did not show them during linux install or in gparted. 
[*]I ran dmesg, but there is so much data, I don't know what to grep for for hard drive entries (to see if it was atleast looking for a hard drive) 
[/LIST]
 
Any ideas guys? Is there some way to force the terminal to find all drives attached to a computer and then mount them so they can be used in the linux install?

Thanks for helping!!

---

### Post by LastDino on 2017-05-21
[https://help.ubuntu.com/lts/serverguide/advanced-installation.html](https://help.ubuntu.com/lts/serverguide/advanced-installation.html)

You seem to be having hardware RAID 0 config, while someone who actually has experience with this config comes along, read through the link, it has some useful info and steps if you want to follow.


I've personally not made this setup yet, so I can't affirm you on this with success remark but useful info till someone comes along who has done it.

---

### Post by oldfred on 2017-05-21
I also do not know RAID, but RAID 0 is just for speed. It used to be used with two hard drives to make them faster before SSD. But now with SSD, less need for RAID 0.
Also RAID 0 is not recommended or a standard system. If either drive fails then you lose all data. Half is on one drive and half on the other.
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

You do not have 1TB with RAID 0 and have the two 500GB drives. They mis-represented the system to you.
With RAID 0 you would have to backup system and reinstall to one drive after breaking RAID. Generally it is a FakeRAID controlled by UEFI/BIOS.
 
You should have a setting somewhere to turn RAID off. It may be an Intel setting in UEFI also. But drives should be AHCI.
Make sure you have latest UEFI/BIOS from Asus.
Many newer Asus have needed boot parameter and nVidia often needs nomodeset.

 [http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04](http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04) 

 ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[URL="https://ubuntuforums.org/showthread.php?t=2327570"]https://ubuntuforums.org/showthread.php?t=2327570


[/URL]

---

### Post by darga33 on 2017-05-21
I looked at that link but the issue I'm having is I can not even access my drives using fdisk -l or gparted, or anything. I don't know why it just doesn't let me and I don't know what to do to be able to access them. That article shows that when you type X command you will see a list of your drives. I boot into the live ubuntu session and it only shows access to my USB. I was wondering if I try and install ubuntu SERVER edition, maybe it might pick up on the raid config. I wish I could remove the raid config but even if I remove it from BIOS (delete the raid and make them stand alone drives), then the Sata Config is only set to RAID, there is no other option for that. Maybe UBUNTU server would pickup on on the drives. and then I can install the desktop gui package on top of it once it's working.

I saw an article online that you can actually force your drives to be AHCI from windows 10.but you have to have win 10 installed and I no longer have it installed (and when I try to install it with the image, it says my media is lacking drivers - it could be referring to the USB media, or the hard drives themselves - not sure). This option seems the most promising - if I had windows 10 installed again, I could give it a shot.
[http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/](http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/)

Either way it looks like my problem is hung up in that I can't access my drives some how. Any ideas on how to access my drives? If I can get access to them I can run gparted on them and remove all partitions and then the linux install might find it.

---

### Post by oldfred on 2017-05-21
For Windows 10 with the RAID, you often have to install the AHCI drivers for Windows to work.
But setting is really in UEFI/BIOS. 

Check with vendor if there is an update. Or ask them directly. 
Since they did not give you the 1TB as advertised you have some leverage. Just do not mention Linux as they immediately claim not to know anything.
Just say you are concerned about RAID 0's reliability and want to remove it.

---

### Post by darga33 on 2017-05-21
Hi Oldfred! 

Thanks for the info on RAID0. I wish there was somewhere where I can turn RAID off. BIOS lets me delete the RAID volume but even after making them independent, there is another setting in BIOS - SATA config - that says RAID and it gives no other option. The link I posted in the other reply says that if I do it in windows, I can then do it in the BIOS, but I'm not even sure that a different BIOS option will be displayed. I'm thinking that this BIOS is stuck on RAID sata config. Not sure though.

How do I make sure that I have the latest UEFI/BIOS from Asus ? I'm not sure how to do that? I would think I would have the latest seeing that this laptop is a high end laptop, although I did get it on sale from newegg as shown in the link in my original post.

I don't kno whow to do the boot parameter stuff - even though I read those instructions - keep in mind, I am very new to ubuntu and am trying to absorb everything as quickly as possible because if I can't get ubuntu installed then I have to send this laptop back. I didn't think the boot param thing would help me because people who had issues with that didn't look like they had issues recognizing the hard drives. It looked like they had other install issues. 

I would like to try it but I dont' know how even following the instructions that you wrote here:
[https://ubuntuforums.org/showthread.php?t=2303665](https://ubuntuforums.org/showthread.php?t=2303665) --- pasted below so you don' have to go to the link
> 
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)

You add pci=nomsi like nomodeset in these examples:

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 


 [http://ubuntuforums.org/showthread.p...3#post13502963]("http://ubuntuforums.org/showthread.php?t=2327103&p=13502963#post13502963")

So I guess I'm stuck with, is there some way to get something to recognize the drives? If there is not - do you think if I took out the drive and plugged it into my old laptop and tried to format it and install linux on it, that I could put it back into the new laptop and it might work (as long as I remove the raid volume from BIOS even though the SATA config will still be set to raid since I have no way around that?)

Thanks! Jordan

> **oldfred said:**
> For Windows 10 with the RAID, you often have to install the AHCI drivers for Windows to work.
But setting is really in UEFI/BIOS. 

Check with vendor if there is an update. Or ask them directly. 
Since they did not give you the 1TB as advertised you have some leverage. Just do not mention Linux as they immediately claim not to know anything.
Just say you are concerned about RAID 0's reliability and want to remove it.

When you say "Check with the vendor" who do you mean because I bought it from newegg and I bet they have no clue about anything to do with it since they sell all kinds of stuff. Or are you saying check with ASUS the manufacturer?

---

### Post by LastDino on 2017-05-21
In older days there used to be way to access Raid0 during BIOS boot up by pressing either Ctrl-I {I think  AMD RAID is Ctrl-F} during BIOS booting or in the Storage Configuration. 

But in newer more latest versions it has became even more hard to do this, on older desktops you could do it with simply removing jumpers. Therefor, with no experience with your system it is hard to tell how to do it if it is not easily visible in BIOS (But it really should be there)

As **oldfred** suggested, your best bet is vendor, and you do have a reason to fight here. 

Best bet would be Asus, you can even write a mail and ask questions on motherboard.

---

### Post by oldfred on 2017-05-21
First link in Google on Asus RAID 0 and AHCI was this.
[https://rog.asus.com/forum/showthread.php?83061-G752VY-BIOS-211-released-with-AHCI-and-RAID-0](https://rog.asus.com/forum/showthread.php?83061-G752VY-BIOS-211-released-with-AHCI-and-RAID-0)

Not your model, so you need to check if newest UEFI has similar update or complain to Asus.

---

### Post by darga33 on 2017-05-21
> **oldfred said:**
> First link in Google on Asus RAID 0 and AHCI was this.
[https://rog.asus.com/forum/showthread.php?83061-G752VY-BIOS-211-released-with-AHCI-and-RAID-0](https://rog.asus.com/forum/showthread.php?83061-G752VY-BIOS-211-released-with-AHCI-and-RAID-0)

Not your model, so you need to check if newest UEFI has similar update or complain to Asus.

SO those pictures at the top of that link are the ones from my BIOS with one exception. 
The third pic down, I do not have access to turn to AHCI. 

You mention about installing the latest BIOS. How would I do that? I am clueless. 

Also I noticed there is something in the BIOS that says something like "RUN EFI command line" or something along those lines. Would I need to enter into that in order to upgrade the BIOS firmware? Is it possible that you could walk me through step by step on how to upgrade BIOS because I am very new to this BIOS / EFI stuff. I am just in total shock that I can not for the life of me access these two SSD drives in the ubuntu install. Neither fedora, neither mint.

---

### Post by oldfred on 2017-05-21
I do not know Asus' install procedure.
I do have an Asus motherboard, but motherboards often have a lot more features and flexibility.

You typically have to go to Asus' site, and search for updates to UEFI/BIOS. The often have support or download based on model(s).
Then their may be options or just one larger download that includes options.

My motherboards (several brands over time) have had 3 ways to update. From Windows. From booting a DOS flash drive. They include a DOS image & instructions on creating a bootable flash drive with an new image for UEFI. And the one I normally use is from within UEFI find the image update file. It has to be in a FAT32 (with UEFI) folder or flash drive as that is only file system UEFI reads. My last time I copied into my ESP, but typically have just used a FAT32 flash drive.

First page of Google search:
[https://www.asus.com/us/support/Download/3/877/0/1/dAhI04x4Qb8OhVWL/45/](https://www.asus.com/us/support/Download/3/877/0/1/dAhI04x4Qb8OhVWL/45/)
They still call it BIOS, but it has to be UEFI.
You also may want manual.
Do not download any Windows drivers. But not sure if Windows "BIOS" is any different than "Other".
And review FAQ, but most are Windows related.

---

### Post by darga33 on 2017-05-21
> **oldfred said:**
> I do not know Asus' install procedure.
I do have an Asus motherboard, but motherboards often have a lot more features and flexibility.

You typically have to go to Asus' site, and search for updates to UEFI/BIOS. The often have support or download based on model(s).
Then their may be options or just one larger download that includes options.

My motherboards (several brands over time) have had 3 ways to update. From Windows. From booting a DOS flash drive. They include a DOS image & instructions on creating a bootable flash drive with an new image for UEFI. And the one I normally use is from within UEFI find the image update file. It has to be in a FAT32 (with UEFI) folder or flash drive as that is only file system UEFI reads. My last time I copied into my ESP, but typically have just used a FAT32 flash drive.

First page of Google search:
[https://www.asus.com/us/support/Download/3/877/0/1/dAhI04x4Qb8OhVWL/45/](https://www.asus.com/us/support/Download/3/877/0/1/dAhI04x4Qb8OhVWL/45/)
They still call it BIOS, but it has to be UEFI.
You also may want manual.
Do not download any Windows drivers. But not sure if Windows "BIOS" is any different than "Other".
And review FAQ, but most are Windows related.

Hey so I went to that link, which is awesome. I saw the BIOS utility. And I clicked to download it. It had a setup file so I ran it and it extracted some files. Then I had to run some other file to extract more files. Then I put them all on the USB drive. Since it wasn't an ISO I did not use unetbootin. When I went to BIOS and inserted the flash drive and selected that option to "FLASH the BIOS". It brought me to a screen to select a file and so I went through the entire directory structure selecting each file and it never found a final leaf node file to use. 

Any other options or am I pretty much out of luck and I have to send this laptop back? 

I was thinking what if I took the drive out of the laptop and if it was compatable with my old laptop (this one I'm using now), then maybe I could try and install ubuntu on it and put it back in. Do you think it is possible for that to work? If I just make it so that the BIOS on the new setup does not use RAID, even though under SATA configuration it will still say RAID since it doesn't give any other option other than RAID?

---

### Post by darga33 on 2017-05-21
Hey Oldfred, I just found out something that is going to make me return the laptop. Since I bought it as an openbox, someone tried to pry open the hinge, and I only noticed it when I read the manual on how to open the computer and it says you need to open the hinge. I'm going to send the computer back and just stick with my old laptop for a little while. So now if it is possible I would like to install windows 10 back on it. I hope that windows 10 recognizes the drives and allows me to install it. The only thing is, I have changed the BIOS settings so I'm not sure how that will affect it although I have put it back to "reset to defaults". 

Any idea on how to do a clean install of windows 10. I've already downloaded the ISO, and am in the process of burning it to the USB with unetbootin. 

Thanks so much for your help in trying to figure out why we could not get the hard drives to display to gparted or the linux install, or pretty much anything. 

I am wondering if I am going to need to open up that EFI control command line that there is an option in the BIOS for in order to get windows 10 to run. Maybe that is the only way that windows 10 will recognize the drives. We will soon see :-)

---

### Post by oldfred on 2017-05-21
OEM versions of Windows like Asus may include drivers. That is why it is always best to do a backup. And with Windows it just about has to be some sort of image backup. 
With Ubuntu the operating system is free and relatively easy to reinstall (once you learn how), so backup of data & configuration is all that is required.

The RAID setting & drivers may be an issue.
But the site with downloads probably had all the other extra drivers you may need.

UEFI normally has a reset to defaults setting. I have avoid that as I must have 5 or 10 settings that I change. And even UEFI updates reset to defaults and I have to redo them. With old BIOS system I took photos of every screen I changed. With UEFI, it has screen shots & one system even lists all the changes which I copy.

---

### Post by darga33 on 2017-05-21
> **oldfred said:**
> OEM versions of Windows like Asus may include drivers. That is why it is always best to do a backup. And with Windows it just about has to be some sort of image backup. 
With Ubuntu the operating system is free and relatively easy to reinstall (once you learn how), so backup of data & configuration is all that is required.

The RAID setting & drivers may be an issue.
But the site with downloads probably had all the other extra drivers you may need.

UEFI normally has a reset to defaults setting. I have avoid that as I must have 5 or 10 settings that I change. And even UEFI updates reset to defaults and I have to redo them. With old BIOS system I took photos of every screen I changed. With UEFI, it has screen shots & one system even lists all the changes which I copy.

Ok so I am going to try and install windows 10 ISO. If I need those drivers that you are mentioning. Do you know how to actually install them? Do I need to use unetbootin and have the drivers as images so they are bootable or do I just put all of those files on a USB drive and then if windows asks for some drivers them I just point windows to the USB which will have all the drivers ?

Wish me luck!

---

### Post by darga33 on 2017-05-21
I can't believe this I tried everything to recognize those drives but nothing will. I even found this really cool windows 10 recovery ISO - which is amazing. It boots you into a windows UI and everything but it just recognizes the USB drive.  [https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)

So I have officially given up. Thank you guys so much for helping me especially you Oldfred. I really appreciate it. It looks like I'm sending the computer back. Even with the damage to the computer's hinge I would keep it if I can just get this thing to recognize the drives. I was going to take it apart and see if I could put the drives into my old computer to install linux on them but when I saw the other guy's damage (because it was open box), I was like no way I'm not touching this thing anymore. Anyways I have learned a lot in this process, No where near enough ofcourse, but atleast it's a step in the right direction! 

Thanks again Oldfred! I will be packing this thing up tomorrow to ship it back. Have a good rest of the evening!

---

### Post by oldfred on 2017-05-21
Sorry we could not figure out your drives. I have seen others with RAID 0 make it eventually work.

Good luck on next computer.

(I am anti-laptop)
They are not ergonomic, screen too small, keyboard too high, really only good on laptop.
I prefer desktop, and like to build my own. But some do need the portability of a laptop for job or school.

---

### Post by LastDino on 2017-05-22
You will actually have better luck with RAID0 config on gaming forums as they usually buy these high end laptops and get rid of these settings or maintain as per performance requirement.

---

