---
title: "Access to Grub Menu"
date: 2015-06-30
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2015-06-30
I am installing Ubuntu 14.04 from a live CD but the default driver for the display does not work on my Gateway PC. The shift key does not work on trying to access the GRUB menu. I can get to the Try Ubuntu logo from loading the CD and have managed to get into the GRUB menu but a recent update for Ubuntu seems to have messed up this access.

---

### Post by Bashing-om on 2015-06-30
angel mike; Hey ;

If this is a UEFI system, it is the escape key that grub looks for. As soon as the firmware screen clears, repeatedly depress/release the escape key. There is but a 3 second window for grub to recognize that the escape key is pressed.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by angel mike on 2015-07-01
Thanks for picking up my post once again Bashing-om. I have tried the shift key and the esc but cannot get into GRUB. Following your last set of instructions with the live CD - then booting without it - I cannot get into the terminal using either ctrl+alt+t or ctrl+alt+F1. The latter works when I boot from the CD.

---

### Post by oldfred on 2015-07-01
What are specs on your computer, RAM, video card, cpu?

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by angel mike on 2015-07-02
Thanks oldfred - have run the two sets of code - the first was ok but the second although producing a lot of output failed at some point and did not finish with a $ sign or give a url address. A part sample of the failure lines is : {(glade2script:6050:Gtk-Critical..... 'GTK_IS_STYLE PROVIDOR' failed} and also {/usr/share/boot-sav/gui-g2slaunch.sh:line29:6050 Segmentation fault}
Computer is a Gateway bought 2007 Model GM5066b upgraded to 2GB Memory/Dual Intel Processor 1.86GHZ/Hard Drive 320GB/Video NVIDA Corp G72(GeForce 7300 LE). Using a live CD with Ubuntu 14.04.1 LTS and did manage to get into grub and also to change the video/driver to 304.125 version (proprietry,tested) which worked. But then a few weeks later I used the update manager and lost it all !
For more details about computer and commands used last time see my posts with Bashing-om about 6 weeks ago. I have tried the previous method but the updates I used then must have changed.
The bootup uses the BIOS not a UEFI.
Regards Mike

---

### Post by oldfred on 2015-07-02
How did you install nVidia driver?
If you install from nVidia directly with its .run file, you in effect have to reinstall every kernel update. But if you use Ubuntu repository and System Settings, Software & Updates, drivers tab, it will work with every new kernel automatically.

If you install one way and then want to change to the other way, you must totally purge before reinstalling. Otherwise you get conflicts and problems.

Until I get correct nVidia driver working, I always have had to use nomodeset.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

       
 Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

      
 # only reason to purge is there are several versions, if you know you have different nVidia use that:
Also must make sure parts of old install or persistence issue are not presevered as they are in use.
#To see available versions:
dpkg -l | grep -i nvidia*
#see details for version installed
sudo apt-cache policy nvidia*
dkms status


 #Then for verson installed
sudo apt-cache policy nvidia-3XX-updates 

   sudo mv /etc/X11/xorg.conf /etc/X11/xorg/conf.old
Shows any file with nvidia in name, lots of files.
sudo find / -name "nvidia*"
Shows versions in repository:
sudo apt-cache search nvidia-sett*
Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*

You would then install the correct legacy driver which does seem to be the 304.xx version.

 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)

---

### Post by angel mike on 2015-07-02
Originally after making changes using the live cd (see Bashing-om instructions) I rebooted without the cd and was able to get into grub using shift key (does not work now) and did an edit (see Bashing-om). I was able to get a screen and went into the Open Software sources (Menu) from the Software Center - last tab is 'Additional Drivers' which gave a list of four options - the 304.125 from nvidia-304(proprietry, tested) worked.
Thanks for all the nvidia details but not sure how to use it - have not read in detail. At the moment all I can access is the terminal with the cd loaded. regards
Mike

---

### Post by oldfred on 2015-07-02
If using the CD, you probably also need nomodeset. Link on installer boot screens shows that.

---

### Post by angel mike on 2015-07-02
I cannot get into grub only the BIOS . The computer uses BIOS not UEFI or am I missing something.

---

### Post by oldfred on 2015-07-02
When you reboot, press & hold shift key from first BIOS boot screen, until grub menu appears.

---

### Post by Geoffrey_Arndt on 2015-07-02
Angel . . . on this computer, a different approach may be needed re install.   I would suggest using a distro that does not call/require nvidia graphics to run.   Something that will be happy with the open source driver.   So, perhaps Xubuntu, Lubuntu or even something like AntiX (which uses openbox, fluxbox, etc.) will allow for functioning system.   You can get AntiX or any of the buntu lighter distros via Distrowatch.com or similar site(s).   Mint Mate might also be suitable (which is a better distro than most of the above).

---

### Post by angel mike on 2015-07-03
Yes I have done that many times but it just does not work. What I find puzzling is during loading up the live CD I get a screen all the way to the Try/Install web page and in the Install phase right to giving a login/password. But after that the screen is blank with both options. Since that 14.04.2 release I cannot update to the same files as before - at least thats my theory!. Would I be better off trying Lubuntu or Kubuntu - would I encounter the same problems.I am not short of capacity. Regards  Mike

---

### Post by oldfred on 2015-07-03
With BIOS and any Ubuntu version/flavor live installer, you should get a selection screen if you press any key. Then you can add the nomodeset option with f6.
       Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Grub menu is after you have installed and on first boot or until you install proprietary video driver, you will need nomode set. Then you have to use shift key and manually add nomodeset on the Linux line in grub.

---

### Post by angel mike on 2015-07-04
Thanks Geoffrey for those useful references - which I will pursue if all else fails with Ubuntu. I have made some progress - see next posting.
 Mike

---

### Post by angel mike on 2015-07-04
Hi Oldfred I have made some progress ! Due to that boot options link - put nomodeset when loading up the CD while the logo shows at bottom and choosing the install option on the same screen - then let installation run. Reboot without disc from hard drive to BIOS tapping F2 key - exit than immediately keep tapping shift key (not holding down) to get the grub menu and put in nomodeset instead of quiet-splash.
All well and good - I get degraded graphics - but can access the desktop. Going into the software center I cannot locate the Additional Driver tab - not all the screen is showing- so cannot load 304.125 from nvidia-304(proprietary, tested) which worked before. Any suggestions appreciated !

---

### Post by Bashing-om on 2015-07-04
angel mike; Hey;

In this situation, may be best to work from terminal. As you are able to get the system booted with degraded graphics display; the foundation of the system is intact.
At the degraded desktop, can you get a terminal interface with key combo ctl+alt+t ?
In this interface what returns :
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list

```
And we see what we can do to purge and (RE-)install the graphics driver .

[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2015-07-04
I had same issue of screen too large and could not scroll with one of my installs. I think I ended up with command line as Bashing-om suggests.

But try right click on screen and see if you get a change screen option and then can you get to system settings?

---

### Post by angel mike on 2015-07-05
Success ! At least I think so - have yet to download updates in cluding 14.04.2. Thanks Bashing-om and Oldfred - a great team !
On putting drivers into the Search it came up with a list of options for NVIDIA drivers - and was able to select 304.125(proprietary, tested even on the restricted screen. Now can access everything on the side bar from the desk top and increase screen size.
The input/output suggested by Bashing-om is
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list

michael@michael-GM5066B:~$ sudo ubuntu-drivers devices
[sudo] password for michael: 
michael
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd000001D1sv0000107Bsd00003A07bc03sc00i00
model    : G72 [GeForce 7300 LE]
vendor   : NVIDIA Corporation
driver   : nvidia-304-updates - distro non-free
driver   : nvidia-173 - distro non-free
driver   : nvidia-304 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

michael@michael-GM5066B:~$ michael
michael: command not found
michael@michael-GM5066B:~$ sudo ubuntu-drivers list
nvidia-304
nvidia-304-updates
nvidia-173
michael@michael-GM5066B:~$ 

```
Would it be worhwhile purging before updating ?
A smiling Mike !

---

### Post by oldfred on 2015-07-05
If you install the wrong nVidia driver or install from a different source, ie Ubuntu repository, ppa (various ones) or nVidia (not really recommended), then you have to purge as each type of install seems to conflict or set incorrect settings somewhere. 
Or purge required if changing driver.
If first install of any nVidia driver, then there really is nothing to purge.

---

### Post by angel mike on 2015-07-05
As I feared-I loaded all the updates ( including Ubuntu 14.04.2) and rebooted - the screen went blank (grey) although it did change size to correct landscape. Using the previous method I could get  into the grub menu and insert 'nomodeset' and on about the third attempt got a desktop screen with the side bar but nothing responded with the mouse - or at least not immediately since I did get the search screen with tabs across -one of which was 'additional driver' but again no immediate mouse response - it then gave a password screen for a guest user- which I typed up- then the screen went grey again. Any thoughts! Mike

---

### Post by oldfred on 2015-07-05
Are you loading full Ubuntu with Unity?

My old laptop with 1.5GB of RAM and old internal Intel behaved slow like that as video did not have enough horsepower for full Unity.
I installed fallback which is the old menu like Ubuntu's old version with gnome2, but now using gnome3. That is a lighterweight gui and worked well. Others often suggest Xubuntu or Lubuntu.

---

