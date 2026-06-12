---
title: "Install Error - Partman failed"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by Tauhshi on 2007-04-30
While installing Ubuntu Feisty, I encountered this error.
[[IMG]http://img254.imageshack.us/img254/269/screenshotyq6.th.png[/IMG]](http://img254.imageshack.us/my.php?image=screenshotyq6.png)

When I go into GParted, I also encounter an error when erasing my Hard drive, but it completed anyway. This worries me as I have never seen anything like this before.

Error Report:
> 
Apr 30 23:22:41 ubuntu ubiquity[11918]: log-output -t ubiquity laptop-detect
Apr 30 23:22:45 ubuntu ubiquity[11918]: switched to page stepLanguage
Apr 30 23:22:46 ubuntu localechooser: info: Locale has been preseeded to en_US.UTF-8
Apr 30 23:22:46 ubuntu localechooser: info: Set languagechooser/language-name = 'English'
Apr 30 23:22:46 ubuntu localechooser: info: Set countrychooser/shortlist-en = 'US'
Apr 30 23:22:46 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Apr 30 23:22:55 ubuntu localechooser: info: LANGNAME=English
Apr 30 23:22:55 ubuntu localechooser: info: line=English;0;en;US;en_US.UTF-8;UTF-8;;kbd=lat0-sun16(utf8)
Apr 30 23:22:55 ubuntu localechooser: info: Set debian-installer/language = 'en'
Apr 30 23:22:55 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Apr 30 23:22:55 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
Apr 30 23:22:55 ubuntu localechooser: info: Set debian-installer/country = 'US'
Apr 30 23:22:55 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'kbd=lat0-sun16(utf8)'
Apr 30 23:22:55 ubuntu localechooser: info: Set debconf/language = 'en'
Apr 30 23:22:55 ubuntu localechooser: info: Set countrychooser/country-name = 'United States'
Apr 30 23:22:55 ubuntu localechooser: info: Set debian-installer/country = 'US'
Apr 30 23:22:55 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Apr 30 23:22:55 ubuntu ubiquity[11918]: debconffilter_done: Language (current: Language)
Apr 30 23:22:55 ubuntu ubiquity[11918]: Step_before = stepLanguage
Apr 30 23:22:57 ubuntu ubiquity[11918]: switched to page stepLocation
Apr 30 23:22:57 ubuntu ubiquity[11918]: Step_after = stepLocation
Apr 30 23:23:04 ubuntu localechooser: info: Locale has been preseeded to en_US.UTF-8
Apr 30 23:23:04 ubuntu localechooser: info: Set languagechooser/language-name = 'English'
Apr 30 23:23:04 ubuntu localechooser: info: Set countrychooser/shortlist-en = 'US'
Apr 30 23:23:04 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Apr 30 23:23:04 ubuntu localechooser: info: Set debconf/language = ''
Apr 30 23:23:04 ubuntu localechooser: info: Set countrychooser/country-name = 'United States'
Apr 30 23:23:04 ubuntu localechooser: info: Set debian-installer/country = 'US'
Apr 30 23:23:04 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Apr 30 23:23:05 ubuntu ubiquity[11918]: debconffilter_done: Timezone (current: Timezone)
Apr 30 23:23:05 ubuntu ubiquity[11918]: Step_before = stepLocation
Apr 30 23:23:05 ubuntu ubiquity[11918]: switched to page stepKeyboardConf
Apr 30 23:23:05 ubuntu ubiquity[11918]: Step_after = stepKeyboardConf
Apr 30 23:23:06 ubuntu ubiquity[11918]: log-output -t ubiquity setxkbmap -model pc105 -layout us
Apr 30 23:23:10 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Apr 30 23:23:10 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Apr 30 23:23:10 ubuntu ubiquity[11918]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Apr 30 23:23:10 ubuntu ubiquity[11918]: debconffilter_done: ConsoleSetup (current: ConsoleSetup)
Apr 30 23:23:10 ubuntu ubiquity[11918]: Step_before = stepKeyboardConf
Apr 30 23:23:10 ubuntu ubiquity[11918]: switched to page stepPartAuto
Apr 30 23:23:10 ubuntu ubiquity[11918]: Step_after = stepPartAuto
Apr 30 23:23:11 ubuntu ubiquity: /bin/sh: Can't open parted_server
Apr 30 23:23:11 ubuntu ubiquity[11918]: debconffilter_done: Partman (current: Partman)
Apr 30 23:23:11 ubuntu ubiquity[11918]: dbfilter_handle_status: ('Partman', 10)

---

