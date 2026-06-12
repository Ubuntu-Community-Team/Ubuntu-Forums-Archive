---
title: "E: /var/cache/apt/archives/linux-image-2.6.22-14-server_2.6.22-14.52_i386.deb: files"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by animeh on 2008-02-12
I am trying to run the update and get this error, I think I have messed up my system. Will I need to reinstall or ther is a fix. 

here is the error: 

E: /var/cache/apt/archives/linux-image-2.6.22-14-server_2.6.22-14.52_i386.deb: files list file for package `procps' is missing final newline

---

### Post by Rocket2DMn on 2008-02-12
Can you please post the contents of the list file for procps?
```
cat /var/lib/dpkg/info/procps.list
```

---

### Post by animeh on 2008-02-12
/.
/etc
/etc/sysctl.conf
/etc/init.d
/etc/init.d/procps.sh
/lib
/lib/libproc-3.2.7.so
/sbin
/sbin/sysctl
/bin
/bin/kill
/bin/ps
/usr
/usr/bin
/usr/bin/uptime
/usr/bin/tload
/usr/bin/free
/usr/bin/top
/usr/bin/vmstat
/usr/bin/watch
/usr/bin/skill
/usr/bin/pmap
/usr/bin/pgrep
/usr/bin/slabtop
/usr/bin/pwdx
/usr/bin/w.procps
/usr/share
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/procps
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/free.1.gz
/usr/share/man/man1/top.1.gz
/usr/share/man/man1/watch.1.gz
/usr/share/man/man1/skill.1.gz
/usr/share/man/man1/kill.1.gz
/usr/share/man/man1/pgrep.1.gz
/usr/share/man/man1/ps.1.gz
/usr/share/man/man1/pwdx.1.gz
/usr/share/man/man1/w.procps.1.gz
/usr/share/man/man1/uptime.1.gz
/usr/share/man/man1/tload.1.gz
/usr/share/man/man1/pmap.1.gz
/usr/share/man/man1/slabtop.1.gz
/usr/share/man/man5
/usr/share/man/man5/sysctl.conf.5.gz
/usr/share/man/man8
/usr/share/man/man8/vmstat.8.gz
/usr/share/man/man8/sysctl.8.gz
/usr/share/doc
/usr/share/doc/procps
/usr/share/doc/procps/changelog.gz
/usr/share/doc/procps/TODO.gz
/usr/share/doc/procps/BUGS
/usr/share/doc/procps/README.Debian
/usr/share/doc/procps/copyright
/usr/share/doc/procps/examples
/usr/share/doc/procps/examples/sysctl.conf
/usr/share/doc/procps/changelog.Debian.gz
/usr/share/doc/procps/README.top.gz
/usr/share/menu
/usr/share/menu/procps
/usr/bin/snice
/usr/bin/pkill
/usr/share/man/man1/snice.1.gz
/usr/share/man/man1/pkill.1.gz
>
<!ENTITY Breton "br">
<!ENTITY Catalan "ca">
<!ENTITY Corsican "co">
<!ENTITY Czech "cs">
<!ENTITY Welsh "cy">
<!ENTITY Danish "da">
<!ENTITY German "de">
<!ENTITY Bhutani "dz">
<!ENTITY Greek "el">
<!-- <!ENTITY EnglishAmerican 'en'> --><!ENTITY EnglishAmerican "C">
<!ENTITY Esperanto "eo">
<!ENTITY Spanish "es">
<!ENTITY Estonian "et">
<!ENTITY Basque "eu">
<!ENTITY Persian "fa">
<!ENTITY Finnish "fi">
<!ENTITY Fiji "fj">
<!ENTITY Faeroese "fo">
<!ENTITY French "fr">
<!ENTITY Frisian "fy">
<!ENTITY Irish "ga">
<!ENTITY Gaelic "gd">
<!ENTITY ScotsGaelic "gd">
<!ENTITY Galician "gl">
<!ENTITY Guarani "gn">
<!ENTITY Gujarati "gu">
<!ENTITY Hausa "ha">
<!ENTITY Hindi "hi">
<!ENTITY Croatian "hr">
<!ENTITY Hungarian "hu">
<!ENTITY Armenian "hy">
<!ENTITY Interlingua "ia">
<!ENTITY Interlingue "ie">
<!ENTITY Inupiak "ik">
<!ENTITY Indonesian "in">
<!ENTITY Icelandic "is">
<!ENTITY Italian "it">
<!ENTITY Hebrew "iw">
<!ENTITY Japanese "ja">
<!ENTITY Yiddish "ji">
<!ENTITY Javanese "jw">
<!ENTITY Georgian "ka">
<!ENTITY Kazakh "kk">
<!ENTITY Greenlandic "kl">
<!ENTITY Cambodian "km">
<!ENTITY Kannada "kn">
<!ENTITY Korean "ko">
<!ENTITY Kashmiri "ks">
<!ENTITY Kurdish "ku">
<!ENTITY Kirghiz "ky">
<!ENTITY Latin "la">
<!ENTITY Lingala "ln">
<!ENTITY Laothian "lo">
<!ENTITY Lithuanian "lt">
<!ENTITY Latvian "lv">
<!ENTITY Lettish "lv">
<!ENTITY Malagasy "mg">
<!ENTITY Maori "mi">
<!ENTITY Macedonian "mk">
<!ENTITY Malayalam "ml">
<!ENTITY Mongolian "mn">
<!ENTITY Moldavian "mo">
<!ENTITY Marathi "mr">
<!ENTITY Malay "ms">
<!ENTITY Maltese "mt">
<!ENTITY Burmese "my">
<!ENTITY Nauru "na">
<!ENTITY Nepali "ne">
<!ENTITY Dutch "nl">
<!ENTITY Norwegian "no">
<!ENTITY Occitan "oc">
<!ENTITY Afan "om">
<!ENTITY Oromo "om">
<!ENTITY Oriya "or">
<!ENTITY Punjabi "pa">
<!ENTITY Polish "pl">
<!ENTITY Pushto "ps">
<!ENTITY Pashto "ps">
<!ENTITY Portuguese "pt">
<!ENTITY Quechua "qu">
<!ENTITY Rhaeto-Romance "rm">
<!ENTITY Kirundi "rn">
<!ENTITY Romanian "ro">
<!ENTITY Russian "ru">
<!ENTITY Kinyarwanda "rw">
<!ENTITY Sanskrit "sa">
<!ENTITY Sindhi "sd">
<!ENTITY Sangro "sg">
<!ENTITY Serbo-Croatian "sh">
<!ENTITY Singhalese "si">
<!ENTITY Slovak "sk">
<!ENTITY Slovenian "sl">
<!ENTITY Samoan "sm">
<!ENTITY Shona "sn">
<!ENTITY Somali "so">
<!ENTITY Albanian "sq">
<!ENTITY Serbian "sr">
<!ENTITY Siswati "ss">
<!ENTITY Sesotho "st">
<!ENTITY Sudanese "su">
<!ENTITY Swedish "sv">
<!ENTITY Swahili "sw">
<!ENTITY Tamil "ta">
<!ENTITY Tegulu "te">
<!ENTITY Tajik "tg">
<!ENTITY Thai "th">
<!ENTITY Tigrinya "ti">
<!ENTITY Turkmen "tk">
<!ENTITY Tagalog "tl">
<!ENTITY Setswana "tn">
<!ENTITY Tonga "to">
<!ENTITY Turkish "tr">
<!ENTITY Tsonga "ts">
<!ENTITY Tatar "tt">
<!ENTITY Twi "tw">
<!ENTITY Ukrainian "uk">
<!ENTITY Urdu "ur">
<!ENTITY Uzbek "uz">
<!ENTITY Vietnamese "vi">
<!ENTITY Volapuk "vo">
<!ENTITY Wolof "wo">
<!ENTITY Xhosa "xh">
<!ENTITY Yoruba "yo">
<!ENTITY Chinese "zh">
<!ENTITY Zulu "zu">
<!ENTITY % cdo-C SYSTEM "../../../libs/cdo-C.ent">
<!-- COMMON DOC OBJECTS --><!ENTITY copyright SYSTEM "../common/C/copyright.xml">
<!ENTITY conventions SYSTEM "../common/C/conventions.xml">
<!ENTITY feedback SYSTEM "../common/C/feedback.xml">
<!ENTITY publisher SYSTEM "../common/C/publisher.xml">
<!ENTITY disclaimer SYSTEM "../common/C/disclaimer.xml">
<!ENTITY inline-ubuntu-icon SYSTEM "../common/C/inlinemediaobject-ubuntu-icon.xml">
<!ENTITY inline-ubuntu-icon-header SYSTEM "../common/C/inlinemediaobject-ubuntu-icon-header.xml">
<!ENTITY relative-ubuntu-icon SYSTEM "../common/C/mediaobject-relative-ubuntu-icon.xml">
<!ENTITY ubuntu-icon SYSTEM "../common/C/mediaobject-ubuntu-icon.xml">
<!ENTITY gpl SYSTEM "../common/C/gpl.xml">
<!ENTITY fdl SYSTEM "../common/C/fdl.xml">
<!ENTITY cc-by-sa SYSTEM "../common/C/ccbysa.xml">
<!ENTITY licenses SYSTEM "../common/C/licenses.xml">
<!ENTITY legalnotice SYSTEM "../common/C/legalnotice.xml">
<!ENTITY klegalnotice SYSTEM "../kubuntu/libs/legalnotice.xml">
<!ENTITY % gnome-menus-C SYSTEM "../../../ubuntu/libs/gnome-menus-C.ent">
<!-- MENUS --><!-- Please keep entries alphabetical, it makes them much easiermr

---

### Post by Rocket2DMn on 2008-02-12
Looks like either the list got cut off, or the forums just cut it.  Either way, let's get rid of the list file, reconfigure dpkg, then try to update/upgrade
```
sudo mv /var/lib/dpkg/info/procps.list /var/lib/dpkg/info/procps.list.bak
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by animeh on 2008-02-13
After completing what you asked here is the following: 

 sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libpq5 linux-headers-2.6.22-14 linux-headers-2.6.22-14-generic linux-image-2.6.22-14-server
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/27.3MB of archives.
After unpacking 77.8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: serious warning: files list file for package `procps' missing, assuming package has no files currently installed.
98737 files and directories currently installed.)
Preparing to replace linux-image-2.6.22-14-server 2.6.22-14.51 (using .../linux-image-2.6.22-14-server_2.6.22-14.52_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.22-14-server ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-server
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Preparing to replace libpq5 8.2.6-0ubuntu0.7.10.1 (using .../libpq5_8.3.0-1~gutsy1_i386.deb) ...
Unpacking replacement libpq5 ...
Preparing to replace linux-headers-2.6.22-14 2.6.22-14.51 (using .../linux-headers-2.6.22-14_2.6.22-14.52_all.deb) ...
Unpacking replacement linux-headers-2.6.22-14 ...
Preparing to replace linux-headers-2.6.22-14-generic 2.6.22-14.51 (using .../linux-headers-2.6.22-14-generic_2.6.22-14.52_i386.deb) ...
Unpacking replacement linux-headers-2.6.22-14-generic ...
Setting up linux-image-2.6.22-14-server (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-server
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.51 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-server
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up libpq5 (8.3.0-1~gutsy1) ...

Setting up linux-headers-2.6.22-14 (2.6.22-14.52) ...
Setting up linux-headers-2.6.22-14-generic (2.6.22-14.52) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place


It works thanks a million!

---

### Post by Rocket2DMn on 2008-02-13
I thought you might get an error like that, so if you still get it, reinstall the package
```
sudo apt-get install --reinstall procps
```
Let's not let that error go unfixed.

---

### Post by animeh on 2008-02-13
ok I have reinstlled the file.

Thank You for helping me

---

