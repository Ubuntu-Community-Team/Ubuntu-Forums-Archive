---
title: "Upgrade 11.04 to 11.10 failed"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by ratcheer on 2011-10-13
My upgrade failed and I have no idea why.

First, I made sure Natty was fully up-to-date. Then I ran the graphical  Update Manager and started the upgrade. It took a long time downloading  packages (estimated time was over an hour and a half), so I worked on  some other needs around the house. When I came back, the screen was  black and could not be reactivated. I was pretty sure the system was  doing nothing, because there was no disk activity, at all. I watched the  light for several minutes.

So, I rebooted. Natty came back up just fine. I am in it, right now. Whatever happened does not seem to have messed anything up.

What should I do to troubleshoot? What should I do befor reattempting  the upgrade? I have a Parted Magic CD and good testing installations of  Oneiric and Arch Linux on the same PC, so there are plenty of tools to  work with.

Thanks,
Tim

---

### Post by ratcheer on 2011-10-13
More info:

1) Natty started crashing, just freezing up. So more was affected than I originally thought. I am now posting from my Oneiric testing installation.

2) I found /var/log/dist-upgrade folder. The last updated file in it was more than 45 minutes prior to my rebooting the PC.

3) This PC may have a Catch-22. Both the ethernet NIC and the wireless card require proprietary drivers that are not in the Linux kernel. Since I know the kernel will be upgraded from 2.6 to 3.0, the system will probably lose connectivity at some point during the installation.

Also, I will do a recovery boot of Natty and try to get the requested info from apt-sources.lst.

Tim

---

### Post by Blasphemist on 2011-10-13
What does update manager now say needs updated? Anything? Does synaptic report any upgrades can be marked? If either say there are updates needed, do them. All downloads should happen before the upgrades start so at worst I'd expect a complete upgrade and then a need to re-implement your networking programs.

---

### Post by ratcheer on 2011-10-13
/etc/apt/sources.list appears to have been updated, properly. All sources that are not commented out are for the Oneiric repositories.

I guess I will re-attempt the upgrade from the recovery mode root command line.

@Blasphemist, I agree, it looks like it was going to download everything before it changed anything. So, the upgrade should run to completion.

Thanks,
Tim

---

### Post by ratcheer on 2011-10-13
Well, it is good news and bad news.

The good news is that, although it took two more upgrades stopping, then rebooting the system to get back in control, and resuming the upgrade, it finally completed, successfully.

The bad news is that, after using the new system for about 15 minutes of checking things out (everything I checked looked pretty good), it froze again. I rebooted back into it, and it froze again before I could do anything.

So, here I am back on my Oneiric testing installation, again, wondering how to get my main system to act right.

Tim

---

### Post by 23dornot23d on 2011-10-13
Have you checked the log file viewer .....

Try to spot in there what is causing the lock up .... ?

---

### Post by ratcheer on 2011-10-13
Ok, I have been up for over 10 minutes checking the logs, with no freeze (knock on wood). So far, I have not seen anything that caught my eye in the logs. I have looked at dmesg, syslog, xorg.0.log.old, and maybe a couple of other places.

I was suspecting Firefox, but right now, I am using it without trouble.

I have to go work on dinner for my family. I'll be back, later.

Thanks,
Tim

---

### Post by Blasphemist on 2011-10-13
Can you tell if the lockups are complete or just x possibly? You might try something from this list of options that I keep at hand. I just know that sometimes you can't tell if the screen just isn't letting you see how to interface with a system. This is from MAFoElffen's sticky thread.
> Here is a short quick-reference of Linux short-cuts and hot-keys to help you get around and to help diagnose graphics problems in an Linux Xsession. Some are also helpful later in just everyday kind of tasks. Like I said, this is only an abbreviated list, but I included them here because they do come in handy in diagnostics and the correction of boot and video errors: 

<Ctrl><Alt><F1> 
Switch to the first text terminal. Under Linux you can have several (6 in standard setup) terminals opened at the same time. Terminals start as tty0 and go up from there. Most of the time the normal boot text console, that is present "under" the GUI or Xsession (in Ubuntu) is tty1, so you would press <Cntrl><Alt><F2> to get to it... 

<Ctrl><Alt><Fn> (n=1..6) 
Switch to the nth text terminal. 

tty<Enter> 
Print the name of the terminal in which you are typing this command. 

<Ctrl><Alt><F7> 
Switch to the first GUI terminal (if X-windows is running on this terminal). 

<Ctrl><Alt><Fn> (n=7..12) 
Switch to the nth GUI terminal (if a GUI terminal is running on screen n-1). On default, nothing is running on terminals 
8 to 12, but you can run another server there. 

<Tab> 
(In a text terminal) Autocomplete the command if there is only one option, or else show all the available options. 
THIS SHORTCUT IS VERY HANDY! This also works at LILO or GRUB prompt! 

<ArrowUp> 
Scroll and edit the previous command history. You can then use that command as is or edit it to change. Press <Enter> to execute. 

<Arrow><Down> 
As above, but go back to the next command in history. 

<Shift><PgUp> 
Scroll terminal output up. Work also at the login prompt in the tty text console, so you can scroll through your bootup messages to find errors and messages. Does not work to see terminal output that has been "cleared." 

<Shift><PgDown> 
As above, but scrolls terminal output down. 

<Ctrl><Alt><+> 
(in X-windows) Change to the next X-server resolution (if you set up the X-server to more than one resolution in /etc/X11/XF86Config). For multiple resolutions on my standard SVGA card/monitor, I have the following line in the file /etc/X11/XF86Config (the first resolution starts on default, the largest determines the size of the "virtual screen"): 
Modes "1440x900" "1024x768" "800x600" "640x480" "512x384" "480x300" "400x300" "1152x864" Whichever resolution you have as first in this line will be the default. 

<Ctrl><Alt><-> 
(in X-windows) Change to the previous X-server resolution. 

<Ctrl><Atl><Backspace>
Linux Ubuntu version 10.10 and previous- Kill the current X-session.

<Alt>-<SysReq>-<k>
Linux Ubuntu version 11.04 and later- Kill the current X-session.

-- The "Linux shortcut keys" are just that, meaning Linux is already booted. to use them-- although "some" of them do work in the Grub CLI. *such as the <Tab> for autocomplete)


---

### Post by ratcheer on 2011-10-13
Thanks, Jim. But none of those things work. When it is freezing, it seems to be completely frozen.

Also, I had just returned to my PC after dinner, and it was at the LightDM login screen. But that was frozen, too. Prior to dinner, I had used it for about an hour with no problems.

I may just need to migrate all my important data from it and convert this testing instance to my "real" instance.

Tim

---

### Post by 23dornot23d on 2011-10-13
Just from what I have been watching on the threads today ..... many are having freezes 
with ATI cards ..... so it may be related .....

Not seen a fix yet though ..... if I see one I will let you know ,,,,,

---

### Post by ratcheer on 2011-10-13
But, I have the same card in the same PC with my testing instance and, no freezes.

Tim

---

### Post by jfever311 on 2011-10-13
My laptop froze twice after upgrading. I simply restarted each time, and after the second time, there have been no issues. Might just be the hardware needs time to recognize the new software?? Then again, I am a crane operator, not a computer tech.

---

### Post by laycor on 2011-10-14
I performed the upgrade last night and it's foobar'd

first off I checked to ensure there were no updates pending.

Then I launched the update manager and clicked on Upgrade to 11.10.

It went through all the actions of downloading and installing and popped up with 2 error messages - both of which related to SAMBA being unable to be installed, but I could fix this later by reinstalling SAMBA - not a problem.

Once it had finished I rebooted and nothing.. The screen is black.

I booted into recovery mode and then continued with the boot and watched the messages.

It looks like it can't handle mounting the encrypted FS.

If anyone has any way around this - I'm all ears, before I wipe it and put Windows back on there ;o)

---

### Post by Blasphemist on 2011-10-14
> **laycor said:**
> I performed the upgrade last night and it's foobar'd

first off I checked to ensure there were no updates pending.

Then I launched the update manager and clicked on Upgrade to 11.10.

It went through all the actions of downloading and installing and popped up with 2 error messages - both of which related to SAMBA being unable to be installed, but I could fix this later by reinstalling SAMBA - not a problem.

Once it had finished I rebooted and nothing.. The screen is black.

I booted into recovery mode and then continued with the boot and watched the messages.

It looks like it can't handle mounting the encrypted FS.

If anyone has any way around this - I'm all ears, before I wipe it and put Windows back on there ;o)
Personally I think you're a bit premature on the wiping. I think you should create a new thread on this and see if someone with good knowledge on encryption can help. I can think of some ideas but I think you should try for help from someone with better experience with encryption and SAMBA. Send me a message if you don't find the help you need.

Tim-
What can you describe as the differences in your working and not working environments? How much can you do toward helping to get focused on the right thing from the logs? Have you tried mounting the non working environment while running the good to get log file access while not having lockups? As always its best to keep it simple so starting by finding differences should help.

---

### Post by ratcheer on 2011-10-14
Back to my problems. Here is the current state of my packages. It says it wants to do these upgrades and new installs, but when I tell it to go ahead, nothing gets updated.
```

The following NEW packages will be installed:
  flashplugin-downloader{ab} gcc-4.6-base{a} gir1.2-atspi-2.0{a} gir1.2-wnck-3.0{a} gvfs-bin{a} ia32-libs-multiarch{a} 
  indicator-status-provider-mc5{a} lib32ffi6{a} libacl1{a} libasound2{a} libasound2-plugins{a} libasyncns0{a} libatk1.0-0{a} 
  libattr1{a} libaudio2{a} libavahi-client3{a} libavahi-common-data{a} libavahi-common3{a} libbrasero-media3-1{a} libc6{a} 
  libcairo2{a} libcomerr2{a} libcups2{a} libcupsimage2{a} libcurl3{a} libdatrie1{a} libdb5.1{a} libdbus-1-3{a} libdrm-intel1{a} 
  libdrm-nouveau1a{a} libdrm-radeon1{a} libdrm2{a} libevince3-3{ab} libexpat1{a} libffi6{a} libflac8{a} libfontconfig1{a} 
  libfreetype6{a} libgcc1{a} libgcrypt11{a} libgdbm3{a} libgdk-pixbuf2.0-0{a} libgl1-mesa-dri{a} libgl1-mesa-glx{a} libglapi-mesa{a} 
  libglib2.0-0{a} libgnutls26{a} libgpg-error0{a} libgssapi-krb5-2{a} libgtk2.0-0{a} libice6{a} libidn11{a} 
  libindicator-messages-status-provider1{a} libjack-jackd2-0{a} libjasper1{a} libjpeg62{a} libjpeg8{a} libjson0{a} libk5crypto3{a} 
  libkeyutils1{a} libkrb5-3{a} libkrb5support0{a} liblcms1{a} libldap-2.4-2{a} libllvm2.9{a} libmng1{a} libmysqlclient16{ab} 
  libnspr4{a} libnspr4-0d{a} libnss3{a} libnss3-1d{a} libogg0{a} libpango1.0-0{a} libpciaccess0{a} libpcre3{a} libpixman-1-0{a} 
  libpng12-0{a} libpulse0{a} libqt4-dbus{a} libqt4-declarative{a} libqt4-designer{a} libqt4-network{a} libqt4-opengl{a} 
  libqt4-qt3support{a} libqt4-script{a} libqt4-scripttools{a} libqt4-sql{a} libqt4-sql-mysql{a} libqt4-svg{a} libqt4-test{a} 
  libqt4-xml{a} libqt4-xmlpatterns{a} libqtcore4{a} libqtgui4{a} librtmp0{a} libsamplerate0{a} libsasl2-2{a} libsasl2-modules{a} 
  libselinux1{a} libsm6{a} libsndfile1{a} libspeexdsp1{a} libsqlite3-0{a} libssl1.0.0{a} libstdc++6{a} libtasn1-3{a} libthai0{a} 
  libtiff4{a} libuuid1{a} libvorbis0a{a} libvorbisenc2{a} libwrap0{a} libx11-6{a} libxau6{a} libxcb-render0{a} libxcb-shm0{a} 
  libxcb1{a} libxcomposite1{a} libxcursor1{a} libxdamage1{a} libxdmcp6{a} libxext6{a} libxfixes3{a} libxft2{a} libxi6{a} 
  libxinerama1{a} libxrandr2{a} libxrender1{a} libxss1{a} libxt6{a} libxxf86vm1{a} nspluginviewer{a} python-pyatspi2{ab} zlib1g{a} 
The following packages will be upgraded:
  brasero brasero-cdrkit brasero-common console-setup{b} evince evince-common flashplugin-installer gnome-orca gnome-panel{b} 
  gnome-panel-data gvfs{b} gvfs-backends gvfs-fuse ia32-libs indicator-messages{b} indicator-session{b} libv4l-0 nspluginwrapper 
  ntfs-3g{b} python-gconf python-glade2 python-gnome2{b} python-gtk2 
23 packages upgraded, 134 newly installed, 0 to remove and 0 not upgraded.
```

```
Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
```


Tim

---

### Post by ubontik on 2011-10-14
I upgraded and after restarting it freezes on the Ubuntu flash screen.  I tried to reboot but it stops on the same screen.

I do not want to do clean install. Is there a way to do it safe.

Thanks

---

### Post by ratcheer on 2011-10-14
Ok, although aptitude would not upgrade the remaining stuff, I ran the GUI Update Manager program and it did. It upgraded or installed 149 more packages and removed 18. 

So, when I upgraded yesterday and it said it completed, in fact the upgrade was ***not*** complete.

I am keeping my fingers crossed that this will resolve the issues. If things work well for a good while, I will mark the thread as Solved.

Tim

---

### Post by sturg_nz on 2011-10-14
> **laycor said:**
> I performed the upgrade last night and it's foobar'd

first off I checked to ensure there were no updates pending.

Then I launched the update manager and clicked on Upgrade to 11.10.

It went through all the actions of downloading and installing and popped up with 2 error messages - both of which related to SAMBA being unable to be installed, but I could fix this later by reinstalling SAMBA - not a problem.

Once it had finished I rebooted and nothing.. The screen is black.

I booted into recovery mode and then continued with the boot and watched the messages.

It looks like it can't handle mounting the encrypted FS.

If anyone has any way around this - I'm all ears, before I wipe it and put Windows back on there ;o)
To fix this one, I discovered that during my upgrade I had a whole bunch of 403 errors with my local mirror. I changed the repository to main server, completed the partial upgrade (it kept on annoying me to complete) and voila. All good now. Except for my bluetooth which is a minor annoyance.

---

### Post by ratcheer on 2011-10-14
Even after post #17 activities, aptitude still reports these problems:

```
sudo aptitude full-upgrade
The following NEW packages will be installed:
  flashplugin-downloader{ab} libasound2{a} libasound2-plugins{a} libasyncns0{a} libevince3-3{ab} libflac8{a} 
  libjack-jackd2-0{a} libjson0{a} libnspr4-0d{a} libnss3-1d{a} libogg0{a} libpulse0{a} libsamplerate0{a} libsndfile1{a} 
  libspeexdsp1{a} libvorbis0a{a} libvorbisenc2{a} libwrap0{a} 
The following packages will be upgraded:
  evince evince-common flashplugin-installer 
3 packages upgraded, 18 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.0 kB/4,011 kB of archives. After unpacking 14.5 MB will be used.
The following packages have unmet dependencies:
  libevince3-3: Breaks: libevdocument3 but 2.32.0-0ubuntu12.3 is installed.
                Breaks: libevview3 but 2.32.0-0ubuntu12.3 is installed.
  flashplugin-downloader: Conflicts: flashplugin-nonfree (< 11.0.1.152ubuntu1) but 11.0.1.152ubuntu0.11.04.1 is installed.
  flashplugin-nonfree: Conflicts: flashplugin-nonfree which is a virtual package.
Unable to resolve dependencies!  Giving up...
The following NEW packages will be installed:
  flashplugin-downloader{ab} libasound2{a} libasound2-plugins{a} libasyncns0{a} libevince3-3{ab} libflac8{a} 
  libjack-jackd2-0{a} libjson0{a} libnspr4-0d{a} libnss3-1d{a} libogg0{a} libpulse0{a} libsamplerate0{a} libsndfile1{a} 
  libspeexdsp1{a} libvorbis0a{a} libvorbisenc2{a} libwrap0{a} 
The following packages will be upgraded:
  evince evince-common flashplugin-installer 
3 packages upgraded, 18 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.0 kB/4,011 kB of archives. After unpacking 14.5 MB will be used.
aptitude failed to find a solution to these dependencies.  You can solve them yourself by hand or type 'n' to quit.
The following packages have unmet dependencies:
  libevince3-3: Breaks: libevdocument3 but 2.32.0-0ubuntu12.3 is installed.
                Breaks: libevview3 but 2.32.0-0ubuntu12.3 is installed.
  flashplugin-downloader: Conflicts: flashplugin-nonfree (< 11.0.1.152ubuntu1) but 11.0.1.152ubuntu0.11.04.1 is installed.
  flashplugin-nonfree: Conflicts: flashplugin-nonfree which is a virtual package.
Resolve these dependencies by hand? [N/+/-/_/:/?] Y
Enter a package management command (such as '+ package' to install a package), 'R' to attempt automatic dependency resolution or
'N' to abort.
Resolve these dependencies by hand? [N/+/-/_/:/?] N
Abort.

```

Tim

---

### Post by ratcheer on 2011-10-14
Ok, since I install my Flash player manually, I removed packages flashplugin-installer and flashplugin-nonfree. This reduced the mess to:

```
The following NEW packages will be installed:
  libevince3-3{ab} 
The following packages will be upgraded:
  evince evince-common 
2 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,021 kB of archives. After unpacking 6,107 kB will be used.
The following packages have unmet dependencies:
  libevince3-3: Breaks: libevdocument3 but 2.32.0-0ubuntu12.3 is installed.
                Breaks: libevview3 but 2.32.0-0ubuntu12.3 is installed.
The following actions will resolve these dependencies:

       Remove the following packages:
```

Then it wants to remove 106 packages, including such things as ubuntu-desktop, several libqt4 packages, and even libc6. I declined the resolution. But, apparently I am down to just three top-level packages that have problems.

Any advice on cleaning this up non-destructively would be much appreciated.

Thanks,
Tim

---

### Post by ratcheer on 2011-10-14
Can anyone help?

Thanks,
Tim

---

### Post by 23dornot23d on 2011-10-14
do 

**aptitude safe-upgrade **

see what it returns ......

---

### Post by ratcheer on 2011-10-14
I found a suggestion in another thread to "sudo apt-get -f install evince evince-common". This seems to have worked. All packages seem to be installed with none held.

However, as soon as that command completed, the system froze again. It rebooted and so far, things look good.

Thanks, 23dornot23d

Tim

---

### Post by 23dornot23d on 2011-10-14
welcome I hope it runs ok now ....

---

### Post by ratcheer on 2011-10-14
Unfortunately, I am back to the freezes, again. It has frozen two more times since my last post. I am back on my Oneiric testing instance.

Tim

---

### Post by ratcheer on 2011-10-15
I have decided to give up on my production instance, mount my production /home on my testing instance, and make my new testing instance my production instance.
 
IMHO, even though it appeared I was 99.9% there, **UPGRADE FAILED!**
 
Tim

---

### Post by ratcheer on 2011-10-15
Thread is marked Solved, but no solution was found to the repeated freezes.

Tim

---

