---
title: "Formatted Thinkpad Edge E425 Laptop. cannot install Ubuntu thru either cd/dvd or USB"
date: 2016-06-28
forum: Installation &amp; Upgrades
---

### Post by KageRyu on 2016-06-28
HI Guys I'm semi noob to Linux so keep it down on the jargon ok?

SPECS: 
**Edge E425 (ThinkPad)**
[IMG]http://support.lenovo.com/%7E/media//Images/ProdImageLaptops/thinkpad_edge_e425[/IMG]
Serial Number
R9LXFBA
Machine type model
1198A19

Machine info
E2-3000M(1.8Ghz),  2GB RAM(4gb ram i added myself) so 6gb, 320GB 5400rpm HD, 14in 1366x768 LCD, AMD Radeon HD 6470M,  CDRW/DVDRW, 802.11bgn wireless, 1Gb Ethernet, UltraNav, Camera, 6c  Li-Ion

Operating System
NONE CURRENTLY(but came with
Windows 7 (64-bit))

this laptop I just formatted and decided to install Ubuntu.

So my problem is i've made a usb bootloader with (Universal-USB-Installer-1.9.6.5 also tried both usbs with UNETBOOTIN 625) and (ubuntu-16.04-desktop-amd64.iso) when i boot it up i see the ubuntu menu with //// try ubuntu without install//// Installl Ubuntu /// etc    either of those options along with check for errors option causes it to freeze right after the five dots change color at the purple ubuntu loading screen. afterwards i tried another usb same problem.  i tried these usbs on two different computers they boot up without any problems.  So I thought maybe my laptops USB drivers are bugged(they worked fine before my format). So I made a DVD with the ubuntu ISO( ubuntu-16.04-desktop-amd64.iso) and when i set boot order and load it my laptop doesnt even acknowledge the cd. when i try any other computer they recognize the cd and boot up with it. and Yes ive tried changing boot order from bios and yes i opened boot menu and selected the boot from dvd drive option and I also check if secure boot was enabled (didnt see such an option in Bios.

So i'm at an impasse tried to fix this for 5 hours last night. Hope you guys can help me figure out this problem .


o7

PS. if your going to say perhaps the ISO is corrupted tried with multiple downloads of the latest ubuntu-16.04-desktop-amd64.iso)

---

### Post by oldfred on 2016-06-28
Sounds like graphics issue, but I do not know Radeon.

Have you tried nomodeset?

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by KageRyu on 2016-06-28
Thank you very much after a long time figuring out how to get to the grub menu, finally booted up ubuntu in try mode.
but my resolution is so bad that i cant really see my options in the installer,
 I dont just want to blindy press enter while installing what is the fix for that?

---

### Post by oldfred on 2016-06-28
Do not know if this helps or not:

 16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware). 
With 15.10 Release notes
AMD's fglrx driver does not work with the current kernel
The fglrx driver is now deprecated in 16.04, use radeon and amdgpu 
   AMD driver discussion with 16.04
[http://ubuntuforums.org/showthread.php?t=2321963](http://ubuntuforums.org/showthread.php?t=2321963)
[http://ubuntuforums.org/showthread.php?t=2327075](http://ubuntuforums.org/showthread.php?t=2327075) 
   How Ubuntu 16.04 Is Performing With AMDGPU/Radeon Graphics Compared To Ubuntu 14.04 With FGLRX
[http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1)

---

### Post by mc4man on 2016-06-29
Assuming this laptop is 4-5 yrs. old maybe try a live usb of 14.04.1

 [http://old-releases.ubuntu.com/releases/14.04.1/](http://old-releases.ubuntu.com/releases/14.04.1/)
You'll need to scroll down to find -
 ubuntu-14.04.1-desktop-amd64.iso

Otherwise maybe search for kernel options pertaining to AMD Radeon (your gpu)

---

### Post by Bucky Ball on 2016-06-29
> **mc4man said:**
> Assuming this laptop is 4-5 yrs. old maybe try a live usb of 14.04.1


... or Xubuntu 16.04 LTS or Xubuntu-core 16.04. Both a lot more lightweight than Ubuntu and maybe better suited for that rig. Might not fix your problem but even if you do manage to get a full blown Ubuntu 16.04 on that machine, might not be the greatest computing experience.

Also, Xubuntu does not have a graphic installer, it runs a text one, so that will leapfrog (should) graphics issues if that is the seat of your issues. You can always install ubuntu-desktop later once you have Xubuntu running and that would give you Ubuntu 16.04. It may also crash the system, of course, because it can't handle Ubuntu 16.04. :)

---

### Post by KageRyu on 2016-06-29
Thank you everyone for your replies.  ok i was able to get ubuntu to startup with the nomodeset option. I installed ubuntu with a encrypted hard disk . now when i start my computer i come to a password prompt  (with the ubuntu background) after entering the password ubuntu shows the previous behaviour of loading those few dots then freezing. i want to somehow acces the ubuntu desktop and install the required graphics drivers. can anyone tell me how to do these?

EDIT:// I tried re enabling nomodeset: I tried two methods at grub pressed e" then: 
1. deleted $linux_gfx_mode replaced with nomodeset = outcome black screen nothing happens.
2. [IMG]http://imgur.com/q9gqUYH[/IMG] ([http://imgur.com/q9gqUYH](http://imgur.com/q9gqUYH))  here i replace quiet splash with nomodeset  just get a purple screenthat doesnt change. 

i want to be able to boot up ubuntu like the time i used nomodeset to install it . and i wish to boot it up and install the drivers necassary to run it.

Edit 2: on OldFreds suggestions i downloaded and tried ubuntu 14 . but has the same issue of freezing at the splash screen so id stil prefer that i can get ubuntu 16 to work.

---

### Post by kurt18947 on 2016-06-29
You need to change grub so it invokes nomodeset every time. I think this is a reliable how-to:

[http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/?PageSpeed=noscript](http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/?PageSpeed=noscript)

---

### Post by KageRyu on 2016-06-29
i saw a similar solution at a few places the one thing i didnt understan is where do i edit these files? iI finally figured out how to install linux but this time i cant pass the splash screen of my instaled linux.

---

### Post by oldfred on 2016-06-29
If nomodeset worked for the install, then you should be able to use it when you boot as in post #2. Have not seen that editing the gfxmode line works, but many systems need gfxmode setting in /etc/default/grub. But I have seen that more for Intel video.

If you used the Full drive encrypted install that is a more advanced install.  For any other issues you have to use LVM tools not standard Linux tools. Not recommended for beginners unless you absolutely must have full drive encryption.

If you get to a terminal then you can edit grub to make nomodeset a permanent setting.
As per kurt18947 link.

       sudo nano /etc/default/grub 
add nomodeset after quiet splash on GRUB_CMDLINE_LINUX_DEFAULT
Then

 sudo update-grub 

If at grub command line with c instead of e (not Ubuntu's terminal) you can see video modes:

 From a grub command line to see available settings pressing <c> & escape to get back to menu
vbeinfo 

The two lines for extra boot parameters:

 # GRUB_CMDLINE_LINUX
If it exists, this line imports any entries to the end of the 'linux' command line (Grub Legacy's "kernel" line) for both normal and recovery modes. This is similar to the "altoptions" line in menu.lst
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
This line imports any entries to the end of the 'linux' line (Grub Legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. For a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". This line is where other instructions, such as "acpi=off" are placed.

---

### Post by KageRyu on 2016-06-29
summary : [http://paste.ubuntu.com/18100896/](http://paste.ubuntu.com/18100896/)
so how exactly do i get nomodeset to work? is this correct?  [http://imgur.com/iG3rDXq](http://imgur.com/iG3rDXq) 

after  adding nomodeset this happens and it gets stuck  [http://imgur.com/m617be1](http://imgur.com/m617be1)   

whats the next step i can try ?

---

### Post by oldfred on 2016-06-29
I think the nomodeset can be before or after quiet splash.

Have you tried replacing quiet splash. You then get to see all the boot process scroll by quickly. But you may see where it stops. Often last line is not issue, but several lines above it may say error on loading something.

Can you use second line in grub menu or recovery mode? It think that already includes nomodeset and gives you several choices. Try several. Best if you can at least get on-line & to terminal to then run terminal commands.

Which version of Ubuntu have you got this far with?
16.04 or 14.04? 
And then with full Ubuntu or one of the lighter weigh gui versions?

---

### Post by KageRyu on 2016-06-29
i got this far with version 16.04 and recovery mode just causes my screen to go purple and blank.
and when i start normal ubuntu and replace quiet splash with nomodeset i again have the purple blank screen problem.
help me oldfred kenobi your my only hope

---

### Post by oldfred on 2016-06-29
I am running out of ideas.
I just do not know AMD/Radeon issues that well.

Others suggested 14.04, I might try that.

---

### Post by KageRyu on 2016-06-29
alright thanks guys will update if i find a solution.

Hi i got it to run by choosing one of the alternative recovery mode  versions like you said(cant recall which version exactly but was at bottom of list). now what can i do to download the correct  drivers? 

ive started a new thread  here if anyone has any ideas please post them there thank you !   
[http://ubuntuforums.org/showthread.php?t=2329295&p=13511288#post13511288](http://ubuntuforums.org/showthread.php?t=2329295&p=13511288#post13511288)

---

### Post by oldfred on 2016-06-29
I think you have the only response in your new thread already. 
Similar to links in post #4 in this thread.

---

