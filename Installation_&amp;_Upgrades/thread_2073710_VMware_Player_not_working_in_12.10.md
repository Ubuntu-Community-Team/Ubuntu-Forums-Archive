---
title: "VMware Player not working in 12.10"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by dom134 on 2012-10-20
Hello, I have just upgraded from 12.04 to 12.10, but when it came to running VMware Player 5.0.0, the application just stops.

After googling, it appears to be a known issue for 12.10
[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop#QuantalQuetzal.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.VMware_Player](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop#QuantalQuetzal.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.VMware_Player)

Has anyone else managed to get it to work or is it a case of finding a new VM?

---

### Post by stbub on 2012-10-20
When I try to run VMplayer 5.0.0 on Ubuntu 12.10, the player starts, but at some point during startup the graphics mode gets messed up and the screen becomes all unreadable.

---

### Post by astrotest on 2012-10-21
It works!
Look here for the solution - [http://communities.vmware.com/message/2103172#2103172](http://communities.vmware.com/message/2103172#2103172)

Just download the patch, unpack it, make the script executable an run it :)([http://communities.vmware.com/servlet/JiveServlet/download/2103172-94260/vmware9_kernel35_patch.tar.bz2](http://communities.vmware.com/servlet/JiveServlet/download/2103172-94260/vmware9_kernel35_patch.tar.bz2)).
Enjoy!

---

### Post by dom134 on 2012-10-21
Thanks [astrotest]("http://ubuntuforums.org/member.php?u=977420"), works a treat!  I was being a biff; I had previously had to patch VMware Player last year, but had forgotten all about it!

Once again thanks.

---

### Post by foxy202 on 2012-10-21
Hi 
  I got same problem ... after many many try I found that 
vmmon is broken and cannot be removed from rmmod... so 
my solution was 

  1. unzip vmware9_kernel35_patch.tar.bz2 
  2. delete /lib/modules/3.5.0-17-generic/misc/vmmon.ko
  3. restart 
  4. start patch 

.... and I am happy vmware user :)

hope that help

regards

---

### Post by PirateFanAZ on 2012-10-21
> **astrotest said:**
> It works!
Look here for the solution - [http://communities.vmware.com/message/2103172#2103172](http://communities.vmware.com/message/2103172#2103172)

Just download the patch, unpack it, make the script executable an run it :)([http://communities.vmware.com/servlet/JiveServlet/download/2103172-94260/vmware9_kernel35_patch.tar.bz2](http://communities.vmware.com/servlet/JiveServlet/download/2103172-94260/vmware9_kernel35_patch.tar.bz2)).
Enjoy!

Thanks astrotest.  I wanted to post as I had to modify the script for my scenario.  I have multiple vmware products installed.  so vmware-installer -l returned the vmware VIX product before vmware-player and the script set the vmver variable using the VIX product.  The script failed.

I hacked the the script.  I changed the line:

vmver=`vmware-installer -l 2>/dev/null | awk '/vmware-/{print $1substr($2,1,5)}'`

to

vmver=`vmware-installer -l | sed -n '4p' | awk '/vmware-/{print $1substr($2,1,5)}'`

to get the vmver variable set with my installation of vmware player.  This is a hack, I'm not much good at scripting, but it worked for me.  If others are experiencing this script failing when you have the correct version of either product installed check the output of vmware-installer -l to ensure your product is returned first and correctly.

---

### Post by sturdy on 2012-11-02
Thanks guys...works great. My problem occurred after upgrade to 12.10.

---

### Post by dannyvanderzande on 2012-11-03
I can't get it to work.
I've been at it for at least 5 hours, reinstalled VMware 9 at least 8 times and tried patching it for I guess 15 times.

Everytime I run the patch I get an error saying I don't have the correct version of VMware (which im 100% positive I do) or I get an error saying VMWare VMX is still running even though there are not VMWare services running...

Can someone please help me out because I can't figure it out myself..

---

### Post by nvjopsddhapnv on 2013-02-04
Thanks a lot it works for me also.

---

