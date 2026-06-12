---
title: "Installing 10.04 LTS on Dell Latitude E6410"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by kidzer0 on 2010-07-09
I'm trying to install 10.04 LTS on my Latitude E6410. I've tried installing it inside of Windows and it installs - yet when I select it on boot - I get a black screen after the "Press ESC...".

Is it not compatible with the E6410? Any ideas?

---

### Post by Mark Phelps on 2010-07-10
Don't know ... that's what LiveCD mode is for ... to find out IF Ubuntu is compatible with your PC -- BEFORE you install it.

---

### Post by wgarcia on 2010-07-15
I have it perfecly running on this model. If your graphics card is NVIDIA, read the notes here to start the graphics session:

[https://wiki.ubuntu.com/Testing/Laptop/Lucid/Reports/DellLatitudeE6410](https://wiki.ubuntu.com/Testing/Laptop/Lucid/Reports/DellLatitudeE6410)

---

### Post by anrange on 2010-07-16
Hi, I was able to install it (if you have one with the nvidia card)using the alternate install cd.
Just install it normally 

Once it boots, connect an external monitor from the vga port and the content will be displayed there. then follow and installed the proprietary nvidia drivers and voila you are ready.

Now I am trying to get the card reader,the webcam and the microphone to work

---

### Post by rpd_linux on 2010-07-17
Hi. I also manage to install Ubuntu 10.04 LTS on my Latitude E6410, by using this tutorial: [http://blog.katharsys.com/?p=931](http://blog.katharsys.com/?p=931)
After installation you need to reboot, so the black screen reappears. To have access to the login on the screen, you should connect an external monitor from the VGA port and then reboot the system. In this way you will be able to access the login. Login then install the proper NVidia driver (System -> Administration -> Hardware Drivers)
Good Luck!

---

### Post by kidzer0 on 2010-07-28
I have the Intel-Based model. :(

---

### Post by bach on 2010-08-25
See 

[https://bugs.launchpad.net/bugs/561802](https://bugs.launchpad.net/bugs/561802)

and also 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453)

---

### Post by GenBattle on 2010-08-25
I had a similar problem with my machine. Took me a week to figure out how to install ubuntu because the liveCD/USB wouldn't boot.

The solution for me was to edit the GRUB boot entry (it should say something on startup about pressing e to edit an entry).

Options to try:
[LIST]
[*]Add "xforcevesa" to the kernel line
[*]Add "acpi=off" to the kernel line
[*]Add "noapic" to the kernel line
[*]Add "i915.modeset=0" or "i915.modeset=1" to the kernel line
[*]Add "nomodeset" to the kernel line
[*]Remove "splash" and "quiet" from the kernel line
[/LIST]

The problem with this issue is that is has a wide range of root causes. From the sounds of your hardware (an intel graphics card) i would try adding "i915.modeset=0" or "i915.modeset=1" to your kernel boot line first. If that doesn't work try each of the options i listed above, or some combination of them.

Personally for me the solution was "xforcevesa" with a radeon graphics card, but i only had to do this for the install (first boot worked fine).

Also note you should be able to access GRUB by pressing F6 on boot, if it isn't shown by default.

---

### Post by dentharg on 2010-09-08
Install kernel from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.4-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.4-maverick/)

Black screen is gone :)
I have dual screen working like a charm.

---

### Post by elewis on 2010-09-13
dentharg's suggestion worked for me. I tried every permutation of sending the strings, "i915.modeset=0, i915.modeset=1, nomodeset, xforcevesa, acpi=off and noapic" against the standard Lucid kernel (2.6.32.24-generic) to no avail. They all resulted in a black screen.
The only problem (it is a major problem) with the 2.6.35-4-maverick kernel is that as a "mainline" kernel, the ability to use the computer's broadcom wireless card is compromised. The broadcom card does not work.
At least video works; I will end up using cable connection for the time being until a kernel that supports broadcom wireless is developed.
Thanks for good work!

---

### Post by dentharg on 2010-09-14
Hi!
Using this kernel I also have working wireless.

---

### Post by gorthx on 2010-09-22
This kernel fixed the blank screen issue for me as well.  (Although I still can't use an external monitor.)

Thanks!

---

### Post by dentharg on 2010-09-23
Hm.. I'm using 2 external monitors but via docking station.

---

### Post by Aitaix on 2010-09-26
i have a latitude e6510 and I am getting a black screen on first boot up :(


my only options that I can try and that I have were

[LIST]
[*]Add "acpi=off" to the kernel line
[*]Add "noapic" to the kernel line
[*]Add "nomodeset" to the kernel line
[/LIST]

I tried pushing and/or holding down the "e" key during first start up but that didn't bring up the GRUB menu for me. 

What else to try? I've tried 32 bit version, 9.10 worked for me after some tinkering but then I coudln't get wireless to work. AUGH this laptop is a headache.

---

### Post by stackcheese on 2010-09-26
did you put the nomodeset in the startup option by replacing the the splash/quiet?

---

### Post by stackcheese on 2010-09-27
does anyone know how to fix the high pitch screech/noise when you restart/shutdown the computer?

---

### Post by mrodent on 2010-09-27
Dear all,

I am a complete newbie.

I have had utter frustration with installing Ubuntu 10.x or 9.x on my Dell E6410.

Then I tried Ubuntu 10.10 (Beta).  This is the 64-bit variety.

FANTASTIC success.  It seems the problem is the graphics chip, in my case the standard Intel one: it appears that this is very new and the Ubuntu boffins have to work out how Ubuntu is gonna use it.  Perhaps unsurprisingly, they are working this out for the NEXT RELEASE, i.e. 10.10.

For those, like me, who are also utter newbies, and detest, loathe and execrate everything to do with MS (and much to do with Apple too), check out VirtualBox once you have Linux up and running.  This is an amazing app which lets you INSTALL A WXP OS *INSIDE* AN UBUNTU OS.

Hasta la victoria siempre... ¡Hasta Linux!

---

### Post by stackcheese on 2010-10-03
i noticed that my system acts erratically with its shutdown procedures.
it sometimes would do the following:
a) shutdown normally
b) treat it as a restart
c) goes through the shutdown procedures, but it wont completely turn off my system, it would still use power and the power light would still stay blue, but the screen would be black


also anyone have any input on getting rid of the shutdown/restart alert/bell? I've tried adding blacklist pcspkr to /etc/modprobe.d/blacklist.conf file but it still does this loud screech/beep whenever I shut down.

---

### Post by dvandyck on 2010-10-07
> **dentharg said:**
> Install kernel from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.4-maverick/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35.4-maverick/")

Black screen is gone :)
I have dual screen working like a charm.

OK I am willing to try that, but how do I install a kernel from a blank screen? My screen is also blank if I boot in recovery mode...

---

### Post by kgish on 2011-04-13
> **GenBattle said:**
> I had a similar problem with my machine. Took me a week to figure out how to install ubuntu because the liveCD/USB wouldn't boot.

The solution for me was to edit the GRUB boot entry (it should say something on startup about pressing e to edit an entry).

Options to try:
[LIST]
[*]Add "xforcevesa" to the kernel line
[*]Add "acpi=off" to the kernel line
[*]Add "noapic" to the kernel line
[*]Add "i915.modeset=0" or "i915.modeset=1" to the kernel line
[*]Add "nomodeset" to the kernel line
[*]Remove "splash" and "quiet" from the kernel line
[/LIST]

The problem with this issue is that is has a wide range of root causes. From the sounds of your hardware (an intel graphics card) i would try adding "i915.modeset=0" or "i915.modeset=1" to your kernel boot line first. If that doesn't work try each of the options i listed above, or some combination of them.

Personally for me the solution was "xforcevesa" with a radeon graphics card, but i only had to do this for the install (first boot worked fine).

Also note you should be able to access GRUB by pressing F6 on boot, if it isn't shown by default.

Would also like to try these options, e.g. editing the given files, but how can I possibly edit anything when the screen is blank?

---

### Post by matthew.parlette on 2011-04-22
> **kgish said:**
> Would also like to try these options, e.g. editing the given files, but how can I possibly edit anything when the screen is blank?

I'm trying to remember this off the top of my head, but I had this problem with my latitude E6410.

Before I say what fixed it, I just tried the 11.04 beta2 live cd and it booted to the cd just fine, no visual glitches at all. I'll be installing it this weekend, but I would recommend that for now:

[INDENT][http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)
(I recommend the torrent, a straight HTML download would have taken about 7 hours, torrent was 30 mins)[/INDENT]

If you still want to go with 10, then when you boot to the cd, you should see the screen that is black but has the keyboard and icon of the guy down at the bottom. At this point, you need to hit a button (maybe any button) to see a list of options. From there, you can see some options at the bottom of the screen to modify the boot command, where you can then try the options mentioned above.

Let me know if I can help out with anything else there, as I've suffered through the same issues.

---

### Post by kgish on 2011-04-23
I solved my problem by going to the [Dell download page]("http://support.dell.com/support/downloads/download.aspx?c=us&cs=08W&l=en&s=bsdv&releaseid=R284592&SystemID=LAT2120&servicetag=&os=WN104&osl=en&deviceid=26290&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=0&libid=58&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=421648") for Canonical Ubuntu 10.10, where I could download:

[http://ftp.us.dell.com/OS/ubuntu-10.10-i386-dell_A00.iso](http://ftp.us.dell.com/OS/ubuntu-10.10-i386-dell_A00.iso)

Then I burned this to an USB-stick using the UNetbootin utility, rebooted my other laptop (after first reconfiguring the bios to boot from USB first), and installed Ubuntu 10.10 from there.

---

### Post by sammyhood on 2012-02-01
Using i915.modeset=0 xforcevesa worked for me. I have the e6410 with the Intel Video Chipset.

---

