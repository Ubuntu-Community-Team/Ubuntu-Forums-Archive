---
title: "VLC Crashes When Jumping forward after upgrade to 14.04"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by chrisdebo on 2014-04-24
I know others are experiencing the problem where they have upgraded to Ubuntu 14.04 and then VLC will not navigate w/o crashing. You cannot jump forward or use the mouse on the duration slider. What gives and how is this c:confused:orrectable?

---

### Post by andrew.46 on 2014-04-24
Sometimes with an upgraded Ubuntu as well as an upgraded vlc the configuration file for vlc can be a little awry, try the following in a terminal:

```

cvlc --reset-config && cvlc --reset-plugins-cache

```

and this might be enough. If this has no effect time perhaps to dig a little deeper :)

---

### Post by chrisdebo on 2014-04-25
This is the output from the cvlc commands above:
[email]chris@Gig:~/.config[/email]$ cvlc --reset-config %% cvlc --reset-plugins-cache
VLC media player 2.1.2 Rincewind (revision 2.1.2-0-ga4c4876)
[0x2109108] dummy interface: using the dummy interface module...
[0x7f552c001158] filesystem access error: cannot open file /home/chris/.config/%% (No such file or directory)
[0x7f552c001158] main access error: File reading failed
[0x7f552c001158] main access error: VLC could not open the file "/home/chris/.config/%%" (No such file or directory).
[0x7f5534003f58] main input error: open of `file:///home/chris/.config/%25%25' failed
[0x7f5534003f58] main input error: Your input can't be opened
[0x7f5534003f58] main input error: VLC is unable to open the MRL 'file:///home/chris/.config/%25%25'. Check the log for details.
[0x7f552c000e38] filesystem access error: cannot open file /home/chris/.config/cvlc (No such file or directory)
[0x7f552c000e38] main access error: File reading failed
[0x7f552c000e38] main access error: VLC could not open the file "/home/chris/.config/cvlc" (No such file or directory).
[0x7f5534003f58] main input error: open of `file:///home/chris/.config/cvlc' failed
[0x7f5534003f58] main input error: Your input can't be opened
[0x7f5534003f58] main input error: VLC is unable to open the MRL 'file:///home/chris/.config/cvlc'. Check the log for details.
^Cchris@Gig:~/.config$ vlc
VLC media player 2.1.2 Rincewind (revision 2.1.2-0-ga4c4876)
[0x219c118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.


I have tried uninstalling vlc and deleting the HOME/chris/.config/vlc folder and reinstalling, but the problem of vlc crashing persists.

Please help,
Thanks, Chris

---

### Post by andrew.46 on 2014-04-25
The command uses the **[COLOR="#FF0000"]&[/COLOR]** character not the **[COLOR="#FF0000"]%[/COLOR]** character :)

---

### Post by chrisdebo on 2014-04-25
With all due respect, the concatenation symbol is not the main error shown in the listing. I tried the same parameters with vlc i/o cvlc and it completed with no errors. It seems to be crashing less after more jumps than before.

---

### Post by andrew.46 on 2014-04-26
Perhaps it is worthwhile to then look at the video and audio outputs that vlc is set to use and see if a few experimental changes fix your issue. As you may already know video can be seen at: Tools --> Preferences --> Video --> Output. While in that area see if toggling the 'Accelerated Video Output (Overlay)' setting is helpful or not.

---

### Post by chrisdebo on 2014-04-26
Thanks, Andrew, I'll try toggling the [COLOR=#000000] 'Accelerated Video Output (Overlay)' setting. I don't have any ideas what video--> output options are optimal. I am running my ubuntu box connected to a flatscreen tv via hdmi.[/COLOR]

---

### Post by chrisdebo on 2014-04-27
[COLOR=#000000]Turning off the [/COLOR][COLOR=#000000][COLOR=#000000]'Accelerated Video Output (Overlay)' setting made VLC inoperable. VLC is still crashing after jumping forward about four times. I have run VLC with the reset options several times, but it doesn't seem to make a difference. The only thing that has changed since it worked flawlessly was allowing Ubuntu to upgrade to 14.04.[/COLOR][/COLOR]

---

### Post by andrew.46 on 2014-04-27
In that case I am afraid that I am out of ideas. Hopefully somebody with a clearer view can see a solution. FWIW I usually do not upgrade, usually only backup and clean installation and perhaps it might come to this for you as well...

---

### Post by chrisdebo on 2014-04-27
All I can say is "whoops"; I shall not upgrade again if I can get things working the way they are supposed to.

---

### Post by chrisdebo on 2014-04-28
I ran VLC from the command line so I could capture any messages. The messages below are the ones produced after I started jumping forward until it crashed:

Non-reference picture received and no reference available
[h264 @ 0x7f0f14c491a0] decode_slice_header error
[h264 @ 0x7f0f14c49da0] mmco: unref short failure
Non-reference picture received and no reference available
[h264 @ 0x7f0f14c491a0] decode_slice_header error
[h264 @ 0x7f0f14c49da0] mmco: unref short failure
[h264 @ 0x7f0f14c4a1e0] illegal short term buffer state detected
Non-reference picture received and no reference available
[h264 @ 0x7f0f14c491a0] decode_slice_header error
[h264 @ 0x7f0f14c49da0] mmco: unref short failure
Non-reference picture received and no reference available
[h264 @ 0x7f0f14c491a0] decode_slice_header error
[h264 @ 0x7f0f14c49da0] mmco: unref short failure
[h264 @ 0x7f0f14c4a1e0] illegal short term buffer state detected
Non-reference picture received and no reference available
[h264 @ 0x7f0f14c491a0] decode_slice_header error
[h264 @ 0x7f0f14c49da0] mmco: unref short failure
Segmentation fault

---

### Post by andrew.46 on 2014-04-28
Interestingly enough something similar here, although skipping forward is not mentioned,:

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=741240](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=741240)

Rémi Denis-Courmont  is one of the vlc developers and his hints were disable hardware acceleration and get a newer libavcodec...

---

### Post by chrisdebo on 2014-04-29
Om,
I checked and hardware acceleration is Off by default (I have VLC 2.1.2). I used aptitude to look at my installed packages, and libavcodec54 is already installed.:confused:

---

### Post by andrew.46 on 2014-04-29
Looks like for Trusty libavcodec is based on libav 9.11 (libav9.12 was released on 2014-03-14) but remember this is based on a release from the git master on 2013-01-05 :(. Version 10.0 came out on  2014-03-23. Details here:

[http://libav.org/download.html](http://libav.org/download.html)

So by no means does Trusty carry a cutting edge libavcodec, but I guess it is not meant to.  Unfortunately I am out of ideas, with any luck others may encounter the same problem and hopefully come up with a fix...

---

### Post by peryn on 2014-04-29
Have same problem :(

---

### Post by chrisdebo on 2014-05-01
Here is some additional info that may help:
chris@Gig:~$ vainfo
libva info: VA-API version 0.35.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

In /usr/lib/x86_64-linux-gnu/dri, I have a i915_dri.so, i965_dri.so, and dummy_drv_video.so but no i965_drv_video.so
my chipset is actually i915.
I loaded the latest intel driver, no change.

---

### Post by chrisdebo on 2014-05-02
I have resolved the problem. After tons of research, I became to believe that the problem was most likely a broken library link or some other missing dependency.

I believe the REAL problem is that my PC requires proprietary video drivers that are not part of the Ubuntu repository. So when an install/upgrade from the approved repository is applied, the non-repository drivers are overwritten, thus hosing the operation. I think I should be able to apply "approved" updates to Ubuntu w/o my personal changes being affected. You would think that I could protect my changes by ownership or permissions settings. Anyway, I wish I could have logically corrected the problem i/o hit and miss, but I guess I don't understand enough. I gutted software from my install, installed the intel drivers and then VLC and it is working great now.

Here are the steps I took:
Removed VLC: apt-get remove vlc then apt-get purge vlc

Used aptitude to view installed packages of libavcodec

Purged these packages using apt-get with the following options: purge autoremove autoclean

Went to intel website to download latest drivers ([https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)). Downloaded xf86-video-intel -2.99.910 and installed using the Archive Manager.

Reinstalled vlc. Reran /usr/lib/vlc/vlc-cache-gen -f usr/lib/vlc/plugins just for grins.

Went into the VLC preferences, which for this download of v2.1.2, harware accelerated decoding was set to "automatic". I could have sworn that the last install's default value was "off". Set harware acceleration of "off" on Inputs/Codecs Settings page. Went to Video Settings tab and unchecked accelerated video output (Overlay). Now things are back to normal.  I wish I knew which of the(se) steps made the difference.

I installed the intel vaapi driver and turned hardware acceleration back on in VLC, which caused it to crash again. So I reversed these changes back to working order and will probably never update it again! Too much trial and error.

---

