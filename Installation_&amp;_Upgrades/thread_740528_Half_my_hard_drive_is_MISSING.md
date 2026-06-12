---
title: "Half my hard drive is MISSING???"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by rookie4evr on 2008-03-30
Ok..this is frigin weird ....
I installed Ubuntu on my Laptop .....
which has 50 GB hard dirve....
I put half for XP and half for Ubuntu ....
after it completed the process ....
laptop restarted ...now I have the option to go to "Ubuntu" and "XP"
XP... working fine ...
then Ubuntu ... ALL I GET IS A BLACK SCREEN ......
So, I know i did something wrong ...
so ... I reformated the laptop with recovery disk ....
bad luck for me .. only half my hard drive is showing ....
even after reformating ... don't know what the hell happned to the other half ...some PLEASE HELP!!!!!!!!

---

### Post by rookie4evr on 2008-03-30
Anyone please help ......

---

### Post by Pumalite on 2008-03-30
Boot your Live CD. From the Terminal, post
sudo fdisk -lu

---

### Post by rookie4evr on 2008-03-31
"Boot your Live CD. From the Terminal, post
sudo fdisk -lu"

I reformated the comp ... I only have half the hard drive which has XP ...
the half which had UBUNTU ..is gone ..
I don't even get the option to choose which OS I want ...
I am still thiking that ... some where .. the 25GB which have Ubuntu is LOST...

and to your solution ...
u want me to just enter the live CD and 
what do u mean by terminal ???????
are u talking about the boot perameter here?????
where u press "F6" and a command ??????. 
Please i am new to this whole ubuntu .....

---

### Post by PmDematagoda on 2008-03-31
Just boot the Live CD, you do not have to enter any boot parameters, once the Live CD has started up and you are in the desktop just enter the commands provided by Pumalite in a terminal and post the results here.

---

### Post by rookie4evr on 2008-03-31
will give it a try

---

### Post by rookie4evr on 2008-03-31
Guys.... I went into the window of ,"Ububtu" and typed the command that u guys told me to enter in "terminal" ..here is the result ...



To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0464b6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    53849879    26924908+   7  HPFS/NTFS
/dev/sda2       109820340   117210239     3694950    5  Extended
/dev/sda3        53849880   109820339    27985230   83  Linux
/dev/sda5       112326543   117210239     2441848+  82  Linux swap / Solaris
/dev/sda6       109820466   112326479     1253007   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by rookie4evr on 2008-03-31
:(some one help me please ...????/

---

### Post by PmDematagoda on 2008-03-31
The reason you may be seeing only half a drive on Windows is because Windows is incompatible with Ext3(the filesystem Ubuntu uses as default).

Just rerun the installer and instruct it to install itself to the supposedly missing half and that should fix the problem.

Also could you post the specifications of your laptop.

---

### Post by rookie4evr on 2008-03-31
"The reason you may be seeing only half a drive on Windows is because Windows is incompatible with Ext3(the filesystem Ubuntu uses as default).

Just rerun the installer and instruct it to install itself to the supposedly missing half and that should fix the problem.

Also could you post the specifications of your laptop."

I don't understand what u are trying to say here ...
so you want me to actually run 
the "recovery cd of the window" on my laptop ?????

---

### Post by Pumalite on 2008-03-31
You can install this driver in Windows to see Ubuntu:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by rookie4evr on 2008-03-31
so.. all i have to is ..just install this program on my laptop ?????

---

### Post by rookie4evr on 2008-03-31
"You can install this driver in Windows to see Ubuntu:
http://www.fs-driver.org/"


I installed the program ... 
I can see ubuntu part of the hard drive in window xp ...


SO, what is the next step ????
I restarted the comp and try to see if I can get into Ububtu window...
well it is not giving me the option .....

---

### Post by Pumalite on 2008-03-31
et Super Grub and see if you can boot Ubuntu:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by rookie4evr on 2008-03-31
:mad:"et Super Grub and see if you can boot Ubuntu:
http://users.bigpond.net.au/hermanzo...bdiskpage.html"


Hmmm thanks for the info ...
something interesting happened ......
the first time I splited my hard into two for window and ubuntu ....
window worked...and for Ubuntu ... I got BLACK screen everytime I try to boot into Ubuntu ....

I reformaated my laptop and thought it would help me .... :confused:
bad time .... It did not ....
Atleast before I had the choise to go to Ubuntu eventhough I get a black screen ..after I reformated my laptop ... I dont even get a choise .... it boots me to strait to window ...with half my hard drive missing ... after installing Suer Grub ....
I boot it up .. it recognized that I have ubuntu .... but when I try to boot into it ... I am getting the same problem ...
getting a BLACK SCREEN ..when I choose ubuntu .....

CAN SOME MOD help me with this problem i am facing please ....
what can i do to .. get rid of this black screen that is pissing me off....

---

### Post by rookie4evr on 2008-04-01
Black screen I am getting, can it be because of my video card????

---

### Post by sweeny on 2008-04-01
> **rookie4evr said:**
> Black screen I am getting, can it be because of my video card????

What is the configuration of your laptop ?

Well many nvidia users have this problem. AMD users have a tough time too.

---

### Post by rookie4evr on 2008-04-01
hmmm I think mine is AMD laptop ..

Manufacturer "ATI technologies inc."
Chip Type: ATI RADEON XPRESS 200M Series

---

### Post by polmir on 2008-04-01
**rookie4evr**
Put Your cd with Ubuntu to cdrom and run it.
After system run.
Click and run Terminal (Applications->Accessories->Terminal)
Type in terminal:
```
lspci
```
and post output of it.

---

### Post by rookie4evr on 2008-04-01
here is the output ... 


00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
05:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
ubuntu@ubuntu:~$

---

### Post by PmDematagoda on 2008-04-01
Did you attempt to boot Ubuntu through Recovery Mode? If so, does it bring you to a command prompt?

---

### Post by rookie4evr on 2008-04-01
no, i tired the recovery mode too:( ...
just freeze after doing some text based commands ....

---

### Post by rookie4evr on 2008-04-01
I think it could be the video card problem.
anyone know how to fix this problem ...
cause I did install ubunbu *fully on my laptop before) ...

---

### Post by rookie4evr on 2008-04-01
:confused:

I don't know what is going on here .... but*
When I chose, "Ubuntu" to start up ...as usual it gave me the black screen ...
then ... for the hell of it ... I  pressed, "CTRL + ALT + (F6 or F7) .....
it skipped the boot up process and ended up going to the login screen of ubuntu ....
just did the update ..don't know if i can get back in this ubuntu window or not .....:(
anyone know what is going on here...why my ubuntu boot up menu is not working????

---

### Post by rookie4evr on 2008-04-01
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report"



Ok .... I typed the command, " dpkg --configure -a " without the ("") in terminal ...
the output is this ....


rookie@rookie-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
rookie@rookie-laptop:~$ 


I did enter with my user name and my pass word .....

---

### Post by oldos2er on 2008-04-01
sudo dpkg --configure -a

---

### Post by rookie4evr on 2008-04-01
"sudo dpkg --configure -a"

thanks for the info .... it worked.....

and also, I need help with getting the ubuntu boot screen ...
anyone know what I can do to fix the problem...

---

### Post by rookie4evr on 2008-04-01
I typed in "lspci" ...

"rookie@rookie-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
05:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
rookie@rookie-laptop:~$ 
"

can some one tell me what is kind of video card I have ... from the out put..cause I need to download the "Beryl" .... for ubuntu ....

---

### Post by Pumalite on 2008-04-01
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

---

### Post by rookie4evr on 2008-04-01
I found this link, 
[https://bugs.launchpad.net/xorg-server/+bug/144297](https://bugs.launchpad.net/xorg-server/+bug/144297)

this person had the EXACT same problem as me.....
and he removed something ... can some one tell me what he removed ...the step by step to remove it ......

---

### Post by rookie4evr on 2008-04-02
anyone :confused:

---

### Post by macogw on 2008-04-02
In recovery mode, he typed
```
rm /lib/modules/2.6.22-12-generic/kernel/drivers/char/drm/radeon.ko
```

but don't do that...might want it later for 3D stuff

The not-so-permanent way to do it is to use ```
nano /etc/X11/xorg.conf
``` (that's a big X and two ones...yes, capital matters) in recovery mode and scroll to Device section that lists your video card.  Add a line in there that says ```
Option     "DRI"     "off"
``` just like all the other Option lines in that section.  Save & quit by hitting Ctrl+O and then Ctrl+X  Then you can reboot the computer by just typing "reboot" and see what happens.  Good luck!

---

### Post by rookie4evr on 2008-04-02
after typying what u told me ... the last part,


"...Then you can reboot the computer by just typing "reboot" and see what happens."


I typed in "reboot" without the "" .... 
under, "End Selection" ... nothing is happening ????
little help please.....I am still in safe mode .....

---

### Post by Boyohazard on 2008-04-02
You need to save and quit out of the xorg.conf file then type reboot at the prompt

---

### Post by rookie4evr on 2008-04-02
"Option     "DRI"     "off""


NOOO
this is not good .... after I typed this command code in the safe mode and "SAVED IT" .... and went back into normal Ubuntu .....
the screen started to LAG!!!!!!!!!!!
So, I went back and took it off....
still it is LAGGIE!!!!!!
and my special effect is not working ....

then uncheck the box with ATI 3d graphic and rebooted the comp ... now the 3d effect is working but till my SCREEN IS LAGGIE!!!!!!!!!!

---

### Post by rookie4evr on 2008-04-02
:(

---

### Post by rookie4evr on 2008-04-02
Hey ..guys... 
when I press "CTRL + ALT+ F6" to skip the boot menu of ubuntu ....
this is giving me a message ......

8139C+ competable ship is not the right drive but try 8139too driver instead ??????

anyone know what this all about ...

---

### Post by rookie4evr on 2008-04-02
Aray ...iam not getting any sound from the laptop
here is my output from the terminal ..can someone help please ..

"
rookie@rookie-laptop:~$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: SB450 HDA Audio
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel
rookie@rookie-laptop:~$ " 


..........

---

### Post by rookie4evr on 2008-04-03
can someone please tell me how i can solve my volume problem please.......

---

