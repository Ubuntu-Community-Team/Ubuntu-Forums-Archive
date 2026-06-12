---
title: "No Grub after install (13.04), Need dual boot, Linux on 1 SSD, Win7 on 1 HDD"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by justinbyrne001 on 2013-08-22
Okay, I have been determined as hell to get Ubuntu back on my machine, after not having it since **10.04 LTS**, and a lot has happened since then. My rig is not what it was, and I am sure that my current system hardware and configuration plays a role upon why I am experiencing these problems. I have been desperately attempting to acquire the answers to my following questions (below), through various other forums, to no avail. In either case, I am getting close to simply giving up on this matter, and I am hoping that somebody is able to assist me with the following issues:
 
I really hate blasting my system specs online, however, if it may assist anyone in giving a comprehensive solution, then what must be, must be. The base of my system operates on an **ASUS Sabertooth 990fx R2.0** Motherboard, supporting an **AMD FX 8120**, and my MB has a **UEFI** bios. I am fully aware of all of the issues that currently exist between Linux and the Unified Extensible Firmware Interface, which is why I chose **Ubuntu** as my distro, because it appears to have fairly decent support, and a better rate of success than other distros. In either case, I have been able to install **Ubuntu Raring Ringtail** three different times, with **Fast Boot** ‘*disabled’*, and **UEFI Secure Boot** ‘enabled’, on a brand new Corsair SSD.
 
Now, here is my first issue. I already have an **HDD** with **Windows 7** *installed*, which has my developer’s environment completely setup, the way I like it. I design and develop various programs and web-applications, while I am also attending college, therefore, I cannot afford much downtime while I am attempting to sort whatever issues arise while I am working towards getting Ubuntu under control, and eventually tailored. Consequently, I need to be able to have Grub installed, so I can boot into Windows 7 (which is on a separate drive), and Ubuntu, in my spare time to configure, adjust, and tailor it, and, Grub is not there. For whatever reason, I have been unable to install Grub, and add my Windows 7 partition (which is on a separate HDD), into the Grub menu. The only way that I have been able to swap between the two OS’s is by changing their boot sequence in my bios, which, as I am sure you can imagine, is a real pain to deal with each time. Therefore, that is my initial problem to which I need assistance with.
 
· How do I Install Ubuntu 13.04, Grub, and edit Grub to place a pointer, or reference to my Windows 7 partition, which is located on a separate drive?
 
Now, my second issue is a little more difficult. I currently run a triple-head display. I have 2 x ASUS NVidia GeForce GTX 660 DCII OC’s installed within my system, which are connected via SLI, and running at PCI-E 2.0x16, and I am unable to get all three of my monitors operating, as three separate active monitors. Now, I have had mixed results with my attempts to attempt to get this working, hence, why I have installed Ubuntu 3 times already. After I have installed Raring Ringtail, I initially tried updating my system via:
 
sudo apt-get update
sudo apt-get dist-upgrade
 
Rebooted, and once I had NVIDIA X Server Settings to play around with, and other times I did not. Therefore, I also tried the above system update, while including:
 
sudo apt-get install build-essential
sudo apt-get install linux-kernal-headers
 
To which seemed to allow me to choose the latest proprietary NVidia drivers, however, through NVidia X server, it identifies that I have 3 monitors, however, my third is disabled, and does not display anything. Even ‘out-of-the-box’ Ubuntu supports 2 monitors, albeit, they are mirrored, after I install the correct NVidia drivers, the drivers can detect 3 monitors, but one must be disabled? Each attempt I make to enable it fails, and I cannot seem to find an appropriate or proper solution for this anywhere online. Although Ubuntu has been commented by various gamers, including Steam as being the choice OS for gaming, it amazes me that SLI seems to be a difficult thing to get working, when the Scalable Link Interface has been around since 1998. I have seen many YouTube videos with people running Ubuntu, with 3 (or more) monitors, both in standard, active mode, and Surround mode, so there has to be a way. Therefore, my second question is:
 
· What is an appropriate way to ensure a solid install of NVidia drivers, in Ubuntu, and have all three monitors recognized, and active.
 
I would also like to note that all three monitors are identical, come from the same manufacturer, made at the same time, and have identical vertical and horizontal sync polarities, therefore, this ‘should’ be an ideal situation for configuring SLI, under any operating system that supports NVidia, and more than two monitors.
 
I am dumbfounded, and I am sure that my own ignorance, or lack of knowledge of Linux is not helping the situation at hand, however, I am a fairly reasonable person, and have been making various attempts (other than what I have mentioned), in an effort to resolve both of these issues. Any advice, opinions, ideas, comments, or suggestions regarding these two matters would surely be appreciated. As I have mentioned, I am sort of at my wits end, however, I admire Linux for its environment, command line interface, VIM, and the ways in which you can customize a Linux distro, not only from a personal perspective, but also from a developer’s perspective. I just want to get this stuff to gel, and I would be extremely thankful toward anyone who can assist with this matter. Many thanks in advance.

---

### Post by oldfred on 2013-08-22
What mode is Windows installed in UEFI or BIOS. If you want to easily dual boot from grub menu both Ubuntu & Windows have to be in the same boot mode. If both are not same mode you would have to go into UEFI and turn on UEFI to boot Ubuntu and to boot Windows go into UEFI and change to CSM/BIOS/Legacy boot mode. Not easy.

Boot-Repair can convert an UEFI install of Ubuntu back to BIOS. But if you installed Ubuntu in BIOS mode and Windows is UEFI, you may have to reformat as drives have to be partitioned as gpt to work with UEFI. Ubuntu can boot from gpt partitioned drives with either UEFI or BIOS, but with UEFI needs an efi partition or with BIOS needs a bios_grub partition. Often best to have both and then system will correctly install a working version, and you can convert later.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Do not know about multiple monitors.

 ARandR Screen Layout Editor 0.1.4 - Dual screens
[http://christian.amsuess.com/tools/arandr/](http://christian.amsuess.com/tools/arandr/)
Dual nVidia cards - 2013
[http://ubuntuforums.org/showthread.php?t=2129190](http://ubuntuforums.org/showthread.php?t=2129190)

---

### Post by justinbyrne001 on 2013-08-22
I appreciate the quick reply oldfred, and here is what I have done so far, and maybe you can tell me where I am going wrong. I believe that maybe, somehow, I accidentally installed Ubuntu under legacy, because I have my BIOS setup under **[Boot Device Control]** as *UEFI & Legacy OpROM*, and **[Boot from Storage Devices]** as *Both, UEFI first, *instead of *UEFI only*, and when I select *UEFI only*, my BIOS does not even detect my Linux partition, let alone the drive to which it is installed upon. I ran 'Boot Repair', and this is what I received:

**Prompt:**
&#8220;EFI detected. Please check the options.&#8221;

Then 'Boot Repair' loaded, and when I chose [Recommended Repair], I received a prompt stating:
"The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode. Do you want to continue?&#8221;
 
I have no idea why I am receiving this prompt, seeing as though &#8216;Boot Repair&#8217; just stated:
&#8220;EFI detected. Please check the options.&#8221;

Then I restarted my computer, changed BIOS settings. **[Boot Device Control] **=> *UEFI & Legacy **OpROM*, and **[Boot from Storage Devices]** => *Both, UEFI first*, then restarted again. Received the same prompt via &#8216;*Boot Repair&#8217;*. Restarted computer again, changed BIOS settings **[Boot Device Control] **=> *UEFI only*, and then restarted. BIOS did not even detect that there was a Linux partition, or that my SSD existed. Changed BIOS settings **[Boot Device Control] **=> *UEFI & Legacy OpROM,* again, booted into Ubuntu, and now Grub was present, but no option for Windows 7!?

While within &#8216;Boot Repair&#8217;, I reviewed the &#8216;[FONT=courier new]Advanced Options[/FONT],&#8217; and I am wondering whether I should have used those, seeing as though the following options could apply to my system configuration.
 
**[Advanced Options]**
   **[Main Options]** tab
      **[Restore MBR]** &#8211; Should I check this? Would it matter? Will it screw up Windows?
      **[Backup and rename Windows EFI files (solves the [hard-coded-EFI] error)]** &#8211; Again, should I check this? Would it matter? Seems like it could mess up Windows.
   **[GRUB Options] **tab
      **[Secure Boot]** &#8211; Since by BIOS is set to Secure Boot, should I check this?
 
Ultimately, I seem to have GRUB now, however, no Windows 7 entry. In addition, I have been &#8216;attempting&#8217; to get my NVIDIA drivers working within Ubuntu, with really screwed up results. First, I installed NVIDIA&#8217;s drivers via Ubuntu&#8217;s Software Center [NVIDIA Driver Version: 313.30], and I could only get two screens, with the &#8216;TwinView&#8217; configuration. I then selected my third monitor (which was disabled), but, detected, and enabled it, and set all three to &#8216;Separate X Screen&#8217;, where now I only have my &#8216;primary&#8217; monitors displaying Ubuntu, and my other two (left & right) displaying nothing but &#8216;white&#8217;!? Once, I even rebooted, and all three screens lit up with a nice NVIDIA graphic logo, but froze, and I had to hard-reset. I have been able to log back into Ubuntu, however, I am not receiving a display on all three monitors. I had to create an xorg.conf file, to save my settings under /etc/X11/

Here is my xorg.conf file, for review:
 ```

[FONT=courier new]# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 313.30  (buildd@lamiak)  Wed Apr 10 17:19:51 UTC 2013
 
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection
 
Section "Files"
EndSection
 
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
 
Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection
 
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer G206HL"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection
 
Section "Monitor"
    # HorizSync source: unknown, VertRefresh source: unknown
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer G206HL"
    HorizSync       0.0 - 0.0
    VertRefresh     0.0
    Option         "DPMS"
EndSection
 
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660"
    BusID          "PCI:1:0:0"
EndSection
 
Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660"
    BusID          "PCI:6:0:0"
EndSection
 
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-3: nvidia-auto-select +1600+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
 
Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
 [/FONT]
```
I have no idea what to do from here. I still cannot boot into Windows 7 from GRUB, and I must boot from my BIOS. In addition, my NVIDIA situation seems more screwed up than even. I do &#8216;honestly&#8217; appreciate your assistance concerning this matter, and any further assistance will absolutely be meet with much gratitude. I sincerely appreciate your time, and any input, advice, comments, or suggestions that you may have concerning this matter. Thanks again.

CSM
[http://www.flickr.com/photos/100708654@N06/9572089155/](http://www.flickr.com/photos/100708654@N06/9572089155/)

BOOT OPTIONS
[http://www.flickr.com/photos/100708654@N06/9572144297/](http://www.flickr.com/photos/100708654@N06/9572144297/)

BOOT DEVICE CONTROL
[http://www.flickr.com/photos/100708654@N06/9574938532/](http://www.flickr.com/photos/100708654@N06/9574938532/)

BOOT FROM STORAGE DEVICES
[http://www.flickr.com/photos/100708654@N06/9574937864/](http://www.flickr.com/photos/100708654@N06/9574937864/)

BOOT OPTION PRIORITIES
[http://www.flickr.com/photos/100708654@N06/9572142895/](http://www.flickr.com/photos/100708654@N06/9572142895/)

BOOT MENU
[http://www.flickr.com/photos/100708654@N06/9572143013/](http://www.flickr.com/photos/100708654@N06/9572143013/)

NVIDIA X POST DRIVER INSTALL
[http://www.flickr.com/photos/100708654@N06/9572141427/]("http://www.flickr.com/photos/100708654@N06/9572141427/in/photostream/")

POST NVIDIA DRIVER INSTALL[URL="http://www.flickr.com/photos/100708654@N06/9572140907/"]
http://www.flickr.com/photos/100708654@N06/9572140907/[/URL]

DEFAULT NVIDIA SETTINGS - POST INSTALL
[http://www.flickr.com/photos/100708654@N06/9574936364/](http://www.flickr.com/photos/100708654@N06/9574936364/)

NVIDIA LOGO 3 SCREENS
[http://www.flickr.com/photos/100708654@N06/9574936062/](http://www.flickr.com/photos/100708654@N06/9574936062/)

UBUNTU - CURRENT BOOT POST NVIDIA INSTALL, WITH EACH MONITOR SET TO SEPARATE X SCREEN
[http://www.flickr.com/photos/100708654@N06/9572141571/](http://www.flickr.com/photos/100708654@N06/9572141571/)

---

### Post by oldfred on 2013-08-22
I am not on flicker, so I cannot see your posts.

You can attach screen shots with the paper clip icon in the advanced editor. And long posts of output from terminal need to be in code tags to preserve formatting. You can auto add code tags with the # icon in the editor.

Best to post the link from Boot-Repair so we can see details of your Ubuntu & Windows installs. Boot-Repair will not help on Video issues. I have not edited a xorg file for 5 years, but I only have one monitor.

Probably better to post a separate thread on the video issue with 3 nVidia monitors in the title. 
Those that know nVidia better and may have more than one monitor may be then able to directly help. They may never look at a boot issue titled thread.

---

### Post by justinbyrne001 on 2013-08-23
I apologize about the code, and I will run another thread about the video, however, it appears as though I will have to re-install Ubuntu once again from scratch, either tomorrow, or sometime during the weekend, because GRUB2 is no longer there. In an attempt to get everything working with my graphics, and my system up-to-date I ran

```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```

To which GRUB eventually asked me where I wanted the new version of GRUB2 to be installed, therefore I chose my Linux distro, and after a restart, all I get is a command line, awesome. Everything appeared to work fine, however, I guess updating my Linux distro wasn't the best idea, man.

In either case, I have some screenshots of my BIOS for you to look over if you have the time. This is how I currently have everything configured, and if I should have it configured in another manner, please let me know. I will attach them to this post as you said, and I hope that they help you. In either case, I do appreciate both your time and assistance, and I will be checking this forum over the weekend, even though I have a sight that I have to validate, and some JavaScript that I have to debug, along with some other junk that I absolutely 'have' to finish, and it looks like I will be doing it in windows. Thanks again for your time, and I look forward to hearing from you.

[ATTACH=CONFIG]245624[/ATTACH][ATTACH=CONFIG]245625[/ATTACH][ATTACH=CONFIG]245626[/ATTACH][ATTACH=CONFIG]245627[/ATTACH][ATTACH=CONFIG]245628[/ATTACH]

---

### Post by oldfred on 2013-08-23
Nice screen shots, I may steal those to post when others with Asus have questions.

Ubuntu will install and work with secure boot. And Windows should boot with UEFI and secure boot off, but Windows will not boot in CSM mode. Do you want secure boot? It currently is 90% marketing by Microsoft and 10% security. 
 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI secure boot thing is more about control than security


Either way I would turn off CSM/BIOS/Legacy boot as an option. You should have both UEFI and UEFI with secure boot. I might check that Windows boots with secure boot off, it should but a few do not. 
When secure boot is on, it will only show boot options for systems with secure boot. And nothing else will boot.

       One user posted this which you probably need to do for those systems that only boot Windows with secure boot on or if you really want secure boot Ubuntu:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.

    
Boot-Repair can fix your install if it otherwise is ok. If you boot it in UEFI mode or UEFI with secure boot on. It uninstalls grub-pc (BIOS) and installs grub-efi(UEFI). If in secure boot mode it also installs the Microsoft signed versions of grub and kernels.

If in BIOS mode you always install the grub2 boot loader to the MBR even with gpt partitioning. But with gpt you need a bios_grub 1MB unformatted partition to get grub to install correctly in BIOS mode.

---

### Post by justinbyrne001 on 2013-08-23
In all honesty, the whole reason upon why I am migrating back to Ubuntu is for development, customizability, and security reasons, albeit, I am not a huge fan of the whole Unity feature, however, I am ‘absolutely’ aiming at having a solid, and secure OS. This is unquestionably one of my largest concerns, seeing as though I run a small business, and I do not want, nor can I afford any leaks. Right now, I believe that my whole problem has been that I have not been installing Ubuntu in UEFI, because, as you can see, my current BIOS, **Boot Device Control**, is setup as **[UEFI and Legacy OpRom]**. The reasons as to why I feel this way, is because when I set this to **[UEFI only]**, or I set **Boot from Storage Devices** as **[UEFI only]**, my BIOS ‘does not’ see my Linux partition, let alone the drive to which it is installed upon. I apologize if this may seem ignorant, however, I am just becoming familiar with the Unified Extensible Firmware Interface, including its standards, and I currently know nothing about partitioning in GPT. Currently, my Windows 7 OS is installed on a New Technology File System (NTFS) partition, and I am hoping that both Operating Systems do not have to be partitioned with GPT, in order for GRUB2 to recognize them.
 
As I have mentioned, you have been a great help, and I do appreciate both your time, and your assistance. Today, I unfortunately ‘absolutely have to’ get some work done, therefore, I cannot tinker with this today, however, I will be back at it either tomorrow, or Sunday. In either case, I hope that you will still be available, and possibly able to assist me with this solution. Before I attempted to install Linux, I ensured that I had the latest BIOS firmware installed on my MB, because I understand the UEFI is still considered a relatively new technology. In addition, go ahead and use the images that I posted, if they assist you with anything related towards this matter, or any other matter concerning the UEFI BIOS. Thanks again, and I should be back in here, and posting soon. In the meantime, I was hoping that I could get your opinion upon what should be the ‘best practice’, *for me*, to install Ubuntu Raring Ringtail, giving my circumstance, with security in mind, and naturally dual-boot in mind as well. Thanks again for both your time and effort, for I truly do appreciate it. Thanks.

---

### Post by oldfred on 2013-08-23
Because you have the secure boot setting on, only secure boot systems will show. But it still should show the Ubuntu installer on the flash drive. But would not show the Ubuntu install as it is not secure boot version with the signed kernel.

But a few UEFI systems have hard coded the UEFI boot loader to only boot Windows when secure boot is on. That is a violation of UEFI standard but the only work around has been to install in BIOS mode and use Boot-Repair to convert to UEFI or convert to UEFI with secure boot.

 Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

### Post by justinbyrne001 on 2013-08-23
Okay, let me see if I understand this correctly. I can install Linux under **LegacyOpROM**, or have my **Boot device control **set as **[UEFI and Legacy OpROM]**, and if Ubuntu installs in ‘*Legacy mode*’, or ‘*non-UEFI*’, then I should still be able to correct this via ‘Boot Repair’. Although, this all sounds great, Boot Repair, in itself, appears more sophisticated since the last time I used it, back in Lucid Lynx, or 10.04. Therefore, I am wondering whether I should choose **[Recommended Repair]**, or **[Advanced Repair]**, due to the fact that **[Advanced Repair]** seems to have a few input boxes (or check boxes), like **[Backup and rename Windows EFI files (solves the [hard-coded-EFI) error)]**, and **[Secure Boot]**, under the **[Main Options]** and **[GRUB Options]** tab respectively.
 
First, I do not know whether or not if I chose to enable these options, while performing a boot repair, will correct the issue(s) to which I am facing, and/or end up screwing up my Windows 7 partition, which I absolutely cannot afford to lose, at the moment, because of the work that I must continue to do. However, if I can check these options, and not corrupt my Windows 7 MBR somehow, then do you think that it would be worth a try? As I have mentioned, I am unfortunately busy today, and possibly tomorrow, however, I will be checking this forum, and when I do have a free moment, I would like to investigate this myself, to see exactly how these options would influence the boot repair process. The last thing I want to do, or ‘ever’ do, is take pot-shots in the dark, because, chances are, if I have not investigated what I am doing, to a fair degree of comfort, then I will more than likely run the risk of screwing the pooch, so to say, hence, why I am discussing this matter here.
 
Moreover, you mentioned that Secure Boot is approximately 10% security, and 90% Microsoft marketing. Since I am attempting to obtain a ‘secure’ environment in Linux, and when I mean secure, I really mean ‘secure’. Therefore, what would I be sacrificing if I were to disable Secure Boot, since I am seeking an environment with as few holes, or exploits as possible? If it is not really going to make a difference either way, then I will simply disable it, and naturally use a series of monitoring programs, combined with penetration testing, and system hardening to secure my environment, once it is bootable, and viewable. Finally, how do you feel about LVM? I understand that it encrypts the entire partition, and/or home folder, which is a feature that is appealing to me, and since this distro is going on an SSD, I do not see how I am going to experience any type of noticeable lag if the partition is encrypted. However, could this ‘prevent’ me from accomplishing certain tasks, such as running ‘Boot Repair’, and or making any other kinds of adjustments? Personally, this has been the first time that I have noticed LVM as an option within the installation method, and I am simply wondering whether it can be helpful, or if it can be more trouble than it is worth. I am not looking to share files between hard drives, unless a flash drive is involved, and I want to be able to ‘keep’ everything isolated within Linux, and Windows 7 completely separate. I do not even want these two OSs on the same drive.
 
Lastly, I am using a DVD to install Linux, because 1) I feel safer that way, because they are not re-writable, and 2) my ASUS DVD drive is UEFI compatible, and has no problems, or conflicts with my BIOS. I do not know if this changes anything, however, I do appreciate your consistent feedback, knowledge, and insight concerning this matter. You have been a big help, and a really good resource so far, and I want you to know that I appreciate it. Thanks once again.
 
**P.S.:** Let me know if you can whether the **[Advanced Options]** tab in ‘Boot Repair’ could assist me within my situation, or whether I should simply stick to the **[Recommended Repair]** option. Many thanks.

---

### Post by oldfred on 2013-08-23
I have not actually used Boot-Repair to fix my system or with UEFI. Most times I suggest the defaults but that can vary now as with UEFI you may be in secure boot mode, UEFI only mode, or a BIOS/CSM mode that may also boot in UEFI. It can get confusing even if you know it will do that. 
Boot repair actually chroots into your install and uninstalls grub-pc and installs grub-efi. That install changes a full settings like fstab to make it work in UEFI mode. But that will not work with secure boot unless you have the Microsoft signed shim & kernels. I think you can only install those if you have booted in secure boot mode.

I used to use CDs, but then found flash to be faster and reuseable. I used to also burn several LInux repair CDs, like Knoppix, gparted, Parted Magic as well as the installer. Stacks of CDs when doing that every 6 months. But then I found I can directly boot ISO with grub and put all the ISOs on one Flash drive. But now I put ISO on a partition on my old drive and install to my SSD or newer hard drive from hard drive to hard drive. That is a lot quicker.

Only if your system will only boot Windows may you need the rename. What that does is make the shim file with the Microsoft key (so it works) have the name of the Microsoft efi file. Then the UEFI thinks it is booting Windows but really boots grub. And from grub you then can boot the real Microsoft file which is bkp or backed up. Some UEFI have been modified or hard coded which is totally against the UEFI standard.
Examples but there have been a few others. Some vendors have fixed issue after complaints so newer UEFI can resolve some issues also.
 Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

I do not use encryption nor LVM. The slowdown is minor as I understand maybe as much as 5%. But for a home system I do not think it is required.

---

### Post by justinbyrne001 on 2013-09-03
Okay, here is what I did to ‘finally’ get this to work. Linux is installed, GRUB is installed, Windows 7 is a selection in GRUB, and Windows 7 (on a separate drive), boots, and works just fine, and even though there are still a few caveats with my current configuration, it is still a move in the right direction. What I did was, kept **[secure boot]** “on,” because, it ‘appears’ that if I turn “off” **[secure boot]**, my BIOS will default to **[Legacy OpROM]**, and does not boot in **[UEFI]**. If anybody can find any information to the contrary on this, I would be more than happy to see it. In either case, Linux is installed, in **UEFI** mode, and boots just fine, except, for my graphics card issues, which is/are another issue.
 
Now, the way I got this to work was first, I went into my BIOS, and kept **[Launch CSM]** **[enabled]**, changed **[Boot Device Control]** to **[UEFI Only]**, and changed **[Boot from Storage Devices] **to **[UEFI driver first]**, booted live Linux via DVD, deleted all previous partitions on my new SSD, and installed Linux. Once this was complete, I updated everything within Linux, and after a pop-up (via the GUI and Linux system) prompted as to whether I wanted to update my Linux distro, because it had located some packages which were more current than the software packages that I currently had, I went ahead and executed that. Once I rebooted my system, I had, and still do have, GRUB, in all its glory. It has my current Linux distro in there (as it should), a couple alternative methods to boot into my distro (if something needs to be either tested or troubleshot), and two options to boot Windows 7. One of the options to boot Windows 7 is in standard **[Legacy OpROM]** mode, and the other is in **[EFI]** mode, which I thought was strange, however, they both boot, and when I am in either environment, there are some problems.
 
When I boot Windows 7 in **[Legacy OpROM]** mode, everything on my secondary hard drive works fine, USB sticks formatted in FAT32 work fine, and I did not suspect that they wouldn’t, however, each of my external hard drives do not work, and Windows states that they need to be ‘reformatted’ before they can be put into use. This is clearly an Operating System Issue, a BIOS issue, or a combination of the two. Because all of my external drives are viewable under Linux, readable, writable, etc… and not viewable under Windows 7, therefore, the data is not corrupt, and I checked each drive via fdisk. On the other hand, when I boot Windows 7 in **[UEFI]** mode (which is the mode that I should be using), **2** out of the **3** external hard drives that I have, are viewable, readable, writable, etc… however, there is still **1** drive, to which I am unable to connect to, and I receive the following prompt: “*You need to format the disk in drive X: before you can use it*.” I do not know how to correct this issue, in Windows 7, and I would like to figure it out. Although, everything that I have found online to correct this issue, suggests that I install some backwoods shady third-party software (with bloat ware) to clean this up ‘somehow,’ I have been reluctant to jump on these ‘supposed’ solutions, for fear that it is simply malware, spoofing itself as a useful utility. If I can, I like to ‘manually’ adjust things, instead of relying on functions, procedures, or methods that I did not write, and/or do not understand, therefore, I would probably feel more comfortable if there was a more ‘direct’ approach at dealing with this problem.
 
All and all, I am very appreciative of **oldfred**, who has stuck by me this whole time. I hope that we speak again in the future, and seeing as though I am fairly determined at getting Linux installed again, and migrating towards that direction, or that type of environment, in a fiercer way than before, we just might do that. I have always enjoyed Linux, however, it does come with some caveats sometimes, but, once you get everything running, and purring just nicely, it is, in my opinion, the most stable, flexible, and secure Operating System, platform, or environment that I have ever used. Thanks again, oldfred.

---

### Post by oldfred on 2013-09-03
You are welcome.

I only had XP on a MBR drive, which did not read with my gpt partitioned drives. But it was my understanding that newer versions of Windows could boot with a MBR(msdos) drive but then read other drives that that were gpt if NTFS or other Windows formatted partitions. Not sure what else the issue may be.

---

