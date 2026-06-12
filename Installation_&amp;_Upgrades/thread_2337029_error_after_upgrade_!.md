---
title: "error after upgrade ?!"
date: 2016-09-13
forum: Installation &amp; Upgrades
---

### Post by fairbird on 2016-09-13
I'm try to upgrade ubuntu 14.04 to 16.04 but after upgrade it still ubuntu 14.04 and I got this error in terminal 
```
(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1666:45: Missing name of pseudo-class

(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1684:45: Missing name of pseudo-class


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1725:25: Missing name of pseudo-class


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1732:25: Missing name of pseudo-class


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1751:25: Missing name of pseudo-class


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1758:25: Missing name of pseudo-class


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1774:25: Missing name of pseudo-class


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1792:25: Missing name of pseudo-class


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2001:19: Missing name of pseudo-class


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2019:19: Missing name of pseudo-class


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2137:2: Missing name of pseudo-class


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: unity.css:126:28: No property named '-gtk-icon-transform'


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: nautilus.css:40:16: 'outline-radius' is not a valid property name


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: gnome-panel.css:92:20: Missing name of pseudo-class


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: gnome-panel.css:98:20: Missing name of pseudo-class


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: gnome-panel.css:104:20: Missing name of pseudo-class


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: gnome-terminal.css:10:41: Missing name of pseudo-class


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: unity-greeter.css:72:28: No property named '-gtk-icon-transform'


(software-properties-gtk:2541): Gtk-WARNING **: Theme parsing error: calendar.css:9:18: 'outline-radius' is not a valid property name
raed@fairbird:~$
```

Any idea ?! how to fix it and upgrade it my ubuntu ?!

Thank you

---

### Post by Impavidus on 2016-09-14
Those "errors" are gtk warnings, not really errors. They indicate some things in the definition of your theme are incompatible with your version of gtk (responsible for drawing the GUI according to your theme) and those things are ignored. In my experience, you get those warnings all the time when running gtk applications from the terminal. I ignore them.

Why do you think you're still running 14.04? Run **uname -r**. It should show you run a 4.4 kernel. Run **lsb_release -a**. It should say you run 16.04. Check your software sources in /etc/apt/sources.list. It should say xenial.

---

### Post by fairbird on 2016-09-14
my ubuntu after upgrade come crazy mix file system between 14.04 and 16.04
> raed@fairbird:~$ uname -r4.4.0-36-generic
raed@fairbird:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial
raed@fairbird:~$

command info says 16.04
details say 14.04 as photo shown
some of packages still old one from 14.04 did not upgrade ... 

I think I will install the new distribution again ..

Thank you

---

### Post by Impavidus on 2016-09-14
You can do a clean install if you wish. That should solve any problems.

If you prefer to trouble-shoot this, run these two commands. They should attempt to upgrade your software to the latest available for 16.04:```
sudo apt update
sudo apt upgrade
```Post the complete output.

It seems that some tiny bits of your system didn't properly upgrade.

---

### Post by ian-weisser on 2016-09-14
Looks like perhaps you were offered a 'Partial Upgrade,' and selected it. Was that so?

---

### Post by fairbird on 2016-09-14
Thank you ...

I have installed new ubuntu 16.04 ...

But still I have problem ....

I'm update moving from 14.04 to 16.04 because 14.04 doesn't supported ([COLOR=#282828][FONT=helvetica]pcre-tools [/FONT][/COLOR][COLOR=#282828][FONT=helvetica]package[/FONT][/COLOR])
And also 16.04 doesn't supported, just ([COLOR=#282828][FONT=helvetica]pcre2-utils package[/FONT][/COLOR]) ...

I've installed and I got only this code supported 
> raed@fairbird:~/openpli/openpli-oe-core/build$ pcre2test -CPCRE2 version 10.21 2016-01-12
Compiled with
  8-bit support
  16-bit support
  32-bit support
  UTF and UCP support (Unicode version 8.0.0)
  Just-in-time compiler support: x86 32bit (little endian + unaligned)
  Newline sequence is LF
  \R matches CR, LF, or CRLF only
  \C is supported
  Internal link size = 2
  Parentheses nest limit = 250
  Default match limit = 10000000
  Default recursion depth limit = 10000000
  Match recursion uses stack

It missing 
> [COLOR=#000000]UTF[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]8[/COLOR][COLOR=#000000] support[/COLOR]  UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]16[/COLOR] support
  UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]32[/COLOR] support [COLOR=#000000]  [/COLOR][COLOR=#660066]Unicode[/COLOR][COLOR=#000000] properties support[/COLOR]
because  ([COLOR=#282828][FONT=helvetica]pcre-tools [/FONT][/COLOR][COLOR=#282828][FONT=helvetica]package[/FONT][/COLOR]) have this 
> [COLOR=#666600][[/COLOR][COLOR=#000000]wanwizard@catwoman[/COLOR][COLOR=#666600]][/COLOR][COLOR=#000000] $ pcretest [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]C[/COLOR]PCRE version [COLOR=#006666]8.39[/COLOR] [COLOR=#006666]2016[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]06[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]14[/COLOR]
[COLOR=#660066]Compiled[/COLOR] [COLOR=#000088]with[/COLOR]
  [COLOR=#006666]8[/COLOR][COLOR=#666600]-[/COLOR]bit support
  UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]8[/COLOR] support
  [COLOR=#006666]16[/COLOR][COLOR=#666600]-[/COLOR]bit support
  UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]16[/COLOR] support
  [COLOR=#006666]32[/COLOR][COLOR=#666600]-[/COLOR]bit support
  UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]32[/COLOR] support
  [COLOR=#660066]Unicode[/COLOR] properties support
  [COLOR=#660066]Just[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000088]in[/COLOR][COLOR=#666600]-[/COLOR]time compiler support[COLOR=#666600]:[/COLOR] x86 [COLOR=#006666]64bit[/COLOR] [COLOR=#666600]([/COLOR]little endian [COLOR=#666600]+[/COLOR] unaligned[COLOR=#666600])[/COLOR]
  [COLOR=#660066]Newline[/COLOR] sequence [COLOR=#000088]is[/COLOR] LF
  \R matches all [COLOR=#660066]Unicode[/COLOR] newlines
  [COLOR=#660066]Internal[/COLOR] link size [COLOR=#666600]=[/COLOR] [COLOR=#006666]2[/COLOR]
  POSIX malloc threshold [COLOR=#666600]=[/COLOR] [COLOR=#006666]10[/COLOR]
  [COLOR=#660066]Parentheses[/COLOR] nest limit [COLOR=#666600]=[/COLOR] [COLOR=#006666]250[/COLOR]
  [COLOR=#660066]Default[/COLOR] match limit [COLOR=#666600]=[/COLOR] [COLOR=#006666]10000000[/COLOR]
  [COLOR=#660066]Default[/COLOR] recursion depth limit [COLOR=#666600]=[/COLOR] [COLOR=#006666]10000000[/COLOR] [COLOR=#000000]  [/COLOR][COLOR=#660066]Match[/COLOR][COLOR=#000000] recursion uses stack[/COLOR]

I need 
> [COLOR=#000000]UTF[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]8[/COLOR][COLOR=#000000] support[/COLOR]  UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]16[/COLOR] support
  UTF[COLOR=#666600]-[/COLOR][COLOR=#006666]32[/COLOR] support [COLOR=#000000]  [/COLOR][COLOR=#660066]Unicode[/COLOR][COLOR=#000000] properties support[/COLOR]

Because I got this error with my build image dreambox
> | configure: error: *** The system-supplied PCRE does not support Unicode properties or UTF-8.


So How can I get full support from [COLOR=#000000]pcre ?![/COLOR]

---

### Post by ian-weisser on 2016-09-15
> **fairbird said:**
> Thank you ...

I have installed new ubuntu 16.04 ...

Since you solved your original problem, I suggest you mark this thread [SOLVED], and open a new thread with a better title for your pcre issue. You will get more and better help that way.

---

### Post by fairbird on 2016-09-15
OK...
Solved ...

---

