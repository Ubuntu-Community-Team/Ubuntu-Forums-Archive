---
title: "no sound after install ubuntu 9.10"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by envisonhong on 2010-04-15
need help from all those advance user out there. i installed Ubuntu 9.10 yesterday and it was no sound at all.. ><. however, i have been tested that my sound driver were installed properly, and in the desktop i seen the sound icon. everything looks fine for me, but i 
dont know why i have no sound. i have been reading posts last night, try to figure it out, but no luck....:(
:confused::confused::confused::confused::confused:
Please help....i am noob...><
here is some information of my system
laptop>hp>G61-321 nr notebook

---

### Post by zvacet on 2010-04-15
System>preferences>multimedia system menu and there check your sound.You can also go to the system>preferences>sound and see if you can do something there.

---

### Post by quadproc on 2010-04-15
> **envisonhong said:**
> need help from all those advance user out there. i installed Ubuntu 9.10 yesterday and it was no sound at all.
There have been a lot of sound issues in 9.10.  It seems like the issues are hardware dependent and are mostly due to conflicts between several things that want to use the sound subsystem.

You may get some illumination from reading the sticky post at the beginning of this forum regarding 9.10 sound issues.

One other thing - I found that the default sound setting for my system was MUTE after I upgraded to 9.10.  Simply setting the level to something higher than zero was all it took for this machine.

quadproc

---

### Post by _0R10N on 2010-04-15
I had the same problem with my HP DV6 2170-us. I had to edit the /etc/modprobe.d/alsa-base.conf file, adding the following line at the end:
options snd-hda-intel model=hp-dv6

You should replace hp-dv6 with your specific model. Then reboot and go to System->Preferences->Sound->Hardware and select something like "Analog Stereo Duplex". No reboot required.

I hope this helps!

Kind regards!

_0R10N >>

---

### Post by garvinrick4 on 2010-04-15
[SIZE=4]**HOWTO: PulseAudio Fixes & System-Wide Equalizer  Support**[/SIZE]
*Overview:*
 
[COLOR=BLUE]**Note 1. Karmic & Jaunty users:** If you have  dist-upgraded from a previous release, I recommend that you follow the  guide to remove obsolete configuration. If you have performed a clean  installation, follow the guide only if you are experiencing issues.
**Note 2. Jaunty & Intrepid users:** due to a bug in the ALSA  libraries, your PCM mixer may occasionally become muted or reset to 0%  volume. If you cannot hear sound - or hear a faint crackling - refer to  Part A, Step 6.
**Note 3: OSSv4 users:** PulseAudio does not support OSSv4, so this  guide will serve no purpose to you. If you have chosen to install OSSv4  and experience issues, you should seek guidance within the threads  dedicated to OSSv4. I do not recommend users to install OSSv4 due to  compatibility and support issues.
**Note 4: Kubuntu users:** Don't follow this guide - PulseAudio isn't  used in your distribution.
[/COLOR]
PulseAudio is an advanced sound server which has been included in **U**buntu  (i.e. the standard GNOME version) since the release of Hardy Heron  (8.04). Unfortunately, Hardy shipped with a suboptimal configuration of  PulseAudio which has resulted in users experiencing various problems,  ranging from sporadic crashes in Firefox to sound mixing being  completely broken. PulseAudio in Intrepid should work by default, but it  is quite possible that your configuration is suboptimal. For more  information, refer to the **FAQ** below.

For best results, I recommend all users who are interested in PulseAudio  to install the latest release - Karmic Koala (9.10). The developers  have done an excellent job with PulseAudio integration and configuration  in this release - enough to make this guide virtually obsolete.

When you are ready to follow this guide, this is all you need to know:

Hardy users: Follow **Part A** & **B**.
Intrepid users: Follow **Part A** & **C**.
Jaunty users: Follow **Part A**.
Karmic users: Follow **Part A**.

Additionally: 
[LIST]
[*]**Appendix A** gives general troubleshooting  tips - if you have problems, start here.
[*]**Appendix B** gives useful information on the more  advanced/technical features of PulseAudio.
[*]**Appendix C** gives information on how to properly configure  specific applications that may not work with PulseAudio by default,  including (but not limited to): WINE, Skype, and all OSS applications.
[*]**Appendix D** (only for Intrepid and lower) will show you how to  enable equalized audio for **all** applications on your system -  this is especially useful for laptop users who experience poor audio  quality with their internal speakers.
[/LIST]
[SIZE=4]**Frequently Asked Questions**[/SIZE]
*The most common queries are answered here.*

**Q. What exactly is PulseAudio?**
A. From the [homepage]("http://www.pulseaudio.org/"):
     Quote:
                                                 PulseAudio is a sound server for POSIX and Win32 systems. A sound  server is basically a proxy for your sound applications. It allows you  to do advanced operations on your sound data as it passes between your  application and your hardware. Things like transferring the audio to a  different machine, changing the sample format or channel count and  mixing several sounds into one are easily achieved using a sound server.                                 
Simplified: PulseAudio is responsible for playback and mixing of  audio on your system. It is not a sound driver - in fact, it runs on top  of the [Advanced  Linux Sound Architecture]("http://www.alsa-project.org/") (ALSA). Aside from all the cool effects  PulseAudio provides, it serves as a replacement for ALSA's virtual sound  mixing device ([DmixPlugin]("http://alsa.opensrc.org/DmixPlugin"), or "dmix") - thus allowing multiple  applications to share access to your sound card.

**Q. PulseAudio? Bleh! I don't want it on my system.**
A. Well... tough! PulseAudio is *already* installed and active on  Hardy and Intrepid by default; it replaces ESD (ESound Daemon) for  system sounds, and most of Ubuntu's default applications already use it  (Totem, Rhythmbox, and any other applications using the GStreamer  framework). Although some high-profile applications support PulseAudio  natively (such as VLC and mplayer), most applications use plain ALSA or  OSS output, and thus don't have native PulseAudio support.

**Q. If PulseAudio is already installed, why do I need this guide?**
A. While PulseAudio has been installed by default since Hardy Heron  (8.04), we dropped the ball when it came to the configuration part. A  quote from the main PulseAudio developer, [Lennart Pöttering]("http://0pointer.de/blog/projects/jeffrey-stedfast.html"):     Quote:
                                                 Some distributions did a better job adopting PulseAudio than others.  On the good side I certainly have to list Mandriva, Debian, and Fedora.  OTOH Ubuntu didn't exactly do a stellar job. They didn't do their  homework. Adopting PA in a distribution is a fair amount of work, given  that it interfaces with so many different things at so many different  places. The integration with other systems is crucial. The information  was all out there, communicated on the wiki, the mailing lists and on  the PA IRC channel. But if you join and hang around on neither, then you  won't get the memo. To my surprise when Ubuntu adopted PulseAudio they  moved into one of their 'LTS' releases rightaway. Which I guess can be  called gutsy -- on the background that I work for Red Hat and PulseAudio  is not part of RHEL at this time. I get a lot of flak from Ubuntu  users, and I am pretty sure the vast amount of it is undeserving and not  my fault.                                 
When PulseAudio is running, it requires exclusive access to your  sound card in order to work correctly as it assumes responsibility for  mixing application's sounds instead of ALSA's "dmix" device. If you  launch a "regular" application that does not have explicit PulseAudio  support, it will most likely try to open the "Dmix" device - and this  will deprive PulseAudio of control over the sound card. From the user's  perspective, they will observe that audio mixing between applications is  broken. 

PulseAudio includes ALSA plugins (within the package  "libasound2-plugins") which are designed make regular ALSA applications  remap audio to the PulseAudio server (and thus avoid mixing problems as  described above). Unfortunately, Hardy Heron shipped without these  plugins enabled (or even installed) by default, which is causing many,  many audio mixing issues for users. To compound the problem, the version  of these PulseAudio ALSA plugins in the Hardy repositories do not  function correctly, so updated versions are required for ALSA  applications to work correctly with PulseAudio.

By following this guide, your system will be configured to use these  PulseAudio ALSA plugins for Hardy users (and updated versions of  necessary packages will get installed from my [PPA]("https://launchpad.net/%7Epsyke83/+archive")).  Although Intrepid has these plugins installed and configured by  default, following this guide is still worthwhile because a) it will  ensure you have a clean PulseAudio configuration, and b) you will  hopefully gain a better understanding of how PulseAudio works.

**Q. I'm glad to hear these issue are fixed in Intrepid, but why the  hell aren't they fixed in Hardy already?**
A. The simplest answer to this question is: complexity. Hardy is a LTS  (Long Term Support) release, and there is a very strict policy towards  updates (SRU; even the most trivial of bugfixes are entered into a code  review). In order to fix Hardy, many components will require updates and  changes, including but not limited to: libflashsupport, ia32-libs,  pulseaudio, libasound2, libasound2-plugins, flashplugin-nonfree,  nspluginwrapper...

Up until the last moment of Hardy's development cycle, the PulseAudio  ALSA plugins weren't functioning correctly, and Flash 9 absolutely would  not work without the "evil" libflashsupport library (I say evil,  because it caused frequent random crashes in Firefox) - and so it wasn't  possible to enact the required changes before the final release. It's  possible now, but there would require a huge amount of effort to review  and apply these changes.

**Q. I followed your guide and PulseAudio still doesn't work!**
A. Refer to Appendix A and provide the requested information in your  post.

**Q. I can't get Skype/WINE/an OSS application/XYZ working correctly  with PulseAudio, what can I do?**
A. Some applications require some extra configuration, and some  applications don't work with PulseAudio - please refer to Appendix C for  information on specific applications.

**Q. Where can I find the appropriate bug reports related to these  issues?**
A. If you click on a step number it will link to the appropriate bug  report, if one exists.

**[SIZE=4]Part A: Common instructions (Hardy, Intrepid, Jaunty  & Karmic)[/SIZE]**
*All users must must follow the steps in this section to guarantee a  fully working PulseAudio configuration.*

1. Backup (and then delete) your previous configuration files:      Code:
     $ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
$ rm -r ~/.pulse ~/.asound* 
$ sudo rm /etc/asound.conf 
[COLOR=Red]**Warning:** As always, use caution when  removing files on your system. Any typos can potentially cause data  loss.[/COLOR]
[COLOR=Blue]**Note:** Don't worry if some of these files did  not exist on your system.[/COLOR]


2. Ensure you have the necessary PulseAudio libraries and configuration  utilities installed:
     Code:
      $ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio 
[3]("https://bugs.launchpad.net/bugs/192888").  Ensure the evil "libflashsupport" library is **not** installed:     Code:
     $ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound 
[COLOR=Blue]**Note:** the libflashsupport library was  (and to a certain extent, still is) the most common cause of Firefox  instability since the Hardy release, because many users have been misled  into thinking they must install it to ensure Flash & PulseAudio can  work correctly. If you notice any postings that recommend this library  to be installed, please reply to the post and point them to this thread,  or the bug report linked. The more people that are aware of this issue  the better. Thanks![/COLOR]

4. (Karmic users - please skip this step, it's not necessary). Open  System/Preferences/Sound. In the Devices section, ensure that all "Sound  playback" options are set to Autodetect. Set the "Sound capture" item  to "ALSA", or the appropriate hardware definition. Close the application  when you're finished.
[COLOR=Blue]**Note:** Choosing PulseAudio for sound capture  may result in crashes, so you are advised to choose the "direct" ALSA  device instead.[/COLOR]

5. Open the PulseAudio Volume Control application ("pavucontrol", or you  can launch "Applications/Sound & Video/PulseAudio Device Chooser"  and select Volume Control from this applet's menu). In the Output  Devices section you will see a listing of the playback devices available  on your system. Right-click on the entry that you desire to be made the  default playback device on your system and enable the "Default"  checkmark. Similarly, navigate to Input Devices, then right-click on the  device you wish to set as your default input device (microphone), and  ensure the "Default" setting is checked. Close the application when  you're finished.

[COLOR=Blue]**Note:** If you are greeted with the error  "Connection failed: Connection refused", manually launch PulseAudio  before opening the PulseAudio Volume Control application:
     Code:
     $ pulseaudio & pavucontrol 
[/COLOR]6. Ensure that your sound card's PCM mixer is not muted or  set to 0% volume (this appears to be a common bug in Intrepid and  Jaunty):

     Code:
     $ alsamixer [COLOR=Blue]-Dhw[/COLOR] 
[COLOR=Blue]**Note:** When the PulseAudio ALSA plugins  are active, you must explicitly specify your hardware device in  alsamixer (marked in blue above), otherwise it will open the PulseAudio  mixer.[/COLOR]

7. Continue to **Part B** if you are running Hardy Heron (8.04), or **Part  C** if you are running Intrepid Ibex (8.10). If you are running  Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log  out and back in for changes to take effect!
REBOOT YOUR MACHINE TO MAKE SURE THE EFFECTS ARE TAKEN.

---

