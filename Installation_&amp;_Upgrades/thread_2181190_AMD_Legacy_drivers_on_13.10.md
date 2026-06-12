---
title: "AMD Legacy drivers on 13.10"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by hencelence on 2013-10-16
Hello everybody!

I'm using a DELL Laptop from 2009 which has a AMD Mobility Radeon HD 3450/3470 video card built-in.
Until now, I was able to get the legacy drivers via this PPA: [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx) and get great performance out of it.

This PPA doesn't seem to be ported to 13.10. Why?
Are there any workarounds I could try to get the proprietary drivers?


I would love to use the open-source drivers, but the performance is nowhere near the proprietary ones for my card.

Any help would be much appreciated.

---

### Post by mastablasta on 2013-10-17
> **hencelence said:**
> This PPA doesn't seem to be ported to 13.10. Why?

Perhaps because no one ported it yet. i doubt they will.

> Are there any workarounds I could try to get the proprietary drivers?

a couple:
- port the PPA :p
- use 12.04 (with older kernel not the newer 12.04.2 and higher)-supported until 2017
- install latest kernel with latest opensource drivers or try the xorg edgers PPA

---

### Post by ThatNerd2049 on 2013-10-17
AMD Drivers even the ones in xorg edgers at the time of writing currently don't support the new kernel Ubuntu uses.

Info source: [http://support.amd.com/en-us/kb-articles/Pages/Latest-LINUX-Beta-Driver.aspx](http://support.amd.com/en-us/kb-articles/Pages/Latest-LINUX-Beta-Driver.aspx)

I don't see his card in the supported list though. You may have to stick with the old Ubuntu release and use the legacy drivers with that.

One last idea is downgrading your kernel however I could see that breaking things so try at your own risk.

If you are feeling brave this may help. [http://howtoubuntu.org/how-to-install-linux-kernel-3-10-in-ubuntu#.UmCE1ByEzcs](http://howtoubuntu.org/how-to-install-linux-kernel-3-10-in-ubuntu#.UmCE1ByEzcs)

---

### Post by QIII on 2013-10-17
Not entirely correct.

I'm using Saucy with the proprietary driver.

Some hardware may be problematic.

The OP will not be able to us the proprietary driver with that legacy card without some help -- and I don't recommend going there.

---

### Post by ThatNerd2049 on 2013-10-17
Interesting is the info at source I linked out of date then?

---

### Post by QIII on 2013-10-17
Just not updated.

Saucy was just released.  I doubt AMD/ATI rushed their people out immediately to add "13.10" to the text of the page.

---

### Post by ttd1232004 on 2013-10-17
I have been fighting with ADM on my Dell like you. Using open source driver is still good, but the temperature is high.
I used to download and install AMD official driver and it worked perfectly. I can compare as without amd driver the temperature is around 55 - 65C; with AMD driver installed around 48-60C.
However everytime I wanted to upgrade  my system, or at least kernel the whole system would be broken. I had to purge the AMD official driver installed then everything was back to it was. I think it was problem of configuration of the driver to adopt with new kernel which had been upgraded.
Now I am running Ubuntu 13.10 with open source driver and the temperature is high as it should be. I am waiting for someone can find a way to help me get of out this stuff :D

---

### Post by QIII on 2013-10-17
If you install the proprietary driver from the repo, your package management system will handle reinstalling it with any new kernel.

If you install it manually, you should uninstall it before doing any updates that affect the kernel, then reinstall afterwards.  Your package manager will have no idea it exists, which is why you have had problems after updates all along.

---

### Post by ziktofel on 2013-10-21
Hey guys!

I've sucessfully built fglrx-legacy, which works with 3.11 kernel

It's still in alpha, some issues are known, only 64-bit packages yet

Howto (Ubuntu 13.10 Saucy, 64-bit only!):
[LIST=1]
[*]Add RARING ppa: **ppa:makson96/fglrx** 
[*]sudo apt-get update 
[*]download and install:
[LIST=1]
[*][http://ubuntuone.com/1W4B3qa09OB82avCw9kDvP](http://ubuntuone.com/1W4B3qa09OB82avCw9kDvP) 
[*][http://ubuntuone.com/5fly8Ur8c2PKvUYh2f6V8Z](http://ubuntuone.com/5fly8Ur8c2PKvUYh2f6V8Z) 
[*][http://ubuntuone.com/7HbTMeib9RskH21Qrjv9rl](http://ubuntuone.com/7HbTMeib9RskH21Qrjv9rl) 
[/LIST]
  
[*]sudo apt-get -f install 
[*]reboot 
[/LIST]

Known issues: 
[LIST=1]
[*]*[COLOR=#a9a9a9]Ctrl+Alt+Fn terminals are blank screens, boot screen is blank too[/COLOR]* reported as upgrading issue on my testing machine 
[*]32-bit package isn't patched yet 
[/LIST]
 
Troubleshooting:
[LIST=1]
[*]It might be required to replace linux-kernel-generic package with linux-image-generic and linux-headers-generic packages, especially on fresh installs 
[/LIST]
 
Technical info:
[LIST]
[*]Source (for building packages yourself:
[LIST]
[*][http://ubuntuone.com/76d8r5e8odBVo7yAPv2MJg](http://ubuntuone.com/76d8r5e8odBVo7yAPv2MJg) 
[*][http://ubuntuone.com/2WkkrzfbHksWJqZjJhuwWm](http://ubuntuone.com/2WkkrzfbHksWJqZjJhuwWm) 
[/LIST]
  
[*]Package made from raring **ppa:makson96/fglrx** fglrx-legacy, applying those patches from: [https://aur.archlinux.org/packages/catalyst-total-hd234k/](https://aur.archlinux.org/packages/catalyst-total-hd234k/)
[LIST]
[*]foutrelis_3.10_fix_for_legacy.patch 
[*]gentoo_linux-3.10-proc.diff 
[/LIST]
  
[*]only amd64 is patched now 
[/LIST]

Report issues and try to help me improve it and fix the bugs!

---

### Post by jf-soubliere on 2013-10-22
Thank you ziktofel! 

I confirm your patch works and I will continue to make good use of my humble bundles! :)

I'm not experiencing the issues you're having however. My bootscreen works (although the screen ratio is a bit off) and my TTYs work too. I can't really explain why though? The only thing I did differently is skip step#3 and install your .debs directly. But I'm not convinced that would actually make a difference?

Anyways, thanks a lot for your work! I'm really glad I have a functionnal 3d driver again!

Cheers,
JF



> **ziktofel said:**
> Hey guys!

I've sucessfully built fglrx-legacy, which works with 3.11 kernel

It's still in alpha, some issues are known, only 64-bit packages yet

Howto (Ubuntu 13.10 Saucy, 64-bit only!):
[LIST=1]
[*]Add RARING ppa: **ppa:makson96/fglrx** 
[*]sudo apt-get update 
[*]sudo apt-get install fglrx-legacy. The fglrx-legacy will fail to build against kernel 
[*]download and install:
[LIST=1]
[*][http://ubuntuone.com/1W4B3qa09OB82avCw9kDvP](http://ubuntuone.com/1W4B3qa09OB82avCw9kDvP) 
[*][http://ubuntuone.com/5fly8Ur8c2PKvUYh2f6V8Z](http://ubuntuone.com/5fly8Ur8c2PKvUYh2f6V8Z) 
[*][http://ubuntuone.com/7HbTMeib9RskH21Qrjv9rl](http://ubuntuone.com/7HbTMeib9RskH21Qrjv9rl) 
[/LIST]
  
[*]reboot 
[/LIST]

Known issues: 
[LIST=1]
[*]Ctrl+Alt+Fn terminals are blank screens, boot screen is blank too 
[*]32-bit package isn't patched yet 
[/LIST]

Technical info:
[LIST]
[*]Source (for building packages yourself:
[LIST]
[*][http://ubuntuone.com/76d8r5e8odBVo7yAPv2MJg](http://ubuntuone.com/76d8r5e8odBVo7yAPv2MJg) 
[*][http://ubuntuone.com/2WkkrzfbHksWJqZjJhuwWm](http://ubuntuone.com/2WkkrzfbHksWJqZjJhuwWm) 
[/LIST]
  
[*]Package made from raring **ppa:makson96/fglrx** fglrx-legacy, applying those patches from: [https://aur.archlinux.org/packages/catalyst-total-hd234k/](https://aur.archlinux.org/packages/catalyst-total-hd234k/)
[LIST]
[*]foutrelis_3.10_fix_for_legacy.patch 
[*]gentoo_linux-3.10-proc.diff 
[/LIST]
  
[*]only amd64 is patched now 
[/LIST]

Report issues and try to help me improve it and fix the bugs!

---

### Post by ziktofel on 2013-10-22
it might be an issue of the upgrading the testing machine, thx for test result!

probably after some more test results I'll make a ppa bundle with this to be easier to install

Guide updated!

---

### Post by kijotex on 2013-10-24
**ziktofel** : I can't be more thankfull than I am now. You just make my day a lot better.

Thank you so much for this workarround. Just installed the debs following the order you wrote and reboot my 13.10 Desktop. ¡¡¡ Now it works Again !!! flowlessly, tty's works like a charm too, boot screen just like it used to be. no changes excepts that graphics have beed speed up like the have to.

If it's usefull for you, I'm running Ubuntu 13.10 x64 on a AMD Athlon X6, 8GB RAM DDR800, Asus M3N-HT board, and powered by an ATI RADEON HD 4950 1GB DDR3. feel free to ask any dump/log if you want to (and can explain me how to run it;)

Best regards.

---

### Post by cordam1996 on 2013-10-25
Ziktofel I have a Ati Radeon mobility hd 4200 series card and am running ubuntu 13.10. I followed all your step and install the package via terminal running the command sudo dpkg -i fglrx*.deb and when I rebooted the computer the boot screen was missing with you stated but the ttys do work. The system boots to the login screen fine despite that the boot screen is missing however when I attempt to login in to my user account it goes to a blank black screen and then flashes back to the login in screen I attempted this several times with no change I had to remove the packages by using the tty and then reboot. You help would be much appreciated. 

Thank You

---

### Post by ziktofel on 2013-10-25
try:
sudo apt-get -f install
after installing the debs

---

### Post by LuvLinuxOS on 2013-10-26
cordam1996, I had this same problem so I copied /etc/X11 from a 13.10 live cd to my hdd to get a working GUI. Got my desktop back and I have just been researching the problem only to find the same solutions.   I have an integrated Radeon 3100.  Therefore, I will use the open source drivers until a good fglrx-legacy is available for 13.10.  I was enjoying the extra settings that come with ATI Catalyst Control Center but I would much rather have a function machine.  I am using Lubuntu 13.10 on my production desktop and the increased system performance is just too much to downgrade to 13.04 just for display drivers.  Hope this helps.

[> ~LuvLinuxOS~]("http://luvlinuxos.blogspot.com")

---

### Post by cordam1996 on 2013-10-26
Thank you for the reply LuvLinuxOS. So basically what your saying is that I have to use the open-source drivers. I was trying to get the proprietary drivers because the performance of playing games in Linux is very sluggish when using the open-source drivers

---

### Post by ico-_- on 2013-10-26
Nice ziktofel! Would you make one for the 32bit aswell? :)

---

### Post by cordam1996 on 2013-10-26
I still cannot seem to get this to work even with the suggestion by LuvLinuxOS. Please help.

---

### Post by LuvLinuxOS on 2013-10-26
Cordam1996 did you mount your hdd, then from a LXTerminal sudo su, then delete the folder /etc/X11 on you hdd, then copy the folder from the live cd to your hdd!!! It worked beautifully for me and I had some crucial data at stake in my encrypted home folder.  Can you boot to a prompt? If so, you might have to apt-get purge fglrx* then do the copy from live cd.  My bad as I was trying to remember what I did from the top of my head.... Again I hope this helps!!!

[> ~LuvLinuxOS~]("http://luvlinuxos.blogspot.com")

---

### Post by cordam1996 on 2013-10-26
I didn't delete it. It asked to merge I'll try again with deleting it. However is this so I can get into my desktop while continuing to use the properitary drivers or to get back to the open source one.

---

### Post by LuvLinuxOS on 2013-10-27
That will get you back to the open source driver.  I will give it some time until fglrx-legacy is fully ported to Saucy or aleast a proven work around is available.  Yeah merging will not replace all of X settings!!!  Best of luck... I enjoyed the legacy drivers too, but the performance in Lubuntu 13.10 is just to good to downgrade to 13.04!!! Be Blessed!!!

[> ~LuvLinuxOS~]("http://luvlinuxos.blogspot.com")

---

### Post by cordam1996 on 2013-10-27
Thank you very much LuvLinuxOS it worked! Hopefully they port fglrx-legacy to saucy soon.

---

### Post by Mark Phelps on 2013-10-27
> Thank you very much LuvLinuxOS it worked! Hopefully they port fglrx-legacy to saucy soon. 

AMD made it clear a while back they would NOT be updating their Linux AMD HD2x/3x/4x drivers for the X-server used in Ubuntu 13.10 and beyond.

According to the first post: > If there will be no more driver updates made by AMD, than this repository will not support Ubuntu 13.10 and beyond.This indicates that Ubuntu 13.10 and beyond are NOT going to be supported by these drivers.

---

### Post by LuvLinuxOS on 2013-10-27
> Thank you very much LuvLinuxOS it worked! Hopefully they port fglrx-legacy to saucy soon.

you are welcome cordam1996!!! :cool:

> AMD made it clear a while back they would NOT be updating their Linux  AMD HD2x/3x/4x drivers for the X-server used in Ubuntu 13.10 and beyond.

According to the first post:
> This indicates that Ubuntu 13.10 and beyond are NOT going to be supported by these drivers.

Mark, if AMD will not update then the community must.  This seems like a true Open Source Community Project!!! I am not experience in driver development but I would love to help get these drivers ported to Ubuntu 13.10 and beyond.  Will you help???:-({|=\\:D/:-k#-o

[> ~LuvLinuxOS~]("http://luvlinuxos.blogspot.com")

---

### Post by jordie9 on 2013-10-30
Thanx very much... worked perfectly.

J

---

### Post by Mark Phelps on 2013-10-31
> Mark, if AMD will not update then the community must. This seems like a true Open Source Community Project!!!

We don't disagree on this ... 

The problem is that AMD does not see it this way. When they were ATI, they were very active both in cranking out new drivers and in supporting "older" chipsets for a long time.  When they got bought out by AMD, this changed to the degree that they have dropped driver support even when the related chipsets were still being sold!

---

### Post by andlessa on 2013-11-02
I followed  Ziktofel's instructions and everything seems to have been installed without issues. However when I reboot I just get a black screen. Any ideas how to debug it?
Thanks.

---

### Post by mamulyan1980 on 2013-11-20
[http://linuxg.net/how-to-install-linux-kernel-3-2-47-lts-on-ubuntu-13-10-13-04-12-10-12-04-and-linux-mint-15-14-13-via-installation-script/](http://linuxg.net/how-to-install-linux-kernel-3-2-47-lts-on-ubuntu-13-10-13-04-12-10-12-04-and-linux-mint-15-14-13-via-installation-script/)

---

### Post by bigbrownepaul2 on 2013-11-21
I have fixed this problem using the radeon open source driver as follows:

1. Download firmware files for your card from [ftp://plamo.linet.gr.jp/pub/Plamo-5.x/x86_64/boot/installer/lib/firmware/radeon/](ftp://plamo.linet.gr.jp/pub/Plamo-5.x/x86_64/boot/installer/lib/firmware/radeon/)
2. sudo mkdir /lib/firmware/radeon/
3. sudo mv "firmwarefiles" /lib/firmware/radeon/"firmwarefiles"
4. reboot
5. dmesg | egrep 'drm|radeon' to confirm loading messages are ok eg [   49.904946] [drm] Loading RS780 Microcode[   50.019222] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).

Hopefuly this will work for you to!:)

---

### Post by bigbrownepaul2 on 2013-11-21
> **andlessa said:**
> I followed  Ziktofel's instructions and everything seems to have been installed without issues. However when I reboot I just get a black screen. Any ideas how to debug it?
Thanks.

Boot to a tty by using your "advanced" options then choose recovery option.

Then run sudo apt-get remove --purge fglrx* this will remove the ATI drivers that are causing the problem, install the YPPA Manager from software centre and remove the PPA's added above and then sudo apt-get update to ensure you dont cause the problem over again.

Then follow my instructions above to add the firmware into the right place to get 3d acceleration back for the card - assuming its the same problem as me :-)

---

### Post by cemelmaci on 2013-11-27
Thanx very much...its worked

---

### Post by bigbrownepaul2 on 2013-11-28
> **cemelmaci said:**
> Thanx very much...its worked

Most welcome, I have been saved many times by these forums its great to help someone else!

:popcorn:

---

### Post by x6itru on 2013-12-03
hello there! any way to get it working? packages from ziktofel does not work (just black screen ;p) :/ Grettings from x6itru.

---

### Post by squweez on 2013-12-03
Hi there,

after trying Ziktofel's method twice i got stuck in the login loop again. When this happens i can just do unistall fglxr* and i can login - everything works fine then.

After installation my .xsession-errors just say 
> XIO: Fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
After 20 Request (20 known processed) with 0 events remaining 


My actual problem is, that my second Monitor (26'') is detected as 32'', therefore i can't rely use it. 

I also like to have the Drivers installed to play some game - open source drivers wont be enough :/

Btw. I'm using a Radeon HD 4850 at Ubuntu 13.10

Thanks for any help

---

### Post by ziktofel on 2013-12-03
I have only an old HP Probook 4510s with AMD Radeon HD 4300M, 4GB RAM and Intel Core2 Duo CPU to test that thingy

I've reinstalled the system on that recently using a Linux Mint 16 Cinnamon 64-bit iso, the only thing I had to do was to replace linux-kernel-generic package with linux-image-generic and linux-headers-generic. Did all the thnigs in the manual I've released and it works without any problem.

Maybe this will help you

---

### Post by squweez on 2013-12-04
Apperently all of these packages are installed and up to date... shall I remove the linux-generic package?

Just to make sure.. by the manual you have posted, you mean your post in this thread, right?

Btw: Before installing the driver, my monitors are fine at bootscreen (resolution both 16:9.. but thats fine (main monitor is a 4:3 19''), even the second monitor is detected as 26'' @bootscreen, but afterwards its a 32''..). After installing the driver my monitors have different resolution in bootscreen (both they ones they need), but i can't get past the login screen due to the error i mentioned before.

thanks for any help!

//e: it worked.. at least I installed it and I'm still able to login.. i'll configure everything, and give a short answere if everything worked fine when im finished
//e2: it worked fine, I set up my desktop and now they monitors are configured correctly... the only problem i still get low fps (15..) when gaming while i get 30 on win7 with the same machine..., but well at least i can finally work fine! THANX

---

### Post by ziktofel on 2013-12-04
So it helped.

For the performance maybe a build for Linux kernel 3.12 might help (as Phoronix says with Linux 3.12 and AMD GPUs), when I get a free time, I might look into the 3.12 compatibility

EDIT: after a quick survey this patch [https://abf.rosalinux.ru/openmandriva/fglrx/blob/master/fglrx-kernel-3.12.patch](https://abf.rosalinux.ru/openmandriva/fglrx/blob/master/fglrx-kernel-3.12.patch) should to the 3.12 thingy, but it's untested so far

---

### Post by x6itru on 2013-12-04
hello again, i tried to install it once again, i removed linux-generic package, then did all the steps from manual, ( after that i have 3.11 kernel ) but it doesnt work anyway (login loop), i have hd4870 1gb. I will be grateful for help, i really need it working, because i want to port my 3d engine from windows.

---

### Post by ziktofel on 2013-12-04
have you installed the linux-image-generic package?

---

### Post by x6itru on 2013-12-04
yes, when I installed linux-image-generic display driver changed from VESA to Gallium 0.4, but im still in login loop after installing your packages

---

### Post by squweez on 2013-12-05
Well everything works fine for me, except that i have to start the amdcccle as root  (and just hit the ok button) after every boot in order to have my screens setup in the right way (dual screen instead of mirror).

Is there a way to make these settings permanent?

---

### Post by jefft255 on 2014-01-02
Your repository doesn't seem to work anymore... Here's what I get when i run sudo apt-get update:

   ```
W: Failed to fetch http://ppa.launchpad.net/makson96/fglrx/ubuntu/dists/saucy/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/makson96/fglrx/ubuntu/dists/saucy/main/binary-i386/Packages  404  Not Found
```

---

### Post by wrightbyname on 2014-01-02
> **jefft255 said:**
> Your repository doesn't seem to work anymore... Here's what I get when i run sudo apt-get update:

   ```
W: Failed to fetch http://ppa.launchpad.net/makson96/fglrx/ubuntu/dists/saucy/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/makson96/fglrx/ubuntu/dists/saucy/main/binary-i386/Packages  404  Not Found
```

I just encountered similar 404s. Two things:

1) There is no Saucy option - you must amend the software source to Raring instead as per ziktofel's instruction earlier in the thread.

2) However, I still get a 404 even when using raring, because apt looks for files under URIs like [http://ppa.launchpad.net/makson96/fglrx/dists//ubuntu/raring/main/binary-amd64/Packages](http://ppa.launchpad.net/makson96/fglrx/dists//ubuntu/raring/main/binary-amd64/Packages) instead of the correct [http://ppa.launchpad.net/makson96/fglrx/ubuntu/dists/raring/main/binary-amd64/Packages](http://ppa.launchpad.net/makson96/fglrx/ubuntu/dists/raring/main/binary-amd64/Packages) (i.e. "dists" and "ubuntu" are swapped around). Does anyone know how to get it to use a correct URI or is this entirely in the hands of makson96 as the ppa owner?

---

### Post by M4k44n on 2014-01-18
> **wrightbyname said:**
> I just encountered similar 404s. Two things:

1) There is no Saucy option - you must amend the software source to Raring instead as per ziktofel's instruction earlier in the thread.

2) However, I still get a 404 even when using raring, because apt looks for files under URIs like [http://ppa.launchpad.net/makson96/fglrx/dists//ubuntu/raring/main/binary-amd64/Packages](http://ppa.launchpad.net/makson96/fglrx/dists//ubuntu/raring/main/binary-amd64/Packages) instead of the correct [http://ppa.launchpad.net/makson96/fglrx/ubuntu/dists/raring/main/binary-amd64/Packages](http://ppa.launchpad.net/makson96/fglrx/ubuntu/dists/raring/main/binary-amd64/Packages) (i.e. "dists" and "ubuntu" are swapped around). Does anyone know how to get it to use a correct URI or is this entirely in the hands of makson96 as the ppa owner?

Hi, here is what i try, i change the URI to [http://ppa.launchpad.net/makson96/fglrx/ubuntu/](http://ppa.launchpad.net/makson96/fglrx/ubuntu/) , the distribution name to raring (i don't know if necesary, i'm pretty new to linux). After that i can install fglrx-legacy.

Good luck, and sorry for my english. Greetings from Argentina :D

---

### Post by wrightbyname on 2014-01-20
Thanks, I installed the driver in the end by navigating to and downloading it manually. However, I have since bought a more modern (Nvidia) card for a simple life!

---

### Post by roveri on 2014-01-23
Thank you so much @[COLOR=#000000]ziktofel ! Finally I could update my kernel to 3.11.
Did anybody tried it with kernel 3.13 ?
Edit: 
I wanted to have fun and tried...does not (of course) work with kernel 3.13.
but still great with 3.11.

[/COLOR]

---

### Post by Niccola on 2014-01-25
I had no success to install fglrx legacy on Radeon HD 2400 (RV610). Any suggestion?

- On kubuntu 13.10, after login it starts loading Kwin but gets back to login screen.

- Have tried also on Unity, but after login it stucks on a black screen

COmments? Help?

---

### Post by piercegerhart on 2014-01-29
I followed ziktofel's instructions, but I only get a blinking cursor after booting. If I try to boot in recovery mode, I get this:
```
vesafb: module verification failed: signature and/or required key missing - tainting kernel
```
I tried to boot older kernels but it hangs after printing 
```
[drm] Initialized radeon 2.34.0 20080528 for 0000:01:00.0 on minor 0
```
I have a Radeon Mobility HD 4xx0. Any suggestions? The open source drivers were causing some pretty serious overheating, but at this point I just want to revert back to those.

edit: Managed to get to a tty and purge out fglrx. Booted fine once, now is just booting to a blank (backlight off) screen for every kernel. Recovery mode still hangs at 
```
[drm] Initialized radeon 2.34.0 20080528 for 0000:01:00.0 on minor 0
```
This is a real bummer. I may have to reinstall.

---

### Post by Random_Pinenut_Joy on 2014-02-01
will this work for x86 systems or just 64bit

---

### Post by stevini81 on 2014-02-02
Hi all,
I try the first solution of ziktofel but it doesn't work on my Dell Studio XPS 1645. The graphic card is an Ati Mobility Radeon HD 4670.
Then I try the solution of bigbrownepaul2 and it works. The problem is that the temperature of the laptop. With this solution I don't see the difference between now and the first install without drivers. But I am not an expert and I am sure I missed somthing to do. Can someone help me please? Don't leave me alone with windows please...

---

### Post by morganl2010 on 2014-02-06
I can't make any of the following install
[http://ubuntuone.com/1W4B3qa09OB82avCw9kDvP](http://ubuntuone.com/1W4B3qa09OB82avCw9kDvP)
[http://ubuntuone.com/5fly8Ur8c2PKvUYh2f6V8Z](http://ubuntuone.com/5fly8Ur8c2PKvUYh2f6V8Z)
[http://ubuntuone.com/7HbTMeib9RskH21Qrjv9rl](http://ubuntuone.com/7HbTMeib9RskH21Qrjv9rl)

I get this error for each

morgan@PhoenixBase:~/Downloads$ sudo dpkg -i fglrx-legacy-dev_8.97.100.7-ziktofel1~saucy5_amd64.deb 
Selecting previously unselected package fglrx-legacy-dev.
(Reading database ... 164281 files and directories currently installed.)
Unpacking fglrx-legacy-dev (from fglrx-legacy-dev_8.97.100.7-ziktofel1~saucy5_amd64.deb) ...
dpkg: dependency problems prevent configuration of fglrx-legacy-dev:
 fglrx-legacy-dev depends on fglrx-legacy; however:
  Package fglrx-legacy is not installed.

dpkg: error processing fglrx-legacy-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-legacy-dev


what is my problem?

---

### Post by mike-freeman-studio on 2014-02-27
> **morganl2010 said:**
> I can't make any of the following install
[http://ubuntuone.com/1W4B3qa09OB82avCw9kDvP](http://ubuntuone.com/1W4B3qa09OB82avCw9kDvP)
[http://ubuntuone.com/5fly8Ur8c2PKvUYh2f6V8Z](http://ubuntuone.com/5fly8Ur8c2PKvUYh2f6V8Z)
[http://ubuntuone.com/7HbTMeib9RskH21Qrjv9rl](http://ubuntuone.com/7HbTMeib9RskH21Qrjv9rl)

I get this error for each

morgan@PhoenixBase:~/Downloads$ sudo dpkg -i fglrx-legacy-dev_8.97.100.7-ziktofel1~saucy5_amd64.deb 
Selecting previously unselected package fglrx-legacy-dev.
(Reading database ... 164281 files and directories currently installed.)
Unpacking fglrx-legacy-dev (from fglrx-legacy-dev_8.97.100.7-ziktofel1~saucy5_amd64.deb) ...
dpkg: dependency problems prevent configuration of fglrx-legacy-dev:
 fglrx-legacy-dev depends on fglrx-legacy; however:
  Package fglrx-legacy is not installed.

dpkg: error processing fglrx-legacy-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-legacy-dev


what is my problem?

Are you trying to install each one individually? That can cause this dependency problem. If so, try using 'sudo dpkg -i fglrx-legacy*.deb'. That will allow the dpkg program to work out the proper installation order to correct for dependency issues.

---

### Post by xlilcasper on 2014-02-28
New to linux and trying to install these. I have added ppa:makson96/fglrx
Downloaded the three files and tried
```

dpkg -i *.deb

```

I get

```

(Reading database ... 181196 files and directories currently installed.)
Preparing to replace ubuntu-amd-catalyst-install 2.4 (using amd-catalyst-NoobsLab_2.4_amd64.deb) ...
Unpacking replacement ubuntu-amd-catalyst-install ...
Preparing to replace fglrx-amdcccle-legacy 2:8.97.100.7-ziktofel1~saucy5 (using fglrx-amdcccle-legacy_8.97.100.7-ziktofel1~saucy5_amd64.deb) ...
Unpacking replacement fglrx-amdcccle-legacy ...
Setting up ubuntu-amd-catalyst-install (2.4) ...
dpkg: dependency problems prevent configuration of fglrx-amdcccle-legacy:
 fglrx-amdcccle-legacy depends on fglrx-legacy; however:
  Package fglrx-legacy is not installed.


dpkg: error processing fglrx-amdcccle-legacy (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 fglrx-amdcccle-legacy



```

trying to install fglrx-legacy tells me it can't be found.

I am unsure where to go from here. running Mint 16 with a Radon hd 2600 pro kernal is 3.11.0-12-generic

---

### Post by ziktofel on 2014-03-01
have you tried to install all the packages with
```

sudo dpkg -i --force-depends filename
```

and after installing all 3 debs execute

```
sudo apt-get -f install
```
?

---

### Post by xlilcasper on 2014-03-01
```

brian@brian-Inspiron-531s ~/fglrx_test $ sudo dpkg -i --force-depends *.deb
[sudo] password for brian:
(Reading database ... 181196 files and directories currently installed.)
Preparing to replace ubuntu-amd-catalyst-install 2.4 (using amd-catalyst-NoobsLab_2.4_amd64.deb) ...
Unpacking replacement ubuntu-amd-catalyst-install ...
Preparing to replace fglrx-amdcccle-legacy 2:8.97.100.7-ziktofel1~saucy5 (using fglrx-amdcccle-legacy_8.97.100.7-ziktofel1~saucy5_amd64.deb) ...
Unpacking replacement fglrx-amdcccle-legacy ...
Setting up ubuntu-amd-catalyst-install (2.4) ...
dpkg: fglrx-amdcccle-legacy: dependency problems, but configuring anyway as you requested:
 fglrx-amdcccle-legacy depends on fglrx-legacy; however:
  Package fglrx-legacy is not installed.


Setting up fglrx-amdcccle-legacy (2:8.97.100.7-ziktofel1~saucy5) ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
brian@brian-Inspiron-531s ~/fglrx_test $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  fglrx-amdcccle-legacy
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
After this operation, 8,192 B disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 181195 files and directories currently installed.)
Removing fglrx-amdcccle-legacy ...
dpkg: warning: while removing fglrx-amdcccle-legacy, directory '/usr/share/ati' not empty so not removed



```
1 removed 2 not upgraded, I am guessing this didn't work.

---

### Post by ziktofel on 2014-03-02
You're trying to install 
amd-catalyst-NoobsLab_2.4_amd64.deb

you must use a command, which installs only *ziktofel*.deb packages

so:

```

sudo dpkg -i --force-depends *ziktofel*.deb

```

---

### Post by xlilcasper on 2014-03-02
Do I need to install amd-catalyst* after?

---

### Post by ziktofel on 2014-03-02
no, the my debs do provide everything related to catalyst, so you just have to install my debs and the dependencies from mentioned PPA

---

### Post by xlilcasper on 2014-03-02
```

 sudo dpkg -i --force-depends *ziktofel*.deb
Selecting previously unselected package fglrx-amdcccle-legacy.
(Reading database ... 181151 files and directories currently installed.)
Unpacking fglrx-amdcccle-legacy (from fglrx-amdcccle-legacy_8.97.100.7-ziktofel1~saucy5_amd64.deb) ...
dpkg: fglrx-amdcccle-legacy: dependency problems, but configuring anyway as you requested:
 fglrx-amdcccle-legacy depends on fglrx-legacy; however:
  Package fglrx-legacy is not installed.


Setting up fglrx-amdcccle-legacy (2:8.97.100.7-ziktofel1~saucy5) ...

```

Is fglrx-legacy one of those dependencies? It doesn't seem to be in the repository, or at least it can't be found when I try to install it. How can I verify that the correct driver is being used? Sorry for so many questions, just trying to learn as I go.

---

### Post by ziktofel on 2014-03-02
The  fglrx-legacy is one of packages, which you have to download (the ubuntuone links)

---

### Post by Niccola on 2014-03-03
I want to share my experience while installing fglrx-legacy on Ubuntu 13.10

on a fresh install, I followed post #9 (thanks to [ziktofel]("http://ubuntuforums.org/member.php?u=1842443")) and I faced into the following:

1 - I've added RARING makson96/fglrx into repository by adding the lines below on /etc/apt/sources.list

deb [http://ppa.launchpad.net/makson96/fglrx/ubuntu](http://ppa.launchpad.net/makson96/fglrx/ubuntu) raring main 
deb-src [http://ppa.launchpad.net/makson96/fglrx/ubuntu](http://ppa.launchpad.net/makson96/fglrx/ubuntu) raring main then I executed:
```
sudo apt-get update
```
then downloaded and installed following files (as recommended by ziktofel):

[http://ubuntuone.com/1W4B3qa09OB82avCw9kDvP](http://ubuntuone.com/1W4B3qa09OB82avCw9kDvP)
[http://ubuntuone.com/5fly8Ur8c2PKvUYh2f6V8Z](http://ubuntuone.com/5fly8Ur8c2PKvUYh2f6V8Z)
[http://ubuntuone.com/7HbTMeib9RskH21Qrjv9rl](http://ubuntuone.com/7HbTMeib9RskH21Qrjv9rl)

installed by executing following command:
```
sudo dpkg -i --force-depends fglrx-*.deb
```

then I've executed the command bellow to fix dependencies:
```
sudo apt-get install -f
```

then rebooted
I've faced with login screen loop (every time I logged in, the screen turned black then went back to login screen). People who set to automatically may will face with black screen.
To fix it I just pressed CTRL + ALT + F1 to get into TTY1 and logged there. After logged into TTY1 I executed following commands:

```

sudo amdconfig --adapted=all --initial -f
sudo apt-get dist-upgrade -y
```
then confirmed installation of non verified packages

waited until finish then rebooted again

and Voilà

---

### Post by TBeholder on 2014-03-04
And now, another version. :D
I did as [#9](http://ubuntuforums.org/showthread.php?t=2181190&p=12823425#post12823425) suggests. Reboot, it works. VTs work normally, even XFWM4 screen compositing works (I use **gdm**, in case you have problems at this point). But soft actually using 3D bugs out: 
[LIST=1]
[*] "cannot find swrast driver"
[*] unable to compile shaders (Vega Strike)
[*] renders models just fine, but for some reason *fails to use textures on them* (Vega Strike, UFO:AI)
[*]  does something weird that appears to be showing backsides of triangles in the player's model all over the camera (most FPS)
[/LIST] Naturally, this somewhat limits its practical use. ;) What fixed the problem was **glx-alternative-fglrx** from Debian (sid). Of course, it turned out to depend on **nvidia-installer-cleanup**, which was trying to overwrite '/usr/lib/nvidia/pre-install', which is also in package ubuntu-drivers-common 1:0.2.83". I had to install it with
"dpkg --force-overwrite --install /var/cache/apt/archives/nvidia-installer-cleanup_20131102+1_amd64.deb" - then install **glx-alternative-fglrx**/unstable - after this, the problems vanished immediately (no reboot). It looks like not everything was setup correctly, because package creators had remnants of earlier installations that helped along.
Thus, the sum total appears to be: 
```

echo "deb http://ppa.launchpad.net/makson96/fglrx/ubuntu raring main" >/etc/apt/sources.list.d/makson96-fglrx-raring.list
echo "deb-src http://ppa.launchpad.net/makson96/fglrx/ubuntu raring main" >>/etc/apt/sources.list.d/makson96-fglrx-raring.list
echo "deb http://ftp.ch.debian.org/debian/ sid contrib" >>/etc/apt/sources.list
echo "deb-src http://ftp.ch.debian.org/debian/ sid contrib" >>/etc/apt/sources.list
apt-get update

apt-get install fglrx-legacy/raring

mkdir ~/tmp/fglrx_saucy
cd  ~/tmp/fglrx_saucy
wget http://ubuntuone.com/1W4B3qa09OB82avCw9kDvP
wget http://ubuntuone.com/5fly8Ur8c2PKvUYh2f6V8Z
wget http://ubuntuone.com/7HbTMeib9RskH21Qrjv9rl
mv 5fly8Ur8c2PKvUYh2f6V8Z fglrx-legacy-dev_8.97.100.7-ziktofel1~saucy5_amd64.deb
mv 1W4B3qa09OB82avCw9kDvP fglrx-amdcccle-legacy_8.97.100.7-ziktofel1~saucy5_amd64.deb
mv 7HbTMeib9RskH21Qrjv9rl fglrx-legacy_8.97.100.7-ziktofel1~saucy5_amd64.deb
dpkg -R --install ~/tmp/fglrx_saucy

apt-get download  nvidia-installer-cleanup
dpkg --force-overwrite --install nvidia-installer-cleanup_20131102+1_amd64.deb
apt-get install glx-alternative-fglrx/unstable

reboot
```

---

### Post by herculesksp on 2014-03-08
@[COLOR=#000000]Niccola: This helped a lot thanks. I was getting the same bootloop issues and this helped get back into my desktop.
Thanks a mil.[/COLOR]

---

### Post by larry18 on 2014-03-27
Anybody experienced it with a 13.10 32 bits ?

---

### Post by Wallacoloo on 2014-04-04
Following [**[COLOR=#000000]Niccola[/COLOR]**]("http://ubuntuforums.org/member.php?u=1160968")'s advice worked *almost* flawlessly. I'm running Xubuntu and have kernel 3.12 and multiple versions of 3.11 installed. 

Initially, I booted 3.11.0-19 and did the first part of Niccola's instructions, up to the reboot. After rebooting, I had no graphics capabilities *at all, *so I couldn't even pull up a TTY to complete the rest of the steps. Luckily, my 3.12 kernel booted without problems and I completed the rest of the commands there. It should be noted that > sudo amdconfig --adapted=all --initial -f causes an error because "adapted" isn't a valid switch. I assume that had to do with display adapters, of which I'm really only concerned with my internal display (laptop display), so instead I ran > sudo amdconfig --initial -f

After that, I rebooted into 3.11.0-19 and saw the Xubuntu loading animation (Yay!) However, as part of the boot process, the screen blanks after a while and then the login screen is loaded. This time, when the screen blanked, the login screen never appeared. I imagine the blanking has to do with switching to a different video mode or something, which may cause a conflict. But it turns out this is solved by booting up an older kernel version, in my case, 3.11.0-12.

I honestly can't tell if I'm actually running fglrx, but I know I'm not using the radeon drivers anymore. All the commands like lspci -k don't have any "kernel driver in use" line under the graphics card anymore. But youtube and video streaming still works, and most importantly, Mathematica no longer crashes X! netflix-desktop complains about compositing not being available, so I'll probably dig into xorg.conf and see if I can fix that...

Thanks for the very clear procedure, Niccola!

---

### Post by TBeholder on 2014-04-12
An obvious typo: it should be "** --adapter=all**" - to configure for all cards rather than current only (usually this doesn't matter, but it's a very generic instruction).

---

### Post by jms-ubuntu-en on 2014-04-19
Anyone yet using *ziktofel*.deb on 14.04?

---

### Post by anton12 on 2014-05-09
Hi guys,

Today I have managed to get the driver work on Ubuntu 14.04 (LTS) with 3.13 kernel and downgraded X.Org X Server 1.12.4.

The main instructions how to make it work are the same as [for 13.10]("http://ubuntuforums.org/showthread.php?t=2181190&p=12823425#post12823425").

[LIST=1]
[*]Add RARING ppa: **ppa:makson96/fglrx** (I have done it by "sudo add-apt-repository ppa:makson96/fglrx" and replacing /etc/apt/sources.list.d/makson96-fglrx-trusty.list "trusty" with "raring" manually; probably there is a better way, but I don't know it). 
[*]"sudo apt-get update" and installation of all xorg packages ("sudo apt-get update" should probably work too) 
[*]download and install (NOTE: I didn't update the packages meta information (because I am not familiar enough with deb-format), so it is named and signed as from ziktofel and for 13.10; but the content was slightly updated to work for 14.04 -- see details in "technical info"):
[LIST]
[*][https://www.dropbox.com/s/s7bf7t76445bokg/fglrx-legacy_8.97.100.7-ziktofel1%7Esaucy5_amd64.deb](https://www.dropbox.com/s/s7bf7t76445bokg/fglrx-legacy_8.97.100.7-ziktofel1%7Esaucy5_amd64.deb) 
[*][https://www.dropbox.com/s/mojfe7gnjkbcqpf/fglrx-legacy-dev_8.97.100.7-ziktofel1%7Esaucy5_amd64.deb](https://www.dropbox.com/s/mojfe7gnjkbcqpf/fglrx-legacy-dev_8.97.100.7-ziktofel1%7Esaucy5_amd64.deb) 
[*][https://www.dropbox.com/s/yb9n4copgvqvqdp/fglrx-amdcccle-legacy_8.97.100.7-ziktofel1%7Esaucy5_amd64.deb](https://www.dropbox.com/s/yb9n4copgvqvqdp/fglrx-amdcccle-legacy_8.97.100.7-ziktofel1%7Esaucy5_amd64.deb) 
[/LIST]
  
[*]Run "aticonfig --initial" if necessary 
[*]reboot 
[/LIST]

Known issues: 

[LIST=1]
[*]Returning to the X screen after switching to the text console (e.g. Ctrl+Alt+F1) does not work properly sometimes. 
[*]32-bit package isn't built and tested (and will not be built by me because I have no environment to do it; see the description below how to do it -- it's not hard). 
[/LIST]
 
Technical info (for those who wants to build the above deb-packages manually):
1. Download source package as as [for 13.10]("http://ubuntuforums.org/showthread.php?t=2181190&p=12823425#post12823425"): [http://ubuntuone.com/2WkkrzfbHksWJqZjJhuwWm](http://ubuntuone.com/2WkkrzfbHksWJqZjJhuwWm)
2. Unpack it: tar -xzf ./fglrx-legacy_8.97.100.7-ziktofel1~saucy5.tar.gz
3. Build deb-packages for 13.10 (probably instead of steps 1-3 you may just take the original deb-packages for 13.10  ([http://ubuntuone.com/1W4B3qa09OB82avCw9kDvP](http://ubuntuone.com/1W4B3qa09OB82avCw9kDvP),  [http://ubuntuone.com/5fly8Ur8c2PKvUYh2f6V8Z](http://ubuntuone.com/5fly8Ur8c2PKvUYh2f6V8Z),  [http://ubuntuone.com/7HbTMeib9RskH21Qrjv9rl](http://ubuntuone.com/7HbTMeib9RskH21Qrjv9rl)), but I haven't checked it).
4. Unpack the fglrx-legacy deb-package "ar x ./fglrx-legacy_8.97.100.7-ziktofel1~saucy5_amd64.deb" and "tar -Jxf ./data.tar.xz"
5. Add the changes to the files in <fglrx-dir>/usr/src/fglrx-legacy-8.97.100.7 corresponding to the following patch to make drivers work with 3.13 kernel (partially taken from [here]("http://forums.opensuse.org/showthread.php/493913-ATI-Proprietary-driver-13-12-installation-fails-in-openSUSE-13-1")):
```

diff -rup fglrx.orig/firegl_public.c fglrx/firegl_public.c
--- fglrx.orig/firegl_public.c    2013-12-20 01:37:15.155648294 +0100
+++ fglrx/firegl_public.c    2013-12-21 01:02:47.201517242 +0100
@@ -1754,11 +1754,17 @@ KCL_TYPE_Pid ATI_API_CALL KCL_GetTgid(vo
  */
 KCL_TYPE_Uid ATI_API_CALL KCL_GetEffectiveUid(void)
 {
+#ifdef CONFIG_UIDGID_STRICT_TYPE_CHECKS
+    return __kuid_val(current_euid());
+#else
+
 #ifdef current_euid
     return current_euid();
 #else
     return current->euid;
 #endif
+
+#endif
 }
 
 /** /brief Delay execution for the specified number of microseconds
diff -rup fglrx.orig/kcl_acpi.c fglrx/kcl_acpi.c
--- fglrx.orig/kcl_acpi.c    2013-12-20 01:13:55.000000000 +0100
+++ fglrx/kcl_acpi.c    2013-12-21 01:06:00.158734992 +0100
@@ -792,7 +792,9 @@ static unsigned int KCL_ACPI_SearchHandl
 unsigned int ATI_API_CALL KCL_ACPI_GetHandles(kcl_match_info_t *pInfo)
 {
 #if LINUX_VERSION_CODE > KERNEL_VERSION(2,6,12)
-    #if LINUX_VERSION_CODE >= KERNEL_VERSION(3,8,0)
+    #if LINUX_VERSION_CODE >= KERNEL_VERSION(3,13,0)
+        pInfo->video_handle = pInfo->pcidev->dev.acpi_node.companion;
+    #elif LINUX_VERSION_CODE >= KERNEL_VERSION(3,8,0)
         pInfo->video_handle = pInfo->pcidev->dev.acpi_node.handle;
     #elif LINUX_VERSION_CODE > KERNEL_VERSION(2,6,19)
         pInfo->video_handle = pInfo->pcidev->dev.archdata.acpi_handle;

```
6. Pack deb-package back "tar Jcvf ./data.tar.xz ./etc ./lib ./usr" and "ar rcv ./fglrx-legacy_8.97.100.7-ziktofel1~saucy5_amd64.deb debian-binary control.tar.gz data.tar.xz"


Hope this helps someone (or maybe me after a time ;) ).


P.S. Great thanks to Tomasz Makarewicz (for [his ppa]("https://launchpad.net/~makson96/+archive/fglrx")) and [ziktofel]("http://ubuntuforums.org/member.php?u=1842443&tab=activitystream#activitystream") (for update)!

P.P.S. Great "unthanks" to AMD, which made us all these troubles.

---

### Post by ivy2 on 2014-05-18
Thank you [[COLOR=#000000]anton12[/COLOR]]("http://ubuntuforums.org/member.php?u=1922803")[COLOR=#000000] ! You're a life saver. confirmed working - Lubuntu x64 using Ubuntu 14.04 LTS [/COLOR][COLOR=#000000]distribution.[/COLOR]

---

### Post by anakai on 2014-05-19
Hi, excellent work. It worked lie a charm for me on Kubuntu 14.04. I followed your instructions just one thing!
After i downloaded de deb files I run a "sudo dpkg -i *.deb" to install all the deb files I downloaded. Then I had to run "sudo apt-get install -f" to install missing deps.
Good work!!!


> **anton12 said:**
> Hi guys,

Today I have managed to get the driver work on Ubuntu 14.04 (LTS) with 3.13 kernel and downgraded X.Org X Server 1.12.4.

The main instructions how to make it work are the same as [for 13.10]("http://ubuntuforums.org/showthread.php?t=2181190&p=12823425#post12823425").

[LIST=1]
[*]Add RARING ppa: **ppa:makson96/fglrx** (I have done it by "sudo add-apt-repository ppa:makson96/fglrx" and replacing /etc/apt/sources.list.d/makson96-fglrx-trusty.list "trusty" with "raring" manually; probably there is a better way, but I don't know it). 
[*]"sudo apt-get update" and installation of all xorg packages ("sudo apt-get update" should probably work too) 
[*]download and install (NOTE: I didn't update the packages meta information (because I am not familiar enough with deb-format), so it is named and signed as from ziktofel and for 13.10; but the content was slightly updated to work for 14.04 -- see details in "technical info"):
[LIST]
[*][https://www.dropbox.com/s/s7bf7t76445bokg/fglrx-legacy_8.97.100.7-ziktofel1%7Esaucy5_amd64.deb](https://www.dropbox.com/s/s7bf7t76445bokg/fglrx-legacy_8.97.100.7-ziktofel1%7Esaucy5_amd64.deb) 
[*][https://www.dropbox.com/s/mojfe7gnjkbcqpf/fglrx-legacy-dev_8.97.100.7-ziktofel1%7Esaucy5_amd64.deb](https://www.dropbox.com/s/mojfe7gnjkbcqpf/fglrx-legacy-dev_8.97.100.7-ziktofel1%7Esaucy5_amd64.deb) 
[*][https://www.dropbox.com/s/yb9n4copgvqvqdp/fglrx-amdcccle-legacy_8.97.100.7-ziktofel1%7Esaucy5_amd64.deb](https://www.dropbox.com/s/yb9n4copgvqvqdp/fglrx-amdcccle-legacy_8.97.100.7-ziktofel1%7Esaucy5_amd64.deb) 
[/LIST]
  
[*]Run "aticonfig --initial" if necessary 
[*]reboot 
[/LIST]

Known issues: 

[LIST=1]
[*]Returning to the X screen after switching to the text console (e.g. Ctrl+Alt+F1) does not work properly sometimes. 
[*]32-bit package isn't built and tested (and will not be built by me because I have no environment to do it; see the description below how to do it -- it's not hard). 
[/LIST]
 
Technical info (for those who wants to build the above deb-packages manually):
1. Download source package as as [for 13.10]("http://ubuntuforums.org/showthread.php?t=2181190&p=12823425#post12823425"): [http://ubuntuone.com/2WkkrzfbHksWJqZjJhuwWm](http://ubuntuone.com/2WkkrzfbHksWJqZjJhuwWm)
2. Unpack it: tar -xzf ./fglrx-legacy_8.97.100.7-ziktofel1~saucy5.tar.gz
3. Build deb-packages for 13.10 (probably instead of steps 1-3 you may just take the original deb-packages for 13.10  ([http://ubuntuone.com/1W4B3qa09OB82avCw9kDvP](http://ubuntuone.com/1W4B3qa09OB82avCw9kDvP),  [http://ubuntuone.com/5fly8Ur8c2PKvUYh2f6V8Z](http://ubuntuone.com/5fly8Ur8c2PKvUYh2f6V8Z),  [http://ubuntuone.com/7HbTMeib9RskH21Qrjv9rl](http://ubuntuone.com/7HbTMeib9RskH21Qrjv9rl)), but I haven't checked it).
4. Unpack the fglrx-legacy deb-package "ar x ./fglrx-legacy_8.97.100.7-ziktofel1~saucy5_amd64.deb" and "tar -Jxf ./data.tar.xz"
5. Add the changes to the files in <fglrx-dir>/usr/src/fglrx-legacy-8.97.100.7 corresponding to the following patch to make drivers work with 3.13 kernel (partially taken from [here]("http://forums.opensuse.org/showthread.php/493913-ATI-Proprietary-driver-13-12-installation-fails-in-openSUSE-13-1")):
```

diff -rup fglrx.orig/firegl_public.c fglrx/firegl_public.c
--- fglrx.orig/firegl_public.c    2013-12-20 01:37:15.155648294 +0100
+++ fglrx/firegl_public.c    2013-12-21 01:02:47.201517242 +0100
@@ -1754,11 +1754,17 @@ KCL_TYPE_Pid ATI_API_CALL KCL_GetTgid(vo
  */
 KCL_TYPE_Uid ATI_API_CALL KCL_GetEffectiveUid(void)
 {
+#ifdef CONFIG_UIDGID_STRICT_TYPE_CHECKS
+    return __kuid_val(current_euid());
+#else
+
 #ifdef current_euid
     return current_euid();
 #else
     return current->euid;
 #endif
+
+#endif
 }
 
 /** /brief Delay execution for the specified number of microseconds
diff -rup fglrx.orig/kcl_acpi.c fglrx/kcl_acpi.c
--- fglrx.orig/kcl_acpi.c    2013-12-20 01:13:55.000000000 +0100
+++ fglrx/kcl_acpi.c    2013-12-21 01:06:00.158734992 +0100
@@ -792,7 +792,9 @@ static unsigned int KCL_ACPI_SearchHandl
 unsigned int ATI_API_CALL KCL_ACPI_GetHandles(kcl_match_info_t *pInfo)
 {
 #if LINUX_VERSION_CODE > KERNEL_VERSION(2,6,12)
-    #if LINUX_VERSION_CODE >= KERNEL_VERSION(3,8,0)
+    #if LINUX_VERSION_CODE >= KERNEL_VERSION(3,13,0)
+        pInfo->video_handle = pInfo->pcidev->dev.acpi_node.companion;
+    #elif LINUX_VERSION_CODE >= KERNEL_VERSION(3,8,0)
         pInfo->video_handle = pInfo->pcidev->dev.acpi_node.handle;
     #elif LINUX_VERSION_CODE > KERNEL_VERSION(2,6,19)
         pInfo->video_handle = pInfo->pcidev->dev.archdata.acpi_handle;

```
6. Pack deb-package back "tar Jcvf ./data.tar.xz ./etc ./lib ./usr" and "ar rcv ./fglrx-legacy_8.97.100.7-ziktofel1~saucy5_amd64.deb debian-binary control.tar.gz data.tar.xz"


Hope this helps someone (or maybe me after a time ;) ).


P.S. Great thanks to Tomasz Makarewicz (for [his ppa]("https://launchpad.net/~makson96/+archive/fglrx")) and [ziktofel]("http://ubuntuforums.org/member.php?u=1842443&tab=activitystream#activitystream") (for update)!

P.P.S. Great "unthanks" to AMD, which made us all these troubles.

---

### Post by monkeybrain20122 on 2014-05-19
There has been a lot of progress in the open source radeon driver. Instead of forcing to install the fglrx driver I would just upgrade the open driver. For Ubuntu 13.10 and 14.04 [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)  For gpu decoding see the section " Using VDPAU/XvMC accelerated video"in the link.
For 12.04 [https://launchpad.net/~pali/+archive/graphics-drivers](https://launchpad.net/~pali/+archive/graphics-drivers)

For the temperature problem if you have kernel 3.11 or above.
```
gksudo gedit /etc/default/grub
```

Change the line 

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.dpm=1"

Then save, close gedit and run
```

sudo update-grub
```

---

### Post by mike-freeman-studio on 2014-06-02
> **monkeybrain20122 said:**
> There has been a lot of progress in the open source radeon driver. Instead of forcing to install the fglrx driver I would just upgrade the open driver.

This is fine in for average generic use, but on my machine (Mobility Radeon HD 4200), even the newest open source drivers are unusable for the games my family enjoys playing. The AMD Legacy driver is a MUST in that case. The open-source drivers just aren't nearly up to snuff, at least for older cards. So, I'm going to give this method a go on a 14.04 test partition.

---

### Post by monkeybrain20122 on 2014-06-02
> **mike-freeman-studio said:**
> This is fine in for average generic use, but on my machine (Mobility Radeon HD 4200), even the newest open source drivers are unusable for the games my family enjoys playing. The AMD Legacy driver is a MUST in that case. The open-source drivers just aren't nearly up to snuff, at least for older cards. So, I'm going to give this method a go on a 14.04 test partition.

Don't use that ppa from my post at this point. There was a bad commit in the last day or so and things have blown up, just checked that the commit has been reveresed upstream, so wait a bit for the next update.

---

### Post by mike-freeman-studio on 2014-06-02
Well, this time around, it didn't work. As soon as X starts, the whole system completely locks up with a black screen, no disk activity, no response to any keypresses (including Caps Lock, Num Lock, Power, etc.). So, I'll try again, but if I can't get this working, I may have to give up on having a nice, shiny, up-to-date OS. :(

---

### Post by mike-freeman-studio on 2014-06-02
> **monkeybrain20122 said:**
> Don't use that ppa from my post at this point. There was a bad commit in the last day or so and things have blown up, just checked that the commit has been reveresed upstream, so wait a bit for the next update.

Just saw this. Ok. I'll wait before trying again.

---

### Post by mike-freeman-studio on 2014-06-02
> **monkeybrain20122 said:**
> Don't use that ppa from my post at this point. There was a bad commit in the last day or so and things have blown up, just checked that the commit has been reveresed upstream, so wait a bit for the next update.

Ok, just to clarify... Are you talking about the makson96 Proprietary driver PPA, or the open-source driver PPA? I've already got the recent open-source driver running, and it's not usable for me. It's the makson96 PPA method that I'm trying.

---

### Post by monkeybrain20122 on 2014-06-02
> **mike-freeman-studio said:**
> Ok, just to clarify... Are you talking about the makson96 Proprietary driver PPA, or the open-source driver PPA? I've already got the recent open-source driver running, and it's not usable for me. It's the makson96 PPA method that I'm trying.

I am talking about the open one (oibaf). It appears that makson's ppa only works up to 13.10 (no entry for 14.04). Since 13.10 only has a bit longer than one month of support I wouldn't bother if I were you.

---

### Post by 9v-shaun-42 on 2014-06-21
Hi all.

I don't suppose anyone still has ziktofel's source files?  I'd like to repeat anton12's results with the possible addition of uploading the source and built packages to a PPA but with the end of Ubuntu One the provided download links are dead.

Cheers.
Shaun.

---

### Post by Andreas Kohlbecker on 2014-06-23
Hi Shaun,

I just came across your post and checked my workingspaces. I am still having ziktofel's source files! I put them on a dropbox for a while: 
 - [fglrx-legacy_8.97.100.7-ziktofel1~saucy5.tar.gz]("https://dl.dropboxusercontent.com/u/77620030/fglrx-legacy_8.97.100.7-ziktofel1~saucy5.tar.gz")
 - [fglrx-legacy_8.97.100.7-ziktofel1~saucy5.dsc]("http://dl.dropboxusercontent.com/u/77620030/fglrx-legacy_8.97.100.7-ziktofel1~saucy5.dsc")

Cheers
Andreas

---

### Post by 9v-shaun-42 on 2014-06-28
Thanks Andreas.  I'm downloading them now.

---

### Post by Richard_Fleming on 2014-07-21
Any chance that someone might be able to provide a list of exact instructions for getting this to work on a 32-bit system? I can follow instructions if they're precise but I'm pretty much a Linux newbie. It would be great, though, to get my Radeon 2400 Pro working fully.

---

### Post by QIII on 2014-07-21
Hello, Richard_Fleming.

At the very best, those methods for installing that driver on Precise were problematic:  They effectively *break *your OS with unpredictable results.

I would *HIGHLY *recommend *against* trying to use any of those methods -- I don't know how many people I have helped recover broken systems after trying them.

I suggest continuing to use the default open source Radeon driver supplied when you installed Ubuntu and avoid the headaches of a possible borked machine.

---

### Post by Richard_Fleming on 2014-07-21
Thanks for the advice. Unfortunately it looks like this machine is stuck with very choppy video playback then.

---

### Post by Richard_Fleming on 2014-07-21
Is the solution for those who want to game on Linux with an AMD card to go back to an old version of Linux then, one that's compatible with the Catalyst driver? Or have things changed so much that that's not viable?

---

### Post by takeru on 2015-04-12
Pardon the bump, I just wanted to report that [anton12's instructions]("http://ubuntuforums.org/showthread.php?t=2181190&page=7&p=13019100#post13019100") works flawlessly in Elementary OS Freya (released today), letting me take full advantage of my 4670. The only extra thing I had to do was install the 3.8 kernel using debs from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-raring/").

 Thanks!

---

### Post by QIII on 2015-04-12
Thank you for your comment.

This is a very old thread, however.

Closed.

---

