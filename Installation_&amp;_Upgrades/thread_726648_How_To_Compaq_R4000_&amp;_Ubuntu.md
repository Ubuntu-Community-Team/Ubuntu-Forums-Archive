---
title: "How To: Compaq R4000 &amp; Ubuntu"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by Buckwheat469 on 2008-03-16
I'm writing this little "how to" to help out the people that have Compaq R4000s and want to try something different than Windows. Just for reference, Compaq (HP) cannot offer advice or support for drivers or possibly anything if you install Ubuntu, so take the risk if you want.
[B]
Preparing for installation (Dual Boot for testing purposes)[/B]:

First thing's first, you must prepare a partition from Windows. I used Partition Magic to reduce the size of the Windows partition by 20GB. This is enough for a basic installation and then some. After everything I've installed I've only used 4.5G.

After clearing some space, insert the Ubuntu 64Bit Gutsy Gibbon live CD, which you have downloaded and restart the computer.

Click the Install icon and follow the instructions. When the screen gets to the partition section click the Custom Configuration and make 3 new partitions inside the unpartitioned space.
/boot   150M       ext3
/         ~19000M ext3
          ~1950M   swap   (this will haunt us later but it must be done)

**After Installation** (fixing the partition problem):

Go to System->Administration->Synaptic Package Manager. Search for gparted. Install. Then go to System->Administration->Partition Editor. Delete the Linux-swap partition and re-create it. This will fix a bootup error with the resume image.

**After Installation** (Drivers, this is where the fun starts):

*You must be using a wired network for this part.

Open System->Administration->Software Sources. Check main, universe, multiverse, and restricted. Under the Third-Party Software tab check both available sources. Under the Updates tab check gutsy-security and gutsy-updates. Close.

Open System->Administration->Restricted Drivers Manager. Check ATI and Broadcom drivers. Broadcom will ask you for a location to a file, just use the Internet checkbox to download the one provided by the community. Close. Restart.

You should be able to set up your wireless network now.

**Fun Programs**:

Compiz - Open System->Administration->Synaptic Package Manager. Search for Compiz. 
Check:
   Compiz
   compiz-bcop
   compiz-config-settings-manager
   compiz-core
   compiz-dev
   compiz-fusion-plugins-extra
   compiz-fusion-plugins-main
   compiz-gnome
   compiz-plugins
   emerald
   gnome-compiz-manager
   libcompizconfig0
   libcompizconfig-backend-gconf
   libdecoration
   libgnome-compiz-manager0
   python-compizconfig

Apply these new settings.

Open a terminal window. Type 'sudo gedit /etc/X11/xorg.conf'. 
Set:
[FONT="Courier New"]Section "Extensions"
	Option		"Composite"	"0"
EndSection[/FONT]
To:
[FONT="Courier New"]Section "Extensions"
	Option		"Composite"	"1"
EndSection[/FONT]

In the Module section make it look like this:
[FONT="Courier New"]Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"vbe"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection[/FONT]

Restart.

IMPORTANT!!! During reboot press F10 to go into the BIOS manager. Go set the video card to use UMA+Sideport. This will make compiz stable. ATI uses Sideport by default because they didn't trust UMA from AMD's new 64bit processor.

After reboot go to System->Preferences->GLDesktop. Enable GL Desktop. Under the Windows tab check Wobbly. Under the Workspaces tab select the Cube and Rotation radio button. Select 4 viewports. Under the Desktop tab check the Water Effect. Close this window.

Open System->Preferences->Advanced Desktop Effects Settings. Enable whichever ones you want, but I like Desktop Cube, Rotate Cube, Cube Reflection, Wobbly Windows, Cube Caps, Shift Switcher. Either restart the computer or Xorg by pressing Ctrl-Alt-Backspace.

Follow the instructions on [https://help.ubuntu.com/community/SimplyStunningLinuxDesktop]("https://help.ubuntu.com/community/SimplyStunningLinuxDesktop") for transparencies.
and [http://maketecheasier.com/how-to-redesign-your-desktop-the-wow-way/2008/01/10]("http://maketecheasier.com/how-to-redesign-your-desktop-the-wow-way/2008/01/10") for the cool Mac look.

**Sharing a Windows Mail Client** (Thunderbird should already be set up in Windows):

Install Thunderbird from the Synaptic Package Manager. Open a terminal window and type "thunderbird -profilemanager" Create a new profile and point it to your Windows profile folder (/dev/hda1/Documents and Settings/User/Application Data/Thunderbird/profiles/profile.xyz). You can now use Thunderbird in both Windows and Linux!!!


This should cover the basics. If this doesn't help you then it'll at least be useful for me whenever I have to do this again.

---

