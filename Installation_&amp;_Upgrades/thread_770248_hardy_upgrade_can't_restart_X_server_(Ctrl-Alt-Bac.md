---
title: "hardy upgrade: can't restart X server (Ctrl-Alt-Backspace)"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by tanguyr on 2008-04-27
Hello,

After upgrading from Gutsy to Hardy, i am experiencing the following problem with my X server: if i kill the X server (Ctrl-Alt-Backspace), or if it dies of "natural causes" (i.e. compiz crashes) i am left at a black screen with no possibility to get back to a graphical or command line interface. In Gutsy X would restart and i would be returned to the KDM login screen, or at least i could use Ctrl-Alt-F1-F6 to get a CL prompt. Now in Hardy: nothing - i am forced to hard reboot the machine.

This is on an Asus W2 laptop with an ATI X1700 card running fglrx drivers. I am running my xorg.conf file from Gutsy, except that now AIGLX and Compositing are turned on.

Regs,
/t

---

### Post by Quicky on 2008-04-27
I have exactly the same problem. I'm running Ubuntu (not kubuntu), on a laptop with an integrated intel graphics card. I have no desktop effects enabled, so its a fairly different setup to yours, but I still have the same issue. 

I went straight from Dapper (LTS only for me) which was faultless in every respect, and I'm slowly beginning to question why I upgraded.

---

### Post by sporkinum on 2008-05-08
Exact same problem. And that is when running with the vesa driver as I can't get the radeon driver to work at all. This hoses me being able to log out back into the login screen.

I truly think they must have done hardly any testing prior to release.

---

### Post by lordbux on 2009-12-30
bump

---

### Post by lordbux on 2010-04-28
you can re-enable the 
ctr-alt-backspace as it is disabled by default in Hardy 

Using GNOME

* Get to the System->Preferences->Keyboard menu.

* Select the &#8220;Layouts&#8221; tab and click on the &#8220;Layout Options&#8221; button.

* Then select &#8220;Key sequence to kill the X server&#8221; and enable &#8220;Control + Alt + Backspace&#8221;.

------------------------------------
Using KDE

* Launch &#8220;systemsettings&#8221;

* Select &#8220;Regional & Language&#8221;.

* Select &#8220;Keyboard Layout&#8221;.

* Click on &#8220;Enable keyboard layouts&#8221; (in the Layout tab).

* Select the &#8220;Advanced&#8221; tab. Then select &#8220;Key sequence to kill the X server&#8221; and enable &#8220;Control + Alt + Backspace&#8221;.
-------------------------------------===
Using the command line

You can type the following command to enable Zapping immediately.

```
setxkbmap -option terminate:ctrl_alt_bksp
```

If you&#8217;re happy with the new behaviour you can add that command to your ~/.xinitrc in order to make the change permanent.
---------------------------------------------------
Using HAL

You can add the following line in /usr/share/hal/fdi/policy/10osvendor/10-x11-input.fdi (inside the <match key=&#8221;info.capabilities&#8221; contains=&#8221;input.keys&#8221;> section):

```
<merge key="input.xkb.options" type="string">terminate:ctrl_alt_bksp</merge>
```

---

### Post by markjensen on 2010-05-02
> **lordbux said:**
> ...
You can type the following command to enable Zapping immediately.

```
setxkbmap -option terminate:ctrl_alt_bksp
```

If you’re happy with the new behaviour you can add that command to your ~/.xinitrc in order to make the change permanent.
---------------------------------------------------
Using HAL

You can add the following line in /usr/share/hal/fdi/policy/10osvendor/10-x11-input.fdi (inside the <match key=”info.capabilities” contains=”input.keys”> section):

```
<merge key="input.xkb.options" type="string">terminate:ctrl_alt_bksp</merge>
```
I am using Fluxbox, so can't navigate the KDE or Gnome menus.

The command "setxkbmap -option terminate:ctrl_alt_bksp" works fine.  However, I have to enter it in a terminal every time to get it to work again.  I created an .xinitrc file with "setxkbmap -option terminate:ctrl_alt_bksp", but that does nothing.

I tried to follow your HAL instructions, but there is no "10-x11-input.fdi" file.  There is a plain input file: 10-input-policy.fdi that has the indicated input.keys section.   But, as you might guess, there is no restoring CTRL-ALT-Backspace function.

Any additional insight?  Running a 10.04 Xubuntu foundation with fluxbox as my WM.

---

