---
title: "Dual boot on Asus g75vx laptop with win 8"
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by Elssha on 2013-04-12
Hi, 
   As is apparently commonplace, win8 has made it a tragedy to dual boot another OS into it. 
Unaware of this, I bought a new laptop with win 8 (they didn't have 7 anymore >_<). 
Asus g75vx-bhi7n11 to be exact.
Now, I've read a whole bunch of things on how you can apparently install ubuntu... however that only took me far enough that now I have a boot menu (metro-style) that lets me pick b/w windows and 'ubuntu', though there is no workable installation of ubuntu installed. 
When I put in a liveUSB, i can go to the point where you can select try/install/etc (black/white, not the pruple)... but no matter what option I pick, it just hangs. 
Any ideas would really be appreciated, as metro is literally driving me insane. Thanks!

---

### Post by oldfred on 2013-04-13
Is this an UltraBook?

Have you installed, but it is not working or are you having issues booting live installer?

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

IF you have Installed:


 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Another Asus
 Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

---

### Post by Elssha on 2013-04-16
Thanks for the reply ^_^
The computer is from their gaming line (don't think that qualifies as an ultra book); [specs]("http://www.bestbuy.com/site/Asus---17.3%26%2334%3B-Laptop---8GB-Memory---1TB-Hard-Drive---Black/7674057.p?id=1218858193064&skuId=7674057")
No, I don't think it ever installed... just shows a boot choice menu with Ubuntu as one of the options. Of the 50gb partition I set aside for ubuntu (through win8), all but 640kb is shown as free space (and formatting it did not change the outcome, which I tried after reading your post), and selecting the 'ubuntu' option there doesn't do anything (either restarts or makes the comp hang... I forget which).  
I followed several online outlines of what to do and unfortunately didn't keep track of them all. Of the ones that I had bookmarked, I can point out where stuff has failed though. 
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system") I followed the first answer (the one that starts with "Before explaining the steps to do it I want to be clear") and it worked all the way up to the actual installation (I think this is where I got the 2nd boot option from). From this article I went to the the UEFI article mentioned in the post;
[https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI"); problem occured at #3 where selecting "try ubuntu" (or any of the others) just ends in my comp hanging in a black screen. 
[http://ubuntuforums.org/showthread.php?t=2058444]("http://ubuntuforums.org/showthread.php?t=2058444") I tried this as well (the trick with arrows, etc), but nothing kept my computer from hanging as soon as I told ubuntu to run(try) or install. 
I have tried a cd of 12.04, a usb of the 32 and 64 bit as well as the 64bit secure 12.10 that some other installation instructions insisted might work better.
I have looked through the things you posted and still can't get linux to install. Any further help would be greatly appreciated ^_^

---

### Post by oldfred on 2013-04-16
If you have nVidia, you need the nomodeset parameter to boot live installer and on first boot after install.

With UEFI you get the grub menu on live install which is more like the first boot than the BIOS based installer.
You have to use e on grub menu, and on linux line replace splash quiet with nomodeset. Some new computer also need other boot parameters also but that varies are lot.

 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Do not attempt anything other than the 64 bit versions as they are the only ones with UEFI drivers. And only the newer 12.04.2 or 12.10. I cannot just yet suggest 13.04 as it still is beta and you may have other issues, but many are reporting it currently works pretty good. But with beta software fixes are still being added.

Once installed you have to make sure you have headers installed before installing nVidia or any other proprietary drivers.

 # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

---

### Post by Elssha on 2013-04-17
Hi, 
I tried what you said and it nearly did the trick (though as I did not have the graphic purple menu, I did have to hunt down how to do it when F6 did not do anything). 
This got me most of the way there; I now have ubuntu installed on the computer. However, I can only access the terminal version of it. when I use the same trick I used to circumvent the F6 to start in nomodeset (namely using 'e' to edit the load and replacing the splash file with "nomodeset" at the end of the line in /linux as described [here in post #8]("http://forums.opensuse.org/english/get-technical-help-here/pre-release-beta/476744-how-does-one-do-nomodeset-grub2.html")), I get the purple ubuntu bootloader (with the orange dots), followed by a black terminal screen asking for my login and password. I ran sudo apt-get update in this mode, but I'm not great with code and couldn't figure out how to jump from this into a regular OS GUI. When I tried booting into Ubuntu without the nomodeset change, it hung in the purple load screen once all the dots lit up orange. The version of ubuntu I installed is the linux secure 12.10 64bit and the installation process itself was the normal graphic walkthrough I was used to from other Ubuntu installs. Any idea how to revert linux to the normal experience? My command line skills are nearly non-existant >_<

A second problem came up as well, though at this point it is a secondary matter;
The grub bootloader does not load windows, only the binary thing...  though hitting esc at startup (also how I jump into bios) gave me boot options in a bios-like window that let me pick windows or one of two grub loaders (no clue why there are two). Going to the windows loader loads the blue metro loader, which then gives me win8 and ubunu options I had before (the ubuntu option still being useless). This one is more of an annoyance than anything, though I would like to resolve it to where the metro windows loader boots win8 (as it does now) *and* ubuntu, if at all possible... or at least have the grub menu load directly into win8 and ubuntu.

---

### Post by oldfred on 2013-04-17
Post new link to BootInfo report to see if we can see the chainload entry to Windows. But grub only chainloads to Windows so Windows also has to work on its own or not have any issues itself. Boot-Repair will not repair most Windows issues.

If you can boot Ubuntu to command line that is good. You have Ubuntu and recovery in grub menu. It will add two entries each as you get an updated kernel.

It used to be startx, and that may work, but you are supposed to use lightdm, I think. But it varies depending on desktop you are using.
 startx
#or now preferred to restart gdm, I have seen all of these as preferred but do not know if one is better or not.
sudo service gdm start
sudo /etc/init.d/gdm restart
sudo start gdm
sudo start lightdm
# Since Ubuntu 11.10 use lightdm in place of gdm in earlier versions. So the command would be 
sudo service lightdm restart

If you have nVidia you can install from command line:

 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

### Post by Elssha on 2013-04-17
Hi, 
I don't think I explained just what it is I see properly... 

When I hit esc, I get the following blue screen, with the last option taking me to bios; 
[IMG]http://img.photobucket.com/albums/v305/elssha/20130417_173702.jpg[/IMG]
as you can see, there are two entries for ubuntu, both of which do the exact same thing (as far as I can tell, anyway). I did not know what the sequence behind them was (all exactly the same), which is why its blacked out just to be safe. 

When I hit either ubuntu option, I am taken to a screen very similar to the purple screen below (I did not take my own pic of this one), though I don't think I have the memtest options, nor the older version option (obviously); 
[IMG]http://ideasnet.files.wordpress.com/2011/11/ubuntu-11-04-nuovo-grub-2.png?w=645[/IMG] 
I assume these are the two ubuntu options you think I meant. Also, from this screen, though win8 appears.

When I chose the windows option from the first picture above, I am taken to the following, with the ubuntu option seen on the picture going nowhere at all, but the windows option taking me to a working version of win8;
[IMG]http://img.photobucket.com/albums/v305/elssha/20130417_174152.jpg[/IMG]



I tried running the bootInfo as per the link in your earlier post; no luck. Going through the liveUSB tells me I don't have it (and trying to install it fails), going through the actual ubuntu install (still in command line) also failed.

Startx is not seen, and running lightdm restart produced the following, with all the right-sided 'starting' lines at the bottom having an [OK] on the right side (sorry for the quality);
[IMG]http://img.photobucket.com/albums/v305/elssha/20130417_173547.jpg[/IMG]

---

### Post by oldfred on 2013-04-18
Not sure why you are getting two ubuntu entries in UEFI menu. But UEFI menu remembers older things and has to be separately maintained. There should be another place to edit entries.
One user posted this on adding, editing and another wanting deletion:
      >  Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 
And to remove entries as UEFI remembers them.
UEFI system only shows ubuntu. Delete ubuntu entry & reboot a couple of times & it resets to defaults including drives & USB ports.



Have you tried recovery mode or second line in grub menu? That gives choices to continue normally, update, and do some other things. I think it includes nomodeset now as standard.

You may need other boot options, but that requires trial & error unless  someone else with the same system has posted something.
See grub menu further down on editing grub menu with e and adding nomodeset to linux line.
 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)



Not sure why Windows would show Ubuntu. Did you use EasyBCD? That adds an entry to the BCD, I believe. You can use Windows's BCDedit program to remove it if you want.

A couple of these mention other Boot parameters.
 Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Asus UltraBook - kernel comparisons
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)

Is this a system with dual video or Optimus? Some have to turn off one or the other in UEFI/BIOS to get it to work and then install Bumblebee. If it is just nVidia you need nomodeset and then maybe other boot parameters also.

      
 nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)
Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)
Released 319.12 Beta April 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE)

---

### Post by Elssha on 2013-04-21
okay, so I got ubuntu to install ^_^ 
It took installing and fiddling with several nvidia drivers after which I ran startx again with far happier results. 
Now I just need to figure out how to get wireless >_<

---

### Post by oldfred on 2013-04-21
Glad you got it to boot. What actually worked?

I do not know wireless, but those that do need this info. 

lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt
Now post a new thread and attach (via the advanced editor paperclip icon) the abs-network.txt file which will be in your home folder.

---

### Post by Elssha on 2013-05-02
Sorry for the long wait time; been busy. 
Never did get the wireless to work (I will follow your advice as to that file). Also, one other problem came up; I can't access my data partition. I get the following error
[IMG]http://img.photobucket.com/albums/v305/elssha/Screenshotfrom2013-05-0116_54_30.png[/IMG]
As for what worked, it turned out to be a nvidia issue (like you said). I DLed a whole bunch of drivers and finally the startx command jumped me right into desktop. I haven't tackled the boot error, so I still have the weird thing with multiple boot up screens and extra steps -__-;

---

### Post by oldfred on 2013-05-02
I do not know anything about Exfat. Except that is a newer Microsoft format. Does Linux even have drivers for it?

 It is proprietary and patent-pending. 
[http://en.wikipedia.org/wiki/ExFAT](http://en.wikipedia.org/wiki/ExFAT)

---

