---
title: "can't create Japanese locale: get a segmentation fault on generating locale"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by James Keating on 2010-10-13
Maverick 10.10 is unable to create Japanese locales on my wife's laptop (Acer Aspire 3000). This machine previously had no such problem. The install is a fresh install, since the machine froze during the upgrade (no fault of Ubuntu's). A possible complication is that it froze several times more during the install, and I have gone through many recovery boots and iterations of dpkg configure. 

All relevant packages are installed, I believe. Everything else works. Through System, Administration, Language Support, I have installed all components of English and Japanese. Currently English is selected. Japanese should appear in the list but does not. 

Japanese text appears properly, and I can write in Japanese, &#12494;&#12540;&#12503;&#12525;&#12502;&#12524;&#12512;. But all the menus are in English. Fine by me, but my wife will want Japanese when she uses the computer again (not soon).

This mostly likely is a glibc/libc6 problem, as far as I can tell. I can't find any other Ubuntu user with this problem recently.

And now, some outputs:

1. dpkg-reconfigure locales

sudo dpkg-reconfigure locales
Generating locales...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZW.UTF-8... /usr/sbin/locale-gen: line 236: 13102 Segmentation fault      localedef $no_archive -i $input -c -f $charset $locale_alias $locale
failed
  ja_JP.UTF-8... /usr/sbin/locale-gen: line 236: 13129 Segmentation fault      localedef $no_archive -i $input -c -f $charset $locale_alias $locale
failed
Generation complete.


2. locale-gen 

sudo locale-gen ja_JP.UTF-8
Generating locales...
  ja_JP.UTF-8... /usr/sbin/locale-gen: line 236: 13175 Segmentation fault      localedef $no_archive -i $input -c -f $charset $locale_alias $locale
failed
Generation complete.


3. dpkg-reconfigure -a

sudo dpkg-reconfigure -a
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
acpid stop/waiting
acpid start/running, process 13240
Updating anthy.dic...file name prefix=[./] you can change this by -p option.
  copying .///mkworddic/anthy.wdic (word_dic)
  copying .///depgraph/anthy.dep (dep_dic)
  copying .///calctrans/anthy.trans_info (trans_info)
  copying .///calctrans/anthy.cand_info (cand_info)
  copying .///calctrans/anthy.weak_words (weak_words)
  copying .///calctrans/anthy.corpus_bucket (corpus_bucket)
  copying .///calctrans/anthy.corpus_array (corpus_array)
/usr/bin/mkfiledic done.
done.
Segmentation fault


4. gnome-language selector

sudo gnome-language-selector 
/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py:788: GtkWarning: gtk_cell_view_set_cell_data: assertion `cell_view->priv->displayed_row != NULL' failed
  cell = combo.get_child().get_cell_renderers()[0]


Before I re-installed all the relevant packages, gnome-language selector would not run:

sudo gnome-language-selector
(process:1758): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py:788: GtkWarning: gtk_cell_view_set_cell_data: assertion `cell_view->priv->displayed_row != NULL' failed
  cell = combo.get_child().get_cell_renderers()[0]
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory
(... repeat many times ...)
Traceback (most recent call last):
  File "/usr/bin/gnome-language-selector", line 32, in <module>
    options=options)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 199, in __init__
    self.updateLocaleChooserCombo()
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 68, in wrapper
    res = f(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 840, in updateLocaleChooserCombo
    self.updateExampleBox()
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 912, in updateExampleBox
    locale.setlocale(locale.LC_ALL, mylocale)
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

---

### Post by rafaellaguna on 2010-11-02
I'm having a similar problem. I can't install japanese and spanish. Just keep original english from install process. When I try to generate the japanese locale it says:

ja_JP.UTF-8... cannot open locale definition file `ja_JP': No such file or directory

Any idea?

---

