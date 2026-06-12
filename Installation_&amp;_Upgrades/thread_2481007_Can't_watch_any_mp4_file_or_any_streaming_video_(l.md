---
title: "Can't watch any mp4 file or any streaming video (like youtube) after upgrading ubuntu"
date: 2022-11-16
forum: Installation &amp; Upgrades
---

### Post by marietto2008 on 2022-11-16
Hello,

I've just upgraded Ubuntu 22.04 to 22.10. Everything seems to work great except Firefox,mplayer and I suppose any other mp4 player which belongs to a codec (maybe ffmpeg ?) or any other codec that hasn't been installed or reinstalled properly. Below you can see the errors that I see on the upgraded ubuntu 22.10 :

```
ziomario@Z390-AORUS-PRO-DEST:~/Scrivania$ firefox

[GFX1-]: More than 2 GPUs detected via PCI, secondary GPU is arbitrary

ATTENTION: default value of option mesa_glthread overridden by environment.
ATTENTION: default value of option mesa_glthread overridden by environment.
ATTENTION: default value of option mesa_glthread overridden by environment.
ATTENTION: default value of option mesa_glthread overridden by environment.

[2022-11-06T16:55:34Z ERROR mp4parse] Found 2 nul bytes in "\0\0"
[2022-11-06T16:55:34Z ERROR mp4parse] Found 2 nul bytes in "\0\0"
[2022-11-06T16:55:34Z ERROR mp4parse] Found 2 nul bytes in "\0\0"
[2022-11-06T16:55:36Z ERROR mp4parse] Found 2 nul bytes in "\0\0"
[2022-11-06T18:10:17Z ERROR viaduct::backend::ffi] Missing HTTP status
[2022-11-06T18:10:17Z ERROR viaduct::backend::ffi] Missing HTTP status
[2022-11-06T18:10:17Z ERROR viaduct::backend::ffi] Missing HTTP status
[2022-11-06T18:10:17Z ERROR viaduct::backend::ffi] Missing HTTP status
[2022-11-06T18:10:17Z ERROR viaduct::backend::ffi] Missing HTTP status
```

The problem is that when I try to open any video on youtube,for example,I get the error that you see above and it freezes. I've tried to look for a solution posting the error here:

[https://bugzilla.mozilla.org/show_bug.cgi?id=1772085#c19](https://bugzilla.mozilla.org/show_bug.cgi?id=1772085#c19)

developers say that the errors displayed aren't the cause of the problem. They are right. Infact I have installed ubuntu 22.10 from scratch and I saw those errors,but I can play the mp4 videos without problems. BUT if I upgrade ubuntu 22.04 to 22.10,in addition to see the errors,the video stream does not flow automatically. So,I suppose that something breaks during the upgrade. On ubuntu 22.10 (upgraded from 22.04) the ffmpeg and the ubuntu-restricted-extras package results already installed. I can play mp4 files using vlc without problems,but not with mplayer...

This is also what I tried to do :

```
#sudo dpkg-reconfigure libdvd-pkg

libdvd-pkg: Downloading orig source...
I: libdvdcss_1.4.3
/usr/bin/wget --tries=3 --timeout=40 --read-timeout=40 --continue -O libdvdcss_1.4.3.orig.tar.bz2 \
**********https://download.videolan.org/pub/libdvdcss/1.4.3/libdvdcss-1.4.3.tar.bz2 \
********|| /usr/bin/uscan --noconf --verbose --rename --destdir=/usr/src/libdvd-pkg --check-dirname-level=0 --force-download --download-current-version /usr/share/libdvd-pkg/debian
--2022-11-08 12:35:23-- https://download.videolan.org/pub/libdvdcss/1.4.3/libdvdcss-1.4.3.tar.bz2
Risoluzione di download.videolan.org (download.videolan.org)... 213.36.253.2, 2a01:e0d:1:3:58bf:fa02:c0de:5
Connessione a download.videolan.org (download.videolan.org)|213.36.253.2|:443... connesso.
Richiesta HTTP inviata, in attesa di risposta... 200 OK
Lunghezza: 388404 (379K) [application/octet-stream]
Salvataggio in: ‘libdvdcss_1.4.3.orig.tar.bz2’

libdvdcss_1.4.3.orig.tar 100%[==================================>] 379.30K --.-KB/s in 0.1s

2022-11-08 12:35:23 (3.09 MB/s) - ‘libdvdcss_1.4.3.orig.tar.bz2’ salvato [388404/388404]

libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.3.orig.tar.bz2: OK
libdvd-pkg: Unpacking and configuring...
libdvd-pkg: Building the package... (it may take a while)
libdvd-pkg: Build log will be saved to /usr/src/libdvd-pkg/libdvdcss2_1.4.3-1~local_amd64.build
Current: =ep
Bounding set =cap_chown,cap_dac_override,cap_fowner,cap_wake_alarm,cap_block_suspend,cap_audit_read,cap_perfmon,cap_bpf,cap_checkpoint_restore
Ambient set =
Current IAB: !cap_dac_read_search,!cap_fsetid,!cap_kill,!cap_setgid,!cap_setuid,!cap_setpcap,!cap_linux_immutable,!cap_net_bind_service,!cap_net_broadcast,!cap_net_admin,!cap_net_raw,!cap_ipc_lock,!cap_ipc_owner,!cap_sys_module,!cap_sys_rawio,!cap_sys_chroot,!cap_sys_ptrace,!cap_sys_pacct,!cap_sys_admin,!cap_sys_boot,!cap_sys_nice,!cap_sys_resource,!cap_sys_time,!cap_sys_tty_config,!cap_mknod,!cap_lease,!cap_audit_write,!cap_audit_control,!cap_setfcap,!cap_mac_override,!cap_mac_admin,!cap_syslog
Securebits: 024/0x14/5'b10100
*secure-noroot: no (unlocked)
*secure-no-suid-fixup: yes (unlocked)
*secure-keep-caps: yes (unlocked)
*secure-no-ambient-raise: no (unlocked)
uid=0(root) euid=0(root)
gid=0(root)
groups=0(root),107(input),108(kvm),139(libvirt)
Guessed mode: UNCERTAIN (0)
libdvd-pkg: Installing...
Selezionato il pacchetto libdvdcss-dev:amd64 non precedentemente selezionato.
(Lettura del database... 818121 file e directory attualmente installati.)
Preparativi per estrarre .../libdvdcss-dev_1.4.3-1~local_amd64.deb...
Estrazione di libdvdcss-dev:amd64 (1.4.3-1~local)...
Selezionato il pacchetto libdvdcss2:amd64 non precedentemente selezionato.
Preparativi per estrarre .../libdvdcss2_1.4.3-1~local_amd64.deb...
Estrazione di libdvdcss2:amd64 (1.4.3-1~local)...
Configurazione di libdvdcss2:amd64 (1.4.3-1~local)...
Configurazione di libdvdcss-dev:amd64 (1.4.3-1~local)...
Elaborazione dei trigger per libc-bin (2.36-0ubuntu4)...
```

At this point I see a different error : /usr/bin/mpv: error while loading shared libraries. libsixel.so.1 : cannot shared object file : no such file or directory...

I've opened a bug report on the ubuntu bug trackers some time ago,but no one helped :

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-extras/+bug/1996089](https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-extras/+bug/1996089)

at the moment I'm sure that this is not a bug connected only to Firefox,because when I try to open any mp4 file with a different player than VLC,the video stream don't flow at all. I should press stop and play a lot of time to make move the video stream.

UPDATE :

I've fixed the missing library problem and I think that now the real problem comes out :

```
# mplayer video.mp4

MPlayer 1.4 (Debian), built with gcc-12 (C) 2000-2019 MPlayer Team
do_connect: could not connect to socket
connect: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing video.mp4.
libavformat version 59.27.100 (external)
libavformat file format detected.
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x7fa55868ad00]Protocol name not provided, cannot determine if input is local or a network protocol, buffers and access patterns cannot be configured optimally without knowing the protocol
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang und
VIDEO:  [H264]  720x544  24bpp  23.976 fps  1172.0 kbps (143.1 kbyte/s)
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 59.37.100 (external)
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Clip info:
 major_brand: isom
 minor_version: 512
 compatible_brands: isomiso2avc1mp41
 encoder: Lavf59.20.101
Load subtitles in ./
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[aac @ 0x7fa557c0bea0]Multiple frames in a packet.
AUDIO: 48000 Hz, 2 ch, floatle, 129.5 kbit/4.22% (ratio: 16190->384000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
[aac @ 0x7fa557c0bea0]channel element 0.0 duplicate
Movie-Aspect is 1.32:1 - prescaling to correct movie aspect.
VO: [x11] 720x544 => 720x544 Planar YV12 
[swscaler @ 0x7fa5587b5f20]bicubic scaler, from yuv420p to bgra using MMXEXT
[swscaler @ 0x7fa5587b5f20]using unscaled yuv420p -> bgra special converter
A:   0.2 V:   0.3 A-V: -0.105 ct: -0.015   0/  0 ??% ??% ??,?% 1 0 
Capturing not enabled (forgot -capture parameter?)
A:   0.2 V:   0.3 A-V: -0.105 ct: -0.015   0/  0 ??% ??% ??,?% 1 0 


MPlayer interrupted by signal 2 in module: sleep_timer
A:   0.2 V:   0.3 A-V: -0.105 ct: -0.015   0/  0 ??% ??% ??,?% 1 0 

Exiting... (Quit)
```

---

### Post by gab89 on 2022-11-30
[COLOR=#1C1C1C][FONT=&quot]Hello, I am newbie in Linux, have some Ubuntu server with some movies([/FONT][/COLOR][http://criticasdefilmesplus.org](http://criticasdefilmesplus.org)[COLOR=#1C1C1C][FONT=&quot]), it's possible to stream them to Windows machine? Works fine with iPhone and Mac with some ftp player, but with VLC in Windows doesn't work. Get some error message - Could not open file...[/FONT][/COLOR]

---

