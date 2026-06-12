---
title: "Problem Installing Ubuntu 22.04 on New Asus K3402ZA: Out of Memory, Load Kernel First"
date: 2022-10-02
forum: Installation &amp; Upgrades
---

### Post by hipeng4 on 2022-10-02
Greetings,

I bought new Asus Vivobook S14 K3402ZA with 12th Gen i5 EVO certified, 2.8K Resolution Display, and bunch of other specification. I tried to install Ubuntu 22.04 Desktop via USB Live. I was already disabled fast boot and secure boot. When i was booting to the live USB, it was entering the main installation. But soon as i hit the "Install ubuntu", it said "Out of Memory, Load the kernel first". 

I have tried many solution for this kind of problem:
1. Manually load the kernel using GRUB command line.
2. Change the GRUB config gfxmode and set resolution to fixed lower resolution.

I haven't found the fix yet.

---

### Post by TheFu on 2022-10-02
Were you wiping all other OSes on the system with your installation? 
If not, did you make room for Ubuntu to have some storage?  Empty areas of the drive, unformatted?   There needs to be 40G or more that is left unpartitioned.

---

### Post by mIk3_08 on 2022-10-03
> **hipeng4 said:**
> But soon as i hit the "Install ubuntu", it said "Out of Memory, Load the kernel first". 
Did you try to run a Memory test comes with the Ubuntu installer before you try to run the Install Ubuntu? Regards and cheers

---

### Post by hipeng4 on 2022-10-07
> **TheFu said:**
> Were you wiping all other OSes on the system with your installation? 
If not, did you make room for Ubuntu to have some storage?  Empty areas of the drive, unformatted?   There needs to be 40G or more that is left unpartitioned.

Sorry for late reply. 
I have not installed the linux to the laptop storage. It broke at the installation, at the first step. 
I burn the ISO installation image into USB Live Stick. Then I configure my BIOS/UEFI properties to disable the fast boot and the secure boot. After that, I set my boot priority to boot at the USB Installation. Soon as I save the BIOS and reboot to the USB, it doesn't show anything except the GRUB command line. I tried to mount the root using ls and cd command from the GRUB, but still no luck.
I also already set the USB Live Stick to have some persistence storage from RUFUS configuration, but same, no luck :(

---

### Post by hipeng4 on 2022-10-07
> **mIk3_08 said:**
> Did you try to run a Memory test comes with the Ubuntu installer before you try to run the Install Ubuntu? Regards and cheers

Sorry for the late reply.

Simply I cant do that. Because after booting to the USB, it show blank screen for few second and then it does'nt show any GRUB menu, but just i GRUB command prompt in small resolution (probably 800x600 and my screen is 2.8k in resolution).

Regards

---

### Post by mIk3_08 on 2022-10-07
> **hipeng4 said:**
> Sorry for the late reply.

Simply I cant do that. Because after booting to the USB, it show blank  screen for few second and then it doesn't show any GRUB menu, but just i  GRUB command prompt in small resolution (probably 800x600 and my screen  is 2.8k in resolution).

Regards
This looks familiar to me. In my experience when I  try to load new Ubuntu release in my old Acer laptop before that I try  to upgrade my RAM first. I changes it to high capacity from 4GB to 8GB.  yeah. its okay when I booted to the bios. It went well I see the RAM was  change and everything was cool when I try to configured all in my Acer  laptop bios system. Now I then try to load the new Ubuntu release I see  the grub then, when I try to test the RAM It hangs up then automatically  restarts after a few seconds of RAM test.
The new RAM I installed came from my new refurbish  HP Laptop 4 to 5yrs ago came with two stick 4GB Samsung RAM. 
Everything  is so smooth when I use this 4GB Samsung RAM to my  HP Laptop but I  decided to upgrade my RAM for some personal purposes, the hdd to ssd  then decided to use all this components to my old Acer Laptop and the  old acer laptop component like hdd is for my back-up and the two stick  2GB RAM that makes to 4GB is for sale in my small scale online fb  business display. The HP laptop went well when upgraded and also this Hp  laptop loaded with Linux Ubuntu Operating System and it works smoothly  well so far. 

Now back to my Acer laptop, once again when I try  to use my HP laptop two stick 4GB Ram to this Acer laptop and perform a  RAM test using Ubuntu live usb It hangs up then automatically restarts  after a few seconds of RAM test. Here I force to install the new Ubuntu release copy and run the install Ubuntu it went black screen after a few minutes of installation. Then I figured it out that when I try  to load the original two stick 2GB Acer RAM and perform a RAM test using  Ubuntu live usb everything went well. I try to update my Acer firmware  bios laptop but sad to say no available new firmware to the old acer  laptop. Now, I decided to display the  two stick 4GB RAM that makes to  8GB is for sale in my small scale online fb business display. just here  Regards and cheers.

---

### Post by TheFu on 2022-10-07
Don't use Rufus.  There have been issues with that tool this year. I can't really recommend any, as I use 'cp' myself.

Did you read the release notes for specific issue with some GPUs?

12th gen is really new.  We call that the "bleeding edge" for a reason.  Always best to get hardware that is 12-18 months old, unless you look forward to missing drivers, bad drivers, and discovering all sorts of new problems before everyone else.

Before attempting any install, use the Live Boot aspect of the ISO you create. How does that work? If it doesn't and you've tried different USB ports and a different brand of USB flash drive, I'd say to try a different release or different version of Ubuntu, say 20.04 Mate and see if that works. If none of them work, you are in the bleeding edge or have unsupported hardware of some sort. Sometimes, it is possible to disable specific hardware to get the install and limp along for some months until the drivers are available.

If you aren't using the entire HDD/SSD and there is some other OS on it that you don't plan to use, wipe the disk BEFORE trying anything. It probably won't help, but maybe it will?

---

### Post by hipeng4 on 2022-10-08
> **mIk3_08 said:**
> This looks familiar to me. In my experience when I  try to load new Ubuntu release in my old Acer laptop before that I try  to upgrade my RAM first. I changes it to high capacity from 4GB to 8GB.  yeah. its okay when I booted to the bios. It went well I see the RAM was  change and everything was cool when I try to configured all in my Acer  laptop bios system. Now I then try to load the new Ubuntu release I see  the grub then, when I try to test the RAM It hangs up then automatically  restarts after a few seconds of RAM test.
The new RAM I installed came from my new refurbish  HP Laptop 4 to 5yrs ago came with two stick 4GB Samsung RAM. 
Everything  is so smooth when I use this 4GB Samsung RAM to my  HP Laptop but I  decided to upgrade my RAM for some personal purposes, the hdd to ssd  then decided to use all this components to my old Acer Laptop and the  old acer laptop component like hdd is for my back-up and the two stick  2GB RAM that makes to 4GB is for sale in my small scale online fb  business display. The HP laptop went well when upgraded and also this Hp  laptop loaded with Linux Ubuntu Operating System and it works smoothly  well so far. 

Now back to my Acer laptop, once again when I try  to use my HP laptop two stick 4GB Ram to this Acer laptop and perform a  RAM test using Ubuntu live usb It hangs up then automatically restarts  after a few seconds of RAM test. Here I force to install the new Ubuntu release copy and run the install Ubuntu it went black screen after a few minutes of installation. Then I figured it out that when I try  to load the original two stick 2GB Acer RAM and perform a RAM test using  Ubuntu live usb everything went well. I try to update my Acer firmware  bios laptop but sad to say no available new firmware to the old acer  laptop. Now, I decided to display the  two stick 4GB RAM that makes to  8GB is for sale in my small scale online fb business display. just here  Regards and cheers.

I think, the problem is not on the RAM. I bought this laptop with 12 GB RAM soldered on the mainboard. 

Surfed the Internet, seeking possible answer and I discovered some of the problem lead to the integrated graphic (Intel Iris Xe Graphic).
Many thanks for the response.

---

### Post by hipeng4 on 2022-10-08
> **TheFu said:**
> Don't use Rufus.  There have been issues with that tool this year. I can't really recommend any, as I use 'cp' myself.

Did you read the release notes for specific issue with some GPUs?

12th gen is really new.  We call that the "bleeding edge" for a reason.  Always best to get hardware that is 12-18 months old, unless you look forward to missing drivers, bad drivers, and discovering all sorts of new problems before everyone else.

Before attempting any install, use the Live Boot aspect of the ISO you create. How does that work? If it doesn't and you've tried different USB ports and a different brand of USB flash drive, I'd say to try a different release or different version of Ubuntu, say 20.04 Mate and see if that works. If none of them work, you are in the bleeding edge or have unsupported hardware of some sort. Sometimes, it is possible to disable specific hardware to get the install and limp along for some months until the drivers are available.

If you aren't using the entire HDD/SSD and there is some other OS on it that you don't plan to use, wipe the disk BEFORE trying anything. It probably won't help, but maybe it will?

You might be right sir, being early tech adopter is kinda tough :(

> **TheFu said:**
> Did you read the release notes for specific issue with some GPUs?
Yes, I found some forum thread about that issue. Some suggest lowering the resolution by changing grub config gfxmode to lower resolution. But still, no solution. My laptop display powered by Intel Iris Xe integrated GPU. I just bought this laptop a week ago. It's have pre installed Windows 11. I suspect this happen due to minimal display memory (128 MB from dxdiag).

But many thanks for the insight. I will try to install with daily build installation which is already installed kernel 5.9. If there any progress or solution I will post it here.

---

### Post by mIk3_08 on 2022-10-09
> **hipeng4 said:**
> But many thanks for the insight. I will try to install with daily build installation which is already installed kernel 5.9. If there any progress or solution I will post it here. Thanks for this as this will help others when they try to load Ubuntu Operating System into their machine and encounter same thing issue with you. Regards and cheers.

---

### Post by donald187 on 2022-10-10
> **TheFu said:**
> 
12th gen is really new.  We call that the "bleeding edge" for a reason.  Always best to get hardware that is 12-18 months old, unless you look forward to missing drivers, bad drivers, and discovering all sorts of new problems before everyone else.

I'm running Ubuntu 22.04 on a 12th gen i5 and it works fine out of the box.  Dell Inspiron 3910.

```

$ cat /proc/cpuinfo  | grep 'name'| uniq
model name    : 12th Gen Intel(R) Core(TM) i5-12400

```

---

### Post by TheFu on 2022-10-10
> **donald187 said:**
> I'm running Ubuntu 22.04 on a 12th gen i5 and it works fine out of the box.  Dell Inspiron 3910.

```

$ cat /proc/cpuinfo  | grep 'name'| uniq
model name    : 12th Gen Intel(R) Core(TM) i5-12400

```

The CPU is seldom the main issue, if an issue at all, but it has happened like with the 1st Gen AMD Ryzens which had a lockup issue for months after release.  However, the new chipsets and other peripherals like wifi chips and new standards put into hardware BEFORE the standards have been completed have a history if showing problems.  Of course, some peripherals, like a finger print reader, may never have drivers for Linux.  Touchpads can be flakey.  Back in 2010, USB3 support was poor for some systems and took over a year to become stable.

It doesn't always happen, but there are risks on the bleeding edge.  Sorry if I didn't make the point as clearly as possible.

---

### Post by donald187 on 2022-10-10
> **TheFu said:**
> The CPU is seldom the main issue, if an issue at all, but it has happened like with the 1st Gen AMD Ryzens which had a lockup issue for months after release.  However, the new chipsets and other peripherals like wifi chips and new standards put into hardware BEFORE the standards have been completed have a history if showing problems.  Of course, some peripherals, like a finger print reader, may never have drivers for Linux.  Touchpads can be flakey.  Back in 2010, USB3 support was poor for some systems and took over a year to become stable.

It doesn't always happen, but there are risks on the bleeding edge.  Sorry if I didn't make the point as clearly as possible.

Thanks.

I always enjoy your posts by the way. Always full of lots of information. :)

---

