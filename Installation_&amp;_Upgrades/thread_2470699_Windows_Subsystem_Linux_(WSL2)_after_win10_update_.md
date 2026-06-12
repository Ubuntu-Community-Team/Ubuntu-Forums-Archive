---
title: "Windows Subsystem Linux (WSL2) after win10 update xming does not work"
date: 2022-01-08
forum: Installation &amp; Upgrades
---

### Post by dieter-erich on 2022-01-08
Hi,
   please forgive me if this is not the right place to post my question, I could not find any better:

I run xming under Win10 by using the Windows Subsystem Linux (WSL2) in an Ubuntu 20.04 environment. Everything including glxgears ran perfectly well until I updated Windows on the 19th December by the ususal way. According to the update course two function updates were installed (21H2). After the update I now receive the following errors:
 
glxgears
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast

and glxgears ran extremely slowly if at all.

I googled and found a number of entries but none of the procedures described worked. I am convinced that this is a bug but how can I work around it?
Thanks for hints!

---

### Post by TheFu on 2022-01-09
Well, you might not like my answer, but I'd say to wipe that other OS and install Linux on the physical system. That's the only way to get great GPU access, especially for non-experts.

That probably isn't very useful advice, so you may want to use a full virtual machine - perhaps install virtualbox, then install a full Linux into it.  All these funky WSL issues go away.  If you want a full linux, use a full linux. This will not get the high-end performance GPU access, but it is usually sufficient to watch videos and always find to run office applications.  Video editing doesn't like being inside a virtual machine, however.

But know that any heavy graphics will likely have poor performance and need a direct hardware installation to resolve.

I used xming in the early 2000s. It wasn't very good.  That drove me to install a virtual machine tool and load a full Linux desktop. Never looked back.

---

### Post by MAFoElffen on 2022-01-10
Or as a dual boot of Windows and Linux. That is what I have done for the past 13 years now... Well it used to be Windows, Linux and Solaris...

On the problem you described...

(1) Yes... this should have been posted and may still get moved to the Virtualization Section, where most of the WSL and WSL2 posts and questions go... Why? Because it is truly an attempt from Mircosoft to Virtualize Linux with a few extra's. That is what that is.

(2) The graphics part of their Linux virtualization is not worked out yet... Third party vendors have jumped ahead and have tried giving users graphics capabilities through Xming and VcXsrv*... This is not the original attempts... Old-timers like me remembering Ubuntu having  Win App that installed Ubuntu within Windows as a Virt, running on a File-based VM-disk file... Trying to remember. I think it was circa Windows 7 and Ubuntu 12.04 or 14.04... That just by coincidence was when Microsoft and Canonical started getting into agreements together. Then then Microsoft gaining experience from Canonical on Cloud Tech, and Docker, for their development of Azure Cloud... I think that implementation of Ubuntu, running within Windows, was actually was still ahead of where MS is now. 

(3) Microsoft has been working on "WSLg", which is supposed to make VcXsrv and Xming obsolete or at least unneeded.They are not there yet and it is still experimental. Most of their development effort for that are geared for Windows 11, not Windows 10. (Sorry for your loss.)

(4) By your own admission, an update on "Windows 10" broke your ability to use a third party's "Windows 10" app using an implementation of "Xming"... To run Ubuntu, with graphics acceleration in that implementation... Rephrased that way, it is not a problem with Ubuntu Linux at all, but with the Virtualization Host system, that broke it's hooks to the Linux Graphics layer of it's Linux VM Guest.

***- Xming and VcXsrve are applications that try to be able to run XServer and Wayland from within Windows...

By that explanation... Just what Windows update broke it, and is the third party vendor of the Windows App working on a fix to that update? That is outside of any Ubuntu Support, but I personally would be curious and interested in following what the progress of that solution is, because as a User (you), that brought you here for help, thinking we might have some answers that might help.

--> Ubuntu, as an Operating System, running within a virtual Machine, has all the hooks for that to work. If you ran it straight from Hyper-V, as a Gen2 VM, it has hardware Acceleration and works seamlessly, being to cut and paste between. That is the easiest solution for your as a primary Windows user. 

Who knows. After using it for awhile, and learning what you can do, you may want to then expand it to a dual boot system... Or if you really dive into it, run as primary with Windows as a Virtual Machine within it.

The nuts and bolt of it, what you are doing is experimental at the moment, and not very well supported. Since classified as experimental... There are things and changes from MS that are going to break it from time to time. There is easier and more stable ways to do that that have been around for years.

What you do is your own decision. Do you  like to fix things and tinker, or are you someone who needs something stable? I think that is what you need to ask yourself before going on from here.

### Yes... I have supported Virtualization professionally, and then volunteered support for Ubuntu, KVM, MS Hyper-V, VMware VSphere, each,  for well over a decade. I have tried to stay current with the current trends on each, and am a beta tester for all those for all of that time... The current Windows trend for WSL2 is trying, but not Stable yet, In the area of graphics. It's close but still to be considered an "adventure." At the moment. they officially say that Console Sessions are stable, and they support that.

---

### Post by dieter-erich on 2022-01-11
Thanks to both of you for your ample explanations! I admit that I learned only very recently about wsl and simply wanted to try it out. I find it quite handy to have win10 and ubuntu running in parallel although I did not even try to install the gnome desktop. I usually stick to ubuntu mate with the gnome desktop as I hate all the fancy colors and pseudo 3D-stuff and rather prefer it minimalistic.

I had been running WUBI since ubuntu-10.04 in double boot systems with win7 or win10 and despite many warnings and recommendations to not use it, I was always very happy with it. I even ran programs relying heavily on a GPU with reasonable speed. I like very much the possibility to backup a single file to have the entire system ready to copy it back in case of problems. 

I recently acquired an HP Zbook with pre-installed Win10 and tried to install WUBI Ubuntu-20.04 MATE on it but failed so far because of a number of security issues apparently included in the BIOS of this particular laptop. I was too afraid of breaking windows and rather tried wsl.

So, from your answers I understand that wsl is still very experimental. I shall thus go the old way and find out how to install WUBI.

---

### Post by TheFu on 2022-01-11
Just use a virtual machine.  wubi isn't safe and shouldn't be used.
If you must, setup a dual boot, but know that modifies the boot for all OSes. With UEFI, it isn't THAT risky.

---

### Post by MAFoElffen on 2022-01-11
As TheFu said, and I mentioned... Wubi was years and years ago... And it is a Virtual Machine. I don't think WUBI went to (or beyond) 14.04. It was before Windows 10. Hyper-V and other Virtual Machine Host systems were in their infancy.

Hyper-V and other Virtual Host systems are a lot better now. With Hyper-V, with the VM created as a 2nd Gen VM, you will have graphics acceleration, screen sharing, cut & paste, etc. I think you would be happy with that or with a Dual Boot System.

---

### Post by TheFu on 2022-01-11
> **MAFoElffen said:**
>  Hyper-V and other Virtual Host systems are a lot better now. With Hyper-V, with the VM created as a 2nd Gen VM, you will have graphics acceleration, screen sharing, cut & paste, etc. I think you would be happy with that or with a Dual Boot System.

Same for virtualbox, if the guest additions are installed.
Of course, if you make Linux the hostOS, then you gain access to faster and more stable hypervisors that are used 24/7/365 by millions of VMs worldwide.  Basically, there are 2 VPS companies that DON'T use KVM on Linux for the offerings. Everyone else does.  There is a very good reason that KVM is used.

---

### Post by Tadaen_Sylvermane on 2022-01-11
Ii use xming occasionally these days and it works great for me. The WSL is your issue IMHO. Running forwarded X from a bare metal or vm runs quite well.

---

