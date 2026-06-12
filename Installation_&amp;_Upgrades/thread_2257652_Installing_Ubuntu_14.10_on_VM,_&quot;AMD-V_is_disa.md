---
title: "Installing Ubuntu 14.10 on VM, &quot;AMD-V is disabled in the BIOS&quot; error"
date: 2014-12-21
forum: Installation &amp; Upgrades
---

### Post by will.campbell.492 on 2014-12-21
So I'm just barely getting into Linux, and wanted to try it out on VirtualBox first.  I downloaded the .iso, created my virtual hard drive, and set it to the CD/DVD Drive in settings.  Now when trying to start Ubuntu through the VM, I get the following error: 

Failed to open a session for the virtual machine **Will's Linux**.AMD-V is disabled in the BIOS (or by the host OS). (VERR_SVM_DISABLED).
[TABLE="width: 100%"]
[TR]
[TD]Result Code:[/TD]
[TD]E_FAIL (0x80004005)[/TD]
[/TR]
[TR]
[TD]Component:[/TD]
[TD]Console[/TD]
[/TR]
[TR]
[TD]Interface:[/TD]
[TD]IConsole {8ab7c520-2442-4b66-8d74-4ff1e195d2b6}[/TD]
[/TR]
[/TABLE]

I'm rather inexperienced when it comes to working with BIOS's and the nitty-gritty of computers, so step-by-step instructions would be much appreciated.
Also, I'm running Windows 8 x64.

Thanks!

---

### Post by ibjsb4 on 2014-12-23
vBox system settings is also referred to as bios (vm bios).

Look here in the guest install:
[ATTACH=CONFIG]258750[/ATTACH]
If it is grayed out, then you need to look for the option in your computer bios.

Edit
What processor are you running?

---

### Post by nerdtron on 2014-12-23
Yup depends on processor and on the BIOS Setting (of the main computer). 

Maybe on the BIOS you'll see a setting like "Virtualization Technology", you should probably enable that.

---

### Post by will.campbell.492 on 2014-12-23
Thanks!  I changed the Virtualization setting in the BIOS and that fixed it.
I'm successfully running Ubuntu now, but one quick question:  I ran the installer and was told it failed, and it subsequently automatically posted the error report using Firefox.  However, the Ubuntu 14.10 installer is still on the desktop.  I'm kinda confused since it seems that Ubuntu has installed, but I was told it failed.  Any idea what's up with that, if I should ignore the installer or what?

---

### Post by nerdtron on 2014-12-23
What error is it? and also if the ubuntu installer is still on the desktop, are you sure you are not booting the Ubuntu iso which is the cd drive?

---

### Post by will.campbell.492 on 2014-12-23
Well I can't answer either of your questions right now.  After the installer failed, I shut down VirtualBox as I had other things to do.  Now that I'm restarting it, I get this screen and haven't a clue what to do about it.
[IMG]http://s8.postimg.org/59rar86cl/ubuntufail.jpg[/IMG]

---

### Post by nerdtron on 2014-12-23
No clue either.. try reinstalling and this time try to capture the error of the installer.

---

### Post by will.campbell.492 on 2014-12-23
Turns out I just hadn't selected the .iso in storage settings, I guess that was tripping it up.
When I restarted, it didn't go to the desktop, instead I was forced to reinstall Ubuntu.  The installation failed where it has the past two times, and sent me to [this page]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/220961") on Firefox.  Although it says the error would indicate lack of disc space, I remember allotting 30 gb to Ubuntu originally, even though settings say storage is dynamically allocated.  Either should work.

---

### Post by nerdtron on 2014-12-25
Another one to look at is the bad .iso file. Try downloading again. Or try the other versions such as xubuntu.

---

### Post by MAFoElffen on 2014-12-26
IDK. I've followed this thread for the past 2 days... but have just watched it, waiting...

Somethings I've not seen asked is: 
-What is the host OS? 
-What is the host hardware specs? 
-What is the iso image you are trying to install?
-What are the VM settings you are trying to install into?
(all these things affect how things install in a "same" virtual manager.)

Why do I ask those questions? Well, Ubuntu 32bit OS'es install easily in most Virtual Managers using default settings. When I install in most of them, I use Linux-Ubuntu/version... default VCPU settings with 1 VCPU, 1GB RAM, NIC at NAT (or br0), default hdd controller, default video. (Xen, KVM, VirtualBox, VMWare and Hyper-V...) 64 bit you have to set the VT-M virtual hardware switch in the BIOS. I usually start out at 8GB of disk.

Other flavors of Linux and Unix are pickier. Some you have to set the HDD controller to IDE for them to see the virtual disk. Some do not like Virtio network drivers, so they want a NIC card "type" set that they support... Some distro's I have to copy the host cpu setting into the VM's cpu settings... Current Ubuntu seems to support all those drivers, without problems...

I maybe have done over 4000 hard installs and more than that in virtual installs... and I don't understand what may be plaguing your install yet. Sorry, I finally had to jump in and ask. Please answer the above questions and maybe, together, collectively, we might find an answer.

But nerdtron may be right with another aspect, in that, depending on your host, the VM Manager and your host graphics, full blown Ubuntu may not work to it's full capabilities inside a virtual manager. Check to see what the VM host video options are and post back what they are. Unity demands a lot along those lines. Xubuntu might be a better choice if your host and virtual manager's video support can't measure up to that. (Some VM Manager's will do pass through to the host graphics / some don't.)

---

### Post by will.campbell.492 on 2015-01-09
I'm back with my deepest apologies.  I was in North Carolina for a week with my ridiculously slow laptop, and then got swamped with work the first week back at school and had to time for VirtualBox.

To answer MAFoElffen's questions:
Host OS - Windows 8.1 x64
Specs - Processor Information:    Vendor:  AuthenticAMD
    CPU Family:  0x10
    CPU Model:  0x4
    CPU Stepping:  0x3
    CPU Type:  0x0
    Speed:  3013 Mhz
    4 logical processors
    4 physical processors
    HyperThreading:  Unsupported
    FCMOV:  Supported
    SSE2:  Supported
    SSE3:  Supported
    SSSE3:  Unsupported
    SSE4a:  Supported
    SSE41:  Unsupported
    SSE42:  Unsupported

Video Card:
    Driver:  AMD Radeon HD 6700 Series


    DirectX Driver Name:  aticfx32.dll
    Driver Version:  14.200.1004.0
    DirectX Driver Version:  8.17.10.1129
    Driver Date: 20 June 2014
    OpenGL Version: 4.2
    Desktop Color Depth: 32 bits per pixel
    Monitor Refresh Rate: 75 Hz
    DirectX Card: AMD Radeon HD 6700 Series
    VendorID:  0x1002
    DeviceID:  0x68bf
    Number of Monitors:  2
    Number of Logical Video Cards:  2
    No SLI or Crossfire Detected
    Primary Display Resolution:  1920 x 1080
    Desktop Resolution: 3200 x 1080
    Primary Display Size: 20.04" x 11.26"  (22.95" diag)
                                            50.9cm x 28.6cm  (58.3cm diag)
    Primary Bus Type Not Detected
    Primary VRAM: 1024 MB
    Supported MSAA Modes:  2x 4x 8x 

Memory:
    RAM:  7677 Mb
If you need more than this, I'd be happy to provide.  I just included what I thought was most important.  And this is according to Steam.

ISO - Torrented from the Ubuntu site.  File name is ubuntu-14.10-desktop-amd64.iso



VM Settings - It's VirtualBox, and I'm not quite sure what you want me to post settings-wise, as there are a lot, and none are easily copypastable.


I've been wanting to install Ubuntu rather than another version because I want to switch over totally within the next few months.  Windows 8 is not doing it for me, and I love learning about computers anyhow.

Upon trying to install again about an hour ago, it was drastically different from previous installs.  I ran out of space during it, although that was likely because I chose to install media programs and such on the install page.  I don't recall if I had done that before when trying to install.  Anyway, I got these two error messages, and then had to force shut down because the window wouldn't close upon clicking "close" several times, waiting 20 minutes, and trying again.

[IMG]http://s22.postimg.org/e4eg1dgtd/no_space_error.jpg[/IMG]     [IMG]http://s22.postimg.org/g7ov91gm9/ubuntu_crash_error.jpg[/IMG]  this is the one giving me trouble.  I had to to do a manual shut down because "close" wasn't working.
Sorry for such a long, annoying post.  If there's anything I can do to clarify, please let me know.  Thanks!

---

### Post by MAFoElffen on 2015-01-10
Okay- Good to see you back trying this. 

Win 8.1 Pro? If Pro, why aren't you using Hyper-V?

From a cmd prompt in a cmd window:
```

FCIV -md5 -sha1 path\filename.ext

```
Compare that with what Ubuntu has listed for their ISO's: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
To see if it downloaded okay.

I haven't used VirtualBox in a while (have it intsalled here on 3 boxes...). It used to be great. 

Since I do a lot of testing and development. and am trying to slim down my hard iron... I use a lot of visualizations.

I also use VMWare Player, QEMU, KVM, Xen, Hyper-V.

As I remember on VirtualBox (It's currently booting on another box so I  can refer in more detail...), When you create a new VM, it has a panel asking you what type of OS you are trying to install. That presets a loot of options about the Virtual machine, the virtual HDD controller and the disk type settings.

On your screen shot of errors, I see that often. The TSC (time stamp counter) error came be ignored. That is saying that at boot the timestamp is off at the moment, but that resyncs later in the boot to correct that, so... Failed to access perfctr msr (MSR c1 is 0)It's not an error, it says that the CPU doesn't support performance counters.

Set Type = Linux ; Which will open the Version combobox, Select Ubuntu (64bit) ;
10024MB RAM ; Create VHD now. Use the default 8GB for size ; etc...

I create it. Then before starting the first time I review the settings. On start, I use Devices to point the DVD drive to an ISO file. Machine > Reboot VM. No troubles.

On newer kernels, those 2 messages are common place. It's because systemd, even though it has not completely replaced inet in the debain branch yet, the kernel core is the same. The hooks are still there. It does a lot of startup type probes and checks. Even though it has those messages, those do not prevent a startup. (Hoping systemd will be approved this dev cycle)

But I having said that, just that aside, other things about that time will. I notice on a first install of recent rhel, Centos, Fedora and UNIX OS'es in a virt, there is a very long pause at that time (up to 1-1/2 minutes) while it does some checks... Most will continue after that pause. 

Some will not. On those that do not, on other virtual servers, I 1st change the virtual HDD controller type, from SATA to IDE. A lot of those will then work fine. On others, I have to change the CPU type from default to a mirror of the host, so it can get past it's checks... Note that I don't have to do this with an Ubuntu distro. (mostly the Unix distro's)

Hope that info helps.

---

### Post by will.campbell.492 on 2015-01-25
Well, thanks for the heads up about Hyper-V, didn't even know it existed.  Installed Ubuntu with ease using a few tutorials, and I'm having none of the previous install problems.  The only one I've really got at this point is that my network connection is nonexistent.  Hyper-V Manager says it is connected to Virtual Switch 1, an external connection.  Ubuntu tells me that only Ethernet is an option, and gives a "Disconnected - you are now offline" error every few minutes, so I'm not sure what to do in order to connect Ubuntu to that Virtual Switch.  Unless the Virtual Switch itself is the problem, though I followed [this tutorial]("http://www.techrepublic.com/blog/windows-and-office/create-a-virtual-switch-in-windows-8-client-hyper-v/") to the letter.

I've also allocated 2 gb of RAM to the VM, and it's running rather slowly.  I don't know if that's normal, just figured I'd see.

---

### Post by MAFoElffen on 2015-01-25
In Hyper-V, there are 3 different network Virt-switch options... External, Internal and Private. You want to use External. External is the only type that has access to the host and to the internet, through the host. (NAT)

On Memory for a Desktop, I set at 1024, but check the box for dynamic. That means it will try to start in 1024, but adapt to what it needs after that. Giving it  a hard 2GB is too much if you later want to start more at a time. Guest servers I use dynamic at 512MB.

---

### Post by will.campbell.492 on 2015-01-25
[FONT=book antiqua]Yeah, I got the part about virtual switches, mine is set up to be external.  However, in the "Network Connections" tab in Ubuntu, only Ethernet shows up.  I'm not sure if there's an extra step I need to do in order to use NAT.  If so, I haven't done it.  Here's the "Network Connections" tab and the pop-up menu.
[/FONT][IMG]http://s10.postimg.org/6mle6gjpl/noconnectionerror.jpg[/IMG]

---

### Post by MAFoElffen on 2015-01-25
Please explain... What did you think you would see or what more are you trying to find?

(Sidenote- External is NAT.)

I'm thinking from the wording on your last post, that you are looking for a wireless device? If a VM host has a wireless connection and you bind and external virtual switch to the VM hypervisor, the connection will show to the guest as a wired connection... The only exception to that is if you go third paty and add in a special wireless virtual appliance. 

That means the hypervisor would have to have virtual device add for a guest to see that virtual device. Most hypervisors don't have a virtual wireless appliance as an available default device. Wireless is not a VM Guest kind of thing.

So yes, if you bound NAT (Extrenal in Hyper-V) to your Host's wireless device, your guest see it the virtual wired connection.

You have network now right? (That's what I saw in your posted pic...)

---

### Post by will.campbell.492 on 2015-01-26
Well, the part I'm confused on is what I'm supposed to connect to through the VM. I don't have any Internet connection in the VM, even though an external virtual switch is set up as the network adapter.  Should Wired Connection 1 be giving me Internet access?

---

### Post by MAFoElffen on 2015-01-26
Create "external"... during that creation, you bind that to a physical network device on the Host. That could be wither a host eth or host wan. In VM, you select whatever you named that VM NIC connection as... The hypervisor makes the connection between the guest and host through virtual appliances.

You can edit existing, create new, etc and applied them to a VM without doing anything to the VM Guest itself. It will take effect after the VM is off and booted back up with that change.

---

### Post by will.campbell.492 on 2015-02-20
Yeah, that's what I'm confused about.  I've only set up one virtual switch, and it's connected to my wifi.
[IMG]http://s28.postimg.org/wt0jpx499/external_connection.jpg[/IMG]
The virtual machine itself still doesn't have Internet access though.

---

