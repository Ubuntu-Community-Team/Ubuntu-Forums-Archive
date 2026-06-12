---
title: "Dell Inspiron 15 7000 series fails to boot"
date: 2017-06-05
forum: Installation &amp; Upgrades
---

### Post by rdragonrydr on 2017-06-05
I bought this bane of my existence about a month ago because I needed a new computer. Badly. It has wonderful specs, including an i7 6700HQ, SSHD (8GB flash cache), and **Nvidia GT960M graphics card.**

I am sure you know where this is going. :(

I now get the error "Nouveau 0000:02:00.0: pci: failed to adjust linkctl speed" followed by a number of messages stating that the CPU has locked up.
**The splash screen normally hides this message**, and normally freezes when around the same time as this message appears. My research seems to state that this is caused by the **** drivers for the GPU.

Weirdly, when I first got this, it worked perfectly well for quite some time, until I found out that it was not actually using the Nvidia Graphics during the slideshow resulting from trying to run FortressCraft Evolved.
I tried to install Bumblebee to use the card (I did not install the proprietary graphics driver at this time, as it seemed that it would still work without it) and found that I could not load bbswitch due to Secure UEFI being on.

This led me to reinstall Ubuntu with UEFI Secure mode off (it refused to boot the Secure-installed version when I turned Secure UEFI off in the BIOS. Not sure if this was due to the same problem, as I had found a forum post that said it would only boot in its original configuration). It then refused to boot after installation with the above Nouveau problem (I assume). Now it fails to boot no matter what mode the BIOS is in, or how I installed the OS. Sometimes it also fails to boot the CD to install, but only sometimes. I am stumped as to why those work at all, and the installed one does not.

Most recently, I tried installing the Nvidia closed-source drivers after I got it to boot with the nomodeset command in grub. The computer then rebooted, and actually worked. I then told the Nvidia application to use the Intel GPU for the time being, at which point it failed to boot again. (Was this coincidence and finickiness, or does it only work if you forevermore use the Nvidia one once it's installed?)

[B]My question:

[/B]How do I get this accursed computer to reliably boot **and** use the GPU? I would also like to be able to use the Intel GPU during times when I want the 10 hr battery life, and the Nvidia GPU when I am bored. I would *prefer* to use the Nouveau or open source drivers, but I can't figure out if they work or why they are currently not working. Of course, having the computer working is more important than my rabid Open Source fanaticism, but it still is a preference.

I have heard of Prime and Bumblebee, but I do not know what is required to make them work or how/when the GPU is then used. Worse, I was unable to find out which method(s) works at all or would work for my PC. Bumblebee seems to need an "Optirun" preface any command that needs the GPU, so that's probably out of the question already, as depending on how Fortresscraft is launched by Steam, it may not work at all.

Can you please give me a detailed and step-by-step instruction list to get my computer working? Thanks in advance!

---

### Post by rdragonrydr on 2017-06-05
Oh, yes. I also brought it to the IT person over at my college. He's in charge of installing and maintaining all three major OSes (Linux, Windows and Mac) and various software on the university computers, and most of the home computers that the professors break too. This one stumped him. He tried reinstalling Ubuntu in case my attempts had failed, but it didn't help either. I guess it makes sense if this is a graphics issue, since he did state that he hasn't dealt with drivers much.

To be fair, I only did find out that this might be a driver problem, not a secure boot issue, after I had left.

---

### Post by oldfred on 2017-06-05
I thought with the newer nVidia drivers, bumblebee was obsolete.

How did you install the nVidia driver? 
Best to install from repository, or if you really want or need the very newest use the ppa.
Do not install the .run file from nVidia or you will have issues.
And if you change drivers you must first purge everything, nVidia, bumblebee etc before installing a new version.

Did you install in UEFI or BIOS boot mode?

Some other Dell models.
 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install) 
      
 Install Ubuntu 15.10 on Dell XPS 15 2015 9550 with Nvidia 960
[http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960)

       
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
   sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX  

      
 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa
Should now show newer drivers.
sudo ubuntu-drivers devices

---

### Post by rdragonrydr on 2017-06-06
I installed Ubuntu in UEFI mode. My BIOS has an option under both F12 and F2 to switch to UEFI Non-secure, UEFI Secure, and Legacy Boot ROM modes. I have tried it in both UEFI modes and installing in both modes. (The CD won't boot at all in Bios mode!) I would** prefer **to install in BIOS (Legacy ROM) mode than UEFI, but I can't get the CD to boot for that.

Currently it is in UEFI without secure boot, but I can't even get it to boot now with the nomodeset command, since I tried installing the proprietary drivers. I'll probably have to reinstall.

The Nvidia driver was installed by the GUI window Additional Drivers, which is the frontend to Ubuntu-Drivers that you mentioned. I used the single option listed. I don't remember what it was exactly, but it was the proprietary Nvidia driver.
It is normally this prickly when installing drivers for these cards!?

Ideally I'd use the Nouveau drivers with Prime for GPU switching, but something tells me that I know nothing about how that works and that it likely is outdated or would not apply. Sigh.

---

### Post by oldfred on 2017-06-06
Can you boot in recovery mode, second line in grub?
If UEFI use escape when initially booting.
But if you left fast boot in UEFI on, you may not have time to press any keys. But see if total cold boot, or full power down, unplug mains, hold power switch to drain any left over power for 10 sec or so and then reboot immediately pressing correct key to get into UEFI.

Or can you in UEFI turn off nVidia driver and just use Intel?
It may not explicitly say  that is what your setting is changing.

---

### Post by rdragonrydr on 2017-06-06
What should I do once in recovery mode? I got there once (before I tried the Proprietary drivers that seem to have made things worse), but I will have to see if I still can.

I don't think fastboot is on. It shows a Dell screen with the boot mode options/settings options, then goes purple, a short while later goes black, then stays that way. Before trying the Nvidia drivers, it would go to the Ubuntu splash screen with the dots instead of the black screen, and then the dots would freeze and the computer also locked up. Before, I had a chance of hitting E or Escape, but now I either have not been fast enough or it does not listen for the keystroke. The PC is a laptop with an internal battery, so I can't really disconnect power.

I am pretty sure that it now not booting is related to my using the Nvidia settings menu to use the Intel graphics. (I did not want the dedicated card on for the time being, since I just needed to install all my software) Is this a reasonable guess? Why would their own program for switching cards do this?

I have no graphics card options in the BIOS, at least as far as I can tell.

Is there any way to use open source drivers and switch between cards (for all programs at once) with them?

---

### Post by oldfred on 2017-06-06
This says you have an UEFI video setting to enable switchable graphics.

[http://www.dell.com/support/manuals/us/en/04/precision-m7510-workstation/prec7510_om-v1/System-setup-options?guid=GUID-C846848E-83EF-475B-8AB6-6715BC7F66BC&lang=en-us](http://www.dell.com/support/manuals/us/en/04/precision-m7510-workstation/prec7510_om-v1/System-setup-options?guid=GUID-C846848E-83EF-475B-8AB6-6715BC7F66BC&lang=en-us)

---

### Post by rdragonrydr on 2017-06-06
Thanks, but that's actually not the same one. I have a Inspiron 15 7559, [http://downloads.dell.com/Manuals/all-products/esuprt_laptop/esuprt_inspiron_laptop/inspiron-15-7559-laptop_Reference%20Guide_en-us.pdf](http://downloads.dell.com/Manuals/all-products/esuprt_laptop/esuprt_inspiron_laptop/inspiron-15-7559-laptop_Reference%20Guide_en-us.pdf)

It has no switch option that I can find, and I looked through all the BIOS options. I would love to be corrected, though, as it would probably simplify all my problems.

I CAN still get to the grub menu, it seems. Adding modeset now sent me to TTY1, where it would not let me log in. I believe it still locked up, and I should have seen the greeter, not the teminal. Hm

---

### Post by rdragonrydr on 2017-06-06
Okay. I tried nomodeset again, and this time it worked. The Nvidia settings menu was blank, so I used the terminal with prime-select to enable the discrete GPU. Upon reboot, everything worked, but I have a **glorious 2 hour battery life. Oh, joy.**

Also, I got a crash report stating that a /usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitWebProcess crashed. What exactly is this?

It won't let me use the integrated graphics at all, either (Evidently this **IS** what broke it this latest time). Upon logout or reboot, I just get a black screen with a frozen cursor. Prime-select also does not give an intel option. I am rather regretting this whole excursion and want my **10** hour battery life back. I'd also like to be able to use something other than software acceleration, in that case. [B]How might I get the Intel GPU working again, or instead?

[/B]Darn it, Nvidia has made an enemy.

---

### Post by oldfred on 2017-06-06
I have seen some issues with battery life. I think some where some with really bad had a software fix.
And newer kernels/drivers have improvements. But saved no links as my systems are all desktops.

What version of Ubuntu.
I have 16.04 and newest webkitgtk is 3, not 4. And that is not installed by default. You must have installed some application that needs that.

---

### Post by rdragonrydr on 2017-06-07
I have installed nothing yet, since I had to re-install everything earlier. I assume it's for Nvidia's GUI or something then. It's 16.04. Definitely odd.

Anyway, how might I go about getting the integrated GPU working too?

---

### Post by oldfred on 2017-06-07
I only have desktop  & it is which every plug I connect to. So no UEFI or software switches.
And full desktop motherboards do have an internal UEFI setting to turn on/off internal graphics.
Or do not know with your system if it is possible without using nVidia to do switching.

One post here seemed to have to go thru a lot. But see post #40 & later
[https://ubuntuforums.org/showthread.php?t=2329171&page=3](https://ubuntuforums.org/showthread.php?t=2329171&page=3)

---

