---
title: "Word of warning: 11.10, NVidia driver, TROUBLE."
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by ladasky on 2012-04-17
I'm not sure where the right place is to post this warning, but this seems close.

_My system's specifications:_
Gigabyte MA-GM78-US2H motherboard, vintage 2009.
AMD 1090T CPU.
NVidia GeForce 8800 GTS video card, vintage 2006. 
Oneiric 64-bit.

I had a system crash, and I went to do a re-install.  As I have always done, I enabled the NVidia proprietary video driver.  Under System Settings > Hardware> Additional Drivers, I clicked on the "NVidia accelerated graphics driver (version current) [recommended]" button.

_The symptoms:_
After logging in, there was almost complete loss of system control.  The cursor would freeze for 30 seconds at a time.  Only the first mouse click or two would actually work immediately.  I tried to open a terminal window and didn't get one until three or four minutes later.  My hard drive was running constantly.  Occasionally I would see a few random black bars flicker across my screen, which is what clued me in to the fact that the video driver might be my problem.

_The fix:_
Booting into a rescue shell from the alternate install CD, and executing **sudo apt-get remove nvidia-current nvidia-settings** repaired my installation.

Conclusion: whatever the "current" driver is in the Ubuntu repository, it can cause BIG trouble with at least some hardware configurations.  Proceed with caution!

---

### Post by bogan on 2012-04-18
Hi!, **ALL**,

+1 to that [COLOR=Red]WARNING[/COLOR].

It also applies to some other nvidia driver versions. 295.33 seems to be OK.

 See:
[http://phoronix.co]("http://phoronix.com/scan.php?page=news_item&px=MTA4ODc")[/scan.php?page=news_item&px=MTA4ODc]("http://phoronix.com/scan.php?page=news_item&px=MTA4ODc")

[COLOR=Red]Watch Out!![/COLOR]

EDIT:
 Although the Nvidia downloads>Search shows 295.40 to be the latest recommended version, ```
sudo nvidia-installer -latest
``` shows 295.33 as the latest, and that is what```
 sudo nvidia-installer -f 
```will install, as well as un-installing any previous installations.

Chao!, bogan

---

### Post by ladasky on 2012-04-18
Thanks for your reply, bogan.

I was going to follow up and ask how to check what driver version would be installed by Ubuntu if the "current, recommended" driver was chosen.  You answered my question before I even asked it.

---

### Post by creolecat on 2012-04-18
I'm having a similar problem with Ubuntu 11.10. My system is dead in the water! I took the 3.0.0.18 kernel updates and my system crashed with the "busybox v1.13.3 initramfs" error and has been inaccessible ever since.   

My system's specifications (something close to this):
ASUS A8N-SLI motherboard.
AMD Athlon 64 4000+ CPU.
NVidia GeForce 7800GTX video card. 
Oneiric 64-bit.

The symptoms:

Grub screen comes up (dual-boot, dual disks Win7), select Ubuntu, but system would not load. I tried to repair using live CD. Tried to do a complete re-install, several times. It goes for a while but locks up during the "loading system" portion of the installation. I have tried a different hard drive, changed some cables. I tried to load Ubuntu and Mint, still just locks up.
I have done memory tests, md5 verification with no errors. Now I have corrupted Grub and am not able to boot to any system. 

The fix:
None yet

Conclusion: If someone has some suggestions, please post.

---

### Post by MonkeyPaw on 2012-04-18
I'm running quite similar hardware (880G, Phenom X4, 8800GTS 512mb), but I'm on 12.04LTS beta2.  I've been running the recommended driver, 295.40, and it has been stable so far. That's even after several trips to S3 and back.

---

### Post by bogan on 2012-04-19
Hi!, **ladasky**,
You Posted:>  I was going to follow up and ask how to check what driver version would  be installed by Ubuntu if the "current, recommended" driver was chosen.   You answered my question before I even asked it.     Please note that the "current, recommended" nvidia driver in 'Additional Hardware' is unfortunately not identified by version, and is almost certainly different from that shown by the Nvidia/downloads 'Search' function, and also from that given by 'sudo nvidia-installer -f'  # or -latest.

On my 11.10 installation with 295.33 installed and in use, Synaptic Package Manager does not show it as available or installed, and shows nvidia-current as v280.13!!

I do not know how the version number of the 'Additional Hardware' "current, recommended" version can be checked, except by someone who has installed it.

The best way to be sure what version is actually installed apart from  'sudo nvidia-installer -latest' is to run: ```
cat /sys/module/nvidia/version
```@monkeypaw, sure, you are one of the lucky ones, Nvidia's own blog says that the symptoms reported from this 'bug' vary widely from nothing to a complete wipeout, and are unpredictable.

Chao!, **bogan**.

---

### Post by thermobaric on 2012-04-19
Thank you so much for posting this. I resurrected my 2006 gaming rig for my kids so I could run edubuntu. While it behaved itself quite well when running from the livecd. I had the same exact loss of control, and also have an 8800 GTS. You've saved me a few headaches, and lots of time finding a solution. Hopefully a few minutes with ssh will cure it!


Roswell

---

### Post by ladasky on 2012-04-19
You're welcome, thermobaric.

I'm glad that I'm starting to know my way around Linux well enough to offer something back to this community.  I have learned so much from the people here.

---

### Post by MonkeyPaw on 2012-04-19
> **bogan said:**
> @monkeypaw, sure, you are one of the lucky ones, Nvidia's own blog says that the symptoms reported from this 'bug' vary widely from nothing to a complete wipeout, and are unpredictable.


Quite odd indeed. The funny thing is, I paid next to nothing for the card on eBay. It's still running like a champ, which is nice considering I've had bad luck in the past with nVidia. 

Do you think some of my good fortune could be because I'm running 12.04 and not 11.10? Maybe there's some extra polish in there. :confused:

---

### Post by ladasky on 2012-04-19
> **bogan said:**
> @monkeypaw, sure, you are one of the lucky ones, Nvidia's own blog says that the symptoms reported from this 'bug' vary widely from nothing to a complete wipeout, and are unpredictable.

Huh.  The problem can spread that widely?  Now I have to wonder whether the video driver bug precipitated _[my irreversible loss of a dual-boot RAID1 Oneiric/Vista setup]("http://ubuntuforums.org/showthread.php?t=1960251")_.  First my video driver crashed, and on the next reboot my RAID crashed.  I simply could not get my motherboard to rebuild a RAID1, with two hard drives that I knew were good, even starting completely clean.

Thank goodness I had backups.

Perhaps I abandoned rebuilding the dual-boot system before I found the problem, but... I decided to switch over to a virtual-machine approach, running Vista as a guest OS in VirtualBox under Oneiric.  I'm almost done making everything work the way that I want.  And now, I don't have two operating systems fighting to manage the RAID, I just let Linux do it.

---

### Post by 23dornot23d on 2012-04-19
That's interesting .... 

After helping a user with the Nvidia 8500 GT card ...... the 295.33 was the only one
that seemed to work ok and was getting total freeze ups with others ....

Even with the 285.33 set up it was later reporting segfaults .... 

The thread is here if anyone is interested ..... we went as far as we could with it
and then the User swapped to another card ..... as I could not see how to resolve the
issue .....

[[COLOR=Blue]_**295.33 reports back all is fine**_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11832511&postcount=26")

[[COLOR=Blue]**segfaults are shown on the log **[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11854119&postcount=48").... for the 17th ..... the user had tried both drivers
but would boot with a black screen and freeze with the 295.40 installed .... 

So with the 295.40 there may be an issue with some of the Nvidia Cards ......

The User is now using a different graphics card a Asus 4670 - we have yet to conclude this though ....... will see tomorrow if there is still a fault ..... as I was under the impression it could be a hardware fault ....

If someone more experienced understands the segfault given maybe they can help
work out what happened there ......

---

### Post by bogan on 2012-04-20
**MonkeyPaw** Posted:  > Do you think some of my good fortune could be because I'm running 12.04  and not 11.10? Maybe there's some extra polish in there. In the ['Ubuntu +1 (Precise Pangolin)']("http://ubuntuforums.org/forumdisplay.php?f=412") Forum there are even more reports of nvidia driver update problems:"**Re: 12.04 -- April 14/15 Updates Nvidia Regression"**[http://ubuntuforums.org/showthread.php?t=1959416](http://ubuntuforums.org/showthread.php?t=1959416)

Chao!,** bogan.**

---

### Post by creolecat on 2012-04-20
Guys,

Thanks for all of your hard work and suggestions, but I am throwing in the towel. I have been running Ubuntu for a couple of years with almost no issues, until this Nvidia driver issue. I cannot seem to get past it this time. I have lost files that I considered to be secure and my system has been down for almost a month. I think Linux needs to get it together with these driver issues and my opinion about a major upgrade every 6 months is that is too often. Getting ready to remove Linux hard drive, repair my MBR on Win7 and use my computer again. I may have a second look at Linux in the future, but for now SEE YA!

creolecat

---

### Post by Pablo Pablovski on 2012-04-20
I've had trouble the Nvidia driver on my ubuntu 11.04 qnd kubuntu 11.10 installs on the same system. Nvidia 8800GTS (640MB version). Like others, nothing worked properly / repeatably, until I installed the 295.33 drivers, when stability returned on both installs.

Interestingly, I found that I was able to upgrade the Nvidia driver to the "current release with updates" version offered by Jockey under KDE. Once completed, all was well. The Nvidia Server Settings GUI reported that the operational version was 295.**20** - but "nvidia-installer -latest" reported 295.33. 

Go, as they say in the US, figure.

---

### Post by bogan on 2012-04-20
Hi!, **Pablo,**
You Posted: The Nvidia Server Settings GUI reported that the operational version was 295.**20** - but "nvidia-installer -latest" reported 295.33. Checkout the entry under: "Open GL/GLX Information">"Open GL Information".

Mine shows: version 4.2.0 NVIDIA 295.33.
   If it insists on different versions - beware!
There may be remnants of previous installations, and that can lead to all sorts of horrors, especially if there are modules that were assembled with the wrong kernal header version.

Did you uninstall and purge the previous nvidia-* installs ??

As Posted above:
```
cat /sys/module/nvidia/version
``` will tell you which version is installed; there is also in that folder a comprehensive Nvidia ReadMe - not to frighten you, but here is an extract:>  please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not existChao!, **bogan.**

---

### Post by Pablo Pablovski on 2012-04-20
Thanks, @bogan.

295.20 is confirmed.

```
Version    3.3.0 NVIDIA 295.20
```

and

```
pablo@kubuntu-64:~/Documents$ cat /sys/module/nvidia/version
295.20
```

I purged the 295.40 version, and installed 295.33 using the .run file from nvidia.com. That was working fine, so I thought I'd try the "updates" verison offered by Jockey - which, it turns out, is 295.20. Dunno whether Jockey purges the current version but I assume it runs the normal DKMS update to create a suitable kernel module.



295.20 is working without evidence performance regresssion, over several hours and a couple of planned restarts.

---

### Post by ladasky on 2012-04-20
> **creolecat said:**
> Guys,

Thanks for all of your hard work and suggestions, but I am throwing in the towel. I have been running Ubuntu for a couple of years with almost no issues, until this Nvidia driver issue. I cannot seem to get past it this time. I have lost files that I considered to be secure and my system has been down for almost a month. I think Linux needs to get it together with these driver issues and my opinion about a major upgrade every 6 months is that is too often. Getting ready to remove Linux hard drive, repair my MBR on Win7 and use my computer again. I may have a second look at Linux in the future, but for now SEE YA!

creolecat

Just run without the NVidia driver for now!  As long as you don't need super high performance, you'll be fine.

(For the record, I DO need high-performance video for 3D rendering of protein models -- but all of my tools are Linux-based, and I'm not changing that any time soon.)

---

### Post by ladasky on 2012-04-20
Update from Yours Truly: OLDER Nvidia drivers also appear to be causing trouble.

Just a reminder, here is my configuration:

Gigabyte MA-GM78-US2H motherboard.
AMD 1090T x6 CPU.
NVidia GeForce 8800 GTS video card. 
Oneiric 64-bit.

I tried the "current" driver, and reported on the near-catastrophe that resulted in the original post of this thread.

The **nvidia-173-updates** driver ALSO causes serious GUI lags on my system, though it wasn't quite as bad as it was using a 295-series driver.  I was actually able to open Synaptic and uninstall the driver from there.

Thinking that the "updates" part of the 173 driver might include the problematic security fix that NVidia is reporting to the public, I also tried **nvidia-173** (without the updates).  Unfortunately, this too caused major lags.  Again, it wasn't a total meltdown, but the GUI was very sluggish.

The 96-series drivers are also offered, but I'm not going to check them.  Not today, anyway, I have other work that must be completed.

Conclusion: some other update that I recently downloaded is interacting negatively with SEVERAL NVidia drivers, new and old.

If there is a better place to report these bugs, would someone please chime in and let us know?  Thanks.

---

### Post by 23dornot23d on 2012-04-20
> If there is a better place to report these bugs, would someone please chime in and let us know?  Thanks.

Launchpad is the place to report problems ..... login with your id from here create a password and input the bugs .... search first as often its just a case of adding to one
that is already open ..... 

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/737755](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/737755)

The launchpad start page
[https://launchpad.net/](https://launchpad.net/)


> 
Do you think some of my good fortune could be because I'm running 12.04   and not 11.10? Maybe there's some extra polish in there. 
Finding with the latest version 12.04 my graphics are slower but on all my computers work well .....
They do not use the Proprietary drivers now though ...... that is probably why the 12.04
seems to be better ......

Looking forward to the new release .... hope it solves some of the issues we have seen here too ....

---

### Post by jerome1232 on 2012-04-20
> **creolecat said:**
> Guys,

Thanks for all of your hard work and suggestions, but I am throwing in the towel. I have been running Ubuntu for a couple of years with almost no issues, until this Nvidia driver issue. I cannot seem to get past it this time. I have lost files that I considered to be secure and my system has been down for almost a month. I think Linux needs to get it together with these driver issues and my opinion about a major upgrade every 6 months is that is too often. Getting ready to remove Linux hard drive, repair my MBR on Win7 and use my computer again. I may have a second look at Linux in the future, but for now SEE YA!

creolecat

Interesting, you are having problem with drivers built by NVIDIA and you somehow blame the linux community for NVIDIA's driver failing.

If you were running Windows and then when you installed a new driver from NVIDIA and it crippled your system, would you blame Microsoft... or NVIDIA?

---

### Post by MonkeyPaw on 2012-04-20
> **jerome1232 said:**
> Interesting, you are having problem with drivers built by NVIDIA and you somehow blame the linux community for NVIDIA's driver failing.

If you were running Windows and then when you installed a new driver from NVIDIA and it crippled your system, would you blame Microsoft... or NVIDIA?

Funny you mention it. When Vista was getting royally trashed by virtually everyone, it was later determined that nVidia's poor drivers were responsible for the highest percentage of reported  crashes. 

[http://arstechnica.com/hardware/news/2008/03/vista-capable-lawsuit-paints-picture-of-buggy-nvidia-drivers.ars](http://arstechnica.com/hardware/news/2008/03/vista-capable-lawsuit-paints-picture-of-buggy-nvidia-drivers.ars)

Simply put, nVidia dropped the ball, as MS gave plenty of notice regarding driver model changes. One of the many reasons Windows 7 is such a hit is because the graphics driver model didn't change much from Vista and drivers caught up. Quality support resulted in higher OS stability, which resulted in happy customers. Windows 8 stands to undo that happiness, IMO, but that's OT.

Go over to OS X, and it's actually Apple that cuts off Mac models for future OS updates. Some of that is simple firmware updates and driver support, but Apple is quick to abandon the old and move on.

Linux tries to soldier on, but the community can only fix so much since AMD and nVidia don't want to open source their code. I suppose we should be glad there are proprietary drivers at all?

---

### Post by ladasky on 2012-04-20
> **MonkeyPaw said:**
> Funny you mention it. When Vista was getting royally trashed by virtually everyone, it was later determined that nVidia's poor drivers were responsible for the highest percentage of reported crashes.

A shame, really.  I can't live without CUDA, so it's NVidia for me.  But since a large portion of the science software development community (i.e., CUDA users) works on Linux, I think that NVidia would be more diligent in keeping their Linux drivers functional.

---

### Post by Pablo Pablovski on 2012-05-03
**295.49** driver for Nvidia released.

[http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html)

---

### Post by bogan on 2012-05-03
Hi!, **All**.
> ****Pablo Pablovski** said:**
> **  295.49** driver for Nvidia released.

[http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html) I have installed it and it runs with no obvious problems with a GeForce 7650 card.

Edit; Fri May 4th. noon: I have also run it on a GTS 520 and it is OK there too.```
nvidia-installer --latest
``` now returns: v295.49 and ```
nvidia-installer -f
``` will install 295.49 after un-installing the previous version.

Note: Pablo's Link above is for the 64bit version, check you get the coorrect one!

Chao, **bogan**.

---

### Post by jerome1232 on 2012-05-03
Any knowledge of if this update is going to make it into the backports or proposed repos?

Having users turn to that binary driver will be a poor solution due to the hassle involved with installing it.

---

### Post by markbl on 2012-05-04
> **Pablo Pablovski said:**
> **295.49** driver for Nvidia released.

[http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html)

Has been an epic fail for me. See [http://ubuntuforums.org/showpost.php?p=11904367&postcount=8](http://ubuntuforums.org/showpost.php?p=11904367&postcount=8)

---

### Post by mips on 2012-05-04
> **jerome1232 said:**
> Any knowledge of if this update is going to make it into the backports or proposed repos?


I can only speculate but it will probably appear in the x-swat ppa at some stage.

---

### Post by bogan on 2012-05-17
Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.53 available [/COLOR]from nvidia downloads.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux...driver-uk.html]("http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html")

[COLOR=RoyalBlue]**Edit: Updated Thursday May 17th; **[/COLOR]     

      	Code:
 	nvidia-installer --latest 
 now returns: v295.53 and the currently installed version, without altering anything.
     

      	Code:
 	nvidia-installer -f 
 will install 295.53 after un-installing the previous version.

NVNews says of version 295.53:
QUOTE:
**Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**,
 [GeForce4]("http://viglink.pgpartner.com/rd.php?r=10313&m=878281881&q=o&priceret=87.73&pg=%7E%7E3&k=2b6229593608c3c1fb499d0ca9880634&source=feed&url=http%3A%2F%2Fmicropartsusa%2Ecom%2F31p6953%2Dibm%2Dnvidia%2Dgeforce4%2Dmx440%2D64mb%2Dagp8x%2Datx%2Dgraphics%2Dcard%2Dw%2Do%2Dcable%2Dnew%2Dbulk%2Din%2Dstock%2Ehtml&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E") and older GPUs are supported through the **96.43.xx** and **71.86.xx** [NVIDIA]("http://www.nvidia.com/") legacy graphics drivers.
 GeForce FX GPUs are supported through the **173.14.xx** NVIDIA legacy graphics drivers.

[B]
bogan.[/B]

---

### Post by Cavsfan on 2012-05-17
Or if you prefer the CLI method, here is the link:

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1948062_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1948062")

There is a link to download the latest driver 295.53 released yesterday.
There is another with instructions on how to install it.
Then there is a third link from a How to in this forum to create a script that will install the driver into any new kernel that gets installed.

I upgraded it myself this morning with no problems. It been proven to work on 10.04 12.04 and anything in between.

---

### Post by anson123 on 2012-06-17
just to add in what i have experienced....i have been using ubuntu since around version 6 and have had pretty good experiences up until version 11.10.  i am kinda stuck at version 11.04 now.  i also have a similar video card, the 9800M GTS and it seems like version 11.04 is the last ubuntu i can use with the proprietary nvidia drivers.  i have tried both 11.10 and 12.04 and they work find without installing the nvidia drivers, but once insalled, the driver seems to lock up my system about 1-2 minutes after the desktop appears.  This happens with both unity and kde desktops.  while i don't absolutely need to use the nvidia drivers, i like to play diablo 3 and other video games now and then.  honestly i am not sure if the problem is with the nvidia driver or how ubuntu handles it in versions 11.10 and 12.04.

---

### Post by Cavsfan on 2012-06-17
> **anson123 said:**
> just to add in what i have experienced....i have been using ubuntu since around version 6 and have had pretty good experiences up until version 11.10.  i am kinda stuck at version 11.04 now.  i also have a similar video card, the 9800M GTS and it seems like version 11.04 is the last ubuntu i can use with the proprietary nvidia drivers.  i have tried both 11.10 and 12.04 and they work find without installing the nvidia drivers, but once insalled, the driver seems to lock up my system about 1-2 minutes after the desktop appears.  This happens with both unity and kde desktops.  while i don't absolutely need to use the nvidia drivers, i like to play diablo 3 and other video games now and then.  honestly i am not sure if the problem is with the nvidia driver or how ubuntu handles it in versions 11.10 and 12.04.

I agree. I know that the latest version of the driver can be installed with Lucid Lynx 10.04 via the commands in that previous post.
But, I have no experience with any other versions. I decided to only use LTS versions and have 12.04 installed on a partition but,
I am not going to even attempt installing the latest driver until I have backed it up and then I'll see what happens.
As for the versions in between 10.04 and 12.04 I have no knowledge what so ever.
So, thanks for the update.

---

