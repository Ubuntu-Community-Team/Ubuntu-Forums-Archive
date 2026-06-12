---
title: "low memory mode installation"
date: 2004-10-27
forum: Installation &amp; Upgrades
---

### Post by sleepyhead on 2004-10-27
I'm trying to install Ubuntu on an old laptop with only 32 MB memory.  While the installer is loading with the message "Loading components of the Ubuntu installer", I keep getting a low memory message, that says:

Entering low memory mode: This system has relatively little free memory, so it will install in low memory mode. Among other things, this means that the installation will proceed in English.  You should set up swap space as soon as possible.

I press enter to continue, it start over trying to load components, then the low memory message comes back.  I'm stuck in this loop. Can I somehow set up swap space before loading the installer? Or is there another way to install Ubuntu on a low memory system?

Thans!!

Doug

---

### Post by jdong on 2004-10-27
Yeah, Ubuntu doesn't install with that little RAM. It's the debian-installer's fault... If you can "borrow" some RAM, it'll only need it for installation.


Also, what are you gonna do with that laptop? I can't imagine anything more than a console with a computer that limited!

---

### Post by sleepyhead on 2004-10-27
I'm trying to set it up for my sister-in-law. It would be her first PC, she's a complete noobie. I don't think she even knows how to turn it on! All she wants to do is email family in Vietnam, and maybe browse the Web a bit.

I was hoping to run it with a minimalist  DE like fluxbox or iceWM. It runs Windows98 decently, so I'm hoping it can run a minimal Linux setup...

---

### Post by cj2003 on 2004-10-28
I am trying exactely the same as you, sleepyhead - installing on a 32mb system - and gets also the same error message.

I haven't been able to solve it....but at least you should know that you're not alone!

Christian

---

### Post by jdong on 2004-10-28
I've experimented with this setup a bit from VMWare, and came to conclude that it's impossible to install Ubuntu on 32MB RAM.


Your best bet is to install the Ubuntu system on another computer, use **tar** or **cpio** to zip it up, then unpack it onto the laptop.

---

### Post by liberal_tugboat on 2004-11-23
you might be able to install if you partion first using knoppix live CD or the like and make a swap partition, then all you would need to do in mount the swap partition before you start the setup. 
dont ask for instructions cause I havent tried it. jsut making a suggestion to help you along!

---

### Post by Chibi on 2004-11-25
Just some theory here, but if you happen to have two floppies laying around, you can make a slackware rescue disk set, ad cfdisk a swap partition.. Then use mkswap and swapon from busybox to activate the partition? With such little memory, you might not even want to use ubuntu. It ran horrid on my 586 pentium with 32 megs of ram. You should probably spend the time to teach her a little bit and fall back to slackware or some such.
 I personally avoided the 32 meg problem by using the 24meg readline installer for debian sarge, then installing ubuntu over it. The results were NOT pretty, mind you. I managed to get a base system running, but after booting into X with Gnome... Ouch.
 Dropline Gnome for Slackware Linux is /almost/ par with ubuntu. The only thing you may be lacking is APT, which yes, can be a pain in the ass, but your sister probably doesn't really need apt if she's going to have a setup of no more than mail and web-browsing. Mind you, the tests I made on my old machine with ubuntu versus slack were only boottime and app startup times, The most notable diffrence being mozilla-firefox at 15minues with ubuntu versus 2 minutes on slackware.
 If you're willing to go as far as rough hacks for a low memory install of ubuntu, you're probably better off with a more old-optimized distro like slackware or arch anywho, as the difficulty setting up would be the same, and she'd have about the same ability to break either if you keep her locked out of root, and on runlevel 3 where she can't touch the console. n_n;

 By no means am I going against ubuntu here, I'm just speaking from experience that it doesn't run even feasible on low-end machines. (Mainly the fault of all those daemons and gnome). I use ubuntu on my main box, It's a great distro and runs terrific, giving a bright new face to debian-- But debian is about apt, maximum compatibility, and lots of pre-packaged software choices. All of which she should be able to live without.

 I tested my little mkswap theory while writing this. The mkswap succeeded, the addswap succeeded, but the installer still didn't use the swap. Ubuntu won't be easy, unless you prepare your own disc with the readline debian installer.. And you'll probably need to make rough hacks to that unless you want to install debian first.

---

### Post by wallijonn on 2004-11-26
Is there any way that you can use one of the "f" keys to get to a manual / minimal  install when booting? Then you might be able to select what parts get installed.

---

### Post by free on 2005-05-11
[QUOTE=jdong]I've experimented with this setup a bit from VMWare, and came to conclude that it's impossible to install Ubuntu on 32MB RAM.

Well, last night I did an instalation of Hoary on 32MB RAM box, so i don't agree :)

Try to do this:

- first, I assume you have prepared partitions, and that you have one of them set up as swap and remember which one it is

- when you get the firts prompt booting your CD, type in "server-expert" (as far, as i remember it right:))

- go through all install process as far as it goes.

- when the installer realizes it can't go further because of low memory, it kicks you to some menu with particular stages of installation process. Somewhere on the "very" bottom of this menu list, find an option to get to command prompt, or how it is called.

- in this prompt type
  "swapon [and the device, where your swap partition is]"
  in my case it was "swapon /dev/hda5", for instance. It should activate your swap partition and use it during the rest off installation process.

- get back to that previous installation menu typing "exit".

- and now, get back to that stage where you were stopped and kicked to this menu. 

I was trying  to get that ubuntu thing on my 200mhz pentium box with 32RAM. I have no net connection on that box and I don't have  that unofficial ubuntu addon CD mentioned on [http://www.ubuntuguide.org](http://www.ubuntuguide.org), so no X 'n' stuff yet. Just follow the low mem howto to set up GUI part, if you wish.

Things may be different in reality, you know I'm just more experienced BFU. I don't remember them exactly, but the main idea is to get to the command prompt in "server-expert" mode and to "swapon" already prepared swap partiton.

Good luck.

---

### Post by heinous on 2005-05-17
I had the same problem and ended up creating a custom initrd to be small enough to use  for netbooting with ide modules in it so that swap could be created and activated.  Notes at : [http://wiki.heinous.org/index.php/Ubuntu_Notes](http://wiki.heinous.org/index.php/Ubuntu_Notes)

I hope it is useful.

---

### Post by az on 2005-05-17
"
Well, last night I did an instalation of Hoary on 32MB RAM box, so i don't agree

Try to do this:

- first, I assume you have prepared partitions, and that you have one of them set up as swap and remember which one it is"

That is the point.  He does not have partitiona premade.  That is why you are succeding and he is not.


You should be good to go using the slackware boot disks, or the debian boot disks.

Actually, even a windows boot disk has fdisk.  You can use that to make a swap parttition.  Make it about 100 metgs big.  When the installer boot, it will try to use that for virtual memory.  Google around at how to make a linux swap partition with fdisk.

---

### Post by free on 2005-05-20
For creating swap, resizing ntfs and other things i've found [http://www.sysrescd.org](http://www.sysrescd.org)  quite useful. It has only _110MB_. ...yes, there might be something better, but this works in my case.

---

### Post by sciurus on 2005-05-21
Good luck setting up Ubuntu, but you might want to try [Deli](http://www.delilinux.de/).

---

### Post by ensenadaubuntulover on 2005-05-22
[QUOTE=sciurus]Good luck setting up Ubuntu, but you might want to try [Deli](http://www.delilinux.de/).[/QUOTE]
 Is there a DELI ubuntu? I would love that, really. with some fluxbox and sinaptic will do. My laptop is pentium II and 32 mb ram and runs in Mandrake 9.0 already for like 3 years but this ubuntu is something but I can not install it yet.

---

### Post by silver on 2005-05-22
I'm going to recommend two distros that I like as they are both very light weight.

  [http://minislack.slackplanet.org/](http://minislack.slackplanet.org/)

  and

  [http://www.vectorlinux.com](http://www.vectorlinux.com)

I personally prefer Vectorlinux though it's a "work in progress".

---

### Post by mjgumbley on 2005-05-23
I also tried installing Ubuntu (Warty) on a 32 MB laptop, with no success. 

I only want a very basic system, X with a minimalist WM, bash, vim, perhaps firefox and a decent PDF reader. perl, ruby & g++ would be a bonus ;-) I won't be doing enterprise Java development on this system!

I started with the Ubuntu Mini RAM HOWTO from
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

I had previously successfully installed Red Hat 7.3 on this system, which had created a ~100 MB swap partition on /dev/hda3. However, I wanted something a little more modern and had the Ubuntu CDs, so...

Inserted Ubuntu install CD, booted with 'custom', got to the point where it warned me about low memory, hit enter, it loaded the IDE drivers...

I used Alt-F2 and Enter to activate a second console, did a swapon /dev/ide/... part3 (analagous to /dev/hda3, but I could only see the /dev/ide tree, no block special file with the exact name /dev/hda3), then switched back to the installer with Alt-F1.

At some point soon, the installer decided it needed to run the partitioning tool, which it started to do, only to get to 35%, then crash. I couldn't coax any better results out of it - I didn't really want to partition, as RH had done it for me, but the installer wouldn't let me install the base system - it kept trying to run the partitioner... crash.


I'm hoping Hoary will be a little better than this!

Can Warty be successfully installed on such a system? Should I wait for my Hoary CDs to arrive?

---

### Post by JackDeth on 2005-05-26
[QUOTE=sleepyhead]I'm trying to install Ubuntu on an old laptop with only 32 MB memory.  While the installer is loading with the message "Loading components of the Ubuntu installer", I keep getting a low memory message, that says:

Entering low memory mode: This system has relatively little free memory, so it will install in low memory mode. Among other things, this means that the installation will proceed in English.  You should set up swap space as soon as possible.

I press enter to continue, it start over trying to load components, then the low memory message comes back.  I'm stuck in this loop. Can I somehow set up swap space before loading the installer? Or is there another way to install Ubuntu on a low memory system?

Thans!!

Doug[/QUOTE]

I'm having virtually the same problem. Except mine gets to a point where I get "Cannot allocate memory" and then I repeatedly get "Segmentation Fault" about 5-6 times and then the system reboots itself or just hangs. Sometimes I get "Out of Memory - Killed Process ####" where the #### is some four digit number in the two thousands, usually different each time.

I've tried unsuccessfully to follow some of the suggestions listed here. I'm stuck on some of them, though. 

> Just some theory here, but if you happen to have two floppies laying around, you can make a slackware rescue disk set, ad cfdisk a swap partition.. Then use mkswap and swapon from busybox to activate the partition?
Does anyone have a copy of these they could ZIP and email to me (jackdeth @ tds.net)?

> Is there any way that you can use one of the "f" keys to get to a manual / minimal install when booting? Then you might be able to select what parts get installed.
What key(s)? Does anyone know how to do this? Is there a special "command line parameter" I should type in when starting the install to tell it to do a low memory install?

> Well, last night I did an instalation of Hoary on 32MB RAM box, so i don't agree :) 

Try to do this:

- first, I assume you have prepared partitions, and that you have one of them set up as swap and remember which one it is

- when you get the firts prompt booting your CD, type in "server-expert" (as far, as i remember it right)

- go through all install process as far as it goes.

- when the installer realizes it can't go further because of low memory, it kicks you to some menu with particular stages of installation process. Somewhere on the "very" bottom of this menu list, find an option to get to command prompt, or how it is called.

- in this prompt type
"swapon [and the device, where your swap partition is]"
in my case it was "swapon /dev/hda5", for instance. It should activate your swap partition and use it during the rest off installation process.

- get back to that previous installation menu typing "exit".

- and now, get back to that stage where you were stopped and kicked to this menu.....the main idea is to get to the command prompt in "server-expert" mode and to "swapon" already prepared swap partiton. 
I did FDISK and format the drive. I have two partitions. Drive C is 100mb and D is 1100-something (it's a 1.28gb drive). I am really really **really** new to all this and don't know how to tell linux how to create a swapfile it will recognize as I cannot even get that far in the install.

I get through the server-expert install process as the writer says, but where they say to "go as far as it goes" until it kicks you to some menu....it doesn't kick me to the menu again. It reboots the whole damn machine after giving me memory allocation and segmentation fault errors. Even if I selected the "low memory" option off one of the menus during the installation setup phase.   If I try to go to the "command shell" from the menu *before* I run through the installation steps to use the "swapon" command, it does work. It gives me errors that it doesn't recognize /dev/hda5 (or any other number). I don't understand why it won't recognize my partitions.

This is really frustrating to someone who is new to all this but still at least considers themselves a reasonably intelligent human being. :-x 

Can anyone please help with more details information on how I can get through this process? Especially "free", since it sounds like you've been through this already?

TRS

---

### Post by ensenadaubuntulover on 2005-05-26
[QUOTE=heinous]I had the same problem and ended up creating a custom initrd to be small enough to use  for netbooting with ide modules in it so that swap could be created and activated.  Notes at : [http://wiki.heinous.org/index.php/Ubuntu_Notes](http://wiki.heinous.org/index.php/Ubuntu_Notes)

I hope it is useful.[/QUOTE]


wow read it but is too far reaching for me!

I will wait to the ubuntu low memory install that I hope with my fingers crossed that someday will apear mean while I will try the Mr. free aproach.

---

