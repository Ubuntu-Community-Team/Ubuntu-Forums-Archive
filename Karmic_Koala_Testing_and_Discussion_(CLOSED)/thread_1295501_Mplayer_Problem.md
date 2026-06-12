---
title: "Mplayer Problem?"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kraust on 2009-10-19
I updated to Karmic yesterday to test out the updated Flash support and overall improvements to the speed on my computer (it's significant) but when I try to run mplayer I get this error:

```
kraust@ubuntu:~$ mplayer
mplayer: error while loading shared libraries: libdirectfb-1.0.so.0: cannot open shared object file: No such file or directory

```

So I tried to see if it was there or not, and 2 other files weren't there:

```
kraust@ubuntu:~$ ldd /usr/bin/mplayer
	linux-gate.so.1 =>  (0x00994000)
	libdirectfb-1.2.so.0 => /usr/lib/libdirectfb-1.2.so.0 (0x00133000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00469000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x009ee000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00f63000)
	libXv.so.1 => /usr/lib/libXv.so.1 (0x00936000)
	libXvMC.so.1 => /usr/lib/libXvMC.so.1 (0x009d7000)
	libXvMCW.so.1 => /usr/lib/libXvMCW.so.1 (0x003e0000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x0031e000)
	libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0x00b26000)
	libXxf86dga.so.1 => /usr/lib/libXxf86dga.so.1 (0x001e9000)
	libggi.so.2 => /usr/lib/libggi.so.2 (0x00811000)
	libaa.so.1 => /usr/lib/libaa.so.1 (0x00b9f000)
	libcaca.so.0 => /usr/lib/libcaca.so.0 (0x0073b000)
	libvga.so.1 => /usr/lib/libvga.so.1 (0x00df8000)
	libGL.so.1 => /usr/lib/libGL.so.1 (0x001f0000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x002ca000)
	libSDL-1.2.so.0 => /usr/local/lib/libSDL-1.2.so.0 (0x00321000)
	libesd.so.0 => /usr/lib/libesd.so.0 (0x00110000)
	libaudio.so.2 => /usr/lib/libaudio.so.2 (0x006ab000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0x00bc1000)
	libpulse.so.0 => /usr/lib/libpulse.so.0 (0x00269000)
	libjack.so.0 => /usr/lib/libjack.so.0 (0x001ad000)
	libopenal.so.1 => /usr/lib/libopenal.so.1 (0x00c81000)
	libfaac.so.0 => /usr/lib/libfaac.so.0 (0x0011c000)
	libx264.so.67 => /usr/lib/libx264.so.67 (0x00479000)
	libmp3lame.so.0 => /usr/lib/libmp3lame.so.0 (0x003e6000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00f7c000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x0051b000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x001c9000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x002ce000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x002a9000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00908000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x002f7000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0x005d3000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00e78000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x006c5000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x06c21000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00669000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x008b8000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x0012e000)
	libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0x04feb000)
	liblirc_client.so.0 => /usr/lib/liblirc_client.so.0 (0x002c3000)
	libncurses.so.5 => /lib/libncurses.so.5 (0x00b51000)
	libsmbclient.so.0 => /usr/lib/libsmbclient.so.0 (0x0133d000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x0070d000)
	libz.so.1 => /lib/libz.so.1 (0x00304000)
	libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0x003bc000)
	libgif.so.4 => /usr/lib/libgif.so.4 (0x0045d000)
	libasound.so.2 => /usr/lib/libasound.so.2 (0x0182d000)
	libcdda_interface.so.0 => /usr/lib/libcdda_interface.so.0 (0x00696000)
	libcdda_paranoia.so.0 => /usr/lib/libcdda_paranoia.so.0 (0x00c18000)
	libfribidi.so.0 => /usr/lib/libfribidi.so.0 (0x007e3000)
	libenca.so.0 => /usr/lib/libenca.so.0 (0x0093c000)
	liblzo2.so.2 => /usr/lib/liblzo2.so.2 (0x00963000)
	libmad.so.0 => /usr/lib/libmad.so.0 (0x007f2000)
	libspeex.so.1 => /usr/lib/libspeex.so.1 (0x00995000)
	libtheora.so.0 => /usr/lib/libtheora.so.0 (0x00c22000)
	libogg.so.0 => /usr/lib/libogg.so.0 (0x0080a000)
	libmpcdec.so.3 => /usr/lib/libmpcdec.so.3 (0x00ddd000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x09c9a000)
	libopencore-amrnb.so.0 => /usr/lib/libopencore-amrnb.so.0 (0x00d9e000)
	libopencore-amrwb.so.0 => /usr/lib/libopencore-amrwb.so.0 (0x009ac000)
	libdv.so.4 => /usr/lib/libdv.so.4 (0x00eff000)
	libxvidcore.so.4 => /usr/lib/libxvidcore.so.4 (0x02eb6000)
	libdirac_encoder.so.0 => /usr/lib/libdirac_encoder.so.0 (0x018f4000)
	libdirac_decoder.so.0 => /usr/lib/libdirac_decoder.so.0 (0x0978f000)
	libschroedinger-1.0.so.0 => /usr/lib/libschroedinger-1.0.so.0 (0x01988000)
	liboil-0.3.so.0 => /usr/lib/liboil-0.3.so.0 (0x03edb000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x00b45000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00e59000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x01a09000)
	libdirect-1.2.so.0 => /usr/lib/libdirect-1.2.so.0 (0x00b2c000)
	libfusion-1.2.so.0 => /usr/lib/libfusion-1.2.so.0 (0x008f6000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x0031a000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00f29000)
	/lib/ld-linux.so.2 (0x005b6000)
	libvgagl.so.1 => /usr/lib/libvgagl.so.1 (0x009c6000)
	libgii.so.1 => /usr/lib/libgii.so.1 (0x0786e000)
	libgg.so.1 => /usr/lib/libgg.so.1 (0x00985000)
	libslang.so.2 => /lib/libslang.so.2 (0x07e48000)
	libgpm.so.2 => /usr/lib/libgpm.so.2 (0x00900000)
	libncursesw.so.5 => /lib/libncursesw.so.5 (0x01b4d000)
	libx86.so.1 => /lib/libx86.so.1 (0x005b0000)
	libGLcore.so.1 => /usr/lib/libGLcore.so.1 (0x01b90000)
	libnvidia-tls.so.1 => /usr/lib/tls/libnvidia-tls.so.1 (0x001e6000)
	libaudiofile.so.0 => /usr/lib/libaudiofile.so.0 (0x09f5c000)
	[b]libdirectfb-1.0.so.0 => not found
	libfusion-1.0.so.0 => not found
	libdirect-1.0.so.0 => not found[/b]
	libSM.so.6 => /usr/lib/libSM.so.6 (0x009dc000)
	libpulsecommon-0.9.19.so => /usr/lib/libpulsecommon-0.9.19.so (0x022e1000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0x00f47000)
	libXtst.so.6 => /usr/lib/libXtst.so.6 (0x00735000)
	libwrap.so.0 => /lib/libwrap.so.0 (0x009e5000)
	libsndfile.so.1 => /usr/lib/libsndfile.so.1 (0x0372d000)
	libdbus-1.so.3 => /lib/libdbus-1.so.3 (0x04ad8000)
	libsamplerate.so.0 => /usr/lib/libsamplerate.so.0 (0x0232b000)
	libcelt.so.0 => /usr/lib/libcelt.so.0 (0x00b89000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x006a7000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00466000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x0092e000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00dd1000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x00ded000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00b1d000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x04799000)
	libpcre.so.3 => /lib/libpcre.so.3 (0x05890000)
	libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0x05dc4000)
	libselinux.so.1 => /lib/libselinux.so.1 (0x0778b000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x07c34000)
	libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0x00c78000)
	libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0x09bba000)
	libexpat.so.1 => /lib/libexpat.so.1 (0x03daa000)
	libtalloc.so.1 => /usr/lib/libtalloc.so.1 (0x05c91000)
	libwbclient.so.0 => /usr/lib/libwbclient.so.0 (0x069a4000)
	libcap.so.2 => /lib/libcap.so.2 (0x02497000)
	libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0x06811000)
	libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0x047bd000)
	libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0x09095000)
	libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0x0249d000)
	libcom_err.so.2 => /lib/libcom_err.so.2 (0x00bbd000)
	libldap_r-2.4.so.2 => /usr/lib/libldap_r-2.4.so.2 (0x024c8000)
	liblber-2.4.so.2 => /usr/lib/liblber-2.4.so.2 (0x02513000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x06499000)
	libuuid.so.1 => /lib/libuuid.so.1 (0x0360b000)
	libFLAC.so.8 => /usr/lib/libFLAC.so.8 (0x05265000)
	libvorbisenc.so.2 => /usr/lib/libvorbisenc.so.2 (0x059eb000)
	libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0x02522000)
	libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0x05eeb000)
	libkeyutils.so.1 => /lib/libkeyutils.so.1 (0x00c14000)
	libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0x06014000)
	libgnutls.so.26 => /usr/lib/libgnutls.so.26 (0x04bf3000)
	libtasn1.so.3 => /usr/lib/libtasn1.so.3 (0x04344000)
	libgcrypt.so.11 => /lib/libgcrypt.so.11 (0x03dd7000)
	libgpg-error.so.0 => /lib/libgpg-error.so.0 (0x0254d000)

```

I probably have the file around there somewhere. I'm guessing I have to make a symbolic link of it to that Directory but I don't know where it could be.

Also I have libdirectfb-1.2.so.0 in /usr/lib but there is no libdirectfb-1.0.so.0 in that directory.

I already tried a Purge, and I also compiled it from Source earlier today.

---

### Post by Kraust on 2009-10-19
I still need a fix, or a media player that will be lightweight and play my avis, and subtitles + mkvs properly.

---

### Post by mc4man on 2009-10-19
What version of mplayer is installed? (check in synaptic

Did you do an upgrade or fresh install?

---

### Post by Kraust on 2009-10-19
It's a fresh install, I've removed it with sudo apt-get remove --purge mplayer more than once, and the latest version I have now is from Synaptic. As for the version it says 2:1.0~rc3+svn20090904-0karmic1

---

### Post by mc4man on 2009-10-19
If you were to go in terminal this, does it open?
gmplayer

There isn't an mplayer in /usr/local/bin is there?

(vlc should be able to play your files, but it's curious mplayer is 'looking' for those .so's (jaunty versions

---

### Post by mc4man on 2009-10-19
Your using a ppa for mplayer?,( rvm ppa),  maybe for the moment remove it from your sources and also remove all mplayer packages, ect.

Then try the karmic repo version of mplayer

---

### Post by Kraust on 2009-10-19
gmplayer gives the same error as mplayer, and there isn't any mplayer in usr/local/bin

Also, I recently uninstalled VLC and now that I've reinstalled it I can't get it to work either.

```
No suitable decoder module:
VLC does not support the audio or video format "avc1". Unfortunately there is no way for you to fix this.
```

And for that matter I can't get Totem to work. It gives me an error that reads "GStreamer encountered a general stream error."

I really messed something up here <_<.


EDIT~
> **mc4man said:**
> Your using a ppa for mplayer?,( rvm ppa),  maybe for the moment remove it from your sources and also remove all mplayer packages, ect.

Then try the karmic repo version of mplayer

I'll check this out as well.

---

### Post by mc4man on 2009-10-19
Did you add a ppa for Openshot? ( the openshot ffmpeg libs break totem and vlc

If not what version of libavcodec52 are you using ( normal or 'extra'


( What I'd do

Go System -> Admin -> Software Sources and disable all 'Third Party sources, clic close and reload

Then open synaptic, search mplayer and remove all, search ffmpeg and remove all (libavcodec52 ect.

Then re-install mplayer, and or vlc ( from the karmic repo

Then search ffmpeg again and enable the extra versions of libavcodec, libavformat, ect. ( don't remove the existing ones, just mark the 'extra's for install and apply

If you want also then install the gstreamer0.10-ffmpeg package

If you then have mplayer working you could re-enable the rvm ppa and update to the 2:1.0~rc3+svn20090904-0karmic1 ver.

( even though the author said a few hours ago he didn't dl. a karmic version yet ...?

I've tested that ppa version and seems to work fine

[http://ubuntuforums.org/showthread.php?p=8131236#post8131236](http://ubuntuforums.org/showthread.php?p=8131236#post8131236) ( post above mine

---

### Post by Kraust on 2009-10-19
I got Totem and VLC fixed but I still can't get rid of the error in my initial post. It keeps on askfing for libdirectfb-1.0.so.0.

Apparently, I don't have the ppa for the karmic version, and synaptic is only giving me 2:1.0~rc3+svn20090426-0ubuntu1 vs what you suggested 2:1.0~rc3+svn20090904-0karmic1

updated the version to 2:1.0~rc3+svn20090904-0karmic1

[B]
STILL, I get that error.[/B], let me reenable all of my sources and check for updates, maybe it's in there.

---

