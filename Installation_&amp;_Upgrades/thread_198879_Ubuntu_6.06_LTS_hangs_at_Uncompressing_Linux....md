---
title: "Ubuntu 6.06 LTS hangs at Uncompressing Linux..."
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by nick1 on 2006-06-17
Greetings,

To start, here are my System Specs:

Dell Latitude D800 Laptop computer
2GHz Pentium processor with Centrino mobile technology
1GB of RAM
60GB hard drive
NVIDIA GeForce FX Go5650 128MB video card
OS: Windows 2000 Professional SP4
VMware Workstation version 5.5.1 build-19175

Situation:

I'm trying to install Ubuntu 6.06 LTS (Dapper Draker) as a guest OS.
I'm configuring the virtual machine as follows:

Typical > Linux > Ubuntu > bridged networking > disk size: 4GB > Allocate disk space now

I've used the 'CD check' option in Ubuntu to verify that the install CD is defect free.  The installation completes, reboots, then hangs at:
---
Booting 'Ubuntu, kernel 2.6.15-23-server'

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.15-23-server root=/dev/sda1 ro quiet splash
[Linux-bzImage, setup=0x1c00, size=0x16b75f]
initrd /boot/initrd.img-2.6.15-23-server
[Linux-initrd @ 0xf840000, 0x69f606 bytes]
savedefault
boot
Uncompressing Linux... OK, boot the kernel.
---
Then the system just hangs from there :-(
I'm a newbie to Linux so I'm really not sure how to resolve this problem.
I've had previous versions of Ubuntu installed and running on VMware workstation.
Google searching didn't return much in relation to this specific situation.

Any thoughts?

Thank you for your time,

Nick

---

### Post by FredB on 2006-06-18
Looks like you grabbed a server version... What about grabbing a desktop version and try again ? ;)

---

### Post by James Wilford on 2006-06-18
I've got the same problem. I upgraded from Breezy, and this happened as soon as I rebooted. I had some other problems (no sound, no OpenGL) so I decided to do a clean install of Dapper, and this boots, but it uses the 386 kernel.

I have an Athlon CPU, and I have found that it hangs on "Uncompressing Linux" if I use the K7 or 686 versions of the kernel. I have tried:
[LIST]
[*]2.6.15-23-K7
[*]2.6.15-25-K7
[*]2.6.15-25-686
[/LIST]
These all hang. But 2.6.15-25-386 boots OK. Here's my CPU:

$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 8
model name      : AMD Athlon(TM) XP
stepping        : 1
cpu MHz         : 2083.288
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips        : 4169.15

Also, as it might be related, I'm using a SATA drive with a promise on-board controller:

james@james-desktop:~$ lsmod | grep promise
sata_promise           11780  8
libata                 78992  1 sata_promise
scsi_mod              139496  7 sr_mod,sbp2,sg,usb_storage,sd_mod,sata_promise,libata

However, this worked perfectly with the K7 kernel in Breezy.

Any ideas would be appreciated, I don't know how much performance I'm losing by using the 386 kernel but it would be nice to be able to use the proper kernel for my system.

---

### Post by nick1 on 2006-06-18
FredB:  The server version of Ubuntu 6.06 is the version I want to install, not the desktop version.  I'd like to use the LAMP installation option with the server version.  But thank you for your reply anyways.  Any ideas how I can get the server version working on my laptop inside of a virtual machine?

James:  I feel your pain.  It sounds like your receiving the same error after performing an upgrade.  Whereas I'm doing a fresh install of Ubuntu 6.06 server.    How does one go about switching kernel versions?  I'm sorta a newbie to linux but still trying to hang in there despite errors such as these.

I've tried over and over again creating a new virtual machine with Ubuntu 6.06 server.  However each time the same thing happens:  installation is flawless, system reboots, then hangs at Uncompressing Linux...  :( 

Keep each other posted,

Nick

---

### Post by MarkSparks on 2006-06-18
I am having the same issue. I am using VMWare 5.5.0. Upgrading to 5.5.1 didn't help. Older versions of ubuntu work fine. I'm going to try to install it and then use the advanced CD to see if I can upgrade it. I'll let you guys know if it works later today. 

Mark.

I am using the Desktop version.

---

### Post by James Wilford on 2006-06-18
Hi all, after some googling, I've found the solution to this. You just need to disable acpi by adding the kernel option "acpi=off". So my menu.lst entry now looks like this:

title           Ubuntu, kernel 2.6.15-25-k7
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-25-k7 root=/dev/sda2 ro acpi=off noapic nolapic quiet splash
initrd          /boot/initrd.img-2.6.15-25-k7
savedefault
boot

And now I'm happily running the K7 kernel! If you can't boot in order to make this change, you can edit the kernel options before booting at the grub menu.

Another tip, in menu.lst, add your kernel options to this section:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=acpi=off noapic nolapic quiet splash

Note you don't need to uncomment it. This is read by dpkg when installing new kernels, so you can automatically keep your kernel options when the kernel is upgraded.

James

---

### Post by nick1 on 2006-06-18
Thanks for the update.  I too noticed that suggestion via google searching however it doesn't appear to work for me :( Perhaps my laptop is a little different than yours.  Definitely becoming frustrated with this error...

Nick

---

### Post by James Wilford on 2006-06-19
nick1, have you tried "acpi=off noacpi" as per this thread:

[http://www.vmware.com/community/message.jspa?messageID=332362](http://www.vmware.com/community/message.jspa?messageID=332362)

Your situation is slightly different in that you're creating a virtual machine, whereas I'm having the problem on physical hardware.

The only problem with disabling acpi is that now my PC doesn't auto power-off at shutdown. I'm not bothered about the other acpi features as its a desktop, not a laptop. But having to wait for shutdown then press the power button is a bit annoying, so I'm going to see if I can get APM to do this instead.

---

### Post by nick1 on 2006-06-20
Still no success *sigh*
I edited the boot parameters by hitting ESC when displayed the option to do so.
My kernel line looks like:

kernel /boot/vmlinuz-2.6.15-23-server root=/dev/sda1 ro quiet splash acpi=off noacpi

I then rebooted and the system still hangs after Uncompressing Linux... ok, booting the kernel.

I'm stuck.  I have no idea where to go from here.  Can someone PLEASE, PLEASE, PLEASE help me out?  I really want to get Ubuntu 6.06 server installed as a virtual machine in VMware workstation 5.5.1.

I tried editing the menu.lst file with vi however it's extremely frustrating to use and at times displays charactors I'm not even typing.

Thanks,

Nick

---

### Post by nick1 on 2006-06-20
*big sigh*

Well I'm stuck :( I've been trying for days to figure out what's going on with this problem. Today I used the same Ubuntu install cd to create a virtual machine in the same version of VMware workstation but on a different computer running Windows 2003 and it worked.
Figuring it might be an OS issue, I went back to my laptop and booted into my Windows XP installation (I have a dual-boot system: Win2k Pro & WinXP Pro) and tried installing an Ubuntu virtual machine using the same installation disk and version of VMware workstation - it didn't work. Again, the installation hung at 'uncompressing linux' when trying to boot.
So obviously Ubuntu 6.06 + VMware workstation 5.5.1 + a Dell latitude D800 = doesn't work.
What is it about this combination that doesn't work?

PLEASE HELP!

Nick

---

### Post by elchanan on 2006-06-21
I'm seeing the exact same problem using a Thinkpad R51.
I'll be watching this space for enlightenment.

Elchanan
---------

---

### Post by redbyte on 2006-06-21
using a Thinkpad T41p with WinXP Host, VMWare 5.5.1 I encounter the same problem. Annoying :confused: 

--
regards
Marcus

---

### Post by rcarring on 2006-06-21
For nick's benefit:

My system is a toshiba satellite 1110 dating from November 2002, running XP SP2 (I am running Professional not Home btw) with a 16mb ATI Radeon graphics card, 256mb memory and the host hard disk is a 20GB Tosh HDD split into two drives of approx 10Gb each. I use a 100GB usb 2.0 external hdd which is split into 20GB primary and two 40GB logical drives. The vm lives on one of the logical drives.

---

### Post by nick1 on 2006-06-21
A bug report has been filed at:

[https://launchpad.net/distros/ubuntu/+bug/48284](https://launchpad.net/distros/ubuntu/+bug/48284)

Hopefully someone in a higher-up position is seriously looking into resolving this issue.  Lets keep making noise until someone hears us.

Keep each other posted,

Nick

---

### Post by caldaar on 2006-06-21
I am having the same issue trying to install the server install on a D600 laptop.  Although I am not using VMWare, but trying to do a full install.

---

### Post by nick1 on 2006-06-21
Update:

Today I was able to install the 'ubuntu-6.06-alternate-i386' cd in VMware workstation 5.5.1 build-19175 as a virtual machine with Windows 2000 Pro SP4 as the host O.S.  Now why the hell does the alternate cd work and not the server cd?????????
Unfortunately there wasn't a LAMP server option so I don't think those applicatoins are installed at this point.  I'm still not satisfied because the LAMP option is what I want to take advantage of on the server cd.
This thread just keeps getting more and more interesting, lol.  *sigh*
Next I'm going to try to install 6.06 server in VMware Server ([http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)) and VMware ESX ([http://www.vmware.com/products/vi/esx/](http://www.vmware.com/products/vi/esx/).  I'll post my results as usual.

During my adventures I came across a simple yet effective Md5 check sum application for Windows.  The application is available at ([http://www.nullriver.com/index/products/winmd5sum)](http://www.nullriver.com/index/products/winmd5sum)).  Remember to verify the Md5 on each Ubuntu .iso file you download.

Nick

---

### Post by nick1 on 2006-06-22
*HUGE SIGH OF RELIEF*

Well I think I got it working in my case.  I needed to install the 686 kernel for things to work.  Below are instructions on how to install Ubuntu server 6.06 as a guest virtual machine in Windows VMware workstation 5.5.1 using the Ubuntu 686 kernel.  These instructions may also apply if you're not using VMware.

How to Install the Ubuntu 686 Kernel
====================================

1.)  boot to the Ubuntu 6.06 server install cd.  Choose 'Rescue a broken system.'

2.)  when you get to the Rescue Operations screen choose "execute a shell in /dev/discs/disco/part1", this option may read a little differently on your system.

3.)  Click continue if another screen appears.

4.)  At the prompt, type:  sudo apt-get install linux-686

5.)  You will be asked if you want to continue, type: y

6.)  The installation of the 686 kernel will begin.  It looks like an internet connection is required so the install files can be downloaded from the ubuntu website.

7.)  When the installation is done, type:  exit

8.)  You should be returned to the Rescue Operations screen.  Choose the last option: reboot the system.  Make sure you're not booting to the install cd!

9.)  Give the system a few moments to boot-up.  At last, you should be placed at the login: prompt.

10.)  Celebrate!

Helpful websites:

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)
This is a very nice piece of documentation that explains all of the different Ubuntu kernel versions.

[http://www.tuxme.com/node/544](http://www.tuxme.com/node/544)
This is the website that gave me the idea to try the 686 kernel.  This specific document also talks about installing Ubuntu on laptops.

I really wish ubuntu would detect which kernel is best for a system.  It's things like this that I think keep people away from linux.  Linux definitely requires a lot of patience sometimes but I think it's worth it in the end.  

To all of you who replied with suggestions, THANK YOU SOOOOOOOO MUCH!  You're truly a demonstration of the Ubuntu spirit.

Now to finish setting up my LAMP server! :D 

Nick

---

### Post by rgl on 2006-06-22
Using the "desktop" kernel seems to be the way to bypass the problem with the "server" kernel and VMWare.

However, the developer of Ubuntu needs to look into the problem still.  There is absolutely no reason for the server kernel to stop responding like that.

---

### Post by rcarring on 2006-06-23
In my vmware install, it picks the i386 kernel. I guess it is because I have a Celeron cpu.

---

### Post by jdkullmann on 2006-07-03
[QUOTE=nick1]Greetings,


I'm trying to install Ubuntu 6.06 LTS (Dapper Draker) as a guest OS.
I'm configuring the virtual machine as follows:

Typical > Linux > Ubuntu > bridged networking > disk size: 4GB > Allocate disk space now

I've used the 'CD check' option in Ubuntu to verify that the install CD is defect free.  The installation completes, reboots, then hangs at:
---
Booting 'Ubuntu, kernel 2.6.15-23-server'

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.15-23-server root=/dev/sda1 ro quiet splash
[Linux-bzImage, setup=0x1c00, size=0x16b75f]
initrd /boot/initrd.img-2.6.15-23-server
[Linux-initrd @ 0xf840000, 0x69f606 bytes]
savedefault
boot
Uncompressing Linux... OK, boot the kernel.
---
Then the system just hangs from there :-(

Nick[/QUOTE]

So, I had the same issue and tried acpi=off noacpi noapic lnoapic and all the other suggestions

It turns out it was because I was installing the ''server'' CD.

However, I've been doing UNIX ports for 26 years and I have to tell you, I don't understand what kind of different kernel is getting installed from the 'server' CD vs from the 'desktop' CD.

I don't want the whole UI etc which is why I chose the server CD.

I don't have the time to try to figure out why the 'server' kernel won't boot but the 'desktop' kernel will but I'd love to know why anyone would think they need to be different (except perhaps for various config items like numbers of vnode, procs, etc etc , but those should not prevent booting.)

And yes I used the i386 version of both CDs. In fact the 'server' CD installed fine on a white box x86 tower system I have here so i know the CD is ok. I just won't boot up after installing onto my HP zt3000.

---

### Post by mario_7 on 2006-07-04
I have Asus A6RP-AP002 (with Celeron M420 processor and ATI Xpress 200M chipset) notebook and I also have same problem - booting the kernel message and nothing happens... 

Tried to boot without "quiet" and "splash" parameters and now I can see that everything hangs  when this message appears: "Using hpet for high-res timesource". I really don't know why...

I can boot laptop with "acpi=off" but then can't use ethernet card to get internet connection :/ so this is not solution...

Is there any way to disable hpet? I have no such option in BIOS so maybe there is a kernel parameter? Tried "nohpet" and "hpet" but these don't work.

Hope there is solution for this problem...

---

### Post by jdkullmann on 2006-07-04
[QUOTE=mario_7]I have Asus A6RP-AP002 (with Celeron M420 processor and ATI Xpress 200M chipset) notebook and I also have same problem - booting the kernel message and nothing happens... 

Tried to boot without "quiet" and "splash" parameters and now I can see that everything hangs  when this message appears: "Using hpet for high-res timesource". I really don't know why...

I can boot laptop with "acpi=off" but then can't use ethernet card to get internet connection :/ so this is not solution...

Is there any way to disable hpet? I have no such option in BIOS so maybe there is a kernel parameter? Tried "nohpet" and "hpet" but these don't work.

Hope there is solution for this problem...[/QUOTE]

I think you'll need to install the ''desktop'' version, at least that fixed my problem of hanging right after ''uncompressing Linux"

---

### Post by mario_7 on 2006-07-05
[QUOTE=jdkullmann]I think you'll need to install the ''desktop'' version, at least that fixed my problem of hanging right after ''uncompressing Linux"[/QUOTE]
I tried... even 686 kernel doesn't work... Other linux distros don't work too :-? Maybe there is a bug in the kernel? Or this ugly HPET can't work with new "Yonah" Celerons?

---

### Post by RHCEConvert on 2006-07-06
This post was a great help.  Thanks to all of you guys on the Forums.  This is why I think Ubuntu is a great Distro! :-)

---

### Post by fedinho on 2006-08-24
Does anyone know if the Server kernel image has been fixed yet regarding this issue?

---

### Post by ElvTaylor on 2006-08-24
I been having the same issue with the installation freezing at boot.  I tried several different things.  It finally came down to me changing the VM's harddisk from SCSI to IDE and then following the instructions given by nick1 using the "Rescue a broken system option".  Now things are working perfectly.

---

### Post by mario_7 on 2006-09-02
> **fedinho said:**
> Does anyone know if the Server kernel image has been fixed yet regarding this issue?
I had same problem with Ubuntu desktop... I had to configure the newest kernel myself and now everything works fine :)

---

### Post by johnwbyrd on 2006-09-02
> **nick1 said:**
> *HUGE SIGH OF RELIEF*

Well I think I got it working in my case.  I needed to install the 686 kernel for things to work.  Below are instructions on how to install Ubuntu server 6.06 as a guest virtual machine in Windows VMware workstation 5.5.1 using the Ubuntu 686 kernel.  These instructions may also apply if you're not using VMware.


Yep, you get the Twinkie.  These instructions cause 6.06 to correctly boot on recent versions of VMware Server.  This problem Should Not Occur -- someone please patch the 386 kernel to correctly boot under VMware!

---

### Post by knorr.orange on 2007-08-08
It looks like this has all been answered as far as what to do for a workaround but I don't see anything explaining why it is required.  I have been reading about this problem with both VMWare and VirtualBox and the issue seems to be that neither of them properly support PAE.  That seems to be used in the server kernel build, but not the other ones suggested here.  Honestly I don't know what PAE is (and am too lazy to go read up on it now) but I assume it is of some value to server environments.  I hope Ubuntu server kernel builds do not change to remove it just because VMWare players are lacking features.

---

### Post by sylkanu on 2007-12-05
> **nick1 said:**
> *HUGE SIGH OF RELIEF*

Well I think I got it working in my case.  I needed to install the 686 kernel for things to work.  Below are instructions on how to install Ubuntu server 6.06 as a guest virtual machine in Windows VMware workstation 5.5.1 using the Ubuntu 686 kernel.  These instructions may also apply if you're not using VMware.

How to Install the Ubuntu 686 Kernel
====================================

1.)  boot to the Ubuntu 6.06 server install cd.  Choose 'Rescue a broken system.'

2.)  when you get to the Rescue Operations screen choose "execute a shell in /dev/discs/disco/part1", this option may read a little differently on your system.

3.)  Click continue if another screen appears.

4.)  At the prompt, type:  sudo apt-get install linux-686

5.)  You will be asked if you want to continue, type: y

6.)  The installation of the 686 kernel will begin.  It looks like an internet connection is required so the install files can be downloaded from the ubuntu website.

7.)  When the installation is done, type:  exit

8.)  You should be returned to the Rescue Operations screen.  Choose the last option: reboot the system.  Make sure you're not booting to the install cd!

9.)  Give the system a few moments to boot-up.  At last, you should be placed at the login: prompt.

10.)  Celebrate!

Helpful websites:

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)
This is a very nice piece of documentation that explains all of the different Ubuntu kernel versions.

[http://www.tuxme.com/node/544](http://www.tuxme.com/node/544)
This is the website that gave me the idea to try the 686 kernel.  This specific document also talks about installing Ubuntu on laptops.

I really wish ubuntu would detect which kernel is best for a system.  It's things like this that I think keep people away from linux.  Linux definitely requires a lot of patience sometimes but I think it's worth it in the end.  

To all of you who replied with suggestions, THANK YOU SOOOOOOOO MUCH!  You're truly a demonstration of the Ubuntu spirit.

Now to finish setting up my LAMP server! :D 

Nick
Hi nick, huge sigh of relief indeed!!! You saved me from a week of agony trying to figure out the exact problem on a dell latitude d600 being set up as a LAMP server. Your suggestion worked perfectly.  Linux looks like a dream but I enjoy the challenges it poses. I only started using it a week ago. Thanks very much I think I am hooked!!!!!!!!

---

### Post by javierfh on 2008-02-25
Hi , 

i dont know if anyone else has found this problem anymore, but today i tried to install Ubuntu server on VMWARE. 
I have a cd with ubuntu server, and even that i have tried several times with different parameters, no way, it always hangs when installing the kernel.
I could not use the options, that were suggested here, because the system was not responsive, so nothing to do...but when i was about to give up, i decided to try to download the ISO of ubuntu server and then from VMWARE select to install from ISO...and i dont know why, but that did the trick. I also have selected the harddrive to be IDE.

Hope that might help someone.

Javi

---

