---
title: "ubuntu 12.04 -- no gui after update -- hangs during update"
date: 2014-03-02
forum: Installation &amp; Upgrades
---

### Post by ss1133xx on 2014-03-02
Hello:  I'm a fairly new (6 mo.) ubuntu user.  I have run a few updates in the time.  Yesterday an update started which I didn't initiate.  

The update did not finish and hung.  After, I was unable to boot to gui or prompt -- it just hangs during the boot process.  After trial and error (google searches) I found the Recovery Mode, and am now able to boot when using that mode.   I have to watch the boot process then click the Shift key at just the right time to get to the menu that lets me boot to Recovery Mode.  It is not a dual boot computer -- Ubuntu 12.04 only (with virtualbox).

I have a couple of questions and would appreciate suggestions:

* Can I simply instruct the computer to use the Recovery Mode version as the base version -- so I don't have to boot to recovery mode every time?  (Or can I simply go back to the condition before the update?)  (Even after a "suspend," the pc now reboots entirely, rather than waking from the suspend.)

* Any suggestions on how to diagnose the update problem that caused the update to hang?  (It may be related to the Tor browser -- the messages before it hung seems to be related to that.)  (And if I find the problem, what I might do about it now to remedy the issue?)

* After booting to recovery mode, I have lost the dual monitor function, which was working fine before.  Now the two screens are identical.  (I cannot load the "NVIDIA accelerated graphics driver (version 304) (recommended)" which I think worked fine before this update.

* Should I simply start from scratch with an entirely new install of 12.04?  If I do that, is anyone aware of step-by-step re-install instructions?  (I found step-by-step initial installation when I first installed ubuntu, but am not finding re-install instructions.)

I might be asking about too many issues here, but they are arose because of the update, so I am including them.

Would appreciate any suggestions.  Thank you.

---

### Post by Bashing-om on 2014-03-02
ss1133xx; Hi !

Might I suggest that you try and finish the failed update. Then see what the situation is ?
Best in my opinion, is boot to a terminal:
Boot the install, and as soon as the bios screen clears depress and hold the right shift key -> grub boot menu
with the latest NON-recovery kernel version highlighted press the 'e' key for edit mode -> boot parameters screen ->
arrow down and across to the terms "quiet splash" and replace them with the term "text" - without the quotes -
key combo ctl+x to continue the boot process to a Command Line Interface.
Here enter your username and then when asked, your pass word ( no response to the screen ).

Now ready for action; In this terminal enter the following commands - one at a time per line:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

```

now reboot
```

sudo shutdown -r now

```

do you now boot up normally ?

[INDENT][INDENT]hey
[INDENT][INDENT]it can happen
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-02
Bashing:  Thanks for quick reply.  Wanted to clarify your steps:

[COLOR=#000000]1.  Boot the updated install, and when the bios screen clears, depress and hold the right shift key -> to get the grub boot menu
[/COLOR]2.  Select the top listed version (th[COLOR=#000000]e latest NON-recovery kernel version)  
3.  press the 'e' key for edit mode -> boot parameters screen ->
[/COLOR]4.  [COLOR=#000000]arrow down and across to the terms "quiet splash" and replace them with the term "text" - without the quotes -[/COLOR]
[COLOR=#000000]5.  key combo ctl+x to continue the boot process to a Command Line Interface.[/COLOR]
[COLOR=#000000]6.  enter your username and pass word (no response to the screen).
[/COLOR]
7.  (assuming I can get a terminal)[COLOR=#000000] enter the following commands - one at a time per line:[/COLOR]
[COLOR=#000000]Code:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a[/COLOR]
[COLOR=#000000]8.  reboot, then enter:[/COLOR]
[COLOR=#000000]Code:
sudo shutdown -r now[/COLOR]
Do I have it right?

Thanks again.

---

### Post by grahammechanical on 2014-03-02
> [COLOR=#000000]Yesterday an update started which I didn't initiate. [/COLOR]

That should not happen. Unless we have set security updates to download and update automatically in Software Sources/Software and Updates. What was updating?

Regards.

---

### Post by Bashing-om on 2014-03-02
ss1133xx; Hey ,

See the most respected grahammechanical's posting, he does not speak with out a point.

And My advise, yes, you have it right.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe, not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-03
I'm not sure -- it had been a couple months since I ran an update, and I'm not sure how to locate "[COLOR=#000000]Software Sources/Software and Updates[/COLOR]" to see if they are set to auto-update.

---

### Post by deadflowr on 2014-03-03
> **ss1133xx said:**
> I'm not sure -- it had been a couple months since I ran an update, and I'm not sure how to locate "[COLOR=#000000]Software Sources/Software and Updates[/COLOR]" to see if they are set to auto-update.

There's the problem.
Everytime I neglect updating a system for more than a few weeks, I get a ton of updates I have to install.
The more updates, as always, the bigger the chance of something going sour.

That said, the software sources can be found in settings(it's a button at the bottom left) in the update manager, in 12.04.
or
terminal way:
```
software-properties-gtk
```

It won't do auto install/updates though.
For that you need to install something like [unattended-upgrades]("https://help.ubuntu.com/10.04/serverguide/automatic-updates.html").

But if you go the normal route and simply set it to display updates, weekly, then it'll say updates available in the dropdown where the logout,shutdown options are.
12.04 also will post the updates number on the update manager launcher in the launcher dock(left side bar/thingy).

---

### Post by ss1133xx on 2014-03-03
Bashing:  A mixed report:

I went thru each of your steps, and yes, it worked!  Wow, I thought.  The one remaining problem was that now had only one (of two) were monitors working.  So I went back and downloaded the recommended Nvidia driver (which I hoped would again recognize both screens).  After installing that driver, it told me to reboot.

Upon rebooting, it hung again during boot.  Back to square one. 

So I went thru your multiple steps a second time, but that time, no luck -- no boot.  (I never got to the last step "[COLOR=#000000]sudo shutdown -r now[/COLOR]" because it did not boot to a stage where it allowed me to enter that command.

Any more suggestions??  I was thinking great thoughts after your steps worked initially.

Going back to my initial post:

[COLOR=#000000]* Should I simply start from scratch with an entirely new install of 12.04? 
[/COLOR]
Would appreciate any additional suggestions!

---

### Post by Bashing-om on 2014-03-03
ss1133xx; Welp,

Doesn't look to be too serious of an issue - most likely a disparity with the graphics driver.

Lets see what the situation is graphics wise,
Boot to that text terminal once more, log in there.
Run terminal codes:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
of the greater interest is what driver is loaded ( if any) from this like so"
"configuration: driver=radeon latency=0" from my system where my driver is "radeon" .

We want to know what graphics card(s) you have and what driver is loaded. Make sure they are compatible or if even there is a proprietary driver even available to support the graphics.

we got to see
[INDENT][INDENT]one way or another
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-03
Bashing:

I booted into recovery mode so that I could cut and paste your commands into terminal, and here is what I got:

[FONT=arial][INDENT][FONT=georgia, serif]~$ lspci -nnk | grep -iA3 vga[/FONT][/INDENT]
[INDENT][FONT=georgia, serif][SIZE=4]
[/SIZE][/FONT][/INDENT]
[INDENT][FONT=georgia, serif]40:00.0 VGA compatible controller [0300]: NVIDIA Corporation G71GL [Quadro FX 1500] [10de:029e] (rev a1)[/FONT][/INDENT]
[INDENT][FONT=georgia, serif]	Subsystem: NVIDIA Corporation Device [10de:032c][/FONT][/INDENT]
[INDENT][FONT=georgia, serif]	Kernel modules: nouveau, nvidiafb[/FONT][/INDENT]
[FONT=georgia][INDENT]
[/FONT][/INDENT]
[/FONT]
[FONT=arial][INDENT][FONT=georgia, serif]~$ sudo lshw -C display[/FONT][/FONT][/INDENT]
[FONT=arial][INDENT]
[/FONT][/INDENT]
[FONT=arial][INDENT][FONT=georgia, serif]  *-display UNCLAIMED     [/FONT][/FONT][/INDENT]
[FONT=arial][INDENT][FONT=georgia, serif]       description: VGA compatible controller[/FONT][/FONT][/INDENT]
[FONT=arial][INDENT][FONT=georgia, serif]       product: G71GL [Quadro FX 1500][/FONT][/FONT][/INDENT]
[FONT=arial][INDENT][FONT=georgia, serif]       vendor: NVIDIA Corporation[/FONT][/FONT][/INDENT]
[FONT=arial][INDENT][FONT=georgia, serif]       physical id: 0[/FONT][/FONT][/INDENT]
[FONT=arial][INDENT][FONT=georgia, serif]       bus info: pci@0000:40:00.0[/FONT][/FONT][/INDENT]
[FONT=arial][INDENT][FONT=georgia, serif]       version: a1[/FONT][/FONT][/INDENT]
[FONT=arial][INDENT][FONT=georgia, serif]       width: 64 bits[/FONT][/FONT][/INDENT]
[FONT=arial][INDENT][FONT=georgia, serif]       clock: 33MHz[/FONT][/FONT][/INDENT]
[FONT=arial][INDENT][FONT=georgia, serif]       capabilities: pm msi pciexpress vga_controller bus_master cap_list[/FONT][/FONT][/INDENT]
[FONT=arial][INDENT][FONT=georgia, serif]       configuration: latency=0[/FONT][/FONT][/INDENT]
[INDENT][FONT=georgia, serif][FONT=arial, sans-serif]       resources: memory:f0000000-f0ffffff memory:d0000000-dfffffff memory:f1000000-f1ffffff ioport:1000(size=128)[/FONT]
[/FONT][/INDENT]

[FONT=arial, sans-serif][FONT=georgia, serif]I don't know if the [/FONT]recovery[FONT=georgia, serif] mode video driver is the same as the non-[/FONT][/FONT][FONT=georgia, serif]recovery[/FONT][FONT=arial, sans-serif][FONT=georgia] mode video driver.  I don't see a line like you quoted:  "[/FONT][/FONT][COLOR=#000000]configuration: driver=radeon latency=0" from my system where my driver is "radeon""

I will try it again using the text terminal to see if I get different information, and report back if it is different.

Thanks for sticking with me.

[/COLOR]

---

### Post by ss1133xx on 2014-03-03
Bashing:  brief update:  Info from boot text commands:  (new or different info in [COLOR=#ff0000]red[/COLOR])


[COLOR=#000000][FONT=arial][FONT=georgia]~$ lspci -nnk | grep -iA3 vga[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][FONT=georgia][SIZE=4]
[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][FONT=georgia]40:00.0 VGA compatible controller [0300]: NVIDIA Corporation G71GL [Quadro FX 1500] [10de:029e] (rev a1)[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][FONT=georgia]Subsystem: NVIDIA Corporation Device [10de:032c]
[COLOR=#ff0000]Kernel driver in use:  nvidia[/COLOR][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][FONT=georgia]Kernel modules: [COLOR=#ff0000]nvidia_173, nvidia_304, nvidia_304_updates,[/COLOR] nouveau, nvidiafb[/FONT][/FONT][/COLOR]

[COLOR=#000000][FONT=georgia]~$ sudo lshw -C display[/FONT][/COLOR]

[COLOR=#000000][FONT=arial][FONT=georgia]description: VGA compatible controller[/FONT]
[/FONT][/COLOR][COLOR=#000000][FONT=arial][FONT=georgia]product: G71GL [Quadro FX 1500][/FONT]
[/FONT][/COLOR][COLOR=#000000][FONT=arial][FONT=georgia]vendor: NVIDIA Corporation[/FONT]
[/FONT][/COLOR][COLOR=#000000][FONT=arial][FONT=georgia]physical id: 0[/FONT]
[/FONT][/COLOR][COLOR=#000000][FONT=arial][FONT=georgia]bus info: pci@0000:40:00.0[/FONT]
[/FONT][/COLOR][COLOR=#000000][FONT=arial][FONT=georgia]version: a1[/FONT]
[/FONT][/COLOR][COLOR=#000000][FONT=arial][FONT=georgia]width: 64 bits[/FONT]
[/FONT][/COLOR][COLOR=#000000][FONT=arial][FONT=georgia]clock: 33MHz[/FONT]
[/FONT][/COLOR][COLOR=#000000][FONT=arial][FONT=georgia]capabilities: pm msi pciexpress vga_controller bus_master cap_list [COLOR=#ff0000]rom[/COLOR][/FONT]
[/FONT][/COLOR][COLOR=#000000][FONT=arial][FONT=georgia]configuration:[COLOR=#ff0000] driver=nvidia[/COLOR]  latency=0[/FONT]
[/FONT][/COLOR]
Any suggestions on additional things I can try much appreciated.

---

### Post by Bashing-om on 2014-03-03
ss1133xx; Well,

According to Nvidia, that card takes The 304.xx driver. What driver are you attempting to install, and through what means  ?
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
IF we are going to go the proprietary driver route.

Maybe we can do something through recovery mode -> enable networking, boot to the GUI and see what "Addition Drivers" has to offer ?

[INDENT]ain't nothing  but a thing
[/INDENT]

---

### Post by ss1133xx on 2014-03-09
Bashing:  Just saw your reply (didn't see page 2 of chain).  I installed the 304 driver using the built-in search for drivers functionality.  

If you can walk me thru the recovery mode steps, I'd appreciate it.  ("[COLOR=#000000]recovery mode -> enable networking, boot to the GUI and see what "Addition Drivers" has to offer").  

That sounds like what I did.  I hope I can recover the install without starting from scratch.  Thanks for help.


[/COLOR]

---

### Post by Bashing-om on 2014-03-09
ss1133xx; Hey ,

Loosing track of a thread happens, glad we can pick this one back up.

this:
> 
 I installed the 304 driver using the built-in search for drivers functionality. 
 Tends to make me hope all is good in your world now. That is not the case ?

What results now when you boot up ubuntu ?

[INDENT]sometimes I wonder
[INDENT][INDENT]other times I do not know
[/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-09
No, its still not booting.  When I said that I installed the nvidia 304 driver, I did that 6 days ago, after running thru the steps you recommended:

*[COLOR=#000000]I went thru each of your steps, and yes, it worked! Wow, I thought. The one remaining problem was that now only one (of my two) monitors were working. So I went back and downloaded the recommended Nvidia [/COLOR]*[COLOR=#000000][304][/COLOR][I][COLOR=#000000] driver (which I hoped would again recognize both screens). After installing that driver, it told me to reboot.[/COLOR]

[COLOR=#000000]Upon rebooting, it hung again during boot. Back to square one. 

[/COLOR][/I][COLOR=#000000]So, I was able to boot after I ran thru the steps you gave me, but after I (re)installed the Nvidia 304 driver, the boot hangs again.
[/COLOR][I][COLOR=#000000]
[/COLOR][/I][COLOR=#000000]Any suggestions?[/COLOR][I][COLOR=#000000]
[/COLOR][/I]

---

### Post by Bashing-om on 2014-03-09
ss1133xx; Humm,

'Bout at the end of my knowledge. I will ask the obvious though have you used the nvidia-settings utility to try to configure the monitors ?

Also of interest, is that 2nd monitor appearing in the control file "/etc/X11/xorg.conf" any modifications added  to "/etc/X11/xorg.conf.d" ?

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-09
Thanks, will check Bashing.

Regarding your first question ("h[COLOR=#000000]ave you used the nvidia-settings utility to try to configure the monitors ?[/COLOR]")  No, I haven't -- maybe I was lucky, but the dual monitors had always worked seemlessly before this update, and I never had to do anything to get them to work. 

Regarding running the "[COLOR=#000000]nvidia-settings utility,[/COLOR]" would I boot to recovery mode, and then try that utility?

Regarding the second question ("[COLOR=#000000]is that 2nd monitor appearing in the control file "/etc/X11/xorg.conf" any modifications added to "/etc/X11/xorg.conf.d" ?[/COLOR]"), is there a command I can run to get that info?

---

### Post by Bashing-om on 2014-03-09
ss1133xx; Hey,

Now I am going to show my ignorance. It has been a while since I messed with the Nvidia proprietary drivers. But, I expect the "nvidia-settings utility" to be in the sub menu under applications. I would suggest start the system up with but the one operating monitor connected, when the sytem is booted connect the 2nd monitor and see if "nvidia-settings utility" finds the 2nd monitor.

Too see what is in the control file "/etc/X11/xorg.conf" fire up a text editor - the file is a text file.
```

gksudo gedit /etc/X11/xorg.conf

```
Post the file's contents back here and maybe I can flounder my way through it, to our mutual comprehension. Hopefully others will chime in with their advise;

for "/etc/X11/xorg.conf.d" as it is a directory, let's see if there is anything in it to even look at .
```

ls -la /etc/X11/xorg.conf.d

```

I really do anticipate this is but a 
[INDENT][INDENT]matter of configuration
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-10
Well, things have gotten worse.  While I trying to get Ubuntu working as described in this chain, I also created a new logical partition and installed Linux Mint, so that I would have at least one working Linux install.  LM worked initially, but now when I boot, instead of grub, I get "error: file not found" then "grub rescue>".

So I don't even boot to a place that let's me choose recovery mode.

Any ideas for me Bashing?  Ubuntu worked pretty seemlessly for me for 6 months, and now nothing (not Ubuntu, not Linux Mint) is working.

Any ideas how I can get back to a GUI?

---

### Post by Bashing-om on 2014-03-10
ss1133xx; Welp. 
We can work on it.

What do you want as your Primary Operating System ? Only one boot loader (grub) can control the booting process. We have to (re-)install grub from that primary system.

Show us now what the hard drive set up is:
```

sudo fdisk -lu

```
And tell us what partitions belong to ubuntu and which is Mint. Are ubuntu and Mint the same kernel release series ? Think'n maybe we want the newer version -if it differs - as that primary boot. Later kernels have grub version 2.0 and will know how to deal with the earlier versions of grub.

Can you boot to any grub boot menu at this time ? This operation may be tedious, but should be doable. Booting into either of the operating systems will make things much easier than working from the liveEnvironment,

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-11
Hi Bashing.  I'm generally indifferent to which (ubuntu or linux mint) is the primary OS.  I've been using ubuntu for 6 months (versus just installed LM), so I guess making it primary makes sense.
 
At the moment, I cannot boot to a grub menu.  When I boot, its says:  [COLOR=#000000] "Attemptng Bootfrom Hard Drive.  error: file not found. grub rescue>".

If you can get me to a grub menu, I can run the command ("[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo fdisk -lu[/FONT][/COLOR][COLOR=#000000]") and report back.  (I think sda6 is linux mint, but best to run the command to be sure.)
[/COLOR]
Thanks for your help!

---

### Post by Bashing-om on 2014-03-12
ss1133xx: My good morning to ya !

OK, in small steps, and not rushing into things, let's look and see what is before (re-)installing grub.

From the liveDVD of ubuntu:
Boot the liveDVD (bios set as 1st priority to the booting device) ;
As soon as the bios screen clears, depress and hold the right shift key -> language screen, escape key to accept the default ->
Boot menu -> "try ubuntu" -> desk top -> key combo ctl+alt+t -> terminal:

Post back the output of terminal command:
```

sudo fdisk -lu

```
So I have an idea of what we are working with, and have a notion of where to go from here. With the notion to (re-)install grub properly into the ubuntu install.

[INDENT][INDENT]it can happen
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-14
Hey Bashing:  I booted to liveUSB using Linux mint usb,  When I ran your command, I got this:

sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007ead8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   118290431    59144192   83  Linux
/dev/sda2       118292478   156248063    18977793    5  Extended
/dev/sda5       147863552   156248063     4192256   82  Linux swap / Solaris
/dev/sda6       118294528   147861503    14783488   83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007a4ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    31266815    15633392    c  W95 FAT32 (LBA)


Is that what you need?  Or do you need me to boot in a different way?

Thanks.

---

### Post by Bashing-om on 2014-03-14
ss1133xx; Well,

The 1st hard drive is sda and contains the operating systems (2) linux. One of which is 'buntu, the other being your Mint install.
(sdb -2nd hard drive 3TB-  I assume is a data disk - CORRECT my assumption if this is not so !)
 
Still not knowing what is where or if the liveMint DVD is compatible with ubuntu's booting. But, can not see that it will hurt to go ahead and see what results. Let's (re-)install grub to the MBR of sda ( because we now know that disk is partitioned in the legacy "msdos" format and that sda has a boot flag marking it as containing '/').

Try'n !
Boot the liveMint DVD to a terminal:
Terminal Commands:
```

sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```

Reboot ->installed operating system to grub; WHATEVER is installed to sda1 is the Primary booting system;
Select the system that is on sda1 to boot;
When booted to the desktop of the sda1 install -> terminal:
Do terminal command:
```

sudo update-grub

```

Reboot !

Now advise status. Depending on how you use your dual boot system, you may want to dis-able os-prober in that alternate system. Else it is forseeable that an update to the kernel will break grub. Then one must access the primary system once  more and (re)-install grub to that primary system. I say again, there can only be one primary grub, and you have to maintain that primacy.

I quad-boot and I personally do not disable any of the os-prober function in any of the installs. I maintain Grub on each hard drive/system enabling me to boot from bios in the event I do mess up my primary booting system and can not boot from it's grub. Just the way I think. And yeah, I do have to fix grub on occasion ! As you have both systems on the same hard drive, you do not have that amenity.

Else :
[INDENT][INDENT]we will do something different (from ubuntu liveDVD)
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-25
Hi Bashing.  (Been out of pocket a bit.)  

I entered the first set of your suggested commands in terminal as follows:

mint@mint ~ $ sudo mount /dev/sda1 /mnt
mint@mint ~ $ sudo grub-install --boot-directory=/mnt /dev/sda
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
Installation finished. No error reported.
mint@mint ~ $ sudo umount /mnt
mint@mint ~ $ 

Then I rebooted, but did not get a grub menu.  Instead, I got a message which said:  "Minimal BASH-like line editing is supported ...." followed by "grub>"

Any suggestions?  

(I asked earlier about starting over with a brand new Ubuntu install.  Any thoughts about that approach?  Also, can I contact you by email?  Or is this the preferred/only way to correspond?)

Thanks for your support!

---

### Post by Bashing-om on 2014-03-25
ss1133xx; Humm,

let's say Mint is slightly different and take a slightly different approach.
From the liveDVD
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt/work

```
where we make an explicit mount point (/mnt/work);
and let's try the target as "root" rather than "boot".

as to my contact, I rarely open up my email account, here is the better place to catch me, else on IRC @ #ubuntu on freenode.net.

And I see no present need to take that nuclear solution of (RE-)installing. Just a matter of installing grub properly. I think we can do that !

If at first we do not succeed ->
[INDENT][INDENT]try try again (skydiving is excepted !)[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-26
Hi Bashing:

The third command does not appear to have worked:

mint@mint ~ $ sudo mkdir /mnt/work
mint@mint ~ $ sudo mount /dev/sda1 /mnt/work
mint@mint ~ $ sudo grub-install --root-directory=/mnt /dev/sda
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /mnt/boot/grub (is /dev mounted?).
mint@mint ~ $ sudo umount /mnt/work
mint@mint ~ $ 

More suggestions for me?

It would be great if I can get ubuntu workig again without the nuclear option.

Thanks for your help.

---

### Post by Bashing-om on 2014-03-26
ss1133xx; Welp,

How does this now relate to the situation ?
> 
Ubuntu 12.04 only (with virtualbox).

Grub not installing in both instances is kind of weird. Maybe a mismatch of distributions/versions of the kernel ?
What operating system is installed onto the partition sda1 ?
The live medium that is being used to install grub MUST be the same version/distro as what is present on sda1.
Does sda1 still exist as the /rooted booting device ?
```

sudo fdisk -lu

```
Another thought, is that liveMedium a USB stick ? And when booting with it, is the operating system assigning sda to the USB device ?
Maybe pull a number like this to see what is  sda1:
from the liveMedium:
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work
ls -la /mnt/work/home/<your_user_name>
sudo umount /mnt/work ##when all done looking around, DO THIS ##

``` I expect that you will be able to recognize what is sda1 from the files that are present. (ubuntu, Mint, or the liveUSB ??).

Further advise pending knowing what is prevalent in the install.

It is cause and effect
[INDENT][INDENT]we are trying to learn both
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-26
Bashing:  here are the results:

---------------------------------------------------------------
mint@mint ~ $ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007ead8

   Device Boot      Start         End            Blocks            Id  System
/dev/sda1   *        2048       118290431    59144192   83  Linux
/dev/sda2       118292478   156248063    18977793    5   Extended
/dev/sda5       147863552   156248063     4192256    82  Linux swap / Solaris
/dev/sda6       118294528   147861503    14783488   83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007a4ec

 Device Boot      Start         End        Blocks      Id  System
/dev/sdc1   *          32    31266815    15633392    c  W95 FAT32 (LBA)
mint@mint ~ $ 

---------------------------------------------------------
If I am reading it correctly, it looks like the LinuxMint liveUSB is identifying sda1 as the ubuntu partition.  Sda6 is the LM partition.  Sdc1 looks like the liveUSB.  (sdb is data disk.)

Then I ran the other commands you suggested:
--------------------------------------------------------

mint@mint ~ $ sudo mkdir /mnt/work
mkdir: cannot create directory `/mnt/work': File exists
mint@mint ~ $ sudo mount /dev/sda1 /mnt/work
mint@mint ~ $ ls -la /mnt/work/home/<mint@mint>
bash: syntax error near unexpected token `newline'
-----------------------------------------------------------

Does the foregoing answer your question?  I'm pretty sure that sda1 is the ubuntu partition, and sda6 is the LM partitition.

---------------------------------------------------------
I'm not sure what you meant by this:

     How does this now relate to the situation ?
  	 		     Ubuntu 12.04 only (with virtualbox). 			 		

But I had virtualbox installed under ubuntu,
--------------------------------------------------------

Please let me know if you want/need additional info, and thanks again for your help.

---

### Post by Bashing-om on 2014-03-27
ss1133xx; welp, like this

1. This:
> 
mkdir: cannot create directory `/mnt/work': [color=blue]File exists[/color]

indicates to me that you are not booting from a liveDVD/USB
2. This:
> 
mint@mint ~ $ ls -la /mnt/work/home/[color=blue]<mint@mint>[/color]

indicates to me that you did not use the appropriate username for whatever the username you use for the system that is installed to sda1.

We need to mount sda1 OR sda6, depending on what you have for the liveDVD/USB - to match -.
Once the match is established, we can try and install grub once more ( looking like we should be working from sda6, instead of sda1, huh ?)

There is absolutely no reason that I know of - short of a corrupted file system - that prevents mounting and accessing to see what is on those partitions, to determine absolutely what operating system we are working with.

so once more try:
Boot the liveDVD/USB to a terminal;
Terminal codes
```

sudo mkdir /mnt/work ##from the liveDVD this mount point will not persist
sudo mount /dev/sda1 /mnt/work
##Now the install on sda1 is accessable, let's look:
ls -la /mnt/work/home/the_user_name_for_the_system_on_sda1
##because we are mounting sda1##

##while we are here:##
ls -la /mnt/work/boot
##for a listing of the kernels, so I know weather to use "root" or "boot" as the grub install target.##

```
example: Mine
"ls -la /mnt/work/home/sysop" where "sysop" is my user_name

I believe once we have the partitions matched to the liveDVD/USB, we can (RE-)install grub.

[INDENT]ain't nothing but a thing
[/INDENT]

---

### Post by ss1133xx on 2014-03-27
Bashing:

[COLOR=#000000]1. This:[/COLOR]
[COLOR=#000000][I]mkdir: cannot create directory `/mnt/work': [COLOR=blue]File exists[/COLOR]
[/I]
[/COLOR]
[COLOR=#000000]indicates to me that you are not booting from a liveDVD/USB
[/COLOR]
[COLOR=#ff0000]I am booting from a LinuxMint liveUSB -- its the only way I can boot at the moment.  (I can probably download ubuntu liveUSB iso again if it would be easier to boot from ubuntu liveUSB.)[/COLOR]

[COLOR=#000000]2. This:[/COLOR]
[COLOR=#000000][I]mint@mint ~ $ ls -la /mnt/work/home/[COLOR=blue]<mint@mint>[/COLOR]
[/I]
[/COLOR]
[COLOR=#000000]indicates to me that you did not use the appropriate username for whatever the username you use for the system that is installed to sda1.

[/COLOR][COLOR=#ff0000]Sorry, I thot you wanted me to use the liveUSB username.  Its been so long since I booted to ubuntu, I'll have to guess at the username.

I don't understand the following command.  It looks like the first part is an actual command ([/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo mkdir /mnt/work[/FONT][/COLOR][COLOR=#FF0000]) and the second part ([/COLOR][COLOR=#000000][FONT=Ubuntu Mono]##from the liveDVD this mount point will not persist[/FONT][/COLOR][COLOR=#FF0000]) is a comment from you.  Can you clarify?
[/COLOR]
Thanks.
[COLOR=#ff0000]
[/COLOR]sudo mkdir /mnt/work ##from the liveDVD this mount point will not persist

---

### Post by Bashing-om on 2014-03-27
ss1133xx; Outstanding !

We are making good progress.
I too learn to understand, as to the liveUSB of Mint, That too is understandable in that you have enabled persistence on the liveUSB such that "mkdir" will exist across a reboot.
We can work with what you have for the liveUSB.

In  "username"'s we are addressing access authorizations and paths, so the paths we are looking for, the files must relate.

And sorry for the confusion of mixing commands and comments. Your surmise that '#' is a comment is correct.

Let's see if this UN-confuses the issue somewhat, lets mount sda6 - as you think that is the Mint install, and see what results/
```

sudo mkdir /mnt/mint
sudo mount /dev/sda6 /mnt/mint
ls -la /mnt/mint/home/the_user_name_for_the_system_on_sda6

##while we are here:##
ls -la /mnt/mint/boot

```

When done looking around, ReMeMbeR that file system MUST be (UN)mounted !
```

sudo umount /mnt/mint

```
With just a bit of poken' about we can know the user_name on sda1, if and when the need to know should again arise.

All we are trying to do presently is match the liveUSB to the install's partition. And, carry on from there.

We will get ya booting, and then decide on what you want for the Primary operating system. Only one can control the booting process.

Still, this 
[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-27
Bashing:

Re:  "in that you have enabled persistence on the liveUSB such that "mkdir" will exist across a reboot."

The liveUSB does seem to persist --- I'm not sure why.  If I caused it to persist, it was accidental.

I tried the following commands:

   mint@mint ~ $ sudo mkdir /mnt/mint
   mint@mint ~ $ sudo mount /dev/sda6 /mnt/mint
   mint@mint ~ $ ls -la /mnt/mint/home/[***user name on sda6 ***]
   ls: cannot access /mnt/mint/home/[*** user name on sda6 ****]: No such file or directory
   mint@mint ~ $ ls -la /mnt/mint/boot
   ls: cannot access /mnt/mint/boot: No such file or directory

I guessed the user name on sda6, but no luck.  Thinking back, I never really got LinuxMint to work -- so I'm not sure if I established a username.

Suggestions?  (Should I try to reinstall LM on sda6 from the liveUSB?)

Thanks as always.

---

### Post by Bashing-om on 2014-03-27
ss1133xx; Well, Well,

Nah, let's not go compounding our problem at this time.
try:
```

sudo mount /dev/sda6 /mnt/mint
ls -la /mnt/mint/home
sudo umount /mnt/mint

```
and that will give us the username(s) within /home on sda6.

We can do the same, mounting "work" to the "sda1" partition.

Meanwhile,
[INDENT][INDENT]back at the ranch
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-29
Bashing:

Here are the commands:
----------------------------------------------------------------------------
mint@mint ~ $ sudo mount /dev/sda6 /mnt/mint
mint@mint ~ $ ls -la /mnt/mint/home
ls: cannot access /mnt/mint/home: No such file or directory
mint@mint ~ $ sudo umount /mnt/mint
mint@mint ~ $ 
--------------------------------------------------------------------------
I guess I didn't set up an /home partition.

You wrote:  "We can do the same, mounting "work" to the "sda1" partition."

Can you direct me on how to do that?

Thanks.

---

### Post by steeldriver on 2014-03-29
> **ss1133xx said:**
> Bashing:

Here are the commands:
----------------------------------------------------------------------------
[COLOR=#ff0000]mint@mint ~ $ sudo mount /dev/sda6 /mnt/mint
mint@mint ~ $ ls -la /mnt/mint/home
ls: cannot access /mnt/mint/home: No such file or directory[/COLOR]
mint@mint ~ $ sudo umount /mnt/mint
mint@mint ~ $ 
--------------------------------------------------------------------------
[COLOR=#ff0000] I guess I didn't set up an /home partition.[/COLOR]

You wrote:  "We can do the same, mounting "work" to the "sda1" partition."

Can you direct me on how to do that?

Thanks.

Wouldn't it indicate that you probably **did** set up a /home partition? i.e. that the /home **directory** is somewhere else (not located on the /dev/sda6 **partition**)

Now back to your regularly scheduled guru...

EDIT: OK just trawled back through the thread and found your fdisk output, so it looks more likely that /dev/sda6 **is** a /home partition - but that means that it would be mounted **at** /home in which case your ls command would be looking for /home/home (which won't exist) - try plain 

```
ls -la /mnt/mint
```

---

### Post by Bashing-om on 2014-03-29
@ steeldriver; Hey, hey; Always pleasant to see you.

@ ss1133xx: OK, Let's worry with this a bit more, We are going to back up one level and have a go.
Boot the liveUSB of mint -> terminal:
```

sudo mkdir /mnt/mint ##if the mount point already exist, good##
sudo mount /dev/sda6 /mnt/mint ##sda6 because "fdisk" says it is there##
ls -la /mnt/mint ##top level, let's see what results

```
All done - must UNmount what we manually mounted, let's not have corrupted file system adding to our problem !
```

sudo umount /mnt/mint

```

Recall, all we are trying to do is match the liveUSB to what is installed onto the hard drive, now there do exist a bit of concern in that you have advised that you have not been able to get the Mint install to work .. humm, We may want to at some point make up a liveUSB ( I prefer DVD myself  ) of what ever distribution and VERSION that is installed onto sda1. we may be getting ready to cross that bridge.

As we continue in our learning process:
We will keep prodding and poking
[INDENT][INDENT]'till we know
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-29
Hi Bashing:  Here are the most recent results:

--------------------------------------------------------------------------
mint@mint ~ $ sudo mkdir /mnt/mint
mkdir: cannot create directory `/mnt/mint': File exists
mint@mint ~ $ sudo mount /dev/sda6 /mnt/mint
mint@mint ~ $ ls -la /mnt/mint
total 24
drwxr-xr-x 3 root root  4096 Mar  9 22:13 .
drwxr-xr-x 1 root root  4096 Mar 27 19:46 ..
drwx------ 2 root root 16384 Mar  9 22:13 lost+found
mint@mint ~ $ sudo umount /mnt/mint
mint@mint ~ $ 
------------------------------------------------------------------------
(I'm not sure what it means.)  Next steps?  
Thanks.

---

### Post by Bashing-om on 2014-03-29
ss1133xx; sheeshh !

That output do explain a lot - NO /home directory = a bad install !So much for using that install for anything.

So, Presently all I see in one recourse to eventually install grub.
But, for now:
Let's take a look and see what we can see on sda1.
```

sudo mkdir /mnt/work ##once more if the mount point already exist, OK##
sudo mount /dev/sda1 /mnt/work
ls -la /mnt/work
ls -la /mnt/work/boot
##when done UNmount##
sudo umount /mnt/work

```

With the output of "/boot" known, I have another idea we can try.

ELSE, looking to have to download the .iso file you think may be installed onto sda1, and burn a new image.

We can still do this because ->
[INDENT][INDENT]there is still a solution
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-29
Bashing:  Here there are:

---------------------------------------------------------------------------------------------------
mint@mint ~ $ sudo mkdir /mnt/work
mkdir: cannot create directory `/mnt/work': File exists
mint@mint ~ $ sudo mount /dev/sda1 /mnt/work
mint@mint ~ $ ls -la /mnt/work
total 128
drwxr-xr-x  25 root root  4096 Mar 25 19:22 .
drwxr-xr-x   1 root root  4096 Mar 27 19:46 ..
drwxr-xr-x   2 root root  4096 Jan  9 19:55 bin
drwxr-xr-x   4 root root  4096 Mar  4 00:24 boot
drwxr-xr-x   2 root root  4096 Sep 14  2013 cdrom
drwxr-xr-x   4 root root  4096 Aug 20  2013 dev
drwxr-xr-x 145 root root 12288 Mar  9 15:44 etc
drwxr-xr-x   3 root root 12288 Mar 25 19:22 grub
drwxr-xr-x   3 root root  4096 Sep 14  2013 home
lrwxrwxrwx   1 root root    33 Mar  1 23:35 initrd.img -> /boot/initrd.img-3.8.0-36-generic
lrwxrwxrwx   1 root root    37 Mar  1 23:33 initrd.img.old -> /boot/initrd.img-3.2.0-59-generic-pae
drwxr-xr-x  25 root root  4096 Mar  1 23:30 lib
drwx------   2 root root 16384 Sep 14  2013 lost+found
drwxr-xr-x   4 root root  4096 Mar  4 00:41 media
drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt
drwxr-xr-x  10 root root  4096 Dec 14 20:01 opt
drwxr-xr-x   2 root root  4096 Apr 19  2012 proc
drwx------  13 root root  4096 Sep 22  2013 root
drwxr-xr-x   2 root root  4096 Sep 29 12:44 .rpmdb
drwxr-xr-x   9 root root  4096 Sep 14  2013 run
drwxr-xr-x   2 root root  4096 Mar  1 23:26 sbin
drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux
drwxr-xr-x   2 root root  4096 Aug 20  2013 srv
drwxr-xr-x   2 root root  4096 Apr 14  2012 sys
drwxrwxrwt   7 root root  4096 Mar  9 15:41 tmp
drwxr-xr-x  11 root root  4096 Sep 14  2013 usr
drwxr-xr-x  13 root root  4096 Mar  9 15:44 var
lrwxrwxrwx   1 root root    29 Mar  1 23:35 vmlinuz -> boot/vmlinuz-3.8.0-36-generic
lrwxrwxrwx   1 root root    33 Mar  1 23:33 vmlinuz.old -> boot/vmlinuz-3.2.0-59-generic-pae
mint@mint ~ $ ls -la /mnt/work/boot
total 309500
drwxr-xr-x  4 root root     4096 Mar  4 00:24 .
drwxr-xr-x 25 root root     4096 Mar 25 19:22 ..
-rw-r--r--  1 root root   804726 Aug 22  2013 abi-3.2.0-53-generic-pae
-rw-r--r--  1 root root   804726 Sep 10  2013 abi-3.2.0-54-generic-pae
-rw-r--r--  1 root root   804873 Oct  2 08:04 abi-3.2.0-55-generic-pae
-rw-r--r--  1 root root   804873 Oct 23 11:54 abi-3.2.0-56-generic-pae
-rw-r--r--  1 root root   804938 Dec  3 11:02 abi-3.2.0-58-generic-pae
-rw-r--r--  1 root root   804938 Jan  7 16:09 abi-3.2.0-59-generic-pae
-rw-r--r--  1 root root   926372 Aug 14  2013 abi-3.8.0-29-generic
-rw-r--r--  1 root root   926429 Aug 23  2013 abi-3.8.0-30-generic
-rw-r--r--  1 root root   926513 Sep 11  2013 abi-3.8.0-31-generic
-rw-r--r--  1 root root   926513 Oct  2 09:46 abi-3.8.0-32-generic
-rw-r--r--  1 root root   926578 Oct 24 09:55 abi-3.8.0-33-generic
-rw-r--r--  1 root root   926578 Jan 30 09:50 abi-3.8.0-35-generic
-rw-r--r--  1 root root   926578 Feb  3 14:21 abi-3.8.0-36-generic
-rw-r--r--  1 root root   147576 Aug 22  2013 config-3.2.0-53-generic-pae
-rw-r--r--  1 root root   147576 Sep 10  2013 config-3.2.0-54-generic-pae
-rw-r--r--  1 root root   147576 Oct  2 08:04 config-3.2.0-55-generic-pae
-rw-r--r--  1 root root   147576 Oct 23 11:54 config-3.2.0-56-generic-pae
-rw-r--r--  1 root root   147576 Dec  3 11:02 config-3.2.0-58-generic-pae
-rw-r--r--  1 root root   147576 Jan  7 16:09 config-3.2.0-59-generic-pae
-rw-r--r--  1 root root   160917 Aug 14  2013 config-3.8.0-29-generic
-rw-r--r--  1 root root   160917 Aug 23  2013 config-3.8.0-30-generic
-rw-r--r--  1 root root   160917 Sep 11  2013 config-3.8.0-31-generic
-rw-r--r--  1 root root   160918 Oct  2 09:46 config-3.8.0-32-generic
-rw-r--r--  1 root root   160918 Oct 24 09:55 config-3.8.0-33-generic
-rw-r--r--  1 root root   160907 Jan 30 09:50 config-3.8.0-35-generic
-rw-r--r--  1 root root   160907 Feb  3 14:21 config-3.8.0-36-generic
drwxr-xr-x  3 root root     4096 Mar  4 00:24 extlinux
drwxr-xr-x  3 root root    12288 Mar  2 02:29 grub
-rw-r--r--  1 root root 19800811 Sep 14  2013 initrd.img-3.2.0-53-generic-pae
-rw-r--r--  1 root root 14201385 Sep 29 12:45 initrd.img-3.2.0-54-generic-pae
-rw-r--r--  1 root root 14201861 Nov  6 01:18 initrd.img-3.2.0-55-generic-pae
-rw-r--r--  1 root root 14201849 Jan  4 11:09 initrd.img-3.2.0-56-generic-pae
-rw-r--r--  1 root root 14201207 Jan  4 11:11 initrd.img-3.2.0-58-generic-pae
-rw-r--r--  1 root root 14201328 Mar  1 23:34 initrd.img-3.2.0-59-generic-pae
-rw-r--r--  1 root root 15859951 Sep 14  2013 initrd.img-3.8.0-29-generic
-rw-r--r--  1 root root 16026229 Sep 14  2013 initrd.img-3.8.0-30-generic
-rw-r--r--  1 root root 16027584 Oct 29 23:25 initrd.img-3.8.0-31-generic
-rw-r--r--  1 root root 16030248 Nov  6 01:22 initrd.img-3.8.0-32-generic
-rw-r--r--  1 root root 16029103 Mar  2 14:40 initrd.img-3.8.0-33-generic
-rw-r--r--  1 root root 16082062 Mar  1 23:39 initrd.img-3.8.0-35-generic
-rw-r--r--  1 root root 16084046 Mar  2 22:10 initrd.img-3.8.0-36-generic
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2321335 Aug 22  2013 System.map-3.2.0-53-generic-pae
-rw-------  1 root root  2321477 Sep 10  2013 System.map-3.2.0-54-generic-pae
-rw-------  1 root root  2321891 Oct  2 08:04 System.map-3.2.0-55-generic-pae
-rw-------  1 root root  2321891 Oct 23 11:54 System.map-3.2.0-56-generic-pae
-rw-------  1 root root  2321986 Dec  3 11:02 System.map-3.2.0-58-generic-pae
-rw-------  1 root root  2322099 Jan  7 16:09 System.map-3.2.0-59-generic-pae
-rw-------  1 root root  2549142 Aug 14  2013 System.map-3.8.0-29-generic
-rw-------  1 root root  2549368 Aug 23  2013 System.map-3.8.0-30-generic
-rw-------  1 root root  2549215 Sep 11  2013 System.map-3.8.0-31-generic
-rw-------  1 root root  2549251 Oct  2 09:46 System.map-3.8.0-32-generic
-rw-------  1 root root  2549418 Oct 24 09:55 System.map-3.8.0-33-generic
-rw-------  1 root root  2552743 Jan 30 09:50 System.map-3.8.0-35-generic
-rw-------  1 root root  2552792 Feb  3 14:21 System.map-3.8.0-36-generic
-rw-------  1 root root  5028480 Aug 22  2013 vmlinuz-3.2.0-53-generic-pae
-rw-------  1 root root  5028896 Sep 10  2013 vmlinuz-3.2.0-54-generic-pae
-rw-------  1 root root  5030048 Oct  2 08:04 vmlinuz-3.2.0-55-generic-pae
-rw-------  1 root root  5030080 Oct 23 11:54 vmlinuz-3.2.0-56-generic-pae
-rw-------  1 root root  5031904 Dec  3 11:02 vmlinuz-3.2.0-58-generic-pae
-rw-------  1 root root  5033760 Jan  7 16:09 vmlinuz-3.2.0-59-generic-pae
-rw-r--r--  1 root root  5438944 Aug 20  2013 vmlinuz-3.8.0-29-generic
-rw-------  1 root root  5438816 Aug 23  2013 vmlinuz-3.8.0-30-generic
-rw-------  1 root root  5438528 Sep 11  2013 vmlinuz-3.8.0-31-generic
-rw-------  1 root root  5439456 Oct  2 09:46 vmlinuz-3.8.0-32-generic
-rw-------  1 root root  5441888 Oct 24 09:55 vmlinuz-3.8.0-33-generic
-rw-------  1 root root  5469504 Jan 30 09:50 vmlinuz-3.8.0-35-generic
-rw-------  1 root root  5469664 Feb  3 14:21 vmlinuz-3.8.0-36-generic
mint@mint ~ $ sudo umount /mnt/work
mint@mint ~ $ 

-------------------------------------------------------------------------------------------------------------------
I don't think I have an /home partition on sda1 either.  (If you have a minute, I'd appreciate your thoughts on why installing without a /home partition is a bad install.  (Why doesn't ubuntu install /home automatically?  Can one be installed after the original install?

Regarding:  "ELSE, looking to have to download the .iso file you think may be installed onto sda1, and burn a new image."

I assume the ubuntu iso has to be burned on a different USB than the LinuxMint iso.  Is that right?  Also, hopefully it will no tbe hard to find the original iso -- I used version 
12.04.

Thanks much.

---

### Post by Bashing-om on 2014-03-30
ss1133xx;  Making progress once more;


While it is on my mind: please use code tags for your posted outputs, makes things much more readable, and maintains the formatting.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


OK, We know now that sda1 is the ubuntu install of release 12.04. "-rw-r--r-- 1 root root 804726 Aug 22 2013 abi-3.2.0-53-generic-pae" tells us so.
Let's get the username for that install:
And it does have a /home directory !
> 
drwxr-xr-x 3 root root 4096 Sep 14 2013 home

```

sudo mount /dev/sda1 /mnt/work
ls -la /mnt/work/home
##when done UNmount##
sudo umount /mnt/work

```

If you can find the install disk of 12.04 we are in business.
Here is the link to download a new .iso file:
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Verify the .iso file's integrity once it is on your system:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Burn at a slow speed:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And lastly, in the liveUSB, boot to the boot options screen and choose:
"check disk for defects".
Now we are back to the nitty gritty !
Then from that 12.04 ubuntu liveCD/USB, do:
```

sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```

REboot into the install, grub should now appear (if Mint is not picked up, will have to hold the right shift key as soon as the bios screen clears).
And that I expect will have you bootable once more.

As to fixing Mint, I highly doubt it.  I have no experience with Mint, but I would expect it to also make a default /home directory in root's partition.
As it is not there, May i suggest - unless others come along with a better suggestion - that you wipe the Mint install with GParted.

Once we have ubuntu 12.04 straightened out, if you want, then (RE-)install Mint.

Be aware, I am presently experiencing boot problems, and to this time I have not isolated the cause, so if I do not get back to you in a timely manner -> I have not resolved my booting problem !

Things are looking
[INDENT][INDENT]brighter
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-30
Bashing:

```

mint@mint ~ $ sudo mount /dev/sda1 /mnt/work
mint@mint ~ $ ls -la /mnt/work/home
total 12
drwxr-xr-x  3 root root 4096 Sep 14  2013 .
drwxr-xr-x 25 root root 4096 Mar 25 19:22 ..
drwxr-xr-x 59 1000 1000 4096 Mar  4 00:48 ##user name on sda1##
mint@mint ~ $ sudo umount /mnt/work
mint@mint ~ $ 

```

I found the original USB I used to install ubuntu.  I will try to boot to it, run ***md5sum, ***"check disk for defects", and the other commands, and report back.

Thanks.

---

### Post by ss1133xx on 2014-03-30
Bashing:

When I checked the ubuntu liveUSB for defects, it found none:

[COLOR=#000000]```
[/COLOR]
check finished: no errors found
[COLOR=#000000]
```[/COLOR]


Then after I rebooted, but did not get a grub menu. Instead, I got the same message I got a few days ago: 

```

Minimal BASH-like line editing is supported.  For the first word ....

grub>

```

Any suggestions?

Hope you have been able to resolve your own boot problem!

Thanks much.

P.S.  Fixing Mint is not an issue -- I only installed it to try to get a working OS.  Ubuntu had worked great for me until the update a few weeks ago.

---

### Post by Bashing-om on 2014-03-30
ss1133xx; Hey,

Here we go:

From that liveUSB of ubunru -> terminal commands:
```

sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```
Will run for a few tics, and hope the result is installed with no errors.

Back out, shut your system down ( just because here lately I have had problems when I only reboot !).
Now from a cold start boot the install on the hard drive, to a terminal:
Terminal commnd:
```

sudo update-grub

```
reboot and let's see what results. It is concievable that the hosed up install of Mint might effect ubuntu's grub. If Mint is removed from the system, at that time will also need to "update-grub" once more to keep it in line.

---------------------

My booting problems, only getting worse, I finally got one of my installs to boot, but the others are so hosed up that any attempt to boot them gives me a kernel panic !
Now I must do what I have advised you to do, Download and burn the appropriate .iso file and burn baby burn. And from the liveDVD (RE-)install grub. As I have not got one for the hosed up grubs -  Maybe I will install 14.04 early !

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-03-31
Bashing:  The first part worked fine:

```


ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo umount /mnt

```

But after the cold reboot, the results look wrong:

```

[COLOR=#000080]ubuntu@ubuntu:~$ sudo update grub
sudo: update: command not found
[/COLOR]
```

(I cold booted to the liveUSB -- I assumed that's what you meanr, since I can't boot to ubuntu (yet.))

More ideas??  Thanks.

---

### Post by Bashing-om on 2014-03-31
ss1133xx; Haste - on my part - makes waste !

Correct my typo to be terminal command:
```

sudo update-grub

```
Run this command from the booted up install on the hard drive ( change boot priority ).
> 
since I can't boot to ubuntu (yet.))

That is what we are working on - to boot the install of ubuntu - at this point should boot !

I fix my prior posting error as I had left out that silly little hyphen.

All good now ?

---

### Post by ss1133xx on 2014-03-31
Hay Bashing:

Here is what I did:  I booted to liveUSB (my only option at the moment) and ran the command, to wit:

```

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

```

I don't follow this:

      "Run this command from the booted up install on the hard drive ( change boot priority )."

I'm not sure how I can run that command "on the hard drive" since I'm booted to liveUSB.  I'm also not sure how to "change boot priority."  Maybe I should understand that talk by now --  if so, apologies.

More ideas?

Did you resolve you own boot issue?

Thanks.

---

### Post by Bashing-om on 2014-03-31
ss1133xx; Sure.

Recall that the point is to get the install of ubuntu functional. When you installed Mint the bootloader "grub" got hammered. So what is needed is to (RE-)install grub onto the hard drive.
> 
Here is what I did: I booted to liveUSB (my only option at the moment) and ran the command, to wit:

NO !. I say again we want to boot the install, boot the hard drive !

Grub install:
That is done - in this instance - by booting the liveUSB and "installing" grub to the hard drive (sda) Master Boot Record (grub-install --boot-directory).
So now grub has been installed and the ubuntu install should now boot up. Now tell Bios where to expect the boot code to be by changing the boot priority from that of the usb to the hard drive. Continue the boot from bios, and I hope and expect you to boot up ubuntu on the hard drive.
Look in your bios settings and reset the boot order to the hard drive as the first priority.

Once you have booted up from the hard drive, now run that grub-update command:
```

sudo update-grub

```
Now, I hope hope hope that the "update-grub" command does not pick up that bad Mint install and hose things up again.
Let's see:
Since the "update-grub" commnad did complete successfully, RE-boot. and let's see what happens!


Take care in your selection and DO NOT boot Mint.

------------------------------
My own booting issues: 
The more I mess with it the worse I make things. I tried to change root today, and welp, I do not run anything close to standard installation, and in my attempts to get the package manager functioning ( was going to download grub's files, from within the install ) I "may" have trashed the operating system when I removed grub and tried to (re-)install. I really miss my working system ! .. I may toss in the towel on this one and do a clean install. I have the core packages onhand for 14.04 and I am thinking now is a good time to build 14.04. Now See if I had of had a liveDVD of 13.10 I would not be in this situation. I bet when I get 14.04 built I will burn a liveDVD for 14.04.
-------------------

None of us were born knowing  ->
[INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT]

This is one of those "It won't happen to me" times.

---

### Post by ss1133xx on 2014-04-01
Bashing:

It seems like we are close, but now circling back to earlier notes.  

I tried to follow your commands, but I can't boot to the harddrive.  When I try to boot to the harddrive, rather the the live USB,, I get the same message I have reported twice before:

[COLOR=#000000]```

[/COLOR]GNU GRUB version 1.99-21ubuntu3.10
Minimal BASH-like line editing is supported.  For the first word ....


grub>
[COLOR=#000000]
```[/COLOR]

Well, I thot, maybe I'm supposed to enter "sudo update-grub" after the grub>, so:

```

GNU GRUB version 1.99-21ubuntu3.10
Minimal BASH-like line editing is supported.  For the first word ....


grub>


grub>  sudo update-grub
error:  unknown command 'sudo'
grub> update-grub
error:  unknown command 'update'

```


Maybe I'm hopeless, but I'm not getting it how to boot to the harddrive (to run the command: "sudo update-grub") when I can't boot to the harddrive.

Suggestions?

Thanks.

---

### Post by Bashing-om on 2014-04-01
ss1133xx; Well well,

That is a disappointment !
As you are able to boot to grub, and not beyond, in the install indicates that grub's secondary files are corrupt  (say maybe /boot/grub/grub.cfg).

At this point we can try one other thing and try to salvage the installation of ubuntu. We can "change root" into the install from the liveUSB, remove/purge grub and reinstall grub. This procedure is not for the un-initiated as it involves making on-the-spot decisions and knowing how to manipulate the pop up menus. It can be done, if you are willing to undertake the learning experience. There is the risk of totally hose-ing up the operating system to a non-fixable state, though in your case, if you are slow and careful, - successfully complete each step in the process - that risk is minimal  . As you have never been in this situation before, will take some to get you through it with no little anxiety and frustration on your part. It is a steep step on that learning curve.

To be honest, IF I Really really knew my stuff, we could examine the file "/boot/grub/grub.cfg" and perhaps get an idea of what is not going on. I am not to that point in my own learning curve. ->
Maybe post that file to this thread, and those with that knowledge/experience will advise us ?
Mount sda1 from the liveUSB; And:
```

sudo mount /dev/sda1 /mnt/work
cat /mnt/work/boot/grub/grub.cfg
sudo umount /mnt/work

```
OR You want to go for the "change root" now and see what results  ?


EDIT: 'nother thought !
More learning, you can, from that grub prompt, direct what and where to boot, The instructions to do so are in this comprehensive guide-to-grub by drs305:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
That may or may not prove fruitful. Depends on if the operating system can find the kernel images. -as in my present circumstance, not -
[INDENT]in for a penny
[INDENT][INDENT]in for a pound
[INDENT][INDENT]don't see that we can hurt to try
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-01
Bashing:  It sounds like there might be three options:

Option 1:   Mount sda1 from the liveUSB and:


     Code:
     sudo mount /dev/sda1 /mnt/work
     cat /mnt/work/boot/grub/grub.cfg
     sudo umount /mnt/work

     [what happens after that?  Reboot and see if I get to a grub menu?]


Option 2:  "go for the "change root" now and see what results?"


Option 3:  from that grub prompt, direct what and where to boot. The instructions to do so are in this comprehensive guide-to-grub by drs305:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

As to what option to try next,  I'd appreciate your suggestion, with the goal to get ubuntu working asap.

What do you think you work best, and with the least effort?  Thanks.

---

### Post by Bashing-om on 2014-04-01
ss1133xx; 
option #1 is not a real option to repair grub, but a means to look and see what there might be to repair. All that is taking place is looking at the primary file that the system parses to boot the system; built up from several other control files.
Of the two remaining options, this may work to get into the install - rather generic - but possible,
Boot the install to that grub prompt;
There enter these commands:
```

set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
insmod linux
linux (hd0,1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,1)/initrd.img
boot

```
Like I say this is real generic, - all we are doing is telling the system where the boot files are located, in a language that grub understands - post back if the system squawks, giving an indication of specific needs.
Once we are able to boot into the system, we still gave to fix grub. But, let's get booted up before we cross that bridge.

[INDENT][INDENT]maybe yes
[INDENT][INDENT]more probable, not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

I am done for, for this session - will continue this at a later time.

---

### Post by Bashing-om on 2014-04-02
ss1133xx;  Hey ;

I am back, awaiting the results of the grub commands.

[INDENT]where there is life
[INDENT][INDENT]there is hope
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-04-05
ss1133xx; Hey ;

Where are you ? and What now is the status ?

[INDENT][INDENT]in the process
[INDENT][INDENT][INDENT]of learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-05
Hi Bashing.  Sorry about delay.  I enter those commands:

---------------------------------------
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
insmod linux
linux (hd0,1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,1)/initrd.img
boot
---------------------------------------

The screen flashed an rolled a couple times, and is now stopped.  The last line reads:

* Stopping userspace bootsplash          [ok]

All the displayed lines show an "[ok]" except this one:

* Starting load fallback graphics devices    [fail]

Not sure how useful this is in diagnosing the current issue.  But any ideas for next steps?

Thanks.

P.s.  Maybe time for a reinstall (like you were contemplating for your system): " [COLOR=#000000]I may toss in the towel on this one and do a clean install.[/COLOR]""

---

### Post by Bashing-om on 2014-04-05
ss1133xx; Euurraaah....

Not the output I had anticipated.

Let's back up a bit and do some regrouping.
At the grub > prompt ; what results ?
Grub terminal commands:
```

##to get an idea of how far along in the boot process grub is ##
set 
ls (hd0,msdos1)/boot/grub/grub.cfg ## not a good output ? do ->
ls (hd0,msdos1)/boot ##no ? ->
ls (hd0,msdos1)
##want to know now if the system has found the kernel ##
ls (hd0,msdos1)/vmlinuz
##has the system found the startup file ? ##
ls (hd0,msdos1)/
ls (hd0,msdos1)/initrd

```

In theory if root, prefix, linux, and initrd are correct and set, It is supposed to be able to boot !
//
MY situation: I can now boot my working install - NO damage is done to my operating system ! - And I have isolated the fault, just do not know what will be the final fix to allow me to boot any of my installed systems from the controlling grub menu - real real weird as nothing conforms to accepted troubleshooting procedures -- and I think when my original install of the alternate OS as version upgraded went hog wild and some crazy stuff happened  .. ( How that install wound up on sda7 is beyond my understanding, 90% certainty was not installed there originally )..and maybe now /etc/grub.d/10_linux is all wrong, and in updating my working system's grub it picks up that bad bad result for the alternate install. I continue to play with it in the interest of what I can learn.
//

Your situation with a bad Mint install may be similar. There are a number of things we can look at and try and see what is not going on. But, my mind works on one thing at a time, this post will keep us occupied till we know more,

My news is good news. hopefully 
[INDENT][INDENT]soon, yours will be too
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-05
Ok, here are the results of your latest commands:  (I can't cut and paste, so its slow going.)

grub>  ls (hd0,msdos1)/boot/grub/grub.cfg
grub.cfg

ls (hd0,msdos1)/boot 
[screen rolled and lot of text appeared -- looks like the grub menu, but with word wrap]


ls (hd0,msdos1)
[##want to know now if the system has found the kernel ##]
[I don't see a kernel number, but prior command produced a grub-like list]



ls (hd0,msdos1)/vmlinuz
##has the system found the startup file ? ##
vmlinuz



ls (hd0,msdos1)/
[three lines of text starting with "lost and found"]



ls (hd0,msdos1)/initrd
error: file not found

Hope that answered your questions.  If not, let me know and I'll try again.

Thanks.

PS.  Glad to hear you are back in business.  Its too bad I tried to install Linux Mint -- I was trying to get a working OS, and thought LM might do the trick, but it seems to have made things worse.

---

### Post by Bashing-om on 2014-04-05
ss1133xx; Well, well,

So far so good, everything thus far is there and in place.

I made a boo-boo on my last.

What returns form
Grub terminal command:
```

ls (hd0,msdos1)/initrd.img
##and## ##for curiosities sake:
search -f /sbin/init

```

Now IF the file initrd.img and /sbin/init are found, let's try and boot !
Grub terminal commands:
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1
initrd (hd0,msdos1)/initrd.img
boot

```

[INDENT]hey, it could happen
[/INDENT]

---

### Post by ss1133xx on 2014-04-05
Bashing:  Here you go:

ls (hd0,msdos1)/intrd.img ## (typo?  changed to:
ls (hd0,msdos1)/in**_i_**trd.img
in**_i_**trd.img



##and## ##for curiosities sake:
search -f /sbin/init
hd0,msdos1

linux (hd0,msdos1)/vmlinuz root=/dev/sda1
grub>



initrd (hd0,msdos1)/initrd.img
grub>



boot
[rolled past a couplke screens of text, including last line, I think was "[COLOR=#000000]* Stopping userspace bootsplash [ok][/COLOR]"

Then hung -- blinking cursor on otherwise blank screen.

More ideas?   Thanks.

---

### Post by Bashing-om on 2014-04-05
ss1133xx; Yeah, typo

You done good.

Should have booted ! ,, wonder what it booted too ?
Let's try this one:
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```
Maybe Read Only and let initrd take care of (re)mounting the file system (?).

Try once more and boot from grub .. if/when ya get to that blank screen ->
What results from key combo ctl+alt+f1 ?

[INDENT][INDENT]making progress.
[INDENT][INDENT]one of these times -> pow
[INDENT][INDENT]it is going to boot !
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-05
Ok, here they are:

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
grub>



initrd (hd0,msdos1)/initrd.img
grub>


boot
[blinking cursor on otherwise blank screen]


ctl+alt+f1
[no result]
[shutdown and reboot]

reboots to grub>

More thoughts?

---

### Post by Bashing-om on 2014-04-05
ss1133xx; Humm,

Thinkn';

You are booting to something, we just do not know what/where. Maybe it is a graphics thing ?
let's see what is set for the the gfx_mode:
Grub terminal commands once more:
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
set

``` what do you see in the respect to gfx_mode ?

Ok finish the boot attempt.
```

boot

```

As you are booting to something somewhere some how, rather than taking a chance on corrupting the file system with a dirty shut down, let's back out gracefully:
A hard stretch for small hands and short fingers but ->
key combo ctl+alt+"Prt Scrn" and S L O W l Y while holding those three keys down, press r s e i r o , one at a time in that sequence<- which will back out of everything, shut the system down and power off. 

[INDENT][INDENT]I be scratchn' and lookn'
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-06
Here is the latest, Bashing:

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
grub>


initrd (hd0,msdos1)/initrd.img
grub>


set
?=0
color_highlight=black/white
color_normal=white/black
pager=
prefix=(hd0,msdos1)/grub
root=hdo,msdos1
grub>

[In other words, no mention of "gfx_mode"]

boot

Screen rolled a couple times with text, last line reads:  "* Stopping userspace bootsplash [ok]"

[shutdown, reboot to "grub>"] and then [re-run earlier commands after seeing the key combo instructions, then press key combo:]



ctl+alt+"Prt Scrn" and SLOWlY press r s e i r o

[shuts down]
[cold reboot to grub>]

Does the help??  Thanks.

---

### Post by Bashing-om on 2014-04-06
ss1133xx; Well !

Yeah, that might explain why there is no display when you are booted into the operating system.
I had another thought in mind to look at, but this changes my thoughts.

Lemme re-boot and refresh my memory, and I will be back soonest I get caught up on what is going on in the forum at large.

---------------
My booting -- looks like I have all my issues resolved ! ... pending additional testing but I think I think ! I am presently able to boot any of my installs from the primary booting grub.

[INDENT][INDENT]if at first you do not succeed
[INDENT][INDENT][INDENT]try try again ( sky diving excepted )
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-04-06
ss1133xx; Hello,

I have (re)-booted into my grub prompt, this is what my grub set command returns:
```

grub> set
color_highlight=black/white
color_normal=white/black
default=0
feature_200_final=y
[color=blue]feature_all_video_module=y[/color]
feature_chainloader_bpp=y
feature_default_font_path=y
feature_menuentry_id=y
feature_menuentry_options=y
feature_ntldr=y
feature_platform_search_hint=y
font=unicode
[color=blue]gfxmode=auto[/color]
grub_cpu=i386
grub_platform=pc
have_grubenv=true
lang=en_US
linux_gfx_mode=keep
local_dir=(hdo,msdos1)/boot/grub/locale
match=0
menu_color_highlight=black/light-grey
menu_color_normal=white/black
menuentry_id_option=--id
pager=
prefix=hdo,msdos1
secondary_local_dir=
grub>

```

Comparing my output to your output, I highly suspect that when your grub reads the file "/boot/grub/grub.cfg" that file is corrupt and really messes up the boot process.

Let's take a look at that file and see if I can make heads or tails out of it.

Boot the liveUSB -> terminal commands:
```

sudo mount /dev/sda1 /mnt/work
cat /mnt/work/boot/grub/grub.cfg #post that output back to this thread#
sudo umount /mnt/work

```

I anticipate editing that file (yeah, that is a no-no to edit that file; but this time is what we are going to do ) and disabling 30_os-prober,
update-grub .. and I fully expect you to be able to boot.

more than one way
[INDENT][INDENT]to skin  this cat
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-06
Bashing:  Here we go:

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/work
mount: mount point /mnt/work does not exist

ubuntu@ubuntu:~$ sudo mount /dev/sda1/mnt/work
mount: can't find /dev/sda1/mnt/work in /etc/fstab or /etc/mtab

ubuntu@ubuntu:~$ sudo mount/dev/sda1/mnt/work
sudo: mount/dev/sda1/mnt/work: command not found

I tried the second and third times changing the spacing, thinking there might be a typo, but still no luck.

[FONT=georgia]sudo mount /dev/sda1 /mnt/work
mount: mount point /mnt/work does not exist[/FONT]

[FONT=georgia]So I tried the first one again -- still no luck.[/FONT]

[FONT=georgia]More ideas?  Thanks.


[/FONT][FONT=georgia]
[/FONT]

---

### Post by Bashing-om on 2014-04-06
ss1133xx; Hey,

That means the mount point does not exist - just like the system told you -, Recon this is the first time we have mounted the install's partition from this USB drive/ Was in my mind (remember) that the partition had been mounted and that the mount point persisted - must have been from the MintUSB.

Anyway, make a mount point from the ubuntu liveUSB:
```

sudo mkdir /mnt/work

```
and carry on, let's see what "/boot/grub/grub.cfg" contains. 
Hopefully get you back to an operating system !

[INDENT][INDENT]poke enough and
[INDENT][INDENT][INDENT]something is gonna give
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-07
Bashing:  here you go:
cat /mnt/work/boot/grub/grub.cfg #post that output back to this thread#

The terminal box appears to have cut off the first part of the response.  Bit hopefully you can see what you were looking for:
------------------------------------------

 set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.8.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    linux    /boot/vmlinuz-3.8.0-36-generic root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-36-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    echo    'Loading Linux 3.8.0-36-generic ...'
    linux    /boot/vmlinuz-3.8.0-36-generic root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.8.0-36-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.8.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    linux    /boot/vmlinuz-3.8.0-35-generic root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-35-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    echo    'Loading Linux 3.8.0-35-generic ...'
    linux    /boot/vmlinuz-3.8.0-35-generic root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.8.0-35-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    linux    /boot/vmlinuz-3.8.0-33-generic root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-33-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    echo    'Loading Linux 3.8.0-33-generic ...'
    linux    /boot/vmlinuz-3.8.0-33-generic root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.8.0-33-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    linux    /boot/vmlinuz-3.8.0-32-generic root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    echo    'Loading Linux 3.8.0-32-generic ...'
    linux    /boot/vmlinuz-3.8.0-32-generic root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.8.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    linux    /boot/vmlinuz-3.8.0-31-generic root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-31-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    echo    'Loading Linux 3.8.0-31-generic ...'
    linux    /boot/vmlinuz-3.8.0-31-generic root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.8.0-31-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    linux    /boot/vmlinuz-3.8.0-30-generic root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-30-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    echo    'Loading Linux 3.8.0-30-generic ...'
    linux    /boot/vmlinuz-3.8.0-30-generic root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.8.0-30-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    linux    /boot/vmlinuz-3.8.0-29-generic root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    echo    'Loading Linux 3.8.0-29-generic ...'
    linux    /boot/vmlinuz-3.8.0-29-generic root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.8.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-59-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    linux    /boot/vmlinuz-3.2.0-59-generic-pae root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-59-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-59-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    echo    'Loading Linux 3.2.0-59-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-59-generic-pae root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-59-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-58-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    linux    /boot/vmlinuz-3.2.0-58-generic-pae root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-58-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-58-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    echo    'Loading Linux 3.2.0-58-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-58-generic-pae root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-58-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-56-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    linux    /boot/vmlinuz-3.2.0-56-generic-pae root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-56-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-56-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    echo    'Loading Linux 3.2.0-56-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-56-generic-pae root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-56-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-55-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    linux    /boot/vmlinuz-3.2.0-55-generic-pae root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-55-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-55-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    echo    'Loading Linux 3.2.0-55-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-55-generic-pae root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-55-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-54-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    linux    /boot/vmlinuz-3.2.0-54-generic-pae root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-54-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-54-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    echo    'Loading Linux 3.2.0-54-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-54-generic-pae root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-54-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-53-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    linux    /boot/vmlinuz-3.2.0-53-generic-pae root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-53-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-53-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    echo    'Loading Linux 3.2.0-53-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-53-generic-pae root=UUID=140ae6cb-276b-4931-8b9a-be9e27803088 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-53-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 140ae6cb-276b-4931-8b9a-be9e27803088
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
ubuntu@ubuntu:~$ 

---------------------------------------------------------------------
Please let me know what I can do next.  Thanks as always.

---

### Post by Bashing-om on 2014-04-07
ss1133xx; Well shoot !

Throw that thought out the window too. I had "assumed" that 30_os-prober was picking up the Mint install and messing up the situation. But, NO, 30_os-prober is not even seeing the Mint install.

OK, next thought, with all those old old kernels taking up device space, hummmm, out of room in /boot and with no headroom and the system can not operate ?

There is a need to get rid of them anyway. Soo,

How confident do you feel working in a root terminal ? We are talking "root" here, be very sure, know what you are doing and why, there is absolutely no forgiveness for a mistake or error here.

What I have in mind to do now is to change root into the install from the live ubuntu USB; remove those unrequired kernels - that maybe a pain in and of it's self -, then fix grub.

We are going to to this in slow careful, easy stages. I will tell you exactly what to do, you must do exactly as directed. Curiosity now can "kill the cat".

Before we enter into the chroot and remove kernels, let's look and see what the system thinks it is booting so we do not remove that booting kernel.
from the liveUSB -> 
Terminal commands:
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work
ls -la /mnt/work/vmlinuz
sudo umount /mnt/work

```
of interest here is the out put of "ls -la /mnt/work/vmlinuz".

We are going to remove those old kernels, maybe then the booting issue will be resolved, if not, well then -> going to have to purge/restore Grub. That purging/restoring operation will require a working internet connection in that change root environment, may take a bit to make sure that happens. - just a heads up -

For now let's get the booting kernel version then remove kernels and see what results.

[INDENT][INDENT]sounds like a plan to me
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-07
Bashing:  Yup, sounds like a plan.  here we go:

ubuntu@ubuntu:~$ ls -la /mnt/work/vmlinuz
lrwxrwxrwx 1 root root 29 Mar  2 07:35 /mnt/work/vmlinuz -> boot/vmlinuz-3.8.0-36-generic

Regarding:  "How confident do you feel working in a root terminal?"

I don't know what that means, but if you can give me the commands, I can ut and paste them.  (At least, cut and paste when working in liveUSB.)
Let's give it a shot.

Thanks.

---

### Post by Bashing-om on 2014-04-07
ss1133xx; OK !

Give me some time to craft the commands. I am now well past my prime, so when I have it set up, will triple check it and will advise you when I have it.

Several hours at this terminal has taken a toll !

[INDENT][INDENT]I be work'n on it
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-04-07
ss1133xx; -->

I have looked this over three times, looks good but I am tired, so, look this over carefully and see if you perceive any errors, or have any questions or points we need to further discuss. Exercising caution is no accident !

Hold your breath, and here goes !
From the ubuntu liveUSB:
1st stage is set up the change root:
```

sudo mount /dev/sda1 /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo chroot /mnt/ /bin/bash

```
You are now in the install on the hard drive !
OK, now you are 'root' and have sole full access to the system. no more needing 'sudo' to gain any elevated authority. YOU my friend are it ! Be Careful.
Now we are going to remove kernels, keeping in mind that 3.8.0-36-generic is kept and 2 others for insurance.
2nd stage:
```

chmod -x /etc/grub.d/30_os-prober ##just to make sure it is disabled##
dpkg -P linux-image-3.2.0-{53,54,55,56,58,59}-generic-pae
dpkg -P linux-headers-3.2.0-{53,54,55,56,58,59}-generic-pae
dpkg -P linux-image-3.8.0-{29,30,31,32}-generic
dpkg -P linux-headers-3.8.0-{29,30,31,32}-generic

##And again for good measure:##
update-grub

```
Now all done for the time being, back out and return to the normal user mode:
```

exit

```
3rd stage:
Back out of the change root environment:
```

sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```

4th and FinaL stage - I think, maybe:
Now, let's see what the result is.

Reboot, set bios to boot the hard drive -> continue the boot process;

Now Please tell me that you boot !

[INDENT][INDENT]ELSE:
[INDENT][INDENT][INDENT]it is a continuing story
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-08
Hey Bashing: By chance do you know how I could get ubuntu's liveUSB to persist, like the Mint liveUSB?  It would be handy if it would remember my webpages, etc.

If so, great, if not, que sera.

---

### Post by Bashing-om on 2014-04-08
ss1133xx; Welp,

Not having used USB drives for that application I can not say directly.
This might help:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

[INDENT][INDENT]not much but,
[INDENT][INDENT]a nudge is better then nothing
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-08
Bashing:  Here you go:

------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
ubuntu@ubuntu:~$ sudo chroot /mnt/ /bin/bash
root@ubuntu:/# chmod -x /etc/grub.d/30_os-prober
root@ubuntu:/# 
---------------------------------------------------------------------
Don't know if want all this, but in case you do, here it is.  (The scoll back stopped at some point, but this is what I can scroll to:
dpkg -P linux-image-3.2.0-{53,54,55,56,58,59}-generic-pae
----------------------------------------------------------------------------Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-58-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-58-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-56-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-56-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-53-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-53-generic-pae /boot/vmlinuz-3.2.0-53-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-53-generic-pae /boot/vmlinuz-3.2.0-53-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-56-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-55-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-54-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-53-generic-pae /boot/vmlinuz-3.2.0-53-generic-pae
Removing linux-image-3.2.0-54-generic-pae ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-54-generic-pae /boot/vmlinuz-3.2.0-54-generic-pae
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-54-generic-pae /boot/vmlinuz-3.2.0-54-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-54-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-54-generic-pae /boot/vmlinuz-3.2.0-54-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-56-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-55-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-54-generic-pae /boot/vmlinuz-3.2.0-54-generic-pae
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-58-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-58-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-56-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-56-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-54-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-54-generic-pae /boot/vmlinuz-3.2.0-54-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-54-generic-pae /boot/vmlinuz-3.2.0-54-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-56-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-55-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-54-generic-pae /boot/vmlinuz-3.2.0-54-generic-pae
Removing linux-image-3.2.0-55-generic-pae ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-55-generic-pae /boot/vmlinuz-3.2.0-55-generic-pae
dkms: removing: virtualbox 4.1.12 (3.2.0-55-generic-pae) (i686)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.2.0-55-generic-pae (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-55-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-55-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-55-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-55-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.......

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-55-generic-pae /boot/vmlinuz-3.2.0-55-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-55-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-55-generic-pae /boot/vmlinuz-3.2.0-55-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-56-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-55-generic-pae /boot/vmlinuz-3.2.0-55-generic-pae
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-58-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-58-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-56-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-56-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-55-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-55-generic-pae /boot/vmlinuz-3.2.0-55-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-55-generic-pae /boot/vmlinuz-3.2.0-55-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-56-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-55-generic-pae /boot/vmlinuz-3.2.0-55-generic-pae
Removing linux-image-3.2.0-56-generic-pae ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
dkms: removing: virtualbox 4.1.12 (3.2.0-56-generic-pae) (i686)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.2.0-56-generic-pae (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-56-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-56-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-56-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-56-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-56-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-58-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-58-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-56-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
Removing linux-image-3.2.0-58-generic-pae ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
dkms: removing: virtualbox 4.1.12 (3.2.0-58-generic-pae) (i686)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.2.0-58-generic-pae (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-58-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-58-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
dpkg: dependency problems prevent removal of linux-image-3.2.0-59-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-59-generic-pae.
dpkg: error processing linux-image-3.2.0-59-generic-pae (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.2.0-59-generic-pae
root@ubuntu:/# 
--------------------------------------------------------------------------------------
root@ubuntu:/# dpkg -P linux-headers-3.2.0-{53,54,55,56,58,59}-generic-pae
-------------------------------------------------------------------------------------------
More scroll:
-------------------------------------------------------------------------------
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-53-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-53-generic-pae /boot/vmlinuz-3.2.0-53-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-53-generic-pae /boot/vmlinuz-3.2.0-53-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-56-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-55-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-54-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-53-generic-pae /boot/vmlinuz-3.2.0-53-generic-pae
Removing linux-image-3.2.0-54-generic-pae ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-54-generic-pae /boot/vmlinuz-3.2.0-54-generic-pae
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-54-generic-pae /boot/vmlinuz-3.2.0-54-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-54-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-54-generic-pae /boot/vmlinuz-3.2.0-54-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-56-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-55-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-54-generic-pae /boot/vmlinuz-3.2.0-54-generic-pae
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-58-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-58-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-56-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-56-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-54-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-54-generic-pae /boot/vmlinuz-3.2.0-54-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-54-generic-pae /boot/vmlinuz-3.2.0-54-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-56-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-55-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-54-generic-pae /boot/vmlinuz-3.2.0-54-generic-pae
Removing linux-image-3.2.0-55-generic-pae ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-55-generic-pae /boot/vmlinuz-3.2.0-55-generic-pae
dkms: removing: virtualbox 4.1.12 (3.2.0-55-generic-pae) (i686)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.2.0-55-generic-pae (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-55-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-55-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-55-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-55-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.......

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-55-generic-pae /boot/vmlinuz-3.2.0-55-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-55-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-55-generic-pae /boot/vmlinuz-3.2.0-55-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-56-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-55-generic-pae /boot/vmlinuz-3.2.0-55-generic-pae
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-58-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-58-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-56-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-56-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-55-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-55-generic-pae /boot/vmlinuz-3.2.0-55-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-55-generic-pae /boot/vmlinuz-3.2.0-55-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-56-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-55-generic-pae /boot/vmlinuz-3.2.0-55-generic-pae
Removing linux-image-3.2.0-56-generic-pae ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
dkms: removing: virtualbox 4.1.12 (3.2.0-56-generic-pae) (i686)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.2.0-56-generic-pae (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-56-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-56-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-56-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-56-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-56-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-58-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-58-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-56-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
Removing linux-image-3.2.0-58-generic-pae ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
dkms: removing: virtualbox 4.1.12 (3.2.0-58-generic-pae) (i686)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.2.0-58-generic-pae (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-58-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-58-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
dpkg: dependency problems prevent removal of linux-image-3.2.0-59-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-59-generic-pae.
dpkg: error processing linux-image-3.2.0-59-generic-pae (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.2.0-59-generic-pae
root@ubuntu:/# dpkg -P linux-headers-3.2.0-{53,54,55,56,58,59}-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.2.0-53-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.2.0-58-generic-pae
(Reading database ... 451921 files and directories currently installed.)
Removing linux-headers-3.2.0-54-generic-pae ...
Removing linux-headers-3.2.0-55-generic-pae ...
Removing linux-headers-3.2.0-56-generic-pae ...
dpkg: dependency problems prevent removal of linux-headers-3.2.0-59-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-59-generic-pae.
dpkg: error processing linux-headers-3.2.0-59-generic-pae (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.2.0-59-generic-pae
root@ubuntu:/# 
-------------------------------------------------------------------------------------
root@ubuntu:/# dpkg -P linux-image-3.8.0-{29,30,31,32}-generic
------------------------------------------------------------------------------------
More scroll:
----------------------------------------------------------------------------------
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-58-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-58-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-56-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
Removing linux-image-3.2.0-58-generic-pae ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
dkms: removing: virtualbox 4.1.12 (3.2.0-58-generic-pae) (i686)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.2.0-58-generic-pae (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-58-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-58-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
dpkg: dependency problems prevent removal of linux-image-3.2.0-59-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-59-generic-pae.
dpkg: error processing linux-image-3.2.0-59-generic-pae (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.2.0-59-generic-pae
root@ubuntu:/# dpkg -P linux-headers-3.2.0-{53,54,55,56,58,59}-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.2.0-53-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.2.0-58-generic-pae
(Reading database ... 451921 files and directories currently installed.)
Removing linux-headers-3.2.0-54-generic-pae ...
Removing linux-headers-3.2.0-55-generic-pae ...
Removing linux-headers-3.2.0-56-generic-pae ...
dpkg: dependency problems prevent removal of linux-headers-3.2.0-59-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-59-generic-pae.
dpkg: error processing linux-headers-3.2.0-59-generic-pae (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.2.0-59-generic-pae
root@ubuntu:/# 
root@ubuntu:/# dpkg -P linux-image-3.8.0-{29,30,31,32}-generic
(Reading database ... 426589 files and directories currently installed.)
Removing linux-image-3.8.0-29-generic ...
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-29-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Removing linux-image-3.8.0-30-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-30-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
Removing linux-image-3.8.0-31-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
dkms: removing: virtualbox 4.1.12 (3.8.0-31-generic) (i686)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.8.0-31-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-31-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-31-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-31-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-31-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-31-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
Removing linux-image-3.8.0-32-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
dkms: removing: virtualbox 4.1.12 (3.8.0-32-generic) (i686)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.8.0-32-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-32-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-32-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-32-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-32-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
root@ubuntu:/# 
---------------------------------------------------------------------------------------------
root@ubuntu:/# dpkg -P linux-headers-3.8.0-{29,30,31,32}-generic

-------------------------------------------------------------------------------------------------
More scroll:
-------------------------------------------------------------------------------------------------
-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-56-generic-pae /boot/vmlinuz-3.2.0-56-generic-pae
Removing linux-image-3.2.0-58-generic-pae ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
dkms: removing: virtualbox 4.1.12 (3.2.0-58-generic-pae) (i686)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.2.0-58-generic-pae (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-58-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-58-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-58-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.8.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
dpkg: dependency problems prevent removal of linux-image-3.2.0-59-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-59-generic-pae.
dpkg: error processing linux-image-3.2.0-59-generic-pae (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.2.0-59-generic-pae
root@ubuntu:/# dpkg -P linux-headers-3.2.0-{53,54,55,56,58,59}-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.2.0-53-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.2.0-58-generic-pae
(Reading database ... 451921 files and directories currently installed.)
Removing linux-headers-3.2.0-54-generic-pae ...
Removing linux-headers-3.2.0-55-generic-pae ...
Removing linux-headers-3.2.0-56-generic-pae ...
dpkg: dependency problems prevent removal of linux-headers-3.2.0-59-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-59-generic-pae.
dpkg: error processing linux-headers-3.2.0-59-generic-pae (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.2.0-59-generic-pae
root@ubuntu:/# 
root@ubuntu:/# dpkg -P linux-image-3.8.0-{29,30,31,32}-generic
(Reading database ... 426589 files and directories currently installed.)
Removing linux-image-3.8.0-29-generic ...
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-29-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.8.0-30-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Removing linux-image-3.8.0-30-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-30-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.8.0-31-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
Removing linux-image-3.8.0-31-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
dkms: removing: virtualbox 4.1.12 (3.8.0-31-generic) (i686)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.8.0-31-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-31-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-31-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-31-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-31-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-31-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.8.0-32-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
Removing linux-image-3.8.0-32-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
dkms: removing: virtualbox 4.1.12 (3.8.0-32-generic) (i686)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.8.0-32-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-32-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-32-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-32-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-32-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-36-generic...
P: Writing config for /boot/vmlinuz-3.8.0-35-generic...
P: Writing config for /boot/vmlinuz-3.8.0-33-generic...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
root@ubuntu:/# 
root@ubuntu:/# dpkg -P linux-headers-3.8.0-{29,30,31,32}-generic
(Reading database ... 407323 files and directories currently installed.)
Removing linux-headers-3.8.0-29-generic ...
Removing linux-headers-3.8.0-30-generic ...
Removing linux-headers-3.8.0-31-generic ...
Removing linux-headers-3.8.0-32-generic ...
root@ubuntu:/# 
----------------------------------------------------------------------------------------------------
root@ubuntu:/# update-grub
----------------------------------------------------------------------------------------------------
root@ubuntu:/# update-grub
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# 
-------------------------------------------------------------------------------------------
root@ubuntu:/# exit
------------------------------------------------------------------------------------------
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ 
-------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo umount /mnt/dev/pts
ubuntu@ubuntu:~$ sudo umount /mnt/sys
ubuntu@ubuntu:~$ sudo umount /mnt/proc
ubuntu@ubuntu:~$ sudo umount /mnt/dev
ubuntu@ubuntu:~$ sudo umount /mnt
ubuntu@ubuntu:~$ 
-------------------------------------------------------------------------------------------
I will report back later tonight with the reboot results.

Thanks for your continued support, Bashing!

---

### Post by Bashing-om on 2014-04-08
ss1133xx; Roger,

Standing by;

Should have operating head room now, and Grub rebuilt. Hope all workie great.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-09
Bashing:  Unfortunately, no luck.  Back to the now familiar refrain:

GNU GRUB ...
Minimal BASH-like line editing ...
grub>


Any more ideas??  Hope so.

---

### Post by Bashing-om on 2014-04-09
ss1133xx; Yuk !

That is some kind of weird.

Let's poke and see if we can get an idea where the problem does indeed lye.
Once more from the install on the hard drive, booted to the grub prompt:
what returns:
```

search -f /sbin/init
ls (hd0,msdos1)/boot/grub/grub.cfg
ls (hd0,msdos1)/vmlinuz
ls (hd0,msdos1)/
ls (hd0,msdos1)
ls /initrd.img

```
If the system paths are known, and the files are in place, the system "should" boot !
If those files are in place and one of several are corrupt, then of course will not boot, and we will have to find and/or rebuild that bad file.

once more we try
[INDENT][INDENT]if at first we do not succeed
[INDENT][INDENT][INDENT]then try try again ( sky diving excepted)
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-10
Hi Bashing:

Initially I could not find this Quick reply box -- had to dig around to find it.  Is there a limit on the number or content of threads?  
Anyway, here is what I got from the latest commands:

search -f /sbin/init
 hdo,msdos1


ls (hd0,msdos1)/boot/grub/grub.cfg
 grub.cfg


ls (hd0,msdos1)/vmlinuz
vmlinuz


ls (hd0,msdos1)/
lost+found/ etc/ #more text#  vmlinuz.old grub/



ls (hd0,msdos1)
   Partition hd0,msdos1:  # more text#   Total size 118288384 sectors


ls /initrd.img
 initrd.img

[exit]

Do you still think it is worth not invoking the nuclear option??

Thanks.

---

### Post by Bashing-om on 2014-04-10
ss1133xx; Well, It is like this.

All the paths are identified, the control files are present, and these control files have just been re-built, should be good !

I would prefer that we find and fix the problem rather than taking that nuclear approach, but it is your time, effort and frustration thus it is your call. So long as there is a possibility to isolate the cause, I am more than willing to - try try again -.

Right now from all the indications you should be able to boot !
Let's try and see what does result.
Boot up, bios set to boot from the hard drive ->
Grub prompt -> grub command line commands:
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```

When you do boot to the desktop -> terminal:
Terminal command:
```

sudo update grub

``` once more to insure the control files get rebuilt with the correct info.

Else: if you do not boot, relay back the exact returns from the commands in that attempt to boot from grub. Those results will indicate where to look for the problem. And we will
[INDENT][INDENT]try try again.[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-10
Hi Bashing, if you are willing to keep trying, I am too.  (I would have given up long ago -- am impressed with your willingness to keep trying things.)

Here goes: It is still booting to the grub> prompt after the previous commands, so:

grub>  linux (hd0,msdos1)vmlinuz root=/dev/sda1error:  invalid file name 'vmlinuz'

#should there be a forward slash before vmlinuz?  ("linux (hd0,msdos1)[COLOR=#ff0000]**/**[/COLOR]vmlinuz root=/dev/sda1" #


I stopped since I got the error.

Next up?  Thanks.

---

### Post by Bashing-om on 2014-04-10
ss1133xx; Yuk,

I hate when I do that  ! Yes that slash is needed !

At this point in my sessions I am tired and my think'n is often cloudy.

Correct the command to be:
```

linux (hd0,msdos1)/vmlinuz /dev/sda1 [color=red]ro[/color]

```
Not certain that the 'ro' boot parameter is needed, but it's use might prevent some problems.

because
[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-12
Hey Bashing:  Here it is:

grub>
linux (hd0,msdos1)/vmlinuz /dev/sda1 ro


# earlier command was slight different:  linux (hd0,msdos1)/vmlinuz [COLOR=#ff0000]root=[/COLOR]/dev/sda1 ro   #
# I used the more recent one    #

grub>
initrd (hd0,msdos1)/initrd.img


grub>
boot

# screen roll.  no boot.  Some of these may help understand what happened:

"Target filesystem doesn't have requested /sbin/init.
" No init found.  Try passing init=bootarg.

"BusyBox v1.18.5 ...
"Enter 'help' ....

"(initramfs)"

boot hangs at that point.

Nay ideas, Bashing?  Thanks.

---

### Post by Bashing-om on 2014-04-12
ss1133xx; Oh Shucks !

I try not to make those errors, knowing how difficult my think'n processes have become by then. And I still did not see that grieveous oversight !
Ok 3rd time is the charm !
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro ##yeah looked 3 times, is correct##
initrd (hd0,msdos1)/initrd.img
boot

```

If it still does not boot, next is to rebuild 'initrd.img' and related files.

[INDENT][INDENT]what does not kill us
[INDENT][INDENT][INDENT]makes us all the stronger
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-13
grub> linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro 
grub> initrd (hd0,msdos1)/initrd.img

grub> boot

Screen rolls.  Hangs.  No obvious error messages.  Last two messages start with "Opening socks listener ..."

More ideas for me, Basher?  Thanks.

---

### Post by Bashing-om on 2014-04-13
ss1133xx; Let's beat on it some more !

Let's try and explicitly load a particular older kernel.
Let's see what there is to work with; 
From that liveUSB, boot to terminal and mount the operating system partition:
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work
##then let's look at what is available and post these back ##
ls -la /mnt/work/vmlinuz
ls -la /mnt/work/boot
## UN mount that partition ##
sudo umount /mnt/work

```

So long as I can find a way forward
[INDENT][INDENT]there ain't no giving up
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-13
Bashing:  Here you go:

ubuntu@ubuntu:~$ sudo mkdir /mnt/work
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/work
ubuntu@ubuntu:~$ ls -la /mnt/work/vmlinuz
lrwxrwxrwx 1 root root 29 Mar  2 07:35 /mnt/work/vmlinuz -> boot/vmlinuz-3.8.0-36-generic
ubuntu@ubuntu:~$ ls -la /mnt/work/boot
total 96140
drwxr-xr-x  4 root root     4096 Apr  9 03:21 .
drwxr-xr-x 25 root root     4096 Mar 26 02:22 ..
-rw-r--r--  1 root root   804938 Jan  8 00:09 abi-3.2.0-59-generic-pae
-rw-r--r--  1 root root   926578 Oct 24 16:55 abi-3.8.0-33-generic
-rw-r--r--  1 root root   926578 Jan 30 17:50 abi-3.8.0-35-generic
-rw-r--r--  1 root root   926578 Feb  3 22:21 abi-3.8.0-36-generic
-rw-r--r--  1 root root   147576 Jan  8 00:09 config-3.2.0-59-generic-pae
-rw-r--r--  1 root root   160918 Oct 24 16:55 config-3.8.0-33-generic
-rw-r--r--  1 root root   160907 Jan 30 17:50 config-3.8.0-35-generic
-rw-r--r--  1 root root   160907 Feb  3 22:21 config-3.8.0-36-generic
drwxr-xr-x  3 root root     4096 Apr  9 03:21 extlinux
drwxr-xr-x  3 root root    12288 Apr  9 03:24 grub
-rw-r--r--  1 root root 14201328 Mar  2 07:34 initrd.img-3.2.0-59-generic-pae
-rw-r--r--  1 root root 16029103 Mar  2 22:40 initrd.img-3.8.0-33-generic
-rw-r--r--  1 root root 16082062 Mar  2 07:39 initrd.img-3.8.0-35-generic
-rw-r--r--  1 root root 16084046 Mar  3 06:10 initrd.img-3.8.0-36-generic
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2322099 Jan  8 00:09 System.map-3.2.0-59-generic-pae
-rw-------  1 root root  2549418 Oct 24 16:55 System.map-3.8.0-33-generic
-rw-------  1 root root  2552743 Jan 30 17:50 System.map-3.8.0-35-generic
-rw-------  1 root root  2552792 Feb  3 22:21 System.map-3.8.0-36-generic
-rw-------  1 root root  5033760 Jan  8 00:09 vmlinuz-3.2.0-59-generic-pae
-rw-------  1 root root  5441888 Oct 24 16:55 vmlinuz-3.8.0-33-generic
-rw-------  1 root root  5469504 Jan 30 17:50 vmlinuz-3.8.0-35-generic
-rw-------  1 root root  5469664 Feb  3 22:21 vmlinuz-3.8.0-36-generic
ubuntu@ubuntu:~$ 

Up next?  Keep up the good work!

---

### Post by Bashing-om on 2014-04-13
ss1133xx; OK .

Let's give this a whirl;
Grub prompt:
```

set ##returns 6 or more lines ?
##then##
linux /boot/vmlinuz-3.8.0-36-generic root=/dev/sda1 ro
initrd /boot/initrd.img-3.8.0-36-generic
boot

```
Depending on what happens, depends on what we do next, BUT ! I truly think this might boot !


Beat on a big rock enough
[INDENT][INDENT]and it will be a little rock
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-13
Hey Bashing:

"set" returned a lot mor ethan 6 lines.  here is the part of the scroll I can see: 

------------------------------------------------------
{ 
    initctl list | awk '{print $1}' | sort -u
}
_upstart_reload () 
{ 
    COMPREPLY=();
    _get_comp_words_by_ref cur prev;
    opts="--help --version -q --quiet -v --verbose --session --system --dest=";
    case "$prev" in 
        --help | --version)
            COMPREPLY=();
            return 0
        ;;
    esac;
    COMPREPLY=($(compgen -W "$opts $(_upstart_stoppable_jobs)" -- ${cur}));
    return 0
}
_upstart_restart () 
{ 
    COMPREPLY=();
    _get_comp_words_by_ref cur prev;
    opts="--help --version -q --quiet -v --verbose --session --system --dest=         -n --no-wait";
    case "$prev" in 
        --help | --version)
            COMPREPLY=();
            return 0
        ;;
    esac;
    COMPREPLY=($(compgen -W "$opts $(_upstart_stoppable_jobs)" -- ${cur}));
    return 0
}
_upstart_start () 
{ 
    COMPREPLY=();
    _get_comp_words_by_ref cur prev;
    opts="--help --version -q --quiet -v --verbose --session --system --dest=         -n --no-wait";
    case "$prev" in 
        --help | --version)
            COMPREPLY=();
            return 0
        ;;
    esac;
    COMPREPLY=($(compgen -W "$opts $(_upstart_startable_jobs)" -- ${cur}));
    return 0
}
_upstart_startable_jobs () 
{ 
    initctl list | cut -d\, -f1 | awk '$2 == "stop/waiting" {print $1}'
}
_upstart_status () 
{ 
    COMPREPLY=();
    _get_comp_words_by_ref cur prev;
    opts="--help --version -q -d --detail -e --enumerate --quiet -v --verbose --session --system --dest=";
    case "$prev" in 
        --help | --version)
            COMPREPLY=();
            return 0
        ;;
    esac;
    COMPREPLY=($(compgen -W "$opts $(_upstart_jobs)" -- ${cur}));
    return 0
}
_upstart_stop () 
{ 
    COMPREPLY=();
    _get_comp_words_by_ref cur prev;
    opts="--help --version -q --quiet -v --verbose --session --system --dest=         -n --no-wait";
    case "$prev" in 
        --help | --version)
            COMPREPLY=();
            return 0
        ;;
    esac;
    COMPREPLY=($(compgen -W "$opts $(_upstart_stoppable_jobs)" -- ${cur}));
    return 0
}
_upstart_stoppable_jobs () 
{ 
    initctl list | cut -d\, -f1 | awk '$2 == "start/running" {print $1}'
}
_upvar () 
{ 
    if unset -v "$1"; then
        if (( $# == 2 )); then
            eval $1=\"\$2\";
        else
            eval $1=\(\"\${@:2}\"\);
        fi;
    fi
}
_upvars () 
{ 
    if ! (( $# )); then
        echo "${FUNCNAME[0]}: usage: ${FUNCNAME[0]} [-v varname" "value] | [-aN varname [value ...]] ..." 1>&2;
        return 2;
    fi;
    while (( $# )); do
        case $1 in 
            -a*)
                [[ -n ${1#-a} ]] || { 
                    echo "bash: ${FUNCNAME[0]}: \`$1': missing" "number specifier" 1>&2;
                    return 1
                };
                printf %d "${1#-a}" &>/dev/null || { 
                    echo "bash:" "${FUNCNAME[0]}: \`$1': invalid number specifier" 1>&2;
                    return 1
                };
                [[ -n "$2" ]] && unset -v "$2" && eval $2=\(\"\${@:3:${1#-a}}\"\) && shift $((${1#-a} + 2)) || { 
                    echo "bash: ${FUNCNAME[0]}:" "\`$1${2+ }$2': missing argument(s)" 1>&2;
                    return 1
                }
            ;;
            -v)
                [[ -n "$2" ]] && unset -v "$2" && eval $2=\"\$3\" && shift 3 || { 
                    echo "bash: ${FUNCNAME[0]}: $1: missing" "argument(s)" 1>&2;
                    return 1
                }
            ;;
            *)
                echo "bash: ${FUNCNAME[0]}: $1: invalid option" 1>&2;
                return 1
            ;;
        esac;
    done
}
_usb_ids () 
{ 
    COMPREPLY=(${COMPREPLY[@]:-} $( compgen -W         "$( PATH="$PATH:/sbin" lsusb | awk '{print $6}' )" -- "$cur" ))
}
_user_at_host () 
{ 
    local cur;
    COMPREPLY=();
    _get_comp_words_by_ref -n : cur;
    if [[ $cur == *@* ]]; then
        _known_hosts_real "$cur";
    else
        COMPREPLY=($( compgen -u -- "$cur" ));
    fi;
    return 0
}
_useradd () 
{ 
    local cur prev split=false;
    COMPREPLY=();
    _get_comp_words_by_ref cur prev;
    _split_longopt && split=true;
    case $prev in 
        -c | --comment | -h | --help | -e | --expiredate | -f | --inactive | -k | --key | -p | --password | -u | --uid | -Z | --selinux-user)
            return 0
        ;;
        -b | --base-dir | -d | --home | -k | --skel)
            _filedir -d;
            return 0
        ;;
        -g | --gid)
            _gids;
            COMPREPLY=($( compgen -W '${COMPREPLY[@]} $( compgen -g )'                 -- "$cur" ));
            return 0
        ;;
        -G | --groups)
            COMPREPLY=($( compgen -g -- "$cur" ));
            return 0
        ;;
        -s | --shell)
            _shells;
            return 0
        ;;
    esac;
    $split && return 0;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '--base-dir --comment --home-dir --defaults \
            --expiredate --inactive --gid --groups --help --skel --key \
            --no-log-init --create-home --no-create-home --no-user-group \
            --non-unique --password --system --shell --uid --user-group \
            --selinux-user' -- "$cur" ));
        return 0;
    fi
}
_userdel () 
{ 
    local cur;
    COMPREPLY=();
    _get_comp_words_by_ref cur;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '--force --help --remove' -- "$cur" ));
        return 0;
    fi;
    COMPREPLY=($( compgen -u -- "$cur" ))
}
_usergroup () 
{ 
    if [[ $cur = *\\\\* || $cur = *:*:* ]]; then
        return;
    else
        if [[ $cur = *\\:* ]]; then
            local prefix;
            prefix=${cur%%*([^:])};
            prefix=${prefix//\\};
            local mycur="${cur#*[:]}";
            if [[ $1 == -u ]]; then
                _allowed_groups "$mycur";
            else
                local IFS='
';
                COMPREPLY=($( compgen -g -- "$mycur" ));
            fi;
            COMPREPLY=($( compgen -P "$prefix" -W "${COMPREPLY[@]}" ));
        else
            if [[ $cur = *:* ]]; then
                local mycur="${cur#*:}";
                if [[ $1 == -u ]]; then
                    _allowed_groups "$mycur";
                else
                    local IFS='
';
                    COMPREPLY=($( compgen -g -- "$mycur" ));
                fi;
            else
                if [[ $1 == -u ]]; then
                    _allowed_users "$cur";
                else
                    local IFS='
';
                    COMPREPLY=($( compgen -u -- "$cur" ));
                fi;
            fi;
        fi;
    fi
}
_usermod () 
{ 
    local cur prev split=false;
    COMPREPLY=();
    _get_comp_words_by_ref cur prev;
    _split_longopt && split=true;
    case $prev in 
        -c | --comment | -d | --home | -e | --expiredate | -f | --inactive | -h | --help | -l | --login | -p | --password | -u | --uid | -Z | --selinux-user)
            return 0
        ;;
        -g | --gid)
            _gids;
            COMPREPLY=($( compgen -W '${COMPREPLY[@]} $( compgen -g )'                 -- "$cur" ));
            return 0
        ;;
        -G | --groups)
            COMPREPLY=($( compgen -g -- "$cur" ));
            return 0
        ;;
        -s | --shell)
            _shells;
            return 0
        ;;
    esac;
    $split && return 0;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '--append --comment --home --expiredate \
            --inactive --gid --groups --help --login --lock --move-home \
            --non-unique --password --shell --uid --unlock --selinux-user'             -- "$cur" ));
        return 0;
    fi;
    COMPREPLY=($( compgen -u -- "$cur" ))
}
_vipw () 
{ 
    local cur prev;
    COMPREPLY=();
    _get_comp_words_by_ref cur prev;
    case $prev in 
        -h | --help)
            return 0
        ;;
    esac;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '--group --help --passwd \
            --quiet --shadow' -- "$cur" ));
        return 0;
    fi
}
_xhost () 
{ 
    local cur;
    _get_comp_words_by_ref cur;
    case $cur in 
        +*)
            _known_hosts_real -p+ "${cur:1}"
        ;;
        -*)
            _known_hosts_real -p- "${cur:1}"
        ;;
        *)
            _known_hosts_real "$cur"
        ;;
    esac;
    return 0
}
_xmodmap () 
{ 
    COMPREPLY=();
    local cur prev;
    _get_comp_words_by_ref cur prev;
    case $prev in 
        -display | -e)
            return 0
        ;;
    esac;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '-display -help -grammar -verbose -quiet -n
            -e -pm -pk -pke -pp' -- "$cur" ));
        return 0;
    fi;
    _filedir
}
_xrandr () 
{ 
    local cur prev output modes;
    COMPREPLY=();
    _get_comp_words_by_ref cur prev;
    case $prev in 
        --output)
            local outputs=$(xrandr|awk '/connected/ {print $1}');
            COMPREPLY=($(compgen -W "$outputs" -- "$cur"));
            return 0
        ;;
        --mode)
            for ((i = 1; i < COMP_CWORD; i++ ))
            do
                if [[ "${COMP_WORDS[i]}" == "--output" ]]; then
                    output=${COMP_WORDS[i+1]};
                    break;
                fi;
            done;
            modes=$(xrandr|sed -e "1,/$output/ d"                 -e "/connected/,$ d"|awk '{print $1}');
            COMPREPLY=($( compgen -W "$modes" -- "$cur"));
            return 0
        ;;
    esac;
    case $cur in 
        *)
            COMPREPLY=($(compgen -W '-display -help --orientation --query \
                --size --rate --version -x -y --screen --verbose --dryrun \
                --prop --fb --fbmm --dpi --output --auto --mode --preferred \
                --pos --reflect --rotate --left-of --right-of --above --below \
                --same-as --set --off --crtc --newmode --rmmode --addmode \
                --delmode' -- "$cur"));
            return 0
        ;;
    esac;
    return 0
}
_xrdb () 
{ 
    COMPREPLY=();
    local cur prev;
    _get_comp_words_by_ref cur prev;
    case $prev in 
        -backup | -display | -help)
            return 0
        ;;
        -cpp | -edit)
            _filedir;
            return 0
        ;;
    esac;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '-help -display -all -global -screen -screens
            -n -quiet -cpp -nocpp -symbols -query -load -override -merge
            -remove -retain -edit -backup' -- "$cur" ));
        return 0;
    fi;
    _filedir
}
_xz () 
{ 
    COMPREPLY=();
    local cur prev;
    _get_comp_words_by_ref cur prev;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '--compress --decompress --test --list \
            --keep --force --stdout --suffix --files --files0 --format --check \
            -0 -1 -2 -3 -4 -5 -6 -7 -8 -9 --fast --best --extreme --memory \
            --lzma1 --lzma2 --x86 --powerpc --ia64 --arm --armthumb --sparc \
            --delta --quiet --verbose --no-warn --help --long-help --version'             -- "$cur" ));
        return 0;
    fi;
    local split=false;
    _split_longopt && split=true;
    local xspec="*.@(xz|lzma|txz|tlz)";
    case $prev in 
        --decompress | --list | --test | -!(-*)[dlt]*)
            xspec="!"$xspec
        ;;
        --files | --files0)
            _filedir;
            return 0
        ;;
        -C | --check)
            COMPREPLY=($( compgen -W 'crc32 crc64 sha256' -- "$cur" ));
            return 0
        ;;
        -F | --format)
            COMPREPLY=($( compgen -W 'auto xz lzma raw' -- "$cur" ));
            return 0
        ;;
        -M | --memory | -S | --suffix | --delta | --lzma1 | --lzma2)
            return 0
        ;;
        -h | --help | -H | --long-help | -V | --version)
            return 0
        ;;
    esac;
    $split && return 0;
    _expand || return 0;
    local IFS='
';
    _compopt_o_filenames;
    COMPREPLY=($( compgen -f -X "$xspec" -- "$cur" ) $( compgen -d -- "$cur" ))
}
_zeitgeist_daemon () 
{ 
    local cur=${COMP_WORDS[COMP_CWORD]};
    COMPREPLY=($(compgen -W "`zeitgeist-daemon --shell-completion`" -- $cur))
}
command_not_found_handle () 
{ 
    if [ -x /usr/lib/command-not-found ]; then
        /usr/bin/python /usr/lib/command-not-found -- "$1";
        return $?;
    else
        if [ -x /usr/share/command-not-found/command-not-found ]; then
            /usr/bin/python /usr/share/command-not-found/command-not-found -- "$1";
            return $?;
        else
            printf "%s: command not found\n" "$1" 1>&2;
            return 127;
        fi;
    fi
}
dequote () 
{ 
    eval echo "$1" 2> /dev/null
}
quote () 
{ 
    echo \'${1//\'/\'\\\'\'}\'
}
quote_readline () 
{ 
    local quoted;
    _quote_readline_by_ref "$1" ret;
    printf %s "$ret"
}
ubuntu@ubuntu:~$ 
-------------------------------------------------------------------------
then:

ubuntu@ubuntu:~$ linux /boot/vmlinuz-3.8.0-36-generic root=/dev/sda1 ro

The program 'linux' is currently not installed.  You can install it by typing:

[COLOR=#ff0000]sudo apt-get install user-mode-linux[/COLOR]
You will have to enable the component called 'universe'
ubuntu@ubuntu:~$ 

----------------------------------------------------------------------------
ubuntu@ubuntu:~$ initrd /boot/initrd.img-3.8.0-36-generic
initrd: command not found
---------------------------------------------------------------------------

Should I enter that command?  ("[COLOR=#ff0000]sudo apt-get install user-mode-linux[/COLOR]")

Thanks.

---

### Post by Bashing-om on 2014-04-14
ss1133xx, Wow, did it ever !

Now that had me going until I SAW 
> 
[color=red] ubuntu@ubuntu:~$[/color] linux /boot/vmlinuz-3.8.0-36-generic root=/dev/sda1 ro

Those results are from the liveUSB ! Crashed my hopes that I was fixing to learn something new .

What we are doing now is trying to boot from the install at the grub prompt.

Back up regroup and from the install's grub prompt what returns ;
```

##  Grub prompt:  ##
set ##returns 6 or more lines ? -> remember we have looked at 'set' before, what is it now ?
##then##
linux /boot/vmlinuz-3.8.0-36-generic root=/dev/sda1 ro
initrd /boot/initrd.img-3.8.0-36-generic
boot

```

we be try'n to make that 
[INDENT][INDENT][INDENT]big step forward
[/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-14
Sorry, my mistake Bashing -- I booted to the liveUSB instead of the grub prompt.  Anyway, here goes nothing:

grub> set
# returns 5 lines

linux /boot/vmlinuz-3.8.0-36-generic root=/dev/sda1 ro



initrd /boot/initrd.img-3.8.0-36-generic
boot

# screen flashed and rolls -- no boot -- ends at underline prompt on otherwise blank screen#
#  reboot to grub prompt #

Where to next?

---

### Post by Bashing-om on 2014-04-14
ss1133xx; Curiouser and curiouser !

OK, Let's "assume" that the file initrd.img is damaged. Let's prepare to rebuild it.
1st I want to insure that there is network connectivity from within the change root environment.

So do the change root procedure as directed in post # 72.

Once in the install via the chroot, what returns from terminal command:
```

ping -c3 8.8.8.8

```
If that is a positive result, will continue.

Else, going to have to work on getting an inter net connection within that change root.

[INDENT][INDENT]ain't no quit yet !
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-15
Hey Bashing:  Just to be clear, in psot #72, you mean these commands from the liveUSB:

-----------------------------------------
sudo mount /dev/sda1 /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo chroot /mnt/ /bin/bash
------------------------------------------

and then this one:

ping -c3 8.8.8.8

Do I have that right?

P.S.  What would cause damage to  initrd.img?

---

### Post by Bashing-om on 2014-04-15
ss1133xx: Hello ;;

Yes that is the correct procedure, want to know that you have internet connectivity for sure.

As to if/what can damage the file initrd.img, well, consider that what transpires in the boot process between copying files into ram space and back to 'user" space is  very complex - a lot is going on. Any small glitch can mess things up. 

I have had time to reconsider, and as we have tried to boot with 2 different images, unsuccessfully; I can not see that the problem is in that file.

Let's take this approach, and see what results:
do that change root routine, and once into the install -
Yes I still want to know if there is internet connectivity, do that ping command below and advise on results.
And now the try for a fix:
Remember, in the chroot you are 'root' and "sudo" is not needed.
```

ping -c3 8.8.8.8
chmod -x /etc/grub.d/30_os-prober
update-grub
exit

```
back out of the change root by UNmounting everything and
REboot into the install on the hard drive.
When/if you boot to that dreaded grub prompt, let's look at the condition of 'grub.cfg' .
do at that grub prompt:
```

configfile (hd0,msdos1)/boot/grub/grub.cfg

```
Which should bring up grub's boot menu -> what results when you select to boot ubuntu as you normally would if the boot process were not broken ?

[INDENT]if we poke at it long enough and hard enough
[INDENT][INDENT][INDENT]something is going to give (more information)
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-15
Bashing:  Here you go:

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
ubuntu@ubuntu:~$ sudo chroot /mnt/ /bin/bash

root@ubuntu:/# ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=47 time=21.1 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=47 time=22.1 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=47 time=21.9 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 21.138/21.733/22.127/0.444 ms

root@ubuntu:/# chmod -x /etc/grub.d/30_os-prober

root@ubuntu:/# update-grub
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-59-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# 
-------------------------------------------------------------------------------------

I'll report back about the next boot.  (By the way, I should have said that I knew that I had an internet connection in liveUSB.  That's what's using now to send this.)

---

### Post by Bashing-om on 2014-04-15
[COLOR=#000000]ss1133xx; Hey
[/COLOR]

I am waiting on pins and needles.
> 
[COLOR=#000000]root@ubuntu:/# ping -c3 8.8.8.8
[/COLOR][COLOR=#000000] Hey, guess what ? Here you are not in the USB, but in the hard drive install !
I did want to make sure that you had internet available in the change root ( some times one has to copy some files to get inter net to work).

We may need that connection soon.
[/COLOR][INDENT=2][COLOR=#000000]
just hang'n loose

[/COLOR][/INDENT]

---

### Post by ss1133xx on 2014-04-15
Bashing:  After boot:

configfile (hd0,msdos1)/boot/grub/grub.cfg

# get grub menu, only option is Linux 3.8.0-36-generic, earlier ubuntu versions not listed#


#selected option on top.  screen rolls.  Boot hangs.  Last line "opening control listener ....#

Well, it looked good for awhile. Any more ideas??

---

### Post by Bashing-om on 2014-04-15
[COLOR=#000000]ss1133xx; Yuk ![/COLOR] 

Not at all what I had expected.
> 
[COLOR=#000000]get grub menu, only option is Linux 3.8.0-36-generic, 
[/COLOR][COLOR=#000000]
Yeah real weird ! When we know there a several kernels still installed !..

OK; do the change root routine once more, and let's rebuild initramfs.
When you are back into that full change root;
Terminal command:

[/COLOR]```
update-initramfs -u
exit

```

back out of the chroot (un mount everything).

RE-Boot again and lets see now if you boot normally (!!!).[INDENT=2]maybe yes ??

[/INDENT]

---

### Post by ss1133xx on 2014-04-18
Bashing:

root@ubuntu:/# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.8.0-36-generic
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$

Will report back after boot attempt.

---

### Post by ss1133xx on 2014-04-18
Bashing:  Back to grub>.  Oh well, back to the drawing board.

Any more ideas for me?

---

### Post by Bashing-om on 2014-04-18
ss1133xx; Yeah, I do, I do !

The situation is like this, We know we have a booting problem, however, as the system is not booted, there is no way to log what is not happening. So we have do some extrapolating (more !).
So, because we can display a grub menu we know that grub's stage 2 is loaded. From that grub menu unable to complete the boot process. -> That means that there is a file(s) corrupt or missing. These primary control files are initrd.img and vmlinuz. We know that the file system is intact as we are able to change root into it. Let's try and create those files and see if we can get additional info.

Boot back into the change root to gain access to the installed system and create the files for the most recent kernel image AND we are going to enable verbose mode and write the output to a file we can examine !
In that full change root environment do:
```

update-initramfs -c -v -k 3.8.0-36-generic > /home/<Your_User_name_here>/build.txt 2>&1
##we are rebuilding and there will be a lot of output, may take a bit to complete.##
##where "Your_User_name_here" is the user name you use on that installed operating system ubuntu.
chmod -x /etc/grub.d/30_os-prober ##because the rebuild will reset the execute bit, and presently I do not want os-proper to function.,
exit

```

Back out of the change root, and let's see what the result is.

Reboot and let's see if now you boot, 

Want to know if there is a grub boot menu, as by default - if only one OS is installed the grub menu will not display; we will manually intervene and make it display ( if it is available):
As soon as the bios screen clears, depress repeatedly the right shift key ( there is but a 3 second window for grub to recognize that a key has been depressed ) -> grub boot menu (??).
Yes, - what results when you select 'ubuntu' ?
Not booting when ubuntu is selected ?
reboot 
Then Let's  try and see if the system will boot by 'recovery' mode:
When booting, depress shift key -> boot menu -> advanced options -> recovery; What results when attempting to boot in recovery mode. Is foreseeable that you will boot to a temporary black screen of some duration before the recovery console is loaded. in the recovery console choose 'resume' . Do you now boot into the operating system ?

Else we are going to try to boot with explicit kernel directives from that grub > prompt !

One more time .

[INDENT]keep try'n
[INDENT][INDENT][INDENT]'till something gives
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-26
Hi Bashing:  Here is what I got:

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
ubuntu@ubuntu:~$ sudo chroot /mnt/ /bin/bash
root@ubuntu:/# update-initramfs -c -v -k 3.8.0-36-generic > /home/#name#/build.txt 2>&1
root@ubuntu:/# chmod - x /etc/grub.d/30_os-prober
chmod: cannot access `x': No such file or directory

I'm not sure if the "x" was a placeholder or not -- I entered the command you provided.

More ideas?

Regarding "Back out of the change root,"  is that necessary, given that I'm booting from a non-persistent liveUSB?  In oother words, won't it reset automatically when i re-boot?

Thanks.

---

### Post by Bashing-om on 2014-04-26
ss1133xx, Hey

Thought I had lost ya !

Back alla the way back out of that change root, you are in the actual install and we must protect the file system. Leaving all those things mounted and shutting down leaves all those files in an inconsistent state, You want to drive the system nuts, that is a good way to do so.
As to the wrong 'chmod - x /etc/grub.d/30_os-prober' typo, that silly little space after '-' !!
the proper syntax is:
```

chmod -x /etc/grub.d/30_os-prober

```
I will correct my post.

Back out, reboot, and I expect you to boot to the grub menu.

[INDENT][INDENT]try try try again
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-27
Hey Bashing:

Unfortunately, I'm back to GNU GRUB.  Any more ideas?

Thanks.

---

### Post by Bashing-om on 2014-04-27
ss1133xx; Yukkie.

'Bout to run out of ideas of what file is messed up where in this booting process.
Let's take a look at that file that was built on that initramfs creation; see if there are any hints as to what is transpiring.
From the liveUSB:
```

sudo mkdir mnt/work
sudo mount /dev/sda1 /mnt/work
cat /mnt/work/home/<Your_User_name_here>/build.txt

```
For example:
cat /mnt/work/home/ss1133xx/build.txt
where 'ss1133xx' is the user name for that installed system. make the adjustment as required.
Copy and paste that file back to us.
Then back out of the file system by (UN)mounting '/mnt'.
```

sudo umount /mnt/work

```

What can I say ?
[INDENT]even after all this time ->
[INDENT][INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-27
Bashing:  Here it is: (what I can see on the scroll, at least)

Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/vmw_pvscsi.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
Adding binary /lib/firmware/3.8.0-36-generic/ql2500_fw.bin
Adding firmware ql2500_fw.bin
Adding binary /lib/firmware/3.8.0-36-generic/ql2400_fw.bin
Adding firmware ql2400_fw.bin
Adding binary /lib/firmware/3.8.0-36-generic/ql2322_fw.bin
Adding firmware ql2322_fw.bin
Adding binary /lib/firmware/3.8.0-36-generic/ql2300_fw.bin
Adding firmware ql2300_fw.bin
Adding binary /lib/firmware/ql2200_fw.bin
Adding firmware ql2200_fw.bin
Adding binary /lib/firmware/ql2100_fw.bin
Adding firmware ql2100_fw.bin
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/target/target_core_mod.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/qla2xxx/tcm_qla2xxx.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/hv_storvsc.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/mvumi.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/mvsas/mvsas.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/qlogicfas408.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/qlogicfas.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/3w-xxxx.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/lpfc/lpfc.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/53c700.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/BusLogic.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/fdomain.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/in2000.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/cxgbi/libcxgbi.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/cxgbi/cxgb3i/cxgb3i.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/cxgbi/cxgb4i/cxgb4i.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/be2iscsi/be2iscsi.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/a100u2w.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/eata.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/initio.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/aha1542.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/dpt_i2o.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/stex.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/ipr.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/3w-sas.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/virtio_scsi.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/bnx2fc/bnx2fc.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/hptiop.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/fcoe/fcoe.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/osd/libosd.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/osd/osd.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/qla1280.ko
Adding binary /lib/firmware/3.8.0-36-generic/qlogic/12160.bin
Adding firmware qlogic/12160.bin
Adding binary /lib/firmware/3.8.0-36-generic/qlogic/1280.bin
Adding firmware qlogic/1280.bin
Adding binary /lib/firmware/3.8.0-36-generic/qlogic/1040.bin
Adding firmware qlogic/1040.bin
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/advansys.ko
Adding binary /lib/firmware/3.8.0-36-generic/advansys/38C1600.bin
Adding firmware advansys/38C1600.bin
Adding binary /lib/firmware/3.8.0-36-generic/advansys/38C0800.bin
Adding firmware advansys/38C0800.bin
Adding binary /lib/firmware/3.8.0-36-generic/advansys/3550.bin
Adding firmware advansys/3550.bin
Adding binary /lib/firmware/3.8.0-36-generic/advansys/mcode.bin
Adding firmware advansys/mcode.bin
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/hpsa.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/g_NCR5380_mmio.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/iscsi_tcp.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/wd7000.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/sim710.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/NCR53c406a.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/3w-9xxx.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/aha1740.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/pcmcia/nsp_cs.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/pas16.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/scsi_transport_srp.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/sym53c416.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/pm8001/pm8001.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/imm.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko
Adding binary /lib/firmware/aic94xx-seq.fw
Adding firmware aic94xx-seq.fw
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/message/fusion/mptbase.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/message/fusion/mptscsih.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/message/fusion/mptfc.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/message/fusion/mptsas.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/message/fusion/mptspi.ko
Copying module directory kernel/drivers/block
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/nbd.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/lib/lru_cache.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/drbd/drbd.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/sx8.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/cpqarray.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/cciss.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/pktcdvd.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/floppy.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/mtip32xx/mtip32xx.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/paride.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/frpw.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/epia.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/friq.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/comm.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/epat.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/fit2.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/bpck.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/pd.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/pg.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/pf.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/pcd.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/kbic.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/ktti.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/bpck6.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/on26.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/fit3.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/dstr.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/pt.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/on20.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/paride/aten.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/cryptoloop.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/umem.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/xen-blkback/xen-blkback.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/DAC960.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/aoe/aoe.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/osdblk.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/net/ceph/libceph.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/rbd.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/block/nvme.ko
Copying module directory kernel/drivers/ata
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/sata_sis.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_sc1200.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_hpt366.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_cypress.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/sata_inic162x.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_oldpiix.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_amd.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_cmd64x.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_cs5530.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_piccolo.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/sata_sil24.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_opti.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_sch.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/libahci.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/acard-ahci.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_it821x.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/ahci.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_arasan_cf.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/sata_qstor.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/sata_uli.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_efar.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/sata_via.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_ninja32.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_sil680.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_atiixp.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_hpt3x3.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_optidma.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_ns87415.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_jmicron.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_triflex.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_pdc2027x.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/sata_sx4.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_ali.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_marvell.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_mpiix.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_cmd640.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_legacy.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/sata_sil.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/sata_promise.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pdc_adma.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_ns87410.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_radisys.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_cs5520.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_platform.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_rdc.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_cs5536.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_hpt3x2n.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/sata_nv.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_it8213.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_pcmcia.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/sata_svw.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_atp867x.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_rz1000.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_cs5535.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/sata_vsc.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_netcell.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/sata_mv.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_serverworks.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_via.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_sl82c105.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_acpi.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/ahci_platform.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_pdc202xx_old.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_artop.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_hpt37x.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/ata/pata_isapnp.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/message/i2o/i2o_core.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/message/i2o/i2o_block.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/firewire/firewire-core.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/firewire/firewire-ohci.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/firewire/firewire-sbp2.ko
Copying module directory kernel/drivers/mmc
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/mmc/card/sdio_uart.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/mmc/card/mmc_block.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/mmc/host/sdhci.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/mmc/host/sdhci-acpi.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/mmc/host/sdhci-pci.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/mmc/host/sdricoh_cs.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/mmc/host/wbsd.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/mmc/host/via-sdmmc.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/mmc/host/sdhci-pltfm.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/misc/cb710/cb710.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/mmc/host/cb710-mmc.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/mmc/host/ushc.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/mfd/rtsx_pci.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/mmc/host/rtsx_pci_sdmmc.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/mmc/host/vub300.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/misc/tifm_core.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/mmc/host/tifm_sd.ko
Copying module directory kernel/drivers/usb/storage
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/usb/storage/usb-storage.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/usb/storage/ums-usbat.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/usb/storage/ums-eneub6250.ko
Adding binary /lib/firmware/ene-ub6250/ms_rdwr.bin
Adding firmware ene-ub6250/ms_rdwr.bin
Adding binary /lib/firmware/ene-ub6250/msp_rdwr.bin
Adding firmware ene-ub6250/msp_rdwr.bin
Adding binary /lib/firmware/ene-ub6250/ms_init.bin
Adding firmware ene-ub6250/ms_init.bin
Adding binary /lib/firmware/ene-ub6250/sd_rdwr.bin
Adding firmware ene-ub6250/sd_rdwr.bin
Adding binary /lib/firmware/ene-ub6250/sd_init2.bin
Adding firmware ene-ub6250/sd_init2.bin
Adding binary /lib/firmware/ene-ub6250/sd_init1.bin
Adding firmware ene-ub6250/sd_init1.bin
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/usb/storage/ums-realtek.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/usb/storage/ums-jumpshot.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/usb/storage/ums-cypress.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/usb/storage/ums-isd200.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/usb/storage/ums-freecom.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/usb/storage/ums-datafab.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/usb/storage/ums-alauda.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/usb/storage/ums-sddr09.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/usb/storage/ums-onetouch.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/usb/storage/ums-karma.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/usb/storage/ums-sddr55.ko
Adding module /lib/modules/3.8.0-36-generic/kernel/drivers/hv/hv_utils.ko
Adding binary /etc/initramfs-tools/conf.d/resume
Adding binary /usr/lib/initramfs-tools/bin/wait-for-root
Adding library /lib/i386-linux-gnu/libudev.so.0
Adding library /lib/i386-linux-gnu/libc.so.6
Adding library /lib/i386-linux-gnu/librt.so.1
Adding library /lib/ld-linux.so.2
Adding library /lib/i386-linux-gnu/libpthread.so.0
Adding binary /sbin/modprobe
Adding binary /sbin/rmmod
Adding binary /sbin/blkid
Adding library /lib/i386-linux-gnu/libblkid.so.1
Adding library /lib/i386-linux-gnu/libuuid.so.1
Calling hook compcache
Calling hook fixrtc
Adding binary /bin/date
Adding binary /sbin/hwclock
Adding binary /sbin/dumpe2fs
Adding library /lib/i386-linux-gnu/libext2fs.so.2
Adding library /lib/i386-linux-gnu/libcom_err.so.2
Adding library /lib/i386-linux-gnu/libe2p.so.2
Calling hook fuse
Adding binary /sbin/mount.fuse
Calling hook klibc
Calling hook mountall
Calling hook thermal
Calling hook udev
Adding binary /sbin/udevd
Adding library /lib/i386-linux-gnu/libselinux.so.1
Adding library /lib/i386-linux-gnu/libdl.so.2
Adding binary /sbin/udevadm
Adding binary /lib/udev/firmware
Adding binary /lib/udev/ata_id
Adding binary /sbin/blkid
Adding binary /lib/udev/scsi_id
Calling hook ntfs_3g
Adding binary /bin/ntfs-3g
Adding library /lib/libfuse.so.2
Adding library /lib/i386-linux-gnu/libntfs-3g.so.831
Calling hook console_setup
Calling hook kbd
Adding binary /bin/setfont
Adding binary /bin/kbd_mode
Adding binary /bin/loadkeys
Calling hook busybox
Adding binary /usr/lib/initramfs-tools/bin/busybox
Calling hook dmsetup
Adding binary /sbin/dmsetup
Adding library /lib/libdevmapper.so.1.02.1
Building cpio /boot/initrd.img-3.8.0-36-generic.new initramfs
ubuntu@ubuntu:~$ 

Does that help?  

By the way, I added a forward slash:  
sudo mkdir [COLOR=#ff0000]/[/COLOR]mnt/work

[FONT=century gothic]You mentioned "us" ("paste that file back to us") -- is there more than one of you??
[/FONT][FONT=century gothic]Thanks.
[/FONT]

---

### Post by ss1133xx on 2014-04-27
P.S. Bashing:  I've been unable to access my data drive for a couple months.  Any suggestions on how I can access that drive from the liveUSB?

---

### Post by Bashing-om on 2014-04-27
ss1133xx; Sheessh, 

That at least alleviates some concerns, the image builds and with NO errors ! ( is that impressive or what !) That "should" workie great.
and hey;
> 
You mentioned "us" ("paste that file back to us") -- is there more than one of you??

Consider that here are 1800++ views on this thread, which means several hundred people are looking over our shoulders. /peer review is great !/

OK, let's try and boot from grub with explicit directions: Cutting straight to the nub as all I want to know is - does it boot .
From the grub prompt:
```

linux (hd0,msdos1)/boot/vmlinuz-3.8.0-36-generic root=/dev/sda1 ro
initrd (hd0,msdos1)/boot/initrd.img-3.8.0-36-generic
boot

```
What results ? -> error messages ?, black screen with nothing ? initramfs prompt ? OR glory be it boots !

[INDENT][INDENT]'bout the most trying thing
[INDENT][INDENT][INDENT]I have ever encountered 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-04-27
ss1133xx; OFF topic;

Access to the data disk, sure we can do that from the liveUSB . Is the data disk formatted NTFS or what ? , show (me):
```

sudo fdisk -lu

```
And tell me which of them is the "data disk".
And we will see how to mount and access that sucker from the liveUSB.

[INDENT][INDENT]we can at least do this
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-04-28
Bashing:  Device sdb is my data disk.  sda is where I install the os.  sdc is the liveUSB.

Here is what it shows:

---------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007ead8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   118290431    59144192   83  Linux
/dev/sda2       118292478   156248063    18977793    5  Extended
/dev/sda5       147863552   156248063     4192256   82  Linux swap / Solaris
/dev/sda6       118294528   147861503    14783488   83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    31266815    15633392    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 
---------------------------------------------------------------------------------------------------
Thanks for your willingness to help with an off-topic question!

I will get back to you after running those grub commands.  Re "'bout the most trying thing  I have ever encountered"
Yeah me too.

---

### Post by Bashing-om on 2014-04-28
ss1133xx; Well, well;
Your data disk 'sdb' is formatted 'GPT', the tool fdisk can not deal with it. Need to download another tool.
```

sudo apt-get install gdisk

```
once installed do:
```

sudo gdisk -l /dev/sdb

```
Once known, should be a simple matter to mount and access device 'sdb' from that liveUSB.

[INDENT][INDENT]meanwhile,
[INDENT][INDENT][INDENT]back at the ranch
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-05-02
Bashing:  Hmmm:

---------------------------------------------------------------
ubuntu@ubuntu:~$ sudo apt-get install gdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gdisk
---------------------------------------------------------------

Any ideas?  Also, is it bad that the data disk is formatted GPT?  I thought I used the linux standard when I formatted it.  (You asked if it was NTFS.  Do you like that format better?)

Another off-topic question:  do you know how I can make the liveUSB persist?

Thanks.

P.S.  I will try those grub commands next.

---

### Post by ss1133xx on 2014-05-02
Bashing:

At the grub prompt, I ran:

-----------------------------------------------------------------
linux (hd0,msdos1)/boot/vmlinuz-3.8.0-36-generic root=/dev/sda1 ro
initrd (hd0,msdos1)/boot/initrd.img-3.8.0-36-generic
boot
-----------------------------------------------------------------

The screen flashes and scrolls, and end with a underline cursor in the upper left hand corner of the screen.  I have described that before.

Well, are we at the end of the line?  Time for the nuclear option?  (I need to get my 3tb data drive back in commission.)

Thanks.

---

### Post by ss1133xx on 2014-05-03
Any more ideas for me, Bashing?

---

### Post by Bashing-om on 2014-05-03
ss1133xx; Sheesshh ,

We have done just about everything; rebuilds, replaces, still do not know where the problem lies.

One more time, let's try a different rebuild process.

From the liveUSB and in the full change root environment:
Make sure that you have internet connectivity:
purge old and reinstall new to sda:
```

apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install --recheck /dev/sda
update-grub

```
Again, disregard the warning that 'grub is not installed" and proceed. 
Post back any other errors reported ( hey have yet to get any indicative error direction !)

Back out of the chroot, reboot into the install ( change the boot priority) .. and let's see what the result is.

As much as I hate to say, this is my last thought on a means to restore booting. As much as I want to know the causation, and want to fix this, and as no others have offered better recommendations. Yeah, Time to do the nuclear thing, and get back in business.

[INDENT]one of those times, I just do not know
[/INDENT]

---

### Post by ss1133xx on 2014-05-04
I'll try that Bashing and let you know.

How about gdisk to access my data drive -- did I do something wrong?

---

### Post by Bashing-om on 2014-05-04
ss1133xx; Welp;

On gdisk; makes no sense to me at this time, I see no error, but this results ?
> 
E: Unable to locate package gdisk

HUH ???????

Don't have any idea of what the problem is, as - for me :
'apt-cache show gdisk' :
> 
Filename: pool/main/g/gdisk/gdisk_0.8.7-1_amd64.deb

tells us it is available in the 'main' section of the repository. There should be absolutely no reason you have that fetch turned down in "/etc/apt/sources.list"

Once you have identified the partition containing your data, you can access that partition in a similar manner as we have been accessing the root partition of sda:
Make a means to attache your data to the file system;
```

sudo mkdir /mnt/access

```

Mount that partition with that created mount point.
```

sudo mount /dev/sdb1 /mnt/access ##given that gdisk sees the "data" partition as sdb1 - adjust accordingly.

```

Do as you like now, and when done, ReMemBer -> (UN)mount that partition, file system damage may result elsewise !
```

sudo umount /mnt/access

```

Now are you aware all this can also be done from the file manager in the GUI ? All available file systems should be reflected on the left pane of the file manager. Sometimes, depending on what you are doing, it is quicker and easier to work from the file manager.

[INDENT][INDENT]It is all a process
[INDENT][INDENT][INDENT]learning too is a process
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-05-04
Bashing:

No errors reported on the grub rebuild.  I'll report back after I re-boot.

As for the data drive, I entered those commands:

ubuntu@ubuntu:~$ sudo mkdir /mnt/access
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt/access

But the 3tb drive (sdb) is not listed.  (In the past it has been listed, but when I clicked to open, got a message saying it was unavailable or inaccessible, or something like that.  Then it disappeared from the list.

Any more suggestions?  (I didn't follow your comments about my inability to use gdisk.)

Thanks.

---

### Post by Bashing-om on 2014-05-04
ss1133xx; Hey,

Most likely your data disk is not 'sdb1'. (adjust as required applies).

Show me the output of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
and we see if we can indentify the data disk/partition.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-05-04
Bashing:  The re-boot hung again.  Darn.  Can you help me with a clean reinstall, or suggest a resource for that?


Regarding the data drive, here is the output of those commands:

-----------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007ead8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   118290431    59144192   83  Linux
/dev/sda2       118292478   156248063    18977793    5  Extended
/dev/sda5       147863552   156248063     4192256   82  Linux swap / Solaris
/dev/sda6       118294528   147861503    14783488   83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    31266815    15633392    c  W95 FAT32 (LBA)

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG HD080HJ/ (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  60.6GB  60.6GB  primary   ext4            boot
 2      60.6GB  80.0GB  19.4GB  extended
 6      60.6GB  75.7GB  15.1GB  logical   ext4
 5      75.7GB  80.0GB  4293MB  logical   linux-swap(v1)

Model: ATA ST33000651AS (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  3001GB  3001GB  ext4


Model: SanDisk USB Flash Drive (scsi)
Disk /dev/sdc: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  16.0GB  16.0GB  primary  fat32        boot, lba

ubuntu@ubuntu:~$ 
--------------------------------------------------------------------------------------------------------------------------

---

### Post by Bashing-om on 2014-05-04
ss1133xx; Well;

data drive:

As you said it is GPT partitioned - good ! - and is identified as device 'sdb1'.

so ok, let's take a look at it in terminal:
```

sudo mkdir /mnt/access
sudo mount /dev/sdb1 /mnt/access
ls -la /mnt/access

```
(maybe you do not presently have permissions to access the file system ?, we will see)
so now what do you want to access at that mount point that is revealed by 'ls -la ' ?

(UN)mount the file system when done.
```

sudo umount /mnt/access

```
----------------

As to holding your hand to (RE-)install the operating system, sure ! .. not a problem.
But again, that is the nuclear solution. Just because I am at my wits end to understand why the system fails to boot, others may have greater insight.
That would entail beginning all over again with their thought process to attempt to isolate the problem. As much as I would like to know, I am at my wits end here as I do not know how to see what normal.mod is up to.

It is your call. I can holler for direct assistance and see what my compatriots can come up with. - If you desire to find a less drastic solution - .

---

### Post by ss1133xx on 2014-05-04
Hey Bashing:

--------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ ls -la /mnt/access
ls: cannot open directory /mnt/access: Permission denied
----------------------------------------------------------------------------------------

As you speculated, I apparently don't have "permission" to access the data drive.  I could access it fine before things went haywire, so not sure what the issue is now, or how I can give myself permission.

I appreciate your willingness to continue to try to help me diagnosis my current boot problem, but at this point I think its time to raise the red flag and start over again.  Except for liveUSB, this computer have been out of commission for about two months.  Ubuntu worked great for several months before that, and starting over sounds like my best chance to get it working again soon.

If you are willing to help me go nuclear, that would be great.  I've really appreiated your patience and thoroughness with this process.

Let me know abotu the nuke option.  Thanks.




-

---

### Post by Bashing-om on 2014-05-04
ss1133xx; OK.

Permissions:
```

sudo chown -R ss1133xx:ss1133xx /mnt/access

```
where 'ss1133xx' is the username you use.

OK, the grand RE-install. Back up all data you want as well as any particular .config changes you have made and want to keep.
Then are we going to do this the easy default way - so that the new ubuntu is the sole only operating system installed or "something else" ?
Now, I have nothing against doing it the easy way IF ubuntu is the sole operating system.

[INDENT][INDENT]throwing in the towel
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-05-04
Bashing:

Getting an error message:  "chown: invalid user"

Is it looking for a username for the liveUSB?  If so, I don't have one (didn't create one) or it is the default.  (I tied "default:default" but it didn't work.)   I used by username for my regular ubuntu (and Mint) installs, but it came bak invalid.  Suggestions?

A siImple reinstall sounds good to me --- it worked for the initial install and then for several months afterward.

I don't have a way to back up my 3tb data drive -- one, I can't access it at the moment, and I don't have another drive that large.  But I'm not expecting the installation to touch sdb, so thinking I can safely proceed.  Am I right?

---

### Post by Bashing-om on 2014-05-04
ss1133xx; Humm.

Let's find out who does own the data partition;
```

sudo mkdir /mnt/access
sudo mount /dev/sdb1 /mnt/access
sudo ls -la /mnt/access

```
By golly you should have permission now !

And yes, being aware of what is being done, will not touch the data drive.
In that actual install process, terminal command:
```

sudo parted -l

```
Just to make sure making sure that sdb is still seen as the data drive sdb.
And make doubly tripply sure what the liveUSB is recognized as !
There are times that the liveUSB gets recognized as 'sda' and grub does not install where one would expect it.
So pay close attention to that "parted -l " output, that things are installed in accord with what the system recognizes.

Preferably the system sees
sda -> 1st hard drive s
sdb -> 2nd 3TB data disk
sdc -> liveUSB....
BUT it may not ! Be aware of what we are working with as the system presently sees it.
A usb drive CAN change everything. When you Boot up the liveUSB to install, it is foreseeable that the liveUSB will be recognized 1st and assighned the value 'sda', you will have to accept and adjust to it - see what the 1st hard drive is now labeled and the data drive.
Write them down, a short pencil here beats a long memory, hands down.

Click on the desk top icon "install ubuntu";
Make sure the installer is pointed to sda ( if that is what "parted -l" relates as that 1st hard drive) at the top of the screen;
Choose the option " erase disk and install ubuntu"
Do Not check the boxes for "install updates" OR "install 3rd party software" ( we will do that after the install)
In the install process is an advisory where grub will be installed onto, make sure that this location is 'sda' ( again, IF "parted -l" relates that sda is the 1st hard drive ); I do mean 'sda' NOT as in sda1. - 

OK so far, then is but a matter of answering the few  keyboard, location and user questions, and done. ->
Ubuntu will be installed as the only Operating System using that entire disk for it's self. The install wizard will take care of all partitioning, setting up "root", with /home  and all other directories contained underneath "root", and as well as the "swap" partition. easy peasy.

Reboot into your new ubuntu.

[INDENT][INDENT]noth'n to it
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-05-05
Bashing:  Below is a subset of the output.  I'm not clear on how to read it -- is "drwx" the username?  I don't recall ever using that name.

------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo ls -la /mnt/access
total 318764
drwx------ 24 1000 1000      4096 Mar  9 23:24 .
drwxr-xr-x  1 root root        60 May  5 03:48 ..
drwxrwxr-x  2 1000 1000      4096 Mar  4 08:13 linux software
drwx------  2 1000 1000     16384 Sep 14  2013 lost+found
drwx------  7 1000 1000      4096 Oct 21  2013 Microsoft win and office
drwx------ 63 1000 1000      4096 Nov 30 10:26 Movies
drwx------  5 1000 1000      4096 Feb 18 03:44 .Trash-1000
drwxrwxrwx  2 1000 1000      4096 Oct 23  2013 virtual share
------------------------------------------------------------------------------------------

One issue I recall from back when ubuntu was working fine -- I was unable to delete some files from my trash (to free up disk space) -- it reported that I didn't have access or authority or something, I couldn't fugire out how to give myself authority.

After running your commands, I still don't have access.  I don't get it.
========================================================

Regarding a reinstall, here are the results of "sudo parted -l"


ubuntu@ubuntu:~$ sudo parted -l

Model: ATA SAMSUNG HD080HJ/ (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  60.6GB  60.6GB  primary   ext4            boot
 2      60.6GB  80.0GB  19.4GB  extended
 6      60.6GB  75.7GB  15.1GB  logical   ext4
 5      75.7GB  80.0GB  4293MB  logical   linux-swap(v1)


Model: ATA ST33000651AS (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  3001GB  3001GB  ext4


Model: SanDisk USB Flash Drive (scsi)
Disk /dev/sdc: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  16.0GB  16.0GB  primary  fat32        boot, lba
--------------------------------------------------------------------------------------------------

Looks like i'm good to go -- the liveUSB is sdc, date drive is sdb, and os drive is sda.

Ok, here goes.  I'll send this, then "install ubuntu" and report back.

Thanks.

---

### Post by Bashing-om on 2014-05-05
ss1133xx;
A quicky, and I will respond to the others,

When you boot up to make the install .. using the liveUSB ->
MAKE sure that the usb drive remains as sdc
Check once more before pulling that trigger,

[INDENT]go for it
[/INDENT]

---

### Post by Bashing-om on 2014-05-05
ss1133xx;; Hey,

Hope hings went well, I had intended to wait up for ya and see, but the eyes and brain say otherwise.

I check om my morrow on how thing s progress,

[INDENT][INDENT]movin'n on up
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-05-05
Hi Bashing:  thanks for checking in.  I reinstalled -- so have ubuntu on the boot again -- it  seems a little quirky -- e.g. device list only shows sdb, not sda, mouse & keyboard froze up once, cut & paste didn't work at first, movies won't play, the drive used to spin down after the boot before, but now soins constantly, etc.  Maybe just some getting to to.  Anyway, I'm sort of back in action.

Any suggestions for next steps?  ("install updates" OR "install 3rd party software" ( we will do that after the install)).

Thanks.

---

### Post by Bashing-om on 2014-05-05
ss1133xx; Yeah !

OK, the new install went nicely, let's take care of those little left over things.

Terminal commands:
```

sudo apt-get update ##syncs your system data base with that of your mirror site##
sudo apt-get upgrade ##updates the installed software to what is current in your mirror site##
sudo apt-get dist-upgrade ##new kernels will be installed##
sudo apt-get install ubuntu-restricted-extras ##now movies will play !##

```

And now you should be all set to go > You are invited to advise otherwise.

[INDENT][INDENT]a fresh new start, all things are possible
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-05-05
Hey Bashing:  

All that seemed to work great -- movies now playing.  Thank you.

Regarding the boot problem we worked so hard to resolve,  is there a chance it is caued by a corrupted or infected harddrive?  Is there an app I can use to test the drives for corruption or infection?

Any ideas why sda does not appear in my devise list?

Thanks, appreciate your continued support!

---

### Post by Bashing-om on 2014-05-06
ss1133xx; looking good !

As to why sda no longer appears, will have to do some poke'n see what is.

Checking the hard drive, I was sure we had;
a) disk utility -> S.M.A.R.T 
b) file system check/repair -> fsck which is the front end for e2fsck.
c) any other doubts -> testdisk.

It is past my thinkability, so we will pick this up at a later time.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-06-02
Hey Bashing, hope all is well.

I'd like to follow up on a couple of post-reinstall questions if you have the time and inclination to assist:

1.  [COLOR=#000000]sda does not appear in my devise list, so I'm not sure how to explore the contents of that drive.  (It used to appear.)[/COLOR]

[COLOR=#000000]2.  The pc routinely freezes up when left unattended for a period of time.  For example, I boot it up, use it, then go run errands.  When I get back, the screen is frozen, mouse does not respond, etc.  Seems surprising for an server OS.  Not sure what the cause is.[/COLOR]

[COLOR=#000000]3.  "suspend" function no longer works.  It used to work, before the boot-up issue that you helped me with.  It takes awhile to boot, whereas when it worked, it woke from suspend very quickly.  So I used to use suspend a lot.[/COLOR]

[COLOR=#000000]Any suggestions for me?  

[/COLOR]

---

### Post by Bashing-om on 2014-06-02
ss1133xx; Hey,

Yeah, I am still around, doing well - Thank you.

On a new install it seems strange for sure.

1. What does - maybe the device that held the identifier 'sda' has been reassigned to another - 
```

sudo blkid
sudo fdisk -lu
cat /etc/fstab

```
relate for device identifications ?

2. For starters, disable the screensaver and see what results (maybe #3 related ?).

3. For suspend, what is "swap" doing ?
What returns from :
```

free

```
Maybe all these are swap related ??

How about you close this thread as the original problem is at an end and begin a new thread on each of these new situations. If repairing swap is not the solution.
Thread decorum is one problem to the thread - a lot like dead men -> one to a box .
One item to one thread makes maintaining the forum ( and searching within the forum ) much easier.

It is 
[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-06-03
hey Bashing:  Thanks for quick reply and glad to hear you are well.  

Here you go.

sudo blkid
```
/dev/sda1: UUID="9ca92e8e-1e1a-4da6-8181-ac6f4cd9f72c" TYPE="ext4" 
/dev/sda5: UUID="cb1aac16-4fdf-4e56-bc4b-51f4cf4ca665" TYPE="swap" 
/dev/sdb1: LABEL="3tb" UUID="26379550-f63e-470b-b4b0-c2cbec851d30" TYPE="ext4" 
/dev/sdd1: UUID="8E44-4632" TYPE="vfat" 
/dev/sdc1: LABEL="500gb" UUID="DC6EF0E36EF0B77C" TYPE="ntfs" 

```

sudo fdisk -lu
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00044121


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   147861503    73929728   83  Linux
/dev/sda2       147863550   156248063     4192257    5  Extended
/dev/sda5       147863552   156248063     4192256   82  Linux swap / Solaris


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT


Disk /dev/sdd: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007a4ec


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          32    31266815    15633392    c  W95 FAT32 (LBA)


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf87b4c9a


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976768064   488384001    7  HPFS/NTFS/exFAT
nada@nada-HP-xw8400-Workstation:~$
``` 


```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9ca92e8e-1e1a-4da6-8181-ac6f4cd9f72c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cb1aac16-4fdf-4e56-bc4b-51f4cf4ca665 none            swap    sw              0       0

```

Re:  "disable the screensaver"

Do you mean the the Lock function under "Brightness and Lock" setting?  (If so, ok, I did that.)

free
```
total       used       free     shared    buffers     cached
Mem:       4133224    1287376    2845848          0     101756     553708
-/+ buffers/cache:     631912    3501312
Swap:      4192252          0    4192252

```

Any suggestions for a new thread -- that is, which forum, and which subcategory?

Thanks for assist.

---

### Post by Bashing-om on 2014-06-03
ss1133xx; Hey;

First glance it do appear that "swap" is not set up properly.

I am presently thinking impaired (Minor surgery) --- help me please and edit that post and place those outputs between code tags so I can see the format and so it maintains the readability.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]then
[INDENT][INDENT][INDENT]will see what we can do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by deadflowr on 2014-06-03
Please use [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168") when posting output from the terminal.
Makes it easier to read.
Thank You

---

### Post by Bashing-om on 2014-06-03
@ deadflowr; Thanks, adding the code tags helped bunches.

@ ss1133xx;
> 
/dev/sda5       147863552   156248063     4192256   82  Linux swap / Solaris

Your swap partition is ->h u g e<- . on a factor of 10; encompassing  the entirety of that 'extended partition'.
How much ram do you have installed ? -> You can activate all the applications you normally use ( and youtube too !) and with all active run the 'free' command and see what the swap usage is then, to get an idea of what the swap size should be - making that swap just a tad bit bigger than the amount of ram you have on board to accommodate the suspend function.

I would give some serious consideration to (RE-)installing once more, after due consideration of a partitioning scheme for how I use the system - maybe a data partition and as well perhaps a 'shared - NTFS - partition to share with Windows. Might even go so far as to partition the hard disk in accord with the other hard disks as GPT. A bit more complex, and some additional home work to do to make that happen; but I bet in the long term worth that extra effort.

Perhaps a (RE-)install will resolve all the current issues. 

Else: Make do with
[INDENT][INDENT][INDENT]what we got to work with[/INDENT][/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-06-04
Hey Bashing:  I have 4 gb of RAM.  I didn't set the size of the swap file.  See your post 125, concerning the install wizard, which I followed:

```

Click on the desk top icon "install ubuntu";    
Make sure the installer is pointed to sda ( if that is what "parted -l" relates as that 1st hard drive) at the top of the screen;  
Choose the option " erase disk and install ubuntu"   Do Not check the boxes for "install updates" OR "install 3rd party software" 
(we will do that after the install)
***
OK so far, then is but a matter of answering the few keyboard, location and user questions, and done. ->
Ubuntu will be installed as the only Operating System using that entire disk for it's self. The install wizard will take care of all partitioning, setting
up "root", with /home and all other directories contained underneath "root", and as well as the "swap" partition. easy peasy.

```

So I don't know why the install set the swap to a larger than normal size.  (Any thoughts on that?)

What are the implications of a large swap file?  Which of the issues I asked you about do you think the swap file may be effecting?

FYI:  I recently installed Ubuntu on a laptop, using the same same install wizard instructions as those above, and the swap file on the laptop is also set to the size of the extended partition:

```

sudo fdisk -lu


 Device     Boot       Start         End          Blocks      Id    System
/dev/sda1   *          2048    152127487    76062720   83    Linux
/dev/sda2       152129534   156301311      2085889     5    Extended
/dev/sda5       152129536   156301311      2085888   82    Linux swap / Solaris

```

Appreciate your thoughts.

---

### Post by ss1133xx on 2014-06-05
Any suggestions for me, Bashing?

---

### Post by steeldriver on 2014-06-05
Not sure I'm following here... 4192256 blocks of 512 bytes is a 2GB swap, no?

---

### Post by Bashing-om on 2014-06-07
ss1133xx; Yikes !

I have not a clue what is taking place.
Let me reboot into a couple of standard installs - later - and make some comparisons from them.
FYI My working install with 4 Gigs of ram:
```

sysop@1310mini:~$ free
             total       used       free     shared    buffers     cached
Mem:       4049060     977556    3071504          0      71912     544708
-/+ buffers/cache:     360936    3688124
Swap:         7996          0       7996
sysop@1310mini:


sysop@1310mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
<snip>
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
<snip>

```

I am adding this to the list of things to look at, and later I may know more.
__________
This is my later

My little bitty swap partition that I was - in error - doing the comparison to !

My homework done and here is the skinny.
Fdisk block reports from the kernel @ 1024 byte write cycles resulting in 4 gigs for the extended partition as well as for the swap partition.
4192256 blocks @ 1024 bytes
4292870144 Bytes
4192256 KB (as expected now)
4094 MB
3,99805 GB
Which agrees with what 'free' reports in KB.

As swap does not appear to be at fault. I do not know at this time where to look for a fault.

How about starting new threads and we will continue to explore, see what we can come up with.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by ss1133xx on 2014-06-08
Hi Bashing:

Before opening a new thread, can you help me with this question from an earlier post:

1. sda does not appear in my device list (after reinstalling), so I'm not sure how to explore the contents of that drive. (It used to appear in the list.)

Did you set the swap size manually, or (like me) let the install wizard set the size?

As for a new thread, any suggestions for an appropriate sub-forum?

Thanks.

---

### Post by Bashing-om on 2014-06-08
ss1133xx; Hey,

I can try to help with that question, but this may get involved trying to determine what files systems have been misplaced.
Your reference as to 'sda' not appearing is unjustified.

> 
1.
/dev/sda1: UUID="9ca92e8e-1e1a-4da6-8181-ac6f4cd9f72c" TYPE="ext4" 
2.
Disk /dev/sda: 80.0 GB, 80000000000 bytes
3.
# / was on /dev/sda1 during installation


As the drive is known as 'sda' please explain your terminology "sda does not appear in my device list" -> 'sda' is a hard drive, and what gets displayed - if the reference here is in the file manager - is  the partitions on that hard drive. Now it may be that your partitions are no longer "automounted" and currently the only way you can access those partitions is through the file manager . But that again is a subject to be addressed in another thread.

Now as to my swap partition, I did set up my partition scheme in gparted manually, prior to installing.

And for a place to start new threads, as you are comfortable with the operating system; General Help will be just fine,
Starting new threads - one for each issue - will garner a new audience to expose the issues to and get a faster response.

[INDENT][INDENT]I expect to see you there
[/INDENT][/INDENT]

---

