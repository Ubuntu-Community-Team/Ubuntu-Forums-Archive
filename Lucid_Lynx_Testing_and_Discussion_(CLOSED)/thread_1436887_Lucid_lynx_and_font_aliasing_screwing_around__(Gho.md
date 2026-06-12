---
title: "Lucid lynx and font aliasing screwing around ? (Ghosting in some letters)"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SuppoTaalasmaa on 2010-03-23
After updating to Lucid Lynx today (beta1) I noticed that font rendering has changed somehow. Many places things look more sharper.. 

But also, a problem that wasn't here in the past is happening, now some fonts and sizes there is clear ghosting in the letters, which makes reading quite annoying... 
Here is a sample picture of that:
[IMG]http://i43.tinypic.com/9q8t4z.jpg[/IMG]

Any ideas what is happening ?

---

### Post by kerry_s on 2010-03-23
i did the old ~/.fonts.conf

```

<?xml version="1.0"?>
<fontconfig>
    <match target="font" >
    <edit mode="assign" name="hinting"><bool>true</bool></edit>
    <edit mode="assign" name="hintstyle"><const>hintfull</const></edit>
    <edit mode="assign" name="antialias"><bool>true</bool></edit>
    </match>
</fontconfig>


```

---

### Post by philinux on 2010-03-23
> **SuppoTaalasmaa said:**
> 

Any ideas what is happening ?

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/512615](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/512615)

---

### Post by SuppoTaalasmaa on 2010-03-23
> **kerry_s said:**
> i did the old ~/.fonts.conf

```

<?xml version="1.0"?>
<fontconfig>
    <match target="font" >
    <edit mode="assign" name="hinting"><bool>true</bool></edit>
    <edit mode="assign" name="hintstyle"><const>hintfull</const></edit>
    <edit mode="assign" name="antialias"><bool>true</bool></edit>
    </match>
</fontconfig>


```

Hi kerry_s, can you elaborate ? That file is missing on my system... Should I create it and update font-cache ? 
Those seem like similar settings as in Appearance -> Font and "Detailed" panel... Except that antialias is missing from there...

---

### Post by kerry_s on 2010-03-23
> **SuppoTaalasmaa said:**
> Hi kerry_s, can you elaborate ? That file is missing on my system... Should I create it and update font-cache ? 
Those seem like similar settings as in Appearance -> Font and "Detailed" panel... Except that antialias is missing from there...

yes, that's a file you create. some programs look for it for the font settings.

just create it, paste what i put, log out & back in, see if it helps.

---

### Post by Starks on 2010-03-23
Perhaps unrelated, but Cairo antialiasing is still broken in Lucid's Firefox 3.6

---

### Post by psyke83 on 2010-03-23
> **Starks said:**
> Perhaps unrelated, but Cairo antialiasing is still broken in Lucid's Firefox 3.6

Yes, but there are [ways]("http://ubuntuforums.org/showpost.php?p=9010164&postcount=10") to overcome the problem if you can't wait for the official fix.

---

### Post by SuppoTaalasmaa on 2010-03-23
> **Starks said:**
> Perhaps unrelated, but Cairo antialiasing is still broken in Lucid's Firefox 3.6

> **philinux said:**
> [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/512615](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/512615)

> **psyke83 said:**
> Yes, but there are [ways]("http://ubuntuforums.org/showpost.php?p=9010164&postcount=10") to overcome the problem if you can't wait for the official fix.

Thanks for the replies, this probably is the issue, and I don't mind waiting for official fix.

Btw. does someone have an idea what has been done the the font engine ? I really like the new sharpness of the fonts...

---

### Post by SuppoTaalasmaa on 2010-03-23
> **kerry_s said:**
> yes, that's a file you create. some programs look for it for the font settings.

just create it, paste what i put, log out & back in, see if it helps.

Thanks for the info, I'll try that!

---

### Post by psyke83 on 2010-03-23
> **kerry_s said:**
> i did the old ~/.fonts.conf

```

<?xml version="1.0"?>
<fontconfig>
    <match target="font" >
    <edit mode="assign" name="hinting"><bool>true</bool></edit>
    <edit mode="assign" name="hintstyle"><const>hintfull</const></edit>
    <edit mode="assign" name="antialias"><bool>true</bool></edit>
    </match>
</fontconfig>


```

It's not necessary to create configuration files anymore. Simply run GNOME Appearance Preferences, Fonts tab, and change the options there; it seems that you prefer the "Full" hinting style over the default, "Slight".

Also, this will not help with the ghosting issue as it's a bug in Firefox (see my previous post).

---

### Post by kerry_s on 2010-03-23
> **psyke83 said:**
> It's not necessary to create configuration files anymore. Simply run GNOME Appearance Preferences, Fonts tab, and change the options there; it seems that you prefer the "Full" hinting style over the default, "Slight".

Also, this will not help with the ghosting issue as it's a bug in Firefox (see my previous post).

your not understanding the purpose, some times the system fonts.conf is not right, you can't change that in "Appearance Preferences" so you want to have your own with the settings you want for those programs that are still using fonts.conf, not everybody uses gnome and has "Appearance Preferences", fonts.conf is always the fall back.

---

### Post by psyke83 on 2010-03-23
> **kerry_s said:**
> your not understanding the purpose, some times the system fonts.conf is not right, you can't change that in "Appearance Preferences" so you want to have your own with the settings you want for those programs that are still using fonts.conf, not everybody uses gnome and has "Appearance Preferences", fonts.conf is always the fall back.

Fair enough. However, the OP uses GNOME, and therefore should know that these steps are redundant (changing the hinting style is not a solution, anyway).

---

