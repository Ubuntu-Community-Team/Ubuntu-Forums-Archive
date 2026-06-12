---
title: "Upgrading"
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by leg on 2013-05-31
Hi all, 

       its been a while since I have upgraded my laptop and it is complaining that I need to upgrade to 12.04. I am not on it at the moment and can't remember which version I am on but definitely behind a bit. I am assuming that it is recommending 12.04 as that is the most recent LTS release. My question is that 13.04 has been out for a while so what problems have people found with it. One thing I am keen to know is if the problems with MTP phone connections are still there or if I would be able to connect my Samsung s3 mini and browse the file system.

I intend to upgrade this weekend and would appreciate general opinions as to which of these two versions I should go for.

Thanks

---

### Post by leg on 2013-05-31
Sorry can I get this moved to the correct category?

---

### Post by ibjsb4 on 2013-05-31
13o4 is supported for 9 months; 12o4 for 5 years.

---

### Post by mörgæs on 2013-05-31
I would say that General Help is a fine forum, but if you prefer another please let me know.

The restriction for Samsung S3 is due to Android 4 and not a decision by Buntu. Here is a explanation: 
[http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access)

Whichever release you decide it's better to do a fresh install. It's a healthy approach to wait a few months after release, as you are doing.

---

### Post by 3rdalbum on 2013-05-31
Ubuntu 13.04 finally has decent MTP support so you can work with your phone without a workaround. But you would need to upgrade to 13.10 shortly after it comes out.

You might want to just stick with 12.04 as it will be supported for nearly four more years. Up to you!

---

### Post by leg on 2013-05-31
> **mörgæs said:**
> I would say that General Help is a fine forum, but if you prefer another please let me know. Its just that I saw another called installation and Upgrades which seems more appropriate.

> **mörgæs said:**
> 
The restriction for Samsung S3 is due to Android 4 and not a decision by Buntu. Here is a explanation: 
[http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access)
 Yes I have found the explanation for Google changing and I have also found some tuts for getting it all to work so I am not to worried about that any more.

> **mörgæs said:**
> 
Whichever release you decide it's better to do a fresh install. It's a healthy approach to wait a few months after release, as you are doing.
Yes I don't usually upgrade immediately but I think I left it a bit too long this time. Do you really recommend a fresh install? I was intending to go through the upgrade procedure. I have taken this approach many times and there are always a few little things that need attention once done but I have always thought it works quite well.

---

### Post by leg on 2013-05-31
> **3rdalbum said:**
> Ubuntu 13.04 finally has decent MTP support so you can work with your phone without a workaround. But you would need to upgrade to 13.10 shortly after it comes out.

You might want to just stick with 12.04 as it will be supported for nearly four more years. Up to you!Do you say I would need to upgrade because 13.10 is an LTS release.

---

### Post by 3rdalbum on 2013-05-31
13.04 is only supported for nine months, so you would need to upgrade at the end of it. The next LTS is 14.04.

---

### Post by leg on 2013-05-31
> **3rdalbum said:**
> 13.04 is only supported for nine months, so you would need to upgrade at the end of it. The next LTS is 14.04.

ok thanks

---

### Post by mörgæs on 2013-05-31
Moved.

---

### Post by fantab on 2013-05-31
IMO fresh install is good idea. For one it is 'fresh', clean and new. Upgrades can be messy especially from 10.04 to 12.04.. there have been some big changes in between.

---

### Post by leg on 2013-06-02
ok I have upgraded but I have a problem with my boot menu. It hasn't changed and is showing the entries I had before and not the new 13.04 entry. I have run update-grub and grub-mkconfig and the menu.lst file appears correct but the items in that file are not the ones displyed. The /boot/grub/grub.cfg file has what appears to be the entries I am seeing under a section headed ### BEGIN /etc/grub.d/10_linux ###. When I do boot I appear to be in the correct distribution as the log on screen states Ubuntu 13.04 in the bottom left but I have no virtual desktops. I expect I have other problems but I haven't got past this one yet. Any ideas how to correct the boot menu and makle sure that I am using the correct kernel?

ps just checked and uname -r returns 2.6.35-25-generic when I should be using 3.8.0-23.generic. If I get this fixed I think all will be ok.

---

### Post by fantab on 2013-06-02
From Grub Menu choose 'advanced option for Ubuntu', pick the kernel you want to boot into.
Check with 'uname -r'.

You can use 'Synaptic Package Manager' to remove older kernels.

---

### Post by mörgæs on 2013-06-02
Menu.lst is a leftover from Grub 1, which was the boot loader used by Buntu 9.04 and earlier. Grub 2 uses grub.cfg.

---

### Post by leg on 2013-06-02
In the end I re-installed from my live usb and tht has sorted the boot menu issue and I am now booting into 13.04 correctly and have confirmed the kernel with unsme -r. However I now have a problem with the wireless driver. My network port is broken and I rely on the wireless connection for everything. The hardware is:
```
product: BCM4312 802.11b/g LP-PHY
```

I am currently on the live usb distro typing this and the wireless works fine. When on my installed version the wireless driver is not recognised and if I go to the settings -> software & Updates -> additional drivers the broadcom is identified but not selected. If I click use this driver the process fails and the selection moves back to do not use. I have had problems with this before <[This Thread]("http://ubuntuforums.org/showthread.php?t=2086166")> but that doesn't work for me this time. 

Any ideas as to how I get my wireless driver installed?

---

### Post by leg on 2013-06-02
I have tried updating a couple of times now and the problem may be steimming from an error I get when the installs trys to re-install software. It states that an error occured and I may need to manually install after reboot. Some things I have noticed is that synaptic and some other software is not available. Is the wireless driver meant to be installed because of this and how can I stop the error?

---

### Post by mörgæs on 2013-06-02
I suggest that you post again in the other thread, explaining what the problem is now.

---

### Post by leg on 2013-06-03
I will but I am not sure it is the same issue. I had to do a fresh install into my Ubuntu partition in the end which fixed the general software issues but not the wireless one. I have had a search for this and found one or two suggestions but yes you are quite right I will update that thread to see if they know anything.

thanks.

---

