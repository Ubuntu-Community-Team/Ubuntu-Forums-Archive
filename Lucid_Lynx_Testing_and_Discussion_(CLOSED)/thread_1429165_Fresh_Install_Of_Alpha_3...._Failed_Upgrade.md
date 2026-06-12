---
title: "Fresh Install Of Alpha 3.... Failed Upgrade"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by suprman2020 on 2010-03-13
I tried to upgrade from Karmic to Lucid, but that failed horribly and I decided I was better off doing a clean install (I was gonna do one anyway when Lucid was released). Lucid was able to install without a hitch and everything except the keyboard brightness keys were not working (this isn't my focus though).

I ran update but it gave me an error and my panel applets stopped working. Unfortunately, I didn't think to write down what the error was. I reboot my computer and I get stuck at the new plymouth.

I rebooted again in recovery mode, but that also got stuck. After some searching, I came upon this post, [http://ubuntuforums.org/showpost.php?p=8628383&postcount=2](http://ubuntuforums.org/showpost.php?p=8628383&postcount=2), and I followed the instructions. It told me that I had to "dpkg --configure -a". This is the output I got. Hopefully, you guys can help me out.

```

Setting up mono-gac (2.4.4~svn151842-1ubuntu2) ...
* Installing 6 assemblies from libart2.0-cil into Mono
E: installing Assembly /usr/lib/cli/art-sharp-2.0/art-sharp.dll failed
E: Installation of libart2.0-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from libflickrnet2.2-cil into Mono
E: installing Assembly /usr/lib/cli/FlickrNet-2.2/FlickrNet.dll failed
E: Installation of libflickrnet2.2-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 6 assemblies from libgconf2.0-cil into Mono
E: installing Assembly /usr/lib/cli/gconf-sharp-2.0/gconf-sharp.dll failed
E: Installation of libgconf2.0-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from libglade2.0-cil into Mono
E: installing Assembly /usr/lib/cli/glade-sharp-2.0/glade-sharp.dll failed
E: Installation of libglade2.0-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from libglib2.0-cil into Mono
E: installing Assembly /usr/lib/cli/glib-sharp-2.0/glib-sharp.dll failed
E: Installation of libglib2.0-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from libgmime2.4-cil into Mono
E: installing Assembly /usr/lib/cli/gmime-sharp-2.4/gmime-sharp.dll failed
E: Installation of libgmime2.4-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 2 assemblies from libgnome2.24-cil into Mono
E: installing Assembly /usr/lib/cli/gnome-sharp-2.24/gnome-sharp.dll failed
E: Installation of libgnome2.24-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from libgnome-keyring1.0-cil into Mono
E: installing Assembly /usr/lib/cli/Gnome.Keyring-1.0/Gnome.Keyring.dll failed
E: Installation of libgnome-keyring1.0-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from libgnomepanel2.24-cil into Mono
E: installing Assembly /usr/lib/cli/gnome-panel-sharp-2.24/gnome-panel-sharp.dll failed
E: Installation of libgnomepanel2.24-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 6 assemblies from libgnome-vfs2.0-cil into Mono
E: installing Assembly /usr/lib/cli/gnome-vfs-sharp-2.0/gnome-vfs-sharp.dll failed
E: Installation of libgnome-vfs2.0-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 5 assemblies from libgtk2.0-cil into Mono
E: installing Assembly /usr/lib/cli/gtk-sharp-2.0/gtk-sharp.dll failed
E: Installation of libgtk2.0-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from liblaunchpad-integration1.0-cil into Mono
E: installing Assembly /usr/lib/cli/launchpad-integration-sharp-1/launchpad-integration-sharp.dll failed
E: Installation of liblaunchpad-integration1.0-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 7 assemblies from libmono-addins0.2-cil into Mono
E: installing Assembly /usr/lib/cli/Mono.Addins-0.2/Mono.Addins.dll failed
E: Installation of libmono-addins0.2-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 3 assemblies from libmono-addins-gui0.2-cil into Mono
E: installing Assembly /usr/lib/cli/Mono.Addins.Gui-0.2/Mono.Addins.Gui.dll failed
E: Installation of libmono-addins-gui0.2-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from libndesk-dbus1.0-cil into Mono
E: installing Assembly /usr/lib/cli/NDesk.DBus-1.0/NDesk.DBus.dll failed
E: Installation of libndesk-dbus1.0-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from libndesk-dbus-glib1.0-cil into Mono
E: installing Assembly /usr/lib/cli/NDesk.DBus.GLib-1.0/NDesk.DBus.GLib.dll failed
E: Installation of libndesk-dbus-glib1.0-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 6 assemblies from libnunit2.4-cil into Mono
E: installing Assembly /usr/lib/cli/nunit.core-2.4/nunit.core.dll failed
E: Installation of libnunit2.4-cil with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.10.atk-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.10.atk-sharp.dll failed
E: Installation of policy.2.10.atk-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.10.gdk-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.10.gdk-sharp.dll failed
E: Installation of policy.2.10.gdk-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.10.glade-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libglade2.0-cil/policy.2.10.glade-sharp.dll failed
E: Installation of policy.2.10.glade-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.10.glib-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libglib2.0-cil/policy.2.10.glib-sharp.dll failed
E: Installation of policy.2.10.glib-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.10.gtk-dotnet into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.10.gtk-dotnet.dll failed
E: Installation of policy.2.10.gtk-dotnet with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.10.gtk-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.10.gtk-sharp.dll failed
E: Installation of policy.2.10.gtk-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.10.pango-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.10.pango-sharp.dll failed
E: Installation of policy.2.10.pango-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.4.atk-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.4.atk-sharp.dll failed
E: Installation of policy.2.4.atk-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.4.gdk-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.4.gdk-sharp.dll failed
E: Installation of policy.2.4.gdk-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.4.glade-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libglade2.0-cil/policy.2.4.glade-sharp.dll failed
E: Installation of policy.2.4.glade-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.4.glib-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libglib2.0-cil/policy.2.4.glib-sharp.dll failed
E: Installation of policy.2.4.glib-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.4.gtk-dotnet into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.4.gtk-dotnet.dll failed
E: Installation of policy.2.4.gtk-dotnet with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.4.gtk-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.4.gtk-sharp.dll failed
E: Installation of policy.2.4.gtk-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.4.pango-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.4.pango-sharp.dll failed
E: Installation of policy.2.4.pango-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.6.atk-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.atk-sharp.dll failed
E: Installation of policy.2.6.atk-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.6.gdk-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.gdk-sharp.dll failed
E: Installation of policy.2.6.gdk-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.6.glade-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libglade2.0-cil/policy.2.6.glade-sharp.dll failed
E: Installation of policy.2.6.glade-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.6.glib-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libglib2.0-cil/policy.2.6.glib-sharp.dll failed
E: Installation of policy.2.6.glib-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.6.gtk-dotnet into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.gtk-dotnet.dll failed
E: Installation of policy.2.6.gtk-dotnet with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.6.gtk-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.gtk-sharp.dll failed
E: Installation of policy.2.6.gtk-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.6.pango-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.pango-sharp.dll failed
E: Installation of policy.2.6.pango-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.8.atk-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.8.atk-sharp.dll failed
E: Installation of policy.2.8.atk-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.8.gdk-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.8.gdk-sharp.dll failed
E: Installation of policy.2.8.gdk-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.8.glade-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libglade2.0-cil/policy.2.8.glade-sharp.dll failed
E: Installation of policy.2.8.glade-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.8.glib-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libglib2.0-cil/policy.2.8.glib-sharp.dll failed
E: Installation of policy.2.8.glib-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.8.gtk-dotnet into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.8.gtk-dotnet.dll failed
E: Installation of policy.2.8.gtk-dotnet with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.8.gtk-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.8.gtk-sharp.dll failed
E: Installation of policy.2.8.gtk-sharp with /usr/share/cli-common/runtimes.d/mono failed
* Installing 1 assembly from policy.2.8.pango-sharp into Mono
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.8.pango-sharp.dll failed
E: Installation of policy.2.8.pango-sharp with /usr/share/cli-common/runtimes.d/mono failed
dpkg: error processing mono-gac (--configure):
 subprocess installed post-installation script returned error exit status 9
Setting up linux-image-2.6.32-16-generic (2.6.32-16.25) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-16-generic
grep: /proc/modules: No such file or directory
grep: /proc/modules: No such file or directory
grep: /proc/modules: No such file or directory
Running postinst hook script /usr/sbin/update-grub.
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.32-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-16-generic; however:
  Package linux-image-2.6.32-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (1.98-1ubuntu1) ...
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.16.17); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up light-themes (0.1.5.8) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing light-themes (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of mono-runtime:
 mono-runtime depends on mono-gac (= 2.4.4~svn151842-1ubuntu2); however:
  Package mono-gac is not configured yet.
dpkg: error processing mono-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono2.0-cil:
 libmono2.0-cil depends on mono-runtime (>= 1.1.8.1); however:
  Package mono-runtime is not configured yet.
dpkg: error processing libmono2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-posix2.0-cil:
 libmono-posix2.0-cil depends on mono-runtime (>= 2.4); however:
  Package mono-runtime is not configured yet.
dpkg: error processing libmono-posix2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gbrainy:
 gbrainy depends on mono-runtime (>= 1.1.8.1); however:
  Package mono-runtime is not configured yet.
 gbrainy depends on libmono-posix2.0-cil (>= 2.4); however:
  Package libmono-posix2.0-cil is not configured yet.
dpkg: error processing gbrainy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tomboy:
 tomboy depends on mono-runtime (>= 1.1.8.1); however:
  Package mono-runtime is not configured yet.
 tomboy depends on libmono-posix2.0-cil (>= 2.4); however:
  Package libmono-posix2.0-cil is not configured yet.
dpkg: error processing tomboy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-system-web2.0-cil:
 libmono-system-web2.0-cil depends on libmono2.0-cil (>= 2.0); however:
  Package libmono2.0-cil is not configured yet.
 libmono-system-web2.0-cil depends on mono-runtime (>= 2.4.4~svn151842); however:
  Package mono-runtime is not configured yet.
 libmono-system-web2.0-cil depends on mono-runtime (<< 2.4.4~svn151843); however:
  Package mono-runtime is not configured yet.
dpkg: error processing libmono-system-web2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of f-spot:
 f-spot depends on mono-runtime (>= 1.1.8.1); however:
  Package mono-runtime is not configured yet.
 f-spot depends on libmono-posix2.0-cil (>= 2.4); however:
  Package libmono-posix2.0-cil is not configured yet.
 f-spot depends on libmono-system-web2.0-cil (>= 1.9.1); however:
  Package libmono-system-web2.0-cil is not configured yet.
dpkg: error processing f-spot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-corlib2.0-cil:
 libmono-corlib2.0-cil depends on mono-runtime (>= 2.4.4~svn151842); however:
  Package mono-runtime is not configured yet.
 libmono-corlib2.0-cil depends on mono-runtime (<< 2.4.4~svn151843); however:
  Package mono-runtime is not configured yet.
dpkg: error processing libmono-corlib2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-sqlite2.0-cil:
 libmono-sqlite2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libmono-sqlite2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-system-data2.0-cil:
 libmono-system-data2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libmono-system-data2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-data-tds2.0-cil:
 libmono-data-tds2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libmono-data-tds2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-system-runtime2.0-cil:
 libmono-system-runtime2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
 libmono-system-runtime2.0-cil depends on libmono-system-web2.0-cil (>= 1.9.1); however:
  Package libmono-system-web2.0-cil is not configured yet.
dpkg: error processing libmono-system-runtime2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnunit2.4-cil:
 libnunit2.4-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
 libnunit2.4-cil depends on libmono-system-runtime2.0-cil (>= 2.4); however:
  Package libmono-system-runtime2.0-cil is not configured yet.
dpkg: error processing libnunit2.4-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-cairo2.0-cil:
 libmono-cairo2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libmono-cairo2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-i18n-west2.0-cil:
 libmono-i18n-west2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libmono-i18n-west2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-sharpzip2.84-cil:
 libmono-sharpzip2.84-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libmono-sharpzip2.84-cil (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mono-gac
 linux-image-2.6.32-16-generic
 linux-image-generic
 grub-pc
 linux-generic
 light-themes
 mono-runtime
 libmono2.0-cil
 libmono-posix2.0-cil
 gbrainy
 tomboy
 libmono-system-web2.0-cil
 f-spot
 libmono-corlib2.0-cil
 libmono-sqlite2.0-cil
 libmono-system-data2.0-cil
 libmono-data-tds2.0-cil
 libmono-system-runtime2.0-cil
 libnunit2.4-cil
 libmono-cairo2.0-cil
 libmono-i18n-west2.0-cil
 libmono-sharpzip2.84-cil

```

---

### Post by kansasnoob on 2010-03-13
What disc did you use? The old Alpha2 or the newest Daily?

It would be really helpful to get somewhat of a preliminary snapshot of your system by seeing the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by suprman2020 on 2010-03-13
> **kansasnoob said:**
> What disc did you use? The old Alpha2 or the newest Daily?

It would be really helpful to get somewhat of a preliminary snapshot of your system by seeing the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Thanks, but I was able to mostly fix it with fsck, then update, then upgrade. My only problem now is the light-themes package.

```
dpkg: error processing light-themes (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 light-themes
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by suprman2020 on 2010-03-13
> **suprman2020 said:**
> Thanks, but I was able to mostly fix it with fsck, then update, then upgrade. My only problem now is the light-themes package.

```
dpkg: error processing light-themes (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 light-themes
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Nevermind, I just got this fixed.

---

