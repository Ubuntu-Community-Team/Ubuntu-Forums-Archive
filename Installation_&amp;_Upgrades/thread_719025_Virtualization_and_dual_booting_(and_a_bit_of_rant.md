---
title: "Virtualization and dual booting (and a bit of ranting)"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by Jonathan Métillon on 2008-03-08
Hi,

(I moved ranting to [Testimonials & Experiences : **Can't really get rid of Windows**]("http://ubuntuforums.org/showthread.php?p=4478792"))

[SIZE=-1]I'm currently on Windows XP and want to install Ubuntu with dual boot and virtualization.

My questions are:
[/SIZE][LIST]
[*]What is the best tool for Windows XP virtualization on Ubuntu?
[*]If the answer is [VMware]("http://www.vmware.com/products/desktop_virtualization.html"), what version?
[*]Is this better (in terms of performance and/or hardware compatibility) to -1- have a virtualization tool working over an OS (Ubuntu) and then run the other OS (Windows) over it, or is this better to -2- have a virtualization tool at the bottom and install two OS over it, and run both OS in parallel?
[*]Will I need to create a new partition or will I be able to point the virtualization tool to the existing Windows partition and not reinstall Windows? (if answer is -1- in the precedent question)[/LIST]Thanks!

---

### Post by dorkdork777 on 2008-03-09
[list]
[*]It's debated, but a great number of people seem to like VirtualBox, and I'm definately one of them. I prefer it to VMware.
[*]Which version of VirtualBox? There's an open-source version, but the closed-source version has more features.
[*]I think 1 is better, as there's one host and one guest (2 OSs), while in 2, there's one host and two guests - 3 OSs at once!
[*]VirtualBox does have this feature, but from what I've tested, it's still fairly hard to get started with. By all means try, though!
[/list]

Pretty sure that's right. :)

---

### Post by mimada on 2008-03-09
I prefer VirtualBox as well. Since you currently have a Windows install, you should install Linux as a guest OS to try it out (download and install the Windows version of VirtualBox then create a Linux guest). I recommend eventually running a Linux host and Windows guest, especially if you are worried about security and malware. Be aware that the guest OS runs slower than the host and that a Windows guest will have poor 3D performance (no modern 3D games :().

The virtual hard drive is just a file on your regular hard drive. VirtualBox has a utility to clone the virtual hard drive. What this means is once you've installed the OS and all your apps, you can make a backup of the drive. If something nerfs your VM, you can just delete the virtual drive and make a new one from your backup. It saves me hours of reinstallation time.

Have fun!
Mike

---

### Post by Jonathan Métillon on 2008-03-09
> **dorkdork777 said:**
> [LIST]
[*]It's debated, but a great number of people seem to like VirtualBox, and I'm definately one of them. I prefer it to VMware.
[*]Which version of VirtualBox? There's an open-source version, but the closed-source version has more features.
[*]I think 1 is better, as there's one host and one guest (2 OSs), while in 2, there's one host and two guests - 3 OSs at once!
[*]VirtualBox does have this feature, but from what I've tested, it's still fairly hard to get started with. By all means try, though![/LIST]Thank you DorkDork. :popcorn:

Ok so I'll setup Windows XP as a guest over Ubuntu. But I think case 2 should cannot be seen as 3 OS because the host is very basic and does not generate much overhead. I have a 1.2 Ghz Core Solo + 1.5 GB so I don't think I will notice a big performance hit. Anyway I prefer case 1 because I won't have to format my whole disk, install the guest and reinstall Windows and Ubuntu.

Making VirtualBox to use an existing Windows XP partition is hard? I'd really prefer not to create a file in my Ubuntu partition to reinstall Windows in it. I have a native NTFS partition with all softwares already installed and I want to keep it like that. And so I can still dual boot.


> **mimada said:**
> I prefer VirtualBox as well. Since you currently have a Windows install, you should install Linux as a guest OS to try it out (download and install the Windows version of VirtualBox then create a Linux guest). I recommend eventually running a Linux host and Windows guest, especially if you are worried about security and malware. Be aware that the guest OS runs slower than the host and that a Windows guest will have poor 3D performance (no modern 3D games :().

The virtual hard drive is just a file on your regular hard drive. VirtualBox has a utility to clone the virtual hard drive. What this means is once you've installed the OS and all your apps, you can make a backup of the drive. If something nerfs your VM, you can just delete the virtual drive and make a new one from your backup. It saves me hours of reinstallation time.

Thank you Mike. :guitar:

I won't try Ubuntu as a guest in Windows, I know Ubuntu and I'll directly install it. Then I will run Windows as a guest from Ubuntu.

I will keep the dual boot option. That way, if I need performance I can just reboot to a native host Windows.

But in this case, I think I won't be able to do the virtual disk file backup trick because I will keep my NTFS partition as a real native partition, not transfered into a virtual disk file in my Ubuntu partition. Right?


DorkDork,  Mike, can you tell me why you prefer VirtualBox over VMware? Especially if you advocate the closed source version (more features), then open source is not an argument against VMware.

---

### Post by mimada on 2008-03-09
The only thing the virtual disk backup needs is hard drive space. It doesn't matter what file system you use. In Ubuntu, VirtualBox creates a hard drive image file in the ~/.VirtualBox/VDI directory. When you start the Windows install, the _image_ is formatted with NTFS. The image file resides within the Ubuntu partition not a separate NTFS partition. I set my virtual hard drive at 10 gigs with dynamic expansion. This means that if I run out of virtual hard drive space, VirtualBox will automagically expand the virtual hard drive. BTW just because I set my virtual hard drive to 10 gigs, it doesn't mean the image is 10 gigs (it's actually a little over 5). It's just that Windows sees 10 gigs of hard drive space.

I prefer VirtualBox because I previously had issues with VMware (crashes, network problems, and some installation problems). I suppose they've fixed those issues by now but VirtualBox runs really well on my system and I see no reason to try VMware again. Also, after you install your VM, make sure you install the guest additions. This will allow you to set up a share folder so you can easily transfer files between the host and the guest. The mouse will also work between host and guest seamlessly.

Mike

---

### Post by Jonathan Métillon on 2008-03-09
> **mimada said:**
> The only thing the virtual disk backup needs is hard drive space. It doesn't matter what file system you use. In Ubuntu, VirtualBox creates a hard drive image file in the ~/.VirtualBox/VDI directory. When you start the Windows install, the _image_ is formatted with NTFS. The image file resides within the Ubuntu partition not a separate NTFS partition. I set my virtual hard drive at 10 gigs with dynamic expansion. This means that if I run out of virtual hard drive space, VirtualBox will automagically expand the virtual hard drive. BTW just because I set my virtual hard drive to 10 gigs, it doesn't mean the image is 10 gigs (it's actually a little over 5). It's just that Windows sees 10 gigs of hard drive space.

Yes that's exactly what I don't want :-) Because I won't be able to dual boot anymore.

> **mimada said:**
> I prefer VirtualBox because I previously had issues with VMware (crashes, network problems, and some installation problems). I suppose they've fixed those issues by now but VirtualBox runs really well on my system and I see no reason to try VMware again. Also, after you install your VM, make sure you install the guest additions. This will allow you to set up a share folder so you can easily transfer files between the host and the guest. The mouse will also work between host and guest seamlessly.

Thanks Mike!

---

### Post by mimada on 2008-03-09
I forgot to bring up another point. It seems that you are of the opinion that you can take an existing Windows installation and turn it into a VM. That's not the case. The VM is a separate and different machine from the host. From the point of the VM, it doesn't do you much good to have an existing partition with installed applications. You'll need to install Windows into the VM like you would for a new computer. After the install, you'll need to install the apps you want to use in your virtual machine. Trying to move an existing host image to a VM is just not practical. The Windows registry entries of the host will most likely not map to the VM.

VirtualBox does allow you to setup two more virtual drive partitions per VM. These virtual partitions can be placed in any real partition the host can see.

Mike

---

### Post by Jonathan Métillon on 2008-03-09
Mike,

It looks like it's possible to migrate an existing Windows partition to a VM file for VirtualBox:
[LIST]
[*][existing WinXP to .vdi]("http://forums.virtualbox.org/viewtopic.php?t=1404&start=0&postdays=0&postorder=asc&highlight=")
[*][Making a virutal machine out of a networked computer]("http://forums.virtualbox.org/viewtopic.php?t=4980&start=0&postdays=0&postorder=asc&highlight=")[/LIST]However if I understand your point, it is **NOT** possible to have a host Windows I can boot on, and that same Windows be available as a VM from my other host OS, Ubuntu?

So if I want a virtualized Windows from Ubuntu **PLUS **a native Windows on my computer, I need to have **TWO DIFFERENT** Windows, right?

:(

---

### Post by mimada on 2008-03-09
VirtualBox will not affect dual booting at all. It just takes up hard drive space. It's possible to set up a XP/Ubuntu dual boot, then install a XP VM within Ubuntu and/or an Ubuntu VM within XP. Windows, whether it's a VM or native install will still be vulnerable to malware but with a VM, you simply delete the hard drive image and restore from the backup. Nothing that affects the VM will hurt the host system.

I suggest you set up a XP VM and see how well your apps work with the VM.

Mike

---

### Post by mimada on 2008-03-09
> So if I want a virtualized Windows from Ubuntu PLUS a native Windows on my computer, I need to have TWO DIFFERENT Windows, right?

That's correct. The VM is seen as a completely separate computer. That's one of it's major advantages BTW, at least from a security standpoint. What are you trying to do with the VM?

Mike

---

### Post by mimada on 2008-03-09
> It looks like it's possible to migrate an existing Windows partition to a VM file for VirtualBox:

In the first case, it looks like the poster wants to move data to their VMs. The second post emphasizes how difficult it is to migrate an existing Windows installation to a VM. Yes, it is possible but it's likely to be very messy. You're better off with a fresh install.

Mike

---

### Post by mimada on 2008-03-09
I just read your rant on the other thread. What I suggest you do is to create the XP VM in Ubuntu but _do not_ upgrade it to SP2 or install any resident programs (such as virus scanners or IM). Install the necessary apps one at a time and check the performance of the software.

The stripped down Windows runs a lot faster. Do not use the Windows VM for web stuff or email. Try to use your host for that. Backup your virtual drive and use the VM. See if the performance of your software is more acceptable in the VM. If the VM starts to slow down, transfer your docs to the host and delete the image. Clone another drive from your backup and your apps should be running at full speed again.

Mike

---

### Post by Jonathan Métillon on 2008-03-09
Thank you Mike.

If I install a fresh Windows XP in a VM, as a guest in Ubuntu, but I don't delete the Windows i currently have installed, will I be able to access from the VM the partition from the other native Windows?

That way I could at least share my files between the two Windows.

---

### Post by mimada on 2008-03-09
> If I install a fresh Windows XP in a VM, as a guest in Ubuntu, but I don't delete the Windows i currently have installed, will I be able to access from the VM the partition from the other native Windows?

Yes and no, the best way to do this is to create a share folder that is visible to both Ubuntu and XP. From the VM just move the files into the share and then you'll be able to access the file from XP. You cannot (or should not) try to access a virtual drive from outside the VM. You'll most likely wind up corrupting the drive.

Mike

I should clarify the fact that you can have multiple share folders on different partitions. So if you can access an NTFS partition through Ubuntu, you can install a share folder there and move the files you wish to have available to the XP installation.

---

### Post by Jonathan Métillon on 2008-03-09
Understood :-)

But, as the native NTFS partition is available to Ubuntu, can't I make it an entire "shared folder" so the VM can access all the files from the native Windows? That way I can even reinstall software from the VM but telling it to install into the Program Files from the shared folder, so it will actually overwrite the already installed apps, which will be available from both Windows (VM and native) without duplicating the files. Right?

---

### Post by mimada on 2008-03-09
> But, as the native NTFS partition is available to Ubuntu, can't I make it an entire "shared folder" so the VM can access all the files from the native Windows? That way I can even reinstall software from the VM but telling it to install into the Program Files from the shared folder, so it will actually overwrite the already installed apps, which will be available from both Windows (VM and native) without duplicating the files. Right?

I understand what you're asking. It's sounds cool but a lot of apps may not work properly. You'll just have to experiment with it. Be aware that some windows apps will install dlls, ini and config files in the Windows directory and most will make registry entries. Apps that are shelf contained within their directories should run fine. You may have to install the apps from both within the VM as well as from the native install.

This kind of tinkering has the potential of messing up your Windows installation. I strongly recommend that you backup your VM before trying this. If you have some Windows backup software (like Norton's Ghost) I would backup the native install as well.

Mike

---

### Post by Jonathan Métillon on 2008-03-09
Ok thank you Mike.

One last question. Is the more featured, closed source, VirtualBox version available from Ubuntu repositories? Or is there a .deb available from VirtualBox website?

---

### Post by mimada on 2008-03-09
Just go to virtualbox.org then to the downloads. You'll see a link for the Ubuntu version. The open source version is listed at the bottom of the page.

I hope you have a lot of fun with VirtualBox.:)

Mike

---

### Post by Jonathan Métillon on 2008-03-09
Thank you for your time!

---

### Post by mimada on 2008-03-09
I just noticed in one of your posts that you have Sony recovery discs. I hope you have a regular copy of Windows XP for the VM. A lot of recovery discs won't work in a VM because it has a totally different hardware configuration.

Mike

---

### Post by dorkdork777 on 2008-03-10
@mike - My Fujitsu-Siemens recovery disc works perfectly on all VMs I've tried. Not saying his Sony ones will though.

@Jonathan - By scanning over the thread, it looks like you have run with the assumption that you can't use your existing XP partition with a VM - this is not the case. Go to [this page]("http://www.virtualbox.org/wiki/Downloads"), and download the user manual. Read pages 106 to 108 (the whole of section 9.9) - you will become enlightened. :)

---

### Post by aitvo on 2008-03-10
> **Jonathan Métillon said:**
> Mike,

So if I want a virtualized Windows from Ubuntu **PLUS **a native Windows on my computer, I need to have **TWO DIFFERENT** Windows, right?

:(

No, if you go with VMWare server you will be able to boot the partition native or in a VM. It only requires a little bit of effort, and a reg file from Microsoft.com.

I have the article up here: [http://www.stangdude.com/news/articles/25105759865848/]("http://www.stangdude.com/news/articles/25105759865848/")

Not sure if this would work similarly with vbox, but hope it helps.

---

### Post by Jonathan Métillon on 2008-03-10
> **aitvo said:**
> No, if you go with VMWare server you will be able to boot the partition native or in a VM. It only requires a little bit of effort, and a reg file from Microsoft.com.

I have the article up here: [http://www.stangdude.com/news/articles/25105759865848/](http://www.stangdude.com/news/articles/25105759865848/)

Thank you Aitvo! I will first try Dork's proposal with VBox. But I'll keep the hardware profiles trick from your article.

> **dorkdork777 said:**
> Go to [this page]("http://www.virtualbox.org/wiki/Downloads"), and download the user manual. Read pages 106 to 108 (the whole of section 9.9) - you will become enlightened. :)

**Thanks A LOT Dork!! **This is just _pure magic:_

```
VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk
-rawdisk /dev/sda -partitions 1,5
```Wow, can't wait to try it! This is what I needed. No effort and not even a registry to update ;-)

This time I really should have... [IMG]http://www.southwestrides.com/vbulletin/images/smilies/RTFM.gif[/IMG] 

> **mimada said:**
> A lot of recovery discs won't work in a VM because it has a totally different hardware configuration.

Thank you Mike. Yes I have a special Windows XP from Sony. But the hardware profiles tip from Aitvo's article should help.

> **dorkdork777 said:**
> @mike - My Fujitsu-Siemens recovery disc works perfectly on all VMs I've tried. Not saying his Sony ones will though.

Maybe I won't be able to keep some gadgets like fingerprint reader but if I have at least my hdd and video chipset I'll be fine ;-)

If I need an optimum use of my hardware under Windows, I still have a dual boot option thanks to your help! =D> Thank you all of you for assisting me. I will try this ASAP and post results.

---

### Post by dorkdork777 on 2008-03-12
Hmm, depends what you mean by video chipset... Virtual machines don't support 3D acceleration, so you won't be able to play 3D games in the VM, but you will be able to run apps as long as they don't rely heavily on 3D.

But tell us how it goes - good luck! :)

---

### Post by Jonathan Métillon on 2008-03-12
I'm not playing any game. And the only 3D app I use is Google Earth.

---

### Post by Jonathan Métillon on 2008-03-13
I listed my partitions numbers:

```
Number  Type   StartCHS       EndCHS      Size (MiB)  Start (Sect)
3       0x82  0   /1  /1   1023/254/63          8110           63
2       0x07  1023/0  /1   1023/254/63         38154     16611210
1       0x83  1023/254/63  1023/254/63         30051     94751370
```I created my .vmdk file: 

```
sudo VBoxManage internalcommands createrawvmdk -filename /home/john/.VirtualBox/Machines/Windows.vmdk -rawdisk /dev/sda -partitions 2
sudo chown john:john /home/john/.VirtualBox/Machines/Windows.vmdk
```Then I create a new machine, and in the virtual disc manager I choose the Windows.vmdk file but it says:

```
VD: error opening image file '/home/john/.VirtualBox/Machines/Windows.vmdk' (VERR_ACCESS_DENIED).
```I have r/w access on this file with my user, I don't know why this access denied error.

I try reload VirtualBox, this time as root. My image is accepted and the new Windows XP machine created. I run it and:

```
GRUB Loading stage1.5

GRUB loading, please wait...
Error 17
```Why GRUB? Why is it not Windows launching?

---

### Post by Jonathan Métillon on 2008-03-13
I created a new .vmdk file from partition number 1 this time.

No GRUB error, but GRUB showed with my usual choice with Ubuntu or Windows. I choose Windows and:

```
Error 13: Invalid or unsupported executable format

Press any key to continue...
```

After pressing any key I'm sent back to GRUB choice. I choose Ubuntu just to see, and it worked. Ubuntu started loading. I interrupted it.

So why Windows won't load? And why can't I run VirtualBox as a normal user?

Thanks!

---

### Post by aitvo on 2008-03-13
> **Jonathan Métillon said:**
> I created a new .vmdk file from partition number 1 this time.

No GRUB error, but GRUB showed with my usual choice with Ubuntu or Windows. I choose Windows and:

```
Error 13: Invalid or unsupported executable format

Press any key to continue...
```

After pressing any key I'm sent back to GRUB choice. I choose Ubuntu just to see, and it worked. Ubuntu started loading. I interrupted it.

So why Windows won't load? And why can't I run VirtualBox as a normal user?

Thanks!

Try selecting your XP partition, then boot from the xpquick.img floppy image.

---

### Post by Jonathan Métillon on 2008-03-13
Thank you Andrew. I followed the procedure from [your article]("http://www.silverstang.com/news/articles/25105759865848/") to boot the floppy drive on xpquick.img.

I then get the following error:

```
Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file.
```

---

### Post by aitvo on 2008-03-13
> **Jonathan Métillon said:**
> Thank you Andrew. I followed the procedure from [your article]("http://www.silverstang.com/news/articles/25105759865848/") to boot the floppy drive on xpquick.img.

I then get the following error:

```
Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file.
```

Do you have partition #2 configured as your hard drive in your VM? Partition #2 is your NTFS partition, it's the one you will want to configure as a hard drive device in your VM.

Is there any way to extract the configuration from virtualbox and post it? (Unfortunately I don't have much time logged with VBox, but I'll try to help.)

---

### Post by mimada on 2008-03-13
What you are doing right now looks kind of dangerous to the integrity of your installed OSs. Can you tell me if grub is installed on the MBR or in the Ubuntu partition? It looks to me like it's in the Ubuntu partition but I want to be sure. The reason I'm worried is that you might have set your VM to boot from your Ubuntu partition. This is bad because Ubuntu is your host and loading the host OS as a guest is asking for trouble.

You might want to load up gparted and double-check to see which partition holds which OS. I guessing from your setup that Windows is in partition 2.

Mike

---

### Post by mimada on 2008-03-14
After looking over the docs for VirtualBox and Andrew's howto, I've concluded that you _have_ to use his method (you'll have to adapt it for VirtualBox). The VM has different hardware than your laptop so you need a separate hardware registry profile. The VirtualBox docs describe how to use a physical hard drive partition rather than a virtual hard drive file. It makes the assumption that you only intend to install the virtual machine in the partition rather than have a dual boot system _and_ VM.

You might want to go ahead and install VMware on your laptop if you don't feel confident about adapting Andrew's howto. It won't hurt your system to have both VM programs and once you have the laptop running the way you want it, you can uninstall VirtualBox. That way, you'll just have to follow Andrew's excellent howto.

Mike

---

