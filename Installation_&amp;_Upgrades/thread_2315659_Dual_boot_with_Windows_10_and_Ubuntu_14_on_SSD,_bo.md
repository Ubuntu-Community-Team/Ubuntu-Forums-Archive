---
title: "Dual boot with Windows 10 and Ubuntu 14 on SSD, boot logo loop before install"
date: 2016-03-01
forum: Installation &amp; Upgrades
---

### Post by r7-spam on 2016-03-01
Hello,

I think this has been asked multiple times as I found so many people with the same problem on google and Ubuntu forums, but it's usually very old thread from several years and it looks like the problem still occurs.

I cannot boot on my live USB either to try or to install. It just gets into a boot loop. Google and Ubuntu forums say to add ```
nouveau.setmode=0
```, others say to tamper with the bios, disabling fastboot, changing the UEFI settings or Legacy boot, but it just won't work and I basically have no idea why it's still stuck in the boot loop.

Why does this error still happen to many people after all these years? Am I doing something wrong or is it a recurring bug from Ubuntu?

I suppose has already been resolved so could someone point me in the right direction where the answer is?

Thanks guys!

---

### Post by oldfred on 2016-03-01
What brand/model system? And what video card/chip, or what video do you boot with?

Is system UEFI or BIOS? IF Windows pre-installed it will be UEFI and you want to boot install media in UEFI boot mode.

---

### Post by r7-spam on 2016-03-02
Hey there! Thanks for your answer!! :)

My laptop:
MSi Pe70 6QD

Video cards:
NVidia GeForce GTX950M
Intel HD Graphics 530

Windows was pre-installed but I deleted everything so I could repartition and reinstall windows with a fresh copy alongside Ubuntu. So I have absolutely no idea if I'm on UEFI or not. I also don't know which video card it's booting up with.

While waiting for your answer I will see if I can find out these infos

---

### Post by r7-spam on 2016-03-02
Found one piece of info from setupact.log:
Callback_BootEnvironmentDetect: Detected boot environment: EFI

---

### Post by oldfred on 2016-03-02
Your boot mode is probably Intel video. Some computers let you set which you use in UEFI/BIOS.

Nomodeset usually works with nVidia & AMD, but for Intel you often need different boot parameters. And some laptops need additional boot parameters also.
 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic 

Other MSI systems and yours may need similar settings even if not same model.

 [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

---

### Post by r7-spam on 2016-03-02
Thank you sir! I have a lot of reading to do now! I'll post which solution works if I can find my problem and set it as Resolved :)

Will I have to do these steps only for the initial installation, then it would be ok after this?

---

### Post by oldfred on 2016-03-02
I do not know dual video, but with nVidia you do need to install the proprietary nVidia driver. You can install from repository, or if you need newer version can add a ppa. Do not install nVidia from its .run file.

See note on recommended version
 [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) 


        # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices
sudo apt-get update && sudo apt-get install nvidia-3xx

---

### Post by r7-spam on 2016-03-02
Ok thanks, will check all this! I can edit grub.cfg on my live USB stick so I can just copy paste the grub custom boot options instead of writing them manually on every test and risk making mistakes, is that right?

---

### Post by oldfred on 2016-03-02
You should only need to edit once on live installer, when you boot to install.
But I directly boot ISO with loopmount and add nomodeset to grub since my full desktop has nVidia.

And then you need to edit first boot. If just video parameters install of proprietary driver will eliminate that. 
But if other parameters always required, then we edit /etc/default/grub in install.

---

### Post by r7-spam on 2016-03-02
Awright, thanks again!

---

### Post by r7-spam on 2016-03-04
So I read the forums you sent me, then tried a handful of different combinations of boot params, mixing them together or trying them alone. I removed "quiet" and "splash" to have more feedback, here are the results, hopefully it will give you an idea why it doesn't boot.


**CHANGES NOTHING:**
*acpi=0*
[I]acpi_osi=linux
acpi_backlight=vendor
noalpic 
libata.force=noncq[/I]


**FREEZES AT THE BEGINNING**
*nomodeset* OR *i915.modeset=0*
last line displayed:
> usb 1-8: new full-speed USB device number 4 using xhci_hcd

*i915.i915_enable_rc6=1*
last lines displayed:
> BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
EDD information not available


**GOES A BIT FARTHER AWAY IN THE BOOT PROCESS:**
*video=1920x1080-24@60* OR *video=VGA-1:1920x1080-24@60*
last lines displayed:
> /init: line 7: can't open /dev/sr0: No medium found
/init: line 7: can't open /dev/sr0: No medium found


**CLOSEST I WAS TO BOOTING:**
*intel_idle.max_cstate=0*
Still shows "/init: line 7: can't open /dev/sr0: No medium found" but goes beyhond, last lines displayed:
> NetworkManager.service <Nothing happening after this echo for about 20 seconds until the next line>
NMI watchdog: BUGL soft lockup - CPU#2 stuck for 22s! [gpu-manager:1450]
INFO: rcu_shed self-detected stall on CPU { 2} (t=15000 jiffies g=721 c=720 q=0)
INFO: task systemd:1 blocked for more than 120 seconds
     Tainted: G                L 4.2.0-16-generic #19-Ubuntu
"echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message
<All these line then repeat>


I tried mixing *video=... *with *intel_idle.max_cstate=0 *but I didn't get any better results

I saw in another post that drivers were missing with newer computers, which was causing this boot loop. There was also this line: "Same is true of the hybrid SSD/HDD units that have come out recently." and I have a M.2 SSD inside, where I planned on installing Ubuntu on the second partition. Could that be the problem?

---

### Post by r7-spam on 2016-03-04
I saved that post by the way:
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)

Will be useful once I manage to make it work :D thanks for that!

---

### Post by oldfred on 2016-03-04
I have noticed that last line is not usually the issue. It often shows error or issue several lines above, but still processes several more lines before it stops posting.
See if outright error or other driver not loaded above last line.

I just built new SFF system with Intel i5-6500 and M.2 SSD. But installed 16.04 even though not to be released until April. And it installed & works without issue. Intel only video and I needed no boot parameters at all.

Is your M.2 seen as a standard drive (mine is) or the newer NMVe?

Full spec oldfred's newest system:
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)

I have had errors similar to this when installing from an ISO on sdb to sda or sdb partitions. I needed to unmount /mnt/ISO that somehow was automounted to sda. And installer had asked to umount partitions, but did not fully work. But if just one drive that should not be your issue.
/init: line 7: can't open /dev/sr0: No medium found

---

