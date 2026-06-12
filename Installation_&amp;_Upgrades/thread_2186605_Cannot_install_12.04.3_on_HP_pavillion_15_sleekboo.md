---
title: "Cannot install 12.04.3 on HP pavillion 15 sleekbook with windows 8"
date: 2013-11-08
forum: Installation &amp; Upgrades
---

### Post by avuuren on 2013-11-08
Computer system:  [SIZE=2]HP Pavilion 15-N076ED[/SIZE]

I am not a new linux user. However I am new to windows 8 and UEFI. I bought my new laptop a couple of days ago and was not aware of the fact that on new systems it is more difficult to install ubuntu. First, I used my old LiveDVD that I still had for my old laptop with win7 pre installed. It first gave me a screen in which I had three choices (standard UEFI screen). Both the install and use ubuntu without installation did not work. Making a new LiveDVD did not work either.u
I looked at this website "http:/www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html". There are many other websites but I think they are all quite similar. This one seemed most complete and eassest to read. All steps were easy and I had the idea that it should work fine. Howeer, the final results was that nothing changed. 

In the UEFI of my HP I changed the followin
Secure boot : disabled.
Secure boot keys: empty.
Legacy mode: enabled.

I changed the boot order for both UEFI and legacy mode though my UEFI said that UEFI boot order always has priority (strange why is there a boot order then for legacy mode anywyas if it never has prioirty even in legacy mode). 

I obtain the idea that the computer still uses UEFI mode even with these changes. Why? First, ubuntu still gives me the same screen at start-up (not the somewhat nicer old screen) and maybe more important windows 8 still runs if I take out my liveDVD or liveUSB drive. As far as I know the idea is that windows should not even be able to boot when the computer is in legacy mode. 

Is there anyone who could help me? I am a little afraid that it really is a computer specific problem in the end.

---

### Post by fantab on 2013-11-08
You have to install Ubuntu in same mode [UEFI or Legacy] as Windows is installed in to keep things simple. If Windows is installed in UEFI then DISABLE 'Legacy Mode'. 
To check if Windows is booting in UEFI or Legacy run the following command from Live Ubuntu DVD/USB ["Try Ubuntu without installing"].
```
sudo parted -l
```

If in the output you see '*Partition Table = GPT*' then you are booting in UEFI, because Windows boots in UEFI only from GPT.

If you want to boot Ubuntu in UEFI mode then you HAVE to install it in UEFI mode. To install ubuntu in UEFI mode you will have to boot the ubuntu DVD/USB in EFI mode. If you successfully boot the DVD/USB in EFI mode you see a black screen with options, but if you don't then you will see regular Ubuntu's purplish color screen with options.

Ubuntu can boot with 'Secure Boot' enabled. Disabling it not a must.
However, you HAVE to [disable 'Fast Startup']("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html") in Windows 8.

Create Some space on HDD for Ubuntu. I assume you have done this already.
Install ubuntu.
If there are any problems booting either Ubuntu or Windows then use [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair") utility. Boot-repair's 'Recommeded Repair' should do the trick for you. Save the LINK to Boot-Info Summary and post it here if you still run into boot issues.

---

### Post by gordintoronto on 2013-11-08
The phrase "did not work" gives no hints about how far you got, or how you recognized that it was not working. Could you be more descriptive, please?

---

