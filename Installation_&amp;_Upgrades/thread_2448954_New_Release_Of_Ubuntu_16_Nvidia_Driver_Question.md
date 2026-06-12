---
title: "New Release Of Ubuntu 16: Nvidia Driver Question"
date: 2020-08-17
forum: Installation &amp; Upgrades
---

### Post by O)9(yo&amp;# on 2020-08-17
I was excited to see that they released an updated Ubuntu 16 (16.04.7). I am currently running 14.04, as my 6150SE mobo requires the Nvidia 304 driver (I signed up for the extended support).

My first attempt at trying out 16.04.7 worked, but was a long ordeal, as I had to first install 14.04, then upgrade it to 16.04.7. This is because if I don't have the 304 driver working right from the start, I can't switch it via Additional Drivers, because the screen goes crazy (I can make the switch on 14; it behaves long enough for me to do it on that system).

However, I accidentally installed the 32 bit version of 14. So when upgraded to 16. that made it 32 bit as well. I discovered my mistake when I couldn't install Free Office. Couldn't figure out why until I checked and discovered the error (how did I do such a boneheaded thing? I had both 32 and 64 bit on different USB's, and I simply grabbed the wrong one).

So, I want to finally get the 64 bit version of 16.04.7 going. But I would like to do a clean install, and avoid the several hours involved in an upgrade. How can I get the Nvidia driver running before I boot up? Could I do it via safe mode, using a terminal? I think I have a tutorial on that somewhere if I can find it, but any tips here would be great!

Thanks!

---

### Post by grahammechanical on 2020-08-17
Before wiping out that 32 bit install run these commands

```
ubuntu-drivers list
ubuntu-drivers devices
```

Allow time for the commands to work and you will not only see some information about your graphic card but any proprietary drivers available for that graphic card.

As for your question: 

At the Grub boot menu select Advanced options for Ubuntu. 
Then select a Linux kernel that includes the words "recovery mode."
At the Recovery menu select Network to establish an internet connection.
When back at the Recovery menu select Root shell prompt and enter this command

```
ubuntu-drivers autoinstall
```

That will install the latest (or only) proprietary drivers for your graphic card. You can Exit Root shell prompt by typing Exit. At the Recovery menu selecting Resume will load Ubuntu with an open source driver. Resume always does that. A shutdown and reboot should load Ubuntu with the installed proprietary driver.

You could also at the Root shell prompt enter this command

```
shutdown now -r
```

That should reboot without loading Ubuntu from the Resume option.

Regards

---

### Post by O)9(yo&amp;# on 2020-08-17
Thanks a bunch for that. Only thing is, I need specifically the 304 driver. anything later won't install on that mobo. And open source drivers won't work. but I can just install the 304 with the same command, plus "Nvidia-304" right?

---

### Post by O)9(yo&amp;# on 2020-08-17
I just remembered - I need the driver not just installed, but selected. I believe it is already installed with the system on 14 and 16, and you make the switch in Additional Drivers. But the problem is, with the open drivers, which are used by default, the screen goes nuts, so I can't navigate there and make the switch. so I need a way to do that in the terminal in Recovery Mode.

---

### Post by O)9(yo&amp;# on 2020-08-18
SOLVED: I was able to open a terminal and pull up the Additional Drivers dialogue with  "software-properties-gtk". I first had tried navigating to it via the launcher, but the screen froze. It didn't distort, which was an improvement over the old 16.04 with open-source drivers, but I still couldn't do anything, so I restarted and did it the other way. Took awhile, but it switched to Nvidia 304, and now it's working great. Ubuntu, you did a cool thing in making this new version of 16.04 available!

---

### Post by mastablasta on 2020-08-19
great! yes, you can do it via command line.
first
```
[COLOR=#000000][FONT=menlo]ubuntu-drivers devices[/FONT][/COLOR]
``` 
to detect.

then ```
sudo ubuntu-drivers autoinstall
```or in your case to install specific version
```
sudo apt install nvidia-304
```

then reboot.


so the 16.04.7 version keeps xserver and stuff at the same version? i though they upgrade those as well? does that mean they only update kernel? curious because my card's driver time is ticking as well.

---

### Post by O)9(yo&amp;# on 2020-08-19
> **mastablasta said:**
> 



so the 16.04.7 version keeps xserver and stuff at the same version? i though they upgrade those as well? does that mean they only update kernel? curious because my card's driver time is ticking as well.

Actually, the second time rebooted it threw me for a moment. It appeared to be on VGA graphics (everything way too big); and I could not login. also, got an error message. I booted into Recovery, and saw that it had in fact updated the kernel. must have done it while I wasn't looking! Anyway, I booted into 4.4 and everything was back to normal.

The bug report I looked at (via the error message) talked about how 304 no longer works past kernel 4.4, and maybe 304 needs to be retired. Fortunately, 4.4 is the first SLTS kernel, so machines needing it can count on it until at least 2024, and possibly beyond.

---

### Post by deadflowr on 2020-08-19
Just make sure you only have the linux-generic/linux-image/header-generic packages installed and not the linux-generic-hwe related packages.
The linux-generic packages have the 4.4 kernels and always will on 16.04,
But the hwe related packages are based on the kernels used for the newer release (currently 4.15, which it should stay at)
Ref: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

I believe the 304 driver does work beyond the 4.4 kernel but not beyond at most 4.14.
But from Ubuntu's standpoint, there are no supported Ubuntu kernels between 4.4 and 4.15 so it's rather moot.

---

### Post by O)9(yo&amp;# on 2020-08-19
> **deadflowr said:**
> Just make sure you only have the linux-generic/linux-image/header-generic packages installed and not the linux-generic-hwe related packages.
The linux-generic packages have the 4.4 kernels and always will on 16.04,
But the hwe related packages are based on the kernels used for the newer release (currently 4.15, which it should stay at)
Ref: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I believe the 304 driver does work beyond the 4.4 kernel but not beyond at most 4.14.
But from Ubuntu's standpoint, there are no supported Ubuntu kernels between 4.4 and 4.15 so it's rather moot.

Thanks, I appreciate the info. I'm a little confused, though. Which is the later kernel, 4.14 or 4.4? Logically it would be 4.4, but i'm not sure that's right. I have 4.1 something showing in grub as the first listed kernel. I have to scroll down to boot 4.4. I'm going to eventually either alter grub, or uninstall the other kernel so booting will be easier. I have some tutorials I can use.

Thanks also for the link, some good info there.

---

