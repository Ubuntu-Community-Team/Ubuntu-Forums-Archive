---
title: "problem mount/unmount in koala"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nossie on 2009-10-27
Hi there,

with the recent updates to koala I seem to have lost the ability to mount or unmount drives without being root?

I cant get rid of the ones from the desktop and everytime I try and mount using diskmounter it asks for my root password...

any ideas how this happened or how to fix it?


thanks,
Ian.

---

### Post by fancypiper on 2009-10-27
Add the user to the groups disk and cdrom.

System -> Administration -> Users and Groups -> User Priviledges tab check Access external storage devices and use CDROM

---

### Post by Nossie on 2009-10-27
> **fancypiper said:**
> Add the user to the groups disk and cdrom.

System -> Administration -> Users and Groups -> User Priviledges tab check Access external storage devices and use CDROM

that was already the case :( no cigar

---

### Post by fancypiper on 2009-10-27
Post your /etc/group file

---

### Post by dadedo123 on 2009-10-27
Why is there  mount/unmount button and a safely remove hard-drive? I preferred the unmount button. So are they both going to stay?

---

### Post by Nossie on 2009-10-27
Strange... though check out the screen cap ... it IS ticked



```
 root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:ian,ebox
tty:x:5:
disk:x:6:        <<< wtf?
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:ian
fax:x:21:ian
voice:x:22:
cdrom:x:24:ian
floppy:x:25:
tape:x:26:ian
sudo:x:27:
audio:x:29:pulse,ian
dip:x:30:ian
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:ian
sasl:x:45:
plugdev:x:46:ian
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:ian
nvram:x:105:
fuse:x:106:ian
ssl-cert:x:107:postgres
lpadmin:x:108:ian
crontab:x:109:
mlocate:x:110:
ssh:x:111:
avahi-autoipd:x:112:
gdm:x:113:
netdev:x:114:ian
pulse:x:115:
pulse-access:x:116:
saned:x:118:
messagebus:x:119:
polkituser:x:120:
avahi:x:121:
haldaemon:x:122:
admin:x:123:ian
ian:x:1000:
sambashare:x:124:ian
boinc:x:126:
clamav:x:127:
postgres:x:128:
ebox:x:129:
openldap:x:130:
couchdb:x:117:
rtkit:x:131:


```

---

### Post by fancypiper on 2009-10-27
Hand edit that file and save it.

sudo nano /etc/group

---

### Post by Nossie on 2009-10-27
thanks but that still did not work :(

I also tried unticking the box in user privs saving and then ticking it again but that has not worked either...

Can I ask... the group 'disk' is root supposed to be a member? (it's not)

thanks,
Ian.

---

### Post by fancypiper on 2009-10-27
No, root can do anything the sys admin wants to do.

I would try rebooting and see if it is working.

---

### Post by Nossie on 2009-10-27
I tried that... and then again after seeing your msg....


still the same :(

**EDIT** in properties under each drive it says "the permissions of "x" could not be determined"

and I have two 'removable drives and media' programs in prefs

---

### Post by fancypiper on 2009-10-27
I'm out of ideas.  Anyone else have any suggestions?

---

### Post by nzwrx on 2009-10-28
Bump! I have the same problem on my eee pc 901 running the Beta and now RC of Karmic. I did a fresh install of Karmic both times. SD card in the slot mounts automatically, but the 16GB partition built into the machine does not mount without root privs.

---

