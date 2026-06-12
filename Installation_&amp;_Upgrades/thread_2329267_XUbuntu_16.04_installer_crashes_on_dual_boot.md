---
title: "XUbuntu 16.04 installer crashes on dual boot"
date: 2016-06-29
forum: Installation &amp; Upgrades
---

### Post by jonchin on 2016-06-29
I'm trying to dual boot Windows 10 and Xubuntu 16.04 on my new SSD. I was previously able to do this no problem on an SATA harddrive, using the same install usb keys (one for each).

With my SSD, I installed Windows 10 first, disabled fast startup. When I try to install Xubuntu alongside, it crashes after I select the keyboard layout. I believe it creates the partitions correctly. I tried generating a report but I think it's just a list of hardware components? There's no actual error message?

I've been able to consistently replicate this crash. It crashes right after I select the keyboard layout.

Can anyone help?

---

### Post by oldfred on 2016-06-29
Did you install Windows in UEFI or BIOS boot mode. Or is hardware UEFI capable?
Post this:
sudo parted -l

---

### Post by jonchin on 2016-06-29
Thanks for the quick response. I'm not sure of the answers to either question (pardon my ignorance). Here is the output from parted:

Model: ATA ADATA SP550 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  525MB  524MB   primary   ntfs         boot
 2      525MB   211GB  210GB   primary   ntfs
 3      211GB   240GB  29.4GB  extended


This is the drive:
[https://www.amazon.com/ADATA-Premier-SP550-240GB-ASP550SS3-240GM-C/dp/B013J7Q338](https://www.amazon.com/ADATA-Premier-SP550-240GB-ASP550SS3-240GM-C/dp/B013J7Q338)

---

### Post by yancek on 2016-06-29
You don't seem to have an EFI partition so you probably have windows installed MBR.  You need to create partitions on which to install Ubuntu and create a swap partition.  You can do that with the Extended partition showing if you use the manual (Something Else) option.  The output you posted shows that partitions were not created on which to install Xubuntu.

---

### Post by oldfred on 2016-06-29
I prefer to create / (root), swap and I use /mnt/data partition in advance with gparted and then use Something else to specify which partition is which & format it during install. You can use /home and/or a separate data partition that is NTFS for shared data between Windows & Linux.

       gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions) 
            MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by jonchin on 2016-06-30
Thanks Yancek. But this is a snapshot after several failed attempts and several reinstallations of Windows and Xubuntu.

The automated Xubuntu installer does create the the ext4 partition and a swap partition, but crashes after keyboard layout selection. After a failed attempt, I can see these from both the live usb and from Windows. In fact, if I try to install Xubuntu again, it creates a second set of ext4 and swap partitions.

Once or twice, I even created the partitions manually and it crashed at the same point.

I don't think I have a lousy USB. I've reformatted it and used UNETBOOTIN several times. Plus, the same key installs on my old SATA drive (with Windows already there).

---

### Post by oldfred on 2016-06-30
While a new drive, did you before installing Windows make gpt partitions or RAID partitions.
Those leave hidden data on drive that prevents install, but Windows does not seem to care about.
Parted usually does not show issues with the hidden data. Sometimes fdisk does show issues.
sudo fdisk -ly

But there is a new version of fdisk with 16.04 and I do not know if it still will show any of those issues.

The installer also has a install log file, but you lose it as soon as you shutdown as it really is then only in memory.
Not sure of name, but look in /var/log for install or similar.

---

### Post by jonchin on 2016-06-30
Here are the logs for /var/log/installer/debug

```
[FONT=arial]Ubiquity 2.21.63[/FONT]
[FONT=arial]Gtk-Message: Failed to load module "overlay-scrollbar"[/FONT]
[FONT=arial]Gtk-Message: Failed to load module "overlay-scrollbar"[/FONT]
[FONT=arial]/usr/lib/ubiquity/ubiquity/[/FONT][FONT=arial]frontend/gtk_ui.py:53: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.[/FONT]
[FONT=arial]  from gi.repository import Gtk, Gdk, GObject, GLib, Atk[/FONT]
[FONT=arial]/usr/lib/ubiquity/plugins/ubi-[/FONT][FONT=arial]timezone.py:194: PyGIWarning: TimezoneMap was imported without specifying a version first. Use gi.require_version('[/FONT][FONT=arial]TimezoneMap', '1.0') before import to ensure that the right version gets loaded.[/FONT]
[FONT=arial]  from gi.repository import TimezoneMap[/FONT]
[FONT=arial]No such schema 'org.gnome.nautilus.desktop'[/FONT]
[FONT=arial]/usr/lib/ubiquity/ubiquity/[/FONT][FONT=arial]misc.py:654: PyGIWarning: Xkl was imported without specifying a version first. Use gi.require_version('Xkl', '1.0') before import to ensure that the right version gets loaded.[/FONT]
[FONT=arial]  from gi.repository import Xkl, GdkX11[/FONT]
[FONT=arial]No such schema 'org.gnome.libgnomekbd.[/FONT][FONT=arial]keyboard'[/FONT]
[FONT=arial]update_release_notes_label()[/FONT]
[FONT=arial]update_release_notes_label()[/FONT]
[FONT=arial]Could not translate page (prepare): 'NoneType' object has no attribute 'replace'[/FONT]
[FONT=arial]No such schema 'com.canonical.indicator.[/FONT][FONT=arial]session'[/FONT]
[FONT=arial]No such schema 'com.canonical.indicator.[/FONT][FONT=arial]session'[/FONT]
[FONT=arial]No such schema 'com.canonical.indicator.[/FONT][FONT=arial]session'[/FONT]
[FONT=arial]/usr/lib/ubiquity/plugins/ubi-[/FONT][FONT=arial]timezone.py:98: PyGIWarning: Soup was imported without specifying a version first. Use gi.require_version('Soup', '2.4') before import to ensure that the right version gets loaded.[/FONT]
[FONT=arial]  from gi.repository import Gtk, GObject, GLib, Soup[/FONT]
[FONT=arial]/usr/lib/ubiquity/plugins/ubi-[/FONT][FONT=arial]console-setup.py:72: Warning: Source ID 1023 was not found when attempting to remove it[/FONT]
[FONT=arial]  GLib.source_remove(self.[/FONT][FONT=arial]keyboard_layout_timeout_id)[/FONT]
[FONT=arial]/usr/lib/ubiquity/plugins/ubi-[/FONT][FONT=arial]console-setup.py:74: Warning: Source ID 1026 was not found when attempting to remove it[/FONT]
[FONT=arial]  GLib.source_remove(self.[/FONT][FONT=arial]keyboard_variant_timeout_id)[/FONT]
[FONT=arial]Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.[/FONT]
[FONT=arial]No such schema 'com.canonical.indicator.[/FONT][FONT=arial]session'[/FONT]
[FONT=arial]No such schema 'com.canonical.indicator.[/FONT][FONT=arial]session'[/FONT]
[FONT=arial]No such schema 'com.canonical.indicator.[/FONT][FONT=arial]session'[/FONT]
[FONT=arial]No such schema 'com.canonical.indicator.[/FONT][FONT=arial]session'[/FONT]
[FONT=arial]No such schema 'com.canonical.indicator.[/FONT][FONT=arial]session'[/FONT]
[FONT=arial]No such schema 'com.canonical.indicator.[/FONT][FONT=arial]session'[/FONT]
[FONT=arial]No such schema 'com.canonical.indicator.[/FONT][FONT=arial]session'[/FONT]
[FONT=arial]No such schema 'com.canonical.indicator.[/FONT][FONT=arial]session'[/FONT]
[FONT=arial]No such schema 'org.gnome.settings-daemon.[/FONT][FONT=arial]plugins.media-keys'[/FONT]
[FONT=arial]No such schema 'com.canonical.indicator.[/FONT][FONT=arial]session'[/FONT]
[FONT=arial]No such schema 'org.gnome.settings-daemon.[/FONT][FONT=arial]plugins.media-keys'[/FONT]
[FONT=arial]No such schema 'org.mate.SettingsDaemon.[/FONT][FONT=arial]plugins.media-keys'[/FONT]
[FONT=arial]No such schema 'org.gnome.settings-daemon.[/FONT][FONT=arial]plugins.power'[/FONT]
[FONT=arial]No such schema 'org.gnome.nautilus.desktop'


Here are the logs for /var/log/installer/dm

[/FONT][FONT=arial]ubiquity-dm: starting[/FONT]
[FONT=arial]ubiquity-dm: plymouth[/FONT]
[FONT=arial]ubiquity-dm: start X ['X', '-br', '-ac', '-noreset', '-nolisten', 'tcp', '-background', 'none', 'vt1', ':0'][/FONT]

[FONT=arial]X.Org X Server 1.18.3[/FONT]
[FONT=arial]Release Date: 2016-04-04[/FONT]
[FONT=arial]X Protocol Version 11, Revision 0[/FONT]
[FONT=arial]Build Operating System: Linux 3.13.0-85-generic x86_64 Ubuntu[/FONT]
[FONT=arial]Current Operating System: Linux xubuntu 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64[/FONT]
[FONT=arial]Kernel command line: file=/cdrom/preseed/xubuntu.[/FONT][FONT=arial]seed boot=casper initrd=/casper/initrd.lz quiet splash --- maybe-ubiquity[/FONT]
[FONT=arial]Build Date: 07 April 2016  09:18:50AM[/FONT]
[FONT=arial]xorg-server 2:1.18.3-1ubuntu2 (For technical support please see [/FONT][http://www.ubuntu.com/support](http://www.ubuntu.com/support)[FONT=arial]) [/FONT]
[FONT=arial]Current version of pixman: 0.33.6[/FONT]
[FONT=arial]    Before reporting problems, check [/FONT][http://wiki.x.org]("http://wiki.x.org/")
[FONT=arial]    to make sure that you have the latest version.[/FONT]
[FONT=arial]Markers: (--) probed, (**) from config file, (==) default setting,[/FONT]
[FONT=arial]    (++) from command line, (!!) notice, (II) informational,[/FONT]
[FONT=arial]    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.[/FONT]
[FONT=arial](==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul  1 02:31:47 2016[/FONT]
[FONT=arial](==) Using system config directory "/usr/share/X11/xorg.conf.d"[/FONT]
[FONT=arial](II) [KMS] Kernel modesetting enabled.[/FONT]
[FONT=arial]ubiquity-dm: set vars[/FONT]
[FONT=arial]ubiquity-dm: pam_open_session[/FONT]
[FONT=arial]ubiquity-dm: dm-scripts[/FONT]
[FONT=arial]ubiquity-dm: dbus[/FONT]
[FONT=arial]ubiquity-dm: dconf-service[/FONT]
[FONT=arial]ubiquity-dm: start frontend gtk_ui[/FONT]
[FONT=arial]No such schema 'org.gnome.settings-daemon.[/FONT][FONT=arial]plugins.background'[/FONT]
[FONT=arial]No such schema 'org.gnome.metacity'[/FONT]

[FONT=arial]** (process:1623): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.[/FONT][FONT=arial]DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files[/FONT]
[FONT=arial]ubiquity-dm: start greeter[/FONT]

[FONT=arial](process:1634): indicator-sound-WARNING **: volume-control-pulse.vala:735: unable to get pulse unix socket: GDBus.Error:org.freedesktop.[/FONT][FONT=arial]DBus.Error.ServiceUnknown: The name org.PulseAudio1 was not provided by any .service files[/FONT]
[FONT=arial]Gtk-Message: Failed to load module "overlay-scrollbar"[/FONT]
[FONT=arial]Gtk-Message: Failed to load module "gail"[/FONT]
[FONT=arial]Gtk-Message: Failed to load module "overlay-scrollbar"[/FONT]
[FONT=arial]Gtk-Message: Failed to load module "gail"[/FONT]
[FONT=arial]initctl: UPSTART_SESSION isn't set in the environment. Unable to locate the Upstart instance.[/FONT]
[FONT=arial]Gtk-Message: Failed to load module "overlay-scrollbar"[/FONT]
[FONT=arial]Gtk-Message: Failed to load module "overlay-scrollbar"[/FONT]

[FONT=arial](xfsettingsd:1738): GLib-CRITICAL **: g_str_has_prefix: assertion 'prefix != NULL' failed[/FONT]

[FONT=arial](xfsettingsd:1738): GLib-GObject-CRITICAL **: g_value_get_string: assertion 'G_VALUE_HOLDS_STRING (value)' failed[/FONT]

[FONT=arial](xfsettingsd:1738): GLib-GObject-CRITICAL **: g_value_get_string: assertion 'G_VALUE_HOLDS_STRING (value)' failed[/FONT]
[FONT=arial]Activating service name='org.a11y.atspi.Registry'[/FONT]
[FONT=arial]Successfully activated service 'org.a11y.atspi.Registry'[/FONT]

[FONT=arial](process:1634): indicator-sound-WARNING **: accounts-service-access.vala:[/FONT][FONT=arial]125: unable to find Accounts path for user null: GDBus.Error:org.freedesktop.[/FONT][FONT=arial]DBus.Error.ServiceUnknown: The name com.canonical.UnityGreeter was not provided by any .service files[/FONT]

[FONT=arial](panel:1632): Gdk-CRITICAL **: gdk_window_set_geometry_hints: assertion 'geometry != NULL || geom_mask == 0' failed[/FONT]

[FONT=arial](xfwm4:1624): GLib-CRITICAL **: g_str_has_prefix: assertion 'prefix != NULL' failed[/FONT]
[FONT=arial]ubiquity-dm: greeter exited with code 1[/FONT]
[FONT=arial]ubiquity-dm: Failed with an exception:[/FONT]
[FONT=arial]ubiquity-dm: Traceback (most recent call last):[/FONT]
[FONT=arial]  File "/usr/bin/ubiquity-dm", line 784, in main[/FONT]
[FONT=arial]    ret = run(vt, display, username)[/FONT]
[FONT=arial]  File "/usr/bin/ubiquity-dm", line 759, in run[/FONT]
[FONT=arial]    ret = dm.run(*sys.argv[4:])[/FONT]
[FONT=arial]  File "/usr/bin/ubiquity-dm", line 648, in run[/FONT]
[FONT=arial]    db = DebconfCommunicator('ubiquity'[/FONT][FONT=arial], cloexec=True)[/FONT]
[FONT=arial]  File "/usr/lib/ubiquity/ubiquity/[/FONT][FONT=arial]debconfcommunicator.py", line 37, in __init__[/FONT]
[FONT=arial]    write=self.dccomm.stdin)[/FONT]
[FONT=arial]  File "/usr/lib/python3/dist-[/FONT][FONT=arial]packages/debconf.py", line 50, in __init__[/FONT]
[FONT=arial]    self.setUp(title)[/FONT]
[FONT=arial]  File "/usr/lib/python3/dist-[/FONT][FONT=arial]packages/debconf.py", line 53, in setUp[/FONT]
[FONT=arial]    self.version = self.version(2)[/FONT]
[FONT=arial]  File "/usr/lib/python3/dist-[/FONT][FONT=arial]packages/debconf.py", line 62, in <lambda>[/FONT]
[FONT=arial]    lambda *args, **kw: self.command(command, *args, **kw))[/FONT]
[FONT=arial]  File "/usr/lib/python3/dist-[/FONT][FONT=arial]packages/debconf.py", line 83, in command[/FONT]
[FONT=arial]    status = int(status)[/FONT]
[FONT=arial]ValueError: invalid literal for int() with base 10: ''[/FONT]

[FONT=arial]xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.[/FONT]
[FONT=arial]xfwm4: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.[/FONT]

[FONT=arial](process:1634): indicator-sound-WARNING **: Name lost or unable to acquire bus: com.canonical.indicator.sound[/FONT]

[FONT=arial](nm-applet:1635): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.[/FONT]


[FONT=arial](panel:1632): Gdk-WARNING **: panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.[/FONT]


[FONT=arial](process:1633): indicator-application-service-[/FONT][FONT=arial]WARNING **: Name Lost[/FONT]
[FONT=arial](II) Server terminated successfully (0). Closing log file.

```



Here are the results of parted -l after a failed install:

[/FONT]```
[FONT=arial]Model: ATA ADATA SP550 (scsi)[/FONT]
[FONT=arial]Disk /dev/sda: 240GB[/FONT]
[FONT=arial]Sector size (logical/physical): 512B/4096B[/FONT]
[FONT=arial]Partition Table: msdos[/FONT]
[FONT=arial]Disk Flags: [/FONT]

[FONT=arial]Number  Start   End    Size    Type      File system     Flags[/FONT]
[FONT=arial] 1      1049kB  525MB  524MB   primary   ntfs            boot[/FONT]
[FONT=arial] 2      525MB   211GB  210GB   primary   ntfs[/FONT]
[FONT=arial] 3      211GB   240GB  29.4GB  extended[/FONT]
[FONT=arial] 5      211GB   231GB  20.8GB  logical   ext4[/FONT]
[FONT=arial] 6      231GB   240GB  8586MB  logical   linux-swap(v1)[/FONT]
```

---

### Post by oldfred on 2016-06-30
Added code tags.

Have not installed Xubuntu, so not sure if errors and warnings are critical or not? Sometime errors are posted that do not matter.

---

### Post by jonchin on 2016-07-01
Thanks for the code tags. I assume they are critical because the installer crashes and quits.

---

### Post by oldfred on 2016-07-01
I did a google search on a couple of the critical errors and only real results seemed to be years old and solved but not any fixes and not related to install.

What video card/chip?

---

### Post by jonchin on 2016-07-01
update: I redownloaded Xubuntu and recreated a a boot up usb. This time, I told it to wipe the drive completely (no dual boot).

It still crashed at the same point: after keyboard layout selection. To Google!

---

### Post by jonchin on 2016-07-01
video card: Radeon HD 4870
cpu: AMD Athlon II X3

---

### Post by oldfred on 2016-07-01
I do not know AMD, but we went around & around in this thread. He had dual AMD which was issue.

[http://ubuntuforums.org/showthread.php?t=2329295](http://ubuntuforums.org/showthread.php?t=2329295)

---

