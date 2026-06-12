---
title: "Ubuntu Server 20.04.4 LTS installation fail"
date: 2022-08-13
forum: Installation &amp; Upgrades
---

### Post by sats-nkamotho on 2022-08-13
I installed Ubuntu Desktop version successfully on my NUC11 but then realised I needed Ubuntu Server instead. I then created a USD bootable stick and attempted to install the Server version. This ended up in the Gnu Grub screen and I found some tutorials to get back to Ubuntu territory. At some point I rebooted (with flashdrive in USB slot) and the Server installation ran.  I followed the instructions as best I could and finally rebooted the NUC, but now I end up with a black screen asking for my username and password. It accepts my creds and appear to load the welcome screen and system info, but then leaves me with a blinking cursor.  Any assistance will be appreciated.

---

### Post by SeijiSensei on 2022-08-13
The server edition is designed to be used without a GUI interface. Most administrators use SSH to connect remotely then type in commands.

I suggest you install the desktop version, then add any packages you need to provides services. Under the hood the server and desktop versions are identical; they differ in what packages comes with them by default.

What do you need a server for?

---

### Post by TheFu on 2022-08-14
The difference between a "desktop" Linux and a "Server" linux is just the default packages installed and most Linux servers don't have any GUI, because those GUI packages aren't installed. This is by design, but not what people coming from MS-Windows expect.  There isn't any difference in licensing, concurrent users supported, RAID, network capabilities or anything else.  The exact same kernel is used in the Ubuntu desktops and Ubuntu servers. They are the same OS.  Don't confuse programs with the OS.  In Unix, the GUI isn't the OS, it is just another program for our convenience.  We can choose from many different GUIs (DEs and/or Window Managers), not just the few that are made into "distros" like Kubuntu, Lubuntu, PopOS, Mint, Xubuntu, etc.... It is our choice and extremely flexible.

I cannot think of anything that a server can do that a desktop cannot do as well, except the server will use vastly fewer resources. But on modern computers, there are so any excess resources that typically doesn't matter.  A case could be made that "servers", without any GUI or GUI packages would be more secure, since GUI programs introduce lots more code and more code means more bugs.  That's a truism for all code.  More code == more bugs.  Also, a typical server admin would likely be more security conscious and capable than a typical desktop user. That is probably the biggest aid in system security.

Not that I didn't say anything about user friendliness in either system.

---

### Post by sats-nkamotho on 2022-08-14
Any idea how I can get rid of the Desktop version as I really just need the Server version. The plan is to set up an ETH2 staking node and this should be as simplistic as possible (less code, less bugs like you say)

---

### Post by TheFu on 2022-08-14
> **sats-nkamotho said:**
> Any idea how I can get rid of the Desktop version as I really just need the Server version. The plan is to set up an ETH2 staking node and this should be as simplistic as possible (less code, less bugs like you say)

What's your skill level with Ubuntu?  I suspect it is less than needed to accomplish, besides installing the server version directly.  
Are you prepared for a console and to use only ssh for all management? If you haven't been running Linux at least 6 months, daily, and know about the steep learning curve required, stick with a desktop.

OTOH, if you have, then, remove all GUI tools. That will be both the X/Server and Wayland/Server. I've never done it. Might make for a system that won't boot, so you'll need a "Try Ubuntu" flash drive to boot to go in under a chroot and correct any boot issues, while doing some cleanup.  If this scares you - good.  But it also means you should probably run a desktop, for a few more months to build more skills.  On the desktop, you can still manage everything using ssh only, logged in from another workstation.

---

### Post by SeijiSensei on 2022-08-14
I think it isn't worth the effort to pare down the distribution. Do you want to get work done or play with Linux? I've been doing Linux networking for over thirty years and have no idea what a "ETH2 staking node" might be. If it's just networking, you probably don't need any additional software. Otherwise what packages do you need to install? 

Remember once the system is up and running the GUI pretty much gets out of the way. You could, if you like, just open a terminal instance in full-screen and forget that the GUI exists.

---

### Post by sats-nkamotho on 2022-08-16
> **TheFu said:**
> What's your skill level with Ubuntu?  I suspect it is less than needed to accomplish, besides installing the server version directly.  
Are you prepared for a console and to use only ssh for all management? If you haven't been running Linux at least 6 months, daily, and know about the steep learning curve required, stick with a desktop.

OTOH, if you have, then, remove all GUI tools. That will be both the X/Server and Wayland/Server. I've never done it. Might make for a system that won't boot, so you'll need a "Try Ubuntu" flash drive to boot to go in under a chroot and correct any boot issues, while doing some cleanup.  If this scares you - good.  But it also means you should probably run a desktop, for a few more months to build more skills.  On the desktop, you can still manage everything using ssh only, logged in from another workstation.

My skill level is atrocious, I'd say. Google on one screen, Ubuntu on the other. From what I understand, the application I'm interested in, requires the absolute minimum from an OS, hence Server over Desktop, I assume.

---

### Post by sats-nkamotho on 2022-08-16
> **TheFu said:**
> What's your skill level with Ubuntu?  I suspect it is less than needed to accomplish, besides installing the server version directly.  
Are you prepared for a console and to use only ssh for all management? If you haven't been running Linux at least 6 months, daily, and know about the steep learning curve required, stick with a desktop.

OTOH, if you have, then, remove all GUI tools. That will be both the X/Server and Wayland/Server. I've never done it. Might make for a system that won't boot, so you'll need a "Try Ubuntu" flash drive to boot to go in under a chroot and correct any boot issues, while doing some cleanup.  If this scares you - good.  But it also means you should probably run a desktop, for a few more months to build more skills.  On the desktop, you can still manage everything using ssh only, logged in from another workstation.

Is the a simple way to check whether Ubuntu Desktop is still on my SSD, or would my installation of Server 20.0.4 LTS have removed automatically.  Things are not stable at the moment and I was getting Kernel Panic restarts yesterday.  Another very starnge thing is that when Server boots up and waits for my username, the cursor jumps to the left most character of that line. By hitting enter, it give me a fresh command line and I'm able to enter my username and password.  Lastly, I'm also seeing a "[   66.768297] hdaudio hdaudioCOD2: Unable to bind codec" message. Again, by hitting enter, I'm presented with "nu11 login: <blinking cursor> and I can log on.

---

### Post by TheFu on 2022-08-16
> **sats-nkamotho said:**
> My skill level is atrocious, I'd say. Google on one screen, Ubuntu on the other. From what I understand, the application I'm interested in, requires the absolute minimum from an OS, hence Server over Desktop, I assume.

You should install a desktop, then add whatever server stuff you want.  That will be frustrating enough for someone new who isn't willing to learn the basics, in-order, first, before jumping beyond intermediate level topics.

But you can do anything you like and long-term passion in any subject can easily override other considerations. It is your system.

---

### Post by bingodingo on 2022-08-16
You can spend a lot of time trying to fix a broken installation (or in this case pair two installations down to one) but it's often faster to do a clean install (and you'll generally get a more reliable result).
When you can do everything you want to in the desktop environment, you could start learning how to do everything in that environment from the terminal and change to a server installation when you're good at that.

---

