---
title: "Need help setting up resolution/drivers on a work-related Ubuntu USB drive"
date: 2021-12-16
forum: Installation &amp; Upgrades
---

### Post by ribasmudj on 2021-12-16
So I'm clueless about how Ubuntu and Linux work and am a Windows user of 20+years, but now I have to work via AWS from a Ubuntu USB drive that's on 18.04 version. I'm using it in my desktop with an rtx 3080/5600x and hooked to a 4k monitor, but the only resolution in Ubuntu is 1024x768 at 4:3, which makes everything look stretched and low res making work with text difficult.
 
I've been trying countless terminal solutions and all end up nowhere as the system seems heavily restricted by admins, and it's potentially running in a guest mode or something since there's a "VMware Horizon Client" icon on the top left and most(all I've tried) websites are blocked. I'm allowed to fix it if I can but I'm not sure how, I managed to install and open Software and Updates app and there are many nvidia drivers listed as additional drivers, but they are all grayed out and the only option is "continue with manually installed drivers". Trying to add a custom resolution through the terminal and similar steps always end with "[COLOR=var(--black-800)][FONT=var(--ff-mono)]Failed to get size of gamma for output default".

Another maybe relevant info is that Ubuntu recognizes my 5600x CPU in the about section, but logging to Windows through AWS and checking "about" in Windows displays a random Intel Xeon CPU, not sure if that's relevant at all.

Does anyone have an idea on how to install the drivers or just force 3840x2160 resolution here for normal usage?[/FONT][/COLOR]

---

### Post by Impavidus on 2021-12-16
Is this a live usb or a full install to a usb drive? On a live system you can't install the nvidia drivers. Or at least not activate them. On a full install the admin can install proprietary nvidia drivers. It's best to use the additional drivers utility with a few clicks; don't download it yourself from some website for manual installation.

Note that a full install to a usb drive with proprietary graphics drivers isn't very portable. You can only move it amongst computers with identical graphics hardware.

---

### Post by ribasmudj on 2021-12-16
have no idea really, how can I check? I'm booting straight from the USB, looks like a full install to me but can't say for sure as I've never used Ubuntu. If it's a full install is there a way to force wipe the drivers and install the newer ones that are now grayed out in Softwarw & Updates utility or just force a 16:9 resolution with the current drivers?

I know that other collegues who have the same USBs but are also using the company computers with it (not their personal ones like me), have normal 1920x1080 resolutions etc, so I'm getting less available resolutions that others with the same USB.

---

### Post by yancek on 2021-12-16
>  I've been trying countless terminal solution

It's never a good idea to blindly follow instructions from some web site.  Ubuntu is very well documented and you should look for official documentation or use sites such as this one.  Having a specific warning/error message to work with will make it a lot easier to get help.

A full install would have a user created by the person installing, a 'live' usb would only have the user ubuntu which you can see in the /home directory.  A 'live' system is read only and any changes made are lost on reboot by design.  If the usb is work related, what is the purpose, to learn Linux or VMWare?.  I expect it is a 'live' usb.

---

### Post by ribasmudj on 2021-12-16
I'm supposed to work thourgh Amazon Workspace that virtualizes Windows from the Ubuntu USB, and that's where the resolution actually matters to me, but I also only see 1024x768 within AWS virtualized Windows so I suspect that the fault is with Ubuntu since the resolution is also locked there.

---

### Post by TheFu on 2021-12-16
As you've learned, Windows skills don't really transfer and about 80% of your expectations for how things work are wrong.  A Mac user has much more of the needed background than any Windows users because MacOS is Unix-based and under the pretty GUI works like all other Unix systems.  Linux is a Unix-like OS that is 90% the same as all other Unix systems in the world.  All the most popular OSes run Unix, BTW, except 1. THE most popular OS in the world runs Linux, though it is a little odd in the setup, get deep enough and it is Linux through and through. Of course, I'm speaking about Android. Most IoT devices are running Linux too, BTW.

Most 18.04 flavors of Ubuntu are out of support. They get 3 yrs of support. Ubuntu Server (no GUI) and Ubuntu Desktop with Gnome3 have 5 yrs of no-hassle support. Sadly, Gnome3 is a bloated mom dog and extremely slow, especially when run from a USB flash drive.

So .... 

First, move to 20.04 and any lite flavor of Ubuntu instead for your needs.  XUbuntu or Lubuntu or Ubuntu-Mate are all excellent.

After you do that, perform an install or use a *persistent OS overlay* with **mkusb** and install the needed drivers. To install recognized drivers for a specific system, use 
```
sudo ubuntu-drivers autoinstall
```
There's good news and bad news about this.  The good news is that this will get the current, supported, drivers for the GPU in the machine you are running. The bad news is that, like with all OSes, those drivers are tied to the actual hardware, so you cannot take the flash drive to a different system without identical GPU and expect it to work.

More bad news is that some new hardware, like Ryzen 5xxx series APUs need a very new kernel (5.11.x) to support the built-in GPU.  The default kernel (5.4.x) won't work and you'll likely be stuck with VESA GPU driver support.  On 18.04, forgetaboutit - this applies to any unskilled user.  There are ways to run newer kernels on older OSes running on fairly new hardware, but those techniques are beyond typical Ubuntu users.  I don't know the current support for Intel 11th-gen devices. Sorry.  The newer AMD GPU will need a newer kernel if you want higher resolution. Sorry. The easy answer to get that is move to 20.04 and upgrade the kernel to 5.11.x.  I think that would be the "HWE" kernel.  [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop) has more details. You cannot boot from an ISO. You must do a real install.

nvidia GPU drivers would be installed with the *ubuntu-drivers* command.
AMD and Intel GPU drivers are part of the kernel, so a current kernel is very important.
Older, out of support, nVidia GPUs typically have some working drivers, but they aren't high res versions that I've seen. I had an nvidia GPU lose support when I moved to 16.04. The solution to make the system work was to buy an $80 GPU (nvidia GT 1030). I think it is $110 now.

---

### Post by TheFu on 2021-12-16
In theory, if you right click on the desktop, there should be a display or monitor setting app. Pick that and see if there isn't a way to control the resolution.  Because I don't use a desktop environment (as you know it), I cannot check.

There is also another tool - xrandr - which can control the resolution of a screen.  It works with the X/Windows display server. You may not be using that, but might be using Wayland instead.  Wayland is starting to replace the 40 yr old X/Windows display server. I have no idea how to manage resolution with Wayland, sorry.

You really need an install. Running from an ISO (read-only) won't allow you to change things as you seem to need to change them.

---

### Post by ubfan1 on 2021-12-16
Also, check that your motherboard firmware is up to date.  The 21.10 Ubuntu releases also come with more current kernels out of the box, if you can accept the 9 month support for non Long Term Support releases.

---

### Post by ribasmudj on 2021-12-16
Thanks for the answer. So you'd say the only viable way of adding other resolutions is updating the whole OS first? Can this be done on an USB install since that's the one thing I can't change. I can install Ubuntu on my SSD at any time but I have to be working from this particular USB since it's authorized for AWS by the company, I can't log in to AWS from other installations or from my own Windows for that matter. 

I think I tried the system update yesterday and that it was also locked, can't remember the exact error but I'll give it a try when I get home soon. I know that -xrandr commands for resolution all ended with the "failed to get size of gamma for output default" error that i listed in the post. I also tried the "sudo ubuntu-drivers autoinstall" and there was a dependancy error, can't remember the message but I'll try it again soon and post the exact one.

As for the other users having resolutions other than 4:3 using these exact same USB installs but on company desktops, as opposed to me using the USB on my PC, is that only down to those desktops having older hardware compatible with 18.04?

---

### Post by TheFu on 2021-12-16
> **ribasmudj said:**
> I'm supposed to work thourgh Amazon Workspace that virtualizes Windows from the Ubuntu USB, and that's where the resolution actually matters to me, but I also only see 1024x768 within AWS virtualized Windows so I suspect that the fault is with Ubuntu since the resolution is also locked there.

So ... there are 2 different resolutions.
a) That for the local copy of Ubuntu which you need a newer kernel to access
b) Resolution for the remote Windows system running in AWS.

You can right click on the remote Windows system and change the resolution however you like, but until the local Ubuntu has the proprietary drivers (which I doubt you'll ever get working), I don't see it.  Can you move the Horizon program/app to a newer Ubuntu?  That is really the issue. If that cannot be done, get used to 1080p resolution.

Also, you absolutely need to know if you are using Wayland or X11 (aka X/Windows).  In 20.04, Wayland became the default. In 18.04, they were still using X/Windows with Wayland as a custom install modification.

---

### Post by TheFu on 2021-12-16
> **ribasmudj said:**
> Thanks for the answer. So you'd say the only viable way of adding other resolutions is updating the whole OS first? Can this be done on an USB install since that's the one thing I can't change. I can install Ubuntu on my SSD at any time but I have to be working from this particular USB since it's authorized for AWS by the company, I can't log in to AWS from other installations or from my own Windows for that matter. 

I think I tried the system update yesterday and that it was also locked, can't remember the exact error but I'll give it a try when I get home soon. I know that -xrandr commands for resolution all ended with the "failed to get size of gamma for output default" error that i listed in the post. I also tried the "sudo ubuntu-drivers autoinstall" and there was a dependancy error, can't remember the message but I'll try it again soon and post the exact one.

As for the other users having resolutions other than 4:3 using these exact same USB installs but on company desktops, as opposed to me using the USB on my PC, is that only down to those desktops having older hardware compatible with 18.04?

You aren't just trying to add more resolutions. You are trying to support very new hardware.  Linux updates move fast.  Effectively, you are trying to run the hottest GPU on WinXP. There aren't any drivers for it, so you are stuck with a fallback driver that is meant only to work enough for someone to move to a supported release.
The kernel isn't the entire OS. You need a new kernel which has drivers for the new hardware.  Alas, that new hardware is supported only in 5.11.x kernels and 18.04 came with a v4.15 kernel which could be HWE upgraded to v5.4 kernel. In short, you can't get there from here still using 18.04.

Everyone else is using the company computers which the flash drive was setup to support. Why don't you do the same, for now, until you have a greater understanding of Linux systems.

If it were me, I'd look towards moving the Horizon client to Ubuntu 20.04.
[https://askubuntu.com/questions/1237445/vmware-horizon-client-not-working-in-ubuntu-20-04-lts](https://askubuntu.com/questions/1237445/vmware-horizon-client-not-working-in-ubuntu-20-04-lts) 
[https://www.stephenwagner.com/2021/05/02/install-horizon-agent-linux-ubuntu-20-04-lts-vdi-guest/](https://www.stephenwagner.com/2021/05/02/install-horizon-agent-linux-ubuntu-20-04-lts-vdi-guest/)
Appears in my quick reading that the Horizon authentication is just normal CA setups.  You should be able to pull the CAs from 18.04 and move those into 20.04.

[LIST=1]
[*]Install 20.04 into a fresh storage area. That can be a different Flash drive or SSD or where ever. Do a real install, not just a copy.
[*]Upgrade the system fully, including to the 5.11.x kernel <--- that's just the HWE instructions.
[*]Ensure you run X/Windows, not Wayland. This is a pre-login option.
[*]Set the resolution to whatever you like.
[*]Export and import the AWS/company CA from the 18.04 system into the 20.04 system.  I think this is just a file copy using sudo and running an update command: [https://askubuntu.com/questions/73287/how-do-i-install-a-root-certificate](https://askubuntu.com/questions/73287/how-do-i-install-a-root-certificate)
[*]Install the 20.04 Horizon client to the new 20.04 system. Looks like there are some dependencies that need to be fixed according to the links above. Looks like python2 is one of them. Ouch. This is all VMware stuff. Haven't touched VMware stuff since 2011 when we dumped them for better alternatives for our clients/needs.
[*]Move any Horizon configs and apps from 18.04 to 20.04. I'd just keep the specific locations for everything where they were before. Same userid, same directories.  Be certain to get any settings from /etc/HORIZON or other places that aren't in the HOME directory. I don't know where these things are. Look in VMware's documentation.
[*]Bob's your uncle.  
[/LIST]

Obviously, I've not done this and don't know if it will work or not. The first 5 steps are less than 20 minutes. The VMware dependencies and later are the hard part to me.

---

### Post by MAFoElffen on 2021-12-17
Just some notes...

Hardware-wise, you are running: RTX 3080/5600x, which is bleeding edge highend. The kernel, GPU and hardware support were well after 18.04. 

I would say at least HWE installed, with possibly upgrading to 20.04 LTS. You can installed the HWE and the Video driver for the NVidia RTX 3080 on 18.04, but it would be better supported on 20.04.

Where TheFu said to right-click on the Desktop... Rather,go to the Settings > Desktop.

Next, play with the DE choices at the DM (the Icon to the right of the password input cell on the graphical login panel)to switch to XServer or Wayland to see if that makes a difference. Follow his instructions for ubuntu-driver, for it to see what you have, and it will pick the best choice that will work for the hardware it see's.

Any remote connection, is going to be limited by the resolution of the clients resolution your oc). You cannot display a 1080p session on something that is set at a resolution  that is lower than... yours being 1024x768. If it does display, then it will be larger than your own screen being shown. Yes, I have experience that sometimes.

If you run the Forum's 'system-info" script in my sig-line, while booted from your USB installed session, there is a failrly extensiver graphics settings and environment informaton sectio of that report, that will answer most of the information people have asked you... and more.

---

### Post by TheFu on 2021-12-17
I have an AMD Ryzen 5600G APU. The system runs 18.04, but it isn't used as a desktop. It is mainly a server that I remote into. To get the resolution higher, I did some research and found that support for the Ryzen 5xxxG GPUs (those built into the Ryzen CPUs) requires a 5.11 or later kernel.  Because I'm a long-time Linux user (since 1993) and both have been an admin and a software developer, I was willing to risk running a bleeding edge kernel for a few months before migrating the system to 20.04. I am confident that I'd recognize when an issue was user-error or program error or system error or kernel error. Those are all different, so I installed 5.11.20-051120-generic.  Currently, it runs 5.15.10 - because I haven't gotten the time to move to 20.04 off 18.04. I also boot the 18.04 HWE stock kernel, 5.4.0-91, when no graphics work is planned, which is most of the time.

Alas, if you are running off a USB flash drive with an ISO boot, you cannot change the kernel anyway, so the first step is to get a real install.

Please run that "system-info" script in MAFoElffen signature. It is safe. A few of the most dedicated volunteers here helped create and tested the script that MAFoElffen created. It has been approved by the UF team - safe to use. It gathers information and strips out any system identification stuff that is any concern.  Run the script. Look at the output, then post the URL (paste.ubuntu.com) created and we'll take a look. It should tell us the kernel, how/if this is a real install and a bunch of other things.  Facts, not guesses. That's important.

---

