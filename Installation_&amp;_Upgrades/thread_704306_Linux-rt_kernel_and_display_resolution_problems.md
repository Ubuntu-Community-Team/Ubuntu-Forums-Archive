---
title: "Linux-rt kernel and display resolution problems"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by Paco758 on 2008-02-22
I have just installed UbunuStudio along with the linux-rt kernel over an install of Ubuntu Gutsy vanilla-style. I am having trouble with the screen resolution, however. I can still boot with the vanilla kernel with no problem, but when I boot using the rt kernel, X uses a failsafe config and I get a resolution of 1024x768 at the highest. When I attempt to edit xorg.conf, it breaks the configuration for either kernel and I have to reset the configuration using the "dpkg..." command. 

I have tried setting the display properties using both the GUI and by manually editing the configuration in xorg.conf, but neither seem to work to make the display the correct resolution when booting with the rt kernel. To clarify again: everything works fine with the vanilla kernel booted. The display resolution breaks and has a repeat on the y-axis when the rt kernel is booted.

For reference I am running Ubuntu Gutsy on a Sony VAIO VGN-NR290E with an Intel Core2 Duo T5450 and Intel integrated graphics controller GM965. I understand that there are a few kinks with the experimental driver which is being used for this controller, so perhaps this is part of that set of kinks.

Any suggestions/info will be greatly appreciated. I will post on this thread if I find a solution on my own.

---

### Post by rocketman768 on 2008-04-16
I did the exact same thing and am having the same issue. Are you using the nvidia driver?

I am using the restricted nvidia driver from the repository, and it just fails to load at boot time and instead loads the vesa driver and goes for a generic monitor, completely ignoring my xorg.conf settings for my card and monitor. There are no errors in /var/log/Xorg.0.log except that I see it loads vesa.

WTF mate? :confused:

---

### Post by Paco758 on 2008-04-16
Nah, I'm using the Intel experimental mode-setting driver. I don't think that the problem has to do with the video card though. Are you also having trouble during a vanilla install with brightness and hotkeys?

---

### Post by rocketman768 on 2008-04-17
Nope. I'm using it on a desktop, so no brightness issues to deal with or hotkeys either. However, I do have a Sony Vaio N365E/B and it works right out of the box with the hotkeys and brightness.

So, anybody know what's going on with the resolution with the linux-rt kernel?

---

### Post by Paco758 on 2008-04-18
Alright man, I don't know what happened, but I have been poking around with the 8.04 Beta for the past couple of days. I installed the 64 bit version from the Alternate Install disk. I had been running the 32 bit version before on the same laptop because I had a wonky time with 64 last time I tried it, and I figured that I could live without full hardware acceleration for the time being. 

Today I installed the RT kernel just to see if there would be a difference, and there was. It works perfectly well. I'm not sure what is going on. 

I would still be interested to know if anyone else has had similar problems. I intend to test and see if I can get it to break again and try to figure it out, since there are more than a few factors which have changed since my last attempt. We shall see.

---

### Post by rocketman768 on 2008-04-18
Weird. I too would be able to run the 64-bit version if that fixes it. Let me know how your experience with it goes (if there are any really annoying quirks).

---

### Post by Paco758 on 2008-04-19
I would go for it. Just back up your stuff and run the install CD. I installed from the Alternate Install disk for 8.04 Beta. I had one small trouble during the install though, GRUB would not install, so I just let it install LILO instead. I was able to manually install GRUB after that. It doesn't matter though if you're not particular about your bootloader, I just prefer GRUB. 

I just got it running Jack server with LSM for apps and it works great. Good luck and let us know how it goes. 

Which system are you running again (model/specs)? I'm still interested in the graphics card issues with some Intel cards. 

Cheers.

---

### Post by rocketman768 on 2008-04-22
It's a PC I put together.

Mobo = Intel 82945G
RAM = 2.0GB DDR PC2700
CPU = 3.4 GHz Pentium D
Sound = Audigy ES
Graphics = GeForce 7950 GT (PCI-express)

I will try the other version soon.

---

