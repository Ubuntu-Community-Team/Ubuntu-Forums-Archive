---
title: "Kernel 2.6.30 uploaded to karmic"
date: 2009-04-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by int on 2009-04-28
Kernel 2.6.30rc3 uploaded to karmic


> linux (2.6.30-1.1) karmic; urgency=low

 * Initial release after rebasing against v2.6.30-rc3

Date: Thu, 12 Mar 2009 19:16:07 -0600
Changed-By: Tim Gardner <xxx>
Maintainer: Ubuntu Kernel Team <xxx>
[https://launchpad.net/ubuntu/karmic/+source/linux/2.6.30-1.1](https://launchpad.net/ubuntu/karmic/+source/linux/2.6.30-1.1)

--
Karmic-changes mailing list
[email]Karmic-changes@lists.ubuntu.com[/email]
Modify settings or unsubscribe at: [https://lists.ubuntu.com/mailman/listinfo/karmic-changes](https://lists.ubuntu.com/mailman/listinfo/karmic-changes)

---

### Post by Slug71 on 2009-04-28
Nice, im glad theyve decided to do this early on in the dev cycle this time.

---

### Post by autocrosser on 2009-04-28
Very good to see---I've played with it via the kernel tree, but it will be nice to have it be "real" :P:P

---

### Post by portis on 2009-04-28
Unfortunately, KMS is disabled.

---

### Post by cecilpierce on 2009-04-28
How can I get the new kernel in the repo's ?
Or how do I do it ? Thanks

---

### Post by Gina on 2009-04-28
Updating Karmic should do it.

---

### Post by jfernyhough on 2009-04-28
It might take a little while to get to you. One, it will take some time to be built after being uploaded. Two, it takes some time for mirrors to pick up the changes in the repo.

e.g. I don't see 2.6.30 yet, and I'm using the main archive. I might try an alternate, but it would be further away. :)

---

### Post by Mehall on 2009-04-28
Just updated Karmic, no kernel pushed yet.

I'll try again tomorrow.

BTW: Just got word Gnome is about to be uploaded shortly, and apparently there is a HIGH chance it will break stuff (aww, karmic's first breakage, how cute :D) so watch out every1. (Doesn;t affect me, my karmic box has openbox, though I might make a gnome one too)

---

### Post by meeples on 2009-04-28
how do i get karmic? i really want to help test it. i tried update-manager -d.. lol didnt work.

---

### Post by Mehall on 2009-04-28
> **meeples said:**
> how do i get karmic? i really want to help test it. i tried update-manager -d.. lol didnt work.

that only works on full releases, not even for Beta's, IIRC.

You need to edit the file /etc/apt/sources.list and make all the entries say "karmic" instead of "jaunty", then update and upgrade from Synaptic/update-manager of choice.

If it's your first time, I would advise waiting till the Alpha 1 is out, if I'm honest.

---

### Post by meeples on 2009-04-28
thanks. i dunno i mite wait till alpha, but i like throwing myself in at the deep end. its fun  :P

---

### Post by Mehall on 2009-04-28
Using an Alpha isn't exactly the shallow end ;)

---

### Post by meeples on 2009-04-28
too late, updated :P

---

### Post by TheForkOfJustice on 2009-04-28
What does 2.6.30 offer over what's in Jaunty?

---

### Post by Mehall on 2009-04-28
There are a LOT of things. Biggest among them seems to be faring a LOT better in many benchmarks for multiple things.

Jaunty uses 2.6.28, and a LOT of changes were brought in in .29, which continued in .30

Chief among them were fixing many regressions that had occured, and introducing support for WiMAX

---

### Post by autocrosser on 2009-04-28
Kernel is up on the main server. 5:50 Pacific time.

---

### Post by mc4100 on 2009-04-28
First real chance to dive in since updating to Karmic -- been *trying* to learn LaTeX.
You'll need to install .30 manually for now. It should be default soon enough.

---

### Post by Toe on 2009-04-29
For me the kernel crashes quite late in the boot process, complaining about a null pointer dereference, if I remember correctly.

There doesn't seem to be a bug report yet, so I think I'll need to write the messages down and file one.

Does this problem occur on anyone else's machine?

---

### Post by Slug71 on 2009-04-29
> **portis said:**
> Unfortunately, KMS is disabled.

That sucks. Probably still waiting on drivers.

---

### Post by autocrosser on 2009-04-29
Update to the kernel already---2.6.30-1-2-generic

6:50 Pacific time

---

### Post by jerrylamos on 2009-04-29
The local mirror here had 2.6.30-1 ready for synaptic apply.

On intel integrated graphics i845 "AccelMethod" "uxa" produces garbled display on glxgears, and YouTube videos are jerky.

Slower without "uxa".

It worked, tho.  We'll see about Alpha.  intel graphics broke on Intrepid requiring "NoAccel" until after ship, also broke on jaunty until just before beta.  Hardy's faster however jaunty has a lot more "polish" from my view.

Thanks for putting the karmic linux image out.

Jerry

---

### Post by rudenko_ruslan on 2009-04-29
> **autocrosser said:**
> Update to the kernel already---2.6.30-1-2-generic

6:50 Pacific time
Huh, I still have 2.6.28-11-generic :(

---

### Post by autocrosser on 2009-04-29
Manual install & make sure you are using the main sources---

---

### Post by Starks on 2009-04-29
For KMS on Intel.

* Latest xserver-xorg-video-intel 2.7.99 driver from Xorg Edgers PPA
* Add 'i915 modeset=1' to /etc/modules **OR** before X loads, manually do 'modprobe i915 modeset=1'

---

### Post by plun on 2009-04-29
> **rudenko_ruslan said:**
> Huh, I still have 2.6.28-11-generic :(

Use Synaptic and search for **linux-image** and **linux-headers**  :)


The meta-package isn't there yet...

---

### Post by plun on 2009-04-29
> **Toe said:**
> For me the kernel crashes quite late in the boot process, complaining about a null pointer dereference, if I remember correctly.

There doesn't seem to be a bug report yet, so I think I'll need to write the messages down and file one.

Does this problem occur on anyone else's machine?


Yup, on mine and I have reported this earlier with Kerneloops to upstream.
(not Ubuntu)

---

### Post by mc4100 on 2009-04-29
> **Starks said:**
> For KMS on Intel.

* Latest xserver-xorg-video-intel 2.7.99 driver from Xorg Edgers PPA
* Add 'i915 modeset=1' to /etc/modules **OR** before X loads, manually do 'modprobe i915 modeset=1'
I thought I'd give KMS another try: the Edgers drivers work fine, and I modified /etc/modules (is this definitely the recommended way, as opposed to modprobe.d, which I think I've seem somewhere before?) and it seems to work well, but the only way I could get plymouth to work (on 945GME) was by using vga=... but I'm convinced that's not right!
Any thoughts?
( Damn, I wish they'd just switch to KMS and Plymouth already, so I don't need to guess. )

Edit: By the way ... plymouth, is amazing!

---

### Post by Toe on 2009-04-29
@plun:
Are you running openvpn?

On my machine, I've narrowed it down to this service.

The 2.6.30 kernel works fine for long periods of time, but within two seconds of "/etc/init.d/openvpn start", it crashes.


Edit: The server at kerneloops.org doesn't seem to respond, so I've opened a bug at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369415](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369415)

---

### Post by Ubuntu Terrier on 2009-04-29
I installed the new Kernel on an Intel G45 mainboard, no problems until now, but also apparently no visible change that I can see. Maybe it boots even faster than 9.04 with the 2.6.28 kernel, but that could be only my imagination.

I read somewhere that the new kernel has new Intel video drivers. So I tried setting up UXA acceleration, which works fine (glxgears reports less fps than before, though), but hasn't solved the ugly tearing problem with videos. I would have liked to try the kernel modesetting introduced in 2.6.29 too, but I have no clue on how to activate it.

It would be nice to read a full list of 2.6.30rc3 kernel changes, anyway.

---

### Post by plun on 2009-04-29
> **Toe said:**
> @plun:
Are you running openvpn?

On my machine, I've narrowed it down to this service.

The 2.6.30 kernel works fine for long periods of time, but within two seconds of "/etc/init.d/openvpn start", it crashes.


Edit: The server at kerneloops.org doesn't seem to respond, so I've opened a bug at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369415](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369415)


OK.... I have my crash during boot

```
BUG: unable to handle kernel NULL pointer dereference at 0000000000000020

```

[http://paste.ubuntu.com/160939/](http://paste.ubuntu.com/160939/)

You can probably see yours within kern.log.

---

### Post by andrewabc on 2009-04-29
Jaunty shipped with 2.6.28-11
2.6.29 was released around March 23.
2.6.30 RC3 is out, and I think they normally get a dozen or so RC before release. So 2.6.30 should be released in a month or two? So the question is whether ubuntu will use 2.6.30 or 2.6.31 in 9.10 (time will tell)?

---

### Post by Nullack on 2009-04-29
The kernel version for release will be decided at UDS.

---

### Post by ronacc on 2009-04-29
I can't even start the boot with 2.6.30-1-generic, error file not found from grub !  the files are there initrid.img and vmlinuz etc and I reinstalled them just to be sure . boots fine with 2.6.28-11 . any ideas ?

---

### Post by autocrosser on 2009-04-29
Did you mod menu.lst yourself or let grub do it?  I did a manual & edited menu.lst myself & everything starts good...can't trust grub to do it with my "penti-boot" system :P

---

### Post by ronacc on 2009-04-29
I moded the menu.lst myself , my grub is on another drive and install , I just cloned my working stanza and changed 2.6.28-11 to 2.6.30-1 , that has always worked before .

---

### Post by caryb on 2009-04-29
> **ronacc said:**
> I moded the menu.lst myself , my grub is on another drive and install , I just cloned my working stanza and changed 2.6.28-11 to 2.6.30-1 , that has always worked before .

I had to do the same! For the last few kernel updates I have had this problem.


Cary

---

### Post by ronacc on 2009-04-30
Well I tried purging all 2.6.30 files (including manualy deleting the /var/cache/apt packages ) and reinstalling , same result grub gives an imeadiate file not found .

---

### Post by autocrosser on 2009-04-30
Weird--That's all I ever do---miss anything in the copy/paste???

Mine looks like:
```

title        Karmic (development branch 9.10), kernel 2.6.30-1-generic
uuid        fc1446a5-94e9-40f8-9ebb-2442107fc13c
kernel        /boot/vmlinuz-2.6.30-1-generic root=UUID=fc1446a5-94e9-40f8-9ebb-2442107fc13c ro quiet splash mem=6G concurrency=shell
initrd        /boot/initrd.img-2.6.30-1-generic
quiet
```

Don't mind the extras on the kernel line :)

---

### Post by ronacc on 2009-04-30
I don't think so , I redid that too .

```
title		Ubuntu koala (development branch), kernel 2.6.30-1-generic
root            (hd4,0)
# uuid		5474216d-42f6-4f3e-aada-560ddfcd5279
kernel		/boot/vmlinuz-2.6.30-1-generic root=UUID=5474216d-42f6-4f3e-aada-560ddfcd5279 ro splash 
initrd		/boot/initrd.img-2.6.30-1-generic
quiet


title		Ubuntu koala (development branch), kernel 2.6.28-11-generic
root            (hd4,0)
# uuid		5474216d-42f6-4f3e-aada-560ddfcd5279
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5474216d-42f6-4f3e-aada-560ddfcd5279 ro splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

```

the second stanza boots to 28-11 just fine , I'm typing on it now .

---

### Post by autocrosser on 2009-04-30
Ya---that's strange--Try checking your UUID & boot with that instead if the root line, but other than that---I can't think of anything---going to bed--I'll think about it.........

---

### Post by ronacc on 2009-04-30
tried that , I had to comment out the uuid and add the root line to get 2.6.28-11 to boot to koala  , like I said my grub is on another drive I had 5 installs on this box also , down to 3 ATM . Its late here I'm on the other coast , I'll pound on this some more tomorrow .

---

### Post by Gina on 2009-04-30
I had a problem with grub when I installed 9.04 on my main (safe) P4 machine.  It seemed to find all OSs but my 8.10 Intrepid that I'd been using before wouldn't boot - coming up with File Not Found from grub.  I couldn't see any reason so I edited my new boot menu.lst to use "configfile" to point to the 8.10 menu.lst and all was well.  

Changing to configfile means menu.lst references to kernels in other (older) systems update correctly.  But I expect most people here know that :lolflag:

---

### Post by plun on 2009-04-30
RC4 is also out now.....

The Tux is back....:)

> Lots of random small changes. And one big revert - say "Goodbye" to Tuz, 
and "Hello again" to Tux.

For people who prefer the tazmanian devil, you can revert the revert with 
"git revert 3d4f16348b77efbf81b7fa186a18a0eb815b6b84" and you'll get your 
Tuz back.

Other than that? Pretty random. ARM, m68k, Microblaze, Powerpc updates. 
ACPi and i915. DVB and network drivers. PCI and USB. btrfs and ecryptfs. 
Networking and sound. All over the map, in other words. 

			Linus

[http://lkml.org/lkml/2009/4/30/10](http://lkml.org/lkml/2009/4/30/10)



---

### Post by MacUntu on 2009-04-30
Both (-rc4 and -1) working fine here.

---

### Post by plun on 2009-04-30
> **MacUntu said:**
> Both (-rc4 and -1) working fine here.

Yep and RC4 solved my trouble with freezing gnome-panel.

CPU frequency selector is back.....  it was 5 of them...

---

### Post by DougieFresh4U on 2009-04-30
> **plun said:**
> RC4 is also out now.....

The Tux is back....:)

I have been using the .30rc3 from when Jaunty and there was a thread in Jaunty with link to 'ppa' with .debs. Is that not the correct one I should be using and is there not .debs any more to upgrade to rc4?

---

### Post by rudenko_ruslan on 2009-04-30
> **DougieFresh4U said:**
> I have been using the .30rc3 from when Jaunty and there was a thread in Jaunty with link to 'ppa' with .debs. Is that not the correct one I should be using and is there not .debs any more to upgrade to rc4?
PPA? You mean this - [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) ?

---

### Post by autocrosser on 2009-04-30
> **DougieFresh4U said:**
> I have been using the .30rc3 from when Jaunty and there was a thread in Jaunty with link to 'ppa' with .debs. Is that not the correct one I should be using and is there not .debs any more to upgrade to rc4?

You can get the new kernel thru the normal channels with Synaptic--no need to use the kernel mainline anymore.

---

### Post by DougieFresh4U on 2009-04-30
> **rudenko_ruslan said:**
> PPA? You mean this - [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) ?
That only does as far as .30rc3.
> **autocrosser said:**
> You can get the new kernel thru the normal channels with Synaptic--no need to use the kernel mainline anymore.

I am using 'main' and never got wind of .30 update/upgrade in 'Synaptic' or 'terminal'
Thanks

---

### Post by Gina on 2009-04-30
I installed the new kernel packages with Synaptic and restarted - the new kernel was there in the menu - I thought I might need to add the new bits by hand but Synaptic did it all :)

Only problem I seem to have is that the nvidia 180 driver won't work with the new kernel.  I guess it needs the kernel module recompiling.  I'll have to look up how to do that again - I've done it before.  

Only low graphics mode is available with the new kernel so I'm using the old one for now.

---

### Post by Nullack on 2009-04-30
only 180.18.4 supports it

---

### Post by autocrosser on 2009-04-30
Gina---look at the Xorg drivers thread---there is a line to a PPA that gets you a .deb for the new beta driver....It works great!!!!

---

### Post by Gina on 2009-04-30
Thanks very much :)

---

### Post by Slug71 on 2009-04-30
> **andrewabc said:**
> Jaunty shipped with 2.6.28-11
2.6.29 was released around March 23.
2.6.30 RC3 is out, and I think they normally get a dozen or so RC before release. So 2.6.30 should be released in a month or two? So the question is whether ubuntu will use 2.6.30 or 2.6.31 in 9.10 (time will tell)?


I would put my money on 2.6.31.

---

### Post by autocrosser on 2009-04-30
I agree--2.6.31 has a timeline that looks very good for Karmic release--Reminds me of Intrepid release--so I think it will squeak in right in time....

---

### Post by ronacc on 2009-05-01
a rather bizare update to my 2.6.30 won't boot saga , I have a box I am building up that had jaunty on it as an only install so I edited my sources list and updated to karmic and installed 2.6.30-1 to it (I let it write its own boot stanza ) and that box booted to 2.6.30 just fine , so I copied the menu.lst to a usb drive and added the boot stanza from it to the menu.lst on my test box and copied the uuid from the stanza that wouldn't boot to the new stanza and that box will now boot to 2.6.30 ?????

---

### Post by autocrosser on 2009-05-01
What was the difference??? That is real strange......

Anyway--glad to see you are with the rest of us now........... :) :)

---

### Post by ronacc on 2009-05-01
I can't see any difference thats the bizzare part , but I darn sure will find out , I preserved the original and am going to disect it tomorrow , I will cut and past one line of the stanza at a time to find the offending line and then go over it one character at a time if need be . again its late and I want to do that when my eyes arent so bleary .

---

### Post by JohnJackson on 2009-05-01
> **ronacc said:**
> I can't see any difference thats the bizzare part , but I darn sure will find out , I preserved the original and am going to disect it tomorrow , I will cut and past one line of the stanza at a time to find the offending line and then go over it one character at a time if need be . again its late and I want to do that when my eyes arent so bleary .

Might want to try a diff tool for this? Meld/Kompare for example.

---

### Post by plun on 2009-05-01
> **ronacc said:**
> a rather bizare update to my 2.6.30 won't boot saga , I have a box I am building up that had jaunty on it as an only install so I edited my sources list and updated to karmic and installed 2.6.30-1 to it (I let it write its own boot stanza ) and that box booted to 2.6.30 just fine , so I copied the menu.lst to a usb drive and added the boot stanza from it to the menu.lst on my test box and copied the uuid from the stanza that wouldn't boot to the new stanza and that box will now boot to 2.6.30 ?????


I think we have a bug within the function "keep the local version" or use Maintainer version of menu.lst.

If I keep my version something gets wrong and sometimes its not updated, when I choose Maintainers version it always works but I must manually add some changes
within my menu.lst.

But... howto get a bug-report out of this...:)

---

### Post by ronacc on 2009-05-01
@ plun thats not the case with me, see my earler posts this thread , my grub and menu.lst are on another drive and install , I always manualy edit , I cloned a working boot stanza changed the kernel number and it nolonger works .

---

### Post by plun on 2009-05-01
> **ronacc said:**
> @ plun thats not the case with me, see my earler posts this thread , my grub and menu.lst are on another drive and install , I always manualy edit , I cloned a working boot stanza changed the kernel number and it nolonger works .

Ok...but when you manually install a kernel debconf always starts and prompts you about which version of menu.lst should be used.

Then you must have several menu.lst ie boot/grub.

---

### Post by ronacc on 2009-05-01
no , if I already have a grub on another install I tell ubiquity " don't install a boot loader" to keep things from getting too messy , and then just add what I need .

---

### Post by plun on 2009-05-01
> **ronacc said:**
> no , if I already have a grub on another install I tell ubiquity " don't install a boot loader" to keep things from getting too messy , and then just add what I need .

But again....:)

In this case if you uses Synaptic for installing 2.6.30-1 Debconf will start and ask about Grub and menu.lst.  

But... I am unsure what happens if you have told Ubiquity that no bootloader is in use....

:confused::confused::confused:

---

### Post by plun on 2009-05-01
New Ubuntu kernel based on RC4

> linux (2.6.30-2.3) karmic; urgency=low

  [ Tim Gardner ]

  * [Config] Enabled CC_STACKPROTECTOR=y for all x86en
    - LP: #369152
  * SAUCE: Default to i915_modeset=0 if CONFIG_DRM_I915_KMS=y
  * [Config] CONFIG_DRM_I915_KMS=y
  * [Config] Set CONFIG_SECURITY_DEFAULT_MMAP_MIN_ADDR to appropriate ARCH
    minimums

  [ Upstream Kernel Changes ]

  * rebased to 2.6.30-rc4


[https://lists.ubuntu.com/archives/karmic-changes/2009-May/000294.html](https://lists.ubuntu.com/archives/karmic-changes/2009-May/000294.html)




---

### Post by taavikko on 2009-05-01
New 2.6.30-2 boots nice and seems to be intact...
No detailed analysis for you at this point :D

Hardware works... with minor glitches 
```
[    1.284067] ata2: softreset failed (device not ready)
[    1.284069] ata1: softreset failed (device not ready)
[    1.284076] ata1: failed due to HW bug, retry pmp=0
[    1.284308] ata2: failed due to HW bug, retry pmp=0
[    1.326283] usb 1-3: configuration #1 chosen from 1 choice
[    1.448102] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.448136] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.448819] ata1.00: ATA-8: Hitachi HTS543232L9A300, FB4OC40F, max UDMA/100
[    1.448826] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.449854] ata1.00: configured for UDMA/100
[    1.450094] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54323 FB4O PQ: 0 ANSI: 5
[    1.450525] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    1.450564] sd 0:0:0:0: [sda] Write Protect is off
[    1.450572] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.450633] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.450887]  sda:<5>sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.463692] ata2.00: ATAPI: Optiarc DVD RW AD-7581S, 4H03, max UDMA/100
[    1.473231]  sda1 sda2 <<6>ata2.00: configured for UDMA/100
[    1.482657] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7581S  4H03 PQ: 0 ANSI: 5
[    1.484141]  sda5 >
[    1.484995] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.495553] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.495560] Uniform CD-ROM driver Revision: 3.20
[    1.495792] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.496049] sr 1:0:0:0: Attached scsi generic sg1 type 5

```

---

### Post by plun on 2009-05-01
> taavikko;7192377]New 2.6.30-2 boots nice and seems to be intact...
No detailed analysis for you at this point :D

Well.. I havent tested it....:)

I am running my **1000Hz** plain Vanilla RC4..... including Plymouth..:)

---

### Post by psyke83 on 2009-05-02
> **jerrylamos said:**
> The local mirror here had 2.6.30-1 ready for synaptic apply.

On intel integrated graphics i845 "AccelMethod" "uxa" produces garbled display on glxgears, and YouTube videos are jerky.

Slower without "uxa".

It worked, tho.  We'll see about Alpha.  intel graphics broke on Intrepid requiring "NoAccel" until after ship, also broke on jaunty until just before beta.  Hardy's faster however jaunty has a lot more "polish" from my view.

Thanks for putting the karmic linux image out.

Jerry

You need to set "Tiling" to false in the Device section of your xorg.conf to get 3D working correctly. Youtube et al is slow because the MTRR ranges aren't set to write-combining properly.

See my Intel performance guide for more information. Don't follow the steps, though, it's only for Jaunty.

---

### Post by Amaranth on 2009-05-03
With 2.6.30-2-generic modesetting works but even after patching the broadcom wl driver to build with 2.6.30 it fails to connect to any wireless networks. :(

---

### Post by artir on 2009-05-03
Plymouth+2.6.30 works on Virtualbox, yeah!(But it eats 100% of the CPU when it boots...)

---

### Post by Tom_T on 2009-05-04
I've installed 2.6.30-2.3 on my Acer One D150 (10.1" Screen) and it seems to be working well.

BUT !!  I did notice AppArmor FAILS during boot up
Should I be concerned about this ??

Thanks :)

---

### Post by int on 2009-05-04
nvidia-graphics-drivers-180 (180.44-0ubuntu2) karmic; urgency=low

 * debian.binary/patches/nvidia-x86_64-180.44-2.6.30-rc2.patch:
   - Add patch from
     [http://pavlinux.ru/nv/nvidia-x86_64-180.44-2.6.30-rc2.patch](http://pavlinux.ru/nv/nvidia-x86_64-180.44-2.6.30-rc2.patch)
     to enable compiling against 2.6.30.
 * debian/dkms.conf.in:
   - Apply RT patch on 2.6.30
   - Apply 2.6.30 compilation patch on 2.6.30.
 * debian/control:
   - Update description for libvdpau (LP: #369049)

Date: Mon, 04 May 2009 12:00:43 -0500
Changed-By: Mario Limonciello <mario_limonciello@xxxxxxx>
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@xxxxx>
Signed-By: Mario Limonciello <superm1@xxxxxxxx>
[https://launchpad.net/ubuntu/karmic/+source/nvidia-graphics-drivers-180/180.44-0ubuntu2](https://launchpad.net/ubuntu/karmic/+source/nvidia-graphics-drivers-180/180.44-0ubuntu2)

---

### Post by Tom_T on 2009-05-04
Any idea on AppArmor failing ??

Also does usplash work with this kernel ??

Thanks

---

### Post by amano on 2009-05-04
> **autocrosser said:**
> I agree--2.6.31 has a timeline that looks very good for Karmic release--Reminds me of Intrepid release--so I think it will squeak in right in time....

Intrepid was an exception. They wanted some fixes but it was too hard to backport them, thus they decided to risk upgrading to the new kernel late in the circle. But there were clear drawbacks: The kernel team was too busy with the late upgrade that it couldn't deliver a low latency kernel for Ubuntu studio.

---

### Post by phrostbyte on 2009-05-05
If you find bugs it might be good to put them on the kernels official bug tracker, since 2.6.30 is still in development.

---

### Post by vishalrao on 2009-05-05
I wonder if Karmic will have low-latency kernel enabled like Fedora for some pulseaudio improvements... can hardly wait for UDS to read about Karmic plans...!

---

### Post by Nullack on 2009-05-05
> **vishalrao said:**
> I wonder if Karmic will have low-latency kernel enabled like Fedora for some pulseaudio improvements... can hardly wait for UDS to read about Karmic plans...!

Mate you could ask the kernel team on the devel discuss mailing list

---

### Post by vishalrao on 2009-05-05
OK, will fire out an email :)

Found a link posted in the "improve sound" thread too: [https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003150.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003150.html)

---

### Post by davideotape on 2009-05-06
Quick question: If I've upgraded to karmic, should I have a new kernel? (ie. not the one from jaunty)

---

### Post by taavikko on 2009-05-06
> **davideotape said:**
> Quick question: If I've upgraded to karmic, should I have a new kernel? (ie. not the one from jaunty)

Not yet. ubuntu-desktop and thus linux-image metapackages hasn't been upgraded yet to point towards the new one.

In the meanwhile you have to manually install the new kernel. it's in the repos.

---

### Post by davideotape on 2009-05-06
> **taavikko said:**
> Not yet. ubuntu-desktop and thus linux-image metapackages hasn't been upgraded yet to point towards the new one.

In the meanwhile you have to manually install the new kernel. it's in the repos.

Good :D Thought I was missing out there for a minute :P Do you know when abouts the new kernels will start coming?

---

### Post by plun on 2009-05-06
Meta package description was uploaded today....

[https://lists.ubuntu.com/archives/karmic-changes/2009-May/000567.html](https://lists.ubuntu.com/archives/karmic-changes/2009-May/000567.html)

and directly a new kernel..

[https://lists.ubuntu.com/archives/karmic-changes/2009-May/000577.html](https://lists.ubuntu.com/archives/karmic-changes/2009-May/000577.html)

---

### Post by whoop on 2009-05-06
> **davideotape said:**
> Good :D Thought I was missing out there for a minute :P Do you know when abouts the new kernels will start coming?

It's here, it's here (without installing it manually).

---

### Post by Nullack on 2009-05-06
Seems to be working fine here

---

### Post by maheshasolkar on 2009-05-07
I lost my usplash after updates. I wonder if it is related to the new kernel.

---

### Post by dirtylobster on 2009-05-07
> **plun said:**
> Meta package description was uploaded today....
[https://lists.ubuntu.com/archives/karmic-changes/2009-May/000577.html](https://lists.ubuntu.com/archives/karmic-changes/2009-May/000577.html)

Okay, so how do I install 2.6.30-3-lpia for my EeePC? It's not in the standard repos..

---

### Post by bl4ck32 on 2009-05-07
> **maheshasolkar said:**
> I lost my usplash after updates. I wonder if it is related to the new kernel.

yep, no splash here as well. Guess we have to wait till they make new ones?

---

### Post by aamukahvi on 2009-05-07
> **bl4ck32 said:**
> yep, no splash here as well. Guess we have to wait till they make new ones?
I think they're going for plymouth this cycle?

---

### Post by taavikko on 2009-05-07
> **aamukahvi said:**
> I think they're going for plymouth this cycle?

They might indeed, but this early in the cycle chances are that by some upgrade procedure, usplash got removed.

so check if it is installed.

---

### Post by rudenko_ruslan on 2009-05-09
> **Date:** Fri, 8 May 2009 17:31:30 -0700 (PDT)
**From:** Linus Torvalds
**Subject:** Linux 2.6.30-rc5

It's been a week (and a couple of days - what can I say?), so here's a new 
-rc.

It's been getting quieter, although by -rc5 I obviously always hope for 
not just "pretty quiet" but "almost deathly quiet", and it never is. 

Driver updates (SCSI being the bulk of it, but there are input layer, 
networking, DRI and MD changes too). Arch updates (mostly ARM "davinci" 
support, but some x86 and even alpha). And various random stuff (fairly 
big cifs update, but some smaller ocfs2 and xfs updates, and a fair amount 
of small one-liners all over).
Oh, and if you look at the non-rename-aware patches, you'll see huge 
changes due to moving the dtc and libfdt sources (open-firmware device 
tree building/using support) from arch/powerpc/boot to scripts/dtc so that 
microblaze could use it too.

But on the whole, not a lot of huge issues. Please test and remind people 
about regressions if you've seen any, or (heaven forbid) look for new ones 
if you haven't.

Shortlog appended. 

		Linus
[http://lkml.org/lkml/2009/5/8/505](http://lkml.org/lkml/2009/5/8/505)

This RC will be available there - [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) - after some time, I guess.

> ruslan@ruslan-desktop:~$ uname -a
Linux ruslan-desktop 2.6.30-4-generic #5-Ubuntu SMP Fri May 8 13:20:48 UTC 2009 i686 GNU/Linux
):P

---

### Post by plun on 2009-05-10
Well I "home-brewed" it and RC5 works just fine....:)

---

### Post by plun on 2009-05-12
RC5 based Ubuntu kernel available.

Not yet within a meta-package, easiest installed with Synaptic and searching for linux-image and linux-headers

> [B]linux (2.6.30-5.6) karmic; urgency=low
[/B]
  [ Tim Gardner ]

  * [Config] Enable Keyspan USB serial device firmware in kernel module
    - LP: #334285

  [ Upstream Kernel Changes ]

  * **rebased to 2.6.30-rc5**

[https://lists.ubuntu.com/archives/karmic-changes/2009-May/001018.html](https://lists.ubuntu.com/archives/karmic-changes/2009-May/001018.html)



---

### Post by davideotape on 2009-05-13
> **taavikko said:**
> They might indeed, but this early in the cycle chances are that by some upgrade procedure, usplash got removed.

so check if it is installed.

Seems like it got re-instated today after 2.6.30-5 was uploaded:KS

---

### Post by Priyantha Bleeker on 2009-05-14
Is there already a working patch to compile Vmware Workstation modules ?
I did found this: [http://communities.vmware.com/thread/208963](http://communities.vmware.com/thread/208963)
But it doesn't work for me :(

---

### Post by Phreaker on 2009-05-15
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

I'm trying this on jaunty right now :)

---

### Post by plun on 2009-05-16
and RC6....

> date  fri, 15 may 2009 21:36:02 -0700(pdt)

from linus torvalds <>

subjectlinux 2.6.30-rc6

**another week, another -rc.**

Things definitely are calming down, with just about 300 commits in the
last week. And most of them are pretty small too, although the powerpc
updates brought some defconfig changes that look largish.

Somewhat unusually, the dirstat shows filesystems with as much changes as
drivers - we had some nilfs2 and reiserfs updates there, along with some
mostly trivial vfs layer cleanups. We had a bkl pushdown in the umount
paths, for example (that will hopefully make it easier to then merge the
bkl removal patches for reiserfs during the next merge window).

On the arch side, apart from the powerpc things, we have soem cris and
mips updates. The bulk of the cris updates was merging the compressed boot
code across chris-v10 and chris-v32, so the diffs there look bigger than
they really were.

On the driver front, there's some sata updates, some i915 graphics
updates, and various other small things sprinkled all over. Some sound
driver updates too, although most of those seem to be the davinci stuff
(from the arm merge last -rc), so most people won't notice or care.

And we've hopefully fixed a number of regressions. Please remind people
(me very much included) of all the ones that you still see - i've been
missing rafael's regular regression summaries ;(

linus

[http://lkml.org/lkml/2009/5/16/3](http://lkml.org/lkml/2009/5/16/3)

---

### Post by Nullack on 2009-05-16
Looking at the kernel teams git I dont see an RC5, I only see a tag from 2 weeks ago indicating RC4??

Anyway the 2.6.30-5 generic kernel got installed today from the main repo and it seems to be running ok so far albeit missing the various RC fixes in upstream since.

---

### Post by mabovo on 2009-05-17
> **Nullack said:**
> Looking at the kernel teams git I dont see an RC5, I only see a tag from 2 weeks ago indicating RC4??

Anyway the 2.6.30-5 generic kernel got installed today from the main repo and it seems to be running ok so far albeit missing the various RC fixes in upstream since.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc5/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc5/)

---

### Post by taavikko on 2009-05-17
```
linux (2.6.30-5.6) karmic; urgency=low

  [ Tim Gardner ]

  * [Config] Enable Keyspan USB serial device firmware in kernel module
    - LP: #334285

  [ Upstream Kernel Changes ]

  * rebased to 2.6.30-rc5

 --  Tim Gardner <tim.gardner@canonical.com>  Mon, 11 May 2009 12:02:16 -0600

```

---

### Post by Nullack on 2009-05-17
> **mabovo said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc5/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc5/)

That isnt the karmic git branch however. I dont run non standard kernels as its a core part of the integrity of my test effort.

---

### Post by Nullack on 2009-05-17
> **taavikko said:**
> ```
linux (2.6.30-5.6) karmic; urgency=low

  [ Tim Gardner ]

  * [Config] Enable Keyspan USB serial device firmware in kernel module
    - LP: #334285

  [ Upstream Kernel Changes ]

  * rebased to 2.6.30-rc5

 --  Tim Gardner <tim.gardner@canonical.com>  Mon, 11 May 2009 12:02:16 -0600

```

Thanks mate. I wish the kernel team would consistently tag their git web - unless Ive missed it, I dont think RC5 is tagged.

---

### Post by Sewje on 2009-05-18
This update fixed a shutdown issue with my Acer 5920g. Hurray!

---

### Post by rudenko_ruslan on 2009-05-22
[https://launchpad.net/ubuntu/karmic/+source/linux/2.6.30-6.7](https://launchpad.net/ubuntu/karmic/+source/linux/2.6.30-6.7)
> linux (2.6.30-6.7) karmic; urgency=low

  [ Andy Whitcroft ]

  * Dropped: UBUNTU: SAUCE: input: Blacklist digitizers from joydev.c (now
    upstream)

  [ Upstream Kernel Changes ]

  * rebased to 2.6.30-rc6

 -- Andy Whitcroft <email address hidden>   Mon, 18 May 2009 18:05:54 +0100

---

### Post by rudenko_ruslan on 2009-05-24
> **Date:** Sat, 23 May 2009 15:07:03 -0700 (PDT)
**From:** Linus Torvalds
**Subject:** Linux 2.6.30-rc7

Ok, so 90% of the patch is the addition of one new driver, at around 9000 
lines for the the Cisco PCI-Express FCoE HBA SCSI driver.

If you ignore that (and you should - unless you happen to have such 
hardware and have been pining for the driver to be merged for a long 
time), the rest is really mostly a collection of small fixes. Several 
regressions fixed, lots of small cleanup.

Nothing huge stands out. The diffstat shows the new driver clearly, and 
some of the cifs fixes aren't totally trivial (and the reiserfs xattr 
changes show up), but most of it really is one-liners.

So go wild. I suspect I'll do an -rc8, but we're definitely getting closer 
to release-time - it would be good to get as much testing as possible, and 
it should generally be pretty safe to try this all out.

Thanks,

		Linus
[http://lkml.org/lkml/2009/5/23/121](http://lkml.org/lkml/2009/5/23/121) + [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc7/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc7/)

---

### Post by zika on 2009-05-24
I'm not using Karmic yet but I have a question that is about 2.6.30:
is there a way I could make 2.6.30.rc7 boot with my ext3 on Jaunty in   data=ordered or data=guarded mode? I do not want to use writeback ...   too risky ... :smile:
as I understood data=guarded is not available in 2.6.28?
I've tried things that worked in 2.6.28... data=ordered in /etc/fstab   e.t.c. ... nothing worked. if I put data =ordered in /etc/fstab I get   read-only boot ... :sad:

(excuse me for double-posting ...)
p.s.
it worked now with ```
tune2fs -o journal_data_ordered/dev/sdax
```  now and I', stummied why it did not work before. I had it that way  earlier and I do not know when it changed and by whom ... .)

---

### Post by rudenko_ruslan on 2009-05-25
[https://launchpad.net/ubuntu/karmic/+source/linux/2.6.30-7.8](https://launchpad.net/ubuntu/karmic/+source/linux/2.6.30-7.8)
> linux 2.6.30-7.8 (source) in ubuntu karmic
Changelog

linux (2.6.30-7.8) karmic; urgency=low

  [ Andy Whitcroft ]

  * Enabled NEW configration options:
      Paravirtualization layer for spinlocks (PARAVIRT_SPINLOCKS) [N/y/?] Y
      Cisco FNIC Driver (FCOE_FNIC) [N/m/y/?] M

  [ Upstream Kernel Changes ]

  * rebased to 2.6.30-rc7

 -- Andy Whitcroft <email address hidden>   Sat, 23 May 2009 23:47:24 +0100
Nice! :)

---

### Post by Nullack on 2009-05-25
They are still not tagging their releases in GIT:

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-karmic.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-karmic.git;a=summary)

Last one tagged was RC4

---

### Post by alphacrucis2 on 2009-05-25
I just ran an update on Karmic. I noticed it downloaded kernel 2.6.30-6 but it failed to update the grub menu and it seems that there is no initrd.img-2.6.30-6-generic file under /boot. What would happen if I booted the 2.6.30-6 kernel with the initrd initrd.img-2.6.30-5-generic?

---

### Post by ranch hand on 2009-05-25
When your grub menu comes up, highlight the first line with the kernal number in it.  Hit "e".  Change the number.  Hit enter.  Highlight the second line and do the same things.  This will probably boot you to the new kernal.

If so just
```

gksudo gedit /boot/grub/menu.lst

```
and edit your file.

---

### Post by zika on 2009-05-26
> **alphacrucis2 said:**
> I just ran an update on Karmic. I noticed it downloaded kernel 2.6.30-6 but it failed to update the grub menu and it seems that there is no initrd.img-2.6.30-6-generic file under /boot. What would happen if I booted the 2.6.30-6 kernel with the initrd initrd.img-2.6.30-5-generic?
Did You see only Linux-image-2.6.30-6-generic? Did it install Linux-headers-2.6.30-6-generic? If it did not, wait until that come through updates and it should clear by itself ...

---

### Post by binbash on 2009-05-26
I can not use a USB mouse with this kernel.Mouse responds in 4 secs if it is inactive.

---

### Post by alphacrucis2 on 2009-05-26
> **zika said:**
> Did You see only Linux-image-2.6.30-6-generic? Did it install Linux-headers-2.6.30-6-generic? If it did not, wait until that come through updates and it should clear by itself ...

I am not with my Karmic test machine at present so I can't check. I do recall seeing the Linux image mentioned in the dist-upgrade output and certainly the corresponding vmlinuz compressed kernel ended up in /boot but I noticed the corresponding initrd was missing. I will run another update tomorrow and see if it resolves.

---

### Post by afv on 2009-06-02
2.6.30-7 appeared today at the repositories here. Upgrading&#8230; :)

> 
linux (2.6.30-7.8) karmic; urgency=low

  [ Andy Whitcroft ]

  * Enabled NEW configration options:
      Paravirtualization layer for spinlocks (PARAVIRT_SPINLOCKS) [N/y/?] Y
      Cisco FNIC Driver (FCOE_FNIC) [N/m/y/?] M

  [ Upstream Kernel Changes ]

  * rebased to 2.6.30-rc7

 -- Andy Whitcroft <email address hidden>   Sat, 23 May 2009 23:47:24 +0100


[https://launchpad.net/ubuntu/karmic/+source/linux/2.6.30-7.8](https://launchpad.net/ubuntu/karmic/+source/linux/2.6.30-7.8)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc7/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc7/CHANGES)

---

### Post by tad1073 on 2009-06-02
It is in the repo's

updated and so far so good.

---

### Post by simon_wrafter on 2009-06-02
> **afv said:**
> 2.6.30-7 appeared today at the repositories here. Upgrading… :)

Been using it for a nearly a week. :P It was built during USD and put in the [upload queue]("https://launchpad.net/ubuntu/karmic/+queue") from where I manually downloaded and installed it. working fine :D

---

### Post by rudenko_ruslan on 2009-06-03
And now it's time for -rc8 :)
> **Date:** Tue, 2 Jun 2009 21:06:20 -0700 (PDT)
**From:** Linus Torvalds
**Subject:** Linux 2.6.30-rc8

This is almost certainly the last -rc, and I debated even doing it. But 
rather than just do 2.6.30, I decided that I'd be better off doing a last 
-rc8 and then a real release probably this weekend.

This has mostly driver and arch updates, with perhaps the intel drm/kms 
and network driver changes standing out, but there's powerpc, blackfin and 
arm updates too. Admittedly, the two biggest parts of the powerpc update 
are a revert and a defconfig update.

A lot of small stuff, fixing a few regressions (and at least one bugzilla 
entry going back to 2.6.24). The small stuff does matter. Please test.

		Linus
[http://lkml.org/lkml/2009/6/3/3](http://lkml.org/lkml/2009/6/3/3)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc8/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc8/) - after some time, I guess ;)

---

### Post by ronacc on 2009-06-03
why bother with .30 if we are going to have .31 ? get .31 in here as soon as possible so we can start finding bugs .

---

### Post by psyke83 on 2009-06-03
> **ronacc said:**
> why bother with .30 if we are going to have .31 ? get .31 in here as soon as possible so we can start finding bugs .

...perhaps because 2.6.31 does not exist in *any* form yet? ;)

---

### Post by ronacc on 2009-06-03
> **psyke83 said:**
> ...perhaps because 2.6.31 does not exist in *any* form yet? ;)

congratulations , you've found the first bug :lolflag:

---

### Post by davideotape on 2009-06-03
> **ronacc said:**
> congratulations , you've found the first bug :lolflag:

\\:d/

---

### Post by rudenko_ruslan on 2009-06-03
> linux 2.6.30-8.9 (source) in ubuntu karmic

Changelog

linux (2.6.30-8.9) karmic; urgency=low

  [ Andy Whitcroft ]

  * Config update removed the following options:
        CONFIG_EDAC_AMD8111=m
        CONFIG_EDAC_AMD8131=m

  [ Upstream Kernel Changes ]

  * rebased to 2.6.30-rc8

 -- Andy Whitcroft <email address hidden>   Wed, 03 Jun 2009 09:21:13 +0100
[https://launchpad.net/ubuntu/karmic/+source/linux/2.6.30-8.9](https://launchpad.net/ubuntu/karmic/+source/linux/2.6.30-8.9)

Well, that was fast :)

---

### Post by diebels on 2009-06-03
> **dirtylobster said:**
> Okay, so how do I install 2.6.30-3-lpia for my EeePC? It's not in the standard repos..

Yeah, strange it's not in the repos.

You can find it here [https://launchpad.net/ubuntu/karmic/lpia/+search?text=linux-image](https://launchpad.net/ubuntu/karmic/lpia/+search?text=linux-image)

---

### Post by IanW on 2009-06-03
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc8/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc8/") Now live.

---

### Post by Amaranth on 2009-06-03
The lpia kernel is for a different "architecture". It won't install on your machine just like a package for i386 won't install on an amd64 machine.

Of course it isn't actually a different architecture it's just a way for them to compile all the packages specifically tuned for Atom processors.

---

### Post by rudenko_ruslan on 2009-06-10
> **Date:** Tue, 9 Jun 2009 20:36:36 -0700 (PDT)
**From:** Linus Torvalds
**Subject:** Linux 2.6.30

As mentioned last week, -rc8 was the last -rc, and there really isn't any 
point in delaying the real release any more.

I'm sure we've missed something, and I know we have some regressions 
pending. At the same time, we do need the coverage of a eral release, and 
on the whole it looks pretty good. We've fixed a few regressions in the 
last few days, and there's always 2.6.30.x.

The appended shortlog from 2.6.29-rc8 is not very interesting, but it's 
about as good as it gets. Not a lot of changes (just 72 non-merges, 
according to git rev-list), and most of those are pretty small and 
trivial. We're talking mostly one-liners, with just a couple of them 
standing out (in fact, just mainly the DPMS handling cleanup in 
drm_crtc_helper.c)

As to the whole set of changes since 2.6.29, the best place to look is 
probably just 

	[http://kernelnewbies.org/Linux_2_6_30](http://kernelnewbies.org/Linux_2_6_30)

as usual. One thing that doesn't seem to be mentioned there is that we're 
hopefully now done with the suspend/resume irq re-architecting, and have 
switched to a new world order. Although I suspect lots of details will 
still change, of course.

And as usual, I'll wait a day or two before really opening the merge 
window. I want people to actually test this one rather than immediately 
sending me "please pull" requests. Deal?

		Linus
[http://lkml.org/lkml/2009/6/9/710](http://lkml.org/lkml/2009/6/9/710)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)

---

