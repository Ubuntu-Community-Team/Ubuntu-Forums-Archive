---
title: "Can't install Ubuntu 9.10 on Lenovo T510"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by rozmar564 on 2010-02-17
Hi Guys -

I cant install Ubuntu 9.10 in normal graphics mode on my T510.

This is my config i5-520M(2.4GHz), 2GB RAM, 320GB 7200rpm HD, 15.6in 1366x768 LCD, Intel HD Graphics, CDRW/DVDRW, Intel 802.11bgn wireless, WWAN. 
If I choose to perform a normal install after a few minutes the CD stops spinning and I'm stuck with a blank screen forever. 
However if I choose the safe graphics mode install I can install the OS but then I cant switch to use the intel driver. So my guess is that I have a graphics issue at install time. I add the xorg-edge (PPA) but I am just not able to configure my video.

Any ideas who could I fix this?

---

### Post by chaanakya_chiraag on 2010-02-17
Almost certainly a problem with the Intel graphics driver.  Have you tried 9.04 (Jaunty), 8.04.4 (Hardy), or 10.04 (Lucid, **under development**)?  You can download 9.04 and 8.04.4 from here: [http://releases.ubuntu.com]("http://releases.ubuntu.com")
and 10.04 from here: [http://ubuntu.com/testing]("http://ubuntu.com/testing")

---

### Post by rozmar564 on 2010-02-17
8.04 does not recognize anything. No network, no video, no blue tooth.

9.04 - downloading it as I write this reply :)

10.04 - if nothing will work might try it.

Thx.

---

### Post by chaanakya_chiraag on 2010-02-17
No problem!  Hope it works out well!  If not, post what's happening and we can see what's going on :)

---

### Post by rozmar564 on 2010-02-17
It seem that the issue is solved.

This is a quick list of what I did ::

1. - clean install (9.10)
2. - added [http://ppa.launchpad.net/xorg-edge/ppa/ubuntu](http://ppa.launchpad.net/xorg-edge/ppa/ubuntu) and [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) to the software sources.
3. - after reloading sources sudo apt-get update
4. - this is how I needed to set up my xorg.conf
Section "Device"
        Identifier      "Configured Video Device"
#       Driver          "vesa"
BusID "PCI:0:2:0"
Driver "intel"

EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
5. - needed to modify /etc/xdg/compiz/compiz-manager
# Ubuntu specifc compiz-manager configuration file
# goes into /etc/xdg/compiz/compiz-manager
# works with git://anongit.compiz-fusion.org/fusion/misc/compiz-manager
COMPIZ_BIN_PATH="/usr/bin/"
PLUGIN_PATH="/usr/lib/compiz/"
COMPIZ_NAME="compiz.real"
INDIRECT="yes"
6. - reboot.

This did it for me.

---

### Post by FFFred on 2010-02-17
See this post for better graphics with 2.6.32 kernel :
[http://ubuntuforums.org/showpost.php?p=8826832&postcount=15](http://ubuntuforums.org/showpost.php?p=8826832&postcount=15)[URL="http://ubuntuforums.org/showpost.php?p=8826832&postcount=15"]
[/URL]

---

### Post by chaanakya_chiraag on 2010-02-17
If your issue is fixed, please mark this thread as solved (Thread Tools -> Mark as Solved) to make it easier for others with this issue to find a solution.  Thanks :)

---

### Post by vxg on 2010-03-11
Hello.
 
I Just bought a similar T510 and I also have a similar problem. The difference is that I cannot even install Ubuntu because I get a black screen before I can get to the installation wizard. For example, if I try to boot from the Cd, then I can hear the Ubuntu characteristic sound, but I see nothing on the screen. 
 
I am not very experienced using Ubuntu, can anyone help me ?

---

### Post by rozmar564 on 2010-03-11
vxg :: when you boot from the Live CD - choose the Safe Graphics Mode (I think you can do that by hitting F4). Install in safe graphics mode - then follow my instructions from a few posts earlier.

Cheers.

---

