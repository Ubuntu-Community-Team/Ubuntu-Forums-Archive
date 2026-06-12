---
title: "Problems with install"
date: 2016-09-06
forum: Installation &amp; Upgrades
---

### Post by 11mobi11 on 2016-09-06
Hi, 

I have similar problem. First time when I tried install it everything was fine I went through all the screen's till partition step. Then I stopped installation because somehow I couldn't make partition as I wanted so I came back to Windows and there I split my disk. Since then each time Im trying install it it's stops on loading screen and no matter what i try is neither live cd or installation. 
Sometimes it's freez completely and Caps Lock button start to blink. 
I even tried other Linux editions for example Arch but with same result laptop is getting hot same like my usb memory stick with Os on it.

---

### Post by Bucky Ball on 2016-09-06
*Post moved to own thread.*

Welcome. Your problem is similar, but not the same. They rarely are. You will always get better support specifically for your issue by posting your own thread with as much detail as you can give about your problem. It also avoids confusion and leaves the original poster of the thread the space to fix their issue. 

Post your machine specs and what release of Ubuntu you are trying to install please. You aren't attempting to install Wubi are you, Ubuntu inside Windows? That is no longer supported so suggest you don't go there if you are.

> somehow I couldn't make partition as I wanted 

This is fairly ambiguous but more detail will possibly get us to the problem. And the fact you couldn't make the partitioning how you wanted seems to be the problem. What did you do and what went wrong? Without this information we'd be guessing. :)

---

### Post by 11mobi11 on 2016-09-07
Right i should be more specific.
I was following this tutorial:
```
 http://www.linuxandubuntu.com/home/dual-boot-ubuntu-15-04-14-10-and-windows-10-8-1-8-step-by-step-tutorial-with-screenshots
```
As I was saying before I stopped on partition making step. What I did wrong before is I forgot to shrink space form my already existing partitions to make free space for ubuntu. So that is why I returned to w10 I split the  hard drive and i tried return to installation without success.

Ubuntu i was try to install is the newest available version.

---

### Post by Bucky Ball on 2016-09-07
16.04 is the newest *supported* version. 16.10, due out in October, is available but not yet for general consumption. For the moment, will assume you're talking 16.04 LTS. :)

Ok, let me know when I'm wrong: you have booted the install media, are installing, get to the partition section, choose Something Else, you are looking at your existing partitions and you have a large chunk of unallocated space to install Ubuntu on. What seems to be the problem? The only detail you have given is

> i tried return to installation without success.

? Again, what went wrong? What's the issue? More detail about the 'without success' part, please. Error messages, if any, please. What you've tried to fix, if anything. :-k

Also, what exactly do you already have installed on there? You are looking to do dual-boot with Windows? That guide is for a triple-boot, although the principles are the same.

---

### Post by 11mobi11 on 2016-09-08
The issue was described in the topic where I wrote my post in a first place. 
So the problem now is, when I'm trying run installation it's stops on the loading screen. It's this one: ```
 [https://www.google.co.uk/search?q=ubuntu+loading+screen&client=ms-android-samsung&prmd=ivn&source=lnms&tbm=isch&sa=X&ved=0ahUKEwjT55a7jIDPAhXkCsAKHaNKCtAQ_AUIBygB&biw=360&bih=560#imgrc=6dX0FcFa9TsooM%3A](https://www.google.co.uk/search?q=ubuntu+loading+screen&client=ms-android-samsung&prmd=ivn&source=lnms&tbm=isch&sa=X&ved=0ahUKEwjT55a7jIDPAhXkCsAKHaNKCtAQ_AUIBygB&biw=360&bih=560#imgrc=6dX0FcFa9TsooM%3A)
```
I was waiting 30min nothing was happening. 
First time when i lunched installation there was no problem.

Is there a place where the installation files are being kept? Maybe formatting this place would help somehow

---

### Post by Bucky Ball on 2016-09-08
When you boot the install media and get to the purple screen with the icon down the bottom of the screen, hit any key. That should take you to 'Try Ubuntu' 'Install Ubuntu' etc. 

Hit F6. A bunch of options should pop up. Choose 'nomodeset'. Proceed.

---

### Post by 11mobi11 on 2016-09-12
F6 does nothing. Another attempt of "Try Ubuntu" stopped on, check attachment for screenshot.

---

### Post by 11mobi11 on 2016-10-15
UP

Any idea what should i do ??

---

### Post by oldfred on 2016-10-15
Are you trying to boot live installer or after install to hard drive?
What are system specs, brand/model and video card/chip?
Is hardware UEFI or BIOS, and then are you booting Ubuntu in same boot mode as Windows is installed, UEFI or BIOS?

---

### Post by 11mobi11 on 2016-10-25
So I'm trying to do both live/install nothing works.
UEFI shows negative.
I tried with Mint edition same results. I made some pictures.
In first attachment, installation was showing same screen and from time to time first numbers was changing for higher one 100, 200, 300, and so on.
This is my laptop:
```
https://www.amazon.co.uk/HP-15-ah150sa-A10-8700P-Certified-Refurbished/dp/B01BYNR8UQ
```

Recently I was trying different usb sticks. Every time fist thing what I was doing was choosing option Check USB for defects. Few times it showed errors so then I was coming back to W10 and making bootable usb again. But even with 0 errors it didn't work.

UPDATE

I managed to install it but basically problem is still the same. Now when I try to start Ubuntu black screen appears, after few minutes of waiting caps lock starts to blink.

---

### Post by oldfred on 2016-10-25
I really do not know AMD, graphics can be an issue, but if the open source graphics work then you should be ok.
But you may need nomodeset and/or other boot parameters.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If booting in UEFI mode you only get grub menu. Then you need to manually add nomodeset both to install and maybe to boot after install.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710) 

      
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file) 
    I think this is all after install issues, but perhaps some clues on HP?

 Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244) 
      
 Envy M6 Change boot order sudo efibootmgr -o 2,1 post #23
[URL="http://ubuntuforums.org/showthread.php?t=2227889"]http://ubuntuforums.org/showthread.php?t=2227889
[/URL]
 HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975) 

[URL="http://ubuntuforums.org/showthread.php?t=2227889"]
[/URL]

---

### Post by 11mobi11 on 2016-10-27
I read this articles and all other topics you have posted. 
And somehow I manged to install it, but it's still not working. 
Now when Im trying to boot ubuntu or it showes black screen or some logs and kernel panic. 
Other options like recovery mode etc also are not working.

---

### Post by oldfred on 2016-10-27
Not sure with AMD, but you probably need some other boot parameters probably in addition to nomodeset. 
Or it may be some added settings in UEFI/BIOS.

One other HP used this boot parameter. See links above for a variety of boot parameters.
       acpi=off  worked for HP2000

See also:
[http://askubuntu.com/questions/821762/cant-install-ubuntu-on-hp-probook-455-g3](http://askubuntu.com/questions/821762/cant-install-ubuntu-on-hp-probook-455-g3)

---

### Post by 11mobi11 on 2016-11-01
Yesterday I have tried again. To run an installation it self I need to reboot laptop few times and change USB socket (don't now why) until after choosing option install/run live cd instead of black screen I can see an Ubuntu loading screen. 
Then if I'm lucky it won't freeze. It happens randomly sometimes I was able to start installation sometimes it got freeze during connecting with WiFi. 
But once I have finally finished an installation  the situation stay basically same. 
Once I could even log in to system but it got freeze few seconds after. 
In the meantime I was keep reading more topics for example these two:
```
 http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi
``` 
```
 http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook
```

So this time I have try:
-turn on Secure Boot so both systems were at same boot mode
-I didn't use any programs to make an bootable USB, I was just coping files on USB stick
-NOMODESET I was adding this option before installation and then to run system, but only first one worked, to be more specific, before installation: showed for few seconds some logs and installation have started. To run system: also showed logs and it was keep booting them but even after few minutes nothing else was happening, after reboot or same situation or kernel panic. One question here because I couldn't find straight answer, should I add nomodeset before Quick Splash or replace it?
-radeon.modeset=0, didn't work. 
-Boot Repair, freeze on loading screen 
-I have formatted Linux partition but this time using W10 tools
-cleaning EFI entries this step I missed. Im not sure if I could do it correctly 
-options I didn't try: acpi=off, nolapic and installing drivers because I couldn't find one

---

### Post by oldfred on 2016-11-01
Do not know AMD graphics and you probably need at least one other boot parameter like acpi=off or one or more others.

I like to replace quiet splash just to see the boot process. But with new systems it goes by pretty fast.
With quiet splash that is all hidden with a blank screen until the splash screen loads, then you get log in. 

If you change to UEFI with Secure boot you have to be sure to install Ubuntu by booting installer in Secure boot mode. Many systems do not allow any other boot, with secure boot on. You often have to change UEFI settings to specifically allow USB boot with Secure boot on.
And with Secure Boot on, you cannot use grub menu to dual boot, you have to use UEFI boot menu.
Boot-Mode is UEFI or BIOS, you just need to be sure to use UEFI to boot installer or repair disks whether Secure boot on or off.

When you say you are just copying files, are you using this procedure to create a UEFI only bootable flash drive?
 UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by 11mobi11 on 2016-11-01
I was using this method:
```
 http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media
``` 

Paragraph 1.3 Windows way. 

So it's better to have Secure boot off anyway? 

One more question about all the boot parameters. That is the reason why I have to reboot and change usb port few times until I'll be able to start live cd or installation? And also when I try run the boot repair disc it goes freeze? I was thinking boot repair disc have this options.

---

### Post by oldfred on 2016-11-01
Do you have newest UEFI from HP for your model. Vendors also are making many changes to UEFI to improve it.
You may need to change some settings in UEFI. 

 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try different USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
HP Touchsmart 15
[http://ubuntuforums.org/showthread.php?t=2213041](http://ubuntuforums.org/showthread.php?t=2213041) 
      
 Some HP will not boot a flash drive that is gpt partitioned.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)

---

### Post by 11mobi11 on 2016-11-01
Someone had very similar problem on my laptop 
```
 https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1615361
``` 
According to this topic using different  boot parameters will not change much and it looks like problem has not been solved.

I have found another one
```
 http://www.linlap.com/hp_envy_15
``` 
This person wrote some solutions but not everything is clear for me yet. Is anything there make sense?

I found lots similar topics and apparently I'm not the only one who had problem with this laptop and linux. And seems like most of this problem has been never solved.

---

### Post by oldfred on 2016-11-01
Did you install newest UEFI from HP?

This user seems to have a similar model, but issues with Internet.
HP-15 ac143 laptop
[https://ubuntuforums.org/showthread.php?t=2341753](https://ubuntuforums.org/showthread.php?t=2341753)

---

### Post by 11mobi11 on 2016-11-02
I have found update for bios on hp website and I already install it. I also turn off the secure boot and I installed Ubuntu once again but still nothing.

---

### Post by oldfred on 2016-11-02
HP is not dual boot friendly. Most have to do a work around.

 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file) 

Most dual booting have to copy shim to /EFI/Boot/bootx64.efi as alternate way to boot. Then manual copy of files is not required. Then use hard drive boot entry not Ubuntu entry.
Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI. 
     'Use the standard EFI file' in advanced options.

       Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Rename bootx64.efi
[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair
[/URL]
 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]
[/URL]

---

### Post by 11mobi11 on 2016-11-02
But in this topics people had mostly problem with booting Ubuntu in my case Grub is always showing and working problem begins after that when system is starting. 
I will of course try this way with coping files.

---

### Post by oldfred on 2016-11-02
I then am not sure what problems you have?
Title of thread is with install, if totally different issues better to close this thread and open new one with details on new issues.

If boot related include this info:
 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by 11mobi11 on 2016-11-02
Title say It because it was but after time it evolved to what you can read in all this posts. 
Maybe I should make new topic I different subforum I can't find an answer here anyway. 
Thanks for help anyway.

---

