---
title: "ubiquity installer crashes"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by cedbled on 2006-09-06
Hey,
I got an old Win 98 box, with 384 MB Ram, 20Gb HD, and I have completely reformatted the HD.

The installer always crashes at the same spot where it begins to partition the drive (I always select erase all, because I dont' need windows anymore).

This is the syslog it wrote:

Ubiquity 1.0.12
Wed, 06 Sep 2006 05:46:46 INFO     switched to page stepLanguage
ubiquity: Starting up '['/usr/lib/ubiquity/localechooser/localechooser']' for ubiquity.components.language.Language
ubiquity: Watching for question patterns ^languagechooser/language-name
Wed, 06 Sep 2006 05:47:17 INFO     Step_before = stepLanguage
Wed, 06 Sep 2006 05:47:34 INFO     switched to page stepLocation
Wed, 06 Sep 2006 05:47:35 INFO     Step_after = stepLocation
ubiquity: Starting up '['/usr/share/ubiquity/tzsetup']' for ubiquity.components.timezone.Timezone
ubiquity: Watching for question patterns ^time/zone$
Wed, 06 Sep 2006 05:48:51 INFO     Step_before = stepLocation
Wed, 06 Sep 2006 05:48:51 INFO     switched to page stepKeyboardConf
Wed, 06 Sep 2006 05:48:51 INFO     Step_after = stepKeyboardConf
ubiquity: kbd-chooser prepare
ubiquity: Starting up '['/bin/sh', '-c', '. /usr/share/debconf/confmodule; exec /usr/lib/ubiquity/kbd-chooser/kbd-chooser']' for ubiquity.components.kbd_chooser.KbdChooser
ubiquity: Watching for question patterns ^kbd-chooser/method$, ^console-keymaps.*/keymap$, ERROR
ubiquity: apply_keyboard: us
ubiquity: apply_keyboard: layout us, model pc104
ubiquity: Display map: {u'Swedish': u'se-latin1', u'Icelandic': u'is-latin1', u'Estonian': u'et', u'Romanian': u'ro', u'Italian': u'it', u'Latin American': u'la-latin1', u'Dutch': u'nl', u'Brazilian (EUA layout)': u'br-latin1', u'Belgian': u'be2-latin1', u'Danish': u'dk-latin1', u'Bulgarian': u'bg', u'Turkish (F layout)': u'trfu', u'Hungarian': u'hu', u'Macedonian': u'mk', u'Lithuanian': u'lt', u'French': u'fr-latin9', u'Norwegian': u'no-latin1', u'Slovakian': u'sk-qwerty', u'Russian': u'ru', u'Dvorak': u'dvorak', u'Slovene': u'slovene', u'Finnish': u'fi-latin1', u'British English': u'uk', u'Spanish': u'es', u'Greek': u'gr', u'Canadian French': u'cf', u'Latvian': u'lv-latin4', u'American English': u'us', u'Croatian': u'croat', u'Portuguese': u'pt-latin1', u'Czech': u'cz-lat2', u'Ukrainian': u'ua', u'Japanese': u'jp106', u'Belarusian': u'by', u'Turkish (Q layout)': u'trqu', u'German': u'de-latin1-nodeadkeys', u'Hebrew': u'hebrew', u'Polish': u'pl', u'Brazilian (ABNT2 layout)': u'br-abnt2', u'Swiss French': u'fr_CH-latin1', u'Swiss German': u'sg-latin1', u'Serbian (Cyrillic)': u'sr-cy'}
ubiquity: Untranslated choices: [u'by', u'bg', u'croat', u'cz-lat2', u'sg-latin1', u'de-latin1-nodeadkeys', u'dk-latin1', u'us', u'uk', u'dvorak', u'et', u'es', u'la-latin1', u'fi-latin1', u'fr-latin9', u'be2-latin1', u'cf', u'fr_CH-latin1', u'gr', u'hebrew', u'hu', u'is-latin1', u'it', u'lt', u'lv-latin4', u'jp106', u'mk', u'no-latin1', u'nl', u'pl', u'pt-latin1', u'br-abnt2', u'br-latin1', u'ro', u'ru', u'sk-qwerty', u'slovene', u'sr-cy', u'se-latin1', u'trfu', u'trqu', u'ua']
ubiquity: Choices: [u'Belarusian', u'Bulgarian', u'Croatian', u'Czech', u'Swiss German', u'German', u'Danish', u'American English', u'British English', u'Dvorak', u'Estonian', u'Spanish', u'Latin American', u'Finnish', u'French', u'Belgian', u'Canadian French', u'Swiss French', u'Greek', u'Hebrew', u'Hungarian', u'Icelandic', u'Italian', u'Lithuanian', u'Latvian', u'Japanese', u'Macedonian', u'Norwegian', u'Dutch', u'Polish', u'Portuguese', u'Brazilian (ABNT2 layout)', u'Brazilian (EUA layout)', u'Romanian', u'Russian', u'Slovakian', u'Slovene', u'Serbian (Cyrillic)', u'Swedish', u'Turkish (F layout)', u'Turkish (Q layout)', u'Ukrainian']
ubiquity: console-keymaps-at/keymap db: us
Wed, 06 Sep 2006 05:49:20 INFO     Step_before = stepKeyboardConf
Wed, 06 Sep 2006 05:49:20 INFO     switched to page stepUserInfo
Wed, 06 Sep 2006 05:49:20 INFO     Step_after = stepUserInfo
ubiquity: Starting up '['/usr/lib/ubiquity/user-setup/user-setup-ask', '/target']' for ubiquity.components.usersetup.UserSetup
ubiquity: Watching for question patterns ^passwd/user-fullname$, ^passwd/username$, ^passwd/user-password$, ^passwd/user-password-again$, ERROR
ON STATE: 1
ON STATE: 2
ON STATE: 3
ON STATE: 4
ON STATE: 5
ON STATE: 6
ON STATE: 7
ON STATE: 8
Wed, 06 Sep 2006 05:49:55 INFO     Step_before = stepUserInfo
Wed, 06 Sep 2006 05:49:55 INFO     switched to page stepPartDisk
Wed, 06 Sep 2006 05:49:55 INFO     Step_after = stepPartDisk
ubiquity: Starting up '/bin/partman' for ubiquity.components.partman.Partman
ubiquity: Watching for question patterns ^partman-auto/select_disk$, ^partman-auto/.*automatically_partition$, ^partman-partitioning/new_size$, ^partman/choose_partition$, ^partman/confirm.*, type:boolean, ERROR, PROGRESS
unsupported
kernelmodules_basicfilesystems
kernelmodules_ext3
kernelmodules_jfs
kernelmodules_reiserfs
kernelmodules_xfs
umount_target
parted
dump
update_partitions
filesystems_detected
auto_mountpoints
autouse_swap
backup
Wed, 06 Sep 2006 05:50:34 INFO     switched to page stepPartAuto
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
Wed, 06 Sep 2006 05:51:18 INFO     switched to page stepReady
ubiquity: Starting up '['/usr/share/ubiquity/summary']' for ubiquity.components.summary.Summary
ubiquity: Watching for question patterns ^ubiquity/summary$
/bin/partman: line 194:  8247 Illegal instruction     $s
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1169, in watch_debconf_fd_helper
    return callback(source, debconf_condition)
  File "/usr/lib/python2.4/site-packages/ubiquity/filteredcommand.py", line 144, in process_input
    if not self.process_line():
  File "/usr/lib/python2.4/site-packages/ubiquity/filteredcommand.py", line 82, in process_line
    return self.dbfilter.process_line()
  File "/usr/lib/python2.4/site-packages/ubiquity/debconffilter.py", line 275, in process_line
    progress_title):
  File "/usr/lib/python2.4/site-packages/ubiquity/filteredcommand.py", line 309, in progress_start
    ret = self.frontend.debconf_progress_start(
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1190, in debconf_progress_start
    self.debconf_progress_set(0)
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1199, in debconf_progress_set
    fraction = self.progress_position.fraction()
  File "/usr/lib/python2.4/site-packages/ubiquity/progressposition.py", line 66, in fraction
    fraction = ((self.inner_position - self.positions[0][0]) /
ZeroDivisionError: float division

unsupported


Can anyone help me with this, or at least point me in the right direction?

---

