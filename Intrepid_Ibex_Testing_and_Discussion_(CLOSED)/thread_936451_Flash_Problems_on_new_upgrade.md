---
title: "Flash Problems on new upgrade"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by PRGUY85 on 2008-10-02
Hey:

I just upgraded from Hardy to Intrepid through "sudo update-manager -d".  Everything is great except Flash performance on any browser.  If I visit Flash intensive sites such as ESPN or Hulu, I get slow load times, slow scrolling time, crashes and image flickering inside the page.

I know Flash got upgraded on the dist-upgrade since I saw the package being downloaded and installed.  This is Flash 10, is anyone else having problems with it?

---

### Post by wilsong on 2008-10-02
There have been people posting with issues with Flash and 64bit version.. are you 32x or 64x?

---

### Post by psyke83 on 2008-10-02
> **PRGUY85 said:**
> Hey:

I just upgraded from Hardy to Intrepid through "sudo update-manager -d".  Everything is great except Flash performance on any browser.  If I visit Flash intensive sites such as ESPN or Hulu, I get slow load times, slow scrolling time, crashes and image flickering inside the page.

I know Flash got upgraded on the dist-upgrade since I saw the package being downloaded and installed.  This is Flash 10, is anyone else having problems with it?

The version of Flash we have is outdated, with well-known performance issues. An update is coming soon (when 64 bit issues are resolved), so you can wait patiently, or get it from my PPA. See the [PulseAudio]("http://ubuntuforums.org/showthread.php?t=866965") thread for more information, and the FFe is filed as [bug #257403]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403").

---

### Post by PRGUY85 on 2008-10-02
I'm running on 32x.

This is the sort of thing I want working on Intrepid BEFORE seeing a new theme :)

---

### Post by PRGUY85 on 2008-10-02
Using psyke's repo and its flash plugin upgrade solved the trick.  Thanks a bunch.

---

### Post by ktp on 2008-10-02
> **PRGUY85 said:**
> Using psyke's repo and its flash plugin upgrade solved the trick.  Thanks a bunch.

Ya, 8.10 is working great on 32-bit version when it comes to flash and PulseAudio.  I can't wait until Luke fixes the 64-bit issue, which should be coming very soon.

---

### Post by wilsong on 2008-10-02
Im using the 64 Bit version of Ubuntu 8.10 Interpid and for some reason ive always had working Flash, im not sure how or why but its always worked..

---

### Post by ktp on 2008-10-03
Are you using the nofree version from adobe?  The nofree plugin has known issues:
nspluginwrapper not supporting WindowlessMode correctly:
[https://bugs.launchpad.net/fedora/+source/nspluginwrapper/+bug/272286](https://bugs.launchpad.net/fedora/+source/nspluginwrapper/+bug/272286)
Workaround is to disable windowless mode in the plugin itself by adding following to /etc/adobe/mms.cfg
   WindowlessDisable=true
This still does not solve all the issues for me, but is pretty stable on most sites.

And PulseAudio Sound issues on 64-bit:
Workaround which works:
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/6](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/6)

Another workaround that works for me:
1. Create /etc/ld.so.conf.d/alsa32.conf with the following contents:
/usr/lib32/alsa-lib

2. Create /etc/ld.so.conf.d/alsa64.conf with the following contents:
/usr/lib/alsa-lib

3. sudo ldconfig

4. Open /usr/share/alsa/pulse.conf in the editor and remove the "/usr/lib/alsa-lib/" prefix from the libasound_module_conf_pulse.so file.

---

