---
title: "Upgrading to Studio from Feisty"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by ghostandmachine on 2007-06-08
just installed feisty fawn and am wanting to upgrade to studio. 

completed the instructions on this page [http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads)

when i go into the synpatic manger I search for the ubuntu studio files and try to install them but they all say that I require other files.

any ideas? thanks in advanced.

-gam

---

### Post by tgm4883 on 2007-06-08
Is it saying that it requires other files AND selecting those files for install also?

---

### Post by ghostandmachine on 2007-06-08
here's the error i'm getting when I select all of the ubuntustudio files to be marked for install 

ubuntustudio-artwork:
 Depends: ubuntustudio-look but it is not going to be installed
 Depends: ubuntustudio-theme but it is not going to be installed

ubuntustudio-audio:
 Depends: aconnectgui  but it is not installable
 Depends: ardour
 Depends: audacity  but it is not installable
 Depends: beast  but it is not installable
 Depends: bitscope  but it is not installable
 Depends: bristol  but it is not installable
 Depends: creox  but it is not installable
 Depends: csound  but it is not installable
 Depends: fluidsynth  but it is not installable
 Depends: freebirth  but it is not installable
 Depends: freqtweak  but it is not installable
 Depends: gtick  but it is not installable
 Depends: hydrogen  but it is not installable
 Depends: jack-rack  but it is not installable
 Depends: jack-tools  but it is not installable
 Depends: jackbeat  but it is not installable
 Depends: jackd  but it is not installable
 Depends: jackeq  but it is not installable
 Depends: jamin  but it is not installable
 Depends: jdelay  but it is not installable
 Depends: lilypond  but it is not installable
 Depends: lilypond-data  but it is not installable
 Depends: meterbridge  but it is not installable
 Depends: mixxx  but it is not installable
 Depends: muse  but it is not installable
 Depends: patchage  but it is not installable
 Depends: puredata  but it is not installable
 Depends: qamix  but it is not installable
 Depends: qjackctl  but it is not installable
 Depends: qsynth  but it is not installable
 Depends: rosegarden4  but it is not installable
 Depends: seq24  but it is not installable
 Depends: shaketracker  but it is not installable
 Depends: sooperlooper  but it is not installable
 Depends: swami  but it is not installable
 Depends: tapiir  but it is not installable
 Depends: terminatorx  but it is not installable
 Depends: timemachine  but it is not installable
 Depends: timidity  but it is not installable
 Depends: tk707  but it is not installable
 Depends: vkeybd  but it is not installable
 Depends: wired but it is not going to be installed
 Depends: xmms-jackasyn  but it is not installable
 Depends: xmms-modplug  but it is not installable
 Depends: zynaddsubfx  but it is not installable
 Recommends: linux-image-lowlatency  but it is not installable

ubuntustudio-audio-plugins:
 Depends: blop  but it is not installable
 Depends: caps  but it is not installable
 Depends: cmt  but it is not installable
 Depends: dssi-example-plugins  but it is not installable
 Depends: dssi-host-jack  but it is not installable
 Depends: dssi-plugin-fluidsynth  but it is not installable
 Depends: dssi-plugin-hexter  but it is not installable
 Depends: dssi-plugin-xsynth  but it is not installable
 Depends: dssi-utils  but it is not installable
 Depends: fil-plugins  but it is not installable
 Depends: ladspa-sdk  but it is not installable
 Depends: mcp-plugins  but it is not installable
 Depends: omins  but it is not installable
 Depends: swh-plugins  but it is not installable
 Depends: tap-plugins  but it is not installable
 Depends: vcf-plugins  but it is not installable

ubuntustudio-default-settings:
 Depends: ubuntustudio-artwork but it is not going to be installed

ubuntustudio-desktop:
 Depends: gtk2-engines-murrine  but it is not installable
 Depends: nautilus-actions  but it is not installable
 Depends: nautilus-script-manager  but it is not installable
 Depends: ntfs-3g  but it is not installable
 Depends: ubuntustudio-artwork but it is not going to be installed
 Recommends: ubuntustudio-default-settings but it is not going to be installed

ubuntustudio-gdm-theme:

ubuntustudio-graphics:
 Depends: agave  but it is not installable
 Depends: blender  but it is not installable
 Depends: enblend  but it is not installable
 Depends: gimp-gap  but it is not installable
 Depends: gimp-svg  but it is not installable
 Depends: gimp-ufraw  but it is not installable
 Depends: gnome-raw-thumbnailer  but it is not installable
 Depends: hugin  but it is not installable
 Depends: nautilus-image-converter  but it is not installable
 Depends: synfigstudio  but it is not installable
 Depends: yafray  but it is not installable

ubuntustudio-look:
 Depends: ubuntustudio-theme but it is not going to be installed

ubuntustudio-theme:
 Depends: gtk2-engines-murrine  but it is not installable

ubuntustudio-video:
 Depends: cinepaint  but it is not installable
 Depends: dvgrab  but it is not installable
 Depends: ffmpeg  but it is not installable
 Depends: ffmpeg2theora  but it is not installable
 Depends: pitivi  but it is not installable
 Depends: stopmotion  but it is not installable

---

### Post by Stinger on 2007-06-08
Hi ,
I'm running ubuntustudio , I upgraded from Feisty using this guide :

[UpgradingFromFeisty]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty")

Only hickup I had was the nvidia driver not working but I solved that booting into the old feisty kernel ,  installing the nvidia packages for the low latencety ubuntustudio kernel and rebooting. 

Hope it helps

---

### Post by ghostandmachine on 2007-06-09
I'm still receiving the same error. Is there a way to mount an iso of ubuntu studio and install it that way?

---

### Post by ghostandmachine on 2007-06-09
I finally got studio installed. I used the script that was at the end of the post you sent me. I guess i'll have to look over the script to see what I did wrong. thank you again for your help.

---

### Post by Stinger on 2007-06-10
So glad you got it going , ubuntustudio is IMHO the best of the ubuntu's available , I just love the lowlatencety kernel and the Jack audio applications , not to forget the beautifull artwork.

I would recommed anyone interested in multimedia , music and graphics to try it.

Ubuntustudio rocks !!!!!

:guitar:

Stinger.

---

### Post by dysonsphere23 on 2007-06-12
> **Stinger said:**
> Hi ,
I'm running ubuntustudio , I upgraded from Feisty using this guide :

[UpgradingFromFeisty]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty")

Only hickup I had was the nvidia driver not working but I solved that booting into the old feisty kernel ,  installing the nvidia packages for the low latencety ubuntustudio kernel and rebooting. 

Hope it helps

What exactly would those packages be?  And can I install them before the upgrade?

---

### Post by Stinger on 2007-06-12
The two only packages needed would be the "linux-restricted-modules-lowlatency" packages.
It should be possible to add them after you added the Ubuntustudio repo's.

So after you added the repo's following the guide , do this

```
sudo apt-get install linux-restricted-modules-lowlatency linux-restricted-modules-2.6.20-16-lowlatency
```

and continue with

"Install Ubuntu Studio"

I havent tried it myself but I see absolutely no reson why it shouldn't work.

Hope it helps.

---

