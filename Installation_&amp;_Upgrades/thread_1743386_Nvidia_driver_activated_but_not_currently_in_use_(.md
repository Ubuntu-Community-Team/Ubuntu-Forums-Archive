---
title: "Nvidia driver activated but not currently in use (11.04)"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2011-04-29
> Re: Nvidia driver activated but not currently in use ??
Jockey (Ubuntu's restricted driver manager) doesn't yet support the new alternatives system used by the nvidia driver packages, so in order to install nvidia drivers you will have to install them from the command line:

    sudo apt-get install nvidia-current (or nvidia-173 or nvidia-96)
    select the alternative that matches the driver that you have installed
        (e.g. /usr/lib/nvidia-current/ld.so.conf for nvidia-current):
        sudo update-alternatives --config gl_conf
    update the ld cache:
        sudo ldconfig
    then configure your xorg.conf with:
        sudo nvidia-xconfig
    And restart your computer.


I have followed the above advice, but I think using xorg.conf is out of date. **What should I do instead to activate the nvidia driver?**

---

### Post by Robbyx on 2011-04-29
Having followed the above advice I now find that upon rebooting Ubuntu freezes at the first Ubuntu screen. The mouse stops working as does the keyboard. 

I am using the live CD to post this because I can not get into Ubuntu. I have had something like this happen every time I reboot into Ubuntu after a repair install. It works on the repair and then if I reboot I can not get into Ubuntu.

I am using a nvidia card.

What should I do?

---

### Post by cml21 on 2011-04-29
Sorry that I'm not able to help with a response, but if you do figure it out, please post the solution.  I'm in the same boat as you.

P.S.  If it helps you get running, I started my machine to a terminal and deleted xorg.conf.  Then I could restart into X.  (I still can't get the driver to work, but at least I can scour this site for advice!)   :)

---

### Post by mörgæs on 2011-04-29
Are closed-source drivers necessary at all? How does the machine work with open-source?

Nvidia sometimes needs boot options. Have you tried this?

---

### Post by Robbyx on 2011-04-29
I have found that I can not make the nvidia driver remain activated in the hardware drivers. I pressed F8 on reboot and chose to start with low graphics. I could then proceed to login to Ubuntu.


The reason why I want to use the prop driver instead of the open source is because the open source does not adjust for a wide screen. Everything is stretched. Nvidia's driver does not stretch the contents.

---

### Post by spikoley on 2011-04-30
There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207") on this issue.  Add your details to the bug report, so it will get fixed sooner.

It looks like this issue is caused by jockey (Additional Drivers).

---

### Post by dino99 on 2011-04-30
boot in recovery mode ("shift" key down at bios end process to get grub menu)
open synaptic then: remove/purge ALL the nvidia related packages
then reinstall: nvidia-current, nvidia-common, nvidia-settings

reboot

---

### Post by eentonig on 2011-04-30
Switching from the current (recommended) drivers to the previous 173 version solved the issue for me. You can use 'additional drivers' to do that.

---

### Post by ebbr.bugs on 2011-04-30
Solution here: [http://ubuntuforums.org/showpost.php?p=10742896&postcount=4](http://ubuntuforums.org/showpost.php?p=10742896&postcount=4)

---

### Post by Robbyx on 2011-04-30
I am no longer so sure that I do need the proprietary Nvidia driver for the wide screen. I have just changed the ratio in the monitor setup and have found the stretching effect has disappeared.

Are there any other reasons why I should use Nvidia's driver?

---

### Post by Robbyx on 2011-04-30
I have followed the advice above and have not found the solutions to fully work. 

The nvidia driver is still not in use although it is active.

I can not create any panels, including the one that shows what programs are open. Right click on the edge of the screen does not give the option to create a panel.

---

### Post by derekkrebs on 2011-04-30
> **ebbr.bugs said:**
> Solution here: [http://ubuntuforums.org/showpost.php?p=10742896&postcount=4](http://ubuntuforums.org/showpost.php?p=10742896&postcount=4)

Does not work.

> **eentonig said:**
> Switching from the current (recommended)  drivers to the previous 173 version solved the issue for me. You can use  'additional drivers' to do that.

How do you use 'additional drivers' to do this?  I'm not seeing any more options other than the current version.  Also I do not understand how the current drivers can be "Tested by the Ubuntu developer."  As I am having this problem on 2 Nvidia powered machines.  One is with a GTX 460, and the other is an integrated GeForce 8400.

> **dino99 said:**
> boot in recovery mode ("shift" key down at bios end process to get grub menu)
 open synaptic then: remove/purge ALL the nvidia related packages
 then reinstall: nvidia-current, nvidia-common, nvidia-settings
 
 reboot

This doesn't work either.

---

### Post by spikoley on 2011-05-01
Neither solution worked for me too.

---

### Post by OlorinIWas on 2011-05-01
was gonna let u know, I got around this by chowning my xorg.conf to user and using nvidia-settings to setup and save conf...nvidia-settings would not run as root.

---

### Post by Topazgb on 2011-05-01
> **Robbyx said:**
> ....I have just changed the ratio in the monitor setup and have found the stretching effect has disappeared.

Are there any other reasons why I should use Nvidia's driver?
'Nvidia driver activated but not currently in use' shows on my PC, but the monitor setup has the correct settings.  The only problem I encounter is the occasional blank screen. If Filezilla is open and I try to edit a file in Bluefish then Bluefish  has a blank(white) screen under it's menu.  Same if I try to open  Thunderbird.

Have placed bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773799](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773799) but so far it has not been assigned.  Not sure if this is a driver issue or something else.  But for now I am not too bothered about the drivers.

If it works don't fix it.  It's working (except for the occasional blank screen) so perhaps not fix it until it gets sorted with an update ?

---

### Post by derekkrebs on 2011-05-01
> **OlorinIWas said:**
> was gonna let u know, I got around this by chowning my xorg.conf to user and using nvidia-settings to setup and save conf...nvidia-settings would not run as root.

Could you explain this in more detail?  I ran nvidia-settings after a terminal install of nvidia-current and still have this problem.

---

### Post by Tom_AUT on 2011-05-02
I'm having the same problem with a GeForce 9500 GS. I've switched to Ubuntu Classic (don't like the Unity stuff), and I'm really missing the desktop effects, e.g. pulling away the upper-right corner of an app to look at the clock desklet. It's incredible how much you can get used to such things. ;)

---

### Post by ArinSky on 2011-05-03
Having the same issue with my driver for both the current and 173 drivers.

got this when trying to save the xorg.conf from nvidia-settings:

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Device section "Default Device" must have a Driver line.

my xorg.conf still appears to have no "Default Device" listed (or even an entry for it). Do you think this could be a part of the issue? I chowned it to user as well.

---

### Post by ArinSky on 2011-05-03
So...

I got it working on mine. I purged all nvidia files and did a command line reintall again, had it save the xconf, restarted, and then opened the compiz fusion icon and made sure it was on "Compiz", then reloaded the file manager.

sudo apt-get remove --purge nvidia*
sudo apt-get install nvidia-current
sudo nvidia-settings

          (saved xorg config here, said default device was not a valid field)

sudo update-grub
         (had seen that this problem had once in the past been caused by grub booting the wrong kernel)
uname -a
        (checked against the new grub file)


and then restarted and ran the "Compiz Fusion Icon" from applications->system tools
in the icon that appeared in the taskbar, i clicked and checked it was on compiz, then had it restart the file manager. It reloaded into Unity, with the side bar, and compiz effects working perfectly. I haven't restarted or anything to see how it works, but at worst I know I can get it to run more than likely by putting the command to reload the manager at startup.

---

### Post by Windoze Refugee on 2011-05-03
I think I may be in a similar boat. 
just upgraded to 11.04 and following a reboot cant get in at all...
It started off as an issue with evolution, following the upgrade to 11.04
I tried to open evolution but it appeared to hang when trying to retrieve files ie went greyed out..
I rebooted a couple of times but the same problem persisted.
In the end, on reboot I seletd start with prompt and oppted for "repair broken files"...
And ever since then all I get at boot is a small white rectangle with strange text objects.
Im not sure as IM as tech-savvy as you guys - is there a noobs way to fix this?
cheers

---

### Post by Windoze Refugee on 2011-05-03
I managed to load using a 10.10 disk, so in theory could naviagte to the new install. But....I dont know where to go to change the video drivers (assuming th nvidia thing is the problem) nor what to change when I get there
Any ideas anyone?
CHeers
WR

---

### Post by spikoley on 2011-05-03
> **Windoze Refugee said:**
> I managed to load using a 10.10 disk, so in theory could naviagte to the new install. But....I dont know where to go to change the video drivers (assuming th nvidia thing is the problem) nor what to change when I get there
Any ideas anyone?
CHeers
WR

Its a [bug]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788").  To manage the drivers you would go to System> Administration> Additional Drivers under the classic interface (Gnome).

---

### Post by Topazgb on 2011-05-03
Some have been downgrading their drivers [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/747717](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/747717)

---

### Post by Splat_NJ on 2011-05-03
After installing the ATI driver did you do an "sudo aticonfig --intial", then reboot?

---

### Post by Windoze Refugee on 2011-05-04
Thanks for your input guys. Ive done nothing so far. As I said, Ive managed to get 'in' by booting into a disk version of 10.10 and so can navigate the file structure. But I dont know where to go or what to do. Could you pLease consider me a complete novice and walk me through it? many thanks WR

---

### Post by Windoze Refugee on 2011-05-04
> **spikoley said:**
> Its a [bug]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788").  To manage the drivers you would go to System> Administration> Additional Drivers under the classic interface (Gnome).
  would that be a differnt loction for the main file tree to the temporary one established to run ubuntu form disk as Im doing at the moment?
Cheers for your help
WR

---

### Post by Windoze Refugee on 2011-05-04
> **Splat_NJ said:**
> After installing the ATI driver did you do an "sudo aticonfig --intial", then reboot?
  I havent even got as far as the install because after upgrading to 11.04 nothign worked. IM in only in the sense that Ive booted from a 19.10 disk and am running ubuntu from cd. Not sure where to go, what o change or how. :( Any help gratefully received. Cheers. WR

---

### Post by Splat_NJ on 2011-05-04
OK, be advised I haven't messed with 11.04 yet. I'll wait a few months, thank you.  I had problems with installing my new ATI card into Maverick when I got it. I don't know if this will work here's what I did to get it working: [http://ubuntuforums.org/showpost.php?p=10306271&postcount=15](http://ubuntuforums.org/showpost.php?p=10306271&postcount=15)

---

### Post by EvilBro on 2011-05-04
My system also says "Nvidia driver activated but not currently in use" on 11.04 Classic (unity does not seem to work). However, I do have desktop effects, lspci lists my graphic card ("02:00.0 VGA compatible controller: nVidia Corporation NV36.2 [GeForce FX 5700] (rev a1)") and xorg.conf does list it as well:
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5700"
EndSection

Is the description really accurate? How would I be able to tell?

---

### Post by dino99 on 2011-05-04
got unity failing to start due to missing .compiz/session/xxxxxxxx folders/file and cant get it working (filled bug #777164)

---

### Post by ArinSky on 2011-05-06
I think I've found a fix that works if you can manage to actually get into your ubuntu 11.04. It worked for me at least, so i'll break it down:

(only if you can't log in with classic!) To get in so we can work, on grub highlight the 11.04 OS line and press "e".

Go to the line that starts with "Linux". It should have a huge entry of characters, but after that there should be a few words like "splash" or "quiet". Put a space near here (after the long entry if you don't have other words there) and type "text". This should boot the OS in text form, though you may need to press ALT+f2 to get up a command prompt, not sure how it works in 11.04.

once you manage to boot with text only and log in:

```

sudo apt-get remove --purge nvidia*

```

This will remove all your nvidia installs that are there now. *This is important!* The old drivers were actually the crux of the problem for me.

Now you have to download the correct driver for your card. You can try doing nvidia-current if you think that will help, but for me that brought about the same problems. I had to use nvidia's 173 driver. (i think the normal choices are 96 for really old cards, the 173 is for go 5 to 9 series, and the 185 is for later... but don't quote me on that!)

```

sudo apt-get update
sudo apt-get install nvidia-glx-173

```

Obviously change the 173 to your number if your card is not in the GO 5 to 9 series'. This will install the drivers manually through synaptic.

when you restart, remove the "text" entry you put in earlier, and  hopefully you will be able to load a gui of some kind. If it doesn't  appear to be compiz (as was my issue) you also have to prompt compiz at startup because it wasn't loading properly:
```

compiz --replace

```

Once you get Unity working right, go to startup manager and just add that line in as a startup application, and it will auto-replace and load you into Compiz correctly.

For the record, Additional Hardware Sources will still say your driver is activated but not it use... but if you can make your windows wobble or see the sidebar, your card is working and its just a glytch.

Hope this helps someone else. Unity is so cool, and I like the efficiency of the new sidebar! Totally trumps cario-dock for me.

---

### Post by derekkrebs on 2011-05-10
> **ArinSky said:**
> I think I've found a fix that works if you can manage to actually get into your ubuntu 11.04. It worked for me at least, so i'll break it down:

(only if you can't log in with classic!) To get in so we can work, on grub highlight the 11.04 OS line and press "e".

Go to the line that starts with "Linux". It should have a huge entry of characters, but after that there should be a few words like "splash" or "quiet". Put a space near here (after the long entry if you don't have other words there) and type "text". This should boot the OS in text form, though you may need to press ALT+f2 to get up a command prompt, not sure how it works in 11.04.

once you manage to boot with text only and log in:

```

sudo apt-get remove --purge nvidia*

```This will remove all your nvidia installs that are there now. *This is important!* The old drivers were actually the crux of the problem for me.

Now you have to download the correct driver for your card. You can try doing nvidia-current if you think that will help, but for me that brought about the same problems. I had to use nvidia's 173 driver. (i think the normal choices are 96 for really old cards, the 173 is for go 5 to 9 series, and the 185 is for later... but don't quote me on that!)

```

sudo apt-get update
sudo apt-get install nvidia-glx-173

```Obviously change the 173 to your number if your card is not in the GO 5 to 9 series'. This will install the drivers manually through synaptic.

when you restart, remove the "text" entry you put in earlier, and  hopefully you will be able to load a gui of some kind. If it doesn't  appear to be compiz (as was my issue) you also have to prompt compiz at startup because it wasn't loading properly:
```

compiz --replace

```Once you get Unity working right, go to startup manager and just add that line in as a startup application, and it will auto-replace and load you into Compiz correctly.

For the record, Additional Hardware Sources will still say your driver is activated but not it use... but if you can make your windows wobble or see the sidebar, your card is working and its just a glytch.

Hope this helps someone else. Unity is so cool, and I like the efficiency of the new sidebar! Totally trumps cario-dock for me.

I think its more than a Jockey bug.  As I get choppy window movement and games run like crap.

---

### Post by EvilBro on 2011-05-11
> **ArinSky said:**
> Once you get Unity working right, go to startup manager and just add that line in as a startup application, and it will auto-replace and load you into Compiz correctly.
This seems weird. Ubuntu would start a windows manager and then immediately replace that windows manager with Compiz. Is there a better way to do this? (for instance by modifying some file which tells Ubuntu which windows manager it should use?)

---

### Post by Robbyx on 2011-05-12
I am pleased to say this works for me, but I had to activate the drivers in Additional drivers before it would work.

> **ArinSky said:**
> I think I've found a fix that works if you can manage to actually get into your ubuntu 11.04. It worked for me at least, so i'll break it down:

(only if you can't log in with classic!) To get in so we can work, on grub highlight the 11.04 OS line and press "e".

Go to the line that starts with "Linux". It should have a huge entry of characters, but after that there should be a few words like "splash" or "quiet". Put a space near here (after the long entry if you don't have other words there) and type "text". This should boot the OS in text form, though you may need to press ALT+f2 to get up a command prompt, not sure how it works in 11.04.

once you manage to boot with text only and log in:

```

sudo apt-get remove --purge nvidia*

```

This will remove all your nvidia installs that are there now. *This is important!* The old drivers were actually the crux of the problem for me.

Now you have to download the correct driver for your card. You can try doing nvidia-current if you think that will help, but for me that brought about the same problems. I had to use nvidia's 173 driver. (i think the normal choices are 96 for really old cards, the 173 is for go 5 to 9 series, and the 185 is for later... but don't quote me on that!)

```

sudo apt-get update
sudo apt-get install nvidia-glx-173

```

Obviously change the 173 to your number if your card is not in the GO 5 to 9 series'. This will install the drivers manually through synaptic.

when you restart, remove the "text" entry you put in earlier, and  hopefully you will be able to load a gui of some kind. If it doesn't  appear to be compiz (as was my issue) you also have to prompt compiz at startup because it wasn't loading properly:
```

compiz --replace

```

Once you get Unity working right, go to startup manager and just add that line in as a startup application, and it will auto-replace and load you into Compiz correctly.

For the record, Additional Hardware Sources will still say your driver is activated but not it use... but if you can make your windows wobble or see the sidebar, your card is working and its just a glytch.

Hope this helps someone else. Unity is so cool, and I like the efficiency of the new sidebar! Totally trumps cario-dock for me.

---

### Post by Jimothyscrye on 2011-05-22
> **derekkrebs said:**
> I think its more than a Jockey bug.  As I get choppy window movement and games run like crap.
  This is the case for me as well. I would love to be able to play some Team Fortress 2, but seem to be unable to do so without significant choppiness.

---

### Post by Dans564 on 2011-05-22
I had issues with my nvidia proprietary drivers and found a solution.  I have posted the solution here: [http://ubuntuforums.org/showthread.php?p=10849206#post10849206](http://ubuntuforums.org/showthread.php?p=10849206#post10849206)

Not sure if this applies to ur issue but try it out who know it might just fix it.  Good Luck!

---

### Post by Qubezo on 2011-05-26
I'm having the same problems. Can't seem to find a solution.

---

### Post by EvilBro on 2011-05-26
> **EvilBro said:**
> Is there a better way to do this? (for instance by modifying some file which tells Ubuntu which windows manager it should use?)
I found out how to do this "in a better way". See [here](http://ubuntuforums.org/showthread.php?t=1752623). Anyway, the problem seems to be that "/usr/lib/nux/unity_support_test --compiz" is too pessimistic about what my hardware can do...

---

### Post by zer010 on 2011-05-27
I'm having this problem, however, I'm using Xubuntu 11.04.  I had tried to use Ubuntu, but apparently, Unity[?] didn't think my gfx card was up to snuff....thus Xubuntu. So I'm not even using Compiz, but xfwm...I think!  So what's the underlying issue behind this problem?  Is Jockey reporting wrong or what?  I don't have any graphical issues that I'm aware of [yet], but I'm about to try to get some games going in WINE and I'd really like to know so I can narrow down the issues when troubleshooting....

---

### Post by Bristol_Green on 2011-05-31
Today's updates included "tool for configuring nvidia driver". Now that I've installed it, how do I run it? (Assuming it solves the problem we're all having.)

---

### Post by MikeSz on 2011-06-04
HELP!!

I just cant get anything now that ive upgraded to 11.04 - no boot menu, nothing!  Im running a Nvidia graphics card (no idea which one sorry) - has anyone managed to recover this?

---

### Post by jchw on 2011-06-05
I am afraid this is not going to help you too much but I had the same problem and ended up reinstalling 10.10 which I am still using very successfully.

---

### Post by gylti on 2011-06-06
installed 10.10 from disk after fail with 11.04 caused by messing around, it was working ok just I ruined it, now sys is crashing so nvid prob may be something to do with updates within 10.10 range. Never had this before and been on ubuntu for few years with normal upgrades. Have enabled acceleration but still getting crashes, disabled keyboard x- thing and installed best java with proper ln -s

---

### Post by johnthei on 2011-06-06
there is another thread about this on here. 28 pages of stuff about it. I am stuck just like you, cant get 11.04 to work with nvidia   
see        Graphics Resolution- Upgrade /Blank Screen after reboot

---

### Post by Blasphemist on 2011-06-06
As mentioned in the previous post there is another thread I think many of you should look at and either post to or at least subscribe to. [http://ubuntuforums.org/showthread.php?t=1743535&page=28](http://ubuntuforums.org/showthread.php?t=1743535&page=28) I used this page link as post 280 is one of the many posts with help for nvidia users. The first 3 posts are also very good for troubleshooting.

---

### Post by kherring7383 on 2011-06-06
This Nvidia driver problem in Natty is a known bug. For some, removing the driver and re-installing may help some, but also it may revert back to the same issue. 

However there is a way to find out if your Nvidia driver is in use. 

Check out this link, it covers the commands necessary to check what driver is installed. Hope this helps.


[http://www.reddit.com/r/Ubuntu/comments/h7zdn/this_driver_is_activated_but_not_currently_in_use/]("http://www.reddit.com/r/Ubuntu/comments/h7zdn/this_driver_is_activated_but_not_currently_in_use/")

---

### Post by Blasphemist on 2011-06-06
This is also a very helpful page for nvidia users and while not showing natty it was just updated yesterday for something.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Shaided on 2011-06-19
:popcorn: same problem here aswell.
~

---

### Post by Robbyx on 2011-06-19
I have reverted to nouvea and am not having any problems with my dual screen, non 3d setup.

Go into system settings---hardware---- additional drivers. Disable the in use driver by removing it (ie deactivate it).

rename /etc/x11/xorg.conf to xorg.conf.old

Restart

Check monitor settings in system settings. Make sure both monitors are in use if you have 2.

If it fails to work you can get back into Ubuntu via the low graphics option that appears when you start via the recovery mode. You may then reverse what you did to use nouveau.

---

### Post by beast2k on 2011-07-05
Same problem still, what a mess. Unity and now this, so much for attracting new users.

---

### Post by manipalrajesh on 2011-08-16
hi 
Please visit [http://nvidia.custhelp.com/app/answers/detail/a_id/44](http://nvidia.custhelp.com/app/answers/detail/a_id/44)
there click the below link
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)
You may .....get some helpful......

---

### Post by 1 d4 Nf6 on 2011-09-14
I downloaded this driver [http://www.nvidia.com/object/linux-display-amd64-280.13-driver.html](http://www.nvidia.com/object/linux-display-amd64-280.13-driver.html) but when I tried to open it, I got the message that gedit couldn't read it.

---

### Post by beast2k on 2011-09-14
I after 2 months still had the same problem. When things got real busy at work I had no more time to troubleshoot this problem. When it takes less than 30 min, many times less than 20 min, to install an entire distro you have to question the logic of any time spent longer than 20 min to troubleshoot any problem. I switched distros, problem solved. I wanted to mention this here because I hated to do it but as I said above, troubleshooting these kinds of problems these days is just not practical, not in a world where the whole distro installs in 20 min. Right now the Ubuntu live CD works better than the hard drive install. Anyway best of luck with this one. I had to give up. :(

---

### Post by mörgæs on 2011-09-15
You should only be proud of testing more distros! I just hope that more people would do the same and make an informed choice rather than sticking to a tradition.

---

