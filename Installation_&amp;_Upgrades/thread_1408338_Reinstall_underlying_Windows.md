---
title: "Reinstall underlying Windows"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by Cisc0 on 2010-02-16
Hello!

I installed Ubuntu 8.10 with Wubi under Windows XP. Now the Windows XP installation is damaged due to some filesystem stuff and doesn't boot anymore. Ubuntu still boots and works well.

So I want to reinstall Windows. But, I want to use Windows 7 instead of XP. What I want to achieve is, that after the reinstall process I have the same Dual-Boot menu but with Windows 7 and Ubuntu.

Windows XP is currently installed on Windows Partition C:, Wubi/Ubuntu is installed on another partition D: (where also a lot of Windows files are located).

So can anyone tell me the steps, or point to some documentation how to do this? I don't actually think it's a huge problem, but I wanted to know in advance, what exactly to do before the point of no return. It's extremely important that the ubuntu installation will not be damaged or sth.

Thank you very much,
fabi

---

### Post by howefield on 2010-02-16
I don't think you can save your Wubi install. Someone will correct me if that isn't the case.

This might be an opportunity for you to go for a real dual boot. 

Wubi installs are pretty much intended to give you a flavour of the operating system, if you intend to use it for an extended period of time, Wubi isn't really the way to go.

---

### Post by tommcd on 2010-02-16
> **howefield said:**
> I don't think you can save your Wubi install. Someone will correct me if that isn't the case.

This might be an opportunity for you to go for a real dual boot. 

Wubi installs are pretty much intended to give you a flavour of the operating system, if you intend to use it for an extended period of time, Wubi isn't really the way to go.
This is true. The developer of Wubi even says that:
> Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.
See this interview:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
So do a clean install of Windows 7 to whatever size partition you want. Leave space for Ubuntu. For a great site for getting started with doing a real dual boot with Ubuntu see:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
another great resource for dual booting with Ubuntu:
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

And for Cisc0,
Welcome to the Ubuntu forums!!

---

### Post by Cisc0 on 2010-02-16
Hmm. That's actually surprising. I thought Wubi installs in an NTFS-Container-File and uses the standard Windows Booting mechanism? And it is impossible to backup the container and "reactivate" it with a new windows installation? That's actually hard to believe ;-)

My problem is: I need a working Windows installation and I currently don't have time to reinstall ubuntu completely as a real dual-boot system.

---

### Post by darkod on 2010-02-16
> **Cisc0 said:**
> Hmm. That's actually surprising. I thought Wubi installs in an NTFS-Container-File and uses the standard Windows Booting mechanism? And it is impossible to backup the container and "reactivate" it with a new windows installation? That's actually hard to believe ;-)

My problem is: I need a working Windows installation and I currently don't have time to reinstall ubuntu completely as a real dual-boot system.

Why don't you boot wubi (which still works) and copy to ext hdd what ever data you want to keep from it.
Then just temporary forget about it and install win7, but don't forget to install it only to a part of the hdd, not the whole. Otherwise you have to shrink it later for ubuntu.
Then when you have the time just do a proper ubuntu install as already suggested and put the data back on it if you want to.

One of the main benefits of proper dual boot is in fact that the OSs reside on independent partitions. You are losing that advantage with wubi, that's the price you pay for the easy install. Not that installing full linux is complicated.

It's not that hard to believe. Don't forget, windows is also involved here, not just ubuntu. Do you think it offers a simple way to re-attach the wubi data? Windows bootloader doesn't even provide booting other OSs, not to mention what you are asking for.

---

### Post by howefield on 2010-02-16
> **Cisc0 said:**
> Hmm. That's actually surprising. I thought Wubi installs in an NTFS-Container-File and uses the standard Windows Booting mechanism? And it is impossible to backup the container and "reactivate" it with a new windows installation? That's actually hard to believe ;-)

I didn't say it was impossible, just that I didn't think it could be done (easily). After all, it is only software. Question is whether you will spend more time finding out, than the time it takes to install Ubuntu.

In the 30 minutes since your original post, Ubuntu could be installed twice, maybe even 3 times :) 

> My problem is: I need a working Windows installation and I currently don't have time to reinstall ubuntu completely as a real dual-boot system.

Sure is a bummer when you don't have a robust backup strategy.

---

### Post by tommcd on 2010-02-16
> **Cisc0 said:**
> Hmm. That's actually surprising. I thought Wubi installs in an NTFS-Container-File and uses the standard Windows Booting mechanism? And it is impossible to backup the container and "reactivate" it with a new windows installation? That's actually hard to believe ;-)
As Howefield said, I don't believe this is possible. Why would you want to continue using Ubuntu this way anyway? You would surely get much better performance in Ubuntu doing a proper install.
> **Cisc0 said:**
> 
My problem is: I need a working Windows installation and I currently don't have time to reinstall ubuntu completely as a real dual-boot system.
I can do a clean install of Ubuntu in about 20 minutes. It then takes perhaps another hour, at the most, to get the updates and reinstall all the programs I use and set things up the way I want. Most of this time is spent waiting for stuff to happen. If you have times to install Windows 7, then you have more than enough time to install Ubuntu.
Understand that installing Ubuntu becomes easier the more times you do it. You will have to do some reading to get the most out of Ubuntu, or any linux distro. The links I gave in my last post are a great place to start.
Write back if you need more help with this.

---

### Post by Cisc0 on 2010-02-16
> **tommcd said:**
> I can do a clean install of Ubuntu in about 20 minutes. It then takes perhaps another hour, at the most, to get the updates and reinstall all the programs I use and set things up the way I want. Most of this time is spent waiting for stuff to happen. If you have times to install Windows 7, then you have more than enough time to install Ubuntu.


And exactly this is the point, that's not true in my case ;) I'm not a Linux Professional, I used to be a Windows user. It took me very long to have my Ubuntu configured the way I needed it (e.g., video driver for multi-display, eclipse with pydev and svn plugin, thunderbird with all plugins, etc.)

Now my Wubi-Ubuntu does exactly what I need it for. I'm not sure whether I'll need it at all in the future. But it would have been very nice to simply reuse this installation, if i need it for something.

---

### Post by steveneddy on 2010-02-16
Wubi is simply a way for one to try out Ubuntu while running Windows.

Wubi is not stable and will cause issues.

If you don't want to dual boot (I don't) use VirtualBox under Windows to run Ubuntu and you can get the best of both worlds.

I run Ubuntu Intrepid and have VirtualBox running Vista and 7. they run great in a VM and I have no issues.

I also created an .iso of the Windows OS's so that if there were any issues I can simply remount the .iso and go again.

---

### Post by Mark Phelps on 2010-02-16
When you install Win7, do you expect it to retain all your XP files, settings, and applications?  Well ... it won't!  MS has repeatedly said that the ONLY upgrade path they will support from XP to Win7 is a clean install.

So, since that is, by definition, removing ALL your MS Windows files, apps, and settings -- and since Wubi installs Ubuntu just like any other MS Windows app, why should IT be recoverable when others MS Windows apps are not??

BTW, if you want to really "upgrade" to Win7 from XP -- using an approach that WILL retain your stuff -- then check out Laplink PC Mover Windows 7 Upgrade Assistant.  This $20 app will allow you to do an in-place upgrade.  You may not be able to retain everything, but you won't lose everything, either.

---

### Post by tommcd on 2010-02-17
> **Cisc0 said:**
> And exactly this is the point, that's not true in my case ;) I'm not a Linux Professional, I used to be a Windows user. It took me very long to have my Ubuntu configured the way I needed it ...
I am not a linux professional either. In fact, I have no technical background at all. I did not grow up with computers either. I purchased my first (Windows) computer when I was 42 years old. At that time I was so clueless I did not even know what Internet Explorer was! I had never even heard of linux at that time either.
I taught myself all this stuff from doing lots of reading. You can learn this stuff. I did. If you can install and configure Windows, then you can learn to install and configure linux. You won't learn it all in one day though. But all the information you need is readily available.

---

### Post by howefield on 2010-02-18
> **Cisc0 said:**
> And exactly this is the point, that's not true in my case ;) I'm not a Linux Professional, I used to be a Windows user. It took me very long to have my Ubuntu configured the way I needed it (e.g., video driver for multi-display, eclipse with pydev and svn plugin, thunderbird with all plugins, etc.)

I suppose this is a bit different to not having the time, as you'd said earlier.

You could save your /home and reuse, and generate an installed package list to make reinstallation of your packages easier. That would sort out most of your customisations/configurations. 
 
It doesn't take a "Linux Professional" to install UBuntu, if you can install Windows and all the accessory stuff that you'll need for it, then you can install Ubuntu.

How did you get on, I'm interested in the route that you choose.

---

