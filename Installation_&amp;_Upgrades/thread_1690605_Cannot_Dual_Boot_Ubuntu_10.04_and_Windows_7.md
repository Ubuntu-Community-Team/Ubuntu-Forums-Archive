---
title: "Cannot Dual Boot Ubuntu 10.04 and Windows 7"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by Gridwalker on 2011-02-18
Hi there folks,

I switched to Ubuntu back in the days of Breezy Badger and haven't looked back since ... Unfortunately, my current university course requires me to use windows and I have set up windows 7 on an old laptop.

As I don't want to use Windows full time, I have partitioned the 60gb drive into 3 :
[LIST]
[*]30gb Windows 7
[*]5gb Shared Dropbox
[*]25gb Linux
[/LIST]

Before I installed Windows, I had Kubuntu 10.04 running without any problems. The graphics support wasn't great (ATI Radeon Mobile 5700), but it booted and ran perfectly well.

Now, I cannot boot from an Ubuntu live CD. In fact, linux itself seems to have huge problems ... I have tried the latest stable versions of the following Distributions in an attempt to get the system running :
[list]
[*]K/Ubuntu 10.04 (10.10 doesn't support my wifi card)
[*]Mint
[*]Fedora
[*]Mandriva
[*]OpenSUSE
[/list]

All of these distros start to load from their live CD, but freeze whilst loading and never complete booting (no error messages are displayed).

I have managed to boot into Kubuntu using the live CD by turning off APIC and ACPI, but the installer behaves very strangely : the installation stalls and refuses to continue unless I hold down the alt key, or unless I continually move the mouse pointer around.

Once the installation has completed, the system refuses to load ANYTHING when I reboot. I am just presented with a black screen and the hard drive stops spinning. As I know that windows still works, I am forced to swallow my pride and restore the windows master boot record.

I have also managed to install Kubuntu through Wubi, but the performance was terrible and rebooting would disable the laptop screen until I performed a hard shutdown.

I cannot understand why Linux hates my laptop so much : I loathe using windows and cannot bear the thought of using it as my primary OS ... somebody please help!!!

P.S. 
Just because I have been using Linux for a number of years, please don't assume that I know a wide range of console commands. Please talk me through things step by step and let me know what I need to do to give you any information you require ... one of the reasons why I love Ubuntu is that (until now) it just worked.

Any help you can offer will be very much appreciated.

---

### Post by bcbc on 2011-02-18
Booting from a live CD should not be impacted in any way by the OS on your hard drive (or whether you have a hard drive). Check the CD's for errors.

If you had a perfectly good ubuntu working before you installed Windows, then you should be able to get it working again simply by reinstalling the grub bootloader. 

If you can't do it from a live CD you can do it from the wubi install. e.g. boot live CD or wubi. Then identify the partition containing your regular install e.g. /dev/sda5 (change as appropriate - from your description it might be /dev/sda3).
```
sudo mount */dev/sda5* /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot. 

If you need more help then post the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") results.

---

### Post by oldfred on 2011-02-18
I do not know about  the other distributions, but video has been an issue and some new BIOS can cause issues.

First, do you have an Ubuntu installed? If so run this script from the liveCD to see if boot is configured:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

