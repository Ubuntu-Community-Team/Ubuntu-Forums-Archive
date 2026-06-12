---
title: "Dead keys not working in Emacs [Lucid]"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by oyvinst on 2010-05-04
Hi,

I'm having trouble with dead keys in Emacs on Ubuntu Lucid and I'm at my wits' end. Using a standard Norwegian keyboard layout, and dead keys work fine in all Gnome applications. But Emacs just spits out messages about undefined keybindings when I use dead key combinations, for instance for tilde (~): &#8220;<dead_tilde> is undefined&#8221;. This is super-annoying, since I use Emacs a lot, and I need some way to fix this.

What I've tried so far:
[LIST]
[*] Loading the 'iso-transl' library in Emacs seemingly makes the dead keys work, but it's not consistent across modes (works for plain text, though), and I didn't need to do this before. Also, loading this breaks Emacs' latin-1-prefix input method, for some reason.
[*] Fiddling with keyboard-preferences, iBus, im-switch xim/none/ibus, etc.
[*] Removing ~/.xinput.d directory.
[*] Fiddling with various environment variables: GTK_IM_METHOD, GTK_IM_MODULES, XMODIFIERS 
[/LIST]

Of course, I'm testing this in Emacs started with '-Q' to elminiate problems that might be caused by my own rather extensive set of initialization files. Using dead keys in Emacs has never been a problem until I upgraded to Ubuntu Lucid.

---

### Post by mrb@hsdev.com on 2010-05-04
I'm having the exact same issue. Not being able to input characters like 'é' and especially '~' is indeed very annoying. 

I gave up for now and created workaround by adding a 'non-dead-key' extra keyboard layout (with checkbox 'layout per window' set to 'on'), so I can at least enter plain ' and " characters in emacs and have the dead keys in all other windows.

---

### Post by oyvinst on 2010-05-04
> **mrb@hsdev.com said:**
> I'm having the exact same issue. Not being able to input characters like 'é' and especially '~' is indeed very annoying. 

I gave up for now and created workaround by adding a 'non-dead-key' extra keyboard layout (with checkbox 'layout per window' set to 'on'), so I can at least enter plain ' and " characters in emacs and have the dead keys in all other windows.

Looks like I tracked down this bastard of an issue, but it took me some hours of work ! The whole story is explained in the follwing bug, which I just filed:
[https://bugs.launchpad.net/ubuntu/+bug/575084](https://bugs.launchpad.net/ubuntu/+bug/575084)

Basically, Emacs doesn't properly understand the locale set by gnome-language-selector (which is stored in file ~/.dmrc and set upon login from GDM), and dead keys stop working as a result.

The fix:
```
sed -i 's/utf8/UTF-8/' ~/.dmrc
```

Then log out and back in. Let me know if it works for you, and I can set this thread to SOLVED.

---

### Post by mrb@hsdev.com on 2010-05-04
It's a bit different here.

1. I originally had no ~/.dmrc -> problem remains
2. ran gnome-language-sector
   ~/.dmrc does indeed get nl_NL.utf8
3. logged out/in -> problem remains
4. changed to nl_NL.UTF-8 -> problem remains
5. Logged out, chose English as language on login -> SOLVED

rechecked ~/.dmrc after that, and English locale is specified as 'en_US.utf8'

So, the issue is perhaps a bit more subtle than your analysis?

---

### Post by oyvinst on 2010-05-04
> **mrb@hsdev.com said:**
> It's a bit different here.

1. I originally had no ~/.dmrc -> problem remains
2. ran gnome-language-sector
   ~/.dmrc does indeed get nl_NL.utf8
3. logged out/in -> problem remains
4. changed to nl_NL.UTF-8 -> problem remains
5. Logged out, chose English as language on login -> SOLVED

rechecked ~/.dmrc after that, and English locale is specified as 'en_US.utf8'

So, the issue is perhaps a bit more subtle than your analysis?

Perhaps, yes, might even be locale-specific or a combo of keyboard input method and locale. I only tested this for Norwegian UTF-8 locale. But the important thing here is what your LANG variable eventually ends up containing.  What does your LANG variable contain (not value in ~/.dmrc) when Emacs works ?

Invoke Emacs with different alternatives for LANG and see which of them makes or breaks dead keys:
```
$ LANG=nl_NL.utf8 emacs
$ LANG=nl_NL.UTF-8 emacs
$ LANG=en_US.utf8 emacs
$ LANG=en_US.UTF-8 emacs
```

Would be interesting to know. Emacs might be buggy in interpreting locale in general. Or there might be issues with installed locales.

---

### Post by mrb@hsdev.com on 2010-05-04
Surprisingly, emacs does now work with all of them. It is definitely influenced by the language/translation packages and keyboard layouts. 

This has now turned into another problem for me: How to get the default keyboard layout to have dead keys, as on selection, the system throws an error at me: 'Error activating XKB configuration'

---

### Post by oyvinst on 2010-05-04
> **mrb@hsdev.com said:**
> Surprisingly, emacs does now work with all of them. It is definitely influenced by the language/translation packages and keyboard layouts. 

This has now turned into another problem for me: How to get the default keyboard layout to have dead keys, as on selection, the system throws an error at me: 'Error activating XKB configuration'

Doesn't sound good, I've not seen that error message myself when messing around with keyboard layout settings. I'm running with all-defaults in the Gnome keyboard preferences now (I reset it when investigating the Emacs issues). For me, LANG=nb_NO.UTF-8 works, but LANG=nb_NO.utf8 does not (wrt. dead keys in Emacs).

You could try:
```
$ gconftool --recursive-unset /desktop/gnome/peripherals/keyboard
```

Then log out and back in. That should reset keyboard layout settings in Gnome, at least.

You could altså try using the "Set system wide" button in the language selector and see if that does anything to reset things back to normal. I should also note, I'm using a clean Lucid install (no upgrade).

---

### Post by humbaba on 2012-01-31
Just to document another solution.

Using (require 'iso-transl) in the init-file solved the problem for me.

---

