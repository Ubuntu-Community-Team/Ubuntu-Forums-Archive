---
title: "Zotac Atom, Netbok Remix install Guide"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by JohnnyC35 on 2010-03-06
I've been playing around with my new computer a bit and I figured it may   help others using an Atom processor or that someone might find this   somewhat interesting :P

I am using Netbook Remix 32bit on a 8Gb USB stick, I have an Zotac Atom   A-U with 2Gb RAM, and 3 1Tb Internal storage as well as 1Tb/2 500Gb   external storage. My tmpfs might be 'excessive' but I was trying to minimze how much was on the USB drive. Eventually I would like to be able to run the whole thing in RAM (when I have 4Gb and know what I am doing) and only need a hard drive for when I reboot. Oh and my CPU is without a fan, I was able to put a 120mm fan between the motherboard and the from of the case (Apex MI-008. And since I don't need a power supply if I can get my hands on some quiet 40mm fans I will put them in the power supply window. Underload my GPU usually runs about 75C.

Here are the sections:
What was immediately installed
 What was immediately removed
 Getting Vuze to install/update properly and setting up Google Docs
 DPI change and Nvidia
 Grub editing
 Compiz
 Start button
 Concurrency
 Internet settings
 Drapes
 Fstab
 cleaning apt

[U][SIZE=2]What was immediately installed[/SIZE]
[/U] 
Installed VDPAU Nvidia 195 drivers, Swiftfox (Prescott,for Atom), XMBC   media player, Amsn, Claws email, Drapes wallpaper changer, localepurge,   deborphan, apt-mark-sync to sync apt, aptitude, deborphan info,  Ubuntu's  resticted extras, XScreensaver with Extras package for  Caurosel, Adobe  Flash, DNS masq to make the computer look at a saved  DNS cache,Preload,  QEMU for the use of Quicktax via WinXP.iso,  soundconverter to change  over my mp3's to ogg, also install VLC.

NVIDIA Info:
[http://sglnx.com/2009/12/nvidia-195-22-beta-linux-display-driver-available-in-nvidia-vdpau-team-ppa-ubuntu/?utm_source=Arkayne.com&utm_medium=Plugin&utm_campaign=1405](http://sglnx.com/2009/12/nvidia-195-22-beta-linux-display-driver-available-in-nvidia-vdpau-team-ppa-ubuntu/?utm_source=Arkayne.com&utm_medium=Plugin&utm_campaign=1405)
 

 add to /etc/apt/sources.list-> deb  [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian)  unstable non-free

```

sudo add-apt-repository ppa:nvidia-vdpau/ppa
  
sudo add-apt-repository ppa:team-xbmc
 
sudo apt-get update
 
 sudo apt-get install nvidia-195-modaliases nvidia-glx-195   swiftfox-prescott xbmc amsn claws-mail-html2-viewer drapes localepurge   deborphan apt-mark-sync ubuntu-restricted-extras xscreensaver-gl-extras   flashplugin-nonfree dnsmasq preload qemu-launcher soundconverter vlc
 

```
If there is an error with NVIDIA, you can activate the drivers  from  System > Administration > Hardware Drivers.
Also if you have no sound, what I found helped was to goto the terminal and type in 'alsamixer'. From there make sure that Master is full and that IEC958, any and all of them, are not muted by pressing 'M' 

[U][SIZE=2]What was immediately removed.
  [/SIZE][/U]  
Removed some unneeded programs: Bluetooth, Evolution, Netbook Launcher,   Compiz, ACPI Power Managerment stuff, OpenOffice, Transmission,  Empathy,  tomboy, example-content(do w even need that?) Assistive tech,  memtest,  cheese, rhythmbox, totem, other screensaver stuff, artwork,  documents:

```

sudo apt-get purge bluez evolution maximus netbook-launcher webfav   compiz-core acpid pm-utils empathy transmission-common evolution-common   openoffice.org-core tomboy example-content espeak-data software-center   python-ubuntuone-client memtest86+ ubuntu-docs ubuntu-artwork   ubuntu-wallpapers gnome-games-common firefox-3.5 cheese rhythmbox   gnome-pilot at-spi yelp screensaver-deflt-images xscreensaver-gl totem   bogofilter britty
 
```Some other documents can be removed, don't have the names on  hand, I  just went to Synaptic -> Documentation, selected and removed  all  except rarian-compat .


[U][SIZE=2]Getting Vuze to install/update properly and setting up  Google Docs
  [/SIZE][/U]
 followed instructions from:  [http://www.detector-pro.com/2009/12/how-to-install-vuze-43-and-newer-on.html](http://www.detector-pro.com/2009/12/how-to-install-vuze-43-and-newer-on.html)    to install vuze
 
 > 
    * First you need to install JRE (Java Runtime Environment). Open   terminal and paste this line:
  
      sudo apt-get install sun-java6-jre sun-java6-plugin  sun-java6-fonts
  
      * After JRE installation, download Vuze from Official Site or  click  here.
      * Unpack it to the desktop.
      * Go to your home folder and create new folder &#8220;.azureus&#8221; with dot   in front.
      * From nautilus View menu, choose &#8220;show hidden files&#8221;.
      * Copy All files from Vuze folder on your desktop into newly  created  &#8220;.azureus&#8221; folder.
      * You are almost ready. Now you need to add a program launcher to   Applications menu. Go to System/Preferences/Main Menu. Then Choose   Internet and click &#8220;New Item&#8221;. On the Create Launcher window choose   Browse. Then on new Choose an Application.. window right click to choose   Show Hidden Files.
  
      * Next, Go to your Home folder/.azureus and click on &#8220;vuze&#8221;. To  add  the vuze Icon just drag and drop vuze.png as on the next picture.  Click  Ok and that's it :)
  

added a menu item that directed to Google Documents via  Swiftfox: 
swiftfox [https://docs.google.com/](https://docs.google.com/)


   [U][SIZE=2]DPI change and Nvidia
  [/SIZE][/U]     
I have a 1080 res TV connected to my computer so I needed to change the   DPI before I reboot the computer with the res change or it will look   really really small :P

Appearance -> Fonts -> Details -> 150 DPI ; then      'sudo   nvidia-settings'
change resolution 1920x1080, apply and save (will reboot later)

[U][SIZE=2]Grub editing
  [/SIZE][/U]      
I edited GRUB so that the splash screen won't be displayed, or at least   not displayed as long, and told it that I don't use hibernate or a swap   file to save time.
```

sudo gedit /etc/default/grub
 changed 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to
 GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash noresume noswap"
 then 
sudo update-grub2
 
```_[SIZE=2]Compiz[/SIZE]_
                
I don't use Compiz, lots of flash but kills CPU cycles but you can do   some basic stuff. the folowing will give shaowing and change your   alt-tab look a little:
```

gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool   true
 
```_[SIZE=2]Start button[/SIZE]_
               
Make the keyboard Start button (or Super button) open the gnome menu:   type in terminal
```

"gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu   --type string "Super_L"
 
```[SIZE=2][U]Concurrency
  [/U][/SIZE]I added concurrency booting so Ubuntu can take advantage of  dual-core  processors, as well as processors that hyperthread or  multithread. 

'sudo gedit /etc/init.d/rc'
CONCURRENCY=none changed to CONCURRENCY=shell

_[SIZE=2]Internet settings[/SIZE]_
         
Changed some settings for my internet:
Adjust settings for broadband internet...

* scroll to the bottom and just add these lines to it.
 'sudo gedit /etc/sysctl.conf'
```
net.core.rmem_default = 524288
 net.core.rmem_max = 524288
 net.core.wmem_default = 524288
 net.core.wmem_max = 524288
 net.ipv4.tcp_wmem = 4096 87380 524288
 net.ipv4.tcp_rmem = 4096 87380 524288
 net.ipv4.tcp_mem = 524288 524288 524288
 net.ipv4.tcp_rfc1337 = 1
 net.ipv4.ip_no_pmtu_disc = 0
 net.ipv4.tcp_sack = 1
 net.ipv4.tcp_fack = 1
 net.ipv4.tcp_window_scaling = 1
 net.ipv4.tcp_timestamps = 1
 net.ipv4.tcp_ecn = 0
 net.ipv4.route.flush = 1
 
```'reset sysctl: sudo sysctl -p'

Disable IPv6: sudo gedit /etc/modprobe.d/bad_list
add 'alias net-pf-10 off' and then save/exit

how to set the dnsmasq (cache dns info)

sudo gedit /etc/dnsmasq.conf
Replace ```
#resolv-file=
``` if exists with   ```
resolv-file=/etc/resolv.dnsmasq.conf
```then
```

sudo cp /etc/resolv.conf /etc/resolv.dnsmasq.conf
sudo gedit /etc/resolv.conf
[CODE]
and then add

```nameserver 127.0.0.1[/CODE]to the top of the list


 [U][SIZE=2]Drapes
  [/SIZE][/U]           
There is an issue with Drapes not loading on boot. its solved here:
> 
[https://bugs.launchpad.net/drapes/+bug/292051](https://bugs.launchpad.net/drapes/+bug/292051)
 Roland Schigas  wrote on 2009-12-23:        
 
 I just built a new laptop with Ubuntu 9.10 (64-bit), Gnome 2.28.1 &   Drapes 0.5.2. I was getting the same (not running) behaviour and  syslog  warnings as previous posters. I can confirm that editing the   drapes.desktop file to insert "Type=Application" fixed the problem; it   now runs automatically when I log in.
 
 [U][SIZE=2]Fstab
  [/SIZE][/U]             
 And then finally edit my fstab for tmpfs and adding info for my 3   Internal drives and 3 external drives:
 I also changed fstab:
```
# /etc/fstab: static file system information.
 #
 # Use 'blkid -o value -s UUID' to print the universally unique   identifier
 # for a device; this may be used with UUID= as a more robust way to  name
 # devices that works even if disks are added and removed. See fstab(5).
 #
 # <file system> <mount point>   <type>    <options>       <dump>  <pass>
 proc            /proc           proc    defaults        0       0
 # / was on /dev/sdd5 during installation
 UUID=2c929bc6-a715-4dc4-a4ee-aa05b6af0b3c /        ext2      noatime,nodiratime,errors=remount-ro 0 1
 # /home was on /dev/sdd1 during installation
 UUID=523a4fea-32d2-4924-9c4f-ec6772557fb9 /home    ext2      defaults,sync,noatime,nodiratime     0 1
 
 #UUID=60ce04eb-8dc4-430d-aaf7-0864ca65f1fe   /media/Media1 xfs   users,auto,sync,noatime,nodiratime,allocsize=384m 0 1
 #UUID=a2b357b5-700f-4409-b8ed-b4df99f1656e   /media/Media2 xfs   users,auto,sync,noatime,nodiratime,allocsize=384m 0 1
 #UUID=26c94f5c-0708-4031-be12-ece4f0815c90   /media/Media3 xfs   users,auto,sync,noatime,nodiratime,allocsize=384m 0 1
 
 #UUID=4df339f3-1ef9-4516-9762-aad2f2d9160b   /media/Media4 xfs   users,auto,sync,noatime,nodiratime,allocsize=384m 0 1
 #UUID=14e63b39-c51b-466d-bb92-bcb956cd518e   /media/Media5 xfs   users,auto,sync,noatime,nodiratime,allocsize=384m 0 1
 #UUID=81ebbbd2-d799-4dd1-a59c-e3bfc090967c   /media/Media6 xfs   users,auto,sync,noatime,nodiratime,allocsize=384m 0 1
 
 
 tmpfs /var/log tmpfs defaults,noatime,nodiratime 0 0
 tmpfs /tmp tmpfs defaults,noatime,nodiratime 0 0
 tmpfs /var/tmp tmpfs defaults,noatime,nodiratime 0 0
 tmpfs /var/log/apt tmpfs defaults,noatime,nodiratime 0 0
 tmpfs /var/run tmpfs defaults,noatime,nodiratime 0 0
 tmpfs /var/lock tmpfs defaults,noatime,nodiratime 0 0
 tmpfs /var/cache tmpfs defaults,noatime,nodiratime 0 0
 tmpfs /var/cache/apt/archives/ tmpfs defaults,noatime,nodiratime 0 0
 tmpfs /home/john/.thumbnails tmpfs defaults,noatime,nodiratime 0 0
 tmpfs /home/john/.adobe tmpfs defaults,noatime,nodiratime 0 0
 tmpfs /home/john/.cache tmpfs defaults,noatime,nodiratime 0 0
 tmpfs /home/john/.macromedia tmpfs defaults,noatime,nodiratime 0 0
 tmpfs /home/john/.claws-mail/gtkhtml2_viewer tmpfs   defaults,noatime,nodiratime 0 0
 tmpfs /home/john/.azureus/tmp tmpfs defaults,noatime,nodiratime 0 0
 tmpfs /home/john/.mozilla/firefox/t8t8ozn0.default/Cache tmpfs   defaults,noatime,nodiratime 0 0 
 
```I use to have Media1-6 set up here but they are commented out  because as  of right now they show up duplicated in Places and Nautilus  if they are  included. ??

update rc.local:
> 
mkdir -p /var/log/apt
 mkdir -p /var/cache/apt/archives
 mkdir -p /var/cache/apt/partial
 mkdir -p /var/cache/apt/archives/partial
 sysctl -w vm.swappiness=1 # Strongly discourage the swapping of   application data to disk
 sysctl -w vm.vfs_cache_pressure=50 # Don't shrink the inode cache so   aggressively
 oops also run this afterwards:

[U][SIZE=2]Cleaning apt
  [/SIZE][/U]        
```

sudo apt-get clean
 sudo apt-get autoremove
 sudo apt-get autoclean
 sudo apt-get remove $(deborphan)    *Maybe run this one a few times
 
```reboot: on boot press esc and edit your boot menu item, add  'profile' to  reprofile the booting process, possibily making it faster  for you


and if I have to reinstall everything I think I will try this:
[http://www.webupd8.org/2010/03/2-ways-of-reinstalling-all-of-your.html](http://www.webupd8.org/2010/03/2-ways-of-reinstalling-all-of-your.html)

I hope this was easy enough to read. I have posted things before but   this is my first walkthru. Sorry I didn't post more links as to where I got my info. Googling and trolling various forums mainly.

---

