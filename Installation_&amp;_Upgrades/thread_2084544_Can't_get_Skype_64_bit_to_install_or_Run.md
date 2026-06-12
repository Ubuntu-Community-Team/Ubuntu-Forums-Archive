---
title: "Can't get Skype 64 bit to install or Run"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by Hakachukai on 2012-11-15
I downloaded the Dynamic Version of the client here:

```
http://beta.skype.com/en/download-skype/skype-for-linux/downloading/?type=dynamic
```

I uncompressed it and placed it here:

```
hakachukai@Mega-Box:~/Downloads/skype_install$ tar -xvf skype-4.1.0.20.tar.bz2 
skype-4.1.0.20/
skype-4.1.0.20/third-party_attributions.txt
skype-4.1.0.20/LICENSE
skype-4.1.0.20/lang/
skype-4.1.0.20/lang/skype_es.ts
skype-4.1.0.20/lang/skype_es.qm
skype-4.1.0.20/lang/skype_pl.qm
skype-4.1.0.20/lang/skype_it.ts
skype-4.1.0.20/lang/skype_zh_t.qm
skype-4.1.0.20/lang/skype_de.ts
skype-4.1.0.20/lang/skype_ja.ts
skype-4.1.0.20/lang/skype_pt_pt.ts
skype-4.1.0.20/lang/skype_uk.ts
skype-4.1.0.20/lang/skype_th.ts
skype-4.1.0.20/lang/skype_lt.ts
skype-4.1.0.20/lang/skype_ja.qm
skype-4.1.0.20/lang/skype_no.qm
skype-4.1.0.20/lang/skype_pt_br.qm
skype-4.1.0.20/lang/skype_ro.ts
skype-4.1.0.20/lang/skype_ko.ts
skype-4.1.0.20/lang/skype_fr.qm
skype-4.1.0.20/lang/skype_cs.qm
skype-4.1.0.20/lang/skype_ro.qm
skype-4.1.0.20/lang/skype_bg.ts
skype-4.1.0.20/lang/skype_fr.ts
skype-4.1.0.20/lang/skype_lv.qm
skype-4.1.0.20/lang/skype_lv.ts
skype-4.1.0.20/lang/skype_lt.qm
skype-4.1.0.20/lang/skype_zh_t.ts
skype-4.1.0.20/lang/skype_pl.ts
skype-4.1.0.20/lang/skype_pt_pt.qm
skype-4.1.0.20/lang/skype_zh_s.ts
skype-4.1.0.20/lang/skype_pt_br.ts
skype-4.1.0.20/lang/skype_et.qm
skype-4.1.0.20/lang/skype_tr.ts
skype-4.1.0.20/lang/skype_ko.qm
skype-4.1.0.20/lang/skype_bg.qm
skype-4.1.0.20/lang/skype_et.ts
skype-4.1.0.20/lang/skype_uk.qm
skype-4.1.0.20/lang/skype_ru.qm
skype-4.1.0.20/lang/skype_en.qm
skype-4.1.0.20/lang/skype_zh_s.qm
skype-4.1.0.20/lang/skype_cs.ts
skype-4.1.0.20/lang/skype_th.qm
skype-4.1.0.20/lang/skype_de.qm
skype-4.1.0.20/lang/skype_ru.ts
skype-4.1.0.20/lang/skype_it.qm
skype-4.1.0.20/lang/skype_en.ts
skype-4.1.0.20/lang/skype_no.ts
skype-4.1.0.20/lang/skype_tr.qm
skype-4.1.0.20/skype.conf
skype-4.1.0.20/skype
skype-4.1.0.20/avatars/
skype-4.1.0.20/avatars/Beach Skype.png
skype-4.1.0.20/avatars/Skype Smiley.png
skype-4.1.0.20/avatars/Hula Skype.png
skype-4.1.0.20/avatars/Architect Skype.png
skype-4.1.0.20/avatars/Christmas Skype.png
skype-4.1.0.20/avatars/Skypers of the Caribbean.png
skype-4.1.0.20/avatars/Skype-in-one.png
skype-4.1.0.20/avatars/Party Skype.png
skype-4.1.0.20/avatars/Skype Beauty.png
skype-4.1.0.20/avatars/DJ Skype.png
skype-4.1.0.20/avatars/Star Skype.png
skype-4.1.0.20/avatars/Rice Skype.png
skype-4.1.0.20/avatars/Yin Yang Skype.png
skype-4.1.0.20/avatars/The Skypeness.png
skype-4.1.0.20/avatars/Wetsuit Skype.png
skype-4.1.0.20/avatars/DIY Skype.png
skype-4.1.0.20/avatars/Angel Skype.png
skype-4.1.0.20/avatars/Skype Shorty.png
skype-4.1.0.20/avatars/Metal Skype.png
skype-4.1.0.20/avatars/Skype Safety.png
skype-4.1.0.20/avatars/Skype Artiste.png
skype-4.1.0.20/avatars/Carnaval Skype.png
skype-4.1.0.20/avatars/Skype Aid.png
skype-4.1.0.20/avatars/Skype in a Bag.png
skype-4.1.0.20/avatars/Skype Brrr... .png
skype-4.1.0.20/avatars/Sushi Skype.png
skype-4.1.0.20/avatars/Skype Headset.png
skype-4.1.0.20/avatars/Desert Skype.png
skype-4.1.0.20/avatars/Call Me.png
skype-4.1.0.20/avatars/Skypahontas.png
skype-4.1.0.20/avatars/Skype Goaaaaal.png
skype-4.1.0.20/avatars/Skype San.png
skype-4.1.0.20/avatars/Pop Skype.png
skype-4.1.0.20/avatars/Designer Skype.png
skype-4.1.0.20/avatars/Skype-ahoy.png
skype-4.1.0.20/avatars/Skype Candy.png
skype-4.1.0.20/avatars/Skype Jah.png
skype-4.1.0.20/avatars/Business Skype.png
skype-4.1.0.20/avatars/College Skype.png
skype-4.1.0.20/avatars/Fax Skype.png
skype-4.1.0.20/avatars/Call Me Sweetheart.png
skype-4.1.0.20/avatars/Skype Boarder.png
skype-4.1.0.20/avatars/Empire Skype.png
skype-4.1.0.20/avatars/Make Skype Not War.png
skype-4.1.0.20/avatars/Skype Extreme.png
skype-4.1.0.20/avatars/Skype Bling.png
skype-4.1.0.20/avatars/Behind Skype.png
skype-4.1.0.20/avatars/Devil Skype.png
skype-4.1.0.20/avatars/Skype Cool Shades.png
skype-4.1.0.20/avatars/Skype Cola.png
skype-4.1.0.20/avatars/Geisha Skype.png
skype-4.1.0.20/avatars/Skype Time.png
skype-4.1.0.20/avatars/Chic Skype.png
skype-4.1.0.20/avatars/Ninja Skype.png
skype-4.1.0.20/avatars/Skype.png
skype-4.1.0.20/avatars/Skype-a-Manger.png
skype-4.1.0.20/avatars/Skype Jyve.png
skype-4.1.0.20/avatars/Earbud Skype.png
skype-4.1.0.20/avatars/Skype 502.png
skype-4.1.0.20/avatars/Travel Skype.png
skype-4.1.0.20/skype.desktop
skype-4.1.0.20/icons/
skype-4.1.0.20/icons/SkypeBlue_48x48.png
skype-4.1.0.20/icons/SkypeBlue_16x16.png
skype-4.1.0.20/icons/SkypeBlue_32x32.png
skype-4.1.0.20/README
skype-4.1.0.20/sounds/
skype-4.1.0.20/sounds/SkypeLogout.wav
skype-4.1.0.20/sounds/ContactOnline.wav
skype-4.1.0.20/sounds/TransferRequest.wav
skype-4.1.0.20/sounds/CallHangup.wav
skype-4.1.0.20/sounds/CallBusy.wav
skype-4.1.0.20/sounds/ChatIncoming.wav
skype-4.1.0.20/sounds/SkypeLogin.wav
skype-4.1.0.20/sounds/TransferFailed.wav
skype-4.1.0.20/sounds/CallHold.wav
skype-4.1.0.20/sounds/ContactAuthRequest.wav
skype-4.1.0.20/sounds/TransferComplete.wav
skype-4.1.0.20/sounds/ChatOutgoing.wav
skype-4.1.0.20/sounds/ContactOffline.wav
skype-4.1.0.20/sounds/CallRingingOut.wav
skype-4.1.0.20/sounds/CallResume.wav
skype-4.1.0.20/sounds/ContactAdded.wav
skype-4.1.0.20/sounds/ChatIncomingInitial.wav
skype-4.1.0.20/sounds/CallFailed.wav
skype-4.1.0.20/sounds/VoicemailReceived.wav
skype-4.1.0.20/sounds/CallConnecting.wav
skype-4.1.0.20/sounds/CallRemoteHangup.wav
skype-4.1.0.20/sounds/CallRingingIn.wav
hakachukai@Mega-Box:~/Downloads/skype_install$
```


This is my system info:
```
hakachukai@Mega-Box:~/Downloads/skype_install/skype-4.1.0.20$ uname -a
Linux Mega-Box 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
```


It complains that it can't find Certain libs, so I used ldd to check it out:

```
hakachukai@Mega-Box:~/Downloads/skype_install/skype-4.1.0.20$ ldd skype
	linux-gate.so.1 =>  (0xf7717000)
	libasound.so.2 => not found
	libXv.so.1 => not found
	libXss.so.1 => not found
	librt.so.1 => /lib32/librt.so.1 (0xf76f5000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf76f1000)
	libX11.so.6 => not found
	libXext.so.6 => not found
	libQtDBus.so.4 => not found
	libQtWebKit.so.4 => not found
	libQtXml.so.4 => not found
	libQtGui.so.4 => not found
	libQtNetwork.so.4 => not found
	libQtCore.so.4 => not found
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf76d6000)
	libstdc++.so.6 => not found
	libm.so.6 => /lib32/libm.so.6 (0xf76b0000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7694000)
	libc.so.6 => /lib32/libc.so.6 (0xf7538000)
	/lib/ld-linux.so.2 (0xf7718000)
```

I decided to see if those libs were really missing. Apparently they are not Missing:

```
hakachukai@Mega-Box:~/Downloads/skype_install/skype-4.1.0.20$ for x in $(ldd skype | grep -i "not found" | awk '{print $1}'); do locate "$x"; if [ "$?" -gt 0 ]; then echo "$x is Missing"; fi;  done
/usr/lib/libasound.so.2
/usr/lib/libasound.so.2.0.0
/usr/lib/libXv.so.1
/usr/lib/libXv.so.1.0.0
/usr/lib/libXss.so.1
/usr/lib/libXss.so.1.0.0
/usr/lib/libX11.so.6
/usr/lib/libX11.so.6.3.0
/usr/lib/libXext.so.6
/usr/lib/libXext.so.6.4.0
/usr/lib/libQtDBus.so.4
/usr/lib/libQtDBus.so.4.7
/usr/lib/libQtDBus.so.4.7.0
/usr/lib/libQtWebKit.so.4
/usr/lib/libQtWebKit.so.4.7
/usr/lib/libQtWebKit.so.4.7.0
/usr/lib/libQtXml.so.4
/usr/lib/libQtXml.so.4.7
/usr/lib/libQtXml.so.4.7.0
/usr/lib/libQtGui.so.4
/usr/lib/libQtGui.so.4.7
/usr/lib/libQtGui.so.4.7.0
/usr/lib/libQtNetwork.so.4
/usr/lib/libQtNetwork.so.4.7
/usr/lib/libQtNetwork.so.4.7.0
/usr/lib/libQtCore.so.4
/usr/lib/libQtCore.so.4.7
/usr/lib/libQtCore.so.4.7.0
/usr/lib/libstdc++.so.6
/usr/lib/libstdc++.so.6.0.14
```


So I used strace to figure out where it was looking and found it looking in the wrong place: 


```
hakachukai@Mega-Box:~/Downloads/skype_install/skype-4.1.0.20$ strace ./skype 
execve("./skype", ["./skype"], [/* 39 vars */]) = 0
[ Process PID=5880 runs in 32 bit mode. ]
brk(0)                                  = 0xa2f6000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff7724000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=87795, ...}) = 0
mmap2(NULL, 87795, PROT_READ, MAP_PRIVATE, 3, 0) = 0xfffffffff770e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib32/tls/i686/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32/tls/i686/sse2/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib32/tls/i686/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32/tls/i686/sse2", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib32/tls/i686/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32/tls/i686/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib32/tls/i686/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32/tls/i686", 0xffbf31b8)   = -1 ENOENT (No such file or directory)
open("/lib32/tls/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32/tls/sse2/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib32/tls/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32/tls/sse2", 0xffbf31b8)   = -1 ENOENT (No such file or directory)
open("/lib32/tls/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32/tls/cmov", 0xffbf31b8)   = -1 ENOENT (No such file or directory)
open("/lib32/tls/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32/tls", 0xffbf31b8)        = -1 ENOENT (No such file or directory)
open("/lib32/i686/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32/i686/sse2/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib32/i686/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32/i686/sse2", 0xffbf31b8)  = -1 ENOENT (No such file or directory)
open("/lib32/i686/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32/i686/cmov", 0xffbf31b8)  = -1 ENOENT (No such file or directory)
open("/lib32/i686/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32/i686", 0xffbf31b8)       = -1 ENOENT (No such file or directory)
open("/lib32/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32/sse2/cmov", 0xffbf31b8)  = -1 ENOENT (No such file or directory)
open("/lib32/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32/sse2", 0xffbf31b8)       = -1 ENOENT (No such file or directory)
open("/lib32/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32/cmov", 0xffbf31b8)       = -1 ENOENT (No such file or directory)
open("/lib32/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib32", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib32/tls/i686/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32/tls/i686/sse2/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/i686/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32/tls/i686/sse2", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/i686/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32/tls/i686/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/i686/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32/tls/i686", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32/tls/sse2/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32/tls/sse2", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32/tls/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib32/tls/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32/tls", 0xffbf31b8)    = -1 ENOENT (No such file or directory)
open("/usr/lib32/i686/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32/i686/sse2/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib32/i686/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32/i686/sse2", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib32/i686/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32/i686/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib32/i686/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32/i686", 0xffbf31b8)   = -1 ENOENT (No such file or directory)
open("/usr/lib32/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32/sse2/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib32/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32/sse2", 0xffbf31b8)   = -1 ENOENT (No such file or directory)
open("/usr/lib32/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32/cmov", 0xffbf31b8)   = -1 ENOENT (No such file or directory)
open("/usr/lib32/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib32", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/lib/i486-linux-gnu/tls/i686/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/i686/sse2/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/i686/sse2", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/i686/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/i686", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/sse2/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/sse2", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/i686/sse2/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/i686/sse2", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/i686/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/i686", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/sse2/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/sse2", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686/sse2/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686/sse2", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/sse2/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/sse2", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/i686/sse2/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/i686/sse2", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/i686/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/i686", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/sse2/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/sse2/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/sse2/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/sse2", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/cmov/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/cmov", 0xffbf31b8) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/libasound.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu", 0xffbf31b8) = -1 ENOENT (No such file or directory)
writev(2, [{"./skype", 7}, {": ", 2}, {"error while loading shared libra"..., 36}, {": ", 2}, {"libasound.so.2", 14}, {": ", 2}, {"cannot open shared object file", 30}, {": ", 2}, {"No such file or directory", 25}, {"\n", 1}], 10./skype: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory
) = 121
exit_group(127)                         = ?
hakachukai@Mega-Box:~/Downloads/skype_install/skype-4.1.0.20$
```


How do I fix this? Why is it happening?
I'm tempted to just set up symbolic links, but I don't know if the libs are the right Arch / Version.

---

### Post by BertN45 on 2012-11-15
Why are you using the Beta and not the official release 4.1, see next review: [http://www.omgubuntu.co.uk/2012/11/skype-for-linux-adds-windows-live-login-fresh-login-screen](http://www.omgubuntu.co.uk/2012/11/skype-for-linux-adds-windows-live-login-fresh-login-screen)

---

### Post by quentinl on 2012-11-15
have you tried 32-bit?

---

### Post by ogdhekne on 2013-03-25
Bellow cmd in Terminal  for (OS : Kubuntu 12.10 amd64) :

sudo apt-get install libqtcore4 libqtgui4 libqt4-network libqt4-webkit

---

### Post by cforput on 2013-03-31
I'm using 12.04 and just downloaded the 64-bit link from here: [http://www.tucows.com/preview/853867/Skype-For-Ubuntu-64-Bit](http://www.tucows.com/preview/853867/Skype-For-Ubuntu-64-Bit)

It installed and is running OK except I can't get Screen Shareing Mode to work right.

---

