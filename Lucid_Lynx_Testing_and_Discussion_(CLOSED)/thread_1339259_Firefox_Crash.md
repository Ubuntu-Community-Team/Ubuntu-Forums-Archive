---
title: "Firefox Crash"
date: 2009-11-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zenarcher on 2009-11-27
After running all the available updates this morning, Firefox now crashes when starting.  Starting from a terminal, here is what I'm getting:

zenarcher@stantest:~$ firefox
/usr/lib/firefox-3.5.5/firefox: symbol lookup error: /usr/lib/mozilla/plugins/libskypebuttons.so: undefined symbol: _ZN9QHashData13detach_helperEPFvPNS_4NodeEPvEPFvS1_Ei

Chromium browser is also crashing at startup.  This is on a 64 bit Kubuntu install of 10.04 pre-alpha.

Is anyone else experiencing this?

Cheers,
zenarcher

---

### Post by koso on 2009-11-27
I have the same problems on 32 bit version .. firefox / thunderbird dont even open main window .. chrome browser at least open window, but crashes during web page rendering.  

All other applications i tested crashed after some events ... i.e Dolphin when context menu is invoked, inkscape when file dialog is opened.

---

### Post by zenarcher on 2009-11-27
Great!  Glad to know it isn't just me.  Firefox opens and then crashes for me, just like Chromium.  Well, I'm sure it will be figured out soon and in one of the many coming updates.  Thanks for the verification!

Cheers,
zenarcher

---

### Post by xebian on 2009-11-27
> **zenarcher said:**
> After running all the available updates this morning, Firefox now crashes when starting.  Starting from a terminal, here is what I'm getting:

zenarcher@stantest:~$ firefox
/usr/lib/firefox-3.5.5/firefox: symbol lookup error: /usr/lib/mozilla/plugins/libskypebuttons.so: undefined symbol: _ZN9QHashData13detach_helperEPFvPNS_4NodeEPvEPFvS1_Ei

Chromium browser is also crashing at startup.  This is on a 64 bit Kubuntu install of 10.04 pre-alpha.

Is anyone else experiencing this?

Cheers,
zenarcher

Get rid of that offending /usr/lib/mozilla/plugins/libskypebuttons.so and everything will be ok.

What the heck is that skype plugins anyway?

---

### Post by paul_in_london on 2009-11-27
Yeah, I had a similar problem the other day with FF and chromium/chrome crashing under gnome.

I had installed KDE as a secondary desktop and it started happening after a certain set of updates.

I did:

```
sudo apt-file update
apt-file search /usr/lib/mozilla/plugins/libskypebuttons.so
```

Running that last command again now shows that the library belongs to kdenetwork-dbg and kopete.

When I got rid of kopete (which didn't matter to me because I still use gnome almost exclusively) the crashes stopped happening under gnome.

---

### Post by zenarcher on 2009-11-27
> **xebian said:**
> Get rid of that offending /usr/lib/mozilla/plugins/libskypebuttons.so and everything will be ok.

What the heck is that skype plugins anyway?

Thanks for that tip.  I removed the libskypebuttons.so file and Firefox and Chromium are both working just fine now.  I don't use skype, anyway, or any of the chat applications, so I don't bother with them.

Cheers,
zenarcher

---

