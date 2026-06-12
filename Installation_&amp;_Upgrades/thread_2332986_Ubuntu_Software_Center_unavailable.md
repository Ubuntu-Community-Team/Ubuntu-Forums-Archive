---
title: "Ubuntu Software Center unavailable"
date: 2016-08-06
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2016-08-06
Problem:    My Ubuntu Software Center won't open.  

This began right after I installed GNU IceCat (v. 31.8.0).
 Invoking the command software-center on the terminal's command-line returns the following:
```
/usr/bin/software-center:25: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GObject
/usr/share/software-center/softwarecenter/ui/gtk3/views/purchaseview.py:29: PyGIWarning: WebKit2 was imported without specifying a version first. Use gi.require_version('WebKit2', '4.0') before import to ensure that the right version gets loaded.
  from gi.repository import WebKit2 as webkit
2016-08-06 00:57:31,660 - softwarecenter.backend.zeitgeist_logger - WARNING - Support for Zeitgeist disabled
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/symbolic_icons.py:23: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GLib, PangoCairo
2016-08-06 00:57:31,696 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 301, in __init__
    self.db.open(use_axi=self._use_axi)
  File "/usr/share/software-center/softwarecenter/db/database.py", line 243, in open
    self._axi_values = parse_axi_values_file()
  File "/usr/share/software-center/softwarecenter/db/database.py", line 63, in parse_axi_values_file
    for raw_line in open(filename):
IOError: [Errno 13] Permission denied: '/var/lib/apt-xapian-index/values'
```
Also:
--> sudo update-apt-xapian-index -vf 

returns:
```
Reading plugin /usr/share/apt-xapian-index/plugins/aliases.py.
Reading plugin /usr/share/apt-xapian-index/plugins/app-install.py.
Reading plugin /usr/share/apt-xapian-index/plugins/apttags.py.
Reading plugin /usr/share/apt-xapian-index/plugins/cataloged_time.py.
Reading plugin /usr/share/apt-xapian-index/plugins/debtags.py.
Reading plugin /usr/share/apt-xapian-index/plugins/descriptions.py.
Reading plugin /usr/share/apt-xapian-index/plugins/display_name.py.
Reading plugin /usr/share/apt-xapian-index/plugins/origin.py.
Reading plugin /usr/share/apt-xapian-index/plugins/relations.py.
Reading plugin /usr/share/apt-xapian-index/plugins/sections.py.
Reading plugin /usr/share/apt-xapian-index/plugins/sizes.py.
Reading plugin /usr/share/apt-xapian-index/plugins/software_center.py.
Reading plugin /usr/share/apt-xapian-index/plugins/template.py.
Reading plugin /usr/share/apt-xapian-index/plugins/translated-desc.py.
Most recent dataset:    Sat Aug  6 00:27:20 2016.
Most recent update for: Sat Aug  6 00:27:20 2016.
The index /var/lib/apt-xapian-index is up to date, but rebuilding anyway as requested.
Aggregating value information.
Initializing plugins.
Reading .desktop files from /usr/share/app-install/desktop/: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_gezakovacs_ppa_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_mc3man_mpv-tests_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_xenial_universe_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_mc3man_xerus-media_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_atareao_atareao_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_rvm_smplayer_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_xenial-updates_universe_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_teejee2008_ppa_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_ubuntuhandbook1_cantata-qt_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_ubuntu-mate-dev_xenial-mate_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_xenial-security_multiverse_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_peterlevi_ppa_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_videolan_stable-daily_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_gedit-bc-dev-plugins_releases_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_xenial_multiverse_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_jeffreyratcliffe_ppa_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_atareao_nautilus-extensions_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_remmina-ppa-team_remmina-next_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_xenial_partner_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_atareao_utext_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_xenial-updates_multiverse_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_ubuntu-mate-dev_mate-desktop_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_xenial-backports_universe_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_xenial-security_universe_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_webupd8team_tor-browser_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_futurepilot_ppa_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_xenial_restricted_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_ubuntu-mate-dev_welcome_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_andreas-boettger_gmusicbrowser-daily_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_pi-rho_dev_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_bkgaley_ppa_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_atareao_antiviral_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_jtaylor_keepass_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_graphics-drivers_ppa_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_system76-dev_stable_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_jfi_ppa_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_wireshark-dev_stable_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_micahflee_ppa_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Reading en translations from /var/lib/apt/lists/ppa.launchpad.net_pi-rho_security_ubuntu_dists_xenial_main_i18n_Translation-en: done.  
Rebuilding Xapian index: done.  
Installing the new index.
Removing old index /var/cache/apt-xapian-index/index.1.
Writing value information to /var/lib/apt-xapian-index/values.
Writing prefix information to /var/lib/apt-xapian-index/prefixes.
Writing documentation to /var/lib/apt-xapian-index/README.
sudo update-apt-xapian-index -vf  63.62s user 5.34s system 99% cpu 1:09.55 total
```
Also:
  After installing IceCat, /etc/lsb-release was:
  ```

DISTRIB_ID=Trisquel
DISTRIB_RELEASE=6.0.1
DISTRIB_CODENAME=toutatis
DISTRIB_DESCRIPTION="Trisquel GNU/Linux 6.0.1, Toutatis"
```  
I manually changed it (back) to:
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04 LTS"
```  
And I'm not sure that manually changing that is the right  thing to do. 

I think I may have accidentally installed Trisquel without  meaning to, when I installed IceCat.  My distro is Ubuntu Mate 16.04.

QUESTION: How can I get the Software Center to open?

---

### Post by Bucky Ball on 2016-08-06
What errors do you get with a straight forward update/upgrade in a terminal?

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

Suggest you remove whatever you installed prior to this happening then run these commands.

---

### Post by watchpocket on 2016-08-06
Thanks for the response.  I get no errors at all with any of those three commands.  
When I try to open Software Center, it tries to start, but never opens.


By the way, is there any difference at all between those commands and the same commands only using "apt-get" instead of "apt"?

---

### Post by Bucky Ball on 2016-08-06
> **watchpocket said:**
> By the way, is there any difference at all between those commands and the same commands only using "apt-get" instead of "apt"?

[Try this.]("https://www.maketecheasier.com/apt-vs-apt-get-ubuntu/")

---

### Post by watchpocket on 2016-08-27
Thank you! That definitely answers the question.  Had no idea that "apt" has been around since 14.04.  Meanwhile my Software Center mysteriously still doesn't open.  (I'm just glad it's not my only means of getting sw.)

---

