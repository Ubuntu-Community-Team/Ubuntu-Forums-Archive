---
title: "Get GMA500 (Poulsbo) working in Karmic with Jaunty backports.."
date: 2009-08-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Marko Helenius on 2009-08-30
Hi,

I've been using Karmic in my Poulsbo laptop with decent resolution and performance for a while now. Since there are lot of discussions ongoing where fellow forumers are looking for the same solution, I decided to publish my notes about it. Hopefully someone will find it useful, no guarantee.. :)

Start by downloading lucazades psb-kernel-* packages [http://swiss.ubuntuforums.org/showpost.php?p=7773647&postcount=13](http://swiss.ubuntuforums.org/showpost.php?p=7773647&postcount=13)

Following code samples are stripped from my install-poulsbo.sh, almost everything requires sudo:

```

# Adding required PPAs
echo 'deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main' >> /etc/apt/sources.list
echo 'deb-src http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main' >> /etc/apt/sources.list
echo "" >> /etc/apt/sources.list

echo 'deb http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu jaunty main ' >> /etc/apt/sources.list
echo 'deb-src http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu jaunty main' >> /etc/apt/sources.list
echo "" >> /etc/apt/sources.list

# Keys for PPAs
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6598A30
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 99C0198F

apt-get update
apt-get install  dkms fakeroot

apt-get install libdrm-poulsbo1
apt-get install poulsbo-driver-2d poulsbo-driver-3d psb-firmware

# Install downloaded psb-kernel-* packages
dpkg -i psb-kernel-*

echo "blacklist i915" >> /etc/modprobe.d/blacklist.conf

update-initramfs -u

```Create xorg.conf with following content:

```
Section "Device"
        Identifier      "GMA500"
        Option "AccelMethod" "EXA"
#        Option "DRI" "off"
        Option "MigrationHeuristic" "greedy"
        Option "IgnoreACPI" "yes"
        Driver "psb"
EndSection

Section "DRI"
    Mode    0666
EndSection

```And reboot..

I think the key elements are:
* Alberto's libdrm-poulsbo1 which doesn't collide with Karmic's librdm2
* Blacklisting i915 and updating initramfs, so i915 and wrong drm.ko are *not* loaded

Since I actually didn't do anything myself, I thank Lucazade, Albertomilone and Ubuntu-mobile for enabling this. ;) I'll try to keep this short instruction up-to-date, so please let me know how it goes.


_______________________________________________________________________
Edit: added DRI Mode Section

---

### Post by jbernardo on 2009-08-30
Thanks! I'll try updating to karmic straight away, will tell you how it goes.

---

### Post by lucazade on 2009-08-30
:) Great mate!

---

### Post by jbernardo on 2009-08-30
It's working, at least the same as it is working in Jaunty - no working compositing, no 3d acceleration. But at least 2D now works. Thanks!

---

### Post by Marko Helenius on 2009-09-02
> **jbernardo said:**
> It's working, at least the same as it is working in Jaunty - no working compositing, no 3d acceleration. But at least 2D now works. Thanks!

Nice to know! :)

Friend of mine reported that DRI Section was required for 3D operations in Dell laptop, added to xorg.conf example.

---

### Post by jbernardo on 2009-09-02
> **Marko Helenius said:**
> Nice to know! :)

Friend of mine reported that DRI Section was required for 3D operations in Dell laptop, added to xorg.conf example.

With DRI on or off? I'll try now the "Section DRI" setting, to see if it changes anything.

---

### Post by MartinuxP on 2009-09-03
Hi, i've used your scripts and they runs, It says direct rendering: yes (glxinfo) but the computer is very slow, scrolling in the browser makes it flicks.
Is that right?

Sorry for my poor english!

---

### Post by jbernardo on 2009-09-03
> **MartinuxP said:**
> Hi, i've used your scripts and they runs, It says direct rendering: yes (glxinfo) but the computer is very slow, scrolling in the browser makes it flicks.
Is that right?

Sorry for my poor english!

Try glblur (from xscreensavers-gl), here when I run it with "/usr/lib/xscreensaver/glblur -fps -window" I get about 16 fps, the same under jaunty. For comparison, my AA1, which has a GMA945, gives 25fps...

---

### Post by Starks on 2009-09-03
Somebody should add this guide to the Ubuntu wiki. If not, I will.

Is the DRI section in the xorg.conf needed for 3D or Compiz?

---

### Post by jbernardo on 2009-09-04
> **Starks said:**
> Somebody should add this guide to the Ubuntu wiki. If not, I will.

Is the DRI section in the xorg.conf needed for 3D or Compiz?

It should be in the release notes, as a _temporary_ work around for GMA500 support in Karmic, until there is a fully working driver.

As for the DRI section, I didn't test compiz, but on my Asus 1101HA it didn't change anything. The same fps with glblur, and still can't enable kwin effects.

---

### Post by Starks on 2009-09-04
BTW, the page to edit will be here: [http://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](http://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by perfect-camouflage on 2009-09-04
Installation of packages and compiling the psb-kernel-source was successful. But if I try to start gdm an error occurs in xorg log file:

xf86MapVidMem: Could not mmap framebuffer (0x7f6a3010,0x800000) (Operation not permitted)

Any ideas how to solve this???


Installation was made on  Ubuntu Karmic 9.10 Alpha 5 on a Sony Vaio P11Z.

---

### Post by Caliph Alexander on 2009-09-06
As per AdamW ([http://www.happyassassin.net/2009/05/13/native-poulsbo-gma-500-graphics-driver-for-fedora-10/](http://www.happyassassin.net/2009/05/13/native-poulsbo-gma-500-graphics-driver-for-fedora-10/)), add a 'mem=2000MB' parameter to your kernel string, in grub.cfg.  This is a Vaio P-specific issue.

Good luck!

---

### Post by excogitation on 2009-09-07
Nice. Thanks a lot for this guide.

Afair glxgears isn't accurate enough for benchmarks
but without this driver I had around 50-200fps,
with the settings from the first post I get about
800-1800fps depending on EXA/UXA, DRI on/off.

Also you can get Compiz working by setting
```
Option "DRI" "on"
```
in xorg.conf and whitelisting psb in
/usr/bin/compiz
by adding "psb" to the WHITELIST line.

after a reboot go to System -> Preferences -> Appearance and click the Visual Effects and change the setting to "normal".

Info taken from [here]("http://ubuntuforums.org/showthread.php?t=1229345")

Drops glxgears fps to about half (~500fps) though.

---

### Post by jack_mcdowell on 2009-09-12
> **jbernardo said:**
> Try glblur (from xscreensavers-gl), here when I run it with "/usr/lib/xscreensaver/glblur -fps -window" I get about 16 fps, the same under jaunty. For comparison, my AA1, which has a GMA945, gives 25fps...
I'm gettin about 2-5 fps! when doing that, on a dell mini 10 with the 1.33 atom. I have (I think) done everything correctly. I have a proper xorg.conf and the correct screen resolution. Any helps, tips, in finding out why it is so slow? Oh, and I'm using 9.04. Thanks, Jack

---

### Post by jack_mcdowell on 2009-09-12
just tested glxgears and the highest I can get is 102 frames... definitely something wrong here...

---

### Post by excogitation on 2009-09-12
Just in case anyone else runs into this:

For my Vaio P I needed to add mem=2000MB to /etc/default/grub
(I put it at the end of GRUB_CMDLINE_LINUX_DEFAULT) and run update-grub.

(I didn't pay attention that grub2 got installed through a recent update).

---

### Post by jbernardo on 2009-09-15
Well, grub2 on my eee 1101HA doesn't boot - it hangs at "welcome to grub". I had to go back to grub 1.

But what I wanted to ask is if anyone else saw a performance regression with the latest karmic kernel. For me, FPS in glblur have dropped from 15-16 to 9, with 90% cpu. I am going to see if the "mem" parameter in grub will help...

---

### Post by jbernardo on 2009-09-15
Adding the "mem=2000mb" entry in grub brought performance in glblur back to 15-16fps from the 8-9 fps I had before. Still a far cry from the AA1's 30fps, but better.

---

### Post by AdamWill on 2009-09-24
jbernardo: those numbers are about what I'd expect. the few comparative benchmarks I've seen show the GMA 500 as about half as fast as the GMA 945/950 even in Windows. The hardware's just slower.

---

### Post by myrddin52 on 2009-09-27
I just followed this instructions to install new video on Karmic alpha6 on my Sony P11Z and it is working fine. Even suspend and the hotkeys for brightness are working :razz:

Many thanks

---

### Post by Leed on 2009-10-02
Nice thread, I'll sure pay another visit here once I upgrade my eeepc T91 to karmic. I still can't believe there's no psb drivers in karmic, kept me scared of the upcoming upgrade ever since I heard the rumors.

---

### Post by rednukleus on 2009-10-02
I have an Acer AO751h.  I got an error with the tar.gz file when I tried to install the downloaded psb-kernel-* packages. I pasted my output here: [http://pastebin.com/m539cd98b](http://pastebin.com/m539cd98b)

I continued anyway. Hopefully it will work! Please help me if I did something wrong. ..... It seems to have worked. I have the correct resolution now. I've only followed the first post of this thread. Should I do something else? I haven't addressed the error with the tar.gz file.

I installed flashplugin-nonfree through apt-get and I was thrilled to find that Youtube works much more smoothly than it did in Vista. Flash performance was my major reason for getting rid of Vista.

For the general interface performance, is there a way to improve it at all with hardware acceleration? At the moment, I get an error when I try to enable visual effects. I'm not interested in visual effects, but I am interested in hardware acceleration of the desktop environment if possible, to speed things up.

---

### Post by flesh99 on 2009-10-03
> **rednukleus said:**
> I have an Acer AO751h.  I got an error with the tar.gz file when I tried to install the downloaded psb-kernel-* packages. I pasted my output here: [http://pastebin.com/m539cd98b](http://pastebin.com/m539cd98b)

I continued anyway. Hopefully it will work! Please help me if I did something wrong. ..... It seems to have worked. I have the correct resolution now. I've only followed the first post of this thread. Should I do something else? I haven't addressed the error with the tar.gz file.

You don't need to worry about the error. You didn't need to tarball, only the debs. The error is because dpkg tried to install the tar.gz as a deb. Nothing to worry about.

---

### Post by flesh99 on 2009-10-03
Acer 0751h now running in native resolution without any major issues following the guide in the first post. I haven't tested Flash video but that's not an issue for me. I picked up the netbook for under 250 USD to use to connect to my development environment and hosted google apps. With this guide it does exactly what I need it to do. Flash video and HD video are not a concern. I just hope that this guide continues to work after the inevitable kernel updates.

lucazade: I noticed you have a PPA for Karmic containing the debs listed in the guide. Any word on setting up using your PPA?

---

### Post by michael37 on 2009-10-03
I am confused.  If Intel and Canonical tell us that[ there will be no psb support in Karmic 9.10]("http://www.phoronix.com/scan.php?page=news_item&px=NzQzMg"), why bother hacking it?  Isn't Jaunty good enough to wait out till Lucid Lynx 10.04?

---

### Post by lucazade on 2009-10-04
> **michael37 said:**
> I am confused.  If Intel and Canonical tell us that[ there will be no psb support in Karmic 9.10]("http://www.phoronix.com/scan.php?page=news_item&px=NzQzMg"), why bother hacking it?  Isn't Jaunty good enough to wait out till Lucid Lynx 10.04?

Simply because Jaunty support was poor...
In karmic you can also take advantage of "[ClientSideWindows]("http://live.gnome.org/GTK%2B/ClientSideWindows")" feature besides new kernel and software.

Who told you there will be support for Poulsbo in Lucid Lynx 10.04? Mark? Who? :)

---

### Post by michael37 on 2009-10-04
> **lucazade said:**
> Simply because Jaunty support was poor...
In karmic you can also take advantage of "[ClientSideWindows]("http://live.gnome.org/GTK%2B/ClientSideWindows")" feature besides new kernel and software.

Who told you there will be support for Poulsbo in Lucid Lynx 10.04? Mark? Who? :)

Jaunty support for Poulsbo was poor, but Karmic is worse (well, we can say it's about equal given your backport hack).  About 10.04 support -- I was hoping.  Given that Moblin 2.1 came out without GMA 500, the chances of improvement are probably quite dismal :(

It's a pity, I really like my Dell Mini 12 otherwise.

---

### Post by NormanFLinux on 2009-10-04
The vesa drivers give a good display on my Dell Mini 10. The driver situation may or not be rectified. Its too bad we can't run the Windows drivers under WINE.

---

### Post by ludwigbaum on 2009-10-05
Hardware: Sony Vaio VGN-P11Z, System Ubuntu Karmic Beta

I followed the instructions above carefully, controlled every step twice.
The repositories  are there, the authentication keys are there, xorg.conf is correct, the whitelist is correct, the deb-modules install without any sign of a problem, but the result is a hanging start-procedure, flickering video with command-line-log-in.
By the way, I don't know, how the Sony-function-keys (brightness) should work, as someone pretends - they are not part of the poulsbo-driver (?).
 
fdisk /mbr
Windows works

---

### Post by iorbell on 2009-10-05
Just a quick note to say thanks for this thread - I had been struggling for several weeks to load some form of Linux on my MSI X320 laptop with half decent graphics (i.e. not vesa), following several different sets of instructions, and loading numerous different versions of Ubuntu/Fedora etc. These instructions were the first that worked...:)

---

### Post by excogitation on 2009-10-06
> **ludwigbaum said:**
> Hardware: Sony Vaio VGN-P11Z, System Ubuntu Karmic Beta

I followed the instructions above carefully, controlled every step twice.
The repositories  are there, the authentication keys are there, xorg.conf is correct, the whitelist is correct, the deb-modules install without any sign of a problem, but the result is a hanging start-procedure, flickering video with command-line-log-in.
By the way, I don't know, how the Sony-function-keys (brightness) should work, as someone pretends - they are not part of the poulsbo-driver (?).
 
fdisk /mbr
Windows works

> **excogitation said:**
> Just in case anyone else runs into this:

For my Vaio P I needed to add mem=2000MB to /etc/default/grub
(I put it at the end of GRUB_CMDLINE_LINUX_DEFAULT) and run update-grub.


On my P11Z the brightness keys do work - just there are way to many settings (you have to klick twice for each brightness level).

---

### Post by michael37 on 2009-10-06
> **michael37 said:**
> Jaunty support for Poulsbo was poor, but Karmic is worse (well, we can say it's about equal given your backport hack).  About 10.04 support -- I was hoping.  Given that Moblin 2.1 came out without GMA 500, the chances of improvement are probably quite dismal :(

It's a pity, I really like my Dell Mini 12 otherwise.

Update, got brand new beta of karmic LPIA on my Dell Mini 12 with Poulsbo drivers suggested in this thread.  Graphics works splendidly (faster than on another install with Jaunty -- not sure why, maybe legacy?).  Whoever tells you to use i386 instead of lpia, they are lying. 

Now to fix the brightness/dimness keys and suspend...

---

### Post by lucazade on 2009-10-06
> **michael37 said:**
> Update, got brand new beta of karmic LPIA on my Dell Mini 12 with Poulsbo drivers suggested in this thread.  Graphics works splendidly (faster than on another install with Jaunty -- not sure why, maybe legacy?).  Whoever tells you to use i386 instead of lpia, they are lying. 

Now to fix the brightness/dimness keys and suspend...

So, you're happy now?!? ;)

---

### Post by michael37 on 2009-10-06
> **lucazade said:**
> So, you're happy now?!? ;)

:)

---

### Post by michaelcole on 2009-10-07
Hi, I just bought a new Acer Aspire One - Model ZA3.  I was looking for a netbook to run Ubuntu Remix on.

After loading it, graphics performance is stupid slow.

When I do a lspci, it has "(SCH Poulsbo) (rev 07)" on every line, except the Ethernet controller.

After reading this thread, and others, it seems like this netbook won't have decent drivers into the future.

Is this true?  Should I return it and get another?  If so, which would you recommend?

Thanks,

Mike

---

### Post by gzaro on 2009-10-09
Thank you very much for this guide!

I hope for a  better fix but this solution works in karmic beta.

---

### Post by DShad on 2009-10-09
Thank you VERY MUCH!!

I can now use my Sony Vaio-P with Ubuntu Netbook Remix and it works like a charm!!  :)

---

### Post by ludwigbaum on 2009-10-10
Vaio p11z, Ubuntu Karmic Beta

Once again, I installed Karmic Beta and followed the steps above letter by letter. I did not forget the mem=2000mb. Nevertheless, the result is kernel panic after the first steps of the reboot, a pulsating screen with command-line-login, which does not accept any input.

I'd like to hear that someone has done it successfully with Karmic BETA Desktop-Edition. Alternatively: Which build of Karmic runs successfully with the changes?

---

### Post by nukedeath on 2009-10-10
> **ludwigbaum said:**
> Vaio p11z, Ubuntu Karmic Beta

Once again, I installed Karmic Beta and followed the steps above letter by letter. I did not forget the mem=2000mb. Nevertheless, the result is kernel panic after the first steps of the reboot, a pulsating screen with command-line-login, which does not accept any input.

I'd like to hear that someone has done it successfully with Karmic BETA Desktop-Edition. Alternatively: Which build of Karmic runs successfully with the changes?

The same happened to me last night!!
Pulsating screen on reboot :(

---

### Post by jbernardo on 2009-10-10
> **nukedeath said:**
> The same happened to me last night!!
Pulsating screen on reboot :(
Strange, my eee 1101HA is now working... One thing I had to do was to boot in recovery mode after the latest kernel update, and do a "dpkg-reconfigure psb-kernel-source". The only other difference is that I am using lucazade's ppa instead of installing his debs from this thread. That means that I also had to play with dpkg-divert to remove the redirections of /usr/lib/libGL.*.
If you have openGL broken (kde not starting even if X works, etc.) it might be worth a shot, first do a "dpkg-divert --list", then "dpkg-divert --remove" for all the libGL divertions.

---

### Post by excogitation on 2009-10-10
```
sudo dpkg-reconfigure psb-kernel-source
```

edit: well someone already said that ;-)

---

### Post by nukedeath on 2009-10-10
Hello again!
I must now report that i have 2d and 3d acceleration, and compiz works. But bad perfomance, but hey, i got native resolution! :D

EDIT: Anyone know how to enable vertical sync?, looks bad on youtube and VLC.
And spotify audio lags on wine then panics.

---

### Post by ludwigbaum on 2009-10-11
> **nukedeath said:**
> Hello again!
I must now report that i have 2d and 3d acceleration, and compiz works. But bad perfomance, but hey, i got native resolution! :D

EDIT: Anyone know how to enable vertical sync?, looks bad on youtube and VLC.
And spotify audio lags on wine then panics.

My impression is, that we lead a discussion with an important lack of precision. There are reports, that it's working, that it it's not working, that it's working but ...
nukedeath reports at first, that he encounters problems after the reboot (kernel-panic). Than he reports, that it's working and that he got native resolution.
That's fine, but my Karmic beta has native resolution from the beginning (even the desktop of the live-CD offers 1600x768). If nukedeath uses the same hardware (Vaio p11z), there must be a difference in the software.
Conclusion: It's necessary to indicate precisely the karmic-build (and the edition) which has been used.

---

### Post by lucazade on 2009-10-11
Simplified GMA-500/Poulsbo drivers installation:

Install Ubuntu, reboot into recovery mode and use one of the following script:

1) FTP-based (no ppa repositories):
```
wget http://gma500re.altervista.org/scripts/poulsbo.sh && sh ./poulsbo.sh
```

or

2) PPA-based (UbuntuMobile & Milone): 
```
wget http://gma500re.altervista.org/scripts/poulsbo_ppa.sh && sh ./poulsbo_ppa.sh
```

Let me know if ok.. I've tested them on a Acer AO751h. :)

---

### Post by jbernardo on 2009-10-11
I just checked the scripts, they seem great! I'd just recommend adding the mem=2000mb entry to the grub menu, but the place to do that depends on the grub version.

Any reason not to add your ppa besides those two?

---

### Post by lucazade on 2009-10-11
because my ppa is still incomplete

---

### Post by ludwigbaum on 2009-10-11
At first: Thanks to lucazade for his efforts.

Hardware Vaio p11z

This time I, Idownloaded Karmic-UNR-live-CD and installed it without updating. Then I rebooted in recovery-mode and ran the ppa-based script. It executed normally.
Then I tried to reboot and, once again, got the pulsating screen, indicating kernel-panic.

Observations: I got some messages, which -perhaps- are involved.

"Kernel preparation unnecessaary for this kernel. Skipping ..."

Then, after "DKMS:add completed" another message:

"No original module exists within this kernel".

---

### Post by nukedeath on 2009-10-11
> **ludwigbaum said:**
> My impression is, that we lead a discussion with an important lack of precision. There are reports, that it's working, that it it's not working, that it's working but ...
nukedeath reports at first, that he encounters problems after the reboot (kernel-panic). Than he reports, that it's working and that he got native resolution.
That's fine, but my Karmic beta has native resolution from the beginning (even the desktop of the live-CD offers 1600x768). If nukedeath uses the same hardware (Vaio p11z), there must be a difference in the software.
Conclusion: It's necessary to indicate precisely the karmic-build (and the edition) which has been used.

Well, lets precisionize abit :3

**Hardware: **
Asus EEE 1101HA.

**OS: **
Ubuntu 9.10 beta, daliy build (10.10.09)

**Problem: **
No hardware acceleration, no native resolution, bad performance everywhere.

**First Try: **
Failed, kernel panic, pulsating screen, mainly because i forgot to download lucazades psb-kernel-* packages.

**Second Try: **
After reinstall i followed the instructions step by step (and downloaded the psb-kernel-* packages) and poff, it did work. 
Had to change DRI to "on" in xorg.conf and add "psb" to the WHITELIST line in "/usr/bin/compiz" to enable Compiz desktop effects, Which is Laggy.

More problems: [LIST]
[*]Movies have laggy audio in VLC
[/LIST]
[LIST]
[*]Vertical sync problems (Vertical Tearing) when watching youtube and videos.
[/LIST]
[LIST]
[*]And when running a non native resolution on Quake Live fullscreen (1280x720) it does not scale to fullscreen, shoppy audio and 15-30 FPS.
[/LIST]
[LIST]
[*]Hotkeys for screen brightness not working
[/LIST]

EDIT: LOADS :3

---

### Post by Brzydal on 2009-10-11
hey everybody, another eee1101ha user here.

i installed karmic and make last upgrade. got kernel 2.6.31-13.
then installed gma 500

for newest psb kernel-headers / source and modules, just add to sources.list this lines:
```
deb http://ppa.launchpad.net/lucazade/gma500/ubuntu/ karmic main
deb-src http://ppa.launchpad.net/lucazade/gma500/ubuntu/ karmic main
```and install psb-kernel-headers psb-kernel-sources and psb-modules via apt-get

```
mj@brzydal:~$ **sudo aptitude show psb-kernel-headers**
Pakiet: psb-kernel-headers
Stan: zainstalowany
Zainstalowany automatycznie: nie
Wersja: **4.41.6-0ubuntu1~910um1**
Priorytet: opcjonalny
Sekcja: misc
Opiekun: Ubuntu Mobile Developers <ubuntu-mobile@lists.ubuntu.com>
Rozmiar rozpakowanego: 471k
Opis: Kernel module headers for the Poulsbo (psb) 2D X11 driver
 This package contains the kernel headers for the Poulsbo (psb) 2D X11 driver.
```

---

### Post by jbernardo on 2009-10-11
@Brzydal
> **lucazade said:**
> because my ppa is still incomplete
That might be a reason not to use that PPA yet, as it's owner/author says it still is incomplete. :)

---

### Post by ludwigbaum on 2009-10-11
Vaio P11Z, Karmic Beta UNR (10-10-09)

My problem seems to be inside xorg.conf .
I got an error "mmap framebuffer" or "mmap framebuffersize", when I started X from the command-line (recovery-mode). Therefore I tried this:

In the fresh installation without any updates (and without psb-driver) I created the xorg.conf (the model above via clipboard), added "mem=2000MB" to the grub-configuration and rebooted.

Once again, I got my pulsating screen, which indicates a problem with the X-server, not kernel-panic.

My system shows 266MB reserved for video. Is "mem=2000MB" really correct? (RAM-Size-Video=2048-266=1782). Any ideas?

---

### Post by Jonathanius on 2009-10-11
> **lucazade said:**
> Simplified GMA-500/Poulsbo drivers installation:

Install Ubuntu, reboot into recovery mode and use one of the following script:

1) FTP-based (no ppa repositories):
```
wget http://gma500re.altervista.org/scripts/poulsbo.sh && sh ./poulsbo.sh
```or

2) PPA-based (UbuntuMobile & Milone): 
```
wget http://gma500re.altervista.org/scripts/poulsbo_ppa.sh && sh ./poulsbo_ppa.sh
```Let me know if ok.. I've tested them on a Acer AO751h. :)

I noticed that you used the 4.41.2 instead of 4.41.6, do you recommend the 4.41.2?

---

### Post by ludwigbaum on 2009-10-11
It's done. Karmic Beta UNR works on my Vaio P11Z.

After the installation of Karmic, I installed all available updates.
Then, after a reboot, I applied lucazade's ppa-script in the terminal of the desktop. I did not use the recovery-mode!

The script worked perfectly. I controlled xorg.conf and the blacklist with the editor, everything was there.
Then I changed the grub-configuration in /etc/default/grub. I added "mem=1700mb nohz=off" to the cmdline mentioned above, followed by the obligatory "update-grub".

I don't know, if this is the best solution, but the acceleration in Firefox is visible, and the function-keys for brightness are working. As far as I can see, the only difference between my failures and the successfull attempt is in the grub-configuration; mem=2000mb seems to be incompatible with my Vaio. "nohz=off" is perhaps not necessary.

---

### Post by phoenix__ on 2009-10-12
I've just done this on a Dell mini 10 with ubuntu-9.10-beta-netbook-remix-i386. Everything was working fine until I rebooted. Now I get the ubuntu logo for a moment, then a black screen with blue pixel squares and flashing green lines at the top of the screen.

I've tried changing to a console with ctrl+Alt+F1 but that doesn't work, neither does pressing ctrl+alt+del to reboot however when I press the power button, I get the ubuntu logo for a moment, then the machine turns off.

I've tried getting into the grub menu when it says 'grub loading', but neither esc or tab do anything.

Anyone got any ideas?

---

### Post by SQuark on 2009-10-12
I had the same thing happen when I tried to use the same xorg.conf I used to use in Jaunty.

To fix it, I put an Ubuntu Live CD on a USB stick (using USB Startup Disk Creator), booted from that, mounted my HD and deleted the xorg.conf file.

I then rebooted and followed the instructions from this thread.

---

### Post by ludwigbaum on 2009-10-12
I refer to SQuark above without quoting:

Yes, but perhaps in a different way:
Start the live-CD (or USB-media), open the terminal, start gedit with sudo, navigate to the mounted hd, load /etc/X11/xorg.conf, save it as a backup-file, delete the text and save the empty xorg.conf.
This way, you get a backup-file and no problems with the horrible UUID; gedit navigates for you.

If the grub-menu doesn't appear, I suppose that the problem is inside the grub-configuration. Do you get some lines of text when you start the sytem?

---

### Post by phoenix__ on 2009-10-13
Thanks for the replies.

I've tried this, but even after removing the xorg.conf and rebooting I get the ubuntu logo for a moment, then the blue boxes at the top (there is no longer the green bars).

I can see that grub is loading, it flashes 'grub <something>' very quickly (too quick to be able to read the something).

---

### Post by jbernardo on 2009-10-13
Can't you press escape and get to the grub menu, when it flashes by? From there you could use the recovery entry, which should let you boot to a command prompt. I think usplash/xsplash might be leaving the gma500 in a unusable mode.

---

### Post by ludwigbaum on 2009-10-13
There are still some problems in Karmic: Unclean shutdowns can destroy the environment block. And the first failure to start the new psb-configuration results perhaps in an unclean shutdown.
If you manage to get into the grub-menu, press “e”. Delete the first two lines in the new screen (delete-key or ctrl-d). Press ctrl-x to restart grub. If necessary, you can even edit the kernel-line.
If this is not successful, you are in real trouble. Google for “bad environment block”.

---

### Post by phoenix__ on 2009-10-13
I managed to get into grub after about 10 attempts, and deleted the first 2 lines as suggested. I also took out the quiet and splash options.

This time, it booted and gave me the text outout I expected, however then the screen went black (at the time I would expect the GUI login to appear) and nothing happened. I couldn't change to a console or anything.

---

### Post by ludwigbaum on 2009-10-13
Sorry, the error message is "invalid environment block". It is discussed here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784)

Perhaps a fresh installation is less frustrating. But it seems, that there are still bugs, concerning grub2 and ext4. Karmic beta is a little bit more alpha than expected.

---

### Post by phoenix__ on 2009-10-13
I have no issue doing a fresh installation, the only thing I have done to this machine is a dist-upgrade and then attempting to get this working.

---

### Post by NormanFLinux on 2009-10-14
I would hold off installing the Poulsbo drivers until Karmic emerges from beta. There are updates every day 2X a day. Its still not ready to make a final driver installation.

---

### Post by jbernardo on 2009-10-14
> **NormanFLinux said:**
> I would hold off installing the Poulsbo drivers until Karmic emerges from beta. There are updates every day 2X a day. Its still not ready to make a final driver installation.

Apart from having to boot in recovery mode and doing "dpkg-reconfigure psb-kernel-source" at a command prompt after every kernel update, I had no more problems with the Poulsbo drivers in Karmic alpha and betas. At least no more problems than in Jaunty...

---

### Post by ludwigbaum on 2009-10-14
Yesterday, I completed my installation of Karmic Beta with all the programms, I use normally. The installation of the opera10-deb-file crashed, leaving a system, that boots up to the ubuntu logo and stops there. That’s something, I have never seen with 7.04 – 9.04. I recommend to wait for the final version to all those, who need a working system.

---

### Post by nijaba on 2009-10-14
As of kernel 2.6.31-14, the dkms system seems to fail rebuilding the psb module...

Requires reinstalling the packages from alberto milone from scratch.  Why isn't DKMS doing this by default?

---

### Post by jbernardo on 2009-10-14
> **nijaba said:**
> As of kernel 2.6.31-14, the dkms system seems to fail rebuilding the psb module...

Requires reinstalling the packages from alberto milone from scratch.  Why isn't DKMS doing this by default?

Strange - All I had to do was to boot into a recovery mode, then chose a command prompt and ran "dpkg-reconfigure psb-kernel-source". Didn't have to reinstall anything. But I am using the latest psb-kernel-source, from lucazade's PPA.

---

### Post by emnaki on 2009-10-14
I am an owner of a sony P23G and this is the problem I am having. I am getting multicolored screen crash/corruption. This has occurred when I was using VESA and now that I am using Poulsbo. I have followed the instructions given so far and I believe I have solved the problem that this thread was aiming to solve. Now I have fast fps and things seem good except soon after I start ubuntu the screen goes multicolored and I cannot even switch terminal. I tried using Jaunty and the same problem occurs. What can I do to fix it or get an idea about what is wrong?

---

### Post by ludwigbaum on 2009-10-14
The Sony P23 has 1GB of memory (?). Which amount of memory (mem=???mb) did you write into "/etc/default/grub" (karmic) or "/boot/grub/menu.lst" (jaunty)?  Did you "update-grub"?

---

### Post by yannoo on 2009-10-14
Hi there,

I'm trying this out on an Asus EeePC T91 (Touch):

```
wget http://gma500re.altervista.org/scripts/poulsbo.sh && sh ./poulsbo.sh
```

And when I reboot (mem=800 and nohz=off OR not) in normal mode, I get only the terminal, with a rapidly flashing screen (I would have thought it was X trying the various configurations, but it never abandons and flashes too quickly).
Strange.

When getting back to recovery mode, everything is normal (well, I just get to the terminal, but I have no flashing effect).

The reason why I'm trying this out on the Eee PC is that it has a SCH Poulsbo card (following lspci).

To revert the change, I just did an apt-get remove psb-firmware psb-kernel-headers, and changed "psb" for "vesa" in /etc/X11/xorg.conf, then restarted.

Now honestly, this EeePC is really a pain in the *** to use with Karmic. It's just painfully slow. Firefox takes about 30 seconds to start, fresh.
I really hope this will improve drastically in what remains of the month of October. Fingers crossed. Go Go Ubuntu!

---

### Post by emnaki on 2009-10-14
> **ludwigbaum said:**
> The Sony P23 has 1GB of memory (?). Which amount of memory (mem=???mb) did you write into "/etc/default/grub" (karmic) or "/boot/grub/menu.lst" (jaunty)?  Did you "update-grub"?

You are correct, it has 1GB mem. I tried mem=1000mb, 900mb and 700mb. All which did not solve the problem of the multicolored screen crash. Yes I updated with update-grub.

---

### Post by michael37 on 2009-10-15
> **emnaki said:**
> You are correct, it has 1GB mem. I tried mem=1000mb, 900mb and 700mb. All which did not solve the problem of the multicolored screen crash. Yes I updated with update-grub.

Multicolored screen crash is VERY common on Poulsbo if you haven't configured your xorg.conf with MigrationHeuristic.  Read original post.

---

### Post by emnaki on 2009-10-15
I have already set MigrationHeuristic to greedy since I set this up with the below script recommended:

> 
2) PPA-based (UbuntuMobile & Milone):
Code:

wget [http://gma500re.altervista.org/scripts/poulsbo_ppa.sh](http://gma500re.altervista.org/scripts/poulsbo_ppa.sh) && sh ./poulsbo_ppa.sh


The multicolored screen crash occurs even so.

---

### Post by ludwigbaum on 2009-10-15
When I made a fresh installation yesterday, the automatic script paused for a long time, when loading down one of the authentication-keys and continued without it. The drivers did not work. Then I downloaded the keys manually (see page 1), before running the script. The installation performed successfully.

The flashing screen seems to indicate a bad grub-configuration or a bad xorg.conf . The drivers seem to work quite well. I found one bug: After a standby, the mouse-pointer disappears. After the start of a programm (by key-combination), the pointer reappears after some seconds.

As far as I know, apt-get remove of the psb-components should leave a corrupt grub-configuration (if grub expects the changed kernel) ?

---

### Post by yannoo on 2009-10-15
> **ludwigbaum said:**
> As far as I know, apt-get remove of the psb-components should leave a corrupt grub-configuration (if grub expects the changed kernel) ?

Right, I forgot that one but I followed the change with an apt-get update && apt-get dist-upgrade, which in fact proposed me to overwrite the menu.lst with the packager version and fixed it. Otherwise, I would probably have had a grub failure, indeed.

---

### Post by emnaki on 2009-10-16
It looks like I'll have to do a little experimentation myself with the xorg settings to see if I can get it to work without multicolored screen crashes, since the config given in this guide does not work for me. Perhaps its the difference between P11 and P25? Anyhows, where can I find more information about the xorg config options for Poulsbo? Is there a website which explains what all the options are and what they do? Also since my computer becomes totally unresponsive during the crash, is there any way I can find out (any logs for example) what the problem was that caused it to crash?

---

### Post by michael37 on 2009-10-17
> **lucazade said:**
> Simplified GMA-500/Poulsbo drivers installation:

Install Ubuntu, reboot into recovery mode and use one of the following script:

1) FTP-based (no ppa repositories):
```
wget http://gma500re.altervista.org/scripts/poulsbo.sh && sh ./poulsbo.sh
```

or

2) PPA-based (UbuntuMobile & Milone): 
```
wget http://gma500re.altervista.org/scripts/poulsbo_ppa.sh && sh ./poulsbo_ppa.sh
```

Let me know if ok.. I've tested them on a Acer AO751h. :)

@lucazade
All right, I tried this script on my Dell Mini 12.
Another clean reinstall of karmic lpia beta.

I went with the ppa version.

A few things that I didn't like and changed.

1. Got rid of force install of dkms and fakeroot 'cause they are already installed by my Broadcom wireless driver.  
2. Karmic apt puts ppa lists in /etc/apt/sources.list.d, so I used the new standard syntax. It also doesn't pollute your /etc/apt/sources.list
```

10,11c10,11
< echo "deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main" | sudo tee -a /etc/apt/sources.list
< echo "deb http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu jaunty main" | sudo tee -a /etc/apt/sources.list
---
> echo "deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main" | sudo tee /etc/apt/sources.list.d/ubuntu-mobile.list
> echo "deb http://ppa.launchpad.net/albertomilone/poulsbo-graphics/ubuntu jaunty main" | sudo tee -a /etc/apt/sources.list.d/ubuntu-mobile.list

```

Works quite well otherwise.

---

### Post by grege on 2009-10-26
> **lucazade said:**
> Simplified GMA-500/Poulsbo drivers installation:

Install Ubuntu, reboot into recovery mode and use one of the following script:

1) FTP-based (no ppa repositories):
```
wget http://gma500re.altervista.org/scripts/poulsbo.sh && sh ./poulsbo.sh
```

or

2) PPA-based (UbuntuMobile & Milone): 
```
wget http://gma500re.altervista.org/scripts/poulsbo_ppa.sh && sh ./poulsbo_ppa.sh
```

Let me know if ok.. I've tested them on a Acer AO751h. :)

PPA script worked well with my Dell Mini 12. FTP script did not work.

---

### Post by ewolff on 2009-10-26
First of all: Thanks a lot for your efforts - great help!
However, I tried the script with Ubuntu 9.10 Release Candidate and it fails on psb-kernel-source_4.41.2-0ubuntu1~910um1_all.deb IIRC. I did not dig deeper into this to be honest for the time being - anyone else having this issue?
There is another posting in this thread that says that since kernel 2.6.31-14 it doesn't work any more - that might be related.

---

### Post by Belatra on 2009-10-26
Finally I got it working on AspireOne AO751h ZA2 with fresh-installed UNR 9.10 RC.
First I installed the system from CD, then ran
sudo apt-get update
sudo apt-get upgrade

After that I downloaded your script and tried to run it.
It looked like everything was good but after rebooting I got flashing tty1 login prompt.
I found that not all packages have been installed by the script. I did not investigate why, finished installation manually and got at least 2D working.
Great thanks to **lukazade**

---

### Post by emnaki on 2009-10-27
Solved my problem, the multicolored screen crash was actually caused by the wireless. fixed the problem by replacing NM with WICD. Well finally a smooth running vaio p25g. Thank everyone who helped me. Also looks like this method does not work with the new kernel yet, so I guess I am sticking with beta for now.

---

### Post by ludwigbaum on 2009-10-27
My Vaio P11Z is running kernel 2.6.31-14 without problems. I think, that the automatic downloads made by the script don't work always. The script proceeds without the downloads.

---

### Post by lucazade on 2009-10-27
> **ludwigbaum said:**
> My Vaio P11Z is running kernel 2.6.31-14 without problems. I think, that the automatic downloads made by the script don't work always. The script proceeds without the downloads.

2.6.31-14 works for me, i'll see the scripts as soon as possible.

---

### Post by fiamazo on 2009-10-28
> **emnaki said:**
> Solved my problem, the multicolored screen crash was actually caused by the wireless. fixed the problem by replacing NM with WICD. Well finally a smooth running vaio p25g. Thank everyone who helped me. Also looks like this method does not work with the new kernel yet, so I guess I am sticking with beta for now.

I dunno how it happended, but this *exactly* solved also my problem (on 1101HA). Removing nm and installing wicd solved my issue of the screen going wild once in a while ... very often, indeed. Now, my system is rock-solid, even if I suspend and resume.

Spread the word! How did you solve it? And, what the hell has nm/wicd/wireless to do with X/screen/kernel?

Thanks,
Fiamzo

---

### Post by lucazade on 2009-10-28
Interesting post on moblinzone (owned by Intel) about GMA500:

[http://moblinzone.com/blog/743/10/64/Blaming_Intel_for_how_the_world_is](http://moblinzone.com/blog/743/10/64/Blaming_Intel_for_how_the_world_is)

---

### Post by lucazade on 2009-10-28
I've fixed the installation scripts (both ppa and ftp based)

Install Ubuntu, reboot into recovery mode and use one of the following script:


1) PPA-based (UbuntuMobile & Milone): 
Code:
wget [http://gma500re.altervista.org/scripts/poulsbo_ppa.sh](http://gma500re.altervista.org/scripts/poulsbo_ppa.sh) && sh ./poulsbo_ppa.sh

or

2) FTP-based (no ppa repositories):
Code:
wget [http://gma500re.altervista.org/scripts/poulsbo.sh](http://gma500re.altervista.org/scripts/poulsbo.sh) && sh ./poulsbo.sh


let me know if ok.
Luca

---

