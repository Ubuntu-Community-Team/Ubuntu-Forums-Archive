---
title: "apt stops reading packages list with no error warning"
date: 2015-07-26
forum: MINT
---

### Post by heikosch on 2015-07-26
I'm running Mint 13 32 Bit (12.04.1) and since today I can't upgrade my packages nor can I install new ones.
It is reading my packages list. In the end it prompts "Paketlisten werden gelesen..." It counts until 69% and then suddenly stops.
Also Synaptic couldn't be started any more. Mint Update still works.
I tried to clean apt.
```
apt-get clean
``` 
I also tried:
```
apt-get install -f
```
... but to no avail ;(

When I enter terminal mode (Strg Alt F1) I'm greeted with the message 
```
"8 packages can be updated
0 updates are security updates"
```

df -h shows me this:
```
df: »/root/.gvfs“: Keine Berechtigung
Dateisystem    Größe Benutzt Verf. Verw% Eingehängt auf
/dev/sda5        58G    8,5G   47G   16% /
udev            1,5G    8,0K  1,5G    1% /dev
tmpfs           303M    1,1M  302M    1% /run
none            5,0M       0  5,0M    0% /run/lock
none            1,5G    228K  1,5G    1% /run/shm
/dev/sda6        42G     33G  6,3G   84% /home

```

```
heiko@heiko-5610 ~ $ df -h | grep ^\/devdf: »/root/.gvfs“: Keine Berechtigung
/dev/sda5        58G    8,5G   47G   16% /
/dev/sda6        42G     33G  6,3G   84% /home


```

Recently upgrade packages:
```

heiko@heiko-5610 ~ $ awk '$3~/^upgrade$/ {print $4;}' /var/log/dpkg.log
libnss3-1d
libnss3
google-chrome-stable
libcupsfilters1
libwmf0.2-7-gtk
libwmf0.2-7
virtualbox-4.3
bind9-host
dnsutils
libisc83
libdns81
libisccc80
libisccfg82
liblwres80
libbind9-80
firefox
adobe-flash-properties-gtk
adobe-flashplugin
cups-filters
firefox-locale-de
firefox-locale-en
grub-pc
grub-pc-bin
grub2-common
grub-common
linux-libc-dev
p7zip
p7zip-full
pidgin-whatsapp
unattended-upgrades
x11-utils
linux-generic
linux-image-generic
linux-headers-generic
linux-image-3.2.0-87-generic
firefox
firefox-locale-de
firefox-locale-en
google-chrome-stable
google-chrome-stable
firefox
adobe-flash-properties-gtk
adobe-flashplugin
firefox-locale-de
firefox-locale-en
thunderbird-locale-de
thunderbird-locale-en
thunderbird
thunderbird-gnome-support
thunderbird-locale-en-gb
thunderbird-locale-en-us
unetbootin
unetbootin-translations
google-chrome-stable

```

Any suggestions? Would be really appreciated ;)

---

### Post by howefield on 2015-07-26
Thread moved to the "*MINT*" forum.

---

### Post by heikosch on 2015-07-28
Uuh, here's not happening too much ...
I solved the issue according to this thread: [http://www.linuxmintusers.de/index.php?topic=28047.0](http://www.linuxmintusers.de/index.php?topic=28047.0)
I had to remove **X-SWAT** ppa! It happened to be a conflict because afterwards I had to upgrade my graphic drivers from standard ubuntu ppa.
All the best ... ):P

---

