---
title: "Zotac Zbox ION install guide"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by jcostom on 2011-02-06
I had the bug for a Boxee system.  After looking at a bunch of different small HTPC options, I settled on the [Zotac ZBOXHD-ND22-U]("http://www.zotacusa.com/zotac-zbox-zboxhd-nd22-u-intel-celeron-su2300-1-2-ghz-dual-core-all-in-one-mini-pc.html") system.  Highlights of the box:

[LIST]
[*]Dual-core 1.2 Ghz CULV CPU
[*]ION chipset, handles up to 8GB of DDR3 (PC3-8500)
[*]2.5" SATA bay
[*]6xUSB2 ports, front SD slot
[*]HDMI port, supporting up to 7.1 audio
[/LIST]

After a good bit of research, I opted to install Maverick instead of Lucid, since Maverick includes the required ALSA 1.0.23 release.  This isn't an utterly complete cookbook.  I'm doing this from memory... Here's what I did, roughly in order:

1. Install Maverick via a USB stick (built with Unetbootin).  I selected Maverick x86, so I wouldn't have to muck around with the whole 32-bit flash on amd64 business, particularly in an embedded environment.

2. Removed gdm - we'll be booting directly into Boxee here.  aptitude remove gdm, also let it remove the dependencies.  Later, I went back and removed extraneous packages, like all of the gnome desktop stuff.  Seemed fairly pointless to keep it around.

3. Added this to the end of /etc/modprobe.d/alsa-base.conf:

```
# For Nvidia ION
options snd-hda-intel model=3stack

```

4. Created the following /etc/asound.conf:

```
pcm.!default {
type hw
card 0
device 3
}
ctl.!default {
type hw
card 0
}

```

5. Installed mingetty (aptitude install mingetty).

6. Installed binary Nvidia drivers.  I opted to use the download from Nvidia's site, rather than the Ubuntu packages.  If you want to roll with packages, I believe there's a PPA that maintains the latest & greatest drivers.

7. Installed the Medibuntu repository, per the directions on medibuntu.org.

8. Installed boxee, using the package downloaded from boxee.tv.  It will have some package dependencies that likely didn't get installed.

9. Altered /etc/init/tty1.conf:

```

......
respawn
#exec /sbin/getty -8 38400 tty1
exec /sbin/mingetty --noclear --autologin boxee tty1

```

10. The boxee user (I created it during install) gets a bit of mod to its .bashrc and gets a .xsession:

.xsession:
```

#!/bin/bash
/usr/bin/pulseaudio --start --log-target=syslog
exec dbus-launch /opt/boxee/run-boxee-desktop

```

.bashrc:
```

.......
case `tty` in
        /dev/tty[1])
                noAutorunXParam=splash
                cmdLineParams=`cat /proc/cmdline`

                runX=`echo $cmdLineParams | grep $noAutorunXParam | wc -l`
                if [ "$runX" == 0 ]; then
                        echo "Not starting X."
                else
                        echo "Autostarting X..."
                        startx -- -br
                        logout
                fi
        ;;
esac

```

On my install, using a 64gb SSD, I go from power up to looking at Boxee in about 10 seconds.

I found a Windows Media Center USB IR receiver in a drawer, hooked that up and installed lirc.  I told lirc it was a Windows Media Center dongle, which uses the mceusb config.  Boxee was pre-configured to understand the remote.  I programmed our Harmony One to pretend it's a Windows Media Center box, and it's all good.

I'm happily pumping out 1080p with 5.1 sound.  The box also has a WLAN card installed, but I'm not using it, as I've already got a WLAN bridge in my entertainment center.  The NIC uses forcedeth, and works out of the box.

---

### Post by Henk Poley on 2011-02-13
Already a thanks for this topic, my ZBOX HD-ND22 will arrive the coming week. Some remarks:

Point 1. Is 32bit flash really problematic? As far as I know you just install the packaged flash, and it will use a wrapper to run it as 32 bit under a (possibly) 64 bit browser. Much like the flash process isolation already used to work under 32bit Gentoo when I used it back in 2004.

Point 3. Thanks. These kind of hacks for HDMI audio are difficult to track down. Is it still necessary? I see mentions of it going back to 2008.

Point 4. I suspect alternatively you could disable the onboard audio in the BIOS setup. Or do these lines do something different than override what is the default audio card?

Point 6. The PPA with current X drivers (like nvidia's) is described at: [http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)

---

### Post by Henk Poley on 2011-03-07
I'm currently trying put this machine in standby, but the default Ubuntu way (powerbutton & on screen buttons) only put it into hibernation. I already tried toggling the S1/S3/Auto option in the BIOS.

If anybody has any information on how to debug this, I'd appreciate that.

---

