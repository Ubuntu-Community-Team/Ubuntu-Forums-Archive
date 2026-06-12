---
title: "Fedora 7 -&gt; Kubuntu 8.04 fails"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by howei on 2008-04-28
What is the best way to install Kubuntu 8.04 if there is already Fedora 7 installed? At the end of this message you can find my /etc/fstab file

while installing after selecting the language (step3) this message appears:

**Partman failed with exit code 10. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken.**

here is the 'important' part of the /var/log/syslog:

Apr 28 18:16:31 ubuntu ubiquity: Cannot unlink input FIFO: No such file or directory
Apr 28 18:16:31 ubuntu ubiquity: Cannot unlink output FIFO: No such file or directory
Apr 28 18:16:31 ubuntu ubiquity: Cannot unlink stop FIFO: No such file or directory
Apr 28 18:16:31 ubuntu ubiquity: /lib/partman/automatically_partition/10resize_use_free/choices: 204:
Apr 28 18:16:31 ubuntu ubiquity: cannot create /var/lib/partman/stopfifo: Directory nonexistent
Apr 28 18:16:31 ubuntu ubiquity:
Apr 28 18:16:31 ubuntu ubiquity: /lib/partman/display.d/10initial_auto: 134: cannot create /var/lib/partman/snoop
: Directory nonexistent
Apr 28 18:16:31 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:31 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:31 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:31 ubuntu ubiquity:
Apr 28 18:16:31 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:31 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:31 ubuntu ubiquity:
Apr 28 18:16:32 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:32 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:32 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:32 ubuntu ubiquity:
Apr 28 18:16:32 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:32 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:32 ubuntu ubiquity:
Apr 28 18:16:32 ubuntu localechooser: info: LANGNAME=German
Apr 28 18:16:32 ubuntu localechooser: info: line=German;1;de;DE;de_DE.UTF-8;UTF-8;;kbd=lat0-sun16(utf8)
Apr 28 18:16:32 ubuntu localechooser: info: Set debian-installer/language = 'de'
Apr 28 18:16:32 ubuntu localechooser: info: Set debian-installer/locale = 'de_DE.UTF-8'
Apr 28 18:16:32 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'de_DE.UTF-8'
Apr 28 18:16:32 ubuntu localechooser: info: Set debian-installer/country = 'DE'
Apr 28 18:16:32 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'kbd=lat0-sun16(utf8)'
Apr 28 18:16:32 ubuntu localechooser: info: Set debconf/language = 'de'
Apr 28 18:16:32 ubuntu localechooser: info: Set debian-installer/country = 'DE'
Apr 28 18:16:32 ubuntu localechooser: info: Set debian-installer/locale = 'de_DE.UTF-8'
Apr 28 18:16:32 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:32 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:32 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:32 ubuntu ubiquity:
Apr 28 18:16:32 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:32 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:32 ubuntu ubiquity:
Apr 28 18:16:32 ubuntu ubiquity[10799]: debconffilter_done: Language (current: Language)
Apr 28 18:16:32 ubuntu ubiquity[10799]: Step_before = stepLanguage
Apr 28 18:16:32 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:33 ubuntu last message repeated 3 times
Apr 28 18:16:33 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:33 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:33 ubuntu ubiquity:
Apr 28 18:16:33 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:33 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:33 ubuntu ubiquity:
Apr 28 18:16:33 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:33 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:33 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:33 ubuntu ubiquity:
Apr 28 18:16:33 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:33 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:33 ubuntu ubiquity:
Apr 28 18:16:34 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:34 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:34 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:34 ubuntu ubiquity:
Apr 28 18:16:34 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:34 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:34 ubuntu ubiquity:
Apr 28 18:16:34 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:34 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:34 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:34 ubuntu ubiquity:
Apr 28 18:16:34 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:34 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:34 ubuntu ubiquity:
Apr 28 18:16:34 ubuntu ubiquity[10799]: switched to page stepLocation
Apr 28 18:16:35 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:35 ubuntu last message repeated 4 times
Apr 28 18:16:35 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:35 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:35 ubuntu ubiquity:
Apr 28 18:16:35 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:35 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:35 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:35 ubuntu ubiquity:
Apr 28 18:16:35 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:35 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:35 ubuntu ubiquity:
Apr 28 18:16:36 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:36 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:36 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:36 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:36 ubuntu ubiquity:
Apr 28 18:16:36 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:36 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:36 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:36 ubuntu ubiquity:
Apr 28 18:16:36 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:36 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:36 ubuntu ubiquity:
Apr 28 18:16:37 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:37 ubuntu last message repeated 7 times
Apr 28 18:16:37 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:37 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:37 ubuntu ubiquity:
Apr 28 18:16:37 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:37 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:37 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:37 ubuntu ubiquity:
Apr 28 18:16:37 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:38 ubuntu last message repeated 2 times
Apr 28 18:16:38 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:38 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:38 ubuntu ubiquity:
Apr 28 18:16:38 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:39 ubuntu last message repeated 4 times
Apr 28 18:16:39 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:39 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:39 ubuntu ubiquity:
Apr 28 18:16:39 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:39 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:39 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:39 ubuntu ubiquity:
Apr 28 18:16:39 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:39 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:39 ubuntu ubiquity:
Apr 28 18:16:39 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:39 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:39 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:39 ubuntu ubiquity:
Apr 28 18:16:39 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:39 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:39 ubuntu ubiquity:
Apr 28 18:16:40 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:40 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:40 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:40 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:40 ubuntu ubiquity:
Apr 28 18:16:40 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:40 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:40 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:40 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:40 ubuntu ubiquity:
Apr 28 18:16:41 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:41 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:41 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:41 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:41 ubuntu ubiquity:
Apr 28 18:16:41 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:41 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:41 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:41 ubuntu ubiquity:
Apr 28 18:16:41 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:41 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:41 ubuntu ubiquity:
Apr 28 18:16:42 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:42 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:42 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:42 ubuntu ubiquity:
Apr 28 18:16:42 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:42 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:42 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:42 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:42 ubuntu ubiquity:
Apr 28 18:16:42 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:42 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:43 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:43 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:43 ubuntu ubiquity:
Apr 28 18:16:43 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:43 ubuntu localechooser: info: Locale has been preseeded to de_DE.UTF-8
Apr 28 18:16:43 ubuntu localechooser: info: Set languagechooser/language-name-fb = 'German'
Apr 28 18:16:43 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:43 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:43 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:43 ubuntu ubiquity:
Apr 28 18:16:43 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:43 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:43 ubuntu ubiquity:
Apr 28 18:16:43 ubuntu localechooser: info: Set countrychooser/shortlist-de = 'DE'
Apr 28 18:16:43 ubuntu localechooser: info: Set debian-installer/locale = 'de_DE.UTF-8'
Apr 28 18:16:43 ubuntu localechooser: info: Set debconf/language = ''
Apr 28 18:16:43 ubuntu localechooser: info: Set countrychooser/country-name = 'Germany'
Apr 28 18:16:43 ubuntu localechooser: info: Set debian-installer/country = 'DE'
Apr 28 18:16:43 ubuntu localechooser: info: Set debian-installer/locale = 'de_DE.UTF-8'
Apr 28 18:16:43 ubuntu ubiquity[10799]: debconffilter_done: Timezone (current: Timezone)
Apr 28 18:16:43 ubuntu ubiquity[10799]: Step_before = stepLocation
Apr 28 18:16:43 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:43 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:43 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:43 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:43 ubuntu ubiquity:
Apr 28 18:16:44 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:44 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:44 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:44 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:44 ubuntu ubiquity:
Apr 28 18:16:44 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:44 ubuntu last message repeated 7 times
Apr 28 18:16:44 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:44 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:44 ubuntu ubiquity:
Apr 28 18:16:44 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:44 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:44 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:44 ubuntu ubiquity:
Apr 28 18:16:44 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:44 ubuntu ubiquity[10799]: log-output -t ubiquity setxkbmap -model pc105 -layout de
Apr 28 18:16:44 ubuntu ubiquity[10799]: switched to page stepKeyboardConf
Apr 28 18:16:45 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:45 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:45 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:45 ubuntu ubiquity:
Apr 28 18:16:45 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:45 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:45 ubuntu ubiquity:
Apr 28 18:16:45 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:46 ubuntu last message repeated 4 times
Apr 28 18:16:46 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:46 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:46 ubuntu ubiquity:
Apr 28 18:16:46 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:46 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:46 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:46 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:46 ubuntu ubiquity:
Apr 28 18:16:46 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:47 ubuntu last message repeated 3 times
Apr 28 18:16:47 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:47 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:47 ubuntu ubiquity:
Apr 28 18:16:47 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:47 ubuntu last message repeated 10 times
Apr 28 18:16:47 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:47 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:47 ubuntu ubiquity:
Apr 28 18:16:47 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:47 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:47 ubuntu ubiquity:
Apr 28 18:16:47 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Apr 28 18:16:47 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Apr 28 18:16:47 ubuntu ubiquity[10799]: log-output -t ubiquity setxkbmap -model pc105 -layout de -option
Apr 28 18:16:47 ubuntu ubiquity[10799]: debconffilter_done: ConsoleSetup (current: ConsoleSetup)
Apr 28 18:16:47 ubuntu ubiquity[10799]: Step_before = stepKeyboardConf
Apr 28 18:16:48 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:48 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:48 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:48 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent
Apr 28 18:16:48 ubuntu ubiquity:
Apr 28 18:16:48 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9: cannot create /var/lib/partman/
snoop: Directory nonexistent
Apr 28 18:16:48 ubuntu ubiquity: /lib/partman/display.d/80manual_partitioning: 9:
Apr 28 18:16:48 ubuntu ubiquity: cannot create /var/lib/partman/snoop: Directory nonexistent

[B]
my Fedora /etc/fstab file looks like this[/B]

/dev/VolGroup00/LogVol00 /                       ext3    defaults        1 1
LABEL=/boot             /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sda1               /windows/C              vfat    users,gid=users,umask=0002,iocharset=utf8 0 0
/dev/sda7               /windows/F              vfat    users,gid=users,umask=0002,iocharset=utf8 0 0
/dev/sda8               /windows/G              vfat    users,gid=users,umask=0002,iocharset=utf8 0 0
/dev/sda9               /windows/I              vfat    users,gid=users,umask=0002,iocharset=utf8 0 0
/dev/VolGroup00/LogVol01 swap                    swap    defaults        0 0

---

### Post by debjit_bis08 on 2008-04-28
If u don't want to stay with Fedora best would be remove it do a fresh installation of Ubuntu

---

### Post by debjit_bis08 on 2008-04-28
If u don't want to stay with Fedora best would be remove it and do a fresh installation of Ubuntu

---

### Post by Slim Odds on 2008-04-28
howei, are you thinking that there is some sort of "upgrade" path from Fedora to Ubuntu?

There isn't.

They are not in any way related (expect that they are both linux).

---

### Post by howei on 2008-04-28
Thank you!
This is what I was thinking about, too. But how do I remove the Fedora partition in a clean way??

With Ubuntu live CD booted I see only the ubuntu file system.
Is there an option removing/replacing the Fedora ext3 partitions. 
Is it possible to remove the partition within Fedora????:confused:

Sure! There is no update from Fedora to Ubuntu.
But when I switched from SuSE to Fedora some years ago the old (SuSE) partitions were detected and listed and I could repartionate the hard disk for the new installation. 
In this installation the installation just gets stuck - with no message at all.
When I switch to live CD, then start the installation the listed message appears.

Thank you for any further help
HoWei

---

