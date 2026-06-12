---
title: "French keyboard in console mode (not in X)"
date: 2005-02-21
forum: Installation &amp; Upgrades
---

### Post by rom on 2005-02-21
hi,

lately, i found myself unable to print french charaters on the screen in console mode, when not in X. So, for those who might wonder how to do this, and because i could not find it on those forums, here it is:

PS: this information is widely available on the net, just thought there is no harm in duplicating it ;-)

1 - check you've got the right console font for french     

```

ls /usr/share/consolefonts/lat9-16.psf.gz

``` 

edit the file **/etc/console-tools/config** as root
change the last line from 
```

SCREEN_FONT=lat0-sun16

```
to
```

SCREEN_FONT=lat9u-16

```

execute the script **/etc/init.d/console-screen.sh**

At this point, you're done if you're only goal it to being able to "see" french characters (é,ç, etc...). A different font may be choosen to show other languages appropriately.

2 - if you want to change your keyboard to french, check you have this file:
**/usr/share/keymaps/i386/azerty/fr-latin9.kmap.gz**

if yes, type as root
```

cd /usr/share/keymaps/i386/azerty/
loadkeys fr-latin9.kmap.gz

```

Now you should have a pretty much functional french key binding for your keyboard.

To make the change permanent, copy **fr-latin9.kmap.gz** to **/etc/console-tools** as root
```

cp /usr/share/keymaps/i386/azerty/fr-latin9.kmap.gz /etc/console-tools/default.map.gz

```

Or create a simlink to that keymap, it works just as well.

Log in your system again.

3 - Now, even further, say you want to "french-ify" the whole system, edit **/etc/environment**. 
Change
```

LANGUAGE="en_GB:en_US:en_GB:en"
LANG=en_GB.UTF-8

```

to
```

LANGUAGE="fr_FR:fr_FR:fr_FR:fr"
LANG=fr_FR.UTF-8@euro

```

Please note it means you must have the fr_FR.UTF8@euro locale installed. You can equally choose en_FR, en_FR@euro, fr_FR.UTF8, fr_FR.ISO885915 or fr_FR.ISO885915@euro.

If those locales are not installed, do as root
```

dpkg-reconfigure locales

```

and select the ones you need.

That's all. Hope it will help a few people.

Rom

---

