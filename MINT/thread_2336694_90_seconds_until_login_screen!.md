---
title: "90 seconds until login screen!"
date: 2016-09-10
forum: MINT
---

### Post by stealthbyroot on 2016-09-10
I need help. From GRUB to the login screen I have 90 seconds waiting period.
Please find attached logs and let me know if you need more info.

Sorry to the community, I am using Linux Mint which one is based on Ubuntu.
I don't have any other place to ask so I am trying here.
Thx.

---

### Post by oldos2er on 2016-09-10
Moved to MINT.

There is another better place you could ask, [https://forums.linuxmint.com/](https://forums.linuxmint.com/)

---

### Post by Dennis N on 2016-09-10
Press ESC during that 90 second wait. This may show some boot messages.  One you may see begins "A start job is running ...". These messages often time out in 90 seconds.

---

### Post by stealthbyroot on 2016-09-10
I already try on Linux Mint but support is almost equal to zero.

---

### Post by stealthbyroot on 2016-09-10
> **Dennis N said:**
> Press ESC during that 90 second wait. This may show some boot messages.  One you may see begins "A start job is running ...". These messages often time out in 90 seconds.


I try to press ESC but nothing is happening.

---

### Post by Dennis N on 2016-09-10
You can try systemd-analyze blame to see how much time things took to initialize. It may reveal something taking up that 90 seconds. 

Here's what I get on this computer (which does not have any startup problems).

```
dmn@Sydney:~$ systemd-analyze blame
         10.123s systemd-fsck-root.service
          7.316s systemd-udev-settle.service
          5.689s NetworkManager-wait-online.service
          4.692s dev-disk-by\x2duuid-a9f12cc3\x2dd420\x2d488e\x2d9b31\x2d319689f
          1.168s systemd-udevd.service
          1.109s systemd-fsck@dev-disk-by\x2duuid-d97e2feb\x2d1bf6\x2d429b\x2dbb
          1.021s systemd-fsck@dev-disk-by\x2duuid-1291\x2dACCB.service
           921ms NetworkManager.service
           908ms systemd-tmpfiles-setup-dev.service
           721ms ModemManager.service
           704ms plymouth-start.service
           681ms thermald.service
           607ms systemd-modules-load.service
           579ms accounts-daemon.service
           471ms systemd-journald.service
           374ms plymouth-quit-wait.service
           357ms colord.service
           353ms resolvconf.service
           324ms irqbalance.service
           263ms upower.service
           197ms ufw.service
           194ms systemd-setup-dgram-qlen.service
           191ms dev-mqueue.mount
           188ms systemd-udev-trigger.service
           187ms systemd-sysctl.service
           185ms lightdm.service
           171ms systemd-vconsole-setup.service
           159ms sys-kernel-debug.mount
           158ms dev-hugepages.mount
           152ms dev-disk-by\x2duuid-391dcd7b\x2dca92\x2d4cfb\x2d98e4\x2d4619ea2
           148ms avahi-daemon.service
           135ms grub-common.service
           128ms systemd-logind.service
           123ms binfmt-support.service
           117ms lm-sensors.service
           113ms rsyslog.service
           103ms ondemand.service
           103ms gpu-manager.service
            87ms polkitd.service
            86ms kmod-static-nodes.service
            72ms networking.service
            67ms rtkit-daemon.service
            63ms systemd-update-utmp.service
            60ms dev-sdb3.swap
            48ms apparmor.service
            29ms udisks2.service
            27ms console-setup.service
            23ms udev-finish.service
            21ms alsa-restore.service
            17ms apport.service
            15ms kerneloops.service
            14ms systemd-user-sessions.service
            14ms dbus.service
            13ms pppd-dns.service
            13ms systemd-timesyncd.service
            11ms speech-dispatcher.service
            11ms wpa_supplicant.service
            11ms plymouth-read-write.service
            11ms user@1000.service
             9ms mnt-Common\x2dFiles.mount
             7ms systemd-journal-flush.service
             5ms dns-clean.service
             4ms proc-sys-fs-binfmt_misc.mount
             4ms systemd-remount-fs.service
             3ms ifup-wait-all-auto.service
             3ms boot-efi.mount
             3ms systemd-rfkill@rfkill0.service
             2ms systemd-tmpfiles-setup.service
             2ms hddtemp.service
             2ms ureadahead-stop.service
             2ms systemd-update-utmp-runlevel.service
             1ms systemd-random-seed.service
             1ms sys-fs-fuse-connections.mount
           881us rc-local.service

```

Note: These things don't all start up in sequence (one at a time). A can start while B has not completed it's startup.

---

### Post by stealthbyroot on 2016-09-10
> **Dennis N said:**
> You can try systemd-analyze blame to see how much time things took to initialize. It may reveal something taking up that 90 seconds. 

Here's what I get on this computer (which does not have any startup problems).

```
dmn@Sydney:~$ systemd-analyze blame
         10.123s systemd-fsck-root.service
          7.316s systemd-udev-settle.service
          5.689s NetworkManager-wait-online.service
          4.692s dev-disk-by\x2duuid-a9f12cc3\x2dd420\x2d488e\x2d9b31\x2d319689f
          1.168s systemd-udevd.service
          1.109s systemd-fsck@dev-disk-by\x2duuid-d97e2feb\x2d1bf6\x2d429b\x2dbb
          1.021s systemd-fsck@dev-disk-by\x2duuid-1291\x2dACCB.service
           921ms NetworkManager.service
           908ms systemd-tmpfiles-setup-dev.service
           721ms ModemManager.service
           704ms plymouth-start.service
           681ms thermald.service
           607ms systemd-modules-load.service
           579ms accounts-daemon.service
           471ms systemd-journald.service
           374ms plymouth-quit-wait.service
           357ms colord.service
           353ms resolvconf.service
           324ms irqbalance.service
           263ms upower.service
           197ms ufw.service
           194ms systemd-setup-dgram-qlen.service
           191ms dev-mqueue.mount

```

Note: These things don't all start up in sequence (one at a time). A can start while B has not completed it's startup.

Here is my log below:

```
stealthbyroot@Stealthbyroot-Power ~ $ systemd-analyze blame
          8.177s NetworkManager-wait-online.service
          1.335s upower.service
          1.145s lvm2-monitor.service
           546ms dev-sdc3.device
           430ms mnt-92D093A7D0939059.mount
           410ms gpu-manager.service
           357ms [email]systemd-cryptsetup@cryptswap1.servic[/email]e
           331ms systemd-rfkill.service
           240ms mnt-C6140EAD140EA093.mount
           129ms systemd-hwdb-update.service
           112ms ufw.service
           110ms ModemManager.service
           104ms accounts-daemon.service
            94ms systemd-logind.service
            75ms loadcpufreq.service
            73ms NetworkManager.service
            58ms systemd-udevd.service
            57ms console-setup.service
            56ms grub-common.service
            56ms thermald.service
            51ms speech-dispatcher.service
            50ms teamviewerd.service
            48ms irqbalance.service
            47ms virtualbox-guest-utils.service
            43ms ondemand.service
            39ms console-kit-log-system-start.service
            38ms networking.service
            37ms udisks2.service
            36ms keyboard-setup.service
            35ms mnt-102CFA392CFA1984.mount
            34ms systemd-journald.service
            33ms systemd-udev-trigger.service
            27ms rsyslog.service
            24ms bluetooth.service
            22ms plymouth-quit.service
            21ms plymouth-quit-wait.service
            21ms systemd-tmpfiles-setup-dev.service
            21ms systemd-tmpfiles-setup.service
            20ms systemd-modules-load.service
            20ms [email]user@1000.servic[/email]e
            19ms polkitd.service
            19ms cpufrequtils.service
            19ms ntp.service
            17ms systemd-hostnamed.service
            17ms colord.service
            16ms wpa_supplicant.service
            14ms lm-sensors.service
            14ms systemd-sysctl.service
            12ms plymouth-start.service
            12ms pppd-dns.service
            12ms binfmt-support.service
            11ms plymouth-read-write.service
            11ms alsa-restore.service
            10ms dev-mqueue.mount
             8ms media-System_Reserved.mount
             8ms sys-kernel-debug.mount
             7ms hddtemp.service
             6ms console-kit-daemon.service
             6ms dev-hugepages.mount
             5ms dns-clean.service
             4ms systemd-user-sessions.service
             4ms kmod-static-nodes.service
             4ms systemd-journal-flush.service
             4ms proc-sys-fs-binfmt_misc.mount
             3ms resolvconf.service
             2ms systemd-update-utmp.service
             2ms ureadahead-stop.service
             2ms rtkit-daemon.service
             2ms openvpn.service
             2ms avahi-daemon.service
             2ms systemd-remount-fs.service
             2ms systemd-update-utmp-runlevel.service
             2ms rc-local.service
             1ms sys-fs-fuse-connections.mount
             1ms [email]systemd-backlight@backlight:acpi_video0.servic[/email]e
             1ms setvtrgb.service
           925us systemd-random-seed.service
lines 55-77/77 (END)
             8ms media-System_Reserved.mount
             8ms sys-kernel-debug.mount
             7ms hddtemp.service
             6ms console-kit-daemon.service
             6ms dev-hugepages.mount
             5ms dns-clean.service
             4ms systemd-user-sessions.service
             4ms kmod-static-nodes.service
             4ms systemd-journal-flush.service
             4ms proc-sys-fs-binfmt_misc.mount
             3ms resolvconf.service
             2ms systemd-update-utmp.service
             2ms ureadahead-stop.service
             2ms rtkit-daemon.service
             2ms openvpn.service
             2ms avahi-daemon.service
             2ms systemd-remount-fs.service
             2ms systemd-update-utmp-runlevel.service
             2ms rc-local.service
             1ms sys-fs-fuse-connections.mount
             1ms [email]systemd-backlight@backlight:acpi_video0.servic[/email]e
             1ms setvtrgb.service
           925us systemd-random-seed.service
```

---

### Post by Dennis N on 2016-09-10
Well, don't see anything there - the times are very small: ms = millisecond or 1/1000th sec.

There is at least one time out in the sys.log:

```
Sep  9 16:23:10 Stealthbyroot-Power systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-be8af360\x2db1f7\x2d48de\x2da1be\x2db35965283ac6.device.
```

I can read the uuid, which should identify the device: I read the uuid as be8af360*. Don't know how to interpret the rest of the line. 

running ```
ls -l /dev/disk/by-uuid
``` should identify the partition it is trying to mount from the uuid (if it exists). If the uuid is not found in the output, check /etc/fstab to see if it's there. If so, then the uuid in fstab is incorrect for that partition. Also check all the uuids in /etc/fstab to be sure they match devices in the listing.

That is about all I can think of about this.

* see correction to this - post #9

---

### Post by Dennis N on 2016-09-10
_Correction_: My interpretation of the uuid is wrong. be8af360 is just the start of the uuid.

For example, in my display in post #6 is:

```
1.109s systemd-fsck@dev-disk-by\x2duuid-d97e2feb\x2d1bf6\x2d429b\x2dbb

```
but checking, the real uuid is **d97e2feb-1bf6-429b-bb**a5-943264ec1474 and the systemd message only displays the first part (bold) in segments - apparently truncating as well. 

1.109s systemd-fsck@dev-disk-by\x2duuid-**d97e2feb**\x2d**1bf6**\x2d**429b**\x2d**bb**

So you may need to check again.

---

### Post by stealthbyroot on 2016-09-11
Running dmesg I get one really big gap.

```
[   10.098860] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input23
[   99.141162] cgroup: new mount options do not match the existing superblock, will be ignored
```

Full log attached.

Looks like something is going on with disks.[ATTACH]271083[/ATTACH]

---

### Post by stealthbyroot on 2016-09-11
Looks like swap partition is the problem.

```
/dev/sda1: LABEL="New Volume" UUID="C6140EAD140EA093" TYPE="ntfs" PARTUUID="c63193df-01"
/dev/sdb1: UUID="92D093A7D0939059" TYPE="ntfs" PARTUUID="6e607f74-01"
/dev/sdc1: LABEL="System Reserved" UUID="40C2E262C2E25BA2" TYPE="ntfs" PARTUUID="e335bf67-01"
/dev/sdc2: UUID="102CFA392CFA1984" TYPE="ntfs" PARTUUID="e335bf67-02"
/dev/sdc3: UUID="4d354750-7ff0-46e9-bb35-1859f95f09e0" TYPE="ext4" PARTUUID="e335bf67-03"
/dev/sdc4: UUID="93e8f22b-7580-43e1-8e83-e32016c8ec6b" TYPE="swap" PARTUUID="e335bf67-04"
/dev/mapper/cryptswap1: UUID="536c26fe-c531-41ce-9388-aee81501f389" TYPE="swap"
```

---

### Post by DuckHook on 2016-09-11
@OP - please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

I've edited your posts to add such tags, but please do this yourself in future.

In my experience, long boots are often due to unavailable partitions or broken network shares. You've chased the problem down to your swap partition. It looks to me like you've activated swap encryption. This is a good idea for security purposes, but it tends to render the filesystem brittle. In your case, something has likely broken the crypt-linkage and what you are seeing is the system trying to mount swap, choking, and finally timing out to proceed without swap. You can easily tell if swap is active with:```
free -h
```…which should look something like:```
             total       used       free     shared    buffers     cached
Mem:          2.0G       612M       1.4G       1.1M       176M       305M
-/+ buffers/cache:       130M       1.8G
Swap:         998M         0B       998M
```…if the last line beginning with "Swap" is missing, then you don't have a swap file. Another diagnostic trick is to hit the <Shift> button or <Esc> on some MOBOs while the OS is booting. This will get rid of the splash screen and you can then see your services loading line by line. The choke point will usually show as a service that stalls for some period before finally timing out and getting bypassed.

Instructions for deleting/creating/modifying swap file is below:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

My experience with deleting a swap and recreating it has been that I could not thereafter encrypt it again. Your mileage may differ. Let us know how it goes.

---

### Post by stealthbyroot on 2016-09-11
> **DuckHook said:**
> @OP - please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button in the *Adv Reply* toolbar.

I've edited your posts to add such tags, but please do this yourself in future.

In my experience, long boots are often due to unavailable partitions or broken network shares. You've chased the problem down to your swap partition. It looks to me like you've activated swap encryption. This is a good idea for security purposes, but it tends to render the filesystem brittle. In your case, something has likely broken the crypt-linkage and what you are seeing is the system trying to mount swap, choking, and finally timing out to proceed without swap. You can easily tell if swap is active with:```
free -h
```&#8230;which should look something like:```
             total       used       free     shared    buffers     cached
Mem:          2.0G       612M       1.4G       1.1M       176M       305M
-/+ buffers/cache:       130M       1.8G
Swap:         998M         0B       998M
```&#8230;if the last line beginning with "Swap" is missing, then you don't have a swap file. Another diagnostic trick is to hit the <Shift> button or <Esc> on some MOBOs while the OS is booting. This will get rid of the splash screen and you can then see your services loading line by line. The choke point will usually show as a service that stalls for some period before finally timing out and getting bypassed.

Instructions for deleting/creating/modifying swap file is below:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

My experience with deleting a swap and recreating it has been that I could not thereafter encrypt it again. Your mileage may differ. Let us know how it goes.

Swap is not active.

```
stealthbyroot@Stealthbyroot-Power ~ $ free -h
              total        used        free      shared  buff/cache   available
Mem:            15G        1,7G         11G         68M        2,6G         13G
Swap:            0B          0B          0B
```

---

### Post by stealthbyroot on 2016-09-11
I am not sure but I have two swap partition. And UUID is not matching in #Entry for /dev/mapper/cryptswap1 : UUID=be8af360-b1f7-48de-a1be-b35965283ac6    none    swap    sw    0    0

[ATTACH=CONFIG]271093[/ATTACH]

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sdc3 :
UUID=4d354750-7ff0-46e9-bb35-1859f95f09e0    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdc1 :
UUID=40C2E262C2E25BA2    /media/System_Reserved    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdc2 :
#Entry for /dev/sdb1 :
#Entry for /dev/sda1 :
#Entry for /dev/mapper/cryptswap1 :
UUID=be8af360-b1f7-48de-a1be-b35965283ac6    none    swap    sw    0    0

#UUID=93e8f22b-7580-43e1-8e83-e32016c8ec6b    none    swap    sw    0    0
```

---

### Post by DuckHook on 2016-09-11
> **stealthbyroot said:**
> Swap is not active…

> **DuckHook said:**
> @OP - please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

… please do this yourself in future.&#8593;

---

### Post by stealthbyroot on 2016-09-11
Sorry for code insert mistake. Warning accepted. 

```
 
#Entry for /dev/mapper/cryptswap1 :
UUID=be8af360-b1f7-48de-a1be-b35965283ac6    none    swap    sw    0    0

#UUID=93e8f22b-7580-43e1-8e83-e32016c8ec6b    none    swap    sw    0    0

```

Should I leave this two swap partitions or erase one and proceed as per instructions [here]("https://help.ubuntu.com/community/SwapFaq").

---

### Post by DuckHook on 2016-09-11
> **stealthbyroot said:**
> Sorry for code insert mistake. Warning accepted.Not a warning. :) Just a friendly request. Sometimes, leaving code entries in standard format creates some odd artifacts like unwanted added links.
> Should I leave this two swap partitions or erase one and proceed as per instructions [here]("https://help.ubuntu.com/community/SwapFaq").You should consider erasing both so you can start from a clean slate. Then delete all old swap references from your fstab. Then reboot. Then create and add as per link.

---

### Post by Dennis N on 2016-09-11
The 2nd swap shown in fstab is deactivated, so the system hangs waiting for the first one with the wrong UUID. Why not just edit that /etc/fstab entry and change the UUID to what post #11 has?

---

### Post by DuckHook on 2016-09-11
> **Dennis N said:**
> The 2nd swap shown in fstab is deactivated, so the system hangs waiting for the first one with the wrong UUID. Why not just edit that /etc/fstab entry and change the UUID to what post #11 has?OP can try that, but if I recall when my crypt-swap broke, you cannot just change UUIDs with encrypted SWAPs. There is an internal crypt-swap pointer that maps to the original UUID. I suppose that this internal pointer can be changed as well, but don't know how to do that.

No harm in trying your suggestion, though. At most, if it doesn't work, OP is back to recreating another SWAP.

---

### Post by stealthbyroot on 2016-09-12
Now,[ATTACH=CONFIG]271125[/ATTACH][ATTACH=CONFIG]271126[/ATTACH][ATTACH=CONFIG]271127[/ATTACH] I believe that swap is ok and active. But again system is hanging 90 seconds. Maybe I am mistaking somewhere. Please find below logs and screen-shots.

```

stealthbyroot@Stealthbyroot-Power ~ $ free -h
              total        used        free      shared  buff/cache   available
Mem:            15G        1,3G         12G         61M        1,5G         13G
Swap:          4,7G          0B        4,7G

```

```

stealthbyroot@Stealthbyroot-Power ~ $ sudo blkid
[sudo] password for stealthbyroot: 
/dev/sda1: LABEL="New Volume" UUID="C6140EAD140EA093" TYPE="ntfs" PARTUUID="c63193df-01"
/dev/sdb1: UUID="92D093A7D0939059" TYPE="ntfs" PARTUUID="6e607f74-01"
/dev/sdc1: LABEL="System Reserved" UUID="40C2E262C2E25BA2" TYPE="ntfs" PARTUUID="e335bf67-01"
/dev/sdc2: UUID="102CFA392CFA1984" TYPE="ntfs" PARTUUID="e335bf67-02"
/dev/sdc3: UUID="4d354750-7ff0-46e9-bb35-1859f95f09e0" TYPE="ext4" PARTUUID="e335bf67-03"
/dev/sdc4: UUID="4784e070-ee20-4986-ba8b-976d8332d485" TYPE="swap" PARTUUID="e335bf67-04"

```

```

stealthbyroot@Stealthbyroot-Power ~ $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sdc3 :
UUID=4d354750-7ff0-46e9-bb35-1859f95f09e0    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdc1 :
UUID=40C2E262C2E25BA2    /media/System_Reserved    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdc2 :
#Entry for /dev/sdb1 :
#Entry for /dev/sda1 :
#Entry for /dev/sdc4 :
UUID=4784e070-ee20-4986-ba8b-976d8332d485    none    swap    sw    0    0

UUID=92D093A7D0939059 /mnt/92D093A7D0939059 ntfs-3g nosuid,nodev,nofail,x-gvfs-show,remove_hiberfile 0 0
UUID=102CFA392CFA1984 /mnt/102CFA392CFA1984 ntfs-3g nosuid,nodev,nofail,x-gvfs-show,remove_hiberfile 0 0
UUID=C6140EAD140EA093 /mnt/C6140EAD140EA093 ntfs-3g nosuid,nodev,nofail,x-gvfs-show,remove_hiberfile 0 0


```

---

### Post by DuckHook on 2016-09-12
> **stealthbyroot said:**
> I try to press ESC but nothing is happening.On many systems, the key is <Shift>. Just one short press. Don't hold it down. Otherwise, it toggles the splash screen back on.

Don't know what to tell you here. Unless you can see the bootup process, it becomes harder and harder to diagnose.

---

### Post by Dennis N on 2016-09-12
You can use **journalctl -b** to read the systemd messages from the most recent boot. There are many lines of this. You can page through it with Page-Up and Page-Down. You can also redirect the output to a text file:

```
journalctl -b > journalout.txt
```

On my Linux Mint 18, if I press ESC once as soon as the spash screen with the Mint logo appears, it exits the splash and the scrolling system output is visible. This continues until the gdm display manager starts and presents the login screen.

---

### Post by DuckHook on 2016-09-12
> **Dennis N said:**
> You can use **journalctl -b** to read the systemd messages from the most recent boot.Thanks, Dennis N! I'm still discovering new things about systemd all the time and journalctl is incredibly useful.

---

### Post by stealthbyroot on 2016-09-13
> **Dennis N said:**
> You can use **journalctl -b** to read the systemd messages from the most recent boot. There are many lines of this. You can page through it with Page-Up and Page-Down. You can also redirect the output to a text file:

```
journalctl -b > journalout.txt
```

On my Linux Mint 18, if I press ESC once as soon as the spash screen with the Mint logo appears, it exits the splash and the scrolling system output is visible. This continues until the gdm display manager starts and presents the login screen.


Here we go. This is the problem. Code with red was red originally. 

Where to start now?

```

Sep 13 17:52:42 Stealthbyroot-Power nvidia-persistenced[3002]: Shutdown (3002)
Sep 13 17:54:11 Stealthbyroot-Power systemd[1]: dev-disk-by\x2duuid-93e8f22b\x2d7580\x2d43e1\x2d8e83\x2de32016c8ec6b.device: Job dev-disk-by\x2duuid-93e8f22b\x2d7580\x2d43e1\x2d8e83\x2de32016c8ec6b.device/start timed out.
Sep 13 17:54:11 Stealthbyroot-Power systemd[1]: [COLOR=#ff0000]Timed out waiting for device dev-disk-by\x2duuid-93e8f22b\x2d7580\x2d43e1\x2d8e83\x2de32016c8ec6b.device.[/COLOR]
Sep 13 17:54:11 Stealthbyroot-Power systemd[1]: Dependency failed for Cryptography Setup for cryptswap1.
Sep 13 17:54:11 Stealthbyroot-Power systemd[1]: Dependency failed for dev-mapper-cryptswap1.device.
Sep 13 17:54:11 Stealthbyroot-Power systemd[1]: dev-mapper-cryptswap1.device: Job dev-mapper-cryptswap1.device/start failed with result 'dependency'.
Sep 13 17:54:11 Stealthbyroot-Power systemd[1]: Dependency failed for Encrypted Volumes.
Sep 13 17:54:11 Stealthbyroot-Power systemd[1]: cryptsetup.target: Job cryptsetup.target/start failed with result 'dependency'.
Sep 13 17:54:11 Stealthbyroot-Power systemd[1]: systemd-cryptsetup@cryptswap1.service: Job systemd-cryptsetup@cryptswap1.service/start failed with result 'dependency'.
Sep 13 17:54:11 Stealthbyroot-Power systemd[1]: dev-disk-by\x2duuid-93e8f22b\x2d7580\x2d43e1\x2d8e83\x2de32016c8ec6b.device: Job dev-disk-by\x2duuid-93e8f22b\x2d7580\x2d43e1\x2d8e83\x2de32016c8ec6b.device/start failed with result 'timeout
Sep 13 17:54:11 Stealthbyroot-Power systemd[1]: Reached target System Initialization.

```

---

### Post by stealthbyroot on 2016-09-13
> **DuckHook said:**
> Thanks, Dennis N! I'm still discovering new things about systemd all the time and journalctl is incredibly useful.

BTW interesting thing. Many Thx.

---

### Post by DuckHook on 2016-09-14
> **stealthbyroot said:**
> Here we go. This is the problem. Code with red was red originally. 

Where to start now?As suspected, the problem is a non-existent encrypted swap. The encryption service is waiting to decrypt an *encrypted* swap partition that no longer exists. Although you did reactivate your swap by defining a new one (UUID=4784e070-ee20-4986-ba8b-976d8332d485), your cryptswap service is still activate and expecting an old partition (UUID=93e8f22b-7580-43e1-8e83-e32016c8ec6b). You should be able to get rid of the boot delay by removing the cryptswap service. Instructions as follows: [http://askubuntu.com/questions/34519/how-to-disable-cryptswap](http://askubuntu.com/questions/34519/how-to-disable-cryptswap)

---

### Post by stealthbyroot on 2016-09-17
> **DuckHook said:**
> As suspected, the problem is a non-existent encrypted swap. The encryption service is waiting to decrypt an *encrypted* swap partition that no longer exists. Although you did reactivate your swap by defining a new one (UUID=4784e070-ee20-4986-ba8b-976d8332d485), your cryptswap service is still activate and expecting an old partition (UUID=93e8f22b-7580-43e1-8e83-e32016c8ec6b). You should be able to get rid of the boot delay by removing the cryptswap service. Instructions as follows: [http://askubuntu.com/questions/34519/how-to-disable-cryptswap](http://askubuntu.com/questions/34519/how-to-disable-cryptswap)

Yep. This was the problem. DuckHook you are the Man. Many thanks. Problem solved.

With Linux I not bored at all. Always something new to learn.

Thanks a lot to everybody.

---

### Post by DuckHook on 2016-09-17
Glad solution was found.

*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

Good Luck and Happy Ubuntu-ing!

---

### Post by stealthbyroot on 2016-09-18
> **Dennis N said:**
> You can use **journalctl -b** to read the systemd messages from the most recent boot. There are many lines of this. You can page through it with Page-Up and Page-Down. You can also redirect the output to a text file:

```
journalctl -b > journalout.txt
```

On my Linux Mint 18, if I press ESC once as soon as the spash screen with the Mint logo appears, it exits the splash and the scrolling system output is visible. This continues until the gdm display manager starts and presents the login screen.

Sorry Denis N I forget to thank you as well.
Problem solved.

---

