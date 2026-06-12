---
title: "Install 32 bit 14.04 from USB"
date: 2015-08-08
forum: Installation &amp; Upgrades
---

### Post by WilliamColls on 2015-08-08
I am trying to install the 32 bit version of 14.04 server on a machine that does not have a CD drive. It does support booting from a USB stick.

I created the USB using the "Create Startup Disk" function from the system menu on another Ubuntu machine using the ISO downloaded from ubuntu.

When i try to boot, the machine finds the USB and starts the boot process. It prompts for the default language and key board configuration, then goes into the sequence that tries to identify hardware. Coming out of this sequence, it complains that the CD-ROM cannot be mounted, and drops down into a menu of options. One of the options allows me to execute the ash shell. From there, I can see that the USB drive has been recognised, and is mounted on /media. I can cd into /media, and all the file that I expect to see are there.

As a test I was able to install the 32 bit Kubuntu desktop on the machine from a USB with no problems. (The USB was made the same way, on the same machine)

Is there any way I can convince the installer that everything it wants is on the USB, and proceed with the install?

Thanks for your time.

William.

---

### Post by ubfan1 on 2015-08-08
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
2) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
3) Did you ever do a "memory check" (another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media.

---

### Post by WilliamColls on 2015-08-09
[COLOR=#000000]1) Did you md5sum check the downloaded iso? - Yes - they match
[/COLOR][COLOR=#000000]2) Did you select the media check before trying to install? - No -only works for CD-rom, and there is no cd-rom in this case
[/COLOR][COLOR=#000000]3) Did you ever do a "memory check" (another live-media menu choice) on your PC? Yes - No errors[/COLOR]

[COLOR=#000000]On further investigation, it appears that the install is hard coded to run from a cd-rom. In the menu provided one of the choices provided id to manually load the preseed file. This fails with the message "file:///cdrom/preseed/ubuntu-server.seed cannot be found" [/COLOR]

[COLOR=#000000]So, for now, I consider this as case closed, and will pursue alternative options.[/COLOR]

---

### Post by v3.xx on 2015-08-09
I have not done this with the server iso, but I have with the mini iso using Unetbootin.  Maybe that would be an option for you.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[http://unetbootin.github.io/#other](http://unetbootin.github.io/#other)

This will not work with UEFI.

---

