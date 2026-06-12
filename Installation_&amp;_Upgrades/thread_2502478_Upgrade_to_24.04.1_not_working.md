---
title: "Upgrade to 24.04.1 not working"
date: 2024-11-16
forum: Installation &amp; Upgrades
---

### Post by richard76 on 2024-11-16
HELP ! Sorry if this is the wrong place, it is the closest to my problem: I just upgraded from 24.01 to 24.04 and have only the command page (terminal?) showing, I am an old dog and find most of the terms you are all familiar with a foreign language to me, my screen shows:                                                                                                                                                                                     

Ubuntu 24.04.1 LTS richard-Aspire-XC-115 tty1

richard-Aspire-XC-115 login: richard
Password:
Welcome to Ubuntu 24.04.1 LTS (GNU/Linux 6.8.0-48-generic x86_64)

*Documentation: [https://help.ubuntu.com](https://help.ubuntu.com)
*Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
*Support:            [https://ubuntu.com.pro](https://ubuntu.com.pro)
richard@richard-Aspire-XC-115:~$_


I have tried many LS and CD commands and even some sudo apt, sudo install, all fail although I have had pages of text suggesting alternative commands, but the most relevant answer seemed to me that I do not have an internet explorer type of program (I had Google Chrome on 24.01) and of course attempts to install Google all failed for the same reason.
I did try Ctrl Alt F1 to F6 but nothing changed, and of course I typed my password to login and whenever it was requested and most of the suggestions were for old apps and only variations of the letters I tried.
Please help, I assumed that as an LTS update it would be bug free and did not copy all my files to a memory stick, If I have to install as a new OS I will lose years of docs. photos, music etc.

PS. All text in white on a black screen.

---

### Post by richard76 on 2024-11-16
HELP! like PJ my upgrade from 24.01 to 24.04 has failed (no GUI ?) no other OS installed. I am a78yo. so most of the terms you are all so familiar with are like a foreign language to me please keep it simple, my screen shows ;

Ubuntu 24.04.1 LTS richard-Aspire-XC-115 tty1

richard-Aspire-XC-115 login: richard
Password:
Welcome to Ubuntu 24.04.1 LTS (GNU/Linux 6.8.0-48-generic x86-64)

*Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
*Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
*Support:            [https://Ubuntu.com/pro](https://Ubuntu.com/pro)
richard@richard-Aspire-XC-115:~$_


All the above in white on black, I have tried various scenarios from Youtube, forums etc. including tty1 to tty6, some LS commands, some CD commands, some sudo apt commands and install commands, all to no avail, the most helpful onscreen response was that I had no Internet explorer type program (Ihad Google Chrome on 24.01) other suggestions were along the lines of autocorrect where if you type wooden cloggs it suggests wooden dogs. Trying sudo install to retrieve Google Chrome failed of course because I didn't have Google Chrome.
Please help. Because 24.04 has been around for a while and is now LTS I didn't forsee any problems that might lose me all my files, as will happen If I have to install as a new OS.
I enered my password successfully whenever requested

---

### Post by grahammechanical on 2024-11-16
@richard76

Please open your own thread. Do not try to use this thread to seek help. It will get very confusing trying to solve two problems. Besides which, this

> my upgrade from 24.01 to 24.04 has failed

does not make sense. There is/was no Ubuntu 24.01. The rest of your post does not make much sense either. Open your own thread and tell us the situation as it is now. Tell us the specification of your computer. It seems to me that you have tried so many different things that it will be very difficult for us to separate the original problem from any new problems caused by your attempts to correct things.

I suggest that first of all you ask in this new thread how to save your data from a broken operating system. Succeed at doing that, then you can ask about either fixing the existing install or re-installing.

Oh, and as for age - I am 76 years old. In tha.t new thread I may offer suggestions But not in this thread.

Regards

---

### Post by oldfred on 2024-11-16
Moved to your own thread. Was in this solved thread
[https://ubuntuforums.org/showthread.php?t=2502271&page=2](https://ubuntuforums.org/showthread.php?t=2502271&page=2)
Best not to post in solved thread as no one then looks at it as solved. And your issues look different so should be in its own thread, anyway.

there is no 24.01, so what were you upgrading from?

It looks like your system has a nVidia video card/chip.
Did you reinstall the nVidia driver?
That is proprietary to nVidia, so if UEFI Secure boot on, it would not be automatically installed as you have to create a MOK - machine owner key to authorize it as Secure. And upgrades typically do not install drivers, as you uninstall before upgrade & reinstall after upgrade.

If you can boot to a terminal, does this show drivers?
# list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended 

This will show if it is installed.
#What is installed
dkms status

---

### Post by Irihapeti on 2024-11-16
Posts moved to a separate thread, as it's another issue.

---

### Post by oldfred on 2024-11-16
Merged threads.
Please do not post same thread twice. We all are volunteers and need to know what others have posted.
Merged since posts in both threads.

---

### Post by richard76 on 2024-11-17
Thanks for the prompt responses, I would have liked to have started a new thread ( asked a standalone question ) but could not see where to post it, all options seem to be replies or advanced and obviously I'm not ready to go advanced. As to my previous version it was the one with the jellyfish, my computer is an Acer XC-115 with AMD E2-6110 APU and Radeon R2 graphics, the only alteration I have made was to upgrade the RAM from 4GB DDR3 to 8GB. Although I have tried to solve the problem myself, nothing has changed, I shut down and later reboot to the same place I was at before I tried to solve the problem as I listed in my post.

---

### Post by richard76 on 2024-11-17
Thanks,
1. the version with the Jellyfish
2.Radion R2 graphics
3.unless I try a command (all fail) what I have typed above is all I get

---

### Post by richard76 on 2024-11-17
Thanks, will try new thread ?? in the meantime I have answered questions below

---

### Post by oldfred on 2024-11-17
You now have your own trhead here.
Unless question is now different, you do not need new thread.
Did you check driver status for your nVidia as posted above?

---

### Post by grahammechanical on 2024-11-17
Ubuntu 22.04 LTS has the code name Jammy Jellyfish and has support until April 2027.

I am making a few assumptions:

1) The machine loads to a black screen and does not load to a login screen and then on to a desktop environment. In other words - no GUI.
2) The machine has an UEFI motherboard and not a BIOS boot motherboard.
3) Ubuntu is the only operating system on this machine and so the Grub boot menu does not show.

Therefore, as the machine boots and you see the supplier's splash screen press the ESC key perhaps several times. This should/may cause the Grub boot menu to appear. If that happens then select Advanced Options for Ubuntu. That will show a small list of Linux kernels. Select one that has Recovery Mode as part of its description.

This option will load that Linux kernel and present the Friendly Recovery menu. Select Resume. That will resume the loading of Ubuntu using an open source video driver and not the Nvidia proprietary video driver. Does that get you to a working desktop environment?

If it does, open Software and Updates>Other Drivers tab and disable the proprietary video driver. You need to be connected to the internet to do this. Now, you have a working operating system. We hope. 

Sorting out a proprietary video driver will be much easier with a working desktop environment. And different questions will need to be asked.

Regards

---

### Post by richard76 on 2024-11-17
Thanks, no my graphics are Radeon R2, and when I enter #list drivers available the response is "command not found". Once again sorry to be so ignorant, I have been using Linux, mostly Ubuntu, for over 20 years, originally in computers I built myself but have always relied on the OS to work or prompt me to resolve issues, I am not a software hobbyist (probably reduntant info).

---

### Post by grahammechanical on 2024-11-17
Oh, Radion R2 = AMD. My mistake. Actually the advice I gave still applies. Let us find out if the problem is with the proprietary video driver.

P.S. I have found from experience that when doing an online upgrade to a newer version of Ubuntu it is best to take the operating system back to the default state as far as possible. And that includes de-activating a proprietary video driver. It avoids the possibility of the proprietary video driver not being compatible with the newer Linux kernels that are part of the upgrade.

AMD Radion drivers for UBuntu.

[https://community.amd.com/t5/blender-discussions/amd-drivers-for-ubuntu-24-04-amd-gpu-pro-for-latest-linux-kernel/m-p/689763](https://community.amd.com/t5/blender-discussions/amd-drivers-for-ubuntu-24-04-amd-gpu-pro-for-latest-linux-kernel/m-p/689763)

Regards

---

### Post by richard76 on 2024-11-17
@GRAHAMmechanical,
Thanks, I thought we had cracked it when I was able to follow your instructions through to the "resume"stage, sadly that brought me right back to where I started from. As it is late in London now I will keep trying for a breakthrough (I'm in Sydney Aus) and will try to provide more details later in the day.

---

### Post by richard76 on 2024-11-18
@grahammechanical, thanks again, I went to the page re missing radeon drivers and followed the technique that millertime suggested and 1 other had success with but got
E; unable to locate package rocem-opencl-sdk
E; unable to locate package rocm-core

Restarting bought me back to where I began, I tried once more the resume method, nothing changed, I'm feeling computercidal.

---

