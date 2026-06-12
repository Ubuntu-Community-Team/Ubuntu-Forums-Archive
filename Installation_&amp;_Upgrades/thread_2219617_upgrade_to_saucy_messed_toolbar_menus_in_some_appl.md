---
title: "upgrade to saucy messed toolbar menus in some applications"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by nonkreon on 2014-04-24
Hello,
I upgraded from raring to saucy and in some applications the toolbar menus display with weird background color [IMG]http://s21.postimg.org/i7oj6ozvb/Screenshot_2014_04_25_01_08_29.png[/IMG]
applications affected include synaptic thus I know it is system-wide. I tried changing themes but had no luck, still renders incorrect. Some applications however such as leafpad can display their toolbar menus correctly.

Other than this small issue the upgrade works perfectly\\:D/

Cheers

---

### Post by Toz on 2014-04-25
Looks like a GTK3 issue. Does the same happen with the default Greybird theme (Settings Manager >> Appearance >> Style tab)?

Did you make any manual modifications to the GTK3 config files in ~/.config/gtk-3.0 or /etc/gtk-3.0?

Which theme are you using in the screenshot?

---

### Post by nonkreon on 2014-04-25
I don't know why but the shimmer-themes package was not installed and all themes in that package seem to render fine. The theme used was A+Sky-n-Sea. As far as I know there has not been any change to the items in the gtk folders, but since this installation had many adventures let me share the contents of the files:
/etc/gtk-3.0/settings.ini:```
[Settings]
gtk-theme-name = Ambiance
gtk-icon-theme-name = ubuntu-mono-dark
gtk-fallback-icon-theme = gnome
gtk-sound-theme-name = ubuntu
gtk-icon-sizes = panel-menu-bar=24,24

```
/etc/gtk-3.0/im-multipress.conf:(although the content it is completely unrelated maybe the file is missing something)```
# Example configuration file for the GTK+ Multipress Input Method# Authored by Openismus GmbH, 2009.
#
# This file follows the GKeyFile format.  On the left of the equal sign goes
# the key that you press repeatedly to iterate through the text items listed
# on the right-hand side.  The list items are separated by semicolons ";" and
# consist of one or more characters each.  The backslash "\" is used to escape
# characters; for instance "\;" for a literal semicolon.
#
# The example configuration below imitates the behavior of a standard mobile
# phone by a major manufacturer, with German language setting.
[keys]
KP_1 = .;,;?;!;';";1;-;(;);@;/;:;_
KP_2 = a;b;c;2;ä;à;á;ã;â;å;æ;ç
KP_3 = d;e;f;3;è;é;ë;ê;ð
KP_4 = g;h;i;4;ì;í;î;ï
KP_5 = j;k;l;5;£
KP_6 = m;n;o;6;ö;ò;ó;ô;õ;ø;ñ
KP_7 = p;q;r;s;7;ß;$
KP_8 = t;u;v;8;ü;ù;ú;û
KP_9 = w;x;y;z;9;ý;þ
KP_0 = \s;0

```
~/.config/gtk-3.0/bookmarks contains only some default bookmarks. There are no other files in the respective folders.

If you have the time I want to solve this problem completely, and to be able to use my original theme. But if you believe this is enough and I should stick with the shimmer themes, I have nothing else to say other than a big "Thank you!"

---

### Post by Toz on 2014-04-25
GTK3 is a moving target. With every major update, themes need to be updated. If you want to continue using that theme, you should look for an updated version of it or contact the author and ask for an update.

---

### Post by nonkreon on 2014-04-25
Oops, okay then. Thank you very much for solving my problem :)

---

### Post by Topsiho on 2014-04-25
Saucy (13.10) will be discontinued in July.
Approximately the same time the first point release of 14.04 will be released.
AFAIK

Topsiho

---

