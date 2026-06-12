---
title: "Unable to use my Mantis based dvb-s2 card  ( twinhan VP-1041 ) with the latest kernel"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by satfan39 on 2010-07-26
Hello,
 
I am trying to use my twinhan VP-1041 dvb-s2 card with kernel 2.6.32-24 using the latest drivers from v4l-dvb and s2-liplianin. 

I also tried to use my Vp-1041 card with both kernel 2.6.33-rc5 and kernel 2.6.34 but of course, without installing these external drivers since they are supposed to be "merged" in the kernels 2.6.33-rc5 and above ( see link below )

[http://lwn.net/Articles/370711/](http://lwn.net/Articles/370711/)

Result:
 
 
(a)  s2-liplianin and kernel 2.6.32-24 under Ubuntu Lucid
 
- Compiles OK
- All the modules load OK
- the adapter shows up under /dev/dvb/adapter0
- Unfortunately Kaffeine 1.0 pre3, tvheadend 2.11 and Mythtv crash, none of the three applications are able to use the adapter.
 
Note: It all worked fine with Ubuntu Karmic and kernel 2.6.30 and 2.6.31

 
(b) v4l-dvb and kernel 2.6.32-24 under Ubuntu Lucid
 
- Compiles ok
- All the modules load OK
- The adapter does not show up under /dev/dvb/adapter0...
 
Note: Same problem under Ubuntu Karmic
 
(c) Installing kernel 2.6.33-rc5 and 2.6.34 under Ubuntu Lucid
 
-  the adapter does not show up under /dev/dvb/adapter0 ( same symptoms than with the v4l-dvb tree)
 
Conclusion:
 
1)  It looks like my best chances are with the s2-liplianin, tree but for some reasons the current trunk version does not work with kernel 2.6.32-23 in my environement. It looks like I am not compiling this correctly, any specific compiling instructions for 2.6.32-24 ?
 
Please note that I had no issues under Ubuntu Karmic and kernel 2.6.30 and 2.6.31
 
2) I also noticed  that there a few mantis patches in the pipe for the v4l-dvb tree since January 2010, so it looks like it is becoming more up to date than s2-liplianin tree. Unfortunatelt I was never able to get my twinhan card recognised under ubuntu ( whatever the kernel version ) with the V4l-dvb tree. Any help would be appreciated here 
 
3) My understanding is that my dvb_s2 card should be automatically recognised with a kernel 2.6.33-rc5 and above...Unfortunately, it simply does not happen in my Ubuntu Lucid environment. 
 
Any help would be much appreciated.
 
Regards
Peter

---

### Post by satfan39 on 2010-07-26
Installing the package dvb-s2api-liplianin-dkms e works with kernel 2.6.32-24, but I do know why the other procedure fails;

From the terminal:

sudo -s
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6CF20474


Editing the /etc/apt/sources.list and adding the following lines :

deb h**p://ppa.launchpad.net/the-vdr-team/vdr-ubuntu-karmic/ubuntu/ karmic main

Then again from the terminal

apt-get update
apt-get install dvb-s2api-liplianin-dkms

Reboot

---

### Post by satfan39 on 2010-08-02
Ok, it works but not very well. The s2-lipianin vdr deb package that I mentioned in my previous post uses revions 14355 of the s2-liplianin tree. It tunes ok to dvb-s signals, but I get a lot of errors on all dvb-s2, 8psk signals which makes it useless.

In fact, it used to work 100% ok under kernel 2.6.28 - 2.6.30 and  Ubuntu Karmic using  revisions 12463 or inferior of the s2-liplianin tree. 

So it looks like that there is no way out at the moment under Lucid for that specific dvb-s2 card based on mantis drivers

- v4ldvb compiles and installs ok but card is not detected !

- s2-liplianin compiles and installs, but it does not work satisfactorily or event not at all with the lastest versions.

- The linux kernels containing all the good patches for that specific card is 2.6.35-rc 1 !! So, a long time to wait for ubuntu enthusiasts !

If someone succeeded to make it work with the V4l-dvb tree please let me know.

---

### Post by satfan39 on 2010-08-03
Solved

I am now able to use the v4l-dvb repository and/or kernels > 2.6.33-rc5 without additional modules.

The trick is to load the modules manually, they do not autoload like with the s2-liplianin tree

The order in /etc/modules is important, it must be the following:

stb0899
stb6100
lnbp21
mantis_core
mantis

Current v4l-dvb tunes very well.
Regards

---

### Post by Lampi on 2010-08-08
> **satfan39 said:**
> Current v4l-dvb tunes very well.
my 1041 tunes pretty poor on several frequencies (no lock for 20 seconds and more)

What sat equipment are you using?

---

### Post by satfan39 on 2010-08-09
Well, I am using:

Software:
- Unbuntu 10.04
- kernel 2.6.32-24

Hardware :
- Azurewave/twinhan vp-1041
- Azurewave/twinhan vp-1020
- dual core cpu ( E6850 I think ) at 3Ghz no overclovking
- Gygabythe motherboard with Nvidia geoforce 9 embeded, HDMI output
-  2 GB ram
- 1 TB HD

Testing Results with V4l-dvb drivers ( current trunk)
- tvheadend ( current trunk) : 
tunes ok on dvb-s and dvb-s2 transponders :D
- kaffeine-pre 3
tunes ok on dvb-s and dvb-s2 transponders :D
- Mythbuntu installed from Mythbuntu Control centre under ubuntu 10.04 :(
not ok, can not tune at all with my vp-1041 card !! Tunes ok with my vp-1020

Result with the s2-liplianin drivers ( current trunk )
- Kaffeine, tvheadend, mythbuntu not OK  with vp-1041 :( ok with vp 1020 :)

---

### Post by Lampi on 2010-08-11
What do you mean by "not okay"? kaffeine 0.8.7 should be able to tune the 1041 as well, but channel lock takes way to long. Sometimes kaffeine comes up with the "can't tune dvb" message, then you can retry this channel and most of the time you'll get instant lock at the second try.

Sounds to me like this driver is unfinished work yet...

---

### Post by satfan39 on 2010-08-12
Yes, I have used my vp-1041 sucessfully with Kaffeine 0.8.7 too. Looking at the changes in the v4l-dvb pipe it is clear that this driver is not finished.

Just a few questions :

b) Are you using the famous kaffeine-sc plugin or possibly sasc-ng in combination with a softcam ? Because if that is the case, this might be source of your tuning problems

c) Have you tried on FTA channels without any of those plugins / addons ? 

d) Is the tuning problem only on dvb-s2 channels or also on dvb-s 
channels ? 

e) Do you use s2-liplianin or V4l-dvb and which svn versions have you been using ? 

Regards

---

### Post by Lampi on 2010-08-13
b) The red viaccess cam runs pretty fine with kaffeine 0.8.7 - so there is no need to use a softcam. Most other hardware cams are reported as being unusable with the current driver.

c) yes, only on FTA channels. Many channels work, a bunch of frequencies cause constant trouble, especially when I need the diseqc sequence to switch from sat to sat. kaffeine 0.8.7 does let you send the sequence twice, but it won't change the problem.

d) dvb-s2 tunes especially fine and reliable, but with dvb-s2 the lock can get lost after some time for now obvious reason.

e) rev 14630 of s2-liplianin compiles fine, the later ones caused problems the last time I tried. I also tested the current v4l-dvb from linuxtv.org. Latest jusst.de/mantis does load the modules, but /dev/dvb/[xxx] is not created with a 2.6.32 kernel. It doesn't change the problem - both driver sources I could test have the same tuning issues for months now...

I guess I could try to play with the "tuning timeout" setting kaffeine 0.8.7 offers ... because lock sometimes takes like 30 seconds to establish (tested with vdr and szap)

It's possible kaffeine with default "tuning timeout" does not wait long enough for lock to be gained.

There is obviously some code cleanup left to do in the tuning part of this driver.

---

### Post by satfan39 on 2010-08-15
I suggest that you upgrade to Ubuntu Lucid Lynx 10.04 and install Kaffeine 1.0.0 pre3 ( available in de the synaptic reposirory of Ubuntu Lucid ) and also compile the latest version of v4l-dvb ( not s2-liplianin ! ). This works OK with Kaffeine in my environment ( including with sasc-ng and softcams ). The only issue is that some dvb-s2 services get detected several times during the scan, hence increasing the time needed to perform a full scan.

If the /dev/dvb/adapterX do not get created in your environment, check the work arround available at [http://dolot.kipdola.com/wiki/Install_S2API](http://dolot.kipdola.com/wiki/Install_S2API)   ( see $ 3.0 updating udev )



Regards

---

### Post by Lampi on 2010-09-28
> **satfan39 said:**
> and also compile the latest version of v4l-dvb ( not s2-liplianin ! ).
With v4l-dvb this card will tune worse than with s2-liplianin, but there's a patch in [linux-media]("http://www.spinics.net/lists/linux-media/msg23181.html") that basically ports the good stuff from liplianin to v4l-dvb so tuning is faster with 1041

---

### Post by alien878 on 2010-10-13
I just upgraded to 10.10 as the mantis drivers are supposed to be in the kernal (previously had it working in 9.10 with s2-liplianin).

It seems the device is recognized in lspci, but udev doesn't seem to pick it up.  I tried the work-around in the second post with no luck.  Any ideas?

My lspci output:
```
01:05.0 Multimedia controller: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] (rev 01)
        Subsystem: TERRATEC Electronic GmbH Device 1179
        Flags: bus master, medium devsel, latency 64, IRQ 15
        Memory at dffff000 (32-bit, prefetchable) [size=4K]
```I think this is the relevant udev log info:
```
UDEV  [1286995992.036881] add      /devices/pci0000:00/0000:00:09.0/0000:01:05.0
 (pci)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:09.0/0000:01:05.0
SUBSYSTEM=pci
PCI_CLASS=48000
PCI_ID=1822:4E35
PCI_SUBSYS_ID=153B:1179
PCI_SLOT_NAME=0000:01:05.0
MODALIAS=pci:v00001822d00004E35sv0000153Bsd00001179bc04sc80i00
SEQNUM=1410

```
Update: Just checked my working udev log.  The above is the same, but it is followed later with this which is not in the non-working log:
```
UDEV  [1286997946.292455] add      /module/mantis (module)
UDEV_LOG=3
ACTION=add
DEVPATH=/module/mantis
SUBSYSTEM=module
SEQNUM=1521

KERNEL[1286997946.309119] add      /devices/pci0000:00/0000:00:09.0/0000:01:05.0/dvb/dvb0.demux0 (dvb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:09.0/0000:01:05.0/dvb/dvb0.demux0
SUBSYSTEM=dvb
DEVNAME=dvb/adapter0/demux0
DVB_ADAPTER_NUM=0
DVB_DEVICE_TYPE=demux
DVB_DEVICE_NUM=0
SEQNUM=1523
MAJOR=212
MINOR=0

```

---

### Post by Lampi on 2010-10-14
alien878: the driver in 2.6.33 simply sucks:

- slow tuning
- unreliable
- does not load the mantis module -> /etc/module entry required

There is ongoing work to improve the mantis driver for the kernel 2.6.37 pull

Until then you either stick with s2-liplianin rev 14630 or you patch v4l-dvb with numerous patches from the linux-media mailing list.

---

### Post by alien878 on 2010-10-14
Thanks Lampi.

Just before you posted, I discovered that modprobe mantis is required.  However, I've already gone back to 9.10 which is the last version where I could get it working.  Even that is frozen on an older kernel because I can't get s2-liplianin to work in the latest 9.10 kernels.

Kernel 2.6.37 looks like ubuntu 11.10.  Maybe I'll give the linux-media mailing list patches a try before then (Although I find the people on the linux mailing lists a little hard-core sometimes.... and that is coming from someone that longs for the days of rn)

---

### Post by Lampi on 2010-10-14
@alien878: basically you need the tuning improvement patch i posted right about your initial post, then you need [this patch]("http://jusst.de/hg/mantis-v4l-dvb/raw-rev/3731f71ed6bf") to load the mantis module using udev.

There are more patches concerning the 1041 on the linux-media ML, but these two patches should cover what you asked for.

s2-liplianin won't work with the latest tree because of unsolved problems with the remote support, so you need to revert to revision 14630.

---

### Post by alien878 on 2010-10-14
Do you think using hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) would get me workable drivers in 10.10?  Or am I better off figuring out how to get the v4l-dvb sources used in 10.10 and applying the patches you list?

Thanks!

---

### Post by Lampi on 2010-10-14
I recommend you use s2-lipianin rev 14630:

```
cd /usr/local/src
hg clone -r 14630 http://mercurial.intuxication.org/hg/s2-liplianin s2-liplianin-rev-14630
cd s2-liplianin-rev-14630
sudo make menuconfig #unselect firedtv, it won't build with firedtv enabled
make -j 2
sudo make install
#reboot your system
```
it will tune fast, it will auto load the mantis module, the remote will work (again)

What else you need as of right now? All I can say is: the mantis support in v4l-dvb is poor, might improve with 2.6.37 (if the changes are accepted)

---

### Post by satfan39 on 2010-10-15
Well, I must confess I have been too optimistic in my first post.  I unfortunately confirm that this dvb-s2 card ( vp-1041 from twinhan ) does not work correctly with any of the applications that I mentioned earlier in my post. 

With s2-liplianin r 12469 and kernel 2.6.31, all channels are tuning but it is unstablle, and after a while, the cards stops tuning, and the only solution is to reboot !  I have observed this behavior with Kaffeine-pre3, tvheadend and mythtv ( did not test Yavdr though ) 

Using kernel 2.6.35 stable or even 2.6.36-rcx ( those two kernels include natively the v4l-dvb drivers) , does not solve the problem. I confirm it's worse than s2-liplianin. I is very unreliable in the sense that some transponders do not get tune for some strange reasons ( the tuning speed is probably to slow for the application). The slowtuning speed and the reliability issues makes the card unusable. For instance with mythtv ( whatever the version ), it is impossible to use disecq correctly, it will stick on hobird 13, impossible to switch astra 19.2E ! 

I will try s2-liplianin 14630 as suggested above and report here if the situations has improved. Will also try to patch the V4l-dvb drivers with the linux-media patches mentioned above, provide that I succeed to identify them all ( any help would be apprecaited here )

---

### Post by alien878 on 2010-10-15
satfan39:  I have the VP-1041 working fine using ubuntu 9.10 and the older 2.6.31-21 kernel.  It would not work on the current 2.6.31-22 kernel.  Just install and run startupmanager to change the default kernel to boot it and re-install s2-liplainin.  I used s2-liplianin as described here:

[http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_S2_PCI_HD_CI#Making_it_work](http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_S2_PCI_HD_CI#Making_it_work)

I'm not sure which version, but it was default on May 9 when I grabbed it.

I'm going to try to upgrade to 10.10 on the weekend and see how Lampi's patches work.

---

### Post by dabujo on 2010-10-15
> **Lampi said:**
> There is ongoing work to improve the mantis driver for the kernel 2.6.37 pull

Until then you either stick with s2-liplianin rev 14630 or you patch v4l-dvb with numerous patches from the linux-media mailing list.
I want to use my mantis card in 10.10 and I have no experience with handling manual installation etc.
Can I expect the right drivers to be included in the 2.6.37 ubuntu kernel and how long will it take until I get that version?
Im sorry I have to ask these basic questions but I'm really in a bad position here.

---

### Post by Lampi on 2010-10-15
@dabujo: there's an easy solution for you - install the yavdr/testing repository using dkms:

```
sudo add-apt-repository ppa:yavdr/testing-vdr
sudo aptitude update
sudo aptitude install v4l-dvb-dkms
sudo reboot
```This will install v4l-dvb with the patches I mentioned to improve the 1041 tuning.

If you prefer s2-liplianin install it using dkms:
```
sudo aptitude install s2-liplianin-dkms
```

---

### Post by alien878 on 2010-10-16
Yeah!  I got it working on 10.10.

[LIST=1]
[*]ppa:yavdr/testing-vdr didn't work because there is nothing in it for maverick
[*]I tried to apply Lampi's patches to the latest v4l, but there were too many divergences and I didn't feel like reverse engineering them.
[*]I tried s2-liplianin rev 14630, but it wouldn't compile.  Even after I removed all the problem cards I could, I finally got stuck on dvb_net.c which I think is needed.
[*]I finally tried the latest s2-liplainin following lucid instructions at [http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_S2_PCI_HD_CI#Making_it_work](http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_S2_PCI_HD_CI#Making_it_work) and it worked!
[/LIST]

Thanks all for the support.

EDIT:  Note that I have this working with kernel 2.6.35-22 (the original kernel delivered with 10.10).  I have locked/pinned linux-generic, linux-headers-generic and linux-image-generic in synaptic, so I can say how it works with other kernel versions.

Allen

---

### Post by satfan39 on 2010-10-16
As far as I am concerned, I tried ubuntu 9.10 with kernel 2.6.31-21 with s2liplianin svn 12463 ( Dolot site ), svn 14630 ( as recommended here ) and trunk
.

No compilation or installation issues, but it does not work satisfactorily at all, no improvements over the past situation. The vp-1041 is detected but tuning is slow and unreliable. 

I also tried ubuntu 10.10 § maverick with kernel 2.6.35.2, trunk of s2-liplianin and no improvements éither   

 I have two other cards ( dvb-s vp-1020a and twin tuner dvb-s2 bs6981) that work perfectly in the same environment.... so I am starting to think that the problem is the tuner of vp-1041 that might be "burned" or "damaged"

Sill need to try the V4l-dvb with the latest patch for stb0899, this is my last chance to get it working.

---

