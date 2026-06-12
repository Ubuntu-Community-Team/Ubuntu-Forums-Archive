---
title: "problem installing firefox on Ubuntu 10.10"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by dan103 on 2014-05-28
Being a complete newbie, re: anything Linux/Unix/Ubuntu related, I could use some serious help with my very first complete install of Ubuntu. I have a good knowledge of Windows installation; but, that's not the problem. 

I had started with ver 14.04 but ran into issues with the particular machine I was using (as it was already dual-booting into WinXP and Win7). So, I decided to use an older Dell OptiPlex GX110. It has a 900MHz PIII chip, 512mb of RAM, 20GB drive and XP SP3 already installed (running quite well, surprisingly). Figuring it was best to use an older version of Ubuntu, I happened to have downloaded, some time ago, version 10.10.

Using a free partition management software (Aeomi Partition manager) I carved out a 6GB logical drive and created a 2GB extended partition inside it.

The Ubuntu install went very well (amazingly for my first try), but now I would like to upgrade the Firefox 3.6 to a newer version and possibly install Chrome as well, if at all possible.

Again, my Ubuntu/Linux knowledge is very limited, so I anticipated that it would require a simple file download, then run the typical "setup.exe" or "install.exe" file; Wrong! ](*,)

After downloading a "tar" file (whatever that is) I realized it had to be extracted; but, where and what to do after? :confused: 

Not a clue.

Thanks for any help you can offer.


Dan

---

### Post by Bucky Ball on 2014-05-28
You'd have problems installing lots of things on 10.10. It hasn't been supported for ages. I would avoid going online with it. I'd advise using 12.04 LTS if 14.04 is not working for you. Use something like Lubuntu or Xubuntu even, or try a minimal install. I'm surprised you're getting half decent results with Ubuntu 10.10 using 512Mb of RAM, though. 14.04 wouldn't like that and neither will 12.04 if you stick with a straight Ubuntu install.

---

### Post by dan103 on 2014-05-28
Bucky, thanks! I was unaware of 10.10 issues; not even sure when I d/l'd it. This particular pc was basically a "throw away" model that, if something went wrong, it wouldn't be a disaster. However, I will give the 12.04 version a try and see how that works. Thanks again!

Dan

---

### Post by dan103 on 2014-05-28
Oops.. forgot to ask.. how do you install firefox in Ubuntu? There's no simple setup solution I'm aware of. Thanks.

---

### Post by mörgæs on 2014-05-28
I would give it Lubuntu 14.04, but expect a low performance anyway. 
Firefox is standard in this release.

---

### Post by Bucky Ball on 2014-05-28
> **mörgæs said:**
> 
Firefox is standard in this release.

^^^
This. Firefox is the default in current releases, no need to install. You would otherwise use Software Centre, Synaptics package manager or a terminal to install. Simply:

sudo apt-get install firefox

---

### Post by dan103 on 2014-06-05
Bucky, again thanks. I've decided to move to the 14.04 version on a Dell GX260 running Win7 Pro. In order to install Win7, on this machine, I had to install a newer graphics card, as Win7 has no drivers for the built in one. This, being an older pc, has an AGP slot; installed an Nvidia geforce 6200 512mb AGP card which has been running fine. BTW, the pc has 2GB RAM (the most it can take), 3.05 GHz Hyperthreading PIV processor.

I created a 25GB boot partition and a 2GB extended partition for swap. Booting off the 14.04 DVD, I get the man icon with keyboard, then press "enter". At that point the display goes black and nothing further appears to happen. I have to force power off the pc to reboot into Windows. My feeling is the AGP card is the problem, but not sure how to get the appropriate drives loaded when I'm unable to even see an install screen.

---

### Post by mörgæs on 2014-06-05
For Nvidia it's often necessary to add the **nomodeset** boot option.

---

### Post by Bucky Ball on 2014-06-06
> **mörgæs said:**
> For Nvidia it's often necessary to add the **nomodeset** boot option.

Yep, try this. When you are at the first screen when installing, hit F6; you should find 'nomodset' as an option there. Choose it. ;)

---

### Post by dan103 on 2014-06-06
Awesome! that worked perfectly. Now that I have it fully installed and functional (many thanks to Morges and Buckyball) it is running but extremely slow. I do not believe that's a function of the RAM or processor; my feeling is that Ubuntu is not happy with the video card and needs the correct driver for it (I've run into this same problem with Windows). 

Doing searches for other software, it appears installing drivers in Ubuntu is not as easy as double clicking a "setup.exe" file as in Windows. I've seen some postings where very complex commands have to be entered in cryptic locations.

Can you folks offer me some assistance in installing the correct Nvidia driver for this pc?

While on that topic, I've noted that, when using the command line instructions, there is often a request to enter the password for "root". Unfortunately, the password I entered when installing Ubuntu is not the same for "root". Does anyone know if there is a default "root" password?

Many thanks for you help with this.

Dan


Thanks.

---

### Post by mörgæs on 2014-06-06
So far so good.
In post #2 you were warned that Ubuntu might be too heavy for old computers. A fresh install of Lubuntu is a better start.

---

### Post by Bucky Ball on 2014-06-06
Check 'Additional Drivers' (or it might be 'Hardware Drivers') and see if there is a driver available.

---

