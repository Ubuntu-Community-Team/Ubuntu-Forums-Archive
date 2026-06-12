---
title: "Ubuntu 20.04 LTS locked in 640 x 480 (4:3) Resolution!"
date: 2022-04-02
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2022-04-02
Right now am back into running Ubuntu 18.04 LTS, because 20.04 is practically impossible to use now with its present large resolution.
Booted up into 20.04 today which was running great until today. Now all I get is a large screen with 640 x 480 (4:3) Resolution running/showing! 
Tried going into settings to change resolution back to 1920 x 1080 16:9, which was used before and ran great before, but can't in 20.04! Only choice showing is, 640 x 480 (4:3) Resolution, with no other choice available.

Went into 18.04 settings and have several choices to change resolutions if desired but can't change anything right now when going back to 20.04! Only 640 x 480 (4:3) shows and is running.

HELP!

What is needed to get back to 1920 x 1080 16:9 Resolution with 20.04, as it ran before today?

---

### Post by cybrsaylr on 2022-04-03
20.04 LTS is still locked in 640 x 480 (4:3) Resolution.

On boot up tried using GRUB to go into: 
*Advanced options for Ubuntu 20.04
*Ubuntu ..... Recovery Mode
After it got done scrolling got a screen
Chose; dpkg ... Repair Broken Packages....clicked on that, it did some scrolling on, then settled on a black screen with a white cursor blinking in the upper left hand corner of monitor that just kept blinking and did did nothing.

Hit Control, Alt, Delete, keys and PC went into a normal boot up, starting 20.04 again locked up again in, 640 x 480 (4:3) Resolution! 

Help!

How can I get back into 1920 x 1080 16:9 resolution as before?

---

### Post by Impavidus on 2022-04-03
This looks like a graphics driver problem, so what can you tell us about the graphics hardware on that computer and what can you tell about the kernel in use? What happened that could have triggered this problem? A kernel upgrade maybe? Can you boot Ubuntu 20.04 with an older kernel?

Have a look at /var/log/dpkg.log to see which packages were recently upgraded.

---

### Post by cybrsaylr on 2022-04-03
Impavidus, 

Not sure how to do all that, as am running 18.04 right now which runs fine with, 1920 x 1080 16:9 resolution and can easily go to another resolution if desired.

When attempting to boot 20.04, did try the other two older kernel choices in; *Advanced options for Ubuntu 20.04. Neither one would boot up 20.04.

I do all the updates when they are offered by Software Updater.

Here's some driver info I found. Believe this driver was used forever.

[IMG]https://i.postimg.cc/PrVR4XjP/a.png[/IMG]

---

### Post by cybrsaylr on 2022-04-04
Still stuck using 18.04 because 20.04 is still locked in 640 x 480 (4:3) Resolution.

20.04 shows these 2 kernels when attempting to boot up into 20.04, clicking on *Advanced options for Ubuntu:

*Ubuntu, with Linux 5.13.0-39 generic
*Ubuntu, with Linux 5.13.0-39 generic (recovery mode)
*Ubuntu, with Linux 5.13.0-37 generic
*Ubuntu, with Linux 5.13.0-37 generic (recovery mode)

When attempting boot into generic, both boot up to 20.04 locked in 640 x 480 (4:3) Resolution.

When attempting boot into recovery mode, both do some scan, then end up with a blank black screen with a white blinking cursor in the upper left hand corner of my monitor, that keeps blinking forever with no boot up into 20.04.

Don't know what caused this?

---

### Post by cybrsaylr on 2022-04-04
Been looking to Google and YouTube for some help in this. YT can be amazing.

Could the problem be an old CMOS battery?

Got My i7 PC in signature line below back in 2009 on a Black Friday sale making its CMOS battery over 12 yrs old. Overall this i7 Dell desktop with the addition of a couple SSDs runs better now than when it was new.

However some YT clips state an old CMOS battery can cause a PC to get a bit wonky. Lose drivers, time/date go off having to be reset, trouble booting up and a couple other things needing to be reset.

Thoughts?

---

### Post by him610 on 2022-04-04
You are using nouveau driver.
Try installing nvidia-driver-390.
To display system information in terminal...
```

inxi -Fxxz

```

---

### Post by cybrsaylr on 2022-04-05
him610,
 
Went into Software & Updates > Additional Drivers to try installing nvidia-driver-390 but it won't! Seems that is locked also.
All I could do was not use that Broadcom 802.11 wireless driver listed above. Reboot pc but that had no effect on changing resolution. So I went back to using that Broadcom driver.
That nouveau driver seems locked in also. Can't switch to any of the others listed above.

Did install a new CMOS battery. Pulled out the OEM 3 volt CMOS battery, tested it. It was low, 1.24 volts. So put in a new battery.

---

### Post by ActionParsnip on 2022-04-05
What is the output of:
```

sudo lshw -C display; lsb_release -a; uname -a

```
Thanks

---

### Post by cybrsaylr on 2022-04-05
ActionParsnip, here's the output:

>   *-display                 
       description: VGA compatible controller
       product: GF108 [GeForce GT 630]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:d8000000-dfffffff memory:d6000000-d7ffffff ioport:dc00(size=128) memory:c0000-dffff
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.4 LTS
Release:	20.04
Codename:	focal
Linux t-Studio-XPS-8000 5.13.0-39-generic #44~20.04.1-Ubuntu SMP Thu Mar 24 16:43:35 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux


---

### Post by ActionParsnip on 2022-04-05
If you rebuild the nvidia kernel module for the current kernel, does that help

---

### Post by cybrsaylr on 2022-04-05
Don't know how to rebuild the nvidia kernel module for the current kernel?

---

### Post by cybrsaylr on 2022-04-06
Well since I wasn't getting anywhere solving this issue, decided to just format the partition 20.04 was in and reinstall 20.04 there. Reinstall took 14 minutes, then did all the updates etc, that took a little bit longer. 
Now am in the process of installing about 20 favorite programs and apps.....ugh....

20.04 LTS seems to be back to normal. Going into, settings > displays, now have 1920 x 1080 (16:9) resolution and ability to choose several others. Am not locked into one resolution, as in the OP.

FWIW, have to admit 20.04 has been more buggy than earlier versions of Ubuntu. Have been using Ubuntu since 2007. 
20.04 is running great right now. Hope it continues in my system.

My Dell XPS i7 purchased in 2009 still runs great. In fact since adding 3 SSDs this i7 runs better now than when it was new.  It has 4 operating systems on it and they all run fine. Namely Ubuntu 16.04 LTS, Windows 10, 18.04 LTS and 20.04 LTS are shown on the bootloader. All run fine when selected.

---

### Post by cybrsaylr on 2022-04-20
Well it happened again and because of it am back into running 18.04!

Boot up today and AGAIN, Ubuntu 20.04 LTS locked in 640 x 480 (4:3) Resolution, which is almost impossible to run easily locked in 640 x 480 (4:3) Resolution!

20.04 was running great since my last post in this thread after doing a format and reinstall of 20.04 about a week ago. However after booting up today am stuck again in this Ubuntu 20.04 LTS locked in 640 x 480 (4:3) Resolution!

Anyone have any idea watch may be causing this resolution lockup?

Otherwise it looks like I have to reformat this partition and reinstall 20.04 all over again like I did about a week ago.....

---

### Post by cybrsaylr on 2022-04-21
Anyone got any ideas what caused this and how to correct this locked resolution?

---

### Post by #&amp;thj^% on 2022-04-21
show this please:
```
grep nomodeset /etc/ -rs
```

---

### Post by cybrsaylr on 2022-04-21
> **1fallen said:**
> show this please:
```
grep nomodeset /etc/ -rs
```

Running 18.04 right now.
Do I need to go back into 20.04 and attempt to show the results of: code: grep nomodeset /etc/ -rs

Or can I show it running with 18.04?

Here are results with 18.04:

> b@b-Studio-XPS-8000:~$ grep nomodeset /etc/ -rs
/etc/grub.d/10_linux:    GRUB_CMDLINE_LINUX_RECOVERY="$GRUB_CMDLINE_LINUX_RECOVERY nomodeset"
b@b-Studio-XPS-8000:~$ 



---

### Post by #&amp;thj^% on 2022-04-21
> **cybrsaylr said:**
> Running 18.04 right now.
Do I need to go back into 20.04 and attempt to show the results of: code: grep nomodeset /etc/ -rs

Or can I show it running with 18.04?

Here are results with 18.04:

yes please, that's the problem OS right?

---

### Post by cybrsaylr on 2022-04-21
> **1fallen said:**
> show this please:
```
grep nomodeset /etc/ -rs
```

Here's the results of that code when running 20.04

> ~$ grep nomodeset /etc/ -rs
/etc/grub.d/10_linux:    GRUB_CMDLINE_LINUX_RECOVERY="$GRUB_CMDLINE_LINUX_RECOVERY nomodeset"
/etc/grub.d/10_linux_zfs:        GRUB_CMDLINE_LINUX_RECOVERY="${GRUB_CMDLINE_LINUX_RECOVERY} nomodeset"

---

### Post by #&amp;thj^% on 2022-04-21
Remove all the Nvidia drivers

```
sudo apt remove --purge '^nvidia-.*'

```
run: 
```
ubuntu-drivers devices
```
&#8674;select the **recommended** driver &#8674;Apply Changes &#8674;reboot

---

### Post by cybrsaylr on 2022-04-21
Looks like some success, 1fallen.

Ran your first code to purge nvidia. It ran ok.

Ran second code. It ran but couldn't select any other drivers.

Did that by going into, software updates > additional drivers, making changes as shown below:
Before I could not switch out of Nouveau driver, now I could:

[IMG]https://i.postimg.cc/pXZgBSw-0/Screenshot.png[/IMG]

Originally Nouveau and Broadcom drivers were both shown working.
I removed them and am now using NVIDIA 390 driver.

Reboot and now run 1920 x 1080 16:9 resolution fine as before. Also can make several other resolution changes if desired. Am no longer locked into 640 x 480 (4:3) Resolution, with no way out.

Hope this holds and does not revert back as it did about a week ago to locked into 640 x 480 (4:3) Resolution.

Thanks, 1 fallen

---

### Post by #&amp;thj^% on 2022-04-21
happy to hear that.

---

### Post by cybrsaylr on 2022-04-21
Am quite happy also.
Was saved from going through what was done in post 13, all over again!

---

