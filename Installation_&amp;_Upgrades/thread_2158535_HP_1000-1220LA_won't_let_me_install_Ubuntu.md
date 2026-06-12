---
title: "HP 1000-1220LA won't let me install Ubuntu"
date: 2013-06-29
forum: Installation &amp; Upgrades
---

### Post by Itsuki Minami on 2013-06-29
Hi and greetings from Ecuador,

First of all I do checked if this was already posted, I saw people with similar problems like mine but nothing of the things that were posted worked, so this was the last resource i had.

My problem is that I can't install Ubuntu 13.04 in a computer with UEFI, this is what I already tried:


[LIST]
[*]Disabling Secure Boot with legacy mode off. 
[*]Enabling Secure Boot and UEFI 
[*]Enabling UEFI without secure boot 
[*]Enabling Legacy Mode without secure boot 
[*]Disabling Windows Fast Start 
[*]Trying to start the USB Stick from boot options menu, it just doesn't appear even in legacy mode 
[*]Trying to execute Efi file, and it does show Grub, but after selecting any of the options the screen goes like a very dark grey, then it turns black completely like if the screen was turned off 
[*]Modified the quiet splash option with the nomodeset option, this makes the screen black and then it start something terminal like, it somehow completely loads and then in the terminal says "Welcome to Ubuntu 13.04" but can't do anything from there, no graphical environment just terminal and don't know if I can install Ubuntu from there. 
[/LIST]
I think I have tried all my possible options but still no luck with this, maybe someone has some kind of clue that will guide me trough this? 

Thanks in advance, let's hope with the help of the community I can finally install ubuntu in my laptop

---

### Post by oldfred on 2013-06-29
Often best with secure boot off, but it should boot with secure boot on.
But you do need fast boot off.

If USB flash drive does not appear, is your download good and did you create flash drive correctly - not just copy ISO to flash drive?
What video do you have?

       Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Other HP, also see my signature for links to details on installing and fixes.

 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by Itsuki Minami on 2013-06-29
I cheked my Iso with the checksum tool, also I made my booteable pendrive with unetbbotin and also with universal usb installer both with the same result, I will read the links you posted and see if I can finally install it, anyway I will apreciate any other suggestion.
I almost forgot I disabled fast boot in Windows but can find such option in BIOS, maybe that is the problem?

---

### Post by oldfred on 2013-06-29
Some seem to only have it in Windows and others also have a setting in UEFI. Not sure of difference? 

Windows setting off can be critical as that is related to hibernation which is always on. Windows then does not always recover if booted from grub and may by-pass any keys to get into UEFI. If Windows does not boot and you cannot get into UEFI to boot a repair disk you have major issues. Some with Samsungs just had to send system back to vendor.

It seems to be more of a video issue if nomodeset got you started to boot. Is this a system with dual video? And those need Intel turned off in UEFI/BIOS and nomodeset to use the nVidia. Do not know about dual video with AMD.

 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1 
[*]nVidia: nomodeset 
[*]Generic: xforcevesa or nouveau.modeset=0 
[*]Radeon: radeon.modeset=0 
[/LIST]

It looks like you may only have Intel? You can try the above newer setting or one of these as other alternatives.
 Force Intel Video mode as boot parameter in grub menu Change to your monitor/screen size.
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

---

### Post by Itsuki Minami on 2013-06-29
Just correct me if I'm wrong but with the nosetdome parameter I should enter graphical environment right? I just get a Terminal Like Screen. I really hate this UEFI thing, I'm almost giving up on installing any linux system...Seems it's a problem with this computer.

Also to answer the above questions, I don't thinks this is a system with dual screen, but I'm not sure, the video card is a Intelhd 3000, I'm trying now what you suggested, let's hope it works and thanks...


------Update---------

Well I tried all the options provided this: i915.i915_enable_rc6=1
Opened the installer it apparently installed but it won't boot, the said option didn't started ubuntu live usb. Seems like a little step forward but I'm still stuck, the other options didn't  worked.

---

### Post by oldfred on 2013-06-29
If that entry worked to boot installer, you may need it to boot after it installs also.

---

### Post by Itsuki Minami on 2013-06-30
The problem is Grub didn't even showed, the system just went all the way to windows giving me no options, and as far as I know if I want to modify grub I need to boot the live usb not just the installer but the live environment of the usb stick. What I don't understad is why the installer did run, but if I choose Try Ubuntu without installing with the same option nothing happens. I'm seriously thinking leaving this laptop to my wife and buying a native Ubuntu Laptop. Too much problems to install what used to be easy...I know is not Ubuntu's fault it's microsoft and the hardware vendor fault, it's pretty sad that in some machines ubuntu or any other distro will just not work no matter what you do.

---

### Post by oldfred on 2013-06-30
You should always be able to boot flash drive. If you can get back in run this:

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Itsuki Minami on 2013-06-30
Ok I will give them a try and report back, and thanks for helping.

---

### Post by Itsuki Minami on 2013-07-13
Just came to say that I finally managed to install ubuntu 13.04, it worked with the i915.i915_enable_rc6=1 command at the momento of launching the installer, then repairing the video driver once the system was installed and it worked ok, I'm writing this from my ubuntu installation, thanks for all the help

---

