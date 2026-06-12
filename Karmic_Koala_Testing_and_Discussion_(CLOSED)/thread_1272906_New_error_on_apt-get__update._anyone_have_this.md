---
title: "New error on apt-get  update. anyone have this?"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-09-22
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apparmor apparmor-utils binutils gnome-session gnome-session-bin initscripts
  libapparmor-perl libapparmor1 libgudev-1.0-0 libpango1.0-0
  libpango1.0-common libudev0 python-central rsyslog sysv-rc sysvinit-utils
  udev upstart
18 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4707kB of archives.
After this operation, 102kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `initramfs-tools' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by philinux on 2009-09-23
Slightly moved on. Now getting this.
```

Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up udev (147~-4) ...
udev start/running, process 3313
/usr/sbin/update-initramfs: 1: &#3956;&#3851;: not found
/usr/sbin/update-initramfs: 2: Extended_description-el.utf-8:: not found
/usr/sbin/update-initramfs: 3: Extended_description-eo.utf-8:: not found
/usr/sbin/update-initramfs: 4: Extended_description-es.utf-8:: not found
/usr/sbin/update-initramfs: 7: Syntax error: Unterminated quoted string
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by dvlchd3 on 2009-09-23
Try:
```

sudo dpkg --configure -a

```

---

### Post by philinux on 2009-09-23
Tried all that.

Fubar I reckon. Reinstalling alpha6. :P

---

### Post by dinxter on 2009-09-23
i'd try a quick reinstall of init bits to see if it helps if you havent already
$ apt-get install --reinstall initscripts initramfs-tools

---

### Post by philinux on 2009-09-23
Thanks fo reply dinxter. Just busy burning iso from Jaunty but I chrooted in and tried that.

```
sudo apt-get install --reinstall initscripts initramfs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 158kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://archive.ubuntu.com karmic/main initscripts 2.87dsf-4ubuntu7 [73.8kB]
Get: 2 http://archive.ubuntu.com karmic/main initramfs-tools 0.92bubuntu49 [83.9kB]
Fetched 158kB in 0s (248kB/s)        
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `initramfs-tools' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by dinxter on 2009-09-23
strange, i just cant reproduce, maybe try direct download of the package or a slightly earlier version
[http://archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/](http://archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/)

---

### Post by philinux on 2009-09-23
Yes already tried that. Something really messed up. Iso half burnt so reinstall should fix it and let me test the install cd too.

Should be up and running within an hour. More coffee. :P

---

### Post by dinxter on 2009-09-23
/var/lib/dpkg/info/initramfs-tools.list
should look like this
```
/.
/etc
/etc/initramfs-tools
/etc/initramfs-tools/scripts
/etc/initramfs-tools/scripts/init-bottom
/etc/initramfs-tools/scripts/init-premount
/etc/initramfs-tools/scripts/init-top
/etc/initramfs-tools/scripts/local-bottom
/etc/initramfs-tools/scripts/local-premount
/etc/initramfs-tools/scripts/local-top
/etc/initramfs-tools/scripts/nfs-bottom
/etc/initramfs-tools/scripts/nfs-premount
/etc/initramfs-tools/scripts/nfs-top
/etc/initramfs-tools/hooks
/etc/initramfs-tools/conf.d
/etc/initramfs-tools/initramfs.conf
/etc/initramfs-tools/update-initramfs.conf
/usr
/usr/share
/usr/share/initramfs-tools
/usr/share/initramfs-tools/conf.d
/usr/share/initramfs-tools/hooksconf.d
/usr/share/initramfs-tools/modules.d
/usr/share/initramfs-tools/init
/usr/share/initramfs-tools/scripts
/usr/share/initramfs-tools/scripts/init-top
/usr/share/initramfs-tools/scripts/init-top/keymap
/usr/share/initramfs-tools/scripts/init-top/all_generic_ide
/usr/share/initramfs-tools/scripts/init-top/framebuffer
/usr/share/initramfs-tools/scripts/local-premount
/usr/share/initramfs-tools/scripts/local-premount/resume
/usr/share/initramfs-tools/scripts/nfs
/usr/share/initramfs-tools/scripts/local
/usr/share/initramfs-tools/scripts/functions
/usr/share/initramfs-tools/scripts/init-premount
/usr/share/initramfs-tools/scripts/init-premount/blacklist
/usr/share/initramfs-tools/scripts/local-top
/usr/share/initramfs-tools/hooks
/usr/share/initramfs-tools/hooks/thermal
/usr/share/initramfs-tools/hooks/compcache
/usr/share/initramfs-tools/hooks/kernelextras
/usr/share/initramfs-tools/hook-functions
/usr/share/initramfs-tools/modules
/usr/share/doc
/usr/share/doc/initramfs-tools
/usr/share/doc/initramfs-tools/HACKING
/usr/share/doc/initramfs-tools/TODO
/usr/share/doc/initramfs-tools/copyright
/usr/share/doc/initramfs-tools/examples
/usr/share/doc/initramfs-tools/examples/modules
/usr/share/doc/initramfs-tools/examples/example_script
/usr/share/doc/initramfs-tools/examples/example_hook
/usr/share/doc/initramfs-tools/examples/example_hook_cpiogz
/usr/share/doc/initramfs-tools/changelog.gz
/usr/share/doc/initramfs-tools/NEWS.Debian.gz
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/initramfs-tools.8.gz
/usr/share/man/man8/update-initramfs.8.gz
/usr/share/man/man8/mkinitramfs.8.gz
/usr/share/man/man8/mkinitramfs-kpkg.8.gz
/usr/share/man/man5
/usr/share/man/man5/initramfs.conf.5.gz
/usr/share/man/man5/update-initramfs.conf.5.gz
/usr/share/bug
/usr/share/bug/initramfs-tools
/usr/share/bug/initramfs-tools/script
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/initramfs-tools
/usr/sbin
/usr/sbin/mkinitramfs
/usr/sbin/mkinitramfs-kpkg
/usr/sbin/update-initramfs
/var
/var/lib
/var/lib/initramfs-tools
```

---

### Post by philinux on 2009-09-23
LOL pmsl. Well that explains it then.

```
cat var/lib/dpkg/info/initramfs-tools.list
ile}&#65292;&#19988;&#24456;&#26126;&#39023;&#24471;&#26377;&#20854;&#23427;&#30340;&#22871;&#20214;&#22312;&#23433;&#35037;&#24460;&#20063;&#26371;&#29986;&#29983;&#21516;&#19968;&#27284;&#26696;&#12290;&#35531;&#21521;&#25552;&#20379;&#20102; ${hashfile} &#30340;&#22871;&#20214;&#20043;&#31649;&#29702;&#32773;&#22238;&#22577;&#36889;&#21839;&#38988;&#12290;\n\n&#30452;&#33267;&#35442;&#21839;&#38988;&#35299;&#27770;&#20043;&#21069;&#65292;${xxpell} &#23559;&#28961;&#27861;&#21644; ${hashfile} &#19968;&#36215;&#25645;&#37197;&#20351;&#29992;&#12290;
Type: note
Owners: dictionaries-common/ispell-autobuildhash-message

Name: dictionaries-common/move_old_usr_dict
Default: true
Description: Move non-FHS stuff under /usr/dict to /usr/dict-pre-FHS?
Description-ar.utf-8: &#1606;&#1602;&#1604; &#1605;&#1575;&#1607;&#1608; &#1604;&#1610;&#1587; FHS &#1590;&#1605;&#1606; /usr/dict &#1573;&#1604;&#1609; /usr/dict-pre-FHS&#1567;
Description-ast.utf-8: ¿Mover elementos non FHS de /usr/dict a /usr/dict-pre-FHS?
Description-bg.utf-8: &#1044;&#1072; &#1089;&#1077; &#1087;&#1088;&#1077;&#1084;&#1077;&#1089;&#1090;&#1080; &#1083;&#1080; &#1074;&#1089;&#1080;&#1095;&#1082;&#1086;, &#1082;&#1086;&#1077;&#1090;&#1086; &#1085;&#1077; &#1086;&#1090;&#1075;&#1086;&#1074;&#1072;&#1088;&#1103; &#1085;&#1072; FHS, &#1086;&#1090; /usr/dict &#1074; /usr/dict-pre-FHS?
Description-bn.utf-8: /usr/dict &#2447;&#2480; &#2472;&#2472;-FHS &#2460;&#2495;&#2472;&#2495;&#2488;&#2474;&#2468;&#2509;&#2480; /usr/dict-pre-FHS &#2447; &#2488;&#2480;&#2494;&#2472;&#2507; &#2489;&#2476;&#2503;?
Description-bs.utf-8: Premjestiti non-FHS stvari pod /usr/dict na /usr/dict-pre-FHS?
Description-ca.utf-8: Voleu moure les coses no FHS de /usr/dict a /usr/dict-pre-FHS?
Description-cs.utf-8: P&#345;esunout nekompatibilní v&#283;ci z /usr/dict do /usr/dict-pre-FHS?
Description-da.utf-8: Flyt ikke-FHS-ting under /usr/dict til /usr/dict-pre-FHS?
Description-de.utf-8: Nicht-FHS-Material aus /usr/dict nach /usr/dict-pre-FHS verschieben?
Description-dz.utf-8: /usr/dict to /usr/dict-pre-FHS &#3936;&#3964;&#3906;&#3851;&#3939;&#3956;&#3851; &#3944;&#3962;&#3925;&#3954;&#3851;&#3944;&#3962;&#3909;&#3954;&#3851;&#3944;&#3962;&#3942;&#3954;&#3851;&#3928;&#3962;&#3923;&#3851;&#3928;&#3954;&#3851;&#3930;&#3956;&#3851; &#3942;&#4004;&#3964;&#3851;&#3926;&#3940;&#3956;&#3921;&#3851;&#3936;&#3926;&#3921;&#3851;&#3923;&#3954;&#3851;&#3944;&#3954;&#3923;&#3851;&#3923;?
Description-el.utf-8: &#925;&#945; &#956;&#949;&#964;&#945;&#966;&#949;&#961;&#952;&#959;&#973;&#957; &#959;&#964;&#953;&#948;&#942;&#960;&#959;&#964;&#949; &#956;&#951; &#963;&#965;&#956;&#946;&#945;&#964;&#972; &#956;&#949; FHS &#945;&#960;&#972; &#964;&#959; /usr/dict &#963;&#964;&#959; /usr/dict-pre-FHS;
Description-eo.utf-8: &#264;u oni movas 'non-FHS'-dosierojn el '/usr/dict' al '/usr/dict-pre-FHS'?
Description-es.utf-8: ¿Mover elementos no FHS de "/usr/dict" a "/usr/dict-pre-FHS"?
Description-eu.utf-8: Eraman  '/usr/dict'-eko non-FHS '/usr/dict-pre-FHS'-ra?
Description-fi.utf-8: Siirretäänkö hakemistosta /usr/dict ei-FHS:n mukainen tauhka hakemistoon /usr/dict-pre-FHS?
Description-fr.utf-8: Faut-il déplacer les objets non conformes au FHS*?
Description-gl.utf-8: ¿Mover as cousas non FHS de /usr/dict a /usr/dict-pre-FHS?
Description-he.utf-8: &#1492;&#1494;&#1494; &#1491;&#1489;&#1512;&#1497;&#1501; &#1513;&#1488;&#1497;&#1504;&#1501; FHS &#1489;-/usr/dict&#1500;- /usr/dict-pre-FHS?
Description-hu.utf-8: Áttegyük a /usr/dict könyvtár nem-FHS anyagait a /usr/dict-pre-FHS alá?
Description-id.utf-8: Pindahkan berkas-berkas non-FHS pada /usr/dict ke /usr/dict-pre-FHS?
Description-it.utf-8: Spostare i file non FHS da /usr/dict a /usr/dict-pre-FHS?
Description-ja.utf-8: /usr/dict &#12395;&#12354;&#12427;&#38750; FHS &#12398;&#12418;&#12398;&#12434; /usr/dict-pre-FHS &#12395;&#31227;&#21205;&#12375;&#12414;&#12377;&#12363;?
```

---

### Post by dinxter on 2009-09-23
blimey! :) maybe its a sign of more widespread breakage but you might just get away with replacing the file with the good version

---

### Post by philinux on 2009-09-23
Ok so I copied your file contents to replace the above junk. And ran previous command.

```
udo apt-get install --reinstall initscripts initramfs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/158kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 215862 files and directories currently installed.)
Preparing to replace initscripts 2.87dsf-4ubuntu7 (using .../initscripts_2.87dsf-4ubuntu7_amd64.deb) ...
Unpacking replacement initscripts ...
Processing triggers for sreadahead ...
Processing triggers for man-db ...
Setting up initscripts (2.87dsf-4ubuntu7) ...

(Reading database ... 215862 files and directories currently installed.)
Preparing to replace initramfs-tools 0.92bubuntu49 (using .../initramfs-tools_0.92bubuntu49_all.deb) ...
dpkg: error processing /var/cache/apt/archives/initramfs-tools_0.92bubuntu49_all.deb (--unpack):
 too-long line or missing newline in `/var/lib/dpkg/info/initramfs-tools.triggers'
Errors were encountered while processing:
 /var/cache/apt/archives/initramfs-tools_0.92bubuntu49_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by dinxter on 2009-09-23
heres all the dpkg scripts from the same package (working)

---

### Post by philinux on 2009-09-23
Ok I'll copy them in.

---

### Post by philinux on 2009-09-23
Ok moved on. New error. Hah same as post #2

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up udev (147~-4) ...
restart: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
/usr/sbin/update-initramfs: 1: &#3956;&#3851;: not found
/usr/sbin/update-initramfs: 2: Extended_description-el.utf-8:: not found
/usr/sbin/update-initramfs: 3: Extended_description-eo.utf-8:: not found
/usr/sbin/update-initramfs: 4: Extended_description-es.utf-8:: not found
/usr/sbin/update-initramfs: 7: Syntax error: Unterminated quoted string
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by dinxter on 2009-09-23
does seem like a lot of corrupted files on initramfs-tools. last thing i can think of without going through everything by hand is to try a purge and reinstall, maybe even a forced purge (eek!)
at your own risk, last resort, etc :)
$dpkg --purge --force-all initramfs-tools
$apt-get install initramfs-tools

---

### Post by dinxter on 2009-09-23
unless its a chroot issue, but i tried that and it worked ok here

---

### Post by philinux on 2009-09-23
Thanks for efforts. I was getting same errors when booted in so not chroot I dont think.

```
 dpkg --purge --force-all initramfs-tools
dpkg: initramfs-tools: dependency problems, but removing anyway as you requested:
 usplash depends on initramfs-tools (>= 0.40ubuntu30).
 usplash-theme-ubuntu depends on initramfs-tools (>= 0.40ubuntu30).
 apparmor depends on initramfs-tools.
 ubuntu-minimal depends on initramfs-tools.
 linux-image-2.6.31-8-generic depends on initramfs-tools (>= 0.36ubuntu6).
 linux-image-2.6.31-10-generic depends on initramfs-tools (>= 0.36ubuntu6).
 dmsetup depends on initramfs-tools.
 brltty depends on initramfs-tools (>= 0.40ubuntu30).
 kbd depends on initramfs-tools.
 linux-image-2.6.31-9-generic depends on initramfs-tools (>= 0.36ubuntu6).
 console-setup depends on initramfs-tools (>= 0.85eubuntu12).
 ntfs-3g depends on initramfs-tools.
(Reading database ... 215861 files and directories currently installed.)
Removing initramfs-tools ...
Purging configuration files for initramfs-tools ...
**dpkg: warning: while removing initramfs-tools, directory '/var/lib/initramfs-tools' not empty so not removed.**
Processing triggers for man-db ...

root@philcb-desktop:/# apt-get install initramfs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  initramfs-tools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/83.9kB of archives.
After this operation, 422kB of additional disk space will be used.
Selecting previously deselected package initramfs-tools.
(Reading database ... 215806 files and directories currently installed.)
Unpacking initramfs-tools (from .../initramfs-tools_0.92bubuntu49_all.deb) ...
[B]dpkg: error processing /var/cache/apt/archives/initramfs-tools_0.92bubuntu49_all.deb (--unpack):
 too-long line or missing newline in `/var/lib/dpkg/triggers/update-initramfs'[/B]
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/initramfs-tools_0.92bubuntu49_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@philcb-desktop:/# 
```

---

### Post by dinxter on 2009-09-23
everything says that its the actual package that corrupted, are the dpkg scripts in the /var/cache/apt/archives deb ok? very strange though

---

### Post by dinxter on 2009-09-23
i notice that apt isnt downloading the deb on install, might be a good idea to remove the cached version and let it download a fresh one

---

### Post by philinux on 2009-09-23
Ok did that.

```
rm /var/cache/apt/archives/initramfs-tools_0.92bubuntu49_all.deb

root@philcb-desktop:/# apt-get install initramfs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 83.9kB of archives.
After this operation, 422kB of additional disk space will be used.
Get: 1 http://archive.ubuntu.com karmic/main initramfs-tools 0.92bubuntu49 [83.9kB]
Fetched 83.9kB in 0s (184kB/s)       
(Reading database ... 215862 files and directories currently installed.)
Preparing to replace initramfs-tools 0.92bubuntu49 (using .../initramfs-tools_0.92bubuntu49_all.deb) ...
Unpacking replacement initramfs-tools ...
dpkg: error processing /var/cache/apt/archives/initramfs-tools_0.92bubuntu49_all.deb (--unpack):
 **too-long line or missing newline in `/var/lib/dpkg/triggers/update-initramfs**'
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/initramfs-tools_0.92bubuntu49_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@philcb-desktop:/# 
```

---

### Post by philinux on 2009-09-23
cat /var/lib/dpkg/triggers/update-initramfs

```
r/dict la /usr/droot
```

---

### Post by dinxter on 2009-09-23
whats in
/var/lib/dpkg/triggers/update-initramfs
it should be just 
initramfs-tools

---

### Post by dinxter on 2009-09-23
> **philinux said:**
> cat /var/lib/dpkg/triggers/update-initramfs

```
r/dict la /usr/droot
```
ah, more garbage :)
try replacing it with the previous message

---

### Post by philinux on 2009-09-23
:P Yeah Dinxter many thanks for the help. All fixed for now.

Where the hell did that garbage come from. I've been chrooting from jaunty to do updates.

---

### Post by dinxter on 2009-09-23
> **philinux said:**
> :P Yeah Dinxter many thanks for the help. All fixed for now.

Where the hell did that garbage come from. I've been chrooting from jaunty to do updates.

somethings gone badly wrong on a dpkg run sometime i imagine, hopefully thats it but there may be other scrambled files in the packaging system, how deep does the rabbit hole go :)
should be ok, i'm an optimistic gambling man

---

### Post by philinux on 2009-09-23
Lol,

Well I'm in karmic now and all seems to be fixed. Cheers !

And I've got my newly burnt alpha6.

---

