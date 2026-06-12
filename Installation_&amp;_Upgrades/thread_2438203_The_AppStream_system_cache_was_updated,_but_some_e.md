---
title: "The AppStream system cache was updated, but some errors were detected, Ubuntu 18.04"
date: 2020-03-07
forum: Installation &amp; Upgrades
---

### Post by baaridun on 2020-03-07
Hello,

Recently installed Ubuntu 18.04. I added some repos from Elementary OS as I enjoy their apps a lot. I keep getting this error whenever I do an apt update. Not sure why and what the fix is...

The AppStream system cache was updated, but some errors were detected, which might lead to missing metadata. Refer to the verbose log for more information.
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh-cache > /dev/null; fi'
E: Sub-process returned an error code

Googling suggested to refresh the cache forcefully via appstreamcli but that had no luck. Here is the verbose log of "sudo appstreamcli refresh-cache --force --verbose". It seems like something is misconfigured and I dont know why.

```
** (appstreamcli:3173): DEBUG: 17:24:07.578: Added /usr/share/app-info/xmls to XML metadata search path.
** (appstreamcli:3173): DEBUG: 17:24:07.578: Added /usr/share/app-info/yaml to YAML metadata search path.
** (appstreamcli:3173): DEBUG: 17:24:07.578: Added /var/lib/app-info/yaml to YAML metadata search path.
** (appstreamcli:3173): DEBUG: 17:24:07.578: Added /var/cache/app-info/xmls to XML metadata search path.
** (appstreamcli:3173): DEBUG: 17:24:08.014: Refreshing AppStream cache
** (appstreamcli:3173): DEBUG: 17:24:08.014: Searching for data in: /usr/share/app-info/xmls
** (appstreamcli:3173): DEBUG: 17:24:08.014: Searching for data in: /var/cache/app-info/xmls
** (appstreamcli:3173): DEBUG: 17:24:08.014: Searching for data in: /usr/share/app-info/yaml
** (appstreamcli:3173): DEBUG: 17:24:08.014: Searching for data in: /var/lib/app-info/yaml
** (appstreamcli:3173): DEBUG: 17:24:08.014: Reading: /usr/share/app-info/xmls/org.gnome.Software.Featured.xml
** (appstreamcli:3173): DEBUG: 17:24:08.015: Reading: /usr/share/app-info/yaml/pantheon_bionic-extra_amd64.yml.gz
** (appstreamcli:3173): DEBUG: 17:24:08.015: Reading: /usr/share/app-info/yaml/pantheon_bionic-main_amd64.yml.gz
** (appstreamcli:3173): DEBUG: 17:24:08.042: Reading: /var/lib/app-info/yaml/packages.elementary.io_appcenter_dists_bionic_main_dep11_Components-amd64.yml.gz
** (appstreamcli:3173): DEBUG: 17:24:08.096: Reading: /var/lib/app-info/yaml/security.ubuntu.com_ubuntu_dists_bionic-security_main_dep11_Components-amd64.yml.gz
** (appstreamcli:3173): DEBUG: 17:24:08.102: Reading: /var/lib/app-info/yaml/in.archive.ubuntu.com_ubuntu_dists_bionic_main_dep11_Components-amd64.yml.gz
** (appstreamcli:3173): DEBUG: 17:24:08.173: Reading: /var/lib/app-info/yaml/in.archive.ubuntu.com_ubuntu_dists_bionic_universe_dep11_Components-amd64.yml.gz
** (appstreamcli:3173): DEBUG: 17:24:08.729: Reading: /var/lib/app-info/yaml/in.archive.ubuntu.com_ubuntu_dists_bionic_multiverse_dep11_Components-amd64.yml.gz
** (appstreamcli:3173): DEBUG: 17:24:08.736: Reading: /var/lib/app-info/yaml/in.archive.ubuntu.com_ubuntu_dists_bionic-updates_main_dep11_Components-amd64.yml.gz
** (appstreamcli:3173): DEBUG: 17:24:08.782: Reading: /var/lib/app-info/yaml/in.archive.ubuntu.com_ubuntu_dists_bionic-updates_universe_dep11_Components-amd64.yml.gz
** (appstreamcli:3173): DEBUG: 17:24:08.827: Reading: /var/lib/app-info/yaml/security.ubuntu.com_ubuntu_dists_bionic-security_universe_dep11_Components-amd64.yml.gz
** (appstreamcli:3173): DEBUG: 17:24:08.834: Reading: /var/lib/app-info/yaml/in.archive.ubuntu.com_ubuntu_dists_bionic-updates_multiverse_dep11_Components-amd64.yml.gz
** (appstreamcli:3173): DEBUG: 17:24:08.835: Reading: /var/lib/app-info/yaml/in.archive.ubuntu.com_ubuntu_dists_bionic-backports_universe_dep11_Components-amd64.yml.gz
** (appstreamcli:3173): DEBUG: 17:24:08.835: Reading: /var/lib/app-info/yaml/security.ubuntu.com_ubuntu_dists_bionic-security_multiverse_dep11_Components-amd64.yml.gz
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/gstreamer1.0-plugins-good was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/gstreamer1.0-x was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/libreoffice-draw.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/gstreamer1.0-alsa was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/libreoffice-math.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/gstreamer1.0-plugins-base was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/usb-creator-gtk.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/evince.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/gstreamer1.0-pulseaudio was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/org.gnome.FileRoller was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/gstreamer1.0-gl was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/ibus-setup.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/libreoffice-impress.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/gvim.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/vim.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/libreoffice-calc.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.836: Metadata ignored: Detected colliding ids: system/os/package/libreoffice-writer.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.837: Metadata ignored: Detected colliding ids: system/os/package/gstreamer1.0-gtk3 was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.838: Metadata ignored: Detected colliding ids: system/os/package/plank.desktop was already added with the same priority.
** (appstreamcli:3173): DEBUG: 17:24:08.838: Replaced 'system/os/package/org.gnome.Software.Plugin.Snap' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.838: Replaced 'system/os/package/nm-connection-editor.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.838: Metadata ignored: Detected colliding ids: system/os/package/gstreamer1.0-plugins-good was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.838: Metadata ignored: Detected colliding ids: system/os/package/gstreamer1.0-x was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.838: Replaced 'system/os/package/org.gnome.Nautilus.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.838: Metadata ignored: Detected colliding ids: system/os/package/libreoffice-draw.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.838: Replaced 'system/os/package/org.gnome.gedit.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.838: Replaced 'system/os/package/gnome-system-monitor.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.838: Replaced 'system/os/package/gnome-system-monitor-kde.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.838: Metadata ignored: Detected colliding ids: system/os/package/libreoffice-math.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.838: Metadata ignored: Detected colliding ids: system/os/package/gstreamer1.0-alsa was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.838: Replaced 'system/os/package/gparted.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Metadata ignored: Detected colliding ids: system/os/package/gstreamer1.0-plugins-base was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.gnome.Calendar.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Metadata ignored: Detected colliding ids: system/os/package/usb-creator-gtk.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Metadata ignored: Detected colliding ids: system/os/package/gstreamer1.0-gtk3 was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/software-properties-gtk.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/nvidia-settings.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Metadata ignored: Detected colliding ids: system/os/package/evince.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.gnome.Totem.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.gnome.Software.Plugin.Epiphany' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.gnome.Software.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.gnome.Software.Plugin.Fwupd' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.gnome.Software.Plugin.Odrs' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.gnome.Software.Plugin.Steam' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.gnome.DejaDup.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/gnome-session-properties.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Metadata ignored: Detected colliding ids: system/os/package/gstreamer1.0-pulseaudio was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.gnome.Terminal.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.gnome.DiskUtility.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Metadata ignored: Detected colliding ids: system/os/package/gstreamer1.0-gl was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/shotwell.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.freedesktop.appstream.cli' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/gnome-language-selector.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Metadata ignored: Detected colliding ids: system/os/package/org.gnome.FileRoller was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.gnome.Characters.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/gnome-control-center.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.gnome.Calculator.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/ubiquity.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Metadata ignored: Detected colliding ids: system/os/package/ibus-setup.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Metadata ignored: Detected colliding ids: system/os/package/libreoffice-impress.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/im-config.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/update-manager.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Metadata ignored: Detected colliding ids: system/os/package/vim.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/gnome-mines.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/libpinyin.xml' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Metadata ignored: Detected colliding ids: system/os/package/gvim.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Metadata ignored: Detected colliding ids: system/os/package/libreoffice-calc.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.freedesktop.fwupd' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.a11y.brltty' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.gnome.Terminal.Nautilus' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Metadata ignored: Detected colliding ids: system/os/package/libreoffice-writer.desktop was already added with a higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/xfce-workspaces-settings.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/xfce-wmtweaks-settings.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/xfce-wm-settings.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/sweethome3d.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/gnome-split.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.comic' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.userswitcher' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.activitypager' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.notes' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.weather' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.quickshare' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma_applet_dict' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.colorpicker' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.mediaframe' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.binaryclock' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.fuzzyclock' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.kickerdash' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.fifteenpuzzle' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.showdesktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.minimizeall' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.calculator' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.webbrowser' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/de.linrunner.tlp' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/gstreamer1.0-plugins-ugly' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/geogebra.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/wesnoth-1.12.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/wesnoth-1.12_editor.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/org.kde.plasma.konsoleprofiles' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/libreoffice-base.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.839: Replaced 'system/os/package/budgie-plank-prefs.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/wpa_gui.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/wireshark-gtk.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/xfce4-mime-settings.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/xfce-settings-manager.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/xfce-mouse-settings.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/xfce-keyboard-settings.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/xfce4-accessibility-settings.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/xfce-display-settings.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/xfce4-settings-editor.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/xfce-ui-settings.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/evolution-pst' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/ufraw.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.milou' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/network-manager-vpnc' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/com.twilightedge.PikoPixel' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/boinc-manager.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/scilab-cli.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.kinfocenter' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasma.desktop.emptyPanel' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasma.kickoff' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasma.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.desktoptoolbox' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasmashell' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasma.taskmanager' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasma.icontasks' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasma.windowlist' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasma.folder' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasma.pager' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasma.kicker' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasma.desktop.appmenubar' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasma.desktop.defaultPanel' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.paneltoolbox' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasma.trash' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.desktopcontainment' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/jabref.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/nestopia.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasma.themeexplorer' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.cuttlefish.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasma.lookandfeelexplorer' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasmoidviewershell' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.kde.plasma.cuttlefish' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/evolution-bogofilter' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/exo-web-browser.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/exo-mail-reader.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/exo-terminal-emulator.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/exo-file-manager.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/exo-preferred-applications.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/sigil.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/libretro-nestopia' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/ggcov.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/visualvm.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/org.gnome.Epiphany.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.840: Replaced 'system/os/package/wireshark.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/network-manager-fortisslvpn' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.gnome.Software.Plugin.Flatpak' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/com.vinszent.GnomeTwitch.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/bvnc.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/bssh.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/itweb-settings.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.volume' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/pdfsam.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/usb-creator-kde.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/evolution-ews' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/blender.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/SciTE.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.breezedark.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/modem-manager-gui.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/gstreamer1.0-libav' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/jftp.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.gnome.Software.Plugin.Limba' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.hunyango' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.haenau' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.potd' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/gstreamer1.0-opencv' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/evolution-spamassassin' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.systemtray' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.systemmonitor.net' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.image' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.calendar' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.color' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.analogclock' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.clipboard' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.digitalclock' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.systemmonitor.cpu' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.lock_logout' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.slideshow' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.systemmonitor.memory' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.activitybar' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.notifications' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.breeze.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.systemmonitor.diskactivity' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.systemmonitor.diskusage' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.klipper' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.devicenotifier' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.mediacontroller' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.battery' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/chromium-browser.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.discover.flatpak' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/systemsettings.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/kdesystemsettings.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/virt-manager.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/lyx.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/sylpheed.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.plasma.bluetooth' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.kde.ksysguard' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/org.gnome.Evolution.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.841: Replaced 'system/os/package/freedink-dfarc.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/org.gnome.Geary.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/gstreamer1.0-qt5' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/gstreamer1.0-plugins-bad' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/hedgewars.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/xfce4-terminal.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/avahi-discover.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/openjdk-8-policytool.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/org.kde.plasma.vault' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/org.videolan.vlc' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/org.kde.kdeconnect.nonplasma' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/org.kde.kdeconnect.kcm.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/org.libreoffice.kde' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/org.kde.discover.snap' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/lshw-gtk.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/org.kde.discover.packagekit' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/org.kde.discover.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/cmake-gui.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/scilab.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/scilab-adv-cli.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/ubiquity-kdeui.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/org.kde.plasma.networkmanagement' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/budgie-desktop-settings.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/lubuntu-nexus7-identica.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/netbeans.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/usb-creator-kde.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/geogebra.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/wesnoth-1.12.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/wesnoth-1.12_editor.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/libreoffice-base.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/sweethome3d.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/wpa_gui.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/wireshark-gtk.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/ufraw.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/jftp.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/network-manager-vpnc' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/sigil.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/scilab-cli.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/chromium-browser.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/jabref.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/freedink-dfarc.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/gstreamer1.0-qt5' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/openjdk-8-policytool.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/ggcov.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/avahi-discover.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/visualvm.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/wireshark.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/org.videolan.vlc' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/org.libreoffice.kde' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/pdfsam.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/scilab-adv-cli.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/scilab.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/netbeans.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.842: Replaced 'system/os/package/itweb-settings.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.843: Replaced 'system/os/package/bvnc.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.843: Replaced 'system/os/package/bssh.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.843: Replaced 'system/os/package/virtualbox.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.843: Replaced 'system/os/package/virtualbox.desktop' with data of higher priority.
** (appstreamcli:3173): DEBUG: 17:24:08.843: Merged data for 'system/os/package/blender.desktop'
** (appstreamcli:3173): DEBUG: 17:24:08.843: Merged data for 'system/os/package/gimp.desktop'
** (appstreamcli:3173): DEBUG: 17:24:08.843: Merged data for 'system/os/package/gnome-chess.desktop'
** (appstreamcli:3173): DEBUG: 17:24:08.843: Merged data for 'system/os/package/inkscape.desktop'
** (appstreamcli:3173): DEBUG: 17:24:08.843: Merged data for 'system/os/package/mypaint.desktop'
** (appstreamcli:3173): DEBUG: 17:24:08.844: Merged data for 'system/os/package/org.gnome.Builder.desktop'
** (appstreamcli:3173): DEBUG: 17:24:08.844: Merged data for 'system/os/package/org.gnome.Maps.desktop'
** (appstreamcli:3173): DEBUG: 17:24:08.844: Merged data for 'system/os/package/org.gnome.Polari.desktop'
** (appstreamcli:3173): DEBUG: 17:24:08.844: Merged data for 'system/os/package/org.gnome.Weather.Application.desktop'
** (appstreamcli:3173): DEBUG: 17:24:08.844: Merged data for 'system/os/package/transmission-gtk.desktop'
** (appstreamcli:3173): DEBUG: 17:24:08.852: system/os/package/org.kde.latte.shell extends system/os/package/latte-dock, but system/os/package/latte-dock was not found.
** (appstreamcli:3173): DEBUG: 17:24:08.852: system/os/package/com.github.leoiannacone.goopg extends system/os/package/google-chrome.desktop, but system/os/package/google-chrome.desktop was not found.
** (appstreamcli:3173): DEBUG: 17:24:08.858: system/os/package/nemo-gtkhash extends system/os/package/org.Nemo.desktop, but system/os/package/org.Nemo.desktop was not found.
** (appstreamcli:3173): DEBUG: 17:24:08.863: system/os/package/caja-gtkhash extends system/os/package/caja.desktop, but system/os/package/caja.desktop was not found.
** (appstreamcli:3173): DEBUG: 17:24:08.864: system/os/package/nautilus-sendto extends system/os/package/nautilus.desktop, but system/os/package/nautilus.desktop was not found.
** (appstreamcli:3173): DEBUG: 17:24:08.865: system/os/package/zathura-pdf-poppler.desktop extends system/os/package/zathura.desktop, but system/os/package/zathura.desktop was not found.
** (appstreamcli:3173): DEBUG: 17:24:08.866: system/os/package/evolution-rss extends system/os/package/evolution.desktop, but system/os/package/evolution.desktop was not found.
** (appstreamcli:3173): DEBUG: 17:24:08.876: WARNING: Ignored component 'io.elementary.icons': The component is invalid.
** (appstreamcli:3173): DEBUG: 17:24:08.879: Stemming language is: en
** (appstreamcli:3173): DEBUG: 17:24:08.921: Skipping 'ardour5.desktop' from cache inclusion, it is a merge component.
** (appstreamcli:3173): DEBUG: 17:24:09.264: Skipping 'firefox.desktop' from cache inclusion, it is a merge component.
The AppStream system cache was updated, but some errors were detected, which might lead to missing metadata. Refer to the verbose log for more information.
```

---

