---
title: "partman crashed"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by tromort on 2008-01-19
oke I wanted to install ubuntu 7.10, everything looked fine till step 3/7 after i selected my keyboard layout, I click forward but when it loads to set up the partition manager it crashes at 50% and i get the following error:
Partman failed with exit code 10. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken.
since I'm pretty much new to ubuntu I have no idea what that log says..here is it anyway
Jan 19 09:10:36 ubuntu ubiquity[12744]: dbfilter_handle_status: response -4
Jan 19 09:10:37 ubuntu kernel: [ 1092.992942] SQUASHFS error: zlib_inflate returned unexpected result 0xfffffffd, srclength 65536, avail_in 0, avail_out 4
Jan 19 09:10:37 ubuntu kernel: [ 1092.992952] SQUASHFS error: sb_bread failed reading block 0x9c6fb
Jan 19 09:10:37 ubuntu kernel: [ 1092.992956] SQUASHFS error: Unable to read page, block 271b6456, size 8871
Jan 19 09:10:37 ubuntu ubiquity: Bus error (core dumped)
Jan 19 09:10:37 ubuntu ubiquity[12744]: debconffilter_done: Partman (current: Partman)
Jan 19 09:10:39 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Jan 19 09:10:39 ubuntu ubiquity[12744]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^console-setup/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Jan 19 09:10:39 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Jan 19 09:10:39 ubuntu ubiquity[12744]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^xserver-xorg/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Jan 19 09:10:43 ubuntu ubiquity[13469]: Ubiquity 1.6.8
Jan 19 09:10:44 ubuntu ubiquity[13469]: log-output -t ubiquity laptop-detect
Jan 19 09:10:46 ubuntu ubiquity[13469]: switched to page stepLanguage
Jan 19 09:10:47 ubuntu localechooser: info: Locale has been preseeded to en_GB.UTF-8
Jan 19 09:10:47 ubuntu localechooser: info: Set languagechooser/language-name = 'English'
Jan 19 09:10:47 ubuntu localechooser: info: Set countrychooser/shortlist-en = 'GB'
Jan 19 09:10:47 ubuntu localechooser: info: Set debian-installer/locale = 'en_GB.UTF-8'
Jan 19 09:10:47 ubuntu ubiquity[13469]: switched to page stepLanguage
Jan 19 09:10:55 ubuntu localechooser: info: LANGNAME=Dutch
Jan 19 09:10:55 ubuntu localechooser: info: line=Dutch;1;nl;NL;nl_NL.UTF-8;UTF-8;;kbd=lat0-sun16(utf8)
Jan 19 09:10:55 ubuntu localechooser: info: Set debian-installer/language = 'nl'
Jan 19 09:10:55 ubuntu localechooser: info: Set debian-installer/locale = 'nl_NL.UTF-8'
Jan 19 09:10:55 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'nl_NL.UTF-8'
Jan 19 09:10:55 ubuntu localechooser: info: Set debian-installer/country = 'NL'
Jan 19 09:10:55 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'kbd=lat0-sun16(utf8)'
Jan 19 09:10:55 ubuntu localechooser: info: Set debconf/language = 'nl'
Jan 19 09:10:55 ubuntu localechooser: info: Set countrychooser/country-name = 'Netherlands'
Jan 19 09:10:56 ubuntu localechooser: info: Set debian-installer/country = 'NL'
Jan 19 09:10:56 ubuntu localechooser: info: Set debian-installer/locale = 'nl_NL.UTF-8'
Jan 19 09:10:56 ubuntu ubiquity[13469]: debconffilter_done: Language (current: Language)
Jan 19 09:10:56 ubuntu ubiquity[13469]: Step_before = stepLanguage
Jan 19 09:10:58 ubuntu ubiquity[13469]: switched to page stepLocation
Jan 19 09:10:58 ubuntu localechooser: info: Locale has been preseeded to nl_NL.UTF-8
Jan 19 09:10:58 ubuntu localechooser: info: Set languagechooser/language-name = 'Dutch'
Jan 19 09:10:58 ubuntu localechooser: info: Set countrychooser/shortlist-nl = 'NL'
Jan 19 09:10:58 ubuntu localechooser: info: Set debian-installer/locale = 'nl_NL.UTF-8'
Jan 19 09:10:58 ubuntu localechooser: info: Set debconf/language = ''
Jan 19 09:10:58 ubuntu localechooser: info: Set countrychooser/country-name = 'Netherlands'
Jan 19 09:10:58 ubuntu localechooser: info: Set debian-installer/country = 'NL'
Jan 19 09:10:58 ubuntu localechooser: info: Set debian-installer/locale = 'nl_NL.UTF-8'
Jan 19 09:10:59 ubuntu ubiquity[13469]: debconffilter_done: Timezone (current: Timezone)
Jan 19 09:10:59 ubuntu ubiquity[13469]: Step_before = stepLocation
Jan 19 09:10:59 ubuntu ubiquity: locale: Cannot set LC_CTYPE to default locale: No such file or directory
Jan 19 09:10:59 ubuntu ubiquity: locale: Cannot set LC_MESSAGES to default locale: No such file or directory
Jan 19 09:10:59 ubuntu ubiquity: locale: Cannot set LC_ALL to default locale: No such file or directory
Jan 19 09:10:59 ubuntu ubiquity: locale: Cannot set LC_CTYPE to default locale: No such file or directory
Jan 19 09:10:59 ubuntu ubiquity: locale: Cannot set LC_MESSAGES to default locale: No such file or directory
Jan 19 09:10:59 ubuntu ubiquity: locale: Cannot set LC_ALL to default locale: No such file or directory
Jan 19 09:10:59 ubuntu ubiquity: 
Jan 19 09:10:59 ubuntu ubiquity[13469]: log-output -t ubiquity setxkbmap -model pc105 -layout us
Jan 19 09:10:59 ubuntu ubiquity[13469]: switched to page stepKeyboardConf
Jan 19 09:11:01 ubuntu ubiquity: perl: warning: Setting locale failed.
Jan 19 09:11:01 ubuntu ubiquity: perl: warning: Please check that your locale settings:
Jan 19 09:11:01 ubuntu ubiquity: ^ILANGUAGE = "nl_NL.UTF-8",
Jan 19 09:11:01 ubuntu ubiquity: ^ILC_ALL = (unset),
Jan 19 09:11:01 ubuntu ubiquity: ^ILC_COLLATE = "C",
Jan 19 09:11:01 ubuntu ubiquity: ^ILANG = "nl_NL.UTF-8"
Jan 19 09:11:01 ubuntu ubiquity:     are supported and installed on your system.
Jan 19 09:11:01 ubuntu ubiquity: perl: warning: Falling back to the standard locale ("C").
Jan 19 09:11:02 ubuntu ubiquity: perl: warning: Setting locale failed.
Jan 19 09:11:02 ubuntu ubiquity: perl: warning: Please check that your locale settings:
Jan 19 09:11:02 ubuntu ubiquity: ^ILANGUAGE = "nl_NL.UTF-8",
Jan 19 09:11:02 ubuntu ubiquity: ^ILC_ALL = (unset),
Jan 19 09:11:02 ubuntu ubiquity: ^ILC_COLLATE = "C",
Jan 19 09:11:02 ubuntu ubiquity: ^ILANG = "nl_NL.UTF-8"
Jan 19 09:11:02 ubuntu ubiquity:     are supported and installed on your system.
Jan 19 09:11:02 ubuntu ubiquity: perl: warning: Falling back to the standard locale ("C").
Jan 19 09:11:02 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Jan 19 09:11:02 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Jan 19 09:11:02 ubuntu ubiquity[13469]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Jan 19 09:11:02 ubuntu ubiquity[13469]: debconffilter_done: ConsoleSetup (current: ConsoleSetup)
Jan 19 09:11:02 ubuntu ubiquity[13469]: Step_before = stepKeyboardConf
Jan 19 09:11:03 ubuntu kernel: [ 1112.069370] SQUASHFS error: zlib_inflate returned unexpected result 0xfffffffd, srclength 65536, avail_in 0, avail_out 4
Jan 19 09:11:03 ubuntu kernel: [ 1112.069378] SQUASHFS error: sb_bread failed reading block 0x9c6fb
Jan 19 09:11:03 ubuntu kernel: [ 1112.069381] SQUASHFS error: Unable to read page, block 271b6456, size 8871
Jan 19 09:11:03 ubuntu ubiquity: Bus error (core dumped)
Jan 19 09:11:03 ubuntu ubiquity[13469]: debconffilter_done: Partman (current: Partman)
Jan 19 09:11:03 ubuntu ubiquity[13469]: dbfilter_handle_status: ('Partman', 10)
I also saw a partman log, don't know if its usefull but ill post it
/lib/partman/init.d/01unsupported: *******************************************************
/lib/partman/init.d/30parted: *******************************************************

I hope anyone can help me with this.
thanks in advance.

---

### Post by tromort on 2008-01-19
can anyone help me with this?

---

