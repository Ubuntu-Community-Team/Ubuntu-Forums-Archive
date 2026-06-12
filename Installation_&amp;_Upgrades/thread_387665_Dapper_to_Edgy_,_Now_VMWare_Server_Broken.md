---
title: "Dapper to Edgy , Now VMWare Server Broken"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by cknight725 on 2007-03-18
Okay, so I successfully upgraded from Dapper to Edgy and am attempting to get VMWare Server running once again by re-running cmware-config.pl, however it is erroring out in two places:

> 
root@cknight-laptop:/usr/src# /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                        done
   Virtual ethernet                                                            done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: error: Categories values must be one of "Core", "Development", "Building", "Debugger", "IDE", "GUIDesigner", "Profiling", "RevisionControl", "Translation", "Office", "Calendar", "ContactManagement", "Database", "Dictionary", "Chart", "Email", "Finance", "FlowChart", "PDA", "ProjectManagement", "Presentation", "Spreadsheet", "WordProcessor", "Graphics", "2DGraphics", "VectorGraphics", "RasterGraphics", "3DGraphics", "Scanning", "OCR", "Photography", "Viewer", "Settings", "DesktopSettings", "HardwareSettings", "PackageManager", "Network", "Dialup", "InstantMessaging", "IRCClient", "FileTransfer", "HamRadio", "News", "P2P", "RemoteAccess", "Telephony", "WebBrowser", "WebDevelopment", "AudioVideo", "Audio", "Midi", "Mixer", "Sequencer", "Tuner", "Video", "TV", "AudioVideoEditing", "Player", "Recorder", "DiscBurning", "Game", "ActionGame", "AdventureGame", "ArcadeGame", "BoardGame", "BlocksGame", "CardGame", "KidsGame", "LogicGame", "RolePlaying", "Simulation", "SportsGame", "StrategyGame", "Education", "Art", "Construction", "Music", "Languages", "Science", "Astronomy", "Biology", "Chemistry", "Geology", "Math", "MedicalSoftware", "Physics", "Teaching", "Amusement", "Applet", "Archiving", "Electronics", "Emulator", "Engineering", "FileManager", "Shell", "ScreenSaver", "TeminalEmulator", "TrayIcon", "System", "Filesystem", "Monitor", "Security", "Utility", "Accessibility", "Calculator", "Clock", "TextEditor", "KDE", "GNOME", "GTK", "Qt", "Motif", "Java", "ConsoleOnly" (found "Application")
[B]desktop-file-install created an invalid desktop file!
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.[/B]
/usr/share/applications/vmware-console-uri-handler.desktop: error: Categories values must be one of "Core", "Development", "Building", "Debugger", "IDE", "GUIDesigner", "Profiling", "RevisionControl", "Translation", "Office", "Calendar", "ContactManagement", "Database", "Dictionary", "Chart", "Email", "Finance", "FlowChart", "PDA", "ProjectManagement", "Presentation", "Spreadsheet", "WordProcessor", "Graphics", "2DGraphics", "VectorGraphics", "RasterGraphics", "3DGraphics", "Scanning", "OCR", "Photography", "Viewer", "Settings", "DesktopSettings", "HardwareSettings", "PackageManager", "Network", "Dialup", "InstantMessaging", "IRCClient", "FileTransfer", "HamRadio", "News", "P2P", "RemoteAccess", "Telephony", "WebBrowser", "WebDevelopment", "AudioVideo", "Audio", "Midi", "Mixer", "Sequencer", "Tuner", "Video", "TV", "AudioVideoEditing", "Player", "Recorder", "DiscBurning", "Game", "ActionGame", "AdventureGame", "ArcadeGame", "BoardGame", "BlocksGame", "CardGame", "KidsGame", "LogicGame", "RolePlaying", "Simulation", "SportsGame", "StrategyGame", "Education", "Art", "Construction", "Music", "Languages", "Science", "Astronomy", "Biology", "Chemistry", "Geology", "Math", "MedicalSoftware", "Physics", "Teaching", "Amusement", "Applet", "Archiving", "Electronics", "Emulator", "Engineering", "FileManager", "Shell", "ScreenSaver", "TeminalEmulator", "TrayIcon", "System", "Filesystem", "Monitor", "Security", "Utility", "Accessibility", "Calculator", "Clock", "TextEditor", "KDE", "GNOME", "GTK", "Qt", "Motif", "Java", "ConsoleOnly" (found "Application")
[B]desktop-file-install created an invalid desktop file!
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.[/B]
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.17-11-386/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.17-11-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-386'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-386'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove 
it.  Somebody else apparently did it already.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] no

Do you want networking for your virtual machines? (yes/no/help) [yes] 

This program previously created the file /dev/vmnet1, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet2, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet3, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet4, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet5, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet6, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet7, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet8, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet9, and was about to remove 
it.  Somebody else apparently did it already.

Would you prefer to modify your existing networking configuration using the 
wizard or the editor? (wizard/editor/help) [wizard] 

The following bridged networks have been defined:

. vmnet0 is bridged to ath0

Do you wish to configure another bridged network? (yes/no) [no] 

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] 

Configuring a NAT network for vmnet8.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.107.0/255.255.255.0 appears to be unused.

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 192.168.107.0.

Do you wish to configure another NAT network? (yes/no) [no] 

Do you want to be able to use host-only networking in your virtual machines? 
[yes] 

Configuring a host-only network for vmnet1.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.72.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 172.16.72.0.

Do you wish to configure another host-only network? (yes/no) [no] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.17-11-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-386'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
**WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o**
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-386'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902] 

Stopping internet superserver: xinetd.
Starting internet superserver: xinetd.
Configuring the VMware VmPerl Scripting API.

Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Do you want this program to set up permissions for your registered virtual 
machines?  This will be done by setting new permissions on all files found in 
the "/etc/vmware/vm-list" file. [no] 

Generating SSL Server Certificate

In which directory do you want to keep your virtual machine files? 
[/var/lib/vmware/Virtual Machines] 

Do you want to enter a serial number now? (yes/no/help) [no] 

Starting VMware services:
   Virtual machine monitor                                                                      done
   Virtual ethernet                                                                                     done
**   Bridged networking on /dev/vmnet0                                                failed**
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                                              done

The configuration of VMware Server 1.0.1 build-29996 for Linux for this running
kernel completed successfully.


I'm certainly no expert, and it seems that the necessary headers and symlinks are in place ... what am I missing??

---

### Post by zvacet on 2007-03-19
I know it is not popular,but why don´t you uninstall and install again?
```
cd /usr/bin
```
```
sudo ./name_of_vmware_uninstall_file
```
P.S. Be carefull and don´t leave any vmware file behind,because they will mess up your next install.

---

### Post by cknight725 on 2007-03-19
Thanks, but I'd like to keep that as a last resort  ... any other ideas?

---

### Post by cknight725 on 2007-03-20
Well, after much hardship I figured it out -- OCCASIONALLY, when you re-run the vmware-config.pl it does NOT clear the not_configured file from /etc/vmware .... THAT'S ALL THAT WAS CAUSING THE PROBLEMS -- I performed a complete Edgy reload and tossed my old virtual machines in the process, but I figured it out.  

For those that don't want to go to all that trouble, take my word for it, or read post #921 in this thread:
[http://ubuntuforums.org/showthread.php?t=183209&page=93](http://ubuntuforums.org/showthread.php?t=183209&page=93)

---

