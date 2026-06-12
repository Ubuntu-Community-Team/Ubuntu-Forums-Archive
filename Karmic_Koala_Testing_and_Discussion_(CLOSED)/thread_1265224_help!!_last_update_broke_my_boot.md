---
title: "help!! last update broke my boot"
date: 2009-09-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ppjose on 2009-09-13
giving up
xinit: Connection refused (errno 111): unable to connect to Xserver
xinit: No such process (errno 3): server error.

I use nvidia drivers, i have a 6600GT

thanks!!!!

---

### Post by dino99 on 2009-09-13
are you with multi-boot ?
do you have files in /dev with several hours ahead ?
what is your timezone ?

i have this problem too & try to find a way

---

### Post by ppjose on 2009-09-13
i have karmic only in this pc
i edited xorg, change "nvidia" driver to "nv" and i have X again

---

### Post by Hairy_Palms on 2009-09-13
got the same problem here, tried reverting to older nvidia drivers but it didnt fix anything.

---

### Post by wireded on 2009-09-13
Similar here running Kubuntu on an nvidia-pc. Since last update machine still boots fine, but when starting x.org I get a segfault in /var/log/messages:

> Xorg[2960]: segfault at 8e1618a8 ip 8e1618a8 sp bf951968 error 4 in nvidia0[b76bc000+1000]

Already tried to manually reinstall propietary nvidia-drivers but had no luck by now. Choosing the "nv" drivers makes x.org with kde run again, but of course w/o desktop effects.

---

### Post by sena_akada on 2009-09-13
im having this issue too! i cant even use ctrl+alt+f1 to get to the console :(

---

### Post by wireded on 2009-09-13
Try alt+print+r before ctrl+alt+f1 to get keyboard control back from x-server

---

### Post by NCLI on 2009-09-13
I also have this problem. Using the nv driver for now, but I miss my Compiz screenbindings :(

---

### Post by sena_akada on 2009-09-13
i managed to fix my kubuntu install kind of. i reconfigured xorg.conf, removed the jockey nvidia driver, and now i can get to my desktop. i cant install the driver from the nvidia site as it says it finds libnvidia.so.1 or something, and it just fails to install :(:(:(:(:(

---

### Post by gmclachl on 2009-09-13
I am having the same issue, I can't drop to grub, I can't ssh into the machine and I can't use ctrl-alt-fx. So I guess I am pretty knackered, ah well..

---

### Post by ikkefc3 on 2009-09-13
I have te same problem too.
Is there a solution?

---

### Post by oasick on 2009-09-13
Same problem here with nvidia... I used the ubuntu cd to enter in a live session and change the driver "nvidia" to "nv" in xorg.conf.
Now i haven graphic acceleration...

---

### Post by morryis on 2009-09-13
Same same. Has anyone filed a bug report yet?

---

### Post by wireded on 2009-09-13
Well, I'm still trying to find out, which updated package broke the xserver (or to be more specific: nvidia-driver). I was taking a closer look at the update history, but there were (in my case) 58 updates. The only candidate who could have possibly caused this damage might be libc. But I'm far away from being able to call this out loud.
Perhaps we have to wait a few more hours until other people who didn't reboot their machine yet discover this problem as well. At this time we will hopefully get more information on this issue.
Seems nobody has filed a bug right now.

---

### Post by ikkefc3 on 2009-09-13
> **wireded said:**
> Well, I'm still trying to find out, which updated package broke the xserver (or to be more specific: nvidia-driver). I was taking a closer look at the update history, but there were (in my case) 58 updates. The only candidate who could have possibly caused this damage might be libc. But I'm far away from being able to call this out loud.
Perhaps we have to wait a few more hours until other people who didn't reboot their machine yet discover this problem as well. At this time we will hopefully get more information on this issue.
Seems nobody has filed a bug right now.

The problem occured to me before I rebooted: I closed plasma and it wouldn't start againt. Then I logged out, I saw the nVidia splash screen and it wouldn't go further. When I restarted, the screen was just black. When I reverted to the nv driver (alt+printscreen+r -> alt+ctrl+F1 -> login -> sudo rm -r /etc/X11.xorg.conf), it was booting normally.

---

### Post by ruik on 2009-09-13
Count me in, I'm having the same problem. I did a fresh Kubuntu install from today's build and everything worked fine until I installed the nvidia drivers.

---

### Post by NRDNick on 2009-09-13
Same here using ubuntu Karmic. Changed my xorg.conf and replaced "nvidia" with "nv" rebooted and X started up for me. I noticed that I had just installed some libc updates prior to noticing the problem as well.

---

### Post by sparker256 on 2009-09-13
> **ikkefc3 said:**
> The problem occured to me before I rebooted: I closed plasma and it wouldn't start againt. Then I logged out, I saw the nVidia splash screen and it wouldn't go further. When I restarted, the screen was just black. When I reverted to the nv driver (alt+printscreen+r -> alt+ctrl+F1 -> login -> sudo rm -r /etc/X11.xorg.conf), it was booting normally.

Is the right command sudo rm -r /etc/X11/xorg.conf  :confused:

---

### Post by Amodef on 2009-09-13
You can do :

"sudo nano /etc/X11/xorg.conf"

and replace "nvidia" by "nv"

then "ctrl+o" to save and "ctrl+x" to quit.

Just reboot (sudo reboot) and it should works...

---

### Post by oasick on 2009-09-13
In the afternoon the following packages were updated:

libc6-i686_2.10.1-0ubuntu11_i386.deb
libc6_2.10.1-0ubuntu11_i386.deb
libc6-dev_2.10.1-0ubuntu11_i386.deb
libc-dev-bin_2.10.1-0ubuntu11_i386.deb
libc-bin_2.10.1-0ubuntu11_i386.deb
python-pkg-resources_0.6c9-0ubuntu5_all.deb

After that, nvidia driver crashed...

---

### Post by MKdx on 2009-09-13
Another vote for libc. Saw the thread 10 minutes earlier and decided to update libc group to check, and now I have the same result. The screen seems to be trying to switch different modes for few seconds before showing OP error message.

---

### Post by gustavog on 2009-09-13
The same thing happened to me, I tried to re-install nvidia drivers, it gave me an error ("The runtime configuration check failed for the library 'libnvidia-tls.so'"), and even after I fixed that and succesfully reinstalled the driver it still didn't work.
Then I tried to use the nv driver instead, after that I could at least see the login screen. But when I try to login the screen goes black again and the login screen reappears again.

I am currently downloading karmic alpha5 to reinstall in case I can't find another solution.

PS: the problem appeared when I restarted today after the upgrade of libc too.

---

### Post by NRDNick on 2009-09-13
I'm experiencing the issue in Karmic as well, so I'm not sure installing that will fix your issues. But you can always install and not update anything ;)

---

### Post by Wild_Duck66 on 2009-09-13
Black Screen with Kubuntu Alpha 5. After removing the install CD. and rebooting the grub menu did not show the windows entry but its there in the grub.cfg.I installed the Nvidia driver and rebooted, this time windows was in the list and it booted Ok. So I updated and via synaptic downloaded some games the grandkids like but the next reboot I was left with a black screen at login. No keys had any effect (even Caps lock). Using recovery mode I had to manually fsck but it had no effect (init no such file),xorg.conf does not have much to alter. Strange thing is it happened on my laptop as well.

---

### Post by NRDNick on 2009-09-13
if you press alt+printscreen+r this will release the keyboard from the Xserver, then hit crtl+alt+F1 ->log in, then do a sudo nano /etc/X11/xorg.conf and change the line that says 
Section "Device"
Driver         "nvidia"

to 
Section "Device"
Driver         "nv"

Save the file and then issue the command startx or just reboot. That should get your desktop up and running, minus any extra video effects such as compiz.

Hope that helps.

---

### Post by wrb302 on 2009-09-13
mine too. after today's upgrade, X fail to start. Dell D630 w/ Nvidia Quardo 135M video card.

---

### Post by gustavog on 2009-09-13
Found this bug report [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/429003]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/429003")
Anyone knows how I can downgrade the packages libc6 and libc6-i686 to 2.10.1-0ubuntu9? doing apt-cache showpkg doesn't show me any version other than 2.10.1-0ubuntu11

Thanks in advance

---

### Post by FuturePilot on 2009-09-13
Ah, so this is what b0rked my system. I thought it just randomly got corrupted or something.

Same problem here with the nvidia-glx-96 driver.

---

### Post by alligoodw on 2009-09-13
I'm assuming at this point, that without fixing anything and waiting for future updates, this problem will resolve itself.  Am I right?

---

### Post by ayates on 2009-09-13
If you don't have the files in /var/cache/apt/archives they they can be found here:
[http://archive.ubuntulinux.org/ubuntu/pool/main/e/eglibc/](http://archive.ubuntulinux.org/ubuntu/pool/main/e/eglibc/)
Downgrading fixed the problem for me.

---

### Post by gustavog on 2009-09-13
Thanks ayates!!

I can finally login to my desktop pc now, just to clarify, I issued the following commands to fix it:

```
sudo dpkg -i --force-downgrade /var/cache/apt/archives/libc6_2.10.1-0ubuntu9_i386.deb
sudo dpkg -i --force-downgrade /var/cache/apt/archives/libc6-i686_2.10.1-0ubuntu9_i386.deb

```

Thanks again!

---

### Post by wireded on 2009-09-13
> **ayates said:**
> If you don't have the files in /var/cache/apt/archives they they can be found here:
[http://archive.ubuntulinux.org/ubuntu/pool/main/e/eglibc/](http://archive.ubuntulinux.org/ubuntu/pool/main/e/eglibc/)
Downgrading fixed the problem for me.
Great job. Thanks for the hint. Works like a charme.
I pinned the "*0ubuntu9" of libc6* in /etc/apt/preferences until bug is solved.

Let's see what happens :-D

---

### Post by orlox on 2009-09-13
This bug is reported as triaged, and with high importance. Should be fixed soon. (I'm affected by the way...long time since I used the nv drivers...)

---

### Post by Funnnny on 2009-09-13
Reinstall doesn't help, I never thought about downgrade :P, thanks for the hint

---

### Post by nitrogensixteen on 2009-09-14
libc6-dev dependencies will break too, the following will downgrade libc6 and temporarily prevent update back to the broken versions:

Downgrade libc6 to 9 instead of 11:
```
sudo dpkg -i --force-downgrade /var/cache/apt/archives/libc6_2.10.1-0ubuntu9_i386.deb
sudo dpkg -i --force-downgrade /var/cache/apt/archives/libc6-i686_2.10.1-0ubuntu9_i386.deb
sudo dpkg -i --force-downgrade /var/cache/apt/archives/libc6-dev_2.10.1-0ubuntu9_i386.deb
```

Pin v9 vice 11 to prevent update:
```
sudo nano /etc/apt/preferences
```
add the following lines:
```
Package: libc6
Pin: version 2.10.1-0ubuntu9
Pin-Priority: 700

Package: libc6-dev
Pin: version 2.10.1-0ubuntu9
Pin-Priority: 700

Package: libc6-i686
Pin: version 2.10.1-0ubuntu9
Pin-Priority: 700
```

remove these lines when the issue gets fixed.

---

### Post by gds on 2009-09-14
> **ayates said:**
> If you don't have the files in /var/cache/apt/archives they they can be found here:
[http://archive.ubuntulinux.org/ubuntu/pool/main/e/eglibc/](http://archive.ubuntulinux.org/ubuntu/pool/main/e/eglibc/)
Downgrading fixed the problem for me.

They don't seem to be there any more, and I don't have them in my apt cache. Any chance somebody could provide them until this is fixed? I'd like to at least get my laptop usable again.

---

### Post by Paqman on 2009-09-14
> **gds said:**
> They don't seem to be there any more, and I don't have them in my apt cache. Any chance somebody could provide them until this is fixed? I'd like to at least get my laptop usable again.

Me too, would appreciate if someone could pull them out of their cache and post them. Thanks!

---

### Post by L_V on 2009-09-14
> **ayates said:**
> the files can be found here: [http://archive.ubuntulinux.org/ubuntu/pool/main/e/eglibc/](http://archive.ubuntulinux.org/ubuntu/pool/main/e/eglibc/)
I only find ubuntu**11**_i386.deb version on this server.

Where previous versions can be found ?

---

### Post by jmmL on 2009-09-14
> **Paqman said:**
> Me too, would appreciate if someone could pull them out of their cache and post them. Thanks!

The files are too big for the forum. I'm uploading them to rapidshare, it will be done in a few minutes. Hope that's okay for everyone. (if it's against forum policy I'll remove the links)

Thanks to nitrogensixteen.

Edit: Here are the links:
[http://rapidshare.com/files/279913962/libc6-i686_2.10.1-0ubuntu9_i386.deb](http://rapidshare.com/files/279913962/libc6-i686_2.10.1-0ubuntu9_i386.deb)
[http://rapidshare.com/files/279913961/libc6-dev_2.10.1-0ubuntu9_i386.deb](http://rapidshare.com/files/279913961/libc6-dev_2.10.1-0ubuntu9_i386.deb)
[http://rapidshare.com/files/279913960/libc6_2.10.1-0ubuntu9_i386.deb](http://rapidshare.com/files/279913960/libc6_2.10.1-0ubuntu9_i386.deb)

---

### Post by L_V on 2009-09-14
It would be also good to know more generally where to find previous versions in ubuntu archives.
It is not the first time I have problems to downgrade.

---

### Post by dino99 on 2009-09-14
here you go:

[http://packages.ubuntu.com/en/karmic/](http://packages.ubuntu.com/en/karmic/)


All deb packages ever released by ubuntu can be accessed by replacing the variables at the appropriate places in the following URL template.

https://launchpad.net/ubuntu/$ubuntu-release/$arch/$package-name/$package-version

---

### Post by lazka on 2009-09-14
[http://launchpadlibrarian.net/31699761/libc6_2.10.1-0ubuntu9_i386.deb](http://launchpadlibrarian.net/31699761/libc6_2.10.1-0ubuntu9_i386.deb)
[http://launchpadlibrarian.net/31699765/libc6-i686_2.10.1-0ubuntu9_i386.deb](http://launchpadlibrarian.net/31699765/libc6-i686_2.10.1-0ubuntu9_i386.deb)
[http://launchpadlibrarian.net/31699762/libc6-dev_2.10.1-0ubuntu9_i386.deb](http://launchpadlibrarian.net/31699762/libc6-dev_2.10.1-0ubuntu9_i386.deb)

[http://launchpadlibrarian.net/31698629/libc6_2.10.1-0ubuntu9_amd64.deb](http://launchpadlibrarian.net/31698629/libc6_2.10.1-0ubuntu9_amd64.deb)
[http://launchpadlibrarian.net/31698630/libc6-dev_2.10.1-0ubuntu9_amd64.deb](http://launchpadlibrarian.net/31698630/libc6-dev_2.10.1-0ubuntu9_amd64.deb)

---

### Post by Paqman on 2009-09-14
> **dino99 said:**
> 
All deb packages ever released by ubuntu can be accessed by replacing the variables at the appropriate places in the following URL template.

https://launchpad.net/ubuntu/$ubuntu-release/$arch/$package-name/$package-version

Maybe i've got my syntax a bit wonky, but when I try:

[http://packages.ubuntu.com/karmic/amd64/libc6/libc6_2.10.1-0ubuntu9](http://packages.ubuntu.com/karmic/amd64/libc6/libc6_2.10.1-0ubuntu9)

It stops me at an error page saying "two or more packages specified"???

---

### Post by juancarlospaco on 2009-09-14
Same problem..., 
i have tested nVidia Beta Drivers 190.32 and 190.18 and didnt work.
i have tested nVidia old drivers and didnt work.

THIS IS THE REASON WHY NVIDIA DRIVERS NEED TO BE OPEN SOURCE.

:)

---

### Post by dino99 on 2009-09-14
seem that it's due to libc6, need to downgrade

[http://ubuntuforums.org/showthread.php?t=1265224&page=4](http://ubuntuforums.org/showthread.php?t=1265224&page=4)

look at post #35

---

### Post by afv on 2009-09-14
> **Paqman said:**
> Maybe i've got my syntax a bit wonky, but when I try:

[http://packages.ubuntu.com/karmic/amd64/libc6/libc6_2.10.1-0ubuntu9](http://packages.ubuntu.com/karmic/amd64/libc6/libc6_2.10.1-0ubuntu9)

It stops me at an error page saying "two or more packages specified"???

Try [https://launchpad.net/ubuntu/karmic/amd64/libc6/2.10.1-0ubuntu9](https://launchpad.net/ubuntu/karmic/amd64/libc6/2.10.1-0ubuntu9).

---

### Post by Robin Nixon on 2009-09-14
> **Amodef said:**
> You can do :

"sudo nano /etc/X11/xorg.conf"

and replace "nvidia" by "nv"

then "ctrl+o" to save and "ctrl+x" to quit.

Just reboot (sudo reboot) and it should works...

That did the trick for me on both machines (both w/ nvidia cards)

Thanks!

---

### Post by L_V on 2009-09-14
Unfortunately, a very recent update prevents KDE to start, although I did the libs downgrade, and use the radeon free driver (for radeon 9200).
I will use another system, waiting for updates !
Thanks for all replies.

---

### Post by keithpeter on 2009-09-14
> **wireded said:**
> Try alt+print+r before ctrl+alt+f1 to get keyboard control back from x-server

That worked. Edited xorg.conf to have nv as driver and back to desktop.

Now, how do I get nv to show full screen resolution? The System | Preference | Display menu tries to start the nvidia x configure package.

---

### Post by Paqman on 2009-09-14
> **afv said:**
> Try [https://launchpad.net/ubuntu/karmic/amd64/libc6/2.10.1-0ubuntu9](https://launchpad.net/ubuntu/karmic/amd64/libc6/2.10.1-0ubuntu9).

Cheers. That link and lazka's are now both correct. Unfortunately for me i've since upgraded and can't downgrade without uninstalling a ton of other apps. Guess i'm stuck with the nv driver until we get the new libc6.

---

### Post by autocrosser on 2009-09-14
Has the new libc6 "fixed" this problem?

---

### Post by BCurtisWX on 2009-09-14
> **autocrosser said:**
> Has the new libc6 "fixed" this problem?

it has to finish building.  then it has to get accepted.. then it has to get to the "DONE" status before you'll see it in the repos.. BUT... its almost done... so expect it in a few hours

---

### Post by autocrosser on 2009-09-14
Thanks for the info!!!

---

### Post by beach_defender on 2009-09-15
How is it that this Nvidia Screen issue keeps coming back ALL the time. I currently have 2 computers effectively out of commission, simply because in both cases the user accepted a recommendation to upgrade.

I have seen references to this issue going back ages, surely someone could test the updates BEFORE sending them out?

This one issue is causing a extremely high level of stress and frustration in my team, not to count the cost of having people spending most of their time trying to fix something that should never have occurred in the first place.

I have an 8.0.4 install that up until today had been as steady as a rock. Then Update Manager told me that there were updates for Firefox, so I clicked the update button.  I rebooted as prompted.

The I get this 800 X 600 resolution where before I had great settings and it seems that trhe magic updater has removed the nvidia drivers and settings.

why,why,why?

---

### Post by dino99 on 2009-09-15
> **beach_defender said:**
> How is it that this Nvidia Screen issue keeps coming back ALL the time. I currently have 2 computers effectively out of commission, simply because in both cases the user accepted a recommendation to upgrade.

I have seen references to this issue going back ages, surely someone could test the updates BEFORE sending them out?

This one issue is causing a extremely high level of stress and frustration in my team, not to count the cost of having people spending most of their time trying to fix something that should never have occurred in the first place.

I have an 8.0.4 install that up until today had been as steady as a rock. Then Update Manager told me that there were updates for Firefox, so I clicked the update button.  I rebooted as prompted.

The I get this 800 X 600 resolution where before I had great settings and it seems that trhe magic updater has removed the nvidia drivers and settings.

why,why,why?

if you take the risk to use an alpha distro for your work, you might accept all the bad side of testing. If you or/and your team have not the knowledge for that, well stay away and stop complaint.

---

### Post by Bytesource on 2009-09-15
Just found out that the updated libc6 is already out. Updated my system and now everything works great

That was really fast. Thank you very much!

---

### Post by L_V on 2009-09-15
I've tried libc V12  packages found at [https://launchpad.net/ubuntu/+source/eglibc/2.10.1-0ubuntu12/+build/1244034](https://launchpad.net/ubuntu/+source/eglibc/2.10.1-0ubuntu12/+build/1244034)
It did not solve anything for [ KDE4 / ATI radeon 9200 ] configuration.

According to the schedule: September 17th, 2009 => Alpha 6 release
This regression should be fixed for Alpha 6 to avoid a complete mess.

---

### Post by Hairy_Palms on 2009-09-15
the updates fixed it for me,

---

### Post by cyberkilla on 2009-09-15
Well, I reverted to using the NV driver, then proceeded to check for updates and install everything possible.

I'm still having the blinking screen/infinite loop before even reaching GDM, unless I stick with NV.

Any suggestions that don't involve me going away?:)

---

### Post by zenarcher on 2009-09-15
The updates fixed it for me, as well.  I did notice that on one of my systems, the boot was very fast, as usual, while on the other box, the boot seemed to be quite slow.  Not sure about that but perhaps a couple of more fresh boots will tell me more.

Cheers,
zenarcher

---

### Post by Citizen_Kane01 on 2009-09-15
Help Please!

I have the same problem, but don't know how to install updates if I can't boot into Ubuntu.

Thanks in advance.

---

### Post by Bytesource on 2009-09-15
> **Citizen_Kane01 said:**
> Help Please!

I have the same problem, but don't know how to install updates if I can't boot into Ubuntu.

Thanks in advance.

I am not a Linux expert either, but this is how I did it:
1) Start your computer 
2) On the GRUB screen choose "kernel ... (recovery mode)". This is the second option from the top, use the arrow key to move there, then press "enter".
3) You will get to a screen with several options. Use the arrow key to move down to "Shell with networking" (the real name is a little different, but that's how I remember it).
4) You will get to a terminal prompt where you enter the following commands:
```
sudo apt-get update
```
This checks the repositories for available updates and may take a while.
Then enter this command to download and install all updates:
```
sudo apt-get upgrade
```
This also may take a while. After that enter "exit" (without the quotes). You will get to the screen from no. 3) again. Choose "resume normal boot". Now it should work. If not, just reboot.

Please note, when I switched on my laptop today I ran into another problem that broke the booting process. IF you still encounter problems at boot up, please refer to this post: [http://ubuntuforums.org/showthread.php?t=12 67183&highlight=karmic&page=3](http://ubuntuforums.org/showthread.php?t=12 67183&highlight=karmic&page=3) (Karmic Update Breaks Boot)

The following commands given in this thread enabled me to finish booting:
```
sudo start dbus
sudo start hal
sudo start network-manager
sudo start gdm
```
At this time this is only a workaround until the problem gets fixed with a new update. However, at least you will be able to use your computer.

---

### Post by woedend on 2009-09-15
mine wouldn't let me do anything at all...just blackness.  I somehow managed to finagle it working again..the key is to imagine that you are at a shell but just can't see whats being typed.  It IS taking commands, you just can't see them, so type carefully.  I got dbus and hal started i figure, but not network manager.  I actually was kinda desperate and was going to give up so ran sudo shutdown now...after about 30 seconds it booted me to GDM.  From there I got network manager going(sudo NetworkManager start)...case being important there...and was able to do updates. The last round of updates gives me weird boot messages but does end up at GDM finally.

---

### Post by Citizen_Kane01 on 2009-09-16
Thanks Bytesource,

I can now update from the recovery mode, once I remembered to plug in the network cable directly as the wireless does not start up.

I am still not getting Karmic to run, but am happy enough to wait till an update fixes the (Alpha) problem. Here is my summary:

Acer Aspire 7730 (Intel series 4 mobile chipset with integrated graphics)

After update the boot enters verbose mode and hangs at the 'winbind daemon' stage.

I do sudo start dbus, hal, network-manager, gdm. At this stage the screen goes black and starts flashing like a black/ white disco light. That is as far as it goes.

Hope this helps someone in development.

Cant wait for the stable Koala!

---

### Post by Wild_Duck66 on 2009-09-19
Kubuntu 9.10 alpha 5 was alright until an update then a black screen at login, recovery mode did`nt fix it. Alpha 6 (Kubuntu and Ubuntu [seperate downloads]) ran OK.in live mode but initial reboot after install gave one screen of writing then a black screen, identical results in recovery mode. This happens on my desktop and Laptop.
Here`s some of the lines:-
kinit No resume image doing normal kinit
udevd[1196]:NAME "k" is superfluous and breaks kernel supplied
remove it from /lib/udev/rules.d/40 ppc.rules:1
udevd[1196]:unknown key `SYMLINK`{imique} /lib/udev/rules.d/50-udev-default
udevd[1196]:can not read /etc/-----hdparm.rules

I`ve been downloadind Alphas from around the time of Dapper but never had any not work at all.
Gone back to 9.04 now i`ll try again later.

---

### Post by c3apollyon on 2009-09-20
Same problem on my machine...
I can use CTRL-F2 to get to a terminal login, but after a startx command I find I have no keyboard/mouse support in the GUI.  Not sure if that is related to the boot hanging issue or to my bluetooth setup in relation to where the boot halted.

---

### Post by Wild_Duck66 on 2009-09-20
Another interesting thing I noticed is that although I dual boot with Windows (XP on my Desktop, Vista on Laptop)there is no entry in the Grub boot list only K/Ubuntu 9.10 + Recovery mode + Mem test even though it`s in the grub.cfg(at least in Alpha 5 never saw Alpha 6)

---

### Post by somnob on 2009-09-29
Is this bug reported jet?
is thare a fix for this.
becouse i have this problem to you now.

---

### Post by FuturePilot on 2009-09-29
> **somnob said:**
> Is this bug reported jet?
is thare a fix for this.
becouse i have this problem to you now.

This was fixed a long time ago. Make sure you have all updates installed. If you do, I suspect you might have a different problem. Do you have a Nvidia card?

---

### Post by somnob on 2009-09-29
yes it's a compaq presario CQ60-420ED laptop with a nvidia card.
and is't running kubuntu 9.10 alpha 6 with the latest updates.
i update a lot.. :)

---

### Post by somnob on 2009-09-29
and the screen is just geting black after login.

I fix it bij reinstaling the system.

---

