---
title: "T61P, nVidia 570M, Restricted Driver Dialog"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by deltastrong on 2007-12-25
When I click Administrator Mode in the Restricted Drivers dialog and enter the password, the drivers list is still disabled ("greyed out") thus disallowing any change to driver enabled status.  Any ideas?

Brand new T61P, Gutsy, nVidia 570M...

---

### Post by Pumalite on 2007-12-25
Is this your laptop?:

    * Screen: 15.4-inch WUXGA (1920 x 1200) TFT Display,175 NIT, 500:1 Contrast
    * Processor: 2.4GHz Intel Core 2 Duo T7700 (4MB L2 Cache,800MHz FSB)
    * Hard Drive: 100 GB hard drive (Seagate 7200.1 7200RPM)
    * Memory: 2GB x 1 RAM (PC5300, 667 MHz, DDR2 SDRAM)  4GB max memory
    * Optical Drive: DVD+-R Double layer / DVD+-RW Drive
    * External Ports and Slots: Three USB 2.0, Firewire 400, one ExpressCard slot, one SmartCard Reader, one VGA, one 4-in-1 card reader, headphone / line-out, microphone-in, modem, 1Gb Ethernet
    * Wireless: WiFi (Intel 4965AGN 802.11a/b/g/n), Bluetooth 2.0 w/ EDR
    * Graphics: NVIDIA Quadro FX 570M (256MB)
    * Operating System: Windows Vista Ultimate
    * 9-cell Li-Ion battery (10.8V, 7.8AH)
    * Dimensions: (WxDxH): 14.1" x 10.0" x 1.2–1.4"; 358.4mm x 255mm x 29.8–34.5mm
    * Weight: 6.77 pounds (w/ 9 cell battery, 5.67lbs w/o)

---

### Post by logos34 on 2007-12-25
try:

System>administration>Software sources>make sure 'restricted' repo is enabled

sudo apt-get install linux-restricted-modules-generic-`uname -r`

then go back and enable driver in System>admin>Restricted drivers manager

---

### Post by deltastrong on 2007-12-25
Strange one here.  Turns out I needed to delete the .DCOP* files from my home directory.  Could properly access the dialog in Administrator Mode after that...

Thanks for your prompt feedback!

---

### Post by MountainX on 2008-01-15
I have a T61p with the nVidia 570M and I cannot get Ubuntu 7.10 to install.

My laptop specs are:
My 6459CTO THINKPAD T61 WIDESCREEN-1Y  
INTEL CORE 2 DUO  
15.4 WUXGA TFT  
NVIDIAQUAD FX 570M W/WWAN 

When I try to boot from the Ubuntu CD normally I get a blank display. When I try to use the safe graphics mode I get the following error (after the message "Running local boot scripts (/etc/rc.local)).

Error:
The display server has shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again on display :0.

I have tried all the suggestions I've seen on ThinkWiki here:
[http://www.thinkwiki.org/wiki/Talk:Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Talk:Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61)

(This is actually the 4th computer I have tried to install Ubuntu 7.10 on and all have failed with some kind of display related issue.)

It sounds like someone with a very similar laptop got Ubuntu 7.10 installed. I would love to know how.

---

### Post by Pumalite on 2008-01-15
Have you tried the Alternate CD? ( to avoid graphics problems)
If that doesn't work, try some boot parameters. Here is a guide and a collection to try; one at the time:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)

---

### Post by MountainX on 2008-01-15
Thanks. I'm downloading the alternate CD now... wonder if I should choose the 64 bit version?

I have also discovered that the rescue boot option isn't available on the regular live CD...

I am trying (without success) to following the instructions here: [http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p](http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p)

---

### Post by MountainX on 2008-01-15
The alternate CD has the same graphics problems.
If I can't install from the CD in the usual way, how else can I install Ubuntu?
I don't believe I can utilize the Grub boot menu until Linux is installed. So I'm stuck.

---

### Post by Pumalite on 2008-01-16
At the end of the Alternate CD installation, you can reconfigure your xserver.
Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose vesa as the driver
(Once IN the system, then get drivers and change your settings as you wish)

---

### Post by MountainX on 2008-01-16
I did not see the option to reconfigure the X server at the end of the alternate CD installation. And I had already finished the installation by the time I saw your post.

However, now that Ubuntu is installed, I can get to the Grub boot menu and select the recovery mode option. From there I was able to follow the steps at: [http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p](http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p)

Editing xorg.conf was no problem. But upon rebooting I get the same black screen that changing the driver to vesa is supposed to fix.

I just verified the correct settings by booting into recovery mode again and opening xorg.conf. The driver is specified as "vesa" and my device is the Quadro FX 570M that other people seem to be able to get working.

Next I did sudo dpkg-reconfigure xserver-xorg and went through all the options. The driver was already listed as vesa, as expected.

On rebooting I just get a blank screen. Ctrl+Alt+F1 doesn't do anything.

---

### Post by Pumalite on 2008-01-16
Try a different distro to see if you are incompatible with Linux in general or Ubuntu in particular, and if there is a hardware problem with Ubuntu, there are the boot parameters that you can still try.

---

### Post by MountainX on 2008-01-16
I tried PC-BSD and the vesa video driver worked great at 1920x1200. So the problem seems to be Ubuntu. Most recently I have been trying the 64 bit version (using the alternate CD). I could try the 32 bit version, but I think the person who wrote the article was using 64 bit:
[http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p](http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p)

---

### Post by MountainX on 2008-01-16
I finally got Ubuntu installed on my T61p with nVidia 570M. I wish I could offer some feedback on what made the difference, but it was just a lot of effort and time over several days. No one thing seemed to do the trick except persistence.

---

### Post by dokdoom on 2008-03-17
I'm having the same problem as you, followed thinkwiki's guide, changed the driver to vesa and reconfigured X. How did you get this to work! Don't have the exact same problem as me and not tell me how you fixed it :P

/goes back to googling

---

### Post by MountainX on 2008-03-17
> **dokdoom said:**
> I'm having the same problem as you, followed thinkwiki's guide, changed the driver to vesa and reconfigured X. How did you get this to work! Don't have the exact same problem as me and not tell me how you fixed it :P

/goes back to googling

I suggest you use the alternate CD. I updated the page at ThinkWiki a while back with every suggestion I could offer, based on my experiences.

BTW, the alternate CD does not have the same install problems. When I said that earlier in this thread I was mistaken. (The download link for the Alternate CD was actually giving me the std CD at that time. Once I actually used the Alternate CD, it worked.)

Use the 32 bit version of Ubuntu and use Envy to install the nVidia drivers. That should do it. I even have Compiz working with full visual effects on my laptop. It is really cool. I also have my fingerprint reader working. (My only remaining issue is suspend/resume.)

---

### Post by dokdoom on 2008-03-17
Wow thanks for updating! My google searching wasn't looking very good. I did the install with the alternate CD. I even got X to start within recovery mode (/etc/init.d/kdm start) and it worked. I updated my repositories and installed the Restricted Driver. Then I hooked up my monitor and had twinview working. I restart X several times and it would start over and over again. Once I reboot the system it went back to the same blank screen. I'm using the 64 bit so I don't have to sacrifice any memory.

##Edit

I forgot to mention, during the first start when X is supposed to fail, I logged in to recovery mode and changed the driver to vesa as the thinkwiki guide said. Even with that driver I still got the blank screen. That's when I started messing around in the terminal and started X. Even more weird, I can't start X manually anymore.

---

### Post by MountainX on 2008-03-17
Why don't you try the same things I did to get it working:
1. 32 bit version of Ubuntu
2. Use Envy to install restricted nVidia drivers
3. Make sure you are using the alternate CD -- it is a text-based, non-GUI install.

It sounds to me like you aren't using the alternate CD.

---

### Post by dokdoom on 2008-03-17
I am using the alternate CD but it is the 64 bit version. To make sure it wasn't hardware I just reinstalled with xubuntu 32 bit (alternate CD) and it's working fine. I knew I could get a 32 bit OS on here, it's the 64 bit I'm having a problem with. I'm making another 64 bit .iso right now to make sure it's just the one I used earlier. Thanks for the help!

---

### Post by MountainX on 2008-03-18
I have been extremely displeased with 64-bit Firefox. I do not know of a good 64-bit browser and I was not at all happy with using 32-bit Firefox in the 64-bit Ubuntu. I am much happier with the 32-bit Ubuntu.There is really no comparison in my opinion - 32-bit Ubuntu is a much more enjoyable experience. I'm in the process of removing the 64-bit Ubuntu version from my other computer.

---

### Post by Pumalite on 2008-03-18
Wait until April and you'll love the 64 bit.

---

### Post by adi_8079 on 2008-03-18
Hi, I have also a 6459CTO ThinkPad. I was able to install the 64bit version of Ubuntu 7.10 using the alternate CD, the other 64bit just didn't work.
The graphic card, Quadro FX570M was not automatically recognized so I choosed to install the driver using Envy following [these]("http://www.thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p") instructions. I decided to use the Envy tool as this one installs the latest nVidia driver (169.12) and it worked! If you read the guide carefully, you will notice that the nv driver does not support the latest nVidia 570M, so I wouldn't suggest to enable the restricted driver.
 After reboot, I was welcomed by the nVidia splash screen ;), ok I still had to adjust the resolution to get the right one (1680x1050) but this was done easy, I simply used Nvidia Settings.

Hope this helps. Good luck!

---

### Post by MountainX on 2008-03-18
> **Pumalite said:**
> Wait until April and you'll love the 64 bit.

Well, probably not -- unless Adobe comes out with 64bit Flash at that time.

---

### Post by MountainX on 2008-03-18
> **adi_8079 said:**
> Hi, I have also a 6459CTO ThinkPad.

 If you read the guide carefully, you will notice that the nv driver does not support the latest nVidia 570M, so I wouldn't suggest to enable the restricted driver.

ok I still had to adjust the resolution to get the right one (1680x1050) but this was done easy, I simply used Nvidia Settings.

Hope this helps. Good luck!

I am using the restricted driver with the nVidia 570m and it works great. 

Furthermore, I get the full 1920 x 1200 resolution which I like much better (and it is native for the display)

---

### Post by McLogic on 2008-04-26
> **MountainX said:**
> I am using the restricted driver with the nVidia 570m and it works great. 

Furthermore, I get the full 1920 x 1200 resolution which I like much better (and it is native for the display)

Is Hibernate working?
Is Suspend working?
Do you have Intel or non-Intel wireless?

---

### Post by MountainX on 2008-04-26
> **McLogic said:**
> Is Hibernate working?
Is Suspend working?
Do you have Intel or non-Intel wireless?

To answer your three questions:
no, no and Intel 3945ABG

---

### Post by adi_8079 on 2008-05-01
> **McLogic said:**
> Is Hibernate working?
Is Suspend working?
Do you have Intel or non-Intel wireless?

Suspend worked in Ubuntu 7.10 (64bit), see [here]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend"). I was not able to get it work in Hardy (64bit) :(
I haven't try Hibernate :)
WiFi: Intel 4965AGN 802.11a/b/g/n, worked out of the box.

---

### Post by MountainX on 2008-05-01
> **adi_8079 said:**
> Suspend worked in Ubuntu 7.10 (64bit), see [here]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend"). I was not able to get it work in Hardy (64bit) :(
I haven't try Hibernate :)
WiFi: Intel 4965AGN 802.11a/b/g/n, worked out of the box.

Would someone be kind enough to explain [that link]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend") to me.

It looks to me like the problem is related to TwinView and no one has a fix for that...

"Note: enabling TwinView breaks suspend-to-ram (reported to work with drivers 96XX), if you know better please delete this note and write how you did it."

---

