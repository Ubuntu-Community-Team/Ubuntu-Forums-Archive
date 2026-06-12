---
title: "Skype 2.1 Beta on 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by avrono on 2010-04-30
Hi, I just upgraded my 9.04 laptop to 10.04. Skype 2.0 stopped working, crashing when a chat or call was started. So I upgraded to Skype 2.1 , which is also not working. Could this have something to do with Python and Python upgrades on 10.04 ?

---

### Post by Marc Higgins on 2010-05-01
I have a similar issue with Skype 2.1 after upgrading from 9.10 Karmic Koala to 10.04 Lucid Lynx

1) Skype sound quality seems to be substantially depreciated under Lucid

2) Skype frequnetly drops calls under Lucid

2) Skype crashes when I use the instant message feature

I tried to run it from a shell to see if there were any error messaged, it just shows "Aborted" as soon as I try to IM anyone

marc@aspireone:~$ skype
Aborted

---

### Post by vertago1 on 2010-05-01
Mine seems to be working ok, minus the fact that the sound capture is corrupted to the point where the people on the other end cannot understand me at all. I called my self to confirm. Strangely other apps like audacity work fine when I use the pulse sound device.

---

### Post by KIAaze on 2010-05-02
I have the same problem.
When I try a skype test call, it seems to work, but the playback is cut off and it just says "thank you for using skype test call" and ends abruptly.
No message is ever played back.

Using Kubuntu 10.04 64-bit.

edit:
Did a "sudo apt-get remove --purge skype" and reinstalled it. Seems to work better now. Skype test call worked, but I haven't made any real calls yet.

---

### Post by Marc Higgins on 2010-05-02
> **Marc Higgins said:**
> I have a similar issue with Skype 2.1 after upgrading from 9.10 Karmic Koala to 10.04 Lucid Lynx

1) Skype sound quality seems to be substantially depreciated under Lucid

2) Skype frequnetly drops calls under Lucid

2) Skype crashes when I use the instant message feature

I tried to run it from a shell to see if there were any error messaged, it just shows "Aborted" as soon as I try to IM anyone

marc@aspireone:~$ skype
Aborted

I just decided to wipe & load. From a clean install Skype seems to be working perfectly. I still have the old build so I will try purging & reinstalling & see if that works as well.

---

### Post by KIAaze on 2010-05-02
Well, it still has the same bugs as before: Some messages only get delivered after minutes/hours/days. :(
[http://forum.skype.com/topic/105583-chat-messages-undelivered/page__st__20](http://forum.skype.com/topic/105583-chat-messages-undelivered/page__st__20)

---

### Post by Linuxforall on 2010-05-02
Lots of popping under Skype beta, camera works but if call is cut and then re-established, camera doesn't work no more, also the ld preload hack has to be done to make the cam work, sound quality was nothing to talk about with 2.1 beta but now its abysmal with pops every few seconds. Skype beta sorely needs an upgrade for Lucid.

---

### Post by peterroots on 2010-05-02
lucid 10.04 (kubuntu)
HP g60-530us

Mic does not work with skype (or Audacity for that matter)
Purge and reinstall of skype (2.1) makes no difference

---

### Post by freesourcer on 2010-05-05
My Skype will not work at all after upgrade. I have installed and reinstalled several times (and downloded the latest verion several times) . When I try to run the program the Skype icon appears on the menu bar for a few seconds (grey only) then disappears.

---

### Post by alphacrucis2 on 2010-05-05
It works fine for me after installing in a fresh install of Lucid. Maybe the issues are being caused by stuff being left around by the Karmic --> Lucid upgrade path.

---

### Post by johnaaronrose on 2010-05-05
alphacrucis,
I've also done  a clean install of Skype (from their website of the 32 bit 8.10+ version - skype-ubuntu-intrepid_2.1.0.81-1_i386). 'Test sound' function checks out OK. 'Test call' function doesn't record my voice (from a microphone into a laptop's sound in). 'Pulse Audio Server' is shown against the Sound Device of Microphone. Any ideas?

---

### Post by johnaaronrose on 2010-05-05
Problem was due to having microphone & usb webcam (including microphone) both connected. On disconnecting web cam, 'Test Call' function worked though with low volume even though it was set to 100%.

---

### Post by thusi87 on 2010-05-05
Same problem here on 10.04. Skype crashes as it tries to sign in. Tried reinstalling, but no gain yet. 

Have anybody noticed that the .deb the skype site offers is for Hardy?? For god sakes, there are plenty of skype+ubuntu users. So upgrade the beta will ya?

---

### Post by ChrisNZ on 2010-05-09
Likewise - Upgraded to 10.04, started Skype 2.1 beta (as thats all available for linux), started a Instant message and Skype crashed. 
I have now removed it and am trying to reinstall to see if that works as some have found it does!
Yep that seemed to do the trick? However I dont have a web cam and seldom use voice over skype.

The exact version I downloaded was skype-ubuntu-intrepid_2.1.0.81-1_i386.deb from the Skype web site.
hope that helps?

---

### Post by CaronMargarete on 2010-05-13
Hoping that others may have an idea of what I can try.

Before the upgrade to 10.04 (I had koala) I had skype operating on my acer aspire laptop but without sound- everything else seemed to work fine. Before the upgrade I looked unsuccessfully for a solution, so decided to uninstall everything and complete the upgrade. Now I can't get it to install at all. I've taken the 64Bit option from the skype website (2.1 beta 2 for linux), once it downloaded it said that the files were corrupted. So I attempted to download again, same deal. 

I've checked to see what skype things I might have downloaded previously and saw nothing in the package manager to suggest a problem. I'm now at a loss as to how to get it loaded and working.

Ideas? (please keep tech language to a stupid-simplicity and be clear exactly what I need to do/ look for, I'm still learning all-things-ubuntu). Cheers.

---

### Post by raygj on 2010-05-13
> **CaronMargarete said:**
> Hoping that others may have an idea of what I can try.

Before the upgrade to 10.04 (I had koala) I had skype operating on my acer aspire laptop but without sound- everything else seemed to work fine. Before the upgrade I looked unsuccessfully for a solution, so decided to uninstall everything and complete the upgrade. Now I can't get it to install at all. I've taken the 64Bit option from the skype website (2.1 beta 2 for linux), once it downloaded it said that the files were corrupted. So I attempted to download again, same deal. 

I've checked to see what skype things I might have downloaded previously and saw nothing in the package manager to suggest a problem. I'm now at a loss as to how to get it loaded and working.

Ideas? (please keep tech language to a stupid-simplicity and be clear exactly what I need to do/ look for, I'm still learning all-things-ubuntu). Cheers.

give this a go
[http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script")

---

### Post by CaronMargarete on 2010-05-15
> **raygj said:**
> give this a go
[http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script](http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script)

Thanks, will do. :P

Can you suggest which version of Skype I should download (and from where), this link seems to fix the sound problem, but not the one with skype downloading properly...

---

### Post by pduijves on 2010-05-26
> **freesourcer said:**
> My Skype will not work at all after upgrade. I have installed and reinstalled several times (and downloded the latest verion several times) . When I try to run the program the Skype icon appears on the menu bar for a few seconds (grey only) then disappears.

same problem for me.

i managed to fix it by downloading *skype-ubuntu-intrepid_2.1.0.81-1_i386.deb* via
[http://www.skype.com/go/getskype-linux-beta-ubuntu-32]("http://www.skype.com/go/getskype-linux-beta-ubuntu-32") and uninstalling previous version of skype:

sudo apt-get remove --purge skype
sudo dpkg -i skype-ubuntu-intrepid_2.1.0.81-1_i386.deb

also take into account that the audio for skype does not work in combination with some other applications that use audio. for example: i need to quit the Amarok audio player in order to hear sound in skype...

---

### Post by CaronMargarete on 2010-05-26
> **pduijves said:**
> same problem for me.

i managed to fix it by downloading *skype-ubuntu-intrepid_2.1.0.81-1_i386.deb* via
[http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32) and uninstalling previous version of skype:

sudo apt-get remove --purge skype
sudo dpkg -i skype-ubuntu-intrepid_2.1.0.81-1_i386.deb

also take into account that the audio for skype does not work in combination with some other applications that use audio. for example: i need to quit the Amarok audio player in order to hear sound in skype...

I tried to do as you've suggested pduijives but I've hit a snag. Perhaps it was the process I followed since I don't much about the terminal. 

First, I followed your first command and it turns out I've already successfully removed it. Then I tried to do the second and as you'll see below I got an error. So I downloaded the link and tried to run it but got an error: wrong architecture 'i386'; I then tried your second command without success either. 

```
caz@Jamie:~$ sudo apt-get remove --purge skype
[sudo] password for caz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libfreebob0 libopal3.6.4 libxml++2.6-2 libgda-4.0-common
  kdebase-runtime-data-common libqt4-phonon libxklavier15 libicu40
  latex-xft-fonts libgda-4.0-4 libgpg-error-dev libknotificationitem1
  libcompress-bzip2-perl libgupnp-1.0-2 xulrunner-1.9.1-gnome-support libdns53
  libindicate-gtk1 gnome-blackjack libiso9660-5 libass3 qt3-assistant
  python-gda libexiv2-5 python-gdl libkrb5-dev libcln5 librasqal1 python2.5
  libisccc50 khelpcenter4 liblzma0 libpt2.6.4-plugins libindicate3 libx264-67
  python-gtksourceview linux-backports-modules-2.6.31-20-generic python-gksu2
  libgdl-1-common kde-icons-oxygen python-nautilusburn liblwres50 libcelt0
  qcad-doc raptor-utils xulrunner-1.9.1 qcad-data python-gtkmozembed
  libtasn1-3-dev libntfs-3g54 libbind9-50 zlib1g-dev libcups2-dev libffado1
  python-gtkspell libgdata5 libgcrypt11-dev qt3-doc libpt2.6.4 libisccfg50
  rhino redland-utils firefox-3.5-gnome-support libgnutls-dev libisc50
  kdebase-runtime-bin-kde4 libjline-java libgssdp-1.0-1 libgdl-1-3 libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
caz@Jamie:~$ sudo dpkg -i skype-ubuntu-intrepid_2.1.0.81-1_i386.deb
dpkg: error processing skype-ubuntu-intrepid_2.1.0.81-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype-ubuntu-intrepid_2.1.0.81-1_i386.deb
caz@Jamie:~$ sudo dpkg -i skype-ubuntu-intrepid_2.1.0.81-1_i386.deb
[sudo] password for caz: 
dpkg: error processing skype-ubuntu-intrepid_2.1.0.81-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype-ubuntu-intrepid_2.1.0.81-1_i386.deb
caz@Jamie:~$ 
```Recommendations?

---

### Post by KIAaze on 2010-05-26
I think you didn't run the command from the directory containing skype-ubuntu-intrepid_2.1.0.81-1_i386.deb.

But there is an easier than using dpkg: Just double-click on the .deb file you downloaded.
It should open it with gdebi-gtk and offer you to install it.

Otherwise, if you still want to do it by command-line:
Assuming you downloaded into the ~/Downloads directory, run:
```
cd ~/Downloads
sudo dpkg -i skype-ubuntu-intrepid_2.1.0.81-1_i386.deb

```

If you want to learn more about using the command-line:
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Basics of installing software:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[https://help.ubuntu.com/community/InstallingSoftware#Installing%20downloaded%20packages](https://help.ubuntu.com/community/InstallingSoftware#Installing%20downloaded%20packages)

---

### Post by Automat2 on 2010-05-27
My problem with Skype comes with the icon. I open Skype and log on. If I close the app -click on the cross- rather than minimize, it seems to have disappeared from the desktop. It's nowhere to be found.

But if I try to open it again, doesn't let me because it is running on the background and can't open the same app twice.

On Ubuntu 9.10, the Skype icon on the top panel appeared on the top panel, ready to open should I needed it.

Does anybody have found the same problem?

---

### Post by CaronMargarete on 2010-06-06
> **KIAaze said:**
> I think you didn't run the command from the directory containing skype-ubuntu-intrepid_2.1.0.81-1_i386.deb.

But there is an easier than using dpkg: Just double-click on the .deb file you downloaded.
It should open it with gdebi-gtk and offer you to install it.


KIAaza, thanks you were right. I downloaded it again and it worked a charm. 

New problem though- my microphone doesn't seem to work. I'll start a new thread though because it seems that the Sound Recorder doesn't work either.

Thanks again.

---

### Post by Irony on 2010-06-06
You can install skype from the repositories, make sure canonical is enabled.

Also make sure your microphone is enabled by clicking the volume button and clicking sound preferences then hitting the input tab and unticking mute.

---

### Post by giaverim on 2010-06-11
I had the same problem after the upgrade from 8.10 to Lucid Lynx . I have removed it with  "sudo apt-get remove --purge skype"and now looks fine ...Thanks !!

---

### Post by CaronMargarete on 2010-06-11
> **Irony said:**
> You can install skype from the repositories, make sure canonical is enabled.

Also make sure your microphone is enabled by clicking the volume button and clicking sound preferences then hitting the input tab and unticking mute.

Irony, thanks for your input. There is no sound icon in my tray, nothing is muted. I have to go into GNOME Alsa Mixer every time I turn my laptop on to up the speaker again. It seems like a simple case of my computer not recognising my mic but I don't know how to fix it. And the sound, I'm sure that's just a tweak too.

This has nothing to do with skype but my laptop. See thread:
[http://ubuntuforums.org/showthread.php?p=9417793#post9417793](http://ubuntuforums.org/showthread.php?p=9417793#post9417793)

---

### Post by minhajmsm on 2010-06-12
mine working perfectly... after installing a fresh copy through software center,,,, but if i connect the DSL router through USB the cam doesn't function,, but for cable it works fine.. Had a audio problem but changed some settings under audio options... works 5n.... 


** ANOTHER AGE MUST BE THE JUDGE**{Charles Babbage}

---

### Post by Hookheathen on 2010-08-21
May I add my (quite dire crash problems) following upgrade to Lucid 10.04 (from Hardy) and multiple purging and reinstalling of Skype Beta 2.1.0.81(both from Medibuntu repository as well as from Skype site). 

My IBM T42 laptop experiences total system failure(!) dire crashes after approx a minute into a Skype voice call. The screen goes black, no interfaces work and the last sound hangs coming through the speakers. The only way to restart is hard boot - power off/on. Can anyone please advise how to overcome this critical issue. If any consolation, this seems to be the only problem I have encountered so far with the Lucid upgrade!


Prior to upgrade all worked fine.

Pentium M 1.7 GHz
Memory: 1001.9MiB

---

### Post by KIAaze on 2010-08-21
Things that may help you or others debug your problem:
-Does it only happen with Skype voice call?
-Have you tried it with other distros or earlier Ubuntu releases?
-Try different sound systems: [http://www.skype.com/intl/en-us/support/user-guides/sound-setup-linux/](http://www.skype.com/intl/en-us/support/user-guides/sound-setup-linux/)
-Check the log files after a hard reboot, especially /var/log/daemon.log  /var/log/kern.log  /var/log/messages  /var/log/syslog
-Check the output of "dmesg" after a hard reboot
-Store the command-line output of skype with ```
skype 1>~/skype.log 2>&1
```
-Does switching virtual terminals with ctrl+alt+F1/F2/etc still work?
-Check if the kernel is still responding by trying the REISUB combination: [http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
-Check that it's not overheating by monitoring the temperature

---

### Post by Hookheathen on 2010-08-21
Thank you KIAaze, will work through your list immediately following the next crash. But in the meantime, to answer your questions:-
-Does it only happen with Skype voice call? 
[COLOR="DarkRed"]Only Skype voice calls after about 5 minutes of conversation.[/COLOR]
-Have you tried it with other distros or earlier Ubuntu releases?
[COLOR="DarkRed"]Worked fine with both earlier Ubuntu releases[/COLOR]
-Does switching virtual terminals with ctrl+alt+F1/F2/etc still work?
[COLOR="DarkRed"]Hmm, not sure about that. but can switch using Terminal[/COLOR]
-Check if the kernel is still responding by trying the REISUB combination:
[COLOR="DarkRed"]Kernel appears to work fine[/COLOR]
 [http://kember.net/articles/reisub-th...linux-restart/](http://kember.net/articles/reisub-th...linux-restart/)
-Check that it's not overheating by monitoring the temperature
[COLOR="DarkRed"]Temp running around 40 degs[/COLOR]
[COLOR="DarkRed"]I am wondering whether Power Management settings could have upset things. On Mains Power Actions, I had a blank appear in the section for "Put computer to sleep sleep when inactive for" rather than "Never"[/COLOR]

---

### Post by Hookheathen on 2010-08-22
I have just experienced a similar failure on another IBM laptop, here is the syslog output as requested:-

Aug 22 11:52:16 michael-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="671" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Aug 22 11:52:16 michael-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="671" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Aug 22 11:53:15 michael-laptop anacron[886]: Job `cron.daily' terminated
Aug 22 11:53:15 michael-laptop anacron[886]: Normal exit (1 job run)
Aug 22 11:59:25 michael-laptop pulseaudio[1721]: ratelimit.c: 1 events suppressed
Aug 22 11:59:52 michael-laptop pulseaudio[1721]: ratelimit.c: 1 events suppressed
Aug 22 12:02:31 michael-laptop pulseaudio[1721]: ratelimit.c: 1 events suppressed
Aug 22 12:07:17 michael-laptop pulseaudio[1721]: ratelimit.c: 1 events suppressed
Aug 22 12:08:52 michael-laptop pulseaudio[1721]: ratelimit.c: 1 events suppressed
Aug 22 12:10:06 michael-laptop pulseaudio[1721]: last message repeated 2 times
Aug 22 12:13:06 michael-laptop pulseaudio[1721]: ratelimit.c: 5 events suppressed
Aug 22 12:21:07 michael-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Aug 22 12:21:07 michael-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="691" x-info="http://www.rsyslog.com"] (re)start
Aug 22 12:21:07 michael-laptop rsyslogd: rsyslogd's groupid changed to 103
Aug 22 12:21:07 michael-laptop rsyslogd: rsyslogd's userid changed to 102
Aug 22 12:21:07 michael-laptop rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 (Ubuntu 2.6.32-24.41-generic 2.6.32.15+drm33.5)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] KERNEL supported cpus:
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   Intel GenuineIntel
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   AMD AuthenticAMD
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   NSC Geode by NSC
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   Cyrix CyrixInstead
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   Centaur CentaurHauls
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   Transmeta GenuineTMx86
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   Transmeta TransmetaCPU
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   UMC UMC UMC UMC
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff60000 (usable)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  BIOS-e820: 000000003ff60000 - 000000003ff77000 (ACPI data)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  BIOS-e820: 000000003ff77000 - 000000003ff79000 (ACPI NVS)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] DMI present.
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] last_pfn = 0x3ff60 max_arch_pfn = 0x100000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] MTRR default type: uncachable
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] MTRR fixed ranges enabled:
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   00000-9FFFF write-back
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   A0000-BFFFF uncachable
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   C0000-CFFFF write-protect
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   D0000-DBFFF uncachable
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   DC000-DFFFF write-back
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   E0000-FFFFF write-protect
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] MTRR variable ranges enabled:
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   1 base 03FF80000 mask FFFF80000 uncachable
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   2 disabled
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   3 disabled
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   4 disabled
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   5 disabled
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   6 disabled
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   7 disabled
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] PAT not supported by CPU.
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] modified physical RAM map:
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  modified: 0000000000100000 - 000000003ff60000 (usable)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  modified: 000000003ff60000 - 000000003ff77000 (ACPI data)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  modified: 000000003ff77000 - 000000003ff79000 (ACPI NVS)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  modified: 000000003ff80000 - 0000000040000000 (reserved)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  modified: 00000000ff800000 - 0000000100000000 (reserved)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] RAMDISK: 3786e000 - 37fef18c
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Allocated new RAMDISK: 008e2000 - 0106318c
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Move RAMDISK from 000000003786e000 - 0000000037fef18b to 008e2000 - 0106318b
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] ACPI: RSDP 000f6d70 00024 (v02 IBM   )
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] ACPI: XSDT 3ff6a6cd 0004C (v01 IBM    TP-1R    00003190  LTP 00000000)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] ACPI: FACP 3ff6a800 000F4 (v03 IBM    TP-1R    00003190 IBM  00000001)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 (20090903/tbfadt-526)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 000000000000102C/0 (20090903/tbfadt-557)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] ACPI: DSDT 3ff6a9e7 0C4D5 (v01 IBM    TP-1R    00003190 MSFT 0100000E)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] ACPI: FACS 3ff78000 00040
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] ACPI: SSDT 3ff6a9b4 00033 (v01 IBM    TP-1R    00003190 MSFT 0100000E)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] ACPI: ECDT 3ff76ebc 00052 (v01 IBM    TP-1R    00003190 IBM  00000001)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] ACPI: TCPA 3ff76f0e 00032 (v01 IBM    TP-1R    00003190 PTL  00000001)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] ACPI: BOOT 3ff76fd8 00028 (v01 IBM    TP-1R    00003190  LTP 00000001)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] 135MB HIGHMEM available.
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] 887MB LOWMEM available.
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   low ram: 0 - 377fe000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   #5 [00008de000 - 00008e10f4]              BRK ==> [00008de000 - 00008e10f4]
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   #7 [00008e2000 - 000106318c]      NEW RAMDISK ==> [00008e2000 - 000106318c]
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Zone PFN ranges:
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003ff60
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Movable zone start PFN for each node
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] early_node_map[3] active PFN ranges
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0003ff60
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] On node 0 totalpages: 261883
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] free_area_init_node: node 0, pgdat c079a780, node_mem_map c1065000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   HighMem zone: 271 pages used for memmap
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]   HighMem zone: 34387 pages, LIFO batch:7
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Using APIC driver default
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] APIC: disable apic facility
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] nr_irqs_gsi: 16
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bf800000)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36056 r0 d21288 u4194304
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] pcpu-alloc: [0] 0 
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259836
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Kernel command line: root=UUID=8d473178-9948-4341-89f8-907bf6c71e13 ro quiet splash 
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Initializing CPU#0
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] allocated 5239680 bytes of page_cgroup
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003ff60)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Memory: 1017156k/1047936k available (4679k kernel code, 29976k reserved, 2124k data, 660k init, 138632k highmem)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] virtual kernel memory layout:
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Hierarchical RCU implementation.
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Extended CMOS year: 2000
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Console: colour VGA+ 80x25
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] console [tty0] enabled
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Aug 22 12:21:07 michael-laptop kernel: [    0.000000] Detected 1698.669 MHz processor.
Aug 22 12:21:07 michael-laptop kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3397.33 BogoMIPS (lpj=6794676)
Aug 22 12:21:07 michael-laptop kernel: [    0.004025] Security Framework initialized
Aug 22 12:21:07 michael-laptop kernel: [    0.004054] AppArmor: AppArmor initialized
Aug 22 12:21:07 michael-laptop kernel: [    0.004063] Mount-cache hash table entries: 512
Aug 22 12:21:07 michael-laptop kernel: [    0.004204] Initializing cgroup subsys ns
Aug 22 12:21:07 michael-laptop kernel: [    0.004209] Initializing cgroup subsys cpuacct
Aug 22 12:21:07 michael-laptop kernel: [    0.004214] Initializing cgroup subsys memory
Aug 22 12:21:07 michael-laptop kernel: [    0.004225] Initializing cgroup subsys devices
Aug 22 12:21:07 michael-laptop kernel: [    0.004228] Initializing cgroup subsys freezer
Aug 22 12:21:07 michael-laptop kernel: [    0.004231] Initializing cgroup subsys net_cls
Aug 22 12:21:07 michael-laptop kernel: [    0.004259] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 22 12:21:07 michael-laptop kernel: [    0.004262] CPU: L2 cache: 2048K
Aug 22 12:21:07 michael-laptop kernel: [    0.004267] mce: CPU supports 5 MCE banks
Aug 22 12:21:07 michael-laptop kernel: [    0.004285] Performance Events: 
Aug 22 12:21:07 michael-laptop kernel: [    0.004288] no APIC, boot with the "lapic" boot parameter to force-enable it.
Aug 22 12:21:07 michael-laptop kernel: [    0.004291] no hardware sampling interrupt available.
Aug 22 12:21:07 michael-laptop kernel: [    0.004293] p6 PMU driver.
Aug 22 12:21:07 michael-laptop kernel: [    0.004300] ... version:                0
Aug 22 12:21:07 michael-laptop kernel: [    0.004302] ... bit width:              32
Aug 22 12:21:07 michael-laptop kernel: [    0.004305] ... generic registers:      2
Aug 22 12:21:07 michael-laptop kernel: [    0.004307] ... value mask:             00000000ffffffff
Aug 22 12:21:07 michael-laptop kernel: [    0.004310] ... max period:             000000007fffffff
Aug 22 12:21:07 michael-laptop kernel: [    0.004312] ... fixed-purpose events:   0
Aug 22 12:21:07 michael-laptop kernel: [    0.004314] ... event mask:             0000000000000003
Aug 22 12:21:07 michael-laptop kernel: [    0.004320] Checking 'hlt' instruction... OK.
Aug 22 12:21:07 michael-laptop kernel: [    0.020948] SMP alternatives: switching to UP code
Aug 22 12:21:07 michael-laptop kernel: [    0.028869] Freeing SMP alternatives: 19k freed
Aug 22 12:21:07 michael-laptop kernel: [    0.028878] ACPI: Core revision 20090903
Aug 22 12:21:07 michael-laptop kernel: [    0.048343] ACPI: setting ELCR to 0200 (from 0800)
Aug 22 12:21:07 michael-laptop kernel: [    0.052009] ftrace: converting mcount calls to 0f 1f 44 00 00
Aug 22 12:21:07 michael-laptop kernel: [    0.052016] ftrace: allocating 21780 entries in 43 pages
Aug 22 12:21:07 michael-laptop kernel: [    0.056080] Enabling APIC mode:  Flat.  Using 0 I/O APICs
Aug 22 12:21:07 michael-laptop kernel: [    0.056086] weird, boot CPU (#0) not listed by the BIOS.
Aug 22 12:21:07 michael-laptop kernel: [    0.056088] SMP motherboard not detected.
Aug 22 12:21:07 michael-laptop kernel: [    0.056092] Local APIC not detected. Using dummy APIC emulation.
Aug 22 12:21:07 michael-laptop kernel: [    0.056094] SMP disabled
Aug 22 12:21:07 michael-laptop kernel: [    0.056247] Brought up 1 CPUs
Aug 22 12:21:07 michael-laptop kernel: [    0.056250] Total of 1 processors activated (3397.33 BogoMIPS).
Aug 22 12:21:07 michael-laptop kernel: [    0.060054] CPU0 attaching NULL sched-domain.
Aug 22 12:21:07 michael-laptop kernel: [    0.060203] devtmpfs: initialized
Aug 22 12:21:07 michael-laptop kernel: [    0.060603] regulator: core version 0.5
Aug 22 12:21:07 michael-laptop kernel: [    0.060627] Time: 12:20:34  Date: 08/22/10
Aug 22 12:21:07 michael-laptop kernel: [    0.060678] NET: Registered protocol family 16
Aug 22 12:21:07 michael-laptop kernel: [    0.060814] EISA bus registered
Aug 22 12:21:07 michael-laptop kernel: [    0.060824] ACPI: bus type pci registered
Aug 22 12:21:07 michael-laptop kernel: [    0.061034] PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=8
Aug 22 12:21:07 michael-laptop kernel: [    0.061037] PCI: Using configuration type 1 for base access
Aug 22 12:21:07 michael-laptop kernel: [    0.062094] bio: create slab <bio-0> at 0
Aug 22 12:21:07 michael-laptop kernel: [    0.063287] ACPI: EC: EC description table is found, configuring boot EC
Aug 22 12:21:07 michael-laptop kernel: [    0.073350] ACPI: Interpreter enabled
Aug 22 12:21:07 michael-laptop kernel: [    0.073359] ACPI: (supports S0 S3 S4 S5)
Aug 22 12:21:07 michael-laptop kernel: [    0.073384] ACPI: Using PIC for interrupt routing
Aug 22 12:21:07 michael-laptop kernel: [    0.081747] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Aug 22 12:21:07 michael-laptop kernel: [    0.081747] ACPI: Power Resource [PUBS] (on)
Aug 22 12:21:07 michael-laptop kernel: [    0.085058] ACPI: ACPI Dock Station Driver: 3 docks/bays found
Aug 22 12:21:07 michael-laptop kernel: [    0.085089] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 22 12:21:07 michael-laptop kernel: [    0.085134] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.085248] pci 0000:00:1d.0: reg 20 io port: [0x1800-0x181f]
Aug 22 12:21:07 michael-laptop kernel: [    0.085301] pci 0000:00:1d.1: reg 20 io port: [0x1820-0x183f]
Aug 22 12:21:07 michael-laptop kernel: [    0.085354] pci 0000:00:1d.2: reg 20 io port: [0x1840-0x185f]
Aug 22 12:21:07 michael-laptop kernel: [    0.085414] pci 0000:00:1d.7: reg 10 32bit mmio: [0xc0000000-0xc00003ff]
Aug 22 12:21:07 michael-laptop kernel: [    0.085471] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Aug 22 12:21:07 michael-laptop kernel: [    0.085477] pci 0000:00:1d.7: PME# disabled
Aug 22 12:21:07 michael-laptop kernel: [    0.085566] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
Aug 22 12:21:07 michael-laptop kernel: [    0.085571] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
Aug 22 12:21:07 michael-laptop kernel: [    0.085595] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
Aug 22 12:21:07 michael-laptop kernel: [    0.085602] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
Aug 22 12:21:07 michael-laptop kernel: [    0.085610] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
Aug 22 12:21:07 michael-laptop kernel: [    0.085617] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
Aug 22 12:21:07 michael-laptop kernel: [    0.085625] pci 0000:00:1f.1: reg 20 io port: [0x1860-0x186f]
Aug 22 12:21:07 michael-laptop kernel: [    0.085632] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
Aug 22 12:21:07 michael-laptop kernel: [    0.085683] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
Aug 22 12:21:07 michael-laptop kernel: [    0.085727] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
Aug 22 12:21:07 michael-laptop kernel: [    0.085734] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
Aug 22 12:21:07 michael-laptop kernel: [    0.085741] pci 0000:00:1f.5: reg 18 32bit mmio: [0xc0000c00-0xc0000dff]
Aug 22 12:21:07 michael-laptop kernel: [    0.085749] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xc0000800-0xc00008ff]
Aug 22 12:21:07 michael-laptop kernel: [    0.085778] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Aug 22 12:21:07 michael-laptop kernel: [    0.085783] pci 0000:00:1f.5: PME# disabled
Aug 22 12:21:07 michael-laptop kernel: [    0.085813] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
Aug 22 12:21:07 michael-laptop kernel: [    0.085820] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
Aug 22 12:21:07 michael-laptop kernel: [    0.085857] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
Aug 22 12:21:07 michael-laptop kernel: [    0.085862] pci 0000:00:1f.6: PME# disabled
Aug 22 12:21:07 michael-laptop kernel: [    0.085898] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xe0000000-0xe7ffffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.085905] pci 0000:01:00.0: reg 14 io port: [0x3000-0x30ff]
Aug 22 12:21:07 michael-laptop kernel: [    0.085911] pci 0000:01:00.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.085926] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.085946] pci 0000:01:00.0: supports D1 D2
Aug 22 12:21:07 michael-laptop kernel: [    0.085981] pci 0000:00:01.0: bridge io port: [0x3000-0x3fff]
Aug 22 12:21:07 michael-laptop kernel: [    0.085985] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.085989] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe0000000-0xe7ffffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.086025] pci 0000:02:00.0: reg 10 32bit mmio: [0xb0000000-0xb0000fff]
Aug 22 12:21:07 michael-laptop kernel: [    0.086044] pci 0000:02:00.0: supports D1 D2
Aug 22 12:21:07 michael-laptop kernel: [    0.086047] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 22 12:21:07 michael-laptop kernel: [    0.086051] pci 0000:02:00.0: PME# disabled
Aug 22 12:21:07 michael-laptop kernel: [    0.086086] pci 0000:02:00.1: reg 10 32bit mmio: [0xb1000000-0xb1000fff]
Aug 22 12:21:07 michael-laptop kernel: [    0.086105] pci 0000:02:00.1: supports D1 D2
Aug 22 12:21:07 michael-laptop kernel: [    0.086108] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot D3cold
Aug 22 12:21:07 michael-laptop kernel: [    0.086113] pci 0000:02:00.1: PME# disabled
Aug 22 12:21:07 michael-laptop kernel: [    0.086152] pci 0000:02:01.0: reg 10 32bit mmio: [0xc0240000-0xc025ffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.086160] pci 0000:02:01.0: reg 14 32bit mmio: [0xc0200000-0xc020ffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.086167] pci 0000:02:01.0: reg 18 io port: [0x8000-0x803f]
Aug 22 12:21:07 michael-laptop kernel: [    0.086187] pci 0000:02:01.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.086207] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
Aug 22 12:21:07 michael-laptop kernel: [    0.086211] pci 0000:02:01.0: PME# disabled
Aug 22 12:21:07 michael-laptop kernel: [    0.086244] pci 0000:02:02.0: reg 10 32bit mmio: [0xc0210000-0xc021ffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.086324] pci 0000:00:1e.0: transparent bridge
Aug 22 12:21:07 michael-laptop kernel: [    0.086330] pci 0000:00:1e.0: bridge io port: [0x4000-0x8fff]
Aug 22 12:21:07 michael-laptop kernel: [    0.086335] pci 0000:00:1e.0: bridge 32bit mmio: [0xc0200000-0xcfffffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.086340] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xe8000000-0xefffffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.086380] pci_bus 0000:00: on NUMA node 0
Aug 22 12:21:07 michael-laptop kernel: [    0.086385] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 22 12:21:07 michael-laptop kernel: [    0.086439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Aug 22 12:21:07 michael-laptop kernel: [    0.086469] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Aug 22 12:21:07 michael-laptop kernel: [    0.090920] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
Aug 22 12:21:07 michael-laptop kernel: [    0.091117] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
Aug 22 12:21:07 michael-laptop kernel: [    0.091311] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
Aug 22 12:21:07 michael-laptop kernel: [    0.091504] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
Aug 22 12:21:07 michael-laptop kernel: [    0.091678] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Aug 22 12:21:07 michael-laptop kernel: [    0.091852] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Aug 22 12:21:07 michael-laptop kernel: [    0.092040] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Aug 22 12:21:07 michael-laptop kernel: [    0.092235] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
Aug 22 12:21:07 michael-laptop kernel: [    0.092373] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Aug 22 12:21:07 michael-laptop kernel: [    0.092378] vgaarb: loaded
Aug 22 12:21:07 michael-laptop kernel: [    0.092512] SCSI subsystem initialized
Aug 22 12:21:07 michael-laptop kernel: [    0.092553] libata version 3.00 loaded.
Aug 22 12:21:07 michael-laptop kernel: [    0.092630] usbcore: registered new interface driver usbfs
Aug 22 12:21:07 michael-laptop kernel: [    0.092645] usbcore: registered new interface driver hub
Aug 22 12:21:07 michael-laptop kernel: [    0.092672] usbcore: registered new device driver usb
Aug 22 12:21:07 michael-laptop kernel: [    0.092811] ACPI: WMI: Mapper loaded
Aug 22 12:21:07 michael-laptop kernel: [    0.092813] PCI: Using ACPI for IRQ routing
Aug 22 12:21:07 michael-laptop kernel: [    0.093098] NetLabel: Initializing
Aug 22 12:21:07 michael-laptop kernel: [    0.093100] NetLabel:  domain hash size = 128
Aug 22 12:21:07 michael-laptop kernel: [    0.093102] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 22 12:21:07 michael-laptop kernel: [    0.093118] NetLabel:  unlabeled traffic allowed by default
Aug 22 12:21:07 michael-laptop kernel: [    0.093157] Switching to clocksource tsc
Aug 22 12:21:07 michael-laptop kernel: [    0.095399] AppArmor: AppArmor Filesystem Enabled
Aug 22 12:21:07 michael-laptop kernel: [    0.095411] pnp: PnP ACPI init
Aug 22 12:21:07 michael-laptop kernel: [    0.095422] ACPI: bus type pnp registered
Aug 22 12:21:07 michael-laptop kernel: [    0.097673] pnp: PnP ACPI: found 13 devices
Aug 22 12:21:07 michael-laptop kernel: [    0.097676] ACPI: ACPI bus type pnp unregistered
Aug 22 12:21:07 michael-laptop kernel: [    0.097680] PnPBIOS: Disabled by ACPI PNP
Aug 22 12:21:07 michael-laptop kernel: [    0.097691] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097695] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097699] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097702] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097706] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097709] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097713] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097717] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097720] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097724] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097728] system 00:00: iomem range 0xec000-0xeffff could not be reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097731] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097735] system 00:00: iomem range 0x100000-0x3fffffff could not be reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097739] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097747] system 00:02: ioport range 0x1000-0x107f has been reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097751] system 00:02: ioport range 0x1180-0x11bf has been reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097754] system 00:02: ioport range 0x15e0-0x15ef has been reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097758] system 00:02: ioport range 0x1600-0x162f has been reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097761] system 00:02: ioport range 0x1632-0x167f has been reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.097765] system 00:02: ioport range 0x1630-0x1631 has been reserved
Aug 22 12:21:07 michael-laptop kernel: [    0.132460] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Aug 22 12:21:07 michael-laptop kernel: [    0.132464] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
Aug 22 12:21:07 michael-laptop kernel: [    0.132469] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
Aug 22 12:21:07 michael-laptop kernel: [    0.132474] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xe7ffffff
Aug 22 12:21:07 michael-laptop kernel: [    0.132484] pci 0000:02:00.0: CardBus bridge, secondary bus 0000:03
Aug 22 12:21:07 michael-laptop kernel: [    0.132487] pci 0000:02:00.0:   IO window: 0x004000-0x0040ff
Aug 22 12:21:07 michael-laptop kernel: [    0.132492] pci 0000:02:00.0:   IO window: 0x004400-0x0044ff
Aug 22 12:21:07 michael-laptop kernel: [    0.132497] pci 0000:02:00.0:   PREFETCH window: 0xe8000000-0xebffffff
Aug 22 12:21:07 michael-laptop kernel: [    0.132502] pci 0000:02:00.0:   MEM window: 0xc4000000-0xc7ffffff
Aug 22 12:21:07 michael-laptop kernel: [    0.132507] pci 0000:02:00.1: CardBus bridge, secondary bus 0000:07
Aug 22 12:21:07 michael-laptop kernel: [    0.132510] pci 0000:02:00.1:   IO window: 0x004800-0x0048ff
Aug 22 12:21:07 michael-laptop kernel: [    0.132515] pci 0000:02:00.1:   IO window: 0x004c00-0x004cff
Aug 22 12:21:07 michael-laptop kernel: [    0.132520] pci 0000:02:00.1:   PREFETCH window: 0xec000000-0xefffffff
Aug 22 12:21:07 michael-laptop kernel: [    0.132525] pci 0000:02:00.1:   MEM window: 0xc8000000-0xcbffffff
Aug 22 12:21:07 michael-laptop kernel: [    0.132530] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
Aug 22 12:21:07 michael-laptop kernel: [    0.132534] pci 0000:00:1e.0:   IO window: 0x4000-0x8fff
Aug 22 12:21:07 michael-laptop kernel: [    0.132540] pci 0000:00:1e.0:   MEM window: 0xc0200000-0xcfffffff
Aug 22 12:21:07 michael-laptop kernel: [    0.132545] pci 0000:00:1e.0:   PREFETCH window: 0xe8000000-0xefffffff
Aug 22 12:21:07 michael-laptop kernel: [    0.132563] pci 0000:00:1e.0: setting latency timer to 64
Aug 22 12:21:07 michael-laptop kernel: [    0.132901] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [    0.132904] PCI: setting IRQ 11 as level-triggered
Aug 22 12:21:07 michael-laptop kernel: [    0.132909] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [    0.133238] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [    0.133243] pci 0000:02:00.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [    0.133250] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133253] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133257] pci_bus 0000:01: resource 0 io:  [0x3000-0x3fff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133260] pci_bus 0000:01: resource 1 mem: [0xc0100000-0xc01fffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133263] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xe7ffffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133267] pci_bus 0000:02: resource 0 io:  [0x4000-0x8fff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133270] pci_bus 0000:02: resource 1 mem: [0xc0200000-0xcfffffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133273] pci_bus 0000:02: resource 2 pref mem [0xe8000000-0xefffffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133277] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133280] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133283] pci_bus 0000:03: resource 0 io:  [0x4000-0x40ff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133286] pci_bus 0000:03: resource 1 io:  [0x4400-0x44ff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133289] pci_bus 0000:03: resource 2 pref mem [0xe8000000-0xebffffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133293] pci_bus 0000:03: resource 3 mem: [0xc4000000-0xc7ffffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133296] pci_bus 0000:07: resource 0 io:  [0x4800-0x48ff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133299] pci_bus 0000:07: resource 1 io:  [0x4c00-0x4cff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133302] pci_bus 0000:07: resource 2 pref mem [0xec000000-0xefffffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133306] pci_bus 0000:07: resource 3 mem: [0xc8000000-0xcbffffff]
Aug 22 12:21:07 michael-laptop kernel: [    0.133339] NET: Registered protocol family 2
Aug 22 12:21:07 michael-laptop kernel: [    0.133436] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 22 12:21:07 michael-laptop kernel: [    0.133793] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 22 12:21:07 michael-laptop kernel: [    0.134802] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 22 12:21:07 michael-laptop kernel: [    0.135537] TCP: Hash tables configured (established 131072 bind 65536)
Aug 22 12:21:07 michael-laptop kernel: [    0.135541] TCP reno registered
Aug 22 12:21:07 michael-laptop kernel: [    0.135679] NET: Registered protocol family 1
Aug 22 12:21:07 michael-laptop kernel: [    0.135780] pci 0000:01:00.0: Boot video device
Aug 22 12:21:07 michael-laptop kernel: [    0.135919] Simple Boot Flag at 0x35 set to 0x1
Aug 22 12:21:07 michael-laptop kernel: [    0.136022] cpufreq-nforce2: No nForce2 chipset.
Aug 22 12:21:07 michael-laptop kernel: [    0.136058] Scanning for low memory corruption every 60 seconds
Aug 22 12:21:07 michael-laptop kernel: [    0.136220] audit: initializing netlink socket (disabled)
Aug 22 12:21:07 michael-laptop kernel: [    0.136243] type=2000 audit(1282479634.134:1): initialized
Aug 22 12:21:07 michael-laptop kernel: [    0.148528] Trying to unpack rootfs image as initramfs...
Aug 22 12:21:07 michael-laptop kernel: [    0.163350] highmem bounce pool size: 64 pages
Aug 22 12:21:07 michael-laptop kernel: [    0.163358] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Aug 22 12:21:07 michael-laptop kernel: [    0.165188] VFS: Disk quotas dquot_6.5.2
Aug 22 12:21:07 michael-laptop kernel: [    0.165260] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 22 12:21:07 michael-laptop kernel: [    0.170980] fuse init (API version 7.13)
Aug 22 12:21:07 michael-laptop kernel: [    0.171099] msgmni has been set to 1716
Aug 22 12:21:07 michael-laptop kernel: [    0.171385] alg: No test for stdrng (krng)
Aug 22 12:21:07 michael-laptop kernel: [    0.171450] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug 22 12:21:07 michael-laptop kernel: [    0.171454] io scheduler noop registered
Aug 22 12:21:07 michael-laptop kernel: [    0.171457] io scheduler anticipatory registered
Aug 22 12:21:07 michael-laptop kernel: [    0.171459] io scheduler deadline registered
Aug 22 12:21:07 michael-laptop kernel: [    0.171504] io scheduler cfq registered (default)
Aug 22 12:21:07 michael-laptop kernel: [    0.171654] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 22 12:21:07 michael-laptop kernel: [    0.171682] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 22 12:21:07 michael-laptop kernel: [    0.171966] ACPI: AC Adapter [AC] (on-line)
Aug 22 12:21:07 michael-laptop kernel: [    0.172046] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Aug 22 12:21:07 michael-laptop kernel: [    0.172422] ACPI: Lid Switch [LID]
Aug 22 12:21:07 michael-laptop kernel: [    0.172477] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
Aug 22 12:21:07 michael-laptop kernel: [    0.172483] ACPI: Sleep Button [SLPB]
Aug 22 12:21:07 michael-laptop kernel: [    0.172549] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Aug 22 12:21:07 michael-laptop kernel: [    0.172552] ACPI: Power Button [PWRF]
Aug 22 12:21:07 michael-laptop kernel: [    0.179261] Marking TSC unstable due to TSC halts in idle
Aug 22 12:21:07 michael-laptop kernel: [    0.179367] processor LNXCPU:00: registered as cooling_device0
Aug 22 12:21:07 michael-laptop kernel: [    0.180951] Switching to clocksource acpi_pm
Aug 22 12:21:07 michael-laptop kernel: [    0.189417] thermal LNXTHERM:01: registered as thermal_zone0
Aug 22 12:21:07 michael-laptop kernel: [    0.189430] ACPI: Thermal Zone [THM0] (53 C)
Aug 22 12:21:07 michael-laptop kernel: [    0.191144] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Aug 22 12:21:07 michael-laptop kernel: [    0.192109] serial 00:0a: activated
Aug 22 12:21:07 michael-laptop kernel: [    0.192216] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
Aug 22 12:21:07 michael-laptop kernel: [    0.192331] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [    0.192339] serial 0000:00:1f.6: PCI INT B disabled
Aug 22 12:21:07 michael-laptop kernel: [    0.193484] brd: module loaded
Aug 22 12:21:07 michael-laptop kernel: [    0.194044] loop: module loaded
Aug 22 12:21:07 michael-laptop kernel: [    0.194142] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Aug 22 12:21:07 michael-laptop kernel: [    0.194260] ata_piix 0000:00:1f.1: version 2.13
Aug 22 12:21:07 michael-laptop kernel: [    0.194269] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
Aug 22 12:21:07 michael-laptop kernel: [    0.194620] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [    0.194624] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [    0.194678] ata_piix 0000:00:1f.1: setting latency timer to 64
Aug 22 12:21:07 michael-laptop kernel: [    0.200400] isapnp: Scanning for PnP cards...
Aug 22 12:21:07 michael-laptop kernel: [    0.205883] scsi0 : ata_piix
Aug 22 12:21:07 michael-laptop kernel: [    0.206159] scsi1 : ata_piix
Aug 22 12:21:07 michael-laptop kernel: [    0.207535] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
Aug 22 12:21:07 michael-laptop kernel: [    0.207538] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
Aug 22 12:21:07 michael-laptop kernel: [    0.208081] Fixed MDIO Bus: probed
Aug 22 12:21:07 michael-laptop kernel: [    0.208124] PPP generic driver version 2.4.2
Aug 22 12:21:07 michael-laptop kernel: [    0.208193] tun: Universal TUN/TAP device driver, 1.6
Aug 22 12:21:07 michael-laptop kernel: [    0.208196] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 22 12:21:07 michael-laptop kernel: [    0.208325] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 22 12:21:07 michael-laptop kernel: [    0.280165] ACPI: Battery Slot [BAT0] (battery present)
Aug 22 12:21:07 michael-laptop kernel: [    0.280319] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Aug 22 12:21:07 michael-laptop kernel: [    0.280479] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Aug 22 12:21:07 michael-laptop kernel: [    0.280825] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [    0.280831] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [    0.280856] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Aug 22 12:21:07 michael-laptop kernel: [    0.280860] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug 22 12:21:07 michael-laptop kernel: [    0.280948] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Aug 22 12:21:07 michael-laptop kernel: [    0.280986] ehci_hcd 0000:00:1d.7: debug port 1
Aug 22 12:21:07 michael-laptop kernel: [    0.284865] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Aug 22 12:21:07 michael-laptop kernel: [    0.287388] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
Aug 22 12:21:07 michael-laptop kernel: [    0.308100] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Aug 22 12:21:07 michael-laptop kernel: [    0.308292] usb usb1: configuration #1 chosen from 1 choice
Aug 22 12:21:07 michael-laptop kernel: [    0.308332] hub 1-0:1.0: USB hub found
Aug 22 12:21:07 michael-laptop kernel: [    0.308345] hub 1-0:1.0: 6 ports detected
Aug 22 12:21:07 michael-laptop kernel: [    0.308434] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 22 12:21:07 michael-laptop kernel: [    0.308462] uhci_hcd: USB Universal Host Controller Interface driver
Aug 22 12:21:07 michael-laptop kernel: [    0.308774] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Aug 22 12:21:07 michael-laptop kernel: [    0.309336] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Aug 22 12:21:07 michael-laptop kernel: [    0.309349] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [    0.309360] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Aug 22 12:21:07 michael-laptop kernel: [    0.309365] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug 22 12:21:07 michael-laptop kernel: [    0.309434] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Aug 22 12:21:07 michael-laptop kernel: [    0.309463] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
Aug 22 12:21:07 michael-laptop kernel: [    0.309576] usb usb2: configuration #1 chosen from 1 choice
Aug 22 12:21:07 michael-laptop kernel: [    0.309613] hub 2-0:1.0: USB hub found
Aug 22 12:21:07 michael-laptop kernel: [    0.309621] hub 2-0:1.0: 2 ports detected
Aug 22 12:21:07 michael-laptop kernel: [    0.353194] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Aug 22 12:21:07 michael-laptop kernel: [    0.353689] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Aug 22 12:21:07 michael-laptop kernel: [    0.354038] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [    0.354043] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [    0.354051] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Aug 22 12:21:07 michael-laptop kernel: [    0.354055] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug 22 12:21:07 michael-laptop kernel: [    0.354096] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Aug 22 12:21:07 michael-laptop kernel: [    0.354119] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
Aug 22 12:21:07 michael-laptop kernel: [    0.354224] usb usb3: configuration #1 chosen from 1 choice
Aug 22 12:21:07 michael-laptop kernel: [    0.354255] hub 3-0:1.0: USB hub found
Aug 22 12:21:07 michael-laptop kernel: [    0.354264] hub 3-0:1.0: 2 ports detected
Aug 22 12:21:07 michael-laptop kernel: [    0.354310] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [    0.354317] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Aug 22 12:21:07 michael-laptop kernel: [    0.354321] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug 22 12:21:07 michael-laptop kernel: [    0.354355] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Aug 22 12:21:07 michael-laptop kernel: [    0.354376] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
Aug 22 12:21:07 michael-laptop kernel: [    0.354486] usb usb4: configuration #1 chosen from 1 choice
Aug 22 12:21:07 michael-laptop kernel: [    0.354516] hub 4-0:1.0: USB hub found
Aug 22 12:21:07 michael-laptop kernel: [    0.354524] hub 4-0:1.0: 2 ports detected
Aug 22 12:21:07 michael-laptop kernel: [    0.354643] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Aug 22 12:21:07 michael-laptop kernel: [    0.369034] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 22 12:21:07 michael-laptop kernel: [    0.369048] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 22 12:21:07 michael-laptop kernel: [    0.369243] mice: PS/2 mouse device common for all mice
Aug 22 12:21:07 michael-laptop kernel: [    0.369411] rtc_cmos 00:06: RTC can wake from S4
Aug 22 12:21:07 michael-laptop kernel: [    0.369470] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Aug 22 12:21:07 michael-laptop kernel: [    0.369489] rtc0: alarms up to one month, y3k, 114 bytes nvram
Aug 22 12:21:07 michael-laptop kernel: [    0.369651] device-mapper: uevent: version 1.0.3
Aug 22 12:21:07 michael-laptop kernel: [    0.369798] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Aug 22 12:21:07 michael-laptop kernel: [    0.370672] device-mapper: multipath: version 1.1.0 loaded
Aug 22 12:21:07 michael-laptop kernel: [    0.370676] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug 22 12:21:07 michael-laptop kernel: [    0.372795] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4242N, 0J04, max UDMA/33
Aug 22 12:21:07 michael-laptop kernel: [    0.372950] ata1.00: ATA-6: TOSHIBA MK4026GAX RoHS, PA107E, max UDMA/100
Aug 22 12:21:07 michael-laptop kernel: [    0.372954] ata1.00: 78140160 sectors, multi 16: LBA 
Aug 22 12:21:07 michael-laptop kernel: [    0.373232] EISA: Probing bus 0 at eisa.0
Aug 22 12:21:07 michael-laptop kernel: [    0.373239] Cannot allocate resource for EISA slot 1
Aug 22 12:21:07 michael-laptop kernel: [    0.373244] Cannot allocate resource for EISA slot 2
Aug 22 12:21:07 michael-laptop kernel: [    0.373246] Cannot allocate resource for EISA slot 3
Aug 22 12:21:07 michael-laptop kernel: [    0.373249] Cannot allocate resource for EISA slot 4
Aug 22 12:21:07 michael-laptop kernel: [    0.373251] Cannot allocate resource for EISA slot 5
Aug 22 12:21:07 michael-laptop kernel: [    0.373254] Cannot allocate resource for EISA slot 6
Aug 22 12:21:07 michael-laptop kernel: [    0.373256] Cannot allocate resource for EISA slot 7
Aug 22 12:21:07 michael-laptop kernel: [    0.373259] Cannot allocate resource for EISA slot 8
Aug 22 12:21:07 michael-laptop kernel: [    0.373261] EISA: Detected 0 cards.
Aug 22 12:21:07 michael-laptop kernel: [    0.374192] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Aug 22 12:21:07 michael-laptop kernel: [    0.376120] cpuidle: using governor ladder
Aug 22 12:21:07 michael-laptop kernel: [    0.376191] cpuidle: using governor menu
Aug 22 12:21:07 michael-laptop kernel: [    0.376707] TCP cubic registered
Aug 22 12:21:07 michael-laptop kernel: [    0.376894] NET: Registered protocol family 10
Aug 22 12:21:07 michael-laptop kernel: [    0.377431] lo: Disabled Privacy Extensions
Aug 22 12:21:07 michael-laptop kernel: [    0.377780] NET: Registered protocol family 17
Aug 22 12:21:07 michael-laptop kernel: [    0.378001] P-state transition latency capped at 20 uS
Aug 22 12:21:07 michael-laptop kernel: [    0.378287] Using IPI No-Shortcut mode
Aug 22 12:21:07 michael-laptop kernel: [    0.378385] PM: Resume from disk failed.
Aug 22 12:21:07 michael-laptop kernel: [    0.378405] registered taskstats version 1
Aug 22 12:21:07 michael-laptop kernel: [    0.378660]   Magic number: 6:209:330
Aug 22 12:21:07 michael-laptop kernel: [    0.378698] tty tty51: hash matches
Aug 22 12:21:07 michael-laptop kernel: [    0.378785] rtc_cmos 00:06: setting system clock to 2010-08-22 12:20:34 UTC (1282479634)
Aug 22 12:21:07 michael-laptop kernel: [    0.378801] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 22 12:21:07 michael-laptop kernel: [    0.378803] EDD information not available.
Aug 22 12:21:07 michael-laptop kernel: [    0.388678] ata2.00: configured for UDMA/33
Aug 22 12:21:07 michael-laptop kernel: [    0.388885] ata1.00: configured for UDMA/100
Aug 22 12:21:07 michael-laptop kernel: [    0.721657] Freeing initrd memory: 7684k freed
Aug 22 12:21:07 michael-laptop kernel: [    0.819742] isapnp: No Plug & Play device found
Aug 22 12:21:07 michael-laptop kernel: [    0.819989] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK4026GA PA10 PQ: 0 ANSI: 5
Aug 22 12:21:07 michael-laptop kernel: [    0.820246] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
Aug 22 12:21:07 michael-laptop kernel: [    0.820305] sd 0:0:0:0: [sda] Write Protect is off
Aug 22 12:21:07 michael-laptop kernel: [    0.820308] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 22 12:21:07 michael-laptop kernel: [    0.820337] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 22 12:21:07 michael-laptop kernel: [    0.820547]  sda:
Aug 22 12:21:07 michael-laptop kernel: [    0.820766] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug 22 12:21:07 michael-laptop kernel: [    0.825205] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4242N 0J04 PQ: 0 ANSI: 5
Aug 22 12:21:07 michael-laptop kernel: [    0.836231] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Aug 22 12:21:07 michael-laptop kernel: [    0.836235] Uniform CD-ROM driver Revision: 3.20
Aug 22 12:21:07 michael-laptop kernel: [    0.836350] sr 1:0:0:0: Attached scsi CD-ROM sr0
Aug 22 12:21:07 michael-laptop kernel: [    0.836408] sr 1:0:0:0: Attached scsi generic sg1 type 5
Aug 22 12:21:07 michael-laptop kernel: [    0.876376]  sda1 sda2 < sda5 sda6 >
Aug 22 12:21:07 michael-laptop kernel: [    0.920584] sd 0:0:0:0: [sda] Attached SCSI disk
Aug 22 12:21:07 michael-laptop kernel: [    0.920604] Freeing unused kernel memory: 660k freed
Aug 22 12:21:07 michael-laptop kernel: [    0.921287] Write protecting the kernel text: 4680k
Aug 22 12:21:07 michael-laptop kernel: [    0.921329] Write protecting the kernel read-only data: 1844k
Aug 22 12:21:07 michael-laptop kernel: [    0.939322] udev: starting version 151
Aug 22 12:21:07 michael-laptop kernel: [    0.992196] usb 3-2: new full speed USB device using uhci_hcd and address 2
Aug 22 12:21:07 michael-laptop kernel: [    1.168904] usb 3-2: configuration #1 chosen from 1 choice
Aug 22 12:21:07 michael-laptop kernel: [    1.169038] Floppy drive(s): fd0 is 1.44M
Aug 22 12:21:07 michael-laptop kernel: [    1.171297] hub 3-2:1.0: USB hub found
Aug 22 12:21:07 michael-laptop kernel: [    1.173191] hub 3-2:1.0: 4 ports detected
Aug 22 12:21:07 michael-laptop kernel: [    1.183182] Intel(R) PRO/1000 Network Driver - version 7.3.21-k5-NAPI
Aug 22 12:21:07 michael-laptop kernel: [    1.183187] Copyright (c) 1999-2006 Intel Corporation.
Aug 22 12:21:07 michael-laptop kernel: [    1.183235] e1000 0000:02:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [    1.187230] FDC 0 is a National Semiconductor PC87306
Aug 22 12:21:07 michael-laptop kernel: [    1.434737] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:10:c6:df:4f:e7
Aug 22 12:21:07 michael-laptop kernel: [    1.469567] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Aug 22 12:21:07 michael-laptop kernel: [    1.613220] usb 3-2.3: new low speed USB device using uhci_hcd and address 3
Aug 22 12:21:07 michael-laptop kernel: [    1.744355] usb 3-2.3: configuration #1 chosen from 1 choice
Aug 22 12:21:07 michael-laptop kernel: [   31.977815] Adding 1261060k swap on /dev/sda6.  Priority:-1 extents:1 across:1261060k 
Aug 22 12:21:07 michael-laptop kernel: [   32.031017] udev: starting version 151
Aug 22 12:21:07 michael-laptop kernel: [   32.215817] lp: driver loaded but no devices found
Aug 22 12:21:07 michael-laptop kernel: [   32.241589] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 22 12:21:07 michael-laptop kernel: [   32.421365] Linux agpgart interface v0.103
Aug 22 12:21:07 michael-laptop kernel: [   32.460703] intel_rng: FWH not detected
Aug 22 12:21:07 michael-laptop kernel: [   32.500438] parport_pc 00:0b: reported by Plug and Play ACPI
Aug 22 12:21:07 michael-laptop kernel: [   32.500481] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
Aug 22 12:21:07 michael-laptop kernel: [   32.578060] irda_init()
Aug 22 12:21:07 michael-laptop kernel: [   32.578079] NET: Registered protocol family 23
Aug 22 12:21:07 michael-laptop kernel: [   32.596991] Non-volatile memory driver v1.3
Aug 22 12:21:07 michael-laptop kernel: [   32.598239] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
Aug 22 12:21:07 michael-laptop kernel: [   32.611993] lp0: using parport0 (interrupt-driven).
Aug 22 12:21:07 michael-laptop kernel: [   32.682855] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Aug 22 12:21:07 michael-laptop kernel: [   32.717430] ppdev: user-space parallel port driver
Aug 22 12:21:07 michael-laptop kernel: [   32.721035] yenta_cardbus 0000:02:00.0: CardBus bridge found [1014:0552]
Aug 22 12:21:07 michael-laptop kernel: [   32.721053] yenta_cardbus 0000:02:00.0: Using INTVAL to route CSC interrupts to PCI
Aug 22 12:21:07 michael-laptop kernel: [   32.721057] yenta_cardbus 0000:02:00.0: Routing CardBus interrupts to PCI
Aug 22 12:21:07 michael-laptop kernel: [   32.721062] yenta_cardbus 0000:02:00.0: TI: mfunc 0x01d21b22, devctl 0x64
Aug 22 12:21:07 michael-laptop kernel: [   32.725763] type=1505 audit(1282476066.845:2):  operation="profile_load" pid=548 name="/sbin/dhclient3"
Aug 22 12:21:07 michael-laptop kernel: [   32.726473] type=1505 audit(1282476066.845:3):  operation="profile_load" pid=548 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug 22 12:21:07 michael-laptop kernel: [   32.726856] type=1505 audit(1282476066.845:4):  operation="profile_load" pid=548 name="/usr/lib/connman/scripts/dhclient-script"
Aug 22 12:21:07 michael-laptop kernel: [   32.747279] nsc-ircc 00:0c: activated
Aug 22 12:21:07 michael-laptop kernel: [   32.747285] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
Aug 22 12:21:07 michael-laptop kernel: [   32.747484] nsc-ircc, chip->init
Aug 22 12:21:07 michael-laptop kernel: [   32.747493] nsc-ircc, Found chip at base=0x02e
Aug 22 12:21:07 michael-laptop kernel: [   32.747516] nsc-ircc, driver loaded (Dag Brattli)
Aug 22 12:21:07 michael-laptop kernel: [   32.748454] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:02/LNXVIDEO:00/input/input5
Aug 22 12:21:07 michael-laptop kernel: [   32.748614] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Aug 22 12:21:07 michael-laptop kernel: [   32.749445] [drm] Initialized drm 1.1.0 20060810
Aug 22 12:21:07 michael-laptop kernel: [   32.751828] IrDA: Registered device irda0
Aug 22 12:21:07 michael-laptop kernel: [   32.751832] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
Aug 22 12:21:07 michael-laptop kernel: [   32.798782] cfg80211: Calling CRDA to update world regulatory domain
Aug 22 12:21:07 michael-laptop kernel: [   32.837071] usbcore: registered new interface driver hiddev
Aug 22 12:21:07 michael-laptop kernel: [   32.856202] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.3/3-2.3:1.0/input/input6
Aug 22 12:21:07 michael-laptop kernel: [   32.856443] generic-usb 0003:15CA:00C3.0001: input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-2.3/input0
Aug 22 12:21:07 michael-laptop kernel: [   32.856478] usbcore: registered new interface driver usbhid
Aug 22 12:21:07 michael-laptop kernel: [   32.856663] usbhid: v2.6:USB HID core driver
Aug 22 12:21:07 michael-laptop kernel: [   32.858110] cfg80211: World regulatory domain updated:
Aug 22 12:21:07 michael-laptop kernel: [   32.858113] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 22 12:21:07 michael-laptop kernel: [   32.858117] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 22 12:21:07 michael-laptop kernel: [   32.858121] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 22 12:21:07 michael-laptop kernel: [   32.858124] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 22 12:21:07 michael-laptop kernel: [   32.858127] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 22 12:21:07 michael-laptop kernel: [   32.858130] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 22 12:21:07 michael-laptop kernel: [   32.956502] yenta_cardbus 0000:02:00.0: ISA IRQ mask 0x0430, PCI irq 11
Aug 22 12:21:07 michael-laptop kernel: [   32.956507] yenta_cardbus 0000:02:00.0: Socket status: 30000086
Aug 22 12:21:07 michael-laptop kernel: [   32.956516] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
Aug 22 12:21:07 michael-laptop kernel: [   32.956522] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x8fff: clean.
Aug 22 12:21:07 michael-laptop kernel: [   32.957793] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
Aug 22 12:21:07 michael-laptop kernel: [   32.957797] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
Aug 22 12:21:07 michael-laptop kernel: [   32.962027] yenta_cardbus 0000:02:00.1: CardBus bridge found [1014:0552]
Aug 22 12:21:07 michael-laptop kernel: [   32.962044] yenta_cardbus 0000:02:00.1: Using INTVAL to route CSC interrupts to PCI
Aug 22 12:21:07 michael-laptop kernel: [   32.962048] yenta_cardbus 0000:02:00.1: Routing CardBus interrupts to PCI
Aug 22 12:21:07 michael-laptop kernel: [   32.962053] yenta_cardbus 0000:02:00.1: TI: mfunc 0x01d21b22, devctl 0x64
Aug 22 12:21:07 michael-laptop kernel: [   33.012826] [drm] radeon defaulting to kernel modesetting.
Aug 22 12:21:07 michael-laptop kernel: [   33.012832] [drm] radeon kernel modesetting enabled.
Aug 22 12:21:07 michael-laptop kernel: [   33.012953] radeon 0000:01:00.0: power state changed by ACPI to D0
Aug 22 12:21:07 michael-laptop kernel: [   33.012990] radeon 0000:01:00.0: power state changed by ACPI to D0
Aug 22 12:21:07 michael-laptop kernel: [   33.013001] radeon 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [   33.027501] [drm] radeon: Initializing kernel modesetting.
Aug 22 12:21:07 michael-laptop kernel: [   33.028958] [drm] register mmio base: 0xC0100000
Aug 22 12:21:07 michael-laptop kernel: [   33.028962] [drm] register mmio size: 65536
Aug 22 12:21:07 michael-laptop kernel: [   33.029342] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
Aug 22 12:21:07 michael-laptop kernel: [   33.029368] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
Aug 22 12:21:07 michael-laptop kernel: [   33.029384] agpgart-intel 0000:00:00.0: putting AGP V2 device into 1x mode
Aug 22 12:21:07 michael-laptop kernel: [   33.029422] radeon 0000:01:00.0: putting AGP V2 device into 1x mode
Aug 22 12:21:07 michael-laptop kernel: [   33.029447] [drm] radeon: VRAM 64M
Aug 22 12:21:07 michael-laptop kernel: [   33.029449] [drm] radeon: VRAM from 0x00000000 to 0x03FFFFFF
Aug 22 12:21:07 michael-laptop kernel: [   33.029452] [drm] radeon: GTT 256M
Aug 22 12:21:07 michael-laptop kernel: [   33.029454] [drm] radeon: GTT from 0xD0000000 to 0xDFFFFFFF
Aug 22 12:21:07 michael-laptop kernel: [   33.029477] [drm] radeon: irq initialized.
Aug 22 12:21:07 michael-laptop kernel: [   33.030294] [drm] Detected VRAM RAM=64M, BAR=128M
Aug 22 12:21:07 michael-laptop kernel: [   33.030298] [drm] RAM width 64bits DDR
Aug 22 12:21:07 michael-laptop kernel: [   33.030962] [TTM] Zone  kernel: Available graphics memory: 443644 kiB.
Aug 22 12:21:07 michael-laptop kernel: [   33.030965] [TTM] Zone highmem: Available graphics memory: 512960 kiB.
Aug 22 12:21:07 michael-laptop kernel: [   33.030987] [drm] radeon: 32M of VRAM memory ready
Aug 22 12:21:07 michael-laptop kernel: [   33.030990] [drm] radeon: 256M of GTT memory ready.
Aug 22 12:21:07 michael-laptop kernel: [   33.031234] [drm] radeon: cp idle (0x00008383)
Aug 22 12:21:07 michael-laptop kernel: [   33.031361] [drm] Loading R100 Microcode
Aug 22 12:21:07 michael-laptop kernel: [   33.031662] platform radeon_cp.0: firmware: requesting radeon/R100_cp.bin
Aug 22 12:21:07 michael-laptop kernel: [   33.047754] [drm] radeon: ring at 0x00000000D0000000
Aug 22 12:21:07 michael-laptop kernel: [   33.047776] [drm] ring test succeeded in 1 usecs
Aug 22 12:21:07 michael-laptop kernel: [   33.052544] [drm] radeon: ib pool ready.
Aug 22 12:21:07 michael-laptop kernel: [   33.052642] [drm] ib test succeeded in 0 usecs
Aug 22 12:21:07 michael-laptop kernel: [   33.053424] [drm] DFP table revision: 2
Aug 22 12:21:07 michael-laptop kernel: [   33.054116] [drm] Panel ID String: 1024x768                
Aug 22 12:21:07 michael-laptop kernel: [   33.054119] [drm] Panel Size 1024x768
Aug 22 12:21:07 michael-laptop kernel: [   33.054469] [drm] Default TV standard: NTSC
Aug 22 12:21:07 michael-laptop kernel: [   33.054472] [drm] 27.000000000 MHz TV ref clk
Aug 22 12:21:07 michael-laptop kernel: [   33.054475] [drm] Default TV standard: NTSC
Aug 22 12:21:07 michael-laptop kernel: [   33.054477] [drm] 27.000000000 MHz TV ref clk
Aug 22 12:21:07 michael-laptop kernel: [   33.054612] [drm] Radeon Display Connectors
Aug 22 12:21:07 michael-laptop kernel: [   33.054615] [drm] Connector 0:
Aug 22 12:21:07 michael-laptop kernel: [   33.054617] [drm]   VGA
Aug 22 12:21:07 michael-laptop kernel: [   33.054620] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
Aug 22 12:21:07 michael-laptop kernel: [   33.054622] [drm]   Encoders:
Aug 22 12:21:07 michael-laptop kernel: [   33.054624] [drm]     CRT1: INTERNAL_DAC1
Aug 22 12:21:07 michael-laptop kernel: [   33.054626] [drm] Connector 1:
Aug 22 12:21:07 michael-laptop kernel: [   33.054628] [drm]   DVI-D
Aug 22 12:21:07 michael-laptop kernel: [   33.054629] [drm]   HPD1
Aug 22 12:21:07 michael-laptop kernel: [   33.054632] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
Aug 22 12:21:07 michael-laptop kernel: [   33.054634] [drm]   Encoders:
Aug 22 12:21:07 michael-laptop kernel: [   33.054636] [drm]     DFP1: INTERNAL_TMDS1
Aug 22 12:21:07 michael-laptop kernel: [   33.054638] [drm] Connector 2:
Aug 22 12:21:07 michael-laptop kernel: [   33.054640] [drm]   LVDS
Aug 22 12:21:07 michael-laptop kernel: [   33.054641] [drm]   Encoders:
Aug 22 12:21:07 michael-laptop kernel: [   33.054643] [drm]     LCD1: INTERNAL_LVDS
Aug 22 12:21:07 michael-laptop kernel: [   33.054645] [drm] Connector 3:
Aug 22 12:21:07 michael-laptop kernel: [   33.054647] [drm]   S-video
Aug 22 12:21:07 michael-laptop kernel: [   33.054648] [drm]   Encoders:
Aug 22 12:21:07 michael-laptop kernel: [   33.054650] [drm]     TV1: INTERNAL_DAC2
Aug 22 12:21:07 michael-laptop kernel: [   33.112642] [drm] fb mappable at 0xE0040000
Aug 22 12:21:07 michael-laptop kernel: [   33.112646] [drm] vram apper at 0xE0000000
Aug 22 12:21:07 michael-laptop kernel: [   33.112648] [drm] size 786432
Aug 22 12:21:07 michael-laptop kernel: [   33.112650] [drm] fb depth is 8
Aug 22 12:21:07 michael-laptop kernel: [   33.112652] [drm]    pitch is 1024
Aug 22 12:21:07 michael-laptop kernel: [   33.117211] fb0: radeondrmfb frame buffer device
Aug 22 12:21:07 michael-laptop kernel: [   33.117214] registered panic notifier
Aug 22 12:21:07 michael-laptop kernel: [   33.117222] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
Aug 22 12:21:07 michael-laptop kernel: [   33.128077] vga16fb: initializing
Aug 22 12:21:07 michael-laptop kernel: [   33.128082] vga16fb: mapped to 0xc00a0000
Aug 22 12:21:07 michael-laptop kernel: [   33.128087] vga16fb: not registering due to another framebuffer present
Aug 22 12:21:07 michael-laptop kernel: [   33.194337] yenta_cardbus 0000:02:00.1: ISA IRQ mask 0x0430, PCI irq 11
Aug 22 12:21:07 michael-laptop kernel: [   33.194342] yenta_cardbus 0000:02:00.1: Socket status: 30000086
Aug 22 12:21:07 michael-laptop kernel: [   33.194351] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
Aug 22 12:21:07 michael-laptop kernel: [   33.194355] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x8fff: clean.
Aug 22 12:21:07 michael-laptop kernel: [   33.195624] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
Aug 22 12:21:07 michael-laptop kernel: [   33.195628] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
Aug 22 12:21:07 michael-laptop kernel: [   33.201039] ath5k 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [   33.201093] ath5k 0000:02:02.0: registered as 'phy0'
Aug 22 12:21:07 michael-laptop kernel: [   33.659250] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
Aug 22 12:21:07 michael-laptop kernel: [   33.659257] serio: Synaptics pass-through port at isa0060/serio1/input0
Aug 22 12:21:07 michael-laptop kernel: [   33.661517] thinkpad_acpi: ThinkPad ACPI Extras v0.24
Aug 22 12:21:07 michael-laptop kernel: [   33.661519] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
Aug 22 12:21:07 michael-laptop kernel: [   33.661522] thinkpad_acpi: ThinkPad BIOS 1RETDNWW (3.19 ), EC 1RHT71WW-3.04
Aug 22 12:21:07 michael-laptop kernel: [   33.661524] thinkpad_acpi: IBM ThinkPad T42, model 2374BW7
Aug 22 12:21:07 michael-laptop kernel: [   33.661527] thinkpad_acpi: WARNING: Outdated ThinkPad BIOS/EC firmware
Aug 22 12:21:07 michael-laptop kernel: [   33.661529] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
Aug 22 12:21:07 michael-laptop kernel: [   33.674546] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
Aug 22 12:21:07 michael-laptop kernel: [   33.675536] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Aug 22 12:21:07 michael-laptop kernel: [   33.675965] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
Aug 22 12:21:07 michael-laptop kernel: [   33.676365] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
Aug 22 12:21:07 michael-laptop kernel: [   33.676881] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
Aug 22 12:21:07 michael-laptop kernel: [   33.678542] Registered led device: tpacpi::thinklight
Aug 22 12:21:07 michael-laptop kernel: [   33.678579] Registered led device: tpacpi::power
Aug 22 12:21:07 michael-laptop kernel: [   33.678598] Registered led device: tpacpi::standby
Aug 22 12:21:07 michael-laptop kernel: [   33.679449] Console: switching to colour frame buffer device 128x48
Aug 22 12:21:07 michael-laptop kernel: [   33.691398] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
Aug 22 12:21:07 michael-laptop kernel: [   33.703869] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input7
Aug 22 12:21:07 michael-laptop kernel: [   33.713659] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Aug 22 12:21:07 michael-laptop kernel: [   33.858863] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Aug 22 12:21:07 michael-laptop kernel: [   33.858908] Intel ICH 0000:00:1f.5: setting latency timer to 64
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  starting...
Aug 22 12:21:08 michael-laptop avahi-daemon[745]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Aug 22 12:21:08 michael-laptop avahi-daemon[745]: Successfully dropped root privileges.
Aug 22 12:21:08 michael-laptop avahi-daemon[745]: avahi-daemon 0.6.25 starting up.
Aug 22 12:21:08 michael-laptop avahi-daemon[745]: Successfully called chroot().
Aug 22 12:21:08 michael-laptop avahi-daemon[745]: Successfully dropped remaining capabilities.
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  Trying to start the modem-manager...
Aug 22 12:21:08 michael-laptop kernel: [   33.908881] type=1505 audit(1282476068.029:5):  operation="profile_load" pid=752 name="/usr/share/gdm/guest-session/Xsession"
Aug 22 12:21:08 michael-laptop NetworkManager:    SCPlugin-Ifupdown: init!
Aug 22 12:21:08 michael-laptop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Aug 22 12:21:08 michael-laptop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Aug 22 12:21:08 michael-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0)
Aug 22 12:21:08 michael-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0, iface: eth0): no ifupdown configuration found.
Aug 22 12:21:08 michael-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/irda0, iface: irda0)
Aug 22 12:21:08 michael-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/irda0, iface: irda0): no ifupdown configuration found.
Aug 22 12:21:08 michael-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 22 12:21:08 michael-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 22 12:21:08 michael-laptop NetworkManager:    SCPlugin-Ifupdown: end _init.
Aug 22 12:21:08 michael-laptop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 22 12:21:08 michael-laptop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 22 12:21:08 michael-laptop kernel: [   33.924110] type=1505 audit(1282476068.045:6):  operation="profile_replace" pid=755 name="/sbin/dhclient3"
Aug 22 12:21:08 michael-laptop kernel: [   33.929297] type=1505 audit(1282476068.049:7):  operation="profile_replace" pid=755 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug 22 12:21:08 michael-laptop kernel: [   33.929801] type=1505 audit(1282476068.049:8):  operation="profile_replace" pid=755 name="/usr/lib/connman/scripts/dhclient-script"
Aug 22 12:21:08 michael-laptop avahi-daemon[745]: No service file found in /etc/avahi/services.
Aug 22 12:21:08 michael-laptop modem-manager: Loaded plugin MotoC
Aug 22 12:21:08 michael-laptop modem-manager: Loaded plugin Gobi
Aug 22 12:21:08 michael-laptop modem-manager: Loaded plugin Huawei
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Aug 22 12:21:08 michael-laptop NetworkManager:    SCPlugin-Ifupdown: (156456688) ... get_connections.
Aug 22 12:21:08 michael-laptop NetworkManager:    SCPlugin-Ifupdown: (156456688) ... get_connections (managed=false): return empty list.
Aug 22 12:21:08 michael-laptop avahi-daemon[745]: Network interface enumeration completed.
Aug 22 12:21:08 michael-laptop avahi-daemon[745]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 22 12:21:08 michael-laptop avahi-daemon[745]: Server startup complete. Host name is michael-laptop.local. Local service cookie is 2733657419.
Aug 22 12:21:08 michael-laptop modem-manager: Loaded plugin Option High-Speed
Aug 22 12:21:08 michael-laptop kernel: [   33.952958] type=1505 audit(1282476068.073:9):  operation="profile_load" pid=756 name="/usr/bin/evince"
Aug 22 12:21:08 michael-laptop modem-manager: Loaded plugin Option
Aug 22 12:21:08 michael-laptop modem-manager: Loaded plugin Sierra
Aug 22 12:21:08 michael-laptop modem-manager: Loaded plugin Novatel
Aug 22 12:21:08 michael-laptop modem-manager: Loaded plugin Nokia
Aug 22 12:21:08 michael-laptop modem-manager: Loaded plugin ZTE
Aug 22 12:21:08 michael-laptop modem-manager: Loaded plugin Ericsson MBM
Aug 22 12:21:08 michael-laptop modem-manager: Loaded plugin Longcheer
Aug 22 12:21:08 michael-laptop modem-manager: Loaded plugin AnyData
Aug 22 12:21:08 michael-laptop modem-manager: Loaded plugin Generic
Aug 22 12:21:08 michael-laptop kernel: [   33.987110] type=1505 audit(1282476068.105:10):  operation="profile_load" pid=756 name="/usr/bin/evince-previewer"
Aug 22 12:21:08 michael-laptop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (eth0): carrier is OFF
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e1000')
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (eth0): now managed
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (eth0): bringing up device.
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (eth0): preparing device.
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Aug 22 12:21:08 michael-laptop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0/net/eth0
Aug 22 12:21:08 michael-laptop kernel: [   34.001842] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 22 12:21:08 michael-laptop kernel: [   34.005318] type=1505 audit(1282476068.125:11):  operation="profile_load" pid=756 name="/usr/bin/evince-thumbnailer"
Aug 22 12:21:08 michael-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  modem-manager is now available
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  Trying to start the supplicant...
Aug 22 12:21:08 michael-laptop kernel: [   34.173191] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
Aug 22 12:21:08 michael-laptop kernel: [   34.174182] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Aug 22 12:21:08 michael-laptop kernel: [   34.174918] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Aug 22 12:21:08 michael-laptop kernel: [   34.175459] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Aug 22 12:21:08 michael-laptop kernel: [   34.175970] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Aug 22 12:21:08 michael-laptop kernel: [   34.179216] ath: EEPROM regdomain: 0x62
Aug 22 12:21:08 michael-laptop kernel: [   34.179219] ath: EEPROM indicates we should expect a direct regpair map
Aug 22 12:21:08 michael-laptop kernel: [   34.179225] ath: Country alpha2 being used: 00
Aug 22 12:21:08 michael-laptop kernel: [   34.179227] ath: Regpair used: 0x62
Aug 22 12:21:08 michael-laptop kernel: [   34.187514] phy0: Selected rate control algorithm 'minstrel'
Aug 22 12:21:08 michael-laptop kernel: [   34.188461] Registered led device: ath5k-phy0::rx
Aug 22 12:21:08 michael-laptop kernel: [   34.188480] Registered led device: ath5k-phy0::tx
Aug 22 12:21:08 michael-laptop kernel: [   34.188484] ath5k phy0: Atheros AR5213A chip found (MAC: 0x59, PHY: 0x43)
Aug 22 12:21:08 michael-laptop kernel: [   34.188488] ath5k phy0: RF5112B multiband radio found (0x36)
Aug 22 12:21:08 michael-laptop gdm-binary[736]: WARNING: Unable to find users: no seat-id found
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  Found wlan radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Aug 22 12:21:08 michael-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/wlan0, iface: wlan0)
Aug 22 12:21:08 michael-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ath5k')
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (wlan0): now managed
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (wlan0): bringing up device.
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (wlan0): preparing device.
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Aug 22 12:21:08 michael-laptop kernel: [   34.297779] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Aug 22 12:21:08 michael-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Aug 22 12:21:08 michael-laptop init: apport pre-start process (897) terminated with status 1
Aug 22 12:21:08 michael-laptop cron[905]: (CRON) INFO (pidfile fd = 3)
Aug 22 12:21:08 michael-laptop acpid: starting up with proc fs
Aug 22 12:21:08 michael-laptop kernel: [   34.481784] IBM machine detected. Enabling interrupts during APM calls.
Aug 22 12:21:08 michael-laptop kernel: [   34.481790] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug 22 12:21:08 michael-laptop kernel: [   34.481793] apm: overridden by ACPI.
Aug 22 12:21:08 michael-laptop init: apport post-stop process (916) terminated with status 1
Aug 22 12:21:08 michael-laptop anacron[920]: Anacron 2.3 started on 2010-08-22
Aug 22 12:21:08 michael-laptop acpid: 36 rules loaded
Aug 22 12:21:08 michael-laptop acpid: waiting for events: event logging is off
Aug 22 12:21:08 michael-laptop cron[925]: (CRON) STARTUP (fork ok)
Aug 22 12:21:08 michael-laptop cron[925]: (CRON) INFO (Running @reboot jobs)
Aug 22 12:21:08 michael-laptop anacron[920]: Normal exit (0 jobs run)
Aug 22 12:21:08 michael-laptop acpid: client connected from 941[0:0]
Aug 22 12:21:08 michael-laptop acpid: 1 client rule loaded
Aug 22 12:21:08 michael-laptop kernel: [   34.828035] intel8x0_measure_ac97_clock: measured 55394 usecs (2669 samples)
Aug 22 12:21:08 michael-laptop kernel: [   34.828040] intel8x0: clocking to 48000
Aug 22 12:21:10 michael-laptop kernel: [   36.760248] psmouse serio2: ID: 10 00 64
Aug 22 12:21:12 michael-laptop anacron[1503]: Anacron 2.3 started on 2010-08-22
Aug 22 12:21:12 michael-laptop anacron[1503]: Normal exit (0 jobs run)
Aug 22 12:21:12 michael-laptop rtkit-daemon[1522]: Sucessfully called chroot.
Aug 22 12:21:12 michael-laptop rtkit-daemon[1522]: Sucessfully dropped privileges.
Aug 22 12:21:12 michael-laptop rtkit-daemon[1522]: Sucessfully limited resources.
Aug 22 12:21:12 michael-laptop rtkit-daemon[1522]: Running.
Aug 22 12:21:12 michael-laptop rtkit-daemon[1522]: Watchdog thread running.
Aug 22 12:21:12 michael-laptop rtkit-daemon[1522]: Canary thread running.
Aug 22 12:21:12 michael-laptop polkitd[1530]: started daemon version 0.96 using authority implementation `local' version `0.96'
Aug 22 12:21:12 michael-laptop init: plymouth-stop pre-start process (1542) terminated with status 1
Aug 22 12:21:12 michael-laptop rtkit-daemon[1522]: Sucessfully made thread 1519 of process 1519 (n/a) owned by '106' high priority at nice level -11.
Aug 22 12:21:12 michael-laptop rtkit-daemon[1522]: Supervising 1 threads of 1 processes of 1 users.
Aug 22 12:21:12 michael-laptop rtkit-daemon[1522]: Sucessfully made thread 1557 of process 1519 (n/a) owned by '106' RT at priority 5.
Aug 22 12:21:12 michael-laptop rtkit-daemon[1522]: Supervising 2 threads of 1 processes of 1 users.
Aug 22 12:21:12 michael-laptop rtkit-daemon[1522]: Sucessfully made thread 1561 of process 1519 (n/a) owned by '106' RT at priority 5.
Aug 22 12:21:12 michael-laptop rtkit-daemon[1522]: Supervising 3 threads of 1 processes of 1 users.
Aug 22 12:21:12 michael-laptop pulseaudio[1519]: module-alsa-card.c: Failed to find a working profile.
Aug 22 12:21:12 michael-laptop pulseaudio[1519]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Aug 22 12:21:13 michael-laptop anacron[1586]: Anacron 2.3 started on 2010-08-22
Aug 22 12:21:13 michael-laptop anacron[1586]: Normal exit (0 jobs run)
Aug 22 12:21:13 michael-laptop gdm-simple-greeter[1480]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Aug 22 12:21:14 michael-laptop acpid: client connected from 1628[111:123]
Aug 22 12:21:14 michael-laptop acpid: 1 client rule loaded
Aug 22 12:21:14 michael-laptop kernel: [   40.682591] IBM TrackPoint firmware: 0x0e, buttons: 3/3
Aug 22 12:21:15 michael-laptop kernel: [   40.905265] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
Aug 22 12:21:16 michael-laptop gdm-session-worker[1496]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Aug 22 12:21:18 michael-laptop pulseaudio[1519]: ratelimit.c: 2 events suppressed
Aug 22 12:21:21 michael-laptop rtkit-daemon[1522]: Sucessfully made thread 1749 of process 1749 (n/a) owned by '1000' high priority at nice level -11.
Aug 22 12:21:21 michael-laptop rtkit-daemon[1522]: Supervising 4 threads of 2 processes of 2 users.
Aug 22 12:21:21 michael-laptop rtkit-daemon[1522]: Sucessfully made thread 1754 of process 1749 (n/a) owned by '1000' RT at priority 5.
Aug 22 12:21:21 michael-laptop rtkit-daemon[1522]: Supervising 5 threads of 2 processes of 2 users.
Aug 22 12:21:21 michael-laptop gnome-session[1667]: WARNING: Could not launch application 'trackerd.desktop': Unable to start application: Failed to execute child process "trackerd" (No such file or directory)
Aug 22 12:21:21 michael-laptop rtkit-daemon[1522]: Sucessfully made thread 1755 of process 1749 (n/a) owned by '1000' RT at priority 5.
Aug 22 12:21:21 michael-laptop rtkit-daemon[1522]: Supervising 6 threads of 2 processes of 2 users.
Aug 22 12:21:21 michael-laptop pulseaudio[1749]: module-alsa-card.c: Failed to find a working profile.
Aug 22 12:21:21 michael-laptop pulseaudio[1749]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Aug 22 12:21:21 michael-laptop gnome-session[1667]: WARNING: Could not launch application 'gnome-volume-manager.desktop': Unable to start application: Failed to execute child process "/usr/lib/gnome-volume-manager/gnome-volume-manager" (No such file or directory)
Aug 22 12:21:21 michael-laptop gnome-session[1667]: WARNING: Could not launch application 'tracker-applet.desktop': Unable to start application: Failed to execute child process "tracker-applet" (No such file or directory)
Aug 22 12:21:22 michael-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto 0016018C8298'
Aug 22 12:21:22 michael-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug 22 12:21:22 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 22 12:21:22 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 22 12:21:22 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 22 12:21:22 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 22 12:21:22 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 22 12:21:22 michael-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 22 12:21:22 michael-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto 0016018C8298' has security, but secrets are required.
Aug 22 12:21:22 michael-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug 22 12:21:22 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto 0016018C8298' has security, and secrets exist.  No new secrets needed.
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  Config: added 'ssid' value '0016018C8298'
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Aug 22 12:21:23 michael-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 22 12:21:23 michael-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 22 12:21:23 michael-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Aug 22 12:21:28 michael-laptop pulseaudio[1749]: ratelimit.c: 4 events suppressed
Aug 22 12:21:31 michael-laptop wpa_supplicant[759]: WPS-AP-AVAILABLE 
Aug 22 12:21:31 michael-laptop wpa_supplicant[759]: Trying to associate with 00:16:01:8c:82:99 (SSID='0016018C8298' freq=2432 MHz)
Aug 22 12:21:31 michael-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug 22 12:21:31 michael-laptop kernel: [   56.987014] wlan0: deauthenticating from 00:16:01:8c:82:99 by local choice (reason=3)
Aug 22 12:21:31 michael-laptop kernel: [   56.991881] wlan0: direct probe to AP 00:16:01:8c:82:99 (try 1)
Aug 22 12:21:31 michael-laptop kernel: [   56.995893] wlan0: direct probe responded
Aug 22 12:21:31 michael-laptop kernel: [   56.995898] wlan0: authenticate with AP 00:16:01:8c:82:99 (try 1)
Aug 22 12:21:31 michael-laptop kernel: [   56.997594] wlan0: authenticated
Aug 22 12:21:31 michael-laptop kernel: [   56.997615] wlan0: associate with AP 00:16:01:8c:82:99 (try 1)
Aug 22 12:21:31 michael-laptop kernel: [   56.999728] wlan0: RX AssocResp from 00:16:01:8c:82:99 (capab=0x411 status=0 aid=1)
Aug 22 12:21:31 michael-laptop kernel: [   56.999732] wlan0: associated
Aug 22 12:21:31 michael-laptop wpa_supplicant[759]: Associated with 00:16:01:8c:82:99
Aug 22 12:21:31 michael-laptop wpa_supplicant[759]: CTRL-EVENT-CONNECTED - Connection to 00:16:01:8c:82:99 completed (auth) [id=0 id_str=]
Aug 22 12:21:31 michael-laptop kernel: [   57.000737] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 22 12:21:31 michael-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug 22 12:21:31 michael-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Aug 22 12:21:31 michael-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '0016018C8298'.
Aug 22 12:21:31 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 22 12:21:31 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 22 12:21:31 michael-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Aug 22 12:21:31 michael-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Aug 22 12:21:31 michael-laptop NetworkManager: <info>  dhclient started with pid 1849
Aug 22 12:21:31 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 22 12:21:31 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 22 12:21:31 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Aug 22 12:21:31 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 22 12:21:31 michael-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 22 12:21:31 michael-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 22 12:21:31 michael-laptop dhclient: All rights reserved.
Aug 22 12:21:31 michael-laptop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Aug 22 12:21:31 michael-laptop dhclient: 
Aug 22 12:21:31 michael-laptop NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Aug 22 12:21:31 michael-laptop dhclient: Listening on LPF/wlan0/00:14:a4:59:b2:30
Aug 22 12:21:31 michael-laptop dhclient: Sending on   LPF/wlan0/00:14:a4:59:b2:30
Aug 22 12:21:31 michael-laptop dhclient: Sending on   Socket/fallback
Aug 22 12:21:31 michael-laptop pulseaudio[1749]: module-x11-xsmp.c: module-x11-xsmp may no be loaded twice.
Aug 22 12:21:31 michael-laptop pulseaudio[1749]: module.c: Failed to load  module "module-x11-xsmp" (argument: "display=:0.0 session_manager=local/michael-laptop:@/tmp/.ICE-unix/1667,unix/michael-laptop:/tmp/.ICE-unix/1667"): initialization failed.
Aug 22 12:21:32 michael-laptop dhclient: DHCPREQUEST of 192.168.11.4 on wlan0 to 255.255.255.255 port 67
Aug 22 12:21:32 michael-laptop dhclient: DHCPACK of 192.168.11.4 from 192.168.11.1
Aug 22 12:21:32 michael-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Aug 22 12:21:32 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 22 12:21:32 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Aug 22 12:21:32 michael-laptop NetworkManager: <info>    address 192.168.11.4
Aug 22 12:21:32 michael-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Aug 22 12:21:32 michael-laptop NetworkManager: <info>    gateway 192.168.11.1
Aug 22 12:21:32 michael-laptop NetworkManager: <info>    nameserver '192.168.11.1'
Aug 22 12:21:32 michael-laptop NetworkManager: <info>    domain name 'cable.virginmedia.net'
Aug 22 12:21:32 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 22 12:21:32 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 22 12:21:32 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug 22 12:21:32 michael-laptop avahi-daemon[745]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.11.4.
Aug 22 12:21:32 michael-laptop avahi-daemon[745]: New relevant interface wlan0.IPv4 for mDNS.
Aug 22 12:21:32 michael-laptop avahi-daemon[745]: Registering new address record for 192.168.11.4 on wlan0.IPv4.
Aug 22 12:21:32 michael-laptop dhclient: bound to 192.168.11.4 -- renewal in 81134 seconds.
Aug 22 12:21:32 michael-laptop avahi-daemon[745]: Registering new address record for fe80::214:a4ff:fe59:b230 on wlan0.*.
Aug 22 12:21:33 michael-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Aug 22 12:21:33 michael-laptop NetworkManager: <info>  Policy set 'Auto 0016018C8298' (wlan0) as default for routing and DNS.
Aug 22 12:21:33 michael-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Aug 22 12:21:33 michael-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 22 12:21:32 michael-laptop ntpdate[1909]: step time server 91.189.94.4 offset -0.693869 sec
Aug 22 12:21:40 michael-laptop kernel: [   67.252028] wlan0: no IPv6 routers present
Aug 22 12:22:30 michael-laptop AptDaemon: INFO: Initializing daemon
Aug 22 12:28:30 michael-laptop AptDaemon: INFO: Quiting due to inactivity
Aug 22 12:28:30 michael-laptop AptDaemon: INFO: Shutdown was requested

I do not show any dmesg on side panel for this IBM T42, so will send output for X31 separately. Thanks for any guidance.

---

### Post by Hookheathen on 2010-08-22
Hi,

Dmesg output from X31:-

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 (Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff60000 (usable)
[    0.000000]  BIOS-e820: 000000003ff60000 - 000000003ff77000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff77000 - 000000003ff79000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x3ff60 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DBFFF uncachable
[    0.000000]   DC000-DFFFF write-back
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03FF80000 mask FFFF80000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003ff60000 (usable)
[    0.000000]  modified: 000000003ff60000 - 000000003ff77000 (ACPI data)
[    0.000000]  modified: 000000003ff77000 - 000000003ff79000 (ACPI NVS)
[    0.000000]  modified: 000000003ff80000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37869000 - 37fef2d5
[    0.000000] Allocated new RAMDISK: 008e0000 - 010662d5
[    0.000000] Move RAMDISK from 0000000037869000 - 0000000037fef2d4 to 008e0000 - 010662d4
[    0.000000] ACPI: RSDP 000f6df0 00024 (v02 IBM   )
[    0.000000] ACPI: XSDT 3ff69e78 0004C (v01 IBM    TP-1Q    00003004  LTP 00000000)
[    0.000000] ACPI: FACP 3ff69f00 000F4 (v03 IBM    TP-1Q    00003004 IBM  00000001)
[    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 (20090903/tbfadt-526)
[    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 000000000000102C/0 (20090903/tbfadt-557)
[    0.000000] ACPI: DSDT 3ff6a0e7 0CD2A (v01 IBM    TP-1Q    00003004 MSFT 0100000E)
[    0.000000] ACPI: FACS 3ff78000 00040
[    0.000000] ACPI: SSDT 3ff6a0b4 00033 (v01 IBM    TP-1Q    00003004 MSFT 0100000E)
[    0.000000] ACPI: ECDT 3ff76e11 00052 (v01 IBM    TP-1Q    00003004 IBM  00000001)
[    0.000000] ACPI: TCPA 3ff76e63 00032 (v01 IBM    TP-1Q    00003004 PTL  00000001)
[    0.000000] ACPI: BOOT 3ff76fd8 00028 (v01 IBM    TP-1Q    00003004  LTP 00000001)
[    0.000000] 135MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008dc000 - 00008df128]              BRK ==> [00008dc000 - 00008df128]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e0000 - 00010662d5]      NEW RAMDISK ==> [00008e0000 - 00010662d5]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003ff60
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003ff60
[    0.000000] On node 0 totalpages: 261883
[    0.000000] free_area_init_node: node 0, pgdat c0798780, node_mem_map c1068000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 271 pages used for memmap
[    0.000000]   HighMem zone: 34387 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bf800000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259836
[    0.000000] Kernel command line: root=UUID=fdf097c7-f612-4655-860d-dde64fc57b56 ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5239680 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003ff60)
[    0.000000] Memory: 1017156k/1047936k available (4679k kernel code, 29988k reserved, 2116k data, 660k init, 138632k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
[    0.000000]       .data : 0xc0591d43 - 0xc07a2e88   (2116 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591d43   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 599.550 MHz processor.
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 1199.10 BogoMIPS (lpj=2398200)
[    0.004067] Security Framework initialized
[    0.004139] AppArmor: AppArmor initialized
[    0.004161] Mount-cache hash table entries: 512
[    0.004517] Initializing cgroup subsys ns
[    0.004530] Initializing cgroup subsys cpuacct
[    0.004544] Initializing cgroup subsys memory
[    0.004571] Initializing cgroup subsys devices
[    0.004579] Initializing cgroup subsys freezer
[    0.004586] Initializing cgroup subsys net_cls
[    0.004650] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004660] CPU: L2 cache: 1024K
[    0.004672] mce: CPU supports 5 MCE banks
[    0.004711] Performance Events: 
[    0.004719] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.004727] no hardware sampling interrupt available.
[    0.004734] p6 PMU driver.
[    0.004752] ... version:                0
[    0.004759] ... bit width:              32
[    0.004765] ... generic registers:      2
[    0.004772] ... value mask:             00000000ffffffff
[    0.004780] ... max period:             000000007fffffff
[    0.004787] ... fixed-purpose events:   0
[    0.004793] ... event mask:             0000000000000003
[    0.004806] Checking 'hlt' instruction... OK.
[    0.022136] SMP alternatives: switching to UP code
[    0.043320] Freeing SMP alternatives: 19k freed
[    0.043346] ACPI: Core revision 20090903
[    0.082074] ACPI: setting ELCR to 0200 (from 0800)
[    0.084019] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.084035] ftrace: allocating 21780 entries in 43 pages
[    0.088155] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.088167] weird, boot CPU (#0) not listed by the BIOS.
[    0.088174] SMP motherboard not detected.
[    0.088182] Local APIC not detected. Using dummy APIC emulation.
[    0.088190] SMP disabled
[    0.088548] Brought up 1 CPUs
[    0.088557] Total of 1 processors activated (1199.10 BogoMIPS).
[    0.092082] CPU0 attaching NULL sched-domain.
[    0.092373] devtmpfs: initialized
[    0.093627] regulator: core version 0.5
[    0.093668] Time: 12:18:08  Date: 08/22/10
[    0.093805] NET: Registered protocol family 16
[    0.094150] EISA bus registered
[    0.094173] ACPI: bus type pci registered
[    0.094634] PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=8
[    0.094641] PCI: Using configuration type 1 for base access
[    0.098415] bio: create slab <bio-0> at 0
[    0.101833] ACPI: EC: EC description table is found, configuring boot EC
[    0.129376] ACPI: Interpreter enabled
[    0.129398] ACPI: (supports S0 S3 S4 S5)
[    0.129469] ACPI: Using PIC for interrupt routing
[    0.151213] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.151333] ACPI: Power Resource [PUBS] (on)
[    0.156774] ACPI: ACPI Dock Station Driver: 3 docks/bays found
[    0.156850] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.156953] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.157149] pci 0000:00:1d.0: reg 20 io port: [0x1800-0x181f]
[    0.157234] pci 0000:00:1d.1: reg 20 io port: [0x1820-0x183f]
[    0.157318] pci 0000:00:1d.2: reg 20 io port: [0x1840-0x185f]
[    0.157411] pci 0000:00:1d.7: reg 10 32bit mmio: [0xc0000000-0xc00003ff]
[    0.157494] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.157505] pci 0000:00:1d.7: PME# disabled
[    0.157647] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.157659] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.157702] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.157717] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.157732] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.157747] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.157762] pci 0000:00:1f.1: reg 20 io port: [0x1860-0x186f]
[    0.157778] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.157860] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
[    0.157931] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.157946] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    0.157961] pci 0000:00:1f.5: reg 18 32bit mmio: [0xc0000c00-0xc0000dff]
[    0.157976] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xc0000800-0xc00008ff]
[    0.158024] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.158034] pci 0000:00:1f.5: PME# disabled
[    0.158084] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    0.158099] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    0.158157] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.158167] pci 0000:00:1f.6: PME# disabled
[    0.158232] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xe0000000-0xe7ffffff]
[    0.158247] pci 0000:01:00.0: reg 14 io port: [0x3000-0x30ff]
[    0.158261] pci 0000:01:00.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
[    0.158289] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.158324] pci 0000:01:00.0: supports D1 D2
[    0.158384] pci 0000:00:01.0: bridge io port: [0x3000-0x3fff]
[    0.158395] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.158406] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe0000000-0xe7ffffff]
[    0.158466] pci 0000:02:00.0: reg 10 32bit mmio: [0xb0000000-0xb0000fff]
[    0.158497] pci 0000:02:00.0: supports D1 D2
[    0.158505] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.158516] pci 0000:02:00.0: PME# disabled
[    0.158572] pci 0000:02:00.1: reg 10 32bit mmio: [0xb1000000-0xb1000fff]
[    0.158603] pci 0000:02:00.1: supports D1 D2
[    0.158611] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.158622] pci 0000:02:00.1: PME# disabled
[    0.158675] pci 0000:02:00.2: reg 10 32bit mmio: [0xc0240000-0xc02407ff]
[    0.158743] pci 0000:02:00.2: PME# supported from D0 D3hot D3cold
[    0.158753] pci 0000:02:00.2: PME# disabled
[    0.158827] pci 0000:02:01.0: reg 10 32bit mmio: [0xc0220000-0xc023ffff]
[    0.158843] pci 0000:02:01.0: reg 14 32bit mmio: [0xc0200000-0xc020ffff]
[    0.158858] pci 0000:02:01.0: reg 18 io port: [0x8000-0x803f]
[    0.158892] pci 0000:02:01.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[    0.158932] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
[    0.158943] pci 0000:02:01.0: PME# disabled
[    0.159001] pci 0000:02:02.0: reg 10 32bit mmio: [0xc0210000-0xc021ffff]
[    0.159127] pci 0000:00:1e.0: transparent bridge
[    0.159138] pci 0000:00:1e.0: bridge io port: [0x4000-0x8fff]
[    0.159150] pci 0000:00:1e.0: bridge 32bit mmio: [0xc0200000-0xcfffffff]
[    0.159163] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.159230] pci_bus 0000:00: on NUMA node 0
[    0.159245] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.159395] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.159482] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.168136] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.168657] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.169172] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.169686] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.170148] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.170612] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.171074] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.171592] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.171958] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.171974] vgaarb: loaded
[    0.172373] SCSI subsystem initialized
[    0.172491] libata version 3.00 loaded.
[    0.172699] usbcore: registered new interface driver usbfs
[    0.172744] usbcore: registered new interface driver hub
[    0.172816] usbcore: registered new device driver usb
[    0.173203] ACPI: WMI: Mapper loaded
[    0.173209] PCI: Using ACPI for IRQ routing
[    0.173750] NetLabel: Initializing
[    0.173757] NetLabel:  domain hash size = 128
[    0.173763] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.173800] NetLabel:  unlabeled traffic allowed by default
[    0.173910] Switching to clocksource tsc
[    0.177902] AppArmor: AppArmor Filesystem Enabled
[    0.177937] pnp: PnP ACPI init
[    0.177976] ACPI: bus type pnp registered
[    0.187730] pnp: PnP ACPI: found 13 devices
[    0.187738] ACPI: ACPI bus type pnp unregistered
[    0.187748] PnPBIOS: Disabled by ACPI PNP
[    0.187782] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.187793] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.187803] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.187814] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    0.187824] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.187834] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.187845] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.187855] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.187866] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.187876] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.187886] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.187897] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.187907] system 00:00: iomem range 0x100000-0x3fffffff could not be reserved
[    0.187919] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.187943] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.187954] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.187964] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.187974] system 00:02: ioport range 0x1600-0x167f has been reserved
[    0.223047] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.223058] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.223070] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.223081] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xe7ffffff
[    0.223107] pci 0000:02:00.0: CardBus bridge, secondary bus 0000:03
[    0.223115] pci 0000:02:00.0:   IO window: 0x004000-0x0040ff
[    0.223126] pci 0000:02:00.0:   IO window: 0x004400-0x0044ff
[    0.223137] pci 0000:02:00.0:   PREFETCH window: 0xe8000000-0xebffffff
[    0.223149] pci 0000:02:00.0:   MEM window: 0xc4000000-0xc7ffffff
[    0.223160] pci 0000:02:00.1: CardBus bridge, secondary bus 0000:07
[    0.223168] pci 0000:02:00.1:   IO window: 0x004800-0x0048ff
[    0.223179] pci 0000:02:00.1:   IO window: 0x004c00-0x004cff
[    0.223190] pci 0000:02:00.1:   PREFETCH window: 0xec000000-0xefffffff
[    0.223202] pci 0000:02:00.1:   MEM window: 0xc8000000-0xcbffffff
[    0.223213] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.223223] pci 0000:00:1e.0:   IO window: 0x4000-0x8fff
[    0.223236] pci 0000:00:1e.0:   MEM window: 0xc0200000-0xcfffffff
[    0.223247] pci 0000:00:1e.0:   PREFETCH window: 0xe8000000-0xefffffff
[    0.223281] pci 0000:00:1e.0: setting latency timer to 64
[    0.224183] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.224192] PCI: setting IRQ 11 as level-triggered
[    0.224205] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.225077] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    0.225089] pci 0000:02:00.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.225105] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.225115] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.225125] pci_bus 0000:01: resource 0 io:  [0x3000-0x3fff]
[    0.225134] pci_bus 0000:01: resource 1 mem: [0xc0100000-0xc01fffff]
[    0.225144] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xe7ffffff]
[    0.225153] pci_bus 0000:02: resource 0 io:  [0x4000-0x8fff]
[    0.225162] pci_bus 0000:02: resource 1 mem: [0xc0200000-0xcfffffff]
[    0.225172] pci_bus 0000:02: resource 2 pref mem [0xe8000000-0xefffffff]
[    0.225181] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.225190] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.225200] pci_bus 0000:03: resource 0 io:  [0x4000-0x40ff]
[    0.225209] pci_bus 0000:03: resource 1 io:  [0x4400-0x44ff]
[    0.225218] pci_bus 0000:03: resource 2 pref mem [0xe8000000-0xebffffff]
[    0.225227] pci_bus 0000:03: resource 3 mem: [0xc4000000-0xc7ffffff]
[    0.225237] pci_bus 0000:07: resource 0 io:  [0x4800-0x48ff]
[    0.225245] pci_bus 0000:07: resource 1 io:  [0x4c00-0x4cff]
[    0.225255] pci_bus 0000:07: resource 2 pref mem [0xec000000-0xefffffff]
[    0.225264] pci_bus 0000:07: resource 3 mem: [0xc8000000-0xcbffffff]
[    0.225375] NET: Registered protocol family 2
[    0.225685] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.226815] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.228859] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.230060] TCP: Hash tables configured (established 131072 bind 65536)
[    0.230068] TCP reno registered
[    0.230369] NET: Registered protocol family 1
[    0.230551] pci 0000:01:00.0: Boot video device
[    0.230764] Simple Boot Flag at 0x35 set to 0x1
[    0.230988] cpufreq-nforce2: No nForce2 chipset.
[    0.231067] Scanning for low memory corruption every 60 seconds
[    0.231425] audit: initializing netlink socket (disabled)
[    0.231464] type=2000 audit(1282479488.230:1): initialized
[    0.267027] Trying to unpack rootfs image as initramfs...
[    0.307363] highmem bounce pool size: 64 pages
[    0.307381] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.318578] VFS: Disk quotas dquot_6.5.2
[    0.318800] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.321071] fuse init (API version 7.13)
[    0.321399] msgmni has been set to 1716
[    0.326110] alg: No test for stdrng (krng)
[    0.326322] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.326332] io scheduler noop registered
[    0.326339] io scheduler anticipatory registered
[    0.326345] io scheduler deadline registered
[    0.326505] io scheduler cfq registered (default)
[    0.326859] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.326932] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.327409] ACPI: AC Adapter [AC] (off-line)
[    0.327608] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.327884] ACPI: Lid Switch [LID]
[    0.328031] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.328044] ACPI: Sleep Button [SLPB]
[    0.328216] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.328225] ACPI: Power Button [PWRF]
[    0.339377] Marking TSC unstable due to TSC halts in idle
[    0.339559] processor LNXCPU:00: registered as cooling_device0
[    0.342046] Switching to clocksource acpi_pm
[    0.364248] thermal LNXTHERM:01: registered as thermal_zone0
[    0.364276] ACPI: Thermal Zone [THM0] (25 C)
[    0.372497] isapnp: Scanning for PnP cards...
[    0.380163] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.388701] serial 00:0a: activated
[    0.389151] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    0.433277] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.433316] serial 0000:00:1f.6: PCI INT B disabled
[    0.444814] ACPI: Battery Slot [BAT0] (battery present)
[    0.447560] brd: module loaded
[    0.450048] loop: module loaded
[    0.450325] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.450624] ata_piix 0000:00:1f.1: version 2.13
[    0.450647] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.451560] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.451574] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.451669] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.456935] scsi0 : ata_piix
[    0.457222] scsi1 : ata_piix
[    0.459433] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    0.459444] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    0.460844] Fixed MDIO Bus: probed
[    0.460966] PPP generic driver version 2.4.2
[    0.461117] tun: Universal TUN/TAP device driver, 1.6
[    0.461124] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.461390] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.464462] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.468211] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.469106] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.469120] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.469157] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.469166] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.469299] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.469362] ehci_hcd 0000:00:1d.7: debug port 1
[    0.473260] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.476553] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[    0.496065] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.496379] usb usb1: configuration #1 chosen from 1 choice
[    0.496475] hub 1-0:1.0: USB hub found
[    0.496500] hub 1-0:1.0: 6 ports detected
[    0.496680] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.496731] uhci_hcd: USB Universal Host Controller Interface driver
[    0.497785] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.498048] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.498071] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.498090] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.498099] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.498218] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.498261] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    0.498556] usb usb2: configuration #1 chosen from 1 choice
[    0.498652] hub 2-0:1.0: USB hub found
[    0.498674] hub 2-0:1.0: 2 ports detected
[    0.499063] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    0.499937] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    0.500875] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.500888] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.500905] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.500914] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.501031] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.501071] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    0.501368] usb usb3: configuration #1 chosen from 1 choice
[    0.501455] hub 3-0:1.0: USB hub found
[    0.501475] hub 3-0:1.0: 2 ports detected
[    0.501595] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.501612] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.501621] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.501719] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.501757] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[    0.502061] usb usb4: configuration #1 chosen from 1 choice
[    0.502147] hub 4-0:1.0: USB hub found
[    0.502166] hub 4-0:1.0: 2 ports detected
[    0.502466] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.556213] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.556236] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.560533] mice: PS/2 mouse device common for all mice
[    0.560929] rtc_cmos 00:06: RTC can wake from S4
[    0.561068] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.561101] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.561585] device-mapper: uevent: version 1.0.3
[    0.561932] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.563324] device-mapper: multipath: version 1.1.0 loaded
[    0.563333] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.565191] EISA: Probing bus 0 at eisa.0
[    0.565205] Cannot allocate resource for EISA slot 1
[    0.565214] Cannot allocate resource for EISA slot 2
[    0.565221] Cannot allocate resource for EISA slot 3
[    0.565228] Cannot allocate resource for EISA slot 4
[    0.565235] Cannot allocate resource for EISA slot 5
[    0.565242] Cannot allocate resource for EISA slot 6
[    0.565249] Cannot allocate resource for EISA slot 7
[    0.565256] Cannot allocate resource for EISA slot 8
[    0.565262] EISA: Detected 0 cards.
[    0.566911] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.567336] cpuidle: using governor ladder
[    0.567532] cpuidle: using governor menu
[    0.569225] TCP cubic registered
[    0.569835] NET: Registered protocol family 10
[    0.571441] lo: Disabled Privacy Extensions
[    0.576773] NET: Registered protocol family 17
[    0.578026] P-state transition latency capped at 20 uS
[    0.578440] Using IPI No-Shortcut mode
[    0.578530] PM: Resume from disk failed.
[    0.578545] registered taskstats version 1
[    0.578813]   Magic number: 6:209:330
[    0.578861] tty tty51: hash matches
[    0.578958] rtc_cmos 00:06: setting system clock to 2010-08-22 12:18:08 UTC (1282479488)
[    0.578963] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.578965] EDD information not available.
[    0.656715] ata1.00: ATA-6: HTS541040G9AT00, MB2IA60A, max UDMA/100
[    0.656721] ata1.00: 78140160 sectors, multi 16: LBA 
[    0.673054] ata1.00: configured for UDMA/100
[    1.027235] Freeing initrd memory: 7704k freed
[    1.083361] isapnp: No Plug & Play device found
[    1.083633] scsi 0:0:0:0: Direct-Access     ATA      HTS541040G9AT00  MB2I PQ: 0 ANSI: 5
[    1.083922] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.084131] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.084191] sd 0:0:0:0: [sda] Write Protect is off
[    1.084195] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.084226] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.084418]  sda: sda1 sda2 < sda5 sda6 >
[    1.159078] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.159104] Freeing unused kernel memory: 660k freed
[    1.159957] Write protecting the kernel text: 4680k
[    1.160074] Write protecting the kernel read-only data: 1840k
[    1.181073] udev: starting version 151
[    1.477527] Floppy drive(s): fd0 is 1.44M
[    1.477708] Intel(R) PRO/1000 Network Driver - version 7.3.21-k5-NAPI
[    1.477711] Copyright (c) 1999-2006 Intel Corporation.
[    1.477765] e1000 0000:02:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.495308] FDC 0 is a National Semiconductor PC87306
[    1.730795] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:0d:60:cc:5f:71
[    1.765787] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    1.765836] ohci1394 0000:02:00.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    1.822126] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[c0240000-c02407ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.003912] kjournald starting.  Commit interval 5 seconds
[    2.003925] EXT3-fs: mounted filesystem with ordered data mode.
[    3.100198] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00061b0329022e31]
[   28.918006] udev: starting version 151
[   28.973417] Adding 947792k swap on /dev/sda6.  Priority:-1 extents:1 across:947792k 
[   29.243623] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   29.317596] lp: driver loaded but no devices found
[   29.424071] Linux agpgart interface v0.103
[   29.462610] EXT3 FS on sda5, internal journal
[   29.493174] irda_init()
[   29.493197] NET: Registered protocol family 23
[   29.493402] intel_rng: FWH not detected
[   29.506485] Non-volatile memory driver v1.3
[   29.558154] parport_pc 00:0b: reported by Plug and Play ACPI
[   29.558199] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   29.642308] type=1505 audit(1282475917.560:2):  operation="profile_load" pid=494 name="/sbin/dhclient3"
[   29.643068] type=1505 audit(1282475917.560:3):  operation="profile_load" pid=494 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   29.643483] type=1505 audit(1282475917.560:4):  operation="profile_load" pid=494 name="/usr/lib/connman/scripts/dhclient-script"
[   29.652333] lp0: using parport0 (interrupt-driven).
[   29.699099] [drm] Initialized drm 1.1.0 20060810
[   29.714351] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   29.740714] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:02/LNXVIDEO:00/input/input5
[   29.740881] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   29.747263] nsc-ircc 00:0c: activated
[   29.747271] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   29.747479] nsc-ircc, chip->init
[   29.747489] nsc-ircc, Found chip at base=0x02e
[   29.747513] nsc-ircc, driver loaded (Dag Brattli)
[   29.764215] IrDA: Registered device irda0
[   29.764222] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   29.820719] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   29.852215] cfg80211: Calling CRDA to update world regulatory domain
[   29.890240] ppdev: user-space parallel port driver
[   29.892040] cfg80211: World regulatory domain updated:
[   29.892044] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.892049] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.892052] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.892056] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.892059] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.892063] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   30.014993] yenta_cardbus 0000:02:00.0: CardBus bridge found [1014:0532]
[   30.041330] psmouse serio1: ID: 10 00 64
[   30.140750] yenta_cardbus 0000:02:00.0: ISA IRQ mask 0x0430, PCI irq 11
[   30.140757] yenta_cardbus 0000:02:00.0: Socket status: 30000006
[   30.140767] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   30.140772] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x8fff: clean.
[   30.142090] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   30.142094] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   30.145090] yenta_cardbus 0000:02:00.1: CardBus bridge found [1014:0532]
[   30.272484] yenta_cardbus 0000:02:00.1: ISA IRQ mask 0x0430, PCI irq 11
[   30.272490] yenta_cardbus 0000:02:00.1: Socket status: 30000006
[   30.272501] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   30.272506] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x8fff: clean.
[   30.273827] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   30.273832] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   30.290838] [drm] radeon defaulting to kernel modesetting.
[   30.290844] [drm] radeon kernel modesetting enabled.
[   30.290993] radeon 0000:01:00.0: power state changed by ACPI to D0
[   30.291034] radeon 0000:01:00.0: power state changed by ACPI to D0
[   30.291045] radeon 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   30.306296] [drm] radeon: Initializing kernel modesetting.
[   30.316064] ath5k 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   30.316113] ath5k 0000:02:02.0: registered as 'phy0'
[   30.576666] [drm] register mmio base: 0xC0100000
[   30.576671] [drm] register mmio size: 65536
[   30.577098] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   30.577140] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   30.577326] agpgart-intel 0000:00:00.0: putting AGP V2 device into 1x mode
[   30.577366] radeon 0000:01:00.0: putting AGP V2 device into 1x mode
[   30.577399] [drm] radeon: VRAM 64M
[   30.577401] [drm] radeon: VRAM from 0x00000000 to 0x03FFFFFF
[   30.577404] [drm] radeon: GTT 256M
[   30.577407] [drm] radeon: GTT from 0xD0000000 to 0xDFFFFFFF
[   30.577431] [drm] radeon: irq initialized.
[   30.577689] [drm] Detected VRAM RAM=64M, BAR=128M
[   30.577694] [drm] RAM width 32bits DDR
[   30.579585] [TTM] Zone  kernel: Available graphics memory: 443648 kiB.
[   30.579589] [TTM] Zone highmem: Available graphics memory: 512964 kiB.
[   30.579800] [drm] radeon: 16M of VRAM memory ready
[   30.579803] [drm] radeon: 256M of GTT memory ready.
[   30.590683] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.629585] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   30.643130] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input6
[   30.645116] [drm] radeon: cp idle (0x00008080)
[   30.645223] [drm] Loading R100 Microcode
[   30.645564] platform radeon_cp.0: firmware: requesting radeon/R100_cp.bin
[   30.676325] [drm] radeon: ring at 0x00000000D0000000
[   30.676350] [drm] ring test succeeded in 1 usecs
[   30.679110] [drm] radeon: ib pool ready.
[   30.679226] [drm] ib test succeeded in 0 usecs
[   30.689381] [drm] Panel ID String: 1024x768                
[   30.689385] [drm] Panel Size 1024x768
[   30.689552] [drm] Radeon Display Connectors
[   30.689555] [drm] Connector 0:
[   30.689558] [drm]   VGA
[   30.689561] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   30.689563] [drm]   Encoders:
[   30.689566] [drm]     CRT1: INTERNAL_DAC1
[   30.689568] [drm] Connector 1:
[   30.689570] [drm]   LVDS
[   30.689572] [drm]   Encoders:
[   30.689574] [drm]     LCD1: INTERNAL_LVDS
[   30.808992] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   30.809991] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   30.810426] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   30.810797] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   30.811326] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   30.855543] type=1505 audit(1282475918.772:5):  operation="profile_load" pid=503 name="/usr/sbin/ntpd"
[   30.873673] [drm] fb mappable at 0xE0040000
[   30.873678] [drm] vram apper at 0xE0000000
[   30.873680] [drm] size 786432
[   30.873682] [drm] fb depth is 8
[   30.873684] [drm]    pitch is 1024
[   30.889485] fb0: radeondrmfb frame buffer device
[   30.889490] registered panic notifier
[   30.889500] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   30.900494] vga16fb: initializing
[   30.900501] vga16fb: mapped to 0xc00a0000
[   30.900506] vga16fb: not registering due to another framebuffer present
[   30.915354] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   30.915359] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   30.915362] thinkpad_acpi: ThinkPad BIOS 1QET94WW (3.00d), EC 1QHT22WW-1.07b
[   30.915365] thinkpad_acpi: IBM ThinkPad X31, model 2673RG8
[   30.915369] thinkpad_acpi: WARNING: Outdated ThinkPad BIOS/EC firmware
[   30.915371] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
[   30.953507] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is blocked
[   30.960099] Registered led device: tpacpi::thinklight
[   30.960810] Registered led device: tpacpi::power
[   30.961248] Registered led device: tpacpi::standby
[   30.966462] thinkpad_acpi: brightness: will use unverified default: brightness_mode=3
[   30.966467] thinkpad_acpi: brightness: please report to [email]ibm-acpi-devel@lists.sourceforge.net[/email] whether it works well or not on your ThinkPad
[   30.974434] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   31.071329] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input7
[   31.148996] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   31.149053] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   31.149195] Console: switching to colour frame buffer device 128x48
[   31.234583] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   31.235583] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   31.239765] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   31.240255] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   31.240789] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   31.296400] type=1505 audit(1282475919.216:6):  operation="profile_load" pid=769 name="/usr/share/gdm/guest-session/Xsession"
[   31.304472] type=1505 audit(1282475919.224:7):  operation="profile_replace" pid=772 name="/sbin/dhclient3"
[   31.305240] type=1505 audit(1282475919.224:8):  operation="profile_replace" pid=772 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   31.305662] type=1505 audit(1282475919.224:9):  operation="profile_replace" pid=772 name="/usr/lib/connman/scripts/dhclient-script"
[   31.414475] type=1505 audit(1282475919.332:10):  operation="profile_load" pid=774 name="/usr/bin/evince"
[   31.417536] ath: EEPROM regdomain: 0x61
[   31.417540] ath: EEPROM indicates we should expect a direct regpair map
[   31.417547] ath: Country alpha2 being used: 00
[   31.417550] ath: Regpair used: 0x61
[   31.435037] type=1505 audit(1282475919.352:11):  operation="profile_load" pid=774 name="/usr/bin/evince-previewer"
[   31.455376] phy0: Selected rate control algorithm 'minstrel'
[   31.456585] Registered led device: ath5k-phy0::rx
[   31.456609] Registered led device: ath5k-phy0::tx
[   31.456615] ath5k phy0: Atheros AR5212 chip found (MAC: 0x56, PHY: 0x41)
[   31.456619] ath5k phy0: RF5111 5GHz radio found (0x17)
[   31.456622] ath5k phy0: RF2111 2GHz radio found (0x23)
[   31.548538] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.107351] intel8x0_measure_ac97_clock: measured 82653 usecs (3977 samples)
[   32.107356] intel8x0: clocking to 48000
[   32.412064] IBM machine detected. Enabling interrupts during APM calls.
[   32.412070] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   32.412074] apm: overridden by ACPI.

I hope this throws light on the problems. Thanks.

---

### Post by Hookheathen on 2010-08-25
KIAaze, 
Thanks for your suggestions. I have posted the outputs above but have not had any other comments from you, or from any other forum contributors, which is disappointing. 
Given this issue is quite serious, in that it results in complete system failure on two separate machines it would be most helpful if the collective brain power of the bean grinders could identify what is happening and recommend a solution. I am pretty sure I am not the only Thinkpad (T42 and X31) user running 10.04 and Skype!
Please assist.

---

### Post by mattcasters on 2010-09-08
Must be.  Because of other issues I removed pulseaudio.
Re-installing it solved the "Jabba the hut" sound distortion. issue in skype.

---

### Post by wkhasintha on 2010-09-08
Skype is working fine

---

### Post by aiiee on 2010-11-10
> **Hookheathen said:**
> KIAaze, 
Thanks for your suggestions. I have posted the outputs above but have not had any other comments from you, or from any other forum contributors, which is disappointing. 
Given this issue is quite serious, in that it results in complete system failure on two separate machines it would be most helpful if the collective brain power of the bean grinders could identify what is happening and recommend a solution. I am pretty sure I am not the only Thinkpad (T42 and X31) user running 10.04 and Skype!
Please assist.

frustrating isn't it?

Are you using Wubi?  No idea if that's part of the problem or not, but I am using Wubi, and so far nothing I've tried has worked.  Keep looking. LOTS of people are having this problem.
:confused:

/clueless T61p owner here.

---

### Post by KIAaze on 2010-11-10
@aiiee: Do you also experience complete system failure like Hookheathen with Wubi?

@Hookheathen: If you still have the crash problem, you should report it as a bug on Launchpad if you haven't done so yet.
And report it to the Skype developers.

I also had problems with complete system crashes (not skype-related, not black screen, but kernel lockup and frozen screen) as well as non-working resume (black screen, kernel locked up), but never managed to solve them. I have no idea how to really debug such kernel related problems, especially since a reboot is usually necessary and I have no idea how the kernel works. :(

My most recent problem with Skype on Ubuntu 10.10 was the microphone not working, but I finally solved it by just playing around with the sound preferences and setting the device to "analog stereo output"(if I remember correctly, even if it doesn't make much sense for a sound input problem...).

Just to finish with a few links gathered while trying to find something about thinkpad+skype:
[http://brunogirin.blogspot.com/search/label/skype](http://brunogirin.blogspot.com/search/label/skype)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://149.20.54.209/showthread.php?t=13002](http://149.20.54.209/showthread.php?t=13002) (Skype running fine on Thinkpad with FreeBSD!!!)
[http://forum.skype.com/index.php?showtopic=50814](http://forum.skype.com/index.php?showtopic=50814)

Probably won't help (no mentions of crashes), but who knows...
And definitely try "padsp skype" at least.

---

### Post by Hookheathen on 2010-11-11
> **aiiee said:**
> frustrating isn't it?

Are you using Wubi?  No idea if that's part of the problem or not, but I am using Wubi, and so far nothing I've tried has worked.  Keep looking. LOTS of people are having this problem.
:confused:

/clueless T61p owner here.

Firstly, I am reassured that life continues on this thread!
Secondly, I am comforted in the knowledge that LOTS of people are having this problem. So the concentrated brain power may resolve the issue.
Thirdly, I am not using WUBI.

I have researched the links kindly provided by KIAaze and followed his suggestion to raise the matter on Launchpad. Let's hope for all those frustrated Thinkpad users, of which there are many devotees, that some solution will soon be forthcoming.

---

### Post by John Bennett on 2011-05-26
There has been improvement.  In Ubuntu 11.04 Skype aborts rather than locking up the system.

---

