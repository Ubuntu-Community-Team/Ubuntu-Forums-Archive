---
title: "gdmsetup - need two files"
date: 2009-08-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wayne_cat on 2009-08-12
gdmsetup crashes on my system since I have removed (--purge) and reinstalled it.

Could you please post your:

```
/etc/gdm/custom.conf
```and maybe a tar backup of this folder:

```
/var/lib/gdm
```if you can start and unlock gdmsetup.

Thanks

---

### Post by taavikko on 2009-08-12
Here's the custom.conf
```
# GDM configuration storage

[xdmcp]

[chooser]

[security]

[debug]

```

But it's missing the "key" that Sebastian Bacher referred to...

---

### Post by wayne_cat on 2009-08-12
> **taavikko said:**
> Here's the custom.conf
```
# GDM configuration storage

[xdmcp]

[chooser]

[security]

[debug]

```But it's missing the "key" that Sebastian Bacher referred to...

This is what I am looking for ... I had a [daemon] subsection and some defintions
in it ... unfortunately I don't have a backup of this file.

Also ... I have no gconf settings with these parameters in the home directory of the
gdm user ... and I cant find a script that adds them in the gdm deb.

---

### Post by taavikko on 2009-08-12
> **wayne_cat said:**
> This is what I am looking for ... I had a [daemon] subsection and some defintions
in it ... unfortunately I don't have a backup of this file.



If you referred to the autologin entries? that belongs to [daemon] section...
```
AutomaticLoginEnable=true
AutomaticLogin=myusername
```

Those were throwed out of memory, so propably not correct :)

will check for the scripts...

---

### Post by wayne_cat on 2009-08-12
> **taavikko said:**
> If you referred to the autologin entries? that belongs to [daemon] section...
```
AutomaticLoginEnable=true
AutomaticLogin=myusername
```Those were throwed out of memory, so propably not correct :)

will check for the scripts...

There have been more settings.

- TimedLoginEnable
- TimedLoginDelay

not sure what else is missing.

---

### Post by taavikko on 2009-08-12
> **wayne_cat said:**
> There have been more settings.

- TimedLoginEnable
- TimedLoginDelay

not sure what else is missing.

```
TimedLoginEnable=false
TimedLogin=username
TimedLoginDelay=30

```

Maybe we should try googlin these rather trying to remember them from top of our heads :D

---

### Post by taavikko on 2009-08-12
This offers some info: [http://mail.gnome.org/archives/gdm-list/2006-January/msg00000.html](http://mail.gnome.org/archives/gdm-list/2006-January/msg00000.html)

---

### Post by wayne_cat on 2009-08-12
something that I have found in the preinst file

```
# migrate autologin settings
    if ! egrep -q '^(Automatic|Timed)Login(Enable|Delay|)=' /etc/gdm/custom.conf; then
    settings="`egrep '^((Automatic|Timed)LoginEnable=[^f])|^((Automatic|Timed)Login=.)|^TimedLoginDelay=[^3]' /etc/gdm/gdm.conf`" || true
    if [ -n "$settings" ]; then
        echo '[daemon]' >> /etc/gdm/custom.conf
        echo "$settings" >> /etc/gdm/custom.conf

```and the function to register the gconf settings in the postinst file

```
# Automatically added by dh_gconf
if [ "$1" = "configure" ]; then
    gconf-schemas --register gdm-simple-greeter.schemas 
fi
```

---

### Post by tekstr1der on 2009-08-13
Looks like the gdmsetup crashing is fixed in gdm 2.27.4-0ubuntu11

```
gdm (2.27.4-0ubuntu11) karmic; urgency=low

  * debian/patches/09_gdmsetup.patch:
    - clean some unused variables there
    - don't crash if there is no autologin key in the configuration yet
      (lp: #410475)
    - don't specify encoding in desktop entry (lp: #410591)
  * debian/patches/11_crash_for_apport.patch:
    - don't catch crashes so apport can do its job

```

---

### Post by wayne_cat on 2009-08-13
just compiled this version ... fixed

---

