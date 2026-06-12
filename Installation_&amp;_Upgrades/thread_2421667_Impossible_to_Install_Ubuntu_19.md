---
title: "Impossible to Install Ubuntu 19"
date: 2019-06-25
forum: Installation &amp; Upgrades
---

### Post by whisper1530 on 2019-06-25
I tried to install Ubuntu 19. I booted from a flash drive. After seeing the Ubuntu logo, I was met by a black screen. That's it. I then booted using the "nomodeset" option. I booted and it worked! I tried to install additional drivers from the "Software and Updates" program. I looked under "Additional Drivers." There was nothing there. So, I went to AMD's website to download their drivers. The problem is that they are for Ubuntu 18 only. They would not install on Ubuntu 19.

So now I'm stuck. I can't install Ubuntu because it says there are no drivers available for me to download. I would greatly appreciate any help I could get in resolving this frustrating situation.

My Hardware:
[LIST]
[*]Intel Core i5-6500 Processor 
[*]AMD R9 390 Graphics Card 
[*]16 GB of RAM 
[/LIST]

---

### Post by oldfred on 2019-06-25
What motherboard?

Were you trying to install additional drivers from live installer or after booting into your install.
Normally AMD does not need additional drivers.

       [https://ubuntuforums.org/showthread.php?t=2372733](https://ubuntuforums.org/showthread.php?t=2372733)
If your card is supported by AMDGPU, it will be installed when you install Ubuntu. You can only install the AMDGPU-PRO overlay if AMDGPU is installed. If your card is not supported by AMDGPU, the Radeon driver will be installed.
It's automagic now. You don't need to do anything unless you have a need or pressing desire for the overlay-- for instance if you need Vulkan support. In that case, AMD has a script that will take care of it. 
[https://www.amd.com/en/support/kb/faq/gpu-635](https://www.amd.com/en/support/kb/faq/gpu-635)

---

### Post by whisper1530 on 2019-06-25
Thanks for getting back to me so quickly. Please understand I am very new to Linux.

I do understand that these drivers should be installed automatically. The reason I believe it is a driver issue is because I was able to install Ubuntu 18.04 and 18.10. I did this by selecting "nomodeset" and installing drivers from AMD's website for my GPU using the terminal. (I did this after I installed Ubuntu 18. To be clear, I installed Ubuntu 18 using "nomodeset," then, after the installation, still booting with "nomodeset," I installed these drivers.)

I have no interest in that overlay you were talking about. (I didn't even know about it.) I would just very much like for Ubuntu 19 to work for me.

My motherboard is an MSI Z170A SLI.

---

### Post by oldfred on 2019-06-25
Many issues are common by brand (MSI any Intel) and/or chipset(Any brand 170).
So similar Intel based MSI may have same issues.

       MSI turn off external SATA
[https://ubuntuforums.org/showthread.php?t=2411446](https://ubuntuforums.org/showthread.php?t=2411446)
MSI x299 SLI Also acpi=off boot parameter
[https://ubuntuforums.org/showthread.php?t=2371556](https://ubuntuforums.org/showthread.php?t=2371556)
MSI Z170M Intel i7 6700 GTX 980TI 16.10 does not work, 16.04 does
[https://ubuntuforums.org/showthread.php?t=2357641](https://ubuntuforums.org/showthread.php?t=2357641)
Gigabyte Z170 Nvidia 970 16.04   UEFI Settings required                         
[http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04](http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04)
[https://ubuntuforums.org/showthread.php?t=2341704](https://ubuntuforums.org/showthread.php?t=2341704)

---

### Post by whisper1530 on 2019-06-26
I read through the hyperlinks you included in your post. While they didn't directly solve my problem, they gave me the idea to update my motherboard's BIOS. I did. Now, the GRUB menu is HD instead of the blurry resolution it was before. I tried to install Ubuntu 19 again. Again, to install it I had to use "nomodeset." This time, however, when I clicked "Try Ubuntu without Installing," the live desktop was also in HD. In the past, this live desktop option also had a blurry resolution I couldn't change. So, I installed Ubuntu 19 from here. It went fine. I restarted my PC and selected the operating system; however, the same thing happened. It shows the logo for a bit, then an unchanging black screen. I have to shutdown my PC by holding the power button. It is the only way it will cooperate.

---

### Post by oldfred on 2019-06-26
Try nomodeset when booting the install.

But I thought nomodeset was not required with AMD video, you may need a different boot parameter.
Some motherboards also have settings to turn on/off video. Or you can set it to use Intel video which should let you boot and see that it only is the video issue or not.
You also may want to review other UEFI video settings to see if one needs changing.

Found this:
[https://forum.level1techs.com/t/amd-r9-390-finally-usable-on-linux/131922](https://forum.level1techs.com/t/amd-r9-390-finally-usable-on-linux/131922)
Which also says to do this:
[https://wiki.archlinux.org/index.php/AMDGPU](https://wiki.archlinux.org/index.php/AMDGPU)

---

### Post by whisper1530 on 2019-06-26
I read through the two hyperlinks you sent. I followed their instructions. I added:

radeon.cik_support=0 radeon.si_support=0 amdgpu.cik_support=1 amdgpu.si_support=1

after the "linux" line. I got there by pressing "e" on the Ubuntu 19 option on the GRUB menu. I booted by pressing F10. Then, I got an HD Ubuntu logo loading screen. Afterwards, a black screen appeared with a blinking cursor at the top let of the screen. We're getting somewhere? (I hope.)

---

### Post by oldfred on 2019-06-26
Those parameters may conflict?
You have either Radeon or AMDgpu.
       Linux 4.15 Is A Huge Update For Both AMD CPU & Radeon GPU Owners
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.15-AMD-Mega](https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.15-AMD-Mega) 
    
Its supposed to be automatic now with AMD.
        Ryzen 2400G UEFI issue on 4K at 60Hz
[https://ubuntuforums.org/showthread.php?t=2387396](https://ubuntuforums.org/showthread.php?t=2387396)

Raven Ridge With The Ryzen 5 2400G On Mesa 18.2 + Linux 4.17 Is Finally Stable MSI B350M GAMING PRO
[https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1) 
   
After adding "GRUB_GFXMODE=1920x1080x32" to the grub config the next reboot Ubuntu worked perfectly, both monitors fully functional and I could watch videos 
   [https://ubuntuforums.org/showthread.php?t=2372733](https://ubuntuforums.org/showthread.php?t=2372733)

If your card is supported by AMDGPU, it will be installed when you install Ubuntu. You can only install the AMDGPU-PRO overlay if AMDGPU is installed. If your card is not supported by AMDGPU, the Radeon driver will be installed.
It's automagic now. You don't need to do anything unless you have a need or pressing desire for the overlay-- for instance if you need Vulkan support. In that case, AMD has a script that will take care of it. 
[https://www.amd.com/en/support/kb/faq/gpu-635](https://www.amd.com/en/support/kb/faq/gpu-635)

---

### Post by whisper1530 on 2019-06-28
This is my current situation.

When I try to install Ubuntu 18, I select the boot media and wait. It shows me a logo and then a black screen. It is nescesary that I boot using nomodeset. Otherwise, nothing will occur. Once I install Ubuntu 18, I restart. Again if I do not use nomodeset nothing will happen, so I do. I'm now in Ubuntu 18; however, each time I want to boot into Ubuntu 18, I must manually add nomodeset. If I use nomodeset, however, the resolution is low and the system lags. So, I install drivers from here [https://www.amd.com/en/support/graphics/amd-radeon-r9-series/amd-radeon-r9-300-series/amd-radeon-r9-390](https://www.amd.com/en/support/graphics/amd-radeon-r9-series/amd-radeon-r9-300-series/amd-radeon-r9-390) and install them using instructions from here [https://www.maketecheasier.com/install-amdgpu-pro-drivers-ubuntu/](https://www.maketecheasier.com/install-amdgpu-pro-drivers-ubuntu/). Now, I can boot into Ubuntu 18 without changing anything during boot, and the graphical errors are gone.

When I try to install Ubuntu 19, the same thing happens as before. I must use nomodeset to boot. Otherwise, I get a black screen. When I get into Ubuntu 19, the same things are true: it is a low resolution and performs poorly. I tried to install the same drivers I did before; however, they say they are not compatible with Ubuntu 19. So, I tried the advice of this video [https://www.youtube.com/watch?v=97fj4bGJxVM](https://www.youtube.com/watch?v=97fj4bGJxVM). It forces the Ubuntu 18 AMD drivers to install onto Ubuntu 19. This time, after doing this, when I booted Ubuntu 19, it resulted in a flashing white cursor at the top left of my screen in HD. I again must boot using nomodeset to use Ubuntu 19.

You might be wondering, "Why not just use Ubuntu 18 if it's working?" I normally would, but it behaves strangely. It won't launch or install many programs. For example, when I launch Davinci Resolve, my cursor shows that my computer is busy, then nothing happens. Also, when I try to install Trelby [https://www.trelby.org/](https://www.trelby.org/) it launches the software centre. When I click install, the progress bar proceeds super fast and when it is complete, does not give me the option to launch, just to install again.

Additionaly, I tried to install Ubuntu 19 as an upgrade through Ubuntu 18. When it completes and I boot, I get a black screen with tons of white and green text. It won't proceed past that.

---

### Post by whisper1530 on 2019-07-05
In this discussion about Manjaro Linux, the participants concluded that it is not possible to use Manjaro using an AMD R9 390 graphics card.
[URL="https://forum.manjaro.org/t/r9-390-still-not-working-blackscreening/16397/14"]
https://forum.manjaro.org/t/r9-390-still-not-working-blackscreening/16397/14[/URL]

---

