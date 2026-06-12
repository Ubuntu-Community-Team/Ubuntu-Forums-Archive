---
title: "Unable to execute &quot;/usr/sbin/kernel-helper&quot; for last-good-boot"
date: 2009-06-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by imafatmess on 2009-06-18
Right, I can only start up in recovery mode. If I boot up under the latest kernel, 2.6.30-9 not in recovery mode, a blank screen is shown. If I then do a wee bit of button mashing... involving pressing ctrl + alt, the following is shown on the screen (sorry I can't say the buttons I pressed, I can't work it out :S):

```
init: rcS main process (1373) killed by TERM signal
init: Unable to execute "/usr/sbin/kernel-helper" for last-good-boot: No such file or directory

inir: rc6 main process (1400) killed by TERM signal
init: last-good-boot main process (1417) terminated with status 255
```

I'm guessing this should be reported as a bug... but under what? And has anyone else had this issue?

---

### Post by peterpall on 2009-07-10
It has been reported as Bug #253581: Upgrading from Grub to Grub2 removes a file that the package manager will miss, until the line ```
/usr/sbin/kernel-helper -i
``` from ```
/etc/kernel/prerm.d/last-good-boot
``` is removed.

There is still a discussion if there is a more elegant fix for the problem, but this one at least works.

(On the command line type:
```
sudo gedit /usr/sbin/kernel-helper -i
```
...and remove the line, or comment it out with a ```
#
``` character like in
```
#/usr/sbin/kernel-helper -i
```
)

---

### Post by zika on 2009-07-10
There are three occurences of (non-existing) kernel-helper:
1. /etc/kernel/prerm.d/last-good-boot (comment out all lines...)
2. /etc/event.d/last-good-boot (comment out  exec /usr/sbin/kernel-helper -u)
3. /etc/readahead/desktop (erase line /usr/sbin/kernel-helper)
...

---

