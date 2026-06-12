---
title: "Bug: Updated xserver-xorg-video-intel to crash xorg"
date: 2013-03-23
forum: Installation &amp; Upgrades
---

### Post by linux_one on 2013-03-23
about Ubuntu 12.04, but possibly affecting more.
after some updates of middle of last week, xserver-xorg-video-intel frequently causes crash of xorg, such that keyboard doesnt work, only the mouse cursor can be moved around.  only solution is to hard reset.
the bug comes up mostly when browsing heavy web site (that perhaps use a lot of graphics acceleration)

upon login there is an error message about system graphics.
uninstalling xserver-xorg-video-intel solves the problem but removes 3d support.
I think its a very serious bug affecting many people.
related links;
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1158293](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1158293)
[http://ubuntuforums.org/showthread.php?t=2128051](http://ubuntuforums.org/showthread.php?t=2128051)

---

### Post by linux_one on 2013-03-24
temporary solution is to change back to previous kernels;

1) 3.2.0-39-generic: the current version for 12.04 is buggy
2) 3.2.0-38-generic: is also buggy
3) 3.2.0-37-generic: seems solves the bug

so perhaps something went wrong in 3.2.0-38-generic and later kernels.

---

### Post by Roadfighter on 2013-03-24
Same problem here, i have a intel i3 on a asus P8H67-M pro motherboard (no extra videocard) and when i log in i get the crash report instantly.
I did a fresh install of ubuntu 12.04 but how can i see which kernel i am using now in the terminal ?
And how do i set the 3.2.0-37 kernel ?

Emil

---

### Post by linux_one on 2013-03-24
in terminal type:
uname -a
tells you the kernel version.
when the computer start booting hold down the shift key, the grub menu will show up, so you can choose the previous versions of kernel.

---

### Post by cetoka on 2013-03-24
I have the same problem on Dell Optiplex 390.
[COLOR=#000000][FONT=verdana]Ubuntu 12.04 LTS[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Memory 7.7 GB[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Processor Intel core i3-2120CPU@3.30 GHZx4[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Graphics Intel Sandybridge desktop[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]OS Type 64 bit [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Disk 483.9 GB
I did not have any problems a week ago.[/FONT][/COLOR]

---

### Post by Roadfighter on 2013-03-24
After trying to boot with the shift key pressed... which doesn't work ? 
Maybe because i use a ssd ? (boots to fast ;)
i tried the uname -a command and i stil have the 3.2.0-39-generic kernel .
But i did a purge on xserver-xorg-video-intel. (sudo apt-get purge xserver-xorg-video-intel)
Then i did a update of the system with "precise-proposed" set on in the update tab under software sources.
After this i rebooted the system and all works fine now for at least 1 hour.
How can i stress the gpu of my system ? what programm does the most "damage", and of course without me sitting behind the desk :) 
Just want to put the gpu to work.

Emil

---

### Post by perob on 2013-03-24
Hi,

I had similar problems on ubuntu 12.10 64 bit using 3.5.0-26-generic linux kernel.

I just modified grub to allow me booting to previous kernel.
[http://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version](http://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version)

Currently no issues with 3.5.0-25-generic kernel.

Bye

---

### Post by jonnyboysmithy on 2013-03-24
> How can i stress the gpu of my system ? what programm does the most "damage", and of course without me sitting behind the desk :smile: 
Just want to put the gpu to work.If you want to test it run minecraft. When my brother plays that on the new kernel it locks up in within the hour but usually much less.
> Currently no issues with 3.5.0-25-generic kernel. 
With ubuntu 12.10 the 3.5.0-25-generic kernel still causes the same crash with me.
I had to go back all the way to 3.5.0-21.

---

### Post by linux_one on 2013-03-25
one idea can be to install the newest kernels and see if they have fixed the bug in them
use this guide, but only try if you know what you are doing;
[http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade](http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade)

I wonder if one install the latest kernel manually, will it break new updates? or what happens when even newer kernels become available? will they still show up automatically in update list?

---

### Post by jonnyboysmithy on 2013-03-25
You can download and install the kernel manually. Everything else works  like it normally does except that kernel you installed manually won't be  update because it wasn't installed from a repository (when update  manager checks the repository and sees a new version is avaliable it  will show it as an update. The kernel that is installed won't show up in  the repository and hence won't receive updates). I hope that clarifies  it :smile:

---

### Post by FeliceMente on 2013-03-25
> **jonnyboysmithy said:**
> If you want to test it run minecraft. When my brother plays that on the new kernel it locks up in within the hour but usually much less.
 
With ubuntu 12.10 the 3.5.0-25-generic kernel still causes the same crash with me.
I had to go back all the way to 3.5.0-21.

I have problems, on Ubuntu 12.10 x64, with 3.5.0-25-generic, too.

---

### Post by linux_one on 2013-03-26
its actually very terrible. what has happened to Ubuntu?
this kind of bug should not be allowed happen in LTS versions (like 12.04).
sometimes the kernel updates happen so frequently even several times a week, perhaps its a sign that the last release wasn't tested enough ....

---

### Post by krishna.988 on 2013-03-26
I have been affected by this bug:

[https://bugs.freedesktop.org/show_bug.cgi?id=25497](https://bugs.freedesktop.org/show_bug.cgi?id=25497)

Its been for 9 years in Linux and no one seems to be bothered

---

### Post by linux_one on 2013-03-26
@krishna.988
the purpose of my criticism is to help improve ubuntu and linux, but you seem to mention unrelated/useless bug here to shun linux, but please stick back to your MSTabletz and dont waste your time here;
[http://www.youtube.com/watch?v=N1zxDa3t0fg](http://www.youtube.com/watch?v=N1zxDa3t0fg)

---

### Post by krishna.988 on 2013-03-26
> **linux_one said:**
> @krishna.988
the purpose of my criticism is to help improve ubuntu and linux, but you seem to mention unrelated/useless bug here to shun linux, but please stick back to your MSTabletz and dont waste your time here;
[http://www.youtube.com/watch?v=N1zxDa3t0fg](http://www.youtube.com/watch?v=N1zxDa3t0fg)


If that is your thinking I can't help it..I'm not a fan of either Linux or Windows. for your kind information..I use what works for me..and I don't want to waste time..What is your whole idea of sharing the video :lolflag: which is irrelevant for this discussion..It seems pretty infantile..try changing your cerebrations..

---

### Post by dino99 on 2013-03-26
3.5 & 3.7 kernels are not that good; better to use 3.8 kernel now. You can get it by installing that ppa: ubuntu-x-swat/r-lts-backport (when the 3.8 kernel is installed, then deactivate that ppa and re-update again to avoid other problems with the extra packages)

---

### Post by jonnyboysmithy on 2013-03-27
@Dino99 could you please link to the page to the ppa for the 3.8 kernel, I'm not positive I've got the right one.

EDIT: I enabled the updates-proposed repository and installed a newer kernel (3.5.0-27-generic) from there.
Looking at the changelog there have been some changes to the i915 driver and other graphics related stuffs in this particular kernel.
&#822;S&#822;o&#822; &#822;f&#822;a&#822;r&#822; &#822;i&#822;t&#822; &#822;a&#822;l&#822;l&#822; &#822;s&#822;e&#822;e&#822;m&#822;s&#822; &#822;t&#822;o&#822; &#822;b&#822;e&#822; &#822;w&#822;o&#822;r&#822;k&#822;i&#822;n&#822;g&#822; &#822;f&#822;i&#822;n&#822;e&#822;,&#822; &#822;a&#822;l&#822;t&#822;h&#822;o&#822;u&#822;g&#822;h&#822; &#822;I&#822; &#822;p&#822;r&#822;o&#822;b&#822;a&#822;b&#822;l&#822;y&#822; &#822;s&#822;h&#822;o&#822;u&#822;l&#822;d&#822; &#822;h&#822;a&#822;n&#822;g&#822; &#822;o&#822;n&#822; &#822;a&#822; &#822;l&#822;i&#822;t&#822;t&#822;l&#822;e&#822; &#822;l&#822;o&#822;n&#822;g&#822;e&#822;r&#822; &#822;b&#822;e&#822;f&#822;o&#822;r&#822;e&#822; &#822;s&#822;a&#822;y&#822;i&#822;n&#822;g&#822; &#822;t&#822;h&#822;a&#822;t&#822; &#822;i&#822;t&#822; &#822;i&#822;s&#822; &#822;s&#822;t&#822;a&#822;b&#822;l&#822;e&#822; 
Not stable. Media doesn't mount properly. I'm going back to good ol 12.04 and staying there :twisted: :P

---

### Post by adoslyon on 2013-03-28
I'm very disapointed... for a LTS version !
I work with 12.04 LTS with Pentium G630 PC's and i think i'll re-install the 12.04 LTS without any kernel updates until this big bug will be corrected.

---

### Post by annnomius on 2013-03-30
like roadfighter, i also have a p8h67-m pro motherboard, and have run into the same problem with the recent update. i reinstalled 12.04 and found that the newer xserver-xorg-video-intel does not matter, only the newer kernels cause the crashing to occur. i tried both 64 and 32 bit installs and that also makes no difference. somthing changed in the kernel to cause these hangs.
::ann

---

### Post by skjha973 on 2013-04-01
I am using Ubuntu 12.04 3.5.0.26 kernel version and my display freezes almost every hour. Once it completely stopped working and I had to run previous kernel version 3.5.0.17 through grub menu. Thankfully that worked, otherwise I would be scratching my head completely on how to recover from this video driver crash. I am using Dell Inspiron laptop.

Please let me know any which way I can get rid of this problem. If you need any data or configuration details from my system, I can provide you immediately. Also, I am a newbie to Ubuntu having started using it for past 2-3 months only. So, any complicated steps, you should explain in little more detail. 

Thanks for your help

---

### Post by IanGrayland on 2013-04-02
> **skjha973 said:**
> Please let me know any which way I can get rid of this problem. 

keep running with your earlier kernel until a fix becomes available.

just to confirm, i am on 12.04.2 64 bit with intel i5 cpu and i915 graphics. all runs fine on kernels up to and including 3.5.0-25.39, after this up to 3.5.0-27.46 (current at time of writing) crashes and corruption occur.

easy way to test is to scroll through pages on this forum using firefox.

---

### Post by PshhPshh on 2013-04-02
Please, could anyone explain me, why having grub and the abilitie to rollback to an older kernel saves me from the ASTONISHING Important Security Updates ? Grub rolls back only kernel, not other features, right ?

I just intended to say that xserver-xorg-video-intel is not a part of a kernel, is it ?

---

### Post by IanGrayland on 2013-04-02
> **PshhPshh said:**
> Please, could anyone explain me, why having grub and the abilitie to rollback to an older kernel saves me from the ASTONISHING Important Security Updates ? Grub rolls back only kernel, not other features, right ?

I just intended to say that xserver-xorg-video-intel is not a part of a kernel, is it ?

The problem is in the updated kernel(s) NOT xserver-xorg-video-intel.

'far as I can remember, the kernel update (to 3.5.0-26) was in the 'Proposed' repo. If you're looking for stability, which with LTS you probably are, then you should un-check this repo in update manager. Still not an absolute guarantee, but it should help to keep things stable.

incidentally, this bug does not seem to affect all machines. I have an i3 (with integrated graphics) which seems to run the latest kernel without issues and several older core2 duo thinkpads with i965 graphics which are definitely ok.

---

### Post by linux_one on 2013-04-02
> **PshhPshh said:**
> Please, could anyone explain me, why having grub and the abilitie to rollback to an older kernel saves me from the ASTONISHING Important Security Updates ? Grub rolls back only kernel, not other features, right ?

I just intended to say that xserver-xorg-video-intel is not a part of a kernel, is it ?

no worries, grub doesn't roll back anything. when new kernel installed via updates, old versions still remain on your system. grub only allows you to start using older kernels. you will still loose any updates done to kernel after that older version when you start with them, but it doesn't affect any other program.

---

### Post by PshhPshh on 2013-04-02
The problem is with the kernel 3.2.0-39 too, not only 3.5.0 (I had time to test them all, lol)

I appologize for the incorrect word 'rollback', should have used 'start with' instead. But the question that I'm trying to ask looks like this:
after having troubles with some updates, we can start with an older kernel, but not the older packages. This time, as [**[COLOR=#000000]IanGrayland[/COLOR]**]("http://ubuntuforums.org/member.php?u=1597978") mentioned, the problem is with the KERNEL (I purged xserver-xorg-video-intel, lost 3d, but everything else seems to work fine, but nevermind). What if next time the problem will be with some PACKAGE, which crashes the system a millisecond after loading, leaving no chance to 1) detect it and 2) purge it ?

---

### Post by skjha973 on 2013-04-02
Thanks everyone. One question, how do I know that a fix for this problem has been released?

---

### Post by linux_one on 2013-04-02
@PshhPshh, firstly we havnt yet solve the current problem, using older kernels is not best thing to do. at least for long time :) then lets focus on this than  future imaginary problems. perhaps the hope is that such bugs doesnt normally happen.
@skjha973 I think there must have been enough bug report about this, lets hope some big guy in Ubuntu read this thread and update us whats going on!

---

### Post by stig on 2013-04-03
> **linux_one said:**
> ...lets hope some big guy in Ubuntu read this thread and update us whats going on!
Very true. I've now got the problem too and I'm disappointed because I've been using Ubuntu for about 6 years with no serious problems, never needed any help (even though I'm not a techie) and have often prompted others to give Ubuntu a try. My computer wouldn't upgrade to 12.04 successfully, it froze every time no matter which method I used to upgrade. As 10.04 security support is coming to an end I bought a new computer and installed 12.04 64-bit and guess what, it freezes quickly with exactly the same symptoms as described in posts above. A friend has his new computer installed from the same CD as mine but it works fine. They are both: Ubuntu Release 12.04 (precise) 64-bit, Kernel Linux 3.5.0-26-generic
My computer is: Asus Mainboard with Integrated Graphics, Intel I3 3.3 Ghz CPU, 8 GB Kingston RAM, 1000 GB Toshiba Hard drive

My onboard graphics is Intel B75 Express, his is Intel H77 Express, but he has a separate video card and I don't. We have different chips and motherboards. I can get stability by booting into grub and using the one other kernel listed which is 3.5.0-23. It's given a few freezes but nothing like the frequency on 3.5.0-26. My Windows friends who refused to change to Ubuntu are laughing! This problem is not good for the image of Linux and Ubuntu and it's going to particularly worry `ordinary' folk who don't have a techie background but would like to give Ubuntu a try. I have such a friend and he finally decided to try Ubuntu recently but "couldn't get it to work properly". I now realise he was probably hit by the same problem as I'm now suffering.

---

### Post by krishna.988 on 2013-04-04
> **linux_one said:**
> @PshhPshh, firstly we havnt yet solve the current problem, using older kernels is not best thing to do. at least for long time :) then lets focus on this than  future imaginary problems. perhaps the hope is that such bugs doesnt normally happen.
@skjha973 I think there must have been enough bug report about this, lets hope some big guy in Ubuntu read this thread and update us whats going on!


No canonical employees is going to read the thread. As the forum is managed and moderated by volunteers. If there is a bug then we should file a bug report..

---

### Post by stig on 2013-04-04
Reports have already been filed by others. On my PC when I got a message telling me to report an error I tried but it came up with a message saying something like "Pangolin development is complete and no reports will be used".

---

### Post by linux_one on 2013-04-04
maybe one reason this bug is so annoying is that Linux is usually too stable, I can count number times I had to hard reset before, and perhaps never before on 12.04!

---

### Post by FeliceMente on 2013-04-05
I installed this tool and updated Intel drivers: [http://www.webupd8.org/2013/04/intel-linux-graphics-installer-fixed.html](http://www.webupd8.org/2013/04/intel-linux-graphics-installer-fixed.html)

After restarting the system, my xorg configuration was broken (probably because I forced grub to load a pervious kernel version => .17 instead of .26).
I changed grub configuration for loading .26 kernel version again and, after restarting, the system seems to work without problems (but I've been using it for a hour about, maybe it's to early).

---

### Post by linux_one on 2013-04-06
I think installing third party of essential system things can be dangerous and make your system easier break by future updates, maybe its better for system drivers etc stick to Ubuntu updates

---

### Post by FeliceMente on 2013-04-06
Well, in this case the tool just adds a PPA and downloads update versions of the same stuff already present in Ubuntu (and, from what I read, the reason why this tool isn't available for Ubuntu 13.04 is because Ubuntu 13.04 already has lates Intel drivers).

---

### Post by linux_one on 2013-04-07
OK, then I have to say I dont get it why you need this tool to add a PPA, because it can be done by one command!

---

### Post by FeliceMente on 2013-04-07
Well, that's true.
I just found it convenient and, at the end, it worked and I no longer have the problems described in this thread. :-P

---

### Post by linux_one on 2013-04-08
kernel 3.2.0-40 has just released in updates :)
lets all try it and see it fixes the problem

---

### Post by Hans Gankema on 2013-04-09
Hello,

I skipped several kernel versions and this instability first occured here in 3.2.0-40 (sorry!!)

So .. could this be only an Intel driver related issue in combination with certain kernels.... now running 3.2.0-35 without a problem.... so far...

What is a reasonable stable ( or forgiving ) Intel driver version to start this combination search...

kind regards,
-Hans.

---

### Post by linux_one on 2013-04-09
that's not good news! lets see is more experiments done by others. 
we are not sure its only because of Intel drivers, it seems is a combination of the driver and newer kernels that causes this. because seems when you uninstall the driver then its OK even with latest kernels.

---

### Post by linux_one on 2013-04-09
this one seems related to this bug, they are apparently working on it.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716)

---

### Post by MAFoElffen on 2013-04-09
This started affecting people about a month ago. Heard it was bad code shared from Intel in the driver. Surprised more are not affected. 

On those affected- What happens if you you use newer Intel driver from XSwat or Edgers? Just curios, because my intel GPU test box doesn't have this problem so I can't replicate it.

---

### Post by linux_one on 2013-04-10
maybe it causes hang only on certain chip-set.
this is a way to restart softly when this hang happens, without the hard reset that can cause disk damage;
[COLOR=#028002][FONT=arial]www.[/FONT][/COLOR]**ubuntuguide.net/how-to-reboot-a-frozen-[B]ubuntu-the-safe-way**[/B]

---

### Post by linux_one on 2013-04-11
i tried latest released 3.2.0-40-generic its the same bug there.

---

### Post by manybodycpa on 2013-04-14
In case this is of use: 

On an X220 running 12.04, I had to go back all the way to 3.2.0-20-generic.
That kernel has now been running for three days without problems.

---

### Post by linux_one on 2013-04-14
I tried 3.2.0-43-generic in [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) not yet released (but will in soon future) on a friends laptop with Intel HD Graphics 3000, its worst, upon login the system **hangs instantly** with some characters change color. seems with every new release the problem gets worse!!!Also after few days ago updates (using old kernels still anyways) the laptop gets hot very quickly even if no CPU usage, perhaps GPU overload? I think this problem is going to stay for a while. If its from intel code, they are doing great job destabilizing linux!!! and really strange canonical doesnt test these codes on mainstream systems!

---

### Post by linux_one on 2013-04-15
i revert back the xserver-xorg-video-intel to the original version 2:2.17.0-1ubuntu4 now heating problem solved and works smoother. so was obviously GPU overload.
from [https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/](https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/)
something wrong with 2:2.17.0-1ubuntu4.3 and also the proposed 2:2.17.0-1ubuntu4.4

---

### Post by markbl on 2013-04-18
I updated my work 12.04 64 bit box yesterday and struck this terrible bug. Astonishing it has not been fixed. My quick fix yesterday was to add the xorg edgers ppa (which upgrades kernel to 3.5.*) and that worked. So for anybody wanting to do the same:
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get dist-upgrade
<then reboot>

```

Standard xorg edgers disclaimer applies, i.e. Read the notes at [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) before you add this.

---

### Post by FeliceMente on 2013-04-19
> **markbl said:**
> I updated my work 12.04 64 bit box yesterday and struck this terrible bug. Astonishing it has not been fixed. My quick fix yesterday was to add the xorg edgers ppa (which upgrades kernel to 3.5.*) and that worked.

I have this problem on Ubuntu 12.10 with 3.5.0-27-generic kernel, too.

---

### Post by manybodycpa on 2013-04-19
markbl, can you keep us posted about whether or not the bug is really gone after that update?
How many hours has your machine been running?

---

### Post by markbl on 2013-04-19
> **manybodycpa said:**
> markbl, can you keep us posted about whether or not the bug is really gone after that update?
Yes, I am certain that adding the xorg edgers ppa fixes this problem, at least on my machine.

That 12.04 64bit box is shared between 3 of us with individual accounts. I logged in early in the morning and found it had not been updated in a couple of months so I updated it, noticing a lot of updates including a new kernel, xorg, and graphics updates etc. After that I rebooted and then the box would only work for less that 60 secs or so. I use gnome-shell and it failed about 4 times very quickly. All the same - screen lockup but mouse could move. I rebooted and logged in to Unity but found same quick failure. My friend logged in as his account (Unity) and did the same. However, in the failed state, I found that I could ssh in to the box remotely and it seemed ok but with backtraces in the xorg log. There were even a couple of failures that occurred before I got to log in, i.e. at the lightdm login screen, i.e. even before any (gnome-shell or Unity) 3D UI is started. Given that the problem seemed xorg related, and that the box is fairly new with recent intel graphics, and I needed the box working quickly, I just added the xorg ppa from a remote shell, rebooted, and then used the box heavily without issue for the rest of the day.

---

### Post by FeliceMente on 2013-04-20
I just added the PPA to my Ubuntu 12.10 installation, and the kernel was updated from 3.5.0-27-generic to 3.7.0-7-generic. I'll test the system (it usually took no longer than 30 minutes for the first problem to appear...) and let you know if this fixed the issue.

---

### Post by FeliceMente on 2013-04-20
After adding the PPA on Ubuntu 12.10 I no longer had problems of any kind!

The integrated graphic adapter is even working better than before (I had crashes with the 64 bit version of Houdini Apprentice (a program that only actually support high end graphic cards) every time I added an object to the scene or switched to two or more views, while the 32 bit version crashed as soon as I switched to four views, while now the 64 bit version only has some occasional crashes and the 32 bit version never crashed, even with many objects in the scene and when continuusly switching between 1/2/4 views modes...).

---

### Post by linux_one on 2013-04-20
I also added ppa: xorg-edgers/ppa, it broke my system software dependencies terribly, although seem to fix the problem of GPU crash, I had to work out hard how to remove the PPA and restore the system.
I think safest thing is to use an older 3.2.* kernel at the moment. For LTS the kernel 3.5.* are actually much older than the recent 3.2*, you can check for yourself by their built date in [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by FeliceMente on 2013-04-20
What version of Ubuntu are you using?

Anyway, wasn't the suggested "sudo ppa-purge xorg-edgers" able to restore the system?

---

### Post by linux_one on 2013-04-20
I tested this on 12.04 LTS, and no, [COLOR=#000000]ppa-purge[/COLOR] couldn't do it! maybe its more to do with the software you have already installed than Ubuntu version.
this bug sounds more like a code testing on behalf of Canonical or Intel for their graphics driver, perhaps started around middle March, but at any case doing it on LTS version might damage Ubuntu popularity and reputation with those who use it for anything more than hobby. At least now everybody would think twice before updating their system!

---

### Post by PshhPshh on 2013-04-22
> **linux_one said:**
> i revert back the xserver-xorg-video-intel to the original version 2:2.17.0-1ubuntu4 now heating problem solved and works smoother. so was obviously GPU overload.
from [https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/](https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/)
something wrong with 2:2.17.0-1ubuntu4.3 and also the proposed 2:2.17.0-1ubuntu4.4

Hey, I tried to do the same (thx for sharing the link to the older packages btw), and the results were adorable :) I simply logged in, then watched my clock dissapearing for 4 seconds and appearing back for 1 for some minutes, then the system froze. Like a good old ice time bomb :) 

Also, I'm 99% sure, that my system is cracked, because I'm too lame and haven't learnt how to 1) monitor and log hakers scanning me 2) block outgoing traffic 3) detect fishy processes running. So, there's a little possibilitie, that somebody wants to compromyse intel/ubuntu.

---

### Post by FeliceMente on 2013-04-26
I upgraded to 13.04 (I don't know it this was needed, but first performend a ppa-purge on xorg-edgers, and then upgraded), and everything seems to work perfectly, with no video problems.

---

### Post by annnomius on 2013-04-29
there is a test kernel posted in the bug that linux_one referenced:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716)
check comment #177--i tried the precise test kernel and this made the bad crashing go away! so it looks like the ubuntu devs are finally getting closer to fixing this.
unfortunately, it is taking a frustratingly long time to fix such a bad regression on a "long term support" release.

13.04 also appears to be stable.

::ann

---

### Post by FeliceMente on 2013-04-29
> **annnomius said:**
> 
13.04 also appears to be stable.
::ann

After some days of heavy use, I can confirm this: 13.04 doesn't have this problem.

---

### Post by DWade on 2013-04-29
For those of you who do not know how to pick the kernel you want, down load and install grub customizer
using these commands, in a terminal.

        sudo add-apt-repository ppa:danielrichter2007/grub-customizer
        sudo apt-get update
        sudo apt-get install grub-customizer

when you open it click on predefined and change the entry from 1 to the kernel you want.

---

### Post by manybodycpa on 2013-05-25
Have there been any more developments? I noticed there have been several new kernel version recently. Is the problem solved?

---

### Post by FeliceMente on 2013-05-25
I haven't had any problems after upgrading to Ubuntu 13.04. I don't know if the problem was solved on 12.04 and 12.10.

---

### Post by Roadfighter on 2013-05-27
Also running on 13.04 and no problems so far.
I purged the intel driver and it did work for me on 12.04, i didn have hi res anymore and problems playing youtube on 1080i.
Now on 13.04 no more problems.(so far :)

---

### Post by manybodycpa on 2013-05-27
Thanks. Is anyone running a stable 12.04?

---

