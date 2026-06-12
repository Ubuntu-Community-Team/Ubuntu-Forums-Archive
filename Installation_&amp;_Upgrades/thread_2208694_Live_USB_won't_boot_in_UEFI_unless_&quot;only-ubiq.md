---
title: "Live USB won't boot in UEFI unless &quot;only-ubiquity&quot;. Once installed, still won't boot."
date: 2014-03-01
forum: Installation &amp; Upgrades
---

### Post by Bromskloss on 2014-03-01
In UEFI mode, booting from a live USB memory and choosing "Try Ubuntu without installing" leads to a halt with a black screen (with and without "nomodeset").

Choosing instead "Install Ubuntu" (i.e., the "only-ubiquity" option) and "nomodeset", the installer launches and seems to work fine. However, booting into the installed version leads to a black screen again.

I have tried "Intel(R) Rapid Start Technology" enabled as well as disabled.

So, How do I boot Ubuntu in UEFI mode?

---

### Post by oldfred on 2014-03-01
What system and model? Some work easier than others.
 What CPU chip & video chip?

If dual video you may be booting with Intel and need different settings.

You need to have Intel SRT off. It used to not install unless you removed RAID meta-data from drive but if you change to AHCI then it may install. But grub may not install correctly.

Lots more info in link in my signature.

---

### Post by Bromskloss on 2014-03-02
> **oldfred said:**
> What system and model? Some work easier than others.
 What CPU chip & video chip?

If dual video you may be booting with Intel and need different settings.

[The model](http://www.webhallen.com/se-sv/datorer_och_tillbehor/182021-webhallen_config_l13-0303_133_full_hd-i7-4700mq-16gb-750gb__128gb_ssd-gtx765m-win_8) is based on [Clevo W230ST](http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=474).

CPU: Intel Core i7-4700MQ
Video: Nvidia GTX765M

> **oldfred said:**
> You need to have Intel SRT off.

Will do!

> **oldfred said:**
> It used to not install unless you removed RAID meta-data from drive but if you change to AHCI then it may install. But grub may not install correctly.

What would your instructions be here? I've been told that AHCI is what I normally should choose, but I don't know the implications so I can't judge for myself.

> **oldfred said:**
> Lots more info in link in my signature.

Whoa, indeed! Thank you. I'm going to have to buckle up and see if I can find out what applies to me in it.

---

### Post by oldfred on 2014-03-02
Also that is a new Haswell chip & video. That may have a few added issues, but Intel has been good at updating video driver, kernel & support software, but all those fixes are only in the newest distributions. Some have actually had better success with 14.04 which of course is still a couple of months from release. I cannot recomment 14.04 unless you want to experiment as it may have breakage due to other issues. Some like that in solving issues, others get frustrated. 

Can you set which video it uses to boot or is it automatic? Some turn off nVidia and just use Intel video, but that needs different settings, usually.

 Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)

        Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

While a Dell note comment on Intel chip issue common with many vendors
      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

If you have it installed post link to Boot-Info report. But if you can get grub menu, you are into video mode and possibly other boot parameters to get it to work.
       [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Bromskloss on 2014-03-06
> **oldfred said:**
> Can you set which video it uses to boot or is it automatic?

I don't know how to do that.

I have looked at the links you provided, but I'm not sure what applies to my situation.

To potentially clarify my situation: When the screen goes black, I can still do Ctrl+Alt+F1 and get a prompt. If I then do "startx", I get a few errors. Here's "/var/log/Xorg.0.log" as well as the output from "dmesg" and "lspci":

[Xorg.0.log](http://paste.ubuntu.com/7044217/)
[lspci](http://paste.ubuntu.com/7044227/)
[dmesg](http://paste.ubuntu.com/7044228/)

---

### Post by oldfred on 2014-03-06
It is saying no screens found?
And it looks like you have Intel which only has one open source driver but needs different boot paramters than nomodeset. And may need other parameters.
Try some of the options suggested in link below by ubfan1
Did you read the Dell link. It says you may need to have CSM mode on even if booting in UEFI mode as Intel has some issue of some sort.

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by Bromskloss on 2014-03-06
> **oldfred said:**
> It is saying no screens found?

Yes, and on another line it says that screens are found. Here are all the errors from "Xorg.0.log":

```

[   125.383] (EE) open /dev/dri/card0: No such file or directory
[   125.384] (EE) VESA(0): V_BIOS address 0xd00 out of range
[   125.384] (EE) Screen(s) found, but none have a usable configuration.
[   125.384] (EE) 
[   125.384] (EE) no screens found(EE) 
[   125.384] (EE) 
[   125.384] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   125.384] (EE) 
[   125.391] (EE) Server terminated with error (1). Closing log file.

```

I now realise that I get the same errors also when booting with "only-ubiquity", which works.

> **oldfred said:**
> 
Did you read the Dell link. It says you may need to have CSM mode on even if booting in UEFI mode as Intel has some issue of some sort.


Do you mean [this link](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)? I don't know what "CSM" is. Wikipedia turns up Compatibility Support Module. Is that it? I don't have any such option in the BIOS menu. (Well, perhaps it isn't called "BIOS menu" these days.)

> **oldfred said:**
> Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)


Tried those with no effect.

> **oldfred said:**
> 
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

Whoa! That's a lot of parameters.

---

### Post by oldfred on 2014-03-06
BIOS is what we have had since the beginning of the PC over 35 years ago.
UEFI is the new replacement for BIOS but offers CSM. But various vendors use CSM, BIOS, Legacy, AHCI and maybe others.
 UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

A few computers now are coming out with Class 3 UEFI, which leaves out the CSM. Eventually that will be all computers as then it saves once chip and all the old BIOS software support.

Finding what combinations of boot parameters are required is difficult. I might suggest searching Web for any Linux boot of your model or similar models by same vendor. 

You will need at least settings for Intel video but then what added settings varies.
Also some have black screen and it is just that setting is low and f8(or whatever) key needs to be pressed to increase brightness.

Some with Haswell chips find 14.04 works. But it is not offical till April.

---

