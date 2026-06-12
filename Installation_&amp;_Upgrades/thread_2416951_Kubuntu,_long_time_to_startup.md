---
title: "Kubuntu, long time to startup"
date: 2019-04-18
forum: Installation &amp; Upgrades
---

### Post by zalle1 on 2019-04-18
Hi guys,

I'm working on an old Dell Latitude D630 laptot, with 4GB RAM and an SSD, I installed 18.04 Kubuntu, it's all good, except the start up process, which takes a long time (around 4-5minutes). Shutdown also takes at least 1 minute.

XUBUNTU starts up in under 10 seconds, but I can't get the graphics card to work, so I went with Kubuntu.

I tried "systemd-analyze" and I get:

Startup finished in 1min 7.687s (kernel) + 50.834s (userspace) = 1min 58.522s
graphical.target reached after 21.780s in userspace

I also get these errors when starting up:

(   71.081675) leds dell::kbd_backlight: Setting an LED’s brightness failed (-5)
(   80.608217) (drm:drm_atomic helper_wait_for_flip_done (drm_kms_helper)) *ERROR* (CRTC:41:pipe B) flip_done timed out
(   90.848216) (drm:drm_atomic helper_wait_for_dependencies (drm_kms_helper)) *ERROR* (CRTC:41:pipe B) flip_done timed out
(   101.088237) (drm:drm_atomic helper_wait_for_dependencies (drm_kms_helper)) *ERROR* (CONNECTOR:52:SVIDEO-1) flip_done timed out


Any ideas of how I can make it faster?

---

### Post by VMC on 2019-04-18
From terminal type:
```
[FONT=monospace][COLOR=#000000]systemd-analyze blame --no-pager[/COLOR][/FONT]
```

Report back with results.

---

### Post by zalle1 on 2019-04-18
20.029s plymouth-quit.service
          6.419s NetworkManager-wait-online.service
          3.441s dev-sdb5.device
          1.460s mpd.service
          1.135s networkd-dispatcher.service
           809ms udisks2.service
           683ms winbind.service
           587ms ModemManager.service
           480ms accounts-daemon.service
           472ms systemd-rfkill.service
           397ms NetworkManager.service
           360ms keyboard-setup.service
           358ms systemd-journald.service
           349ms snapd.service
           342ms wpa_supplicant.service
           323ms apparmor.service
           291ms apport.service
           291ms avahi-daemon.service
           286ms systemd-udev-trigger.service
           281ms upower.service
           274ms rsyslog.service
           251ms systemd-logind.service
           239ms preload.service
           227ms systemd-journal-flush.service
           224ms thermald.service
           192ms snapd.seeded.service
           186ms swapfile.swap
           163ms grub-common.service
           161ms pppd-dns.service
           150ms systemd-resolved.service
           146ms systemd-timesyncd.service
           137ms gpu-manager.service
           126ms systemd-udevd.service
           125ms systemd-modules-load.service
           117ms polkit.service
            81ms [email]user@1000.servic[/email]e
            68ms packagekit.service
            64ms [email]systemd-backlight@backlight:dell_backlight.servic[/email]e                    
            59ms ufw.service                                                           
            58ms systemd-remount-fs.service                                            
            57ms sys-kernel-debug.mount                                                
            56ms systemd-sysctl.service
            55ms dev-hugepages.mount
            55ms dev-mqueue.mount
            54ms kmod-static-nodes.service
            48ms systemd-tmpfiles-setup.service
            46ms systemd-tmpfiles-setup-dev.service
            40ms plymouth-start.service
            35ms systemd-tmpfiles-clean.service
            31ms setvtrgb.service
            29ms sys-kernel-config.mount
            28ms sys-fs-fuse-connections.mount
            24ms systemd-user-sessions.service
            19ms console-setup.service
            18ms kerneloops.service
            17ms plymouth-read-write.service
            17ms systemd-update-utmp.service
            17ms systemd-random-seed.service
            15ms ureadahead-stop.service
            13ms systemd-update-utmp-runlevel.service
            10ms [email]systemd-backlight@backlight:intel_backlight.servic[/email]e
             6ms rtkit-daemon.service
             6ms [email]systemd-backlight@leds:dell::kbd_backlight.servic[/email]e
             6ms snapd.socket
             5ms sddm.service

---

### Post by VMC on 2019-04-18
Please put your info between code-tags: ```
info
```

---

### Post by zalle1 on 2019-04-19
```
20.214s plymouth-quit.service
          6.491s NetworkManager-wait-online.service
          4.915s apt-daily-upgrade.service
          3.965s dev-sda5.device
          1.233s apparmor.service
          1.220s systemd-udevd.service
          1.118s systemd-journal-flush.service
          1.024s plymouth-read-write.service
          1.004s console-setup.service
           992ms mpd.service
           982ms networkd-dispatcher.service
           830ms udisks2.service
           747ms systemd-rfkill.service
           481ms ModemManager.service
           465ms NetworkManager.service
           396ms systemd-journald.service
           390ms systemd-backlight@backlight:dell_backlight.service
           379ms keyboard-setup.service
           362ms systemd-udev-trigger.service
           338ms accounts-daemon.service
           313ms winbind.service
           306ms snapd.service
           285ms preload.service
           276ms wpa_supplicant.service
           269ms upower.service
           225ms thermald.service
           199ms snapd.seeded.service
           197ms grub-common.service
           174ms apport.service
           170ms avahi-daemon.service
           148ms swapfile.swap
           143ms systemd-timesyncd.service
           135ms systemd-resolved.service
           117ms gpu-manager.service
           105ms systemd-modules-load.service
            95ms rsyslog.service
            77ms systemd-sysctl.service
            77ms user@1000.service
            74ms kmod-static-nodes.service
            74ms polkit.service                                                        
            72ms pppd-dns.service                                                      
            71ms systemd-remount-fs.service                                            
            71ms dev-mqueue.mount                                                      
            69ms dev-hugepages.mount
            66ms packagekit.service
            66ms ufw.service
            62ms sys-kernel-debug.mount
            53ms sys-kernel-config.mount
            52ms sys-fs-fuse-connections.mount
            47ms systemd-logind.service
            46ms systemd-tmpfiles-setup-dev.service
            39ms systemd-tmpfiles-setup.service
            32ms systemd-random-seed.service
            31ms plymouth-start.service
            22ms systemd-user-sessions.service
            20ms kerneloops.service
            20ms setvtrgb.service
            16ms ureadahead-stop.service
            13ms systemd-update-utmp-runlevel.service
            11ms systemd-update-utmp.service
             8ms snapd.socket
             7ms systemd-backlight@leds:dell::kbd_backlight.service
             7ms rtkit-daemon.service
             7ms sddm.service
             6ms systemd-backlight@backlight:intel_backlight.service
```

---

### Post by VMC on 2019-04-19
There's no indication as to the long bootup. What services?
```
systemctl list-unit-files --state=enabled --no-pager
```
Also, the output of pstree:
```
pstree
```

---

### Post by zalle1 on 2019-04-19
```
UNIT FILE                                  STATE  
acpid.path                                 enabled
apport-autoreport.path                     enabled
cups.path                                  enabled
accounts-daemon.service                    enabled
anacron.service                            enabled
apparmor.service                           enabled
autovt@.service                            enabled
avahi-daemon.service                       enabled
bluetooth.service                          enabled
console-setup.service                      enabled
cron.service                               enabled
cups-browsed.service                       enabled
cups.service                               enabled
dbus-fi.w1.wpa_supplicant1.service         enabled
dbus-org.bluez.service                     enabled
dbus-org.freedesktop.Avahi.service         enabled
dbus-org.freedesktop.ModemManager1.service enabled
dbus-org.freedesktop.nm-dispatcher.service enabled
dbus-org.freedesktop.resolve1.service      enabled
dbus-org.freedesktop.thermald.service      enabled
getty@.service                             enabled
gpu-manager.service                        enabled
irqbalance.service                         enabled
kerneloops.service                         enabled
keyboard-setup.service                     enabled
ModemManager.service                       enabled
mpd.service                                enabled
network-manager.service                    enabled
networkd-dispatcher.service                enabled
NetworkManager-dispatcher.service          enabled
NetworkManager-wait-online.service         enabled
NetworkManager.service                     enabled
ondemand.service                           enabled
pppd-dns.service                           enabled
rsync.service                              enabled
rsyslog.service                            enabled
setvtrgb.service                           enabled
snapd.autoimport.service                   enabled
snapd.core-fixup.service                   enabled                                     
snapd.seeded.service                       enabled                                     
snapd.service                              enabled                                     
snapd.system-shutdown.service              enabled                                     
spice-vdagent.service                      enabled
spice-vdagentd.service                     enabled
syslog.service                             enabled
systemd-resolved.service                   enabled
systemd-timesyncd.service                  enabled
thermald.service                           enabled
udisks2.service                            enabled
ufw.service                                enabled
unattended-upgrades.service                enabled
ureadahead.service                         enabled
whoopsie.service                           enabled
winbind.service                            enabled
wpa_supplicant.service                     enabled
acpid.socket                               enabled
apport-forward.socket                      enabled
avahi-daemon.socket                        enabled
cups.socket                                enabled
mpd.socket                                 enabled
snapd.socket                               enabled
uuidd.socket                               enabled
remote-fs.target                           enabled
anacron.timer                              enabled
apt-daily-upgrade.timer                    enabled
apt-daily.timer                            enabled
fstrim.timer                               enabled
motd-news.timer                            enabled
snapd.snap-repair.timer                    enabled

69 unit files listed.


```

---

### Post by zalle1 on 2019-04-19
```
systemd&#9472;&#9516;&#9472;ModemManager&#9472;&#9472;&#9472;2*[{ModemManager}]
        &#9500;&#9472;NetworkManager&#9472;&#9516;&#9472;dhclient
        &#9474;                &#9492;&#9472;2*[{NetworkManager}]
        &#9500;&#9472;accounts-daemon&#9472;&#9472;&#9472;2*[{accounts-daemon}]
        &#9500;&#9472;acpid
        &#9500;&#9472;at-spi-bus-laun&#9472;&#9516;&#9472;dbus-daemon
        &#9474;                 &#9492;&#9472;3*[{at-spi-bus-laun}]
        &#9500;&#9472;at-spi2-registr&#9472;&#9472;&#9472;2*[{at-spi2-registr}]
        &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
        &#9500;&#9472;baloo_file&#9472;&#9472;&#9472;{baloo_file}
        &#9500;&#9472;cron
        &#9500;&#9472;cups-browsed&#9472;&#9472;&#9472;2*[{cups-browsed}]
        &#9500;&#9472;cupsd
        &#9500;&#9472;2*[dbus-daemon]
        &#9500;&#9472;dbus-launch
        &#9500;&#9472;dconf-service&#9472;&#9472;&#9472;2*[{dconf-*********]
        &#9500;&#9472;gconfd-2
        &#9500;&#9472;irqbalance&#9472;&#9472;&#9472;{irqbalance}
        &#9500;&#9472;kactivitymanage&#9472;&#9472;&#9472;6*[{kactivitymanage}]
        &#9500;&#9472;kdeconnectd&#9472;&#9472;&#9472;3*[{kdeconnectd}]
        &#9500;&#9472;kdeinit5&#9472;&#9516;&#9472;file.so
        &#9474;          &#9500;&#9472;firefox&#9472;&#9516;&#9472;Web Content&#9472;&#9472;&#9472;17*[{Web Content}]
        &#9474;          &#9474;         &#9500;&#9472;Web Content&#9472;&#9472;&#9472;15*[{Web Content}]
        &#9474;          &#9474;         &#9500;&#9472;WebExtensions&#9472;&#9472;&#9472;16*[{WebExtensions}]
        &#9474;          &#9474;         &#9492;&#9472;51*[{firefox}]
        &#9474;          &#9500;&#9472;kaccess&#9472;&#9472;&#9472;2*[{kaccess}]
        &#9474;          &#9500;&#9472;kded5&#9472;&#9472;&#9472;7*[{kded5}]
        &#9474;          &#9500;&#9472;klauncher&#9472;&#9472;&#9472;2*[{klauncher}]
        &#9474;          &#9492;&#9472;ksmserver&#9472;&#9516;&#9472;kwin_x11&#9472;&#9472;&#9472;6*[{kwin_x11}]
        &#9474;                      &#9492;&#9472;2*[{ksmserver}]
        &#9500;&#9472;2*[kerneloops]
        &#9500;&#9472;kglobalaccel5&#9472;&#9472;&#9472;2*[{kglobalaccel5}]
        &#9500;&#9472;krunner&#9472;&#9472;&#9472;4*[{krunner}]
        &#9500;&#9472;kscreen_backend&#9472;&#9472;&#9472;2*[{kscreen_backend}]
        &#9500;&#9472;kuiserver5&#9472;&#9472;&#9472;2*[{kuiserver5}]
        &#9500;&#9472;kwalletd5&#9472;&#9472;&#9472;3*[{kwalletd5}]
        &#9500;&#9472;mount.ntfs
        &#9500;&#9472;mpd&#9472;&#9472;&#9472;4*[{mpd}]
        &#9500;&#9472;networkd-dispat&#9472;&#9472;&#9472;{networkd-dispat}
        &#9500;&#9472;obexd
        &#9500;&#9472;org_kde_powerde&#9472;&#9472;&#9472;4*[{org_kde_powerde}]
        &#9500;&#9472;packagekitd&#9472;&#9472;&#9472;2*[{packagekitd}]
        &#9500;&#9472;plasmashell&#9472;&#9516;&#9472;konsole&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
        &#9474;             &#9474;         &#9492;&#9472;3*[{konsole}]
        &#9474;             &#9500;&#9472;ksysguardd
        &#9474;             &#9492;&#9472;9*[{plasmashell}]
        &#9500;&#9472;polkit-kde-auth&#9472;&#9472;&#9472;4*[{polkit-kde-auth}]
        &#9500;&#9472;polkitd&#9472;&#9472;&#9472;2*[{polkitd}]
        &#9500;&#9472;preload
        &#9500;&#9472;pulseaudio&#9472;&#9516;&#9472;gconf-helper
        &#9474;            &#9492;&#9472;2*[{pulseaudio}]
        &#9500;&#9472;rsyslogd&#9472;&#9472;&#9472;3*[{rsyslogd}]
        &#9500;&#9472;rtkit-daemon&#9472;&#9472;&#9472;2*[{rtkit-daemon}]
        &#9500;&#9472;sddm&#9472;&#9516;&#9472;Xorg&#9472;&#9472;&#9472;3*[{Xorg}]
        &#9474;      &#9500;&#9472;sddm-helper&#9472;&#9472;&#9472;startkde&#9472;&#9516;&#9472;kwrapper5
        &#9474;      &#9474;                        &#9492;&#9472;ssh-agent
        &#9474;      &#9492;&#9472;{sddm}
        &#9500;&#9472;start_kdeinit
        &#9500;&#9472;systemd&#9472;&#9472;&#9472;(sd-pam)
        &#9500;&#9472;systemd-journal
        &#9500;&#9472;systemd-logind
        &#9500;&#9472;systemd-resolve
        &#9500;&#9472;systemd-timesyn&#9472;&#9472;&#9472;{systemd-timesyn}
        &#9500;&#9472;systemd-udevd
        &#9500;&#9472;udisksd&#9472;&#9472;&#9472;4*[{udisksd}]
        &#9500;&#9472;unattended-upgr&#9472;&#9472;&#9472;{unattended-upgr}
        &#9500;&#9472;update-apt-xapi&#9472;&#9472;&#9472;{update-apt-xapi}
        &#9500;&#9472;upowerd&#9472;&#9472;&#9472;2*[{upowerd}]
        &#9500;&#9472;whoopsie&#9472;&#9472;&#9472;2*[{whoopsie}]
        &#9500;&#9472;winbindd&#9472;&#9472;&#9472;winbindd
        &#9500;&#9472;wpa_supplicant
        &#9492;&#9472;xembedsniproxy&#9472;&#9472;&#9472;2*[{xembedsniproxy}]


```

---

### Post by VMC on 2019-04-19
I'm unsure about SSD drives. Maybe trim or something else, I don't have a SSD. Regarding long shutdown, and can try this and see if it helps.
```
sudo sed -i 's/\#DefaultTimeoutStartSec=90s/DefaultTimeoutStartSec=10s/' /etc/systemd/system.conf

sudo sed -i 's/\#DefaultTimeoutStopSec=90s/DefaultTimeoutStopSec=10s/' /etc/systemd/system.conf
```

---

### Post by zalle1 on 2019-04-20
Hi, thanks for your answer, it seems slightly faster... But still very slow.

It takes around one minute to show the Kubuntu logo, another minute to show the 4 lines of errors I mentioned above, at around 2m45s I can see and move the cursor, one minute later (3m45s) I log-in.

---

### Post by VMC on 2019-04-20
On that second error, look here:
[https://askubuntu.com/questions/893817/boot-very-slow-because-of-drm-kms-helper-errors](https://askubuntu.com/questions/893817/boot-very-slow-because-of-drm-kms-helper-errors)

---

