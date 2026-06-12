---
title: "ub server live install USB odd issue adding raid / lvm"
date: 2024-05-10
forum: Installation &amp; Upgrades
---

### Post by alanm11 on 2024-05-10
hi all,

new to the forum, just installing 24.04 server on all new hardware and install works lovely, until... trying to specify custom raid...

The menu comes up but none of the devices are shown, just "devices:" at the top then a load of blank options for the volumes and then size at the bottom. I can select the blank items (no indication of which are selected) and the size does update so the volumes are there, just not shown. the lvm menu is the same,

Tried 2 different graphics cards, expecting this is a video issue, is it just me? Do i need to fall back to mdadm on the shell? Would be nice to use the new install

please help :)

Alan

---

### Post by MAFoElffen on 2024-05-11
> **alanm11 said:**
> hi all,

new to the forum, just installing 24.04 server on all new hardware and install works lovely, until... trying to specify custom raid...

The menu comes up but none of the devices are shown, just "devices:" at the top then a load of blank options for the volumes and then size at the bottom. I can select the blank items (no indication of which are selected) and the size does update so the volumes are there, just not shown. the lvm menu is the same,

Tried 2 different graphics cards, expecting this is a video issue, is it just me? Do i need to fall back to mdadm on the shell? Would be nice to use the new install
...
Alan
Alan,

Do you have another PC there that you can ssh into it? This is what I do. I go to the "Help" Button in the upper right > System Prompt. > Find the address > Install openssh-server > then ssh into the install.

I do this so I can document things during an install (cutting and pasting into  document). And to show people where something might be in the installer. or on the server. 

I know. A bit geeky... But I do a lot of testing. I lot of diagnostics. So if I can recreate something, that way, I can document what went wrong, under what circumstances.

---

### Post by MAFoElffen on 2024-05-11
Oh...

The reason I told you about that, was because I am a bit confused where you are in what part of the manual partitioner where you are having troubles, and what it is saying... a cut/paste of the screen, or attached photo's of the screens with your camera on your phone, would be of great hep with that.

---

### Post by alanm11 on 2024-05-11
thanks for the reply :) Yes Ill attache pics from phone later .. seems the best way of showing it at present. I cant believe im the only one with this .. :)

---

### Post by alanm11 on 2024-05-11
I wont let me attach pictures :(

---

### Post by alanm11 on 2024-05-11
The 3 are here... Any idea why this is - is it just me?? TIA :)

Alan

2 50G test volumes
[URL="https://www.imghost.net/aGs2hbnX1CZPxTs"]https://www.imghost.net/aGs2hbnX1CZPxTs

[/URL]none are shown in the MD option
[URL="https://www.imghost.net/1ZKvyl2o3WlwIaj"]https://www.imghost.net/1ZKvyl2o3WlwIaj

[/URL]you can select them invisibly and the size is shown however, so they are there, just hidden...
[https://www.imghost.net/WmOeePvwTuexHJ4](https://www.imghost.net/WmOeePvwTuexHJ4)

---

### Post by alanm11 on 2024-05-25
any thoughts on this? 

thanks
A

---

### Post by MAFoElffen on 2024-05-25
Oh dang... Sorry. I remember writing you a response, but must not have posted (???)

Yes, it seems to be a graphics issue. Even though you would think that Server is text console based, it still is in a VGA graphics mode. 

This would help if we knew the CPU and video GPU of the machine. One of the things I specialize in is supporting the Linux Graphics Layer, and in supporting Server... Without that information given by you, I'll give you generic instructions that work for most machines. 

There are several ways around that:
1.) The easiest and most fool-proof way, is to put it into text-only console mode. At the initial Grub2 boot menu, press the <E> key to get into edit mode on the boot option. <Arrow-Down> to the line that starts with the word "linux" (in that case) ... On the 24.04 Live Server ISO, the boot line will say:
```

    linux     /casper/vmlinuz ---

```
<Arrow-Right> to the end of that line and change it to
```

    linux     /casper/vmlinuz --- 3

```
Press the key combination <Cntrl><X> to boot the installer. That will put it into init 3, multi-user console text only mode... Install.

On the first boot, do the same at the Grub2 menu... Edit the /etc/default/grub file with elevated permissions...
You can either uncomment this line
```

#GRUB_TERMINAL=console

```
To look this
```

GRUB_TERMINAL=console

```
Or edit this line
```

GRUB_CMDLINE_LINUX_DEFAULT=""

```
To this
```

GRUB_CMDLINE_LINUX_DEFAULT="--- 3"

```
Effectively, they do the same thing... Then save & exit... Then do
```

sudo update-grub

```
To pick up the changes

2.) Instead of using "3", use the word "nomodeset" to use safe graphics mode.

3.) This is the option I usually use, because I like to use console theming, and work out the VGA graphics modes, and set screen resolutions of the vtty consoles... I work a lot in console. Though most of my management, I do remotely via ssh.

At the Grub2 Boot Menu, press the <C> key to get to Grub commandline... Enter the command
```

videoinfo   # <--- This command if it booted as UEFI
vbeinfo     # <-- This command if it booted as BIOS legacy

```
Write down the graphics modes that are recognized as being capatible by the BIOS, with the connected display, without any graphics drivers... Pick one and use a "video=..." boot parameter to see if it can use Kernel KMS (kernel mode setting) to clear up the graphics, by giving it what it should expect, instead of letting it guess wrong.

For example, on one of my servers, these are the graphics parts of the kernel boot parameters I use on it:
```

GRUB_CMDLINE_LINUX_DEFAULT="--- video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank consoleblank=0"

```
That way, all the hints are there, and the machine just works how I want it to. When I had all my personal servers in rack with a rack mounted console display, it some wouldn't answer it's EDID query, so I had to set what the display was capable of, and the only resolution mode it would support...

Sometimes the only way to do it with weird hardware. Other times worth it to get things going straight, and happy.

EDIT: If you can post your machines spec's for more info on what you have, I can tailor that solution to your machine.

---

### Post by alanm11 on 2024-05-26
Thanks so much for the reply MAF, and no worries. :)

I did finally get it built using my own work around / mess, built the array over SSH and a temp user, then had to add EFI partitions (not used EFI before) and had some fun getting it to complete the install (the second EFI wasn't formatted so it dumped me out but eventually fixed that and the install was quick and perfect. )  Also X etc seems fine with the 9600 so maybe it just doesnt like the VGA menu on the install.

First GPU was an nvidia MSI GTX8600S. This had some artifacts when installing so I changed for a EN9600GT ... but this still didn't show the MD or LVM menus.

Might be as both these cards are quite old now, but this is a headless mythtv build so not too worried about graphics :)

The rest of the hardware is new - Ryzen 5 4500.

happy to try anything else (non destructive!) if you think its worth fixing for these cards..

cheers

Alan

---

### Post by MAFoElffen on 2024-05-27
Since the Ryzen 5 4500 doesn't have an internal iGPU, I can see why you added a graphics card, but nVidia is not opensource, so needs "nomodeset" as a boot parameter to toggle the graphics into safemode.

What you might think about... That the nVidia MSI GTX8600S is old, and a server doesn't use a desktop Graphics layer where an nVidia driver would be loaded for that card, and that is taking up a PCIe x8 or x16 slot in your motherboard... Where for a server, storage is more important. I have 2 GTX8600's (and some GTX9600's) in my storage. They were good cards 12-14 years ago.

If you need an x16 slot open for an HBA later down the road, you could always swap out the Ryzen 5 cpu with one that series that does have an iCPU, which those do have opensource drivers, which then you could take out that PCIe GPU and use the integrated graphics.

Just an idea for growth down the road for you.

---

### Post by alanm11 on 2024-05-28
hi MAF

thanks that, very useful information :)

Initially was trying to get the on board graphics working before i saw it needed a Ryzen with GPU built in!! 

Will remember that one. Already have a PCI tuner card and I might have to add a CPI-e for more drives so that could be the only way!

cheers
Al

---

### Post by TheFu on 2024-05-28
I moved from a Ryzen 2600 + Nvidia 1030 GT config to a Ryzen 5600G.  It was a pure-CPU-only swap. I kept the same RAM and same motherboard (Asus B450 Strix).  The 5600G was $120 at the time.  40% CPU performance improvement for $120.  Then I sold the Ryzen 2600 and 16GB of RAM for $80 ... so I was out $40 for 40% performance increase. Bargain!

The onboard Ryzen 5600G iGPU is faster than the 1030GT ever was AND supports some things that the older nvidia doesn't like hardware video transcoding in the iGPU.  When HW-Transcoding is running, it doesn't impact the CPU load at all.  HW-Transcoding is about 6x real-time, while Handbrake SW-transcoding is about 1x of real-time, but make much, much better videos.

If you don't want the cost of the 5600G, the 4600G has the same iGPU inside and should be $30 cheaper.

I use LVM and on 24.04 Server, didn't see any issues setting up LVM. Now, all the desktop Ubuntu Flavors seem to have removed LVM support, except for upgrades.  I don't do non-LVM RAID anymore.  The way I do LVM-RAID is to add it after the install. That means just RAID1 is supported.  Can't so anything with striping, but using an lvchange to convert from non-RAID to RAID1 is pretty trivial.  I should say, I don't use RAID on my production servers anymore. SSDs are extremely reliable now.  I made this choice after discussing RAID with an enterprise storage buddy who sells enterprise SSDs with RAID.  He said it was a complete waste of money for almost all his clients, but that he was happy to take their money.  Of course, you and I aren't buying the enterprise SSDs that he sells so our reliability will be less. Just ensure you have good daily backups, so any storage issue is an inconvenience, not anything more.

---

