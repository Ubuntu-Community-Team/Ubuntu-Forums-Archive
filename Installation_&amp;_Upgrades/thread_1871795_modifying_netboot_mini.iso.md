---
title: "modifying netboot mini.iso"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by metalfan_ on 2011-10-29
hi,


found this:
[https://help.ubuntu.com/community/Installation/NetworkConsole](https://help.ubuntu.com/community/Installation/NetworkConsole)

looks very interesting but its outdated, i guess.
for oneiric insolinux.cfg looks like this:
```

# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 0

```

in menu.cfg is a line that reads:  
```

include txt.cfg

```

and in txt.cfg i found this:
```

default install
label install
        menu label ^Install
        menu default
        kernel linux
        append vga=788 initrd=initrd.gz -- quiet 
label cli
        menu label ^Command-line install
        kernel linux
        append tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false vga=788 initrd=initrd.gz -- quiet 

```


is this the right place to add the "default netconsole" part mentioned in the howto?

changes the contents to this:
```

default netconsole
label netconsole
       kernel linux
       append vga=normal initrd=initrd.gz preseed/url=http://192.168.11.170/preseed/default.txt console-setup/layoutcode=us console-setup/layout="U.S. English" console-setup/variantcode=intl countrychooser/country-name=Germany debian-installer/country=DE languagechooser/language-name="English" languagechooser/language-name-fb="English" netcfg/get_hostname=NEWMACHINE mirror/http/countries=DE mirror/http/hostname=de.archive.ubuntu.com DEBCONF_PRIORITY=critical
label install
        menu label ^Install
        menu default
        kernel linux
        append vga=788 initrd=initrd.gz -- quiet 
label cli
        menu label ^Command-line install
        kernel linux
        append tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false vga=788 initrd=initrd.gz -- quiet 

```

i did that to see if it works, but after running:
```

sudo mkisofs -r -V "Custom Ubuntu Netboot image" -cache-inodes -J -l -b isolinux.bin -c boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o /tmp/CustomMini.iso /tmp/miniiso_remastered/

```

the remastered mini.iso is about 16mb in size, the downloaded one is about 23mb....why is that?

---

