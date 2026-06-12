---
title: "Installation ASUS M2A-VM HDMI with AVM FRITZ!WLAN USB stick and RME Multiface"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by li009 on 2007-10-27
On the basis of my current hardware (ASUS M2A-VM HDMI) and my current operating system (Kubuntu 7.10 Gutsy Gibbon) I will for those of you, who have the same or a similar system, explain step-by-step, what I did, to get things going.
 
**[SIZE=7]Invitation:[/SIZE]**
I invite everyone who runs the same mainboard or hardware components on Kubuntu (or Ubuntu) to let me and thus others know about it on this thread. This way we may build a sort of special community and can better help each other out. We M2A-VMians have to stick together, right? :)
 
**HARDWARE**
[LIST]
[*]Mainboard: ASUS M2A-VM HDMI (Northbridge: AMD 690G; Southbridge: ATI SB600)
[*]BIOS-Revision: 1001
[*]Graphics: onboard ATI Radeon X1250
[*]Soundcard 1: onboard Realtek ALC883 (High Definition Audio 6-channel audio CODEC; run in mode legacy AC'97)
[*]Soundcard 2: RME Hammerfall DSP Multiface with PCI-Card
[*]CPU: AMD Athlon 64 X2 4000+
[*]Printer: Canon PIXMA MP780
[*]Internal SATA-Harddisk: Western Digital WD1600AAJS Caviar SE 160G
[*]External Firewire-Harddisk: Maxtor (NTFS fomatted)
[*]WLAN: AVM FRITZ!WLAN USB stick (encrypted by WPA; used with static IP)
[*]Router: AVM FRITZ!Box Fon WLAN 7050
[*]Other things: Diskettedrive, USB-Memorystick, external USB-Harddisk[/LIST]**SOFTWARE**
[LIST]
[*]Operating System: Kubuntu 7.10 Gutsy Gibbon Desktop Edition PC (Intel x86 32 bit)
[*]Emailclient: Migrated from Windows "The Bat!" to Unix "Thunderbird"
[*]Automatix2
[*]Skype[/LIST]

**_INSTALLATION_**
 
**Operating System**
To install Kubuntu Gutsy Gibbon I used a Live-CD. At first I had quite a bit of problems (the updating process later on would halt with some kind of error message). To avoid problems, I connected my computer with a lan-cable to my router, which I temporarily set to use DHCP (usually I use a static IP). Also I made sure, to delete the home-directory prior to installation (or at least rename it). During installation I chose "DEAD GRAVE ACUTE" as keyboard layout. Once the system was installed I followed Kubuntus suggestion to update the system (I believe 16 packages were updated). In order to be able to easily install third-party programs as for example Skype I installed Automatix2 by closely following this HowTo: [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
 
 
**AVM FRITZ!WLAN USB stick**
Installing the WLAN USB stick was somewhat tricky. The good part: Gutsy Gibbon recognizes the USB stick immediately after installation. With Feisty Fawn this was not the case and you had thus to install the linux-driver from AVM. In order for the automatic setup really to happen, I inserted the stick right from the start and never removed it.
[LIST=1]
[*]First I created a text-file /etc/wpa_supplicant/wpa_supplicant.conf with the following content ...```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1
network={
         ssid="Here the SSID in quotation marks"
         scan_ssid=1
         proto=WPA
         key_mgmt=WPA-PSK
         pairwise=TKIP
         group=TKIP
         psk="Here the WPA-password in quotation marks"
}
```
[*]Next I modified the text-file /etc/network/interfaces to look like this ...```
## Loopback interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
 
## LAN interface
#auto eth0
iface eth0 inet static
    address 192.168.178.21
    netmask 255.255.255.0
    gateway 192.168.178.1
 
auto wlan0
 
iface wlan0 inet static
    wpa-driver wext
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
    address 192.168.178.21
    netmask 255.255.255.0
    gateway 192.168.178.1
```
[*]Finally I gave the following command in a root shell (KMenu -> System -> Konsole - Terminal Program -> Terminal-Menu Session -> New Root Shell) ...> echo nameserver 192.168.178.1 >> /etc/resolv.conf[/LIST]A complete restart of the system may be required (I am not sure if this is really true).
 
The situation now is the following: When I have the stick inserted while I boot the system up, things will automatically work. If however I insert the stick later or pull it out and insert it back in, the WLAN-connection will unfortunately not be (re)established automatically. Therefore I have to do that manually by entering two commands ...> sudo ifdown wlan0
sudo ifup wlan0
[COLOR=red]**Unresolved Problems with the AVM FRITZ!WLAN USB stick:**[/COLOR]
[LIST]
[*]No automatic (re-)connection when inserting the WLAN-stick after bootup
(see [http://ubuntuforums.org/showthread.php?p=3652966#post3652966](http://ubuntuforums.org/showthread.php?p=3652966#post3652966))
[*]No easy method found yet to just temporarily deactivate the WLAN-connection[/LIST]

**Graphics: onboard ATI Radeon X1250**
To install the original ATI-driver I simply did the following:
KMenu -> System Settings -> Advanced -> Restricted Drivers -> Administrator Mode -> Select ATI accelerated graphics driver
 
The above described leaded to the installation of a rather old version of an ATI driver. Therefore later on I followed the instructions given here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide). Unfortunately even then I still did not get the overlay-mode to work. The command glxgears shows approximately a frame rate of 1150. I am not sure, if this is a good value. I read, that even 5 year old graphic cards like the ATI Radeon 8500 would easily reach a value of 2000. On the one hand my motherboard is quite new. On the other hand of course I have an onboard graphics card while the ATI Radeon 8500 is an AGP-card.
 
[COLOR=red]**Unresolved Problems with the onboard ATI Radeon X1250:**[/COLOR]
[LIST]
[*]Cannot get the overlay-mode to work
(see [http://ubuntuforums.org/showthread.php?p=3654397#post3654397](http://ubuntuforums.org/showthread.php?p=3654397#post3654397))
[*]Not sure, whether a frame rate of 1150 usind glxgears is OK for a Radeon X1250
(see [http://ubuntuforums.org/showthread.php?p=3653270#post3653270](http://ubuntuforums.org/showthread.php?p=3653270#post3653270))[/LIST]

**Printer Canon PIXMA MP780**
To install the printer I did this ...
[LIST=1][*]KMenu -> System -> Adept Manager -> Menu Adept -> Manage Repositories -> Tab Third-Party Software -> Add: "deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./" (without the quotation marks)
[*]Fetch Updates
[*]Install the 3 packages libcnbj-2.5, bjfilter-2.5 and pstocanonbj
[*]KMenu -> System Settings -> Printers -> Add -> Add Printer / Class -> Next -> Select Local printer (parallel, serial, USB) -> Next -> Select Canon MP780 -> Next -> Button Other -> Path /usr/share/ppd/pstocanonbj/ -> Select File canonpixusip4100.ppd -> OK -> Next -> Settings -> Paper Feed = Cassette -> OK -> Test -> Next -> Next -> Next -> Next -> Type Name: Canon_PIXMA_MP780 -> Next -> Finish[/LIST]
I tried modifying the ppd-file (canonpixusip4100.ppd) as is sometimes suggested (e.g.: [http://wiki.ubuntuusers.de/Canon_Pixma_IP4000]("http://wiki.ubuntuusers.de/Canon_Pixma_IP4000")). In the end it showed though, that the standard resolution of 600x600 is far better than 1200x1200 or 2400x2400 and also, that changing the quality setting does not have any effect whatsoever. Therefore I don't see any need, to edit the ppd-file.


**AMD Athlon 64 X2 4000+ Cool'n'Quiet**
I am not sure, whether Gutsy Gibbon has AMDs feature Cool'n'Quiet automatically activated. To find out I would like to install the AMD Power Monitor. Linux drivers for Suse and Red Hat are here: [http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871_13118,00.html](http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871_13118,00.html). But so far I could not find out, if as a user of Kubuntu one can get this tool going as well.
 
[COLOR=red]**Unresolved Problems with AMD Athlon 64 X2 4000+ Cool'n'Quiet:**[/COLOR]
[LIST]
[*]How can I install the AMD Power Monitor on Gutsy Gibbon?
(see [http://ubuntuforums.org/showthread.php?p=3653270#post3653270](http://ubuntuforums.org/showthread.php?p=3653270#post3653270))[/LIST]

**Onboard soundcard Realtek ALC883**
In order for the onboard soundcard to work well together with Skype I figured out the following setup of KMix by trial and error:
 
Output: PCM-volume = 100%; front-volume = 100% and activated; remaining channel-volumes = 0% and deactivated
Input: Capture left and right volumes = 0%; capture left activated; capture right deactivated (my impression is, that the onboard mic is not capable of adjusting its sensitivity)
Switches: Headphones and IEC958 deactivated; input Source on top = line; input source on the bottom = Mic
 
In addition I enabled full duplex: KMenu -> System Settings -> Sound System -> Hardware -> Select Full duplex
 
[COLOR=red]**Unresolved Problems with the onboard soundcard Realtek ALC883:**[/COLOR]
[LIST]
[*]Is it really true, that the sensitivity of the ASUS-onboard-mic cannot be adjusted in its sensitivity?[/LIST]

**Diskettedrive**
I tried very hard to get access to my diskettedrive by means of the KDE-desktop - unfortunately without success! The only way I figured out so far is to mount and unmount the drive in a terminal ...> sudo mount -t vfat /dev/fd0 /media/floppy
sudo umount /media/floppy
 
[COLOR=red]**Unresolved Problems with the diskettedrive:**[/COLOR]
[LIST]
[*]Cannot get access to diskettes by means of the desktop
(see [http://ubuntuforums.org/showthread.php?p=3653024#post3653024](http://ubuntuforums.org/showthread.php?p=3653024#post3653024))[/LIST]

**RME Hammerfall DSP Multiface with PCI-Card**
This was perhaps the hardest part of the installation!
First I installed the following packages (via KMenu -> System -> Adept Manager) ...> alsaplayer-common
alsa-tools
alsa-tools-gui
alsa-firmware-loaders
Then I needed to get the firmware-file "multiface_firmware_rev11.bin". Unfortunately I did not find it as such on the internet. Somehow I figured out though, that the desired file is part of the RPM-package "alsa-firmware-1.0.10-13.noarch.rpm" (this file is easily found by a google-search). So I downloaded that package to my desktop and extracted its files. In order to do that I gave the following commands ...> sudo apt-get install rpm
rpm2cpio ~/Desktop/alsa-firmware-1.0.10-13.noarch.rpm | cpio -dimv Afterwards I found the .bin-file at ~/lib/firmware and copied it to the location /usr/share/alsa/firmware/hdsploader (this path did not readily exist so I had to first create it). Because I needed administrative rights to do that I pressed ALT-F2 and typed "kdesu konqueror".
 
Next it is important, that at system-bootup the Multiface-firmware is automatically loaded and that the HDSP-Mixer is set correctly. Of course setting up the HDSP-Mixer correctly depends very much on what one exactly wants and how things are hooked up to the Multiface. My personal situation is the following ...
[LIST]
[*]Software-playback via Out 1 (left) and Out 2 (right)
[*]Multiface-output via SPDIF (optical)[/LIST]My aim was therefore, to set the Multiface-routing accordingly automatically at startup. To realize that, together with the firmware-loading, I created the following text file (in order to get administrative rights via ALT F2 -> kdesu kate) ...> hdsploader
amixer -c 1 cset numid=5 26,24,32768
amixer -c 1 cset numid=5 27,25,32768... and saved it to this location: /etc/init.d/hdsploader
 
To round things up I gave the following commands ...> sudo update-rc.d hdsploader defaults
sudo chmod +x /etc/init.d/hdsploader (to make the script executable)
 
Because I have two soundcards (one internal and one external) I needed to make sure, that they are loaded up in a consistent order with regard to their numbering. So I gave the command ...```
sudo nano /etc/modprobe.d/alsa-base
```
... and added the following two lines at the end of the file ...> options snd_hda_intel index=0
options snd_hdsp index=1
 
To let the Multiface know, that it is the optical SPDIF-Out (and not the coaxial), that I want to use, I started KMenu -> Multimedia -> HDSPConf and selected at the section SPDIF-Out the option ADAT1
 
Finally, to be able to just click on a sound-file and instantly listen to it via the RME Multiface, I did the following ...
[LIST]
[*]Right-clicked on a wav-file
[*]Selected Properties
[*]At the tab "General" I clicked the "Edit-file-type"-symbol (a new window opened)
[*]At the tab "General" of the new window, I clicked at the section "Application Preference Order" on the button "Add"
[*]In the text-field of the newly opened window I typed: alsaplayer -d plughw:1,0 %F
[*]At the first window, which now showed again, I selected "alsaplayer" and pressed the button "Edit"
[*]At the now newly opened window I chose the tab "Application"
[*]In the text-field "Name" I typed "Alsaplayer RME" and pressed "OK" afterwards
[*]Then I made sure, that "Alsaplayer RME" was the first entry in the Application Preference Order (using the "Move Up" button)[/LIST]This works quite well except for one thing ...
 
[COLOR=red]**Unresolved Problems with the RME Hammerfall DSP Multiface:**[/COLOR]
[LIST]
[*]Once a sound-file has been played completely to the end, the alsaplayer stays open and does not accept further sound-files!
(see [http://ubuntuforums.org/showthread.php?p=3653086#post3653086](http://ubuntuforums.org/showthread.php?p=3653086#post3653086))[/LIST]TO BE CONTINUED ...

---

### Post by Mjölner on 2007-10-31
What a great post!

the hardware I have is similar and I will be looking at this post at another stage.

I installed Ubuntu for the first time last night and the first thing I wanted to try out was to get online. Due to the position of my PC with respect to my dsl modem I always connect via wlan. 

So the first step: plug in my fritz!wlan usb stick.....    It was recognized and I could see the few access points that are in my street. 

The next step: connect to my fritz!box......      the fritz!box uses wpa encryption as default, and despite checking that the code was right a few times it didn't work. well after a quick reboot into the other os, and a quick look around in the support pages, I found out that I need to use wep encryption. 

Thats it! as simple as.

I'm well happy with my Ubuntu experience so far

---

### Post by li009 on 2007-11-01
WEP is indeed easier to implement as it is directly supported by (K)Ubuntu. WEP however is known to be quite easily breakable.

---

### Post by makeyre on 2007-11-11
I'm stymied with my installation of Gutsy on the basic M2A-VM board.  I've started a new thread on it though.

[http://ubuntuforums.org/showthread.php?t=609491](http://ubuntuforums.org/showthread.php?t=609491)

---

