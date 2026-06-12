---
title: "Video signal lost after upgrading to Groovy"
date: 2020-10-29
forum: Installation &amp; Upgrades
---

### Post by DuckHook on 2020-10-29
My main machine multi&#8209;boots three Ubuntu OSes. Network upgrading one of those partitions to Groovy yesterday broke my video output for that OS. I can get as far as GRUB, but if I choose normal boot, the video then drops out and does not come back. I assume the login process is continuing sans video, but this is a guess. System responds to REISUB.

Things tried so far:
[LIST]
[*]Boot in normal mode &#8594; <Ctrl>+<Alt>+<F3>: No joy. Video is completely absent and I cannot see if I successfully invoked a bash shell.
[*]Boot in rescue mode &#8594; choose older kernel: This works. I can bring up login and get to my desktop.
[*]Boot in normal mode with nomodeset: Video now works but at 1080p (my proper mode is 4K). I also get a lot of system errors (log attached below). Concerningly, dmesg does not work at all:```

duckhook@Zeus:~$ dmesg
dmesg: read kernel buffer failed: Operation not permitted
```Fortunately, syslog still works and the output below is from syslog:```
duckhook@Zeus:~$ cat /var/log/syslog | egrep -i 'error|warn|fault|fatal|fail'
Oct 29 14:56:04 Zeus ureadahead[413]: ureadahead: Error while tracing: No such file or directory
Oct 29 14:56:04 Zeus systemd-sysctl[420]: Not setting net/ipv4/conf/default/promote_secondaries (explicit setting exists).
Oct 29 14:56:04 Zeus kernel: [    0.001016] MTRR default type: uncachable
Oct 29 14:56:04 Zeus kernel: [    0.001937] WARNING: BIOS bug: CPU MTRRs don't cover all of memory, losing 69MB of RAM.
Oct 29 14:56:04 Zeus systemd-udevd[488]: Using default interface naming scheme 'v245'.
Oct 29 14:56:04 Zeus kernel: [    0.345314] pid_max: default: 32768 minimum: 301
Oct 29 14:56:04 Zeus apparmor.systemd[1020]: Warning: found usr.sbin.sssd in /etc/apparmor.d/force-complain, forcing complain mode
Oct 29 14:56:04 Zeus apparmor.systemd[1020]: Warning from /etc/apparmor.d (/etc/apparmor.d/usr.sbin.sssd line 54): Caching disabled for: 'usr.sbin.sssd' due to force complain
Oct 29 14:56:04 Zeus kernel: [    0.687337] iommu: Default domain type: Translated 
Oct 29 14:56:04 Zeus kernel: [    0.687337] NetLabel:  unlabeled traffic allowed by default
Oct 29 14:56:04 Zeus systemd[1]: Condition check resulted in Process error reports when automatic reporting is enabled (file watch) being skipped.
Oct 29 14:56:04 Zeus kernel: [    0.765874] PCI: CLS 64 bytes, default 64
Oct 29 14:56:04 Zeus systemd[1]: Starting GRUB failed boot detection...
Oct 29 14:56:04 Zeus kernel: [    1.192919] RAS: Correctable Errors collector initialized.
Oct 29 14:56:04 Zeus systemd[1]: Finished GRUB failed boot detection.
Oct 29 14:56:04 Zeus kernel: [    3.516459] systemd[1]: systemd 246.6-1ubuntu1 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +ZSTD +SECCOMP +BLKID +ELFUTILS +KMOD +IDN2 -IDN +PCRE2 default-hierarchy=hybrid)
Oct 29 14:56:04 Zeus kernel: [    3.776888] systemd[1]: Queued start job for default target Graphical Interface.
Oct 29 14:56:04 Zeus kernel: [    3.927241] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
Oct 29 14:56:04 Zeus kernel: [    3.972683] systemd[1]: ureadahead.service: Failed with result 'exit-code'.
Oct 29 14:56:04 Zeus kernel: [    4.456601] [drm] Changing default dispclk from 500Mhz to 600Mhz
Oct 29 14:56:04 Zeus kernel: [    4.916544] EDAC sbridge: Failed to register device with error -19.
Oct 29 14:56:04 Zeus kernel: [    5.261974] EDAC sbridge: Failed to register device with error -19.
Oct 29 14:56:04 Zeus kernel: [    5.349913] EDAC sbridge: Failed to register device with error -19.
Oct 29 14:56:04 Zeus kernel: [    5.405817] EDAC sbridge: Failed to register device with error -19.
Oct 29 14:56:04 Zeus kernel: [    5.481893] EDAC sbridge: Failed to register device with error -19.
Oct 29 14:56:04 Zeus kernel: [    5.537793] EDAC sbridge: Failed to register device with error -19.
Oct 29 14:56:04 Zeus kernel: [    5.594098] EDAC sbridge: Failed to register device with error -19.
Oct 29 14:56:04 Zeus kernel: [    5.645843] EDAC sbridge: Failed to register device with error -19.
Oct 29 14:56:04 Zeus kernel: [    5.722379] EDAC sbridge: Failed to register device with error -19.
Oct 29 14:56:04 Zeus kernel: [    5.770355] EDAC sbridge: Failed to register device with error -19.
Oct 29 14:56:04 Zeus kernel: [    5.825848] EDAC sbridge: Failed to register device with error -19.
Oct 29 14:56:04 Zeus kernel: [    5.933703] EDAC sbridge: Failed to register device with error -19.
Oct 29 14:56:04 Zeus NetworkManager[1110]: <info>  [1604004964.6376] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, 20-connectivity-ubuntu.conf, no-mac-addr-change.conf) (run: 10-globally-managed-devices.conf) (etc: default-wifi-powersave-on.conf)
Oct 29 14:56:04 Zeus switcheroo-cont[1149]: g_variant_new_string: assertion 'string != NULL' failed
Oct 29 14:56:04 Zeus switcheroo-cont[1149]: g_variant_ref_sink: assertion 'value != NULL' failed
Oct 29 14:56:04 Zeus switcheroo-cont[1149]: g_variant_ref: assertion 'value != NULL' failed
Oct 29 14:56:04 Zeus switcheroo-cont[1149]: g_variant_unref: assertion 'value != NULL' failed
Oct 29 14:56:04 Zeus systemd[1]: sssd.service: Failed with result 'exit-code'.
Oct 29 14:56:04 Zeus systemd[1]: Failed to start System Security Services Daemon.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD PAM Service responder private socket.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD PAM Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-pam.socket: Job sssd-pam.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: sssd-pam-priv.socket: Job sssd-pam-priv.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD NSS Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD SSH Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-ssh.socket: Job sssd-ssh.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD Sudo Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-sudo.socket: Job sssd-sudo.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD AutoFS Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-autofs.socket: Job sssd-autofs.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD PAC Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-pac.socket: Job sssd-pac.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus thermald[1151]: THD engine start failed
Oct 29 14:56:04 Zeus udisksd[1152]: failed to load module mdraid: libbd_mdraid.so.2: cannot open shared object file: No such file or directory
Oct 29 14:56:04 Zeus udisksd[1152]: Failed to load the 'mdraid' libblockdev plugin
Oct 29 14:56:04 Zeus networkd-dispatcher[1255]: WARNING: systemd-networkd is not running, output will be incomplete.
Oct 29 14:56:04 Zeus systemd[1]: sssd.service: Failed with result 'exit-code'.
Oct 29 14:56:04 Zeus systemd[1]: Failed to start System Security Services Daemon.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD PAM Service responder private socket.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD PAM Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-pam.socket: Job sssd-pam.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: sssd-pam-priv.socket: Job sssd-pam-priv.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD NSS Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD SSH Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-ssh.socket: Job sssd-ssh.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD Sudo Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-sudo.socket: Job sssd-sudo.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD AutoFS Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-autofs.socket: Job sssd-autofs.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD PAC Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-pac.socket: Job sssd-pac.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus NetworkManager[1110]: <info>  [1604004964.7875] settings: (eno1): created default wired connection 'Wired connection 1'
Oct 29 14:56:04 Zeus systemd[1]: sssd.service: Failed with result 'exit-code'.
Oct 29 14:56:04 Zeus systemd[1]: Failed to start System Security Services Daemon.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD PAM Service responder private socket.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD PAM Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-pam.socket: Job sssd-pam.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: sssd-pam-priv.socket: Job sssd-pam-priv.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD NSS Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD SSH Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-ssh.socket: Job sssd-ssh.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD Sudo Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-sudo.socket: Job sssd-sudo.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD AutoFS Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-autofs.socket: Job sssd-autofs.socket/start failed with result 'dependency'.
Oct 29 14:56:04 Zeus systemd[1]: Dependency failed for SSSD PAC Service responder socket.
Oct 29 14:56:04 Zeus systemd[1]: sssd-pac.socket: Job sssd-pac.socket/start failed with result 'dependency'.
Oct 29 14:56:05 Zeus kernel: [    6.960677] [drm:si_dpm_set_power_state [radeon]] *ERROR* si_restrict_performance_levels_before_switch failed
Oct 29 14:56:05 Zeus systemd[1]: sssd.service: Failed with result 'exit-code'.
Oct 29 14:56:05 Zeus systemd[1]: Failed to start System Security Services Daemon.
Oct 29 14:56:05 Zeus systemd[1]: Dependency failed for SSSD PAM Service responder private socket.
Oct 29 14:56:05 Zeus systemd[1]: Dependency failed for SSSD PAM Service responder socket.
Oct 29 14:56:05 Zeus systemd[1]: sssd-pam.socket: Job sssd-pam.socket/start failed with result 'dependency'.
Oct 29 14:56:05 Zeus systemd[1]: sssd-pam-priv.socket: Job sssd-pam-priv.socket/start failed with result 'dependency'.
Oct 29 14:56:05 Zeus systemd[1]: Dependency failed for SSSD NSS Service responder socket.
Oct 29 14:56:05 Zeus systemd[1]: sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Oct 29 14:56:05 Zeus systemd[1]: Dependency failed for SSSD SSH Service responder socket.
Oct 29 14:56:05 Zeus systemd[1]: sssd-ssh.socket: Job sssd-ssh.socket/start failed with result 'dependency'.
Oct 29 14:56:05 Zeus systemd[1]: Dependency failed for SSSD Sudo Service responder socket.
Oct 29 14:56:05 Zeus systemd[1]: sssd-sudo.socket: Job sssd-sudo.socket/start failed with result 'dependency'.
Oct 29 14:56:05 Zeus systemd[1]: Dependency failed for SSSD AutoFS Service responder socket.
Oct 29 14:56:05 Zeus systemd[1]: sssd-autofs.socket: Job sssd-autofs.socket/start failed with result 'dependency'.
Oct 29 14:56:05 Zeus systemd[1]: Dependency failed for SSSD PAC Service responder socket.
Oct 29 14:56:05 Zeus systemd[1]: sssd-pac.socket: Job sssd-pac.socket/start failed with result 'dependency'.
Oct 29 14:56:05 Zeus kernel: [    7.138174] [drm:radeon_dp_link_train_cr [radeon]] *ERROR* clock recovery tried 5 times
Oct 29 14:56:05 Zeus kernel: [    7.138218] [drm:radeon_dp_link_train_cr [radeon]] *ERROR* clock recovery failed
Oct 29 14:56:05 Zeus systemd[1]: sssd.service: Failed with result 'exit-code'.
Oct 29 14:56:05 Zeus systemd[1]: Failed to start System Security Services Daemon.
Oct 29 14:56:05 Zeus systemd[1]: Dependency failed for SSSD PAM Service responder private socket.
Oct 29 14:56:05 Zeus systemd[1]: Dependency failed for SSSD PAM Service responder socket.
Oct 29 14:56:05 Zeus systemd[1]: sssd-pam.socket: Job sssd-pam.socket/start failed with result 'dependency'.
Oct 29 14:56:05 Zeus systemd[1]: sssd-pam-priv.socket: Job sssd-pam-priv.socket/start failed with result 'dependency'.
Oct 29 14:56:05 Zeus systemd[1]: Dependency failed for SSSD NSS Service responder socket.
Oct 29 14:56:05 Zeus systemd[1]: sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Oct 29 14:56:05 Zeus systemd[1]: Dependency failed for SSSD SSH Service responder socket.
Oct 29 14:56:05 Zeus systemd[1]: sssd-ssh.socket: Job sssd-ssh.socket/start failed with result 'dependency'.
Oct 29 14:56:05 Zeus systemd[1]: Dependency failed for SSSD Sudo Service responder socket.
Oct 29 14:56:05 Zeus systemd[1]: sssd-sudo.socket: Job sssd-sudo.socket/start failed with result 'dependency'.
Oct 29 14:56:05 Zeus systemd[1]: Dependency failed for SSSD AutoFS Service responder socket.
Oct 29 14:56:05 Zeus systemd[1]: sssd-autofs.socket: Job sssd-autofs.socket/start failed with result 'dependency'.
Oct 29 14:56:05 Zeus systemd[1]: Dependency failed for SSSD PAC Service responder socket.
Oct 29 14:56:05 Zeus systemd[1]: sssd-pac.socket: Job sssd-pac.socket/start failed with result 'dependency'.
Oct 29 14:56:06 Zeus systemd[1]: sssd.service: Failed with result 'exit-code'.
Oct 29 14:56:06 Zeus systemd[1]: Failed to start System Security Services Daemon.
Oct 29 14:56:06 Zeus systemd[1]: Dependency failed for SSSD PAM Service responder private socket.
Oct 29 14:56:06 Zeus systemd[1]: Dependency failed for SSSD PAM Service responder socket.
Oct 29 14:56:06 Zeus systemd[1]: sssd-pam.socket: Job sssd-pam.socket/start failed with result 'dependency'.
Oct 29 14:56:06 Zeus systemd[1]: sssd-pam-priv.socket: Job sssd-pam-priv.socket/start failed with result 'dependency'.
Oct 29 14:56:06 Zeus systemd[1]: Dependency failed for SSSD NSS Service responder socket.
Oct 29 14:56:06 Zeus systemd[1]: sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Oct 29 14:56:06 Zeus systemd[1]: Dependency failed for SSSD SSH Service responder socket.
Oct 29 14:56:06 Zeus systemd[1]: sssd-ssh.socket: Job sssd-ssh.socket/start failed with result 'dependency'.
Oct 29 14:56:06 Zeus systemd[1]: Dependency failed for SSSD Sudo Service responder socket.
Oct 29 14:56:06 Zeus systemd[1]: sssd-sudo.socket: Job sssd-sudo.socket/start failed with result 'dependency'.
Oct 29 14:56:06 Zeus systemd[1]: Dependency failed for SSSD AutoFS Service responder socket.
Oct 29 14:56:06 Zeus systemd[1]: sssd-autofs.socket: Job sssd-autofs.socket/start failed with result 'dependency'.
Oct 29 14:56:06 Zeus systemd[1]: Dependency failed for SSSD PAC Service responder socket.
Oct 29 14:56:06 Zeus systemd[1]: sssd-pac.socket: Job sssd-pac.socket/start failed with result 'dependency'.
Oct 29 14:56:06 Zeus colord[1409]: failed to get session [pid 1392]: No data available
Oct 29 14:56:07 Zeus systemd[1446]: Not generating service for XDG autostart app-nautilus\x2dautostart-autostart.service, error parsing Exec= line: No such file or directory
Oct 29 14:56:07 Zeus systemd[1446]: Not generating service for XDG autostart app-gnome\x2dsoftware\x2dservice-autostart.service, error parsing Exec= line: No such file or directory
Oct 29 14:56:07 Zeus systemd[1441]: Queued start job for default target Main User Target.
Oct 29 14:56:07 Zeus /usr/libexec/gdm-wayland-session[1463]: dbus-daemon[1463]: [session uid=127 pid=1463] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:07 Zeus /usr/libexec/gdm-wayland-session[1463]: dbus-daemon[1463]: [session uid=127 pid=1463] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:07 Zeus gnome-session[1467]: gnome-session-binary[1467]: WARNING: Failed to reset failed state of units: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:07 Zeus gnome-session-binary[1467]: WARNING: Failed to reset failed state of units: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:07 Zeus /usr/libexec/gdm-wayland-session[1463]: dbus-daemon[1463]: [session uid=127 pid=1463] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:07 Zeus gnome-session[1467]: gnome-session-binary[1467]: WARNING: Falling back to non-systemd startup procedure due to error: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:07 Zeus gnome-session-binary[1467]: WARNING: Falling back to non-systemd startup procedure due to error: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:07 Zeus /usr/libexec/gdm-wayland-session[1463]: dbus-daemon[1463]: [session uid=127 pid=1463] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:07 Zeus /usr/libexec/gdm-wayland-session[1463]: dbus-daemon[1463]: [session uid=127 pid=1463] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:07 Zeus /usr/libexec/gdm-wayland-session[1463]: dbus-daemon[1463]: [session uid=127 pid=1463] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:07 Zeus /usr/libexec/gdm-wayland-session[1463]: dbus-daemon[1463]: [session uid=127 pid=1463] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:07 Zeus /usr/libexec/gdm-wayland-session[1463]: dbus-daemon[1463]: [session uid=127 pid=1463] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:08 Zeus /usr/libexec/gdm-wayland-session[1463]: dbus-daemon[1463]: [session uid=127 pid=1463] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:08 Zeus /usr/libexec/gdm-wayland-session[1463]: dbus-daemon[1463]: [session uid=127 pid=1463] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:08 Zeus /usr/libexec/gdm-wayland-session[1463]: dbus-daemon[1463]: [session uid=127 pid=1463] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:08 Zeus /usr/libexec/gdm-wayland-session[1463]: dbus-daemon[1463]: [session uid=127 pid=1463] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:09 Zeus /hpfax: [1714]: error: Failed to create /var/spool/cups/tmp/.hplip
Oct 29 14:56:09 Zeus gnome-shell[1525]: _clutter_stage_queue_event: assertion 'CLUTTER_IS_STAGE (stage)' failed
Oct 29 14:56:09 Zeus gnome-shell[1525]: _clutter_stage_queue_event: assertion 'CLUTTER_IS_STAGE (stage)' failed
Oct 29 14:56:09 Zeus gnome-shell[1525]: _clutter_stage_queue_event: assertion 'CLUTTER_IS_STAGE (stage)' failed
Oct 29 14:56:09 Zeus gnome-shell[1525]: _clutter_stage_queue_event: assertion 'CLUTTER_IS_STAGE (stage)' failed
Oct 29 14:56:09 Zeus gnome-shell[1525]: _clutter_stage_queue_event: assertion 'CLUTTER_IS_STAGE (stage)' failed
Oct 29 14:56:09 Zeus gnome-shell[1525]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
Oct 29 14:56:09 Zeus switcheroo-cont[1149]: g_variant_new_string: assertion 'string != NULL' failed
Oct 29 14:56:09 Zeus switcheroo-cont[1149]: g_variant_ref_sink: assertion 'value != NULL' failed
Oct 29 14:56:09 Zeus switcheroo-cont[1149]: g_variant_ref: assertion 'value != NULL' failed
Oct 29 14:56:09 Zeus switcheroo-cont[1149]: g_variant_unref: assertion 'value != NULL' failed
Oct 29 14:56:09 Zeus /usr/libexec/gdm-wayland-session[1463]: dbus-daemon[1463]: [session uid=127 pid=1463] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:09 Zeus gsd-sharing[1741]: Failed to StopUnit service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:09 Zeus gsd-sharing[1741]: message repeated 3 times: [ Failed to StopUnit service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1]
Oct 29 14:56:09 Zeus NetworkManager[1110]: <info>  [1604004969.9194] policy: set 'Wired connection 1' (eno1) as default for IPv4 routing and DNS
Oct 29 14:56:09 Zeus /usr/libexec/gdm-wayland-session[1463]: dbus-daemon[1463]: [session uid=127 pid=1463] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:09 Zeus gsd-sharing[1741]: Failed to StopUnit service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
Oct 29 14:56:09 Zeus gsd-sharing[1741]: message repeated 3 times: [ Failed to StopUnit service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1]
Oct 29 14:56:09 Zeus systemd[1]: Started Download data for packages that failed at package install time.
Oct 29 14:56:10 Zeus gsd-media-keys[1762]: Failed to grab accelerator for keybinding settings:rfkill
Oct 29 14:56:10 Zeus gsd-media-keys[1762]: Failed to grab accelerator for keybinding settings:playback-random
Oct 29 14:56:10 Zeus gsd-media-keys[1762]: Failed to grab accelerator for keybinding settings:hibernate
Oct 29 14:56:10 Zeus gsd-media-keys[1762]: Failed to grab accelerator for keybinding settings:playback-repeat
Oct 29 14:56:10 Zeus org.gnome.Shell.desktop[2043]: > Warning:          Unsupported maximum keycode 569, clipping.
Oct 29 14:56:10 Zeus org.gnome.Shell.desktop[2043]: > Internal error:   Could not resolve keysym Invalid
Oct 29 14:56:10 Zeus org.gnome.Shell.desktop[2043]: Errors from xkbcomp are not fatal to the X server
Oct 29 14:56:10 Zeus gsd-printer[1858]: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.PackageKit was not provided by any .service files
Oct 29 14:56:11 Zeus whoopsie[1870]: [14:56:11] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
Oct 29 14:56:20 Zeus systemd-resolved[1025]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 29 14:56:38 Zeus udev-add-printer: D-Bus method call failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Oct 29 14:56:51 Zeus /usr/libexec/gdm-wayland-session[2074]: /usr/share/system-config-printer/scp-dbus-service.py:602: DeprecationWarning: Gdk.threads_enter is deprecated
Oct 29 15:01:04 Zeus systemd[1]: Starting Download data for packages that failed at package install time...
Oct 29 15:01:04 Zeus systemd[1]: Finished Download data for packages that failed at package install time.
Binary file (standard input) matches

```[/LIST]I've filtered output to keep things manageable, but as you can see, a ton of failures and errors.

I'm at a loss for what to try next and appreciate all comments/suggestions.

---

### Post by DuckHook on 2020-10-30
*bump*

---

### Post by oldfred on 2020-10-30
What video card/chip?
Typically nomodeset required with nVidia.
But have seen a few with other video cards that used nomodeset. But all those AMD & Intel video are just supposed to work.

#What is installed
dkms status
#To see video:
lspci -vnn | grep VGA -A 12
sudo lshw -c display

Before you had to uninstall nVidia driver if nVidia, upgrade and reinstall nVidia driver.
New versions with full install automatically install recommended nVidia driver. Not sure with upgrade.

---

### Post by DuckHook on 2020-10-30
Thanks for your kindness in replying oldfred.

I should have posted the display specs before but suspected that GPU wasn't the actual problem. Nonetheless, they are now included below. I have never installed dkms on this OS because I've never needed it in the past:
```
duckhook@Zeus:~$ dkms status
Command 'dkms' not found, but can be installed with:
sudo apt install dkms
duckhook@Zeus:~$ sudo lspci -vnn | grep -iA20 vga
[sudo] password for duckhook: 
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280] [1002:679a] (prog-if 00 [VGA controller])
	Subsystem: Hightech Information System Ltd. Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280] [1787:201c]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fbe00000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at e000 [size=256]
	Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Capabilities: [270] Secondary PCI Express
	Capabilities: [2b0] Address Translation Service (ATS)
	Capabilities: [2c0] Page Request Interface (PRI)
	Capabilities: [2d0] Process Address Space ID (PASID)
	Kernel modules: radeon, amdgpu

01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti HDMI Audio [Radeon HD 7870 XT / 7950/7970] [1002:aaa0]
	Subsystem: Hightech Information System Ltd. Tahiti HDMI Audio [Radeon HD 7870 XT / 7950/7970] [1787:aaa0]
duckhook@Zeus:~$ sudo lshw -c display
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff memory:fbe00000-fbe3ffff ioport:e000(size=256) memory:c0000-dffff

```
At the risk of clouding the issue, please note that someone else has now posted with almost the identical problem on very different HW: [https://ubuntuforums.org/showthread.php?t=2452939](https://ubuntuforums.org/showthread.php?t=2452939)

---

### Post by oldfred on 2020-10-30
Install dkms and run that command, just to see.
But I thought AMD just worked and do not know the work arounds for those models.

From my notes, may not be most current info:
[https://ubuntuforums.org/showthread.php?t=2443998](https://ubuntuforums.org/showthread.php?t=2443998)
[https://amdgpu-install.readthedocs.io/en/latest/](https://amdgpu-install.readthedocs.io/en/latest/)
 latest PRO driver for Ubuntu 20.04. as of May 2020, check that your card is supported
[https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-10](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-10)
If you want to enable support for Open-GL & Open-CL, need to get the amdgpu-Pro driver from AMD website. 
amdgpu enabled by default on newer cards. Old cards can't use amdgpu and use radeon instead. There are some cards in between that could use amdgpu, but it's experimental, so they default to radeon. 


[https://ubuntuforums.org/showthread.php?t=2372733](https://ubuntuforums.org/showthread.php?t=2372733)
If your card is supported by AMDGPU, it will be installed when you install Ubuntu. You can only install the AMDGPU-PRO overlay if AMDGPU is installed. If your card is not supported by AMDGPU, the Radeon driver will be installed.
It's automagic now. You don't need to do anything unless you have a need or pressing desire for the overlay-- for instance if you need Vulkan support. In that case, AMD has a script that will take care of it. 
[https://www.amd.com/en/support/kb/faq/gpu-635](https://www.amd.com/en/support/kb/faq/gpu-635)

---

### Post by DuckHook on 2020-10-30
OK oldfred. Will check into these options later tonight. I'm going to be offline for the next few hours, but will get back to this late tonight.

FTR, though I last checked a couple of years ago, my research at that time indicated that I am restricted to Radeon. Unfortunately, my GPU chipset was apparently the last one on Radeon. All newer chipsets could use AMDGPU, so I bought just a tad too early. But there were rumours that AMD might backport the newer driver to my chipset even then, so I will do more research tonight.

Will try installing DKMS too.

Stay tuned folks&#8230;

---

### Post by DuckHook on 2020-10-31
Installed dkms and its associated dependencies, but still no joy. I confirm that my GPU/chipset uses the older radeon driver. It does not show in the output attached in post #4 above because those results were generated under nomodeset.

I am beginning to suspect that there is something broken in the implementation of the 5.8 kernel. Perhaps a regression or a new incompatibility. The fallback kernel is 5.4 and things are still working nicely with that one: it generates none of the syslog failures/errors that plague the newer kernel. Note also that I can invoke dmesg using the 5.4 kernel but not with 5.8. That, along with the list of errors, leads me to believe that the problem is not the video driver but the kernel implementation.

@oldfred: I've gone through your links and it appears that my video card does not support AMDGPU. Moreover, the site's Radeon driver is version 20.10 and only supports up to Bionic. It does not mention Focal much less Groovy.

I might install ssh server into the cussed thing and try troubleshooting remotely, but seeing as it's a partition that I use mainly for minimal exploration and tinkering, I'm not sure it's worth the time investment. If there are no obvious solutions, I may just compose myself in patience and see whether the next kernel update fixes things.

---

### Post by DuckHook on 2020-10-31
I eliminated some of the more alarming errors (see post #1 above) by nuking *sssd* from the install. Based on [this launchpad thread]("https://bugs.launchpad.net/ubuntu/+source/sssd/+bug/1897153"), it seems that *sssd* was folded into Ubuntu at some point to work with MS Active Directory. I don't need *sssd* at all, so I took a chance and deleted it. This doesn't seem to create any new problems, but unfortunately, it didn't solve my initial problem either. It merely cleaned up the logs a bit.

Will continue to wrestle with this as time allows.

---

### Post by smojo on 2020-11-02
Hey DuckHook, we had rather similar problems.
I fixed mine by upgrading to Kernel 5.10_RC1, maybe worth checking out?

---

### Post by DuckHook on 2020-11-02
> **smojo said:**
> Hey DuckHook, we had rather similar problems.
I fixed mine by upgrading to Kernel 5.10_RC1, maybe worth checking out?
It's very kind of you to update me on your successful strategy. I'm torn between trying an RC kernel vs sticking with my older one, but since it is just a tinkering partition, I might just go ahead. My quandary is, I don't want to depart too much from default because I rely on a relatively default setup in order to help out on these forums.

Thanks for the heads&#8209;up though. It is much appreciated.

---

### Post by DuckHook on 2020-11-04
Brief update:

I've just tried the 5.10_RC1 kernel and it doesn't solve the problem for me. Part of the ongoing process of elimination.

---

### Post by tea for one on 2020-11-04
Out of curiosity - did you ever try a live session with Ubuntu 20.10?

---

### Post by DuckHook on 2020-11-04
> **tea for one said:**
> Out of curiosity - did you ever try a live session with Ubuntu 20.10?
That was going to be my next project. I've been rather lackadaisical over this one because it really is just a tinkering partition, so I haven't pursued it very ardently, but I will be sure to post results when I do so.

---

### Post by DuckHook on 2020-11-14
> **DuckHook said:**
> …I will be sure to post results when I do so.
Final update:

I was never able to get Groovy to behave. A LiveUSB worked. But once installed as a virgin OS, the same problems emerged (requiring nomodeset to display, but even then generating a laundry list of nasty log errors that I was in no mood to chase down). With nothing left to lose (I had lost all my customizations with the virgin install), I took the big leap and upgraded to Hirsute. It now comes up fast and furious, so I am happy/relieved.

The problem has not been "solved" (since I never did get to the bottom of what was bugging out Groovy) so much as it has been "**re**solved" (through upgrading to the current developmental release), so I'm not going to mark this thread solved.

I will spend some time exploring Hirsute. As for Groovy, it will just be one of those releases that I skip.

---

### Post by DuckHook on 2020-11-14
Spoke far too soon. Hirsute misbehaves exactly like Groovy. I got to the DE the first time after upgrading, but not since. Continuing to diagnose.

---

### Post by DuckHook on 2020-11-16
After much trial and error, I've narrowed the issue down to the following. My video card drops its signal to my monitor, likely when the framebuffer kicks in. Though I have neutered both *splash* and *quiet*, the entries still race by so quickly that this is no more than an educated guess, but it conforms to that moment in the sequence when I boot my other 20.04 partition.

The salient info follows:

Driver: Radeon
Discrete video card: ```
duckhook@Zeus:~$ sudo lspci -vk | grep -iA20 vga
[sudo] password for duckhook: 
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280] (prog-if 00 [VGA controller])
	Subsystem: Hightech Information System Ltd. Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
	Flags: bus master, fast devsel, latency 0, IRQ 56
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fbe00000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at e000 [size=256]
	Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Capabilities: [270] Secondary PCI Express
	Capabilities: [2b0] Address Translation Service (ATS)
	Capabilities: [2c0] Page Request Interface (PRI)
	Capabilities: [2d0] Process Address Space ID (PASID)
	Kernel driver in use: radeon
	Kernel modules: radeon, amdgpu
```
Salient log items: ```
duckhook@Zeus:~$ sudo journalctl -b | grep radeon | grep kernel
Nov 15 18:49:01 Zeus kernel: [drm] radeon kernel modesetting enabled.
Nov 15 18:49:01 Zeus kernel: fb0: switching to radeondrmfb from EFI VGA
Nov 15 18:49:01 Zeus kernel: radeon 0000:01:00.0: vgaarb: deactivate vga console
Nov 15 18:49:01 Zeus kernel: radeon 0000:01:00.0: VRAM: 3072M 0x0000000000000000 - 0x00000000BFFFFFFF (3072M used)
Nov 15 18:49:01 Zeus kernel: radeon 0000:01:00.0: GTT: 2048M 0x00000000C0000000 - 0x000000013FFFFFFF
Nov 15 18:49:01 Zeus kernel: [drm] radeon: 3072M of VRAM memory ready
Nov 15 18:49:01 Zeus kernel: [drm] radeon: 2048M of GTT memory ready.
Nov 15 18:49:01 Zeus kernel: [drm] radeon: dpm initialized
Nov 15 18:49:01 Zeus kernel: radeon 0000:01:00.0: WB enabled
Nov 15 18:49:01 Zeus kernel: radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x00000000c0000c00 and cpu addr 0x00000000a217189e
Nov 15 18:49:01 Zeus kernel: radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x00000000c0000c04 and cpu addr 0x0000000050fe85a6
Nov 15 18:49:01 Zeus kernel: radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x00000000c0000c08 and cpu addr 0x0000000020952302
Nov 15 18:49:01 Zeus kernel: radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x00000000c0000c0c and cpu addr 0x000000009ceb52ec
Nov 15 18:49:01 Zeus kernel: radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x00000000c0000c10 and cpu addr 0x0000000091a1317a
Nov 15 18:49:01 Zeus kernel: radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0x00000000fadfaf36
Nov 15 18:49:01 Zeus kernel: radeon 0000:01:00.0: fence driver on ring 6 use gpu addr 0x00000000c0000c18 and cpu addr 0x00000000176b3432
Nov 15 18:49:01 Zeus kernel: radeon 0000:01:00.0: fence driver on ring 7 use gpu addr 0x00000000c0000c1c and cpu addr 0x00000000a7719c7c
Nov 15 18:49:01 Zeus kernel: radeon 0000:01:00.0: radeon: MSI limited to 32-bit
Nov 15 18:49:01 Zeus kernel: radeon 0000:01:00.0: radeon: using MSI.
Nov 15 18:49:01 Zeus kernel: [drm] radeon: irq initialized.
Nov 15 18:49:04 Zeus kernel: [drm] Radeon Display Connectors
Nov 15 18:49:04 Zeus kernel: fbcon: radeondrmfb (fb0) is primary device
Nov 15 18:49:04 Zeus kernel: [drm:si_dpm_set_power_state [radeon]] *ERROR* si_restrict_performance_levels_before_switch failed
Nov 15 18:49:04 Zeus kernel: radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
Nov 15 18:49:04 Zeus kernel: [drm:radeon_dp_link_train_cr [radeon]] *ERROR* clock recovery tried 5 times
Nov 15 18:49:04 Zeus kernel: [drm:radeon_dp_link_train_cr [radeon]] *ERROR* clock recovery failed
Nov 15 18:49:04 Zeus kernel: [drm] Initialized radeon 2.50.0 20080528 for 0000:01:00.0 on minor 0
```
**In summary:**

[list=1]
[*]The LiveUSB is just as problematic. No video signal without nomodeset.
[*]Booting up with the old 5.4.x kernels works. It's the 5.8.x kernel series that causes the problem.
[*]5.10.x-RC kernels do not work either.
[*]nomodeset always works. This is not surprising since it nerfs KMS.
[*]The problem is only the video signal. I can ssh into the session just fine.
[*]When comparing the logs between a successful older kernel and a problematic newer one, the only difference is this: ```
Nov 15 18:49:04 Zeus kernel: [drm:radeon_dp_link_train_cr [radeon]] *ERROR* clock recovery tried 5 times
Nov 15 18:49:04 Zeus kernel: [drm:radeon_dp_link_train_cr [radeon]] *ERROR* clock recovery failed
```[/list]
My Web Search Fu has deserted me. All I could find with respect to these errors were these slim pickings:

[http://linux-kernel.2935.n7.nabble.com/drm-radeon-dp-link-train-ERROR-clock-recovery-failed-td1320976.html](http://linux-kernel.2935.n7.nabble.com/drm-radeon-dp-link-train-ERROR-clock-recovery-failed-td1320976.html)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1579481](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1579481)
[https://askubuntu.com/questions/1278714/ubuntu-20-04-amd-free-radeon-driver-blank-2nd-screen](https://askubuntu.com/questions/1278714/ubuntu-20-04-amd-free-radeon-driver-blank-2nd-screen)
[https://askubuntu.com/questions/1286134/ubuntu-doesnt-boot-after-failed-update-from-20-04-lts-to-20-10](https://askubuntu.com/questions/1286134/ubuntu-doesnt-boot-after-failed-update-from-20-04-lts-to-20-10)

It appears that the problem bites just a few others, and is a recurring one that has some history.

Perhaps the problem is just with my Tahiti chipset&#8209;based card. I wanted to enquire on the Forums in case any of you have found a solution before starting a bug on Launchpad.

---

### Post by DuckHook on 2020-11-17
After more time and trouble than I thought I would ever invest into it, I've traced the problem back via mainline kernel bisection to some change made starting with the 5.5.6 kernel.

I have submitted the following bug report in LaunchPad: [https://bugs.launchpad.net/ubuntu/+source/linux-hwe-5.8/+bug/1904647](https://bugs.launchpad.net/ubuntu/+source/linux-hwe-5.8/+bug/1904647)

It states my findings there. No point in repeating it here. If anyone else has this same problem, please alert the devs that this bug effects multiple users via the above link.

---

### Post by DuckHook on 2021-01-22
Final update:

The problem remains frustratingly unresolved, but I have worked around it by giving up on the Display Port and using HDMI instead. For those stuck with only DP, I'm afraid there has been no action from the devs at Launchpad. I doubt that they see this as a high priority.

---

