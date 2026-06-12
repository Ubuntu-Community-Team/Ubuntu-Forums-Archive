---
title: "[SOLVED] flash plugin for opera"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by rob1984 on 2007-11-27
can anybody help me get the flash browser plugin installed for opera?
i have the package but it automatically installs itself for firefox.
do i need to alter the code? if so where do i need to send the installed file?

cheers

---

### Post by rob1984 on 2007-11-27
done it now.

first i removed my failed attempt:

```
rm /home/*myhomedirectory*/.mozilla/plugins/libflashplayer.so
```

then to install the plugin:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by moe_syzlak on 2007-11-30
first off, i already had firefox and flash plugin installed BEFORE I INSTALLED Opera

Second off, if you have 64bit system u will need to do some linux magic to get it working.

i recommend that u use 32bit ubuntu because 32 bit users have more fun. for instance, 32 bit users of firefox can just click and go to install plugins for 32bit firefox. 64bit firefox users had to install nspluginwrapper for the 64bit firefox to use the 32bit plugin.

are u running 32bit ubuntu with 32bit Opera (I don't know if there is a 64bit Opera). 

all i know is that u cant use a 64bit program with a 32bit plugin as in the case of 64bit firefox and 32bit flash player

---

