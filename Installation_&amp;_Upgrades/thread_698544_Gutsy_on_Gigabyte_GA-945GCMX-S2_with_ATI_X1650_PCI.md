---
title: "Gutsy on Gigabyte GA-945GCMX-S2 with ATI X1650 PCIe (segfault on install screen)"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by Siggma on 2008-02-16
[SOLVED/WORKING]]**New Install **of Gutsy from Alternate CD with ATI (Visiontek) X1650 and amd-64

**Relevant Hardware:**
Gigabyte [GA-945GCMX-S2]("http://www.gigabyte.com.tw/Support/Motherboard/Manual_Model.aspx?ProductID=2521")
[Intel 2140 Core Duo]("http://www.intel.com/support/processors/pentiumdualcore/sb/cs-026774.htm") (1.6Ghz) Overclocked to 266 base (888 FSB 2.1 G internal clock)
2 Gig [DDR2 Kingston (PC6400)]("http://www.newegg.com/product/product.aspx?Item=N82E16820134583")
[SATA2 WD2500KS 250GB 16 mb cache 7200 RPM]("http://www.newegg.com/product/product.aspx?Item=N82E16822144701") for Vista  :(
PATA WD800JB 80gig 7200 8mb cache for Gutsy
[ATI X1650 (Visiontek)]("http://ati.amd.com/products/RadeonX1650/index.html")
[indent]Elo touchsystems **CRT monitor** without the touch overlay. 
I ripped it off the thing since it was scratched and yellow.
:KSGood monitor up to 1280x1024@60 or 1280x960@72[/indent]


**Context:**
With my latest hardware upgrades my son (a die hard Microsoft boob) talked me into trying Vista. While I like the desktop, I despise the company, it's philosophy and it's increasing difficulty getting along with products from non Microsoft (sanctioned) vendors. After spending time trying endless things to delete old Linux files, not being able to backup my Linux server to the NTFS drive (WTF?) and seeing the Compiz-fusion video on Youtube I decided it was time to dump Vista and give Gutxy a try. I run a Debian etch amd-64 web server so I have some Linux experience. I would also like to be able to snap a jpg of a web page on the server which requires X which my server does NOT and probably never will, have. So, having set the context, here is my experience.

**Issues you may encounter:**
I got a cpu register display in a box in the upper left corner of the video and I can't select install options. I tested the same disk with the native video adapter and it works fine so I concluded the PCIE video card was the culprit. I've seen this behavior before on a different board (ECS) with ATI 9200. Having decided there was nothing wrong with my basic hardware I downloaded a copy of the alternate CD and ignored the error.

**Installation:**

[LIST]
[*]Boot from the amd-64 alternate CD, press enter at the initial screen and ignore the apparent segfault error. This gives me a "Boot:" prompt to which I simply pressed enter.
[*]Setup partition and networking
[*]***When prompted for video modes,*** having tried other values I set the video to use ONLY 1024x768 800x600 and 640x480 and let the install finish.
[*]Download and install the proprietary [ATI driver]("http://ati.amd.com/support/drivers/linux/linux-radeon.html") Ver 8.2 posted Feb 13th 2008.
[*]..-Begin Installation-.. Gleaned and copied from [wiki article]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") 
[*]sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms ia32-libs
[*]sudo aptitude install linux-headers-2.6.22-14-generic
[*]sudo sh ati-driver-installer-8-02-x86.x86_64.run --buildpkg Ubuntu/gutsy
[*]sudo dpkg -i *.deb
[*]sudo apt-get install -f
[*]REBOOT to force module to load
[*]Force aticonfig to write a new xorg.conf based on DPMS monitor values with:
sudo aticonfig --initial -f

[*]Logout or Ctrl-Atl-Backspace and login again
[*]Driver initializes OK you're OK so far...
[*]Run Catalyst Control Panel from Applications->Accesseries
.. or run **amdcccle** in a terminal window to check it finds card OK
[*]fglrxinfo shows:
tom@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7281 Release

If not see [wiki article]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

[*]Edit /etc/default/linux-restricted-modules-common
make it look like below at the end: 
DISABLED_MODULES="fglrx"

[*]Edit /usr/bin/compiz to look like below:

COMPIZ_BIN_PATH="/usr/bin/"
PLUGIN_PATH="/usr/lib/compiz/"
COMPIZ_NAME="compiz.real"
WHITELIST="fglrx"


[*]run install meta for compiz and add config manager. I suggest you don't use the gnome-compiz manager but it's your choice.
sudo apt-get install compiz compizconfig-settings-manager

[*]Logout and login again. It usually enables "Normal" desktop effects automatically.
[*]Now, Run: System-> Preferences-> Advanced Desktop Effects
Play with settings. The **Animations** setting is very interesting and has a huge effect on overall desktop use. Rather than replacing items as stated in other posts I recommend you simply highlight the default animation effect and change it to "random" to see all the effects over time. Then you can decide which one's work well and which one's don't. This card is fast enough to support any and all of them, especially with 2gig of RAM.
[*]Necessary Tweaking:
Edit xorg.conf to include driver features not added by aticonfig
See my xorg.conf at the url below for examples. Especially check the two items mentioned below.

[/LIST]
My xorg.conf is at [http://www.trbailey.net/xorg.conf](http://www.trbailey.net/xorg.conf)
I removed the unneeded and undesirable wacom entries and enabled 2D texture support.
Option "Textured2D" "on"

Note also: Option "MaxGARTSize" "512" which sets the virtual memory size and allows the driver to use shared memory, up to 512 meg.

Have fun and leave a comment if you find this useful.
-Tom

---

### Post by wesswei on 2008-03-13
just wanted to ditto this method. however i used the current version and the cchtml method completely. * with a clean working install of amd-64 gutsy
    * i originally had igp with crappy graphics then installed a x1650 pcie
    * once x1650 installed, i had to revert to xorg driver
```
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall libgl1-mesa-glx
```
    * Download and install the latest ATI driver Ver 8.3 posted Mar 5th 2008.
    * installed as per [cchtml]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually")
    * sudo install, generate debs, install debs with -i --force-overwrite commands
    * sudo depmod -a
    * sudo aticonfig --initial -f
    * after a reboot, ati should be loaded and ready. try these commands in terminal window: ```
fglrxinfo, glxinfo, glxgears, amdcccle
```
    * as of 8.3 driver, you shouldn't have to blacklist the fglrx driver or add extensions or options to xorg.conf.

still get the following when running compiz. i assume it's the driver, not fully functional yet.
```
~$ compiz &
[1] 17687
Checking for Xgl: ubuntu:~$ not present. 
Detected PCI ID for VGA: 02:00.0 0300: 1002:71c7 (rev 9e) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

