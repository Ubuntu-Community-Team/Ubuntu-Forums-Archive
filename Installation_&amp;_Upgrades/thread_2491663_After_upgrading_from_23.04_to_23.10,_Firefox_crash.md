---
title: "After upgrading from 23.04 to 23.10, Firefox crashing daily"
date: 2023-10-16
forum: Installation &amp; Upgrades
---

### Post by bswilson on 2023-10-16
After upgrading my desktop to 23.10, I've been pleased with it, other than with Firefox. On a daily basis, Firefox crashes or I have to kill it to move on. Sometimes (not always), other system resources are impacted and other desktop applications are interrupted. I can't recreate the problem on demand, but it's frequent.

I finally launched Firefox (/usr/bin/firefox, which is a script to ultimately start the snap package) from a Terminal window, and captured this: 

```
bswilson@doctordre:~$ firefox
Gtk-Message: 15:35:51.908: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.

(firefox:258636): Gtk-WARNING **: 15:35:52.065: GTK+ module /snap/firefox/3252/gnome-platform/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so cannot be loaded.
GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported.
Gtk-Message: 15:35:52.065: Failed to load module "canberra-gtk-module"

(firefox:258636): Gtk-WARNING **: 15:35:52.068: GTK+ module /snap/firefox/3252/gnome-platform/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so cannot be loaded.
GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported.
Gtk-Message: 15:35:52.068: Failed to load module "canberra-gtk-module"
[Parent 258636, Main Thread] WARNING: OnCloseSessionDone error: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/freedesktop/portal/desktop/session/1_632/firefox_com_1password_1password_132991645”: 'glib warning', file /build/firefox/parts/firefox/build/toolkit/xre/nsSigHandlers.cpp:167

** (firefox:258636): WARNING **: 15:43:26.919: OnCloseSessionDone error: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/freedesktop/portal/desktop/session/1_632/firefox_com_1password_1password_132991645”
[Parent 258636, Main Thread] WARNING: OnCloseSessionDone error: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/freedesktop/portal/desktop/session/1_632/firefox_com_1password_1password_1284719153”: 'glib warning', file /build/firefox/parts/firefox/build/toolkit/xre/nsSigHandlers.cpp:167

** (firefox:258636): WARNING **: 15:50:38.459: OnCloseSessionDone error: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/freedesktop/portal/desktop/session/1_632/firefox_com_1password_1password_1284719153”
bswilson@doctordre:~$ 
```


Has anyone else been seeing any such problems? I have been using the same Firefox configuration and 3 extensions for years. No problems on 23.04.

Thanks.

---

### Post by broti on 2023-10-19
Hi @bswilson,

i've found this post after searching for the same issue: Since upgrading to 23.10 my Firefox is suddenly freezing all the time.
I didn't have any issues before on the previous two Ubuntu versions.

I ran`firefox` in the terminal and my output looks the same as yours:

```
broti@stulle:~$ firefox
Gtk-Message: 13:57:44.484: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.

(firefox:37482): Gtk-WARNING **: 13:57:44.698: GTK+ module /snap/firefox/3252/gnome-platform/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so cannot be loaded.
GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported.
Gtk-Message: 13:57:44.698: Failed to load module "canberra-gtk-module"

(firefox:37482): Gtk-WARNING **: 13:57:44.703: GTK+ module /snap/firefox/3252/gnome-platform/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so cannot be loaded.
GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported.
Gtk-Message: 13:57:44.703: Failed to load module "canberra-gtk-module"
ATTENTION: default value of option mesa_glthread overridden by environment.
ATTENTION: default value of option mesa_glthread overridden by environment.
Missing chrome or resource URL: chrome://browser/skin/aboutNetError.css
```

So it seems I get the same issue when it comes to `libcanberra-gtk-module.so`. Nothing about 1password on my end though, as I am not using that extension. But I get some warning about environment overwrites.
Unfortunately I cannot solve either issue myself yet.

Update:
While surfing I noticed some more messages in the shell. Within the last two hours (no crashes or "do you want to wait or forcibly shut down firefox?" warnings in that time, though) the following messages appeared:
```
ATTENTION: default value of option mesa_glthread overridden by environment.
[Child 37713, MediaDecoderStateMachine #6] WARNING: 7fa1c7bb7a60 OpenCubeb() failed to init cubeb: file /build/firefox/parts/firefox/build/dom/media/AudioStream.cpp:281
[Child 37713, MediaDecoderStateMachine #6] WARNING: Decoder=7fa1d0273e00 [OnMediaSinkAudioError]: file /build/firefox/parts/firefox/build/dom/media/MediaDecoderStateMachine.cpp:4649
[Child 37713, MediaDecoderStateMachine #6] WARNING: Decoder=7fa1d0273e00 Decode error: NS_ERROR_DOM_MEDIA_MEDIASINK_ERR (0x806e000b) - OnMediaSinkAudioError: file /build/firefox/parts/firefox/build/dom/media/MediaDecoderStateMachineBase.cpp:166
[Child 37713, MediaDecoderStateMachine #1] WARNING: 7fa1d020cee0 OpenCubeb() failed to init cubeb: file /build/firefox/parts/firefox/build/dom/media/AudioStream.cpp:281
[Child 37713, MediaDecoderStateMachine #1] WARNING: Decoder=7fa1d0274100 [OnMediaSinkAudioError]: file /build/firefox/parts/firefox/build/dom/media/MediaDecoderStateMachine.cpp:4649
[Child 37713, MediaDecoderStateMachine #1] WARNING: Decoder=7fa1d0274100 Decode error: NS_ERROR_DOM_MEDIA_MEDIASINK_ERR (0x806e000b) - OnMediaSinkAudioError: file /build/firefox/parts/firefox/build/dom/media/MediaDecoderStateMachineBase.cpp:166
Missing chrome or resource URL: chrome://browser/skin/aboutNetError.css

```

---

### Post by bswilson on 2023-10-26
Thank you, @broti! I'll keep messing around with this... It's still happening for me every day.

---

### Post by gxdineruiz on 2023-10-31
What I did was similar to this, and the error disappeared.

sudo apt install libcanberra-gtk-module libcanberra-gtk3-module -y 
sudo apt install libcanberra-gtk-module:i386 -y
sudo apt remove --purge libcanberra-gtk-module libcanberra-gtk3-module -y 
sudo apt remove --purge libcanberra-gtk-module:i386 -y
sudo apt update -y && sudo apt upgrade -y && sudo apt autoremove -y

---

