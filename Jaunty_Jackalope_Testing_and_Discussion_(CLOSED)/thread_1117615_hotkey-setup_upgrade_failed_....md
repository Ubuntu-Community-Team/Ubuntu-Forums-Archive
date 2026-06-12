---
title: "hotkey-setup upgrade failed ..."
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zika on 2009-04-06
hotkey-setup upgrade several minutes ago ended with some errors (due to some "fi" expected ...) (amd_64) not a big deal (i hope), but just to report ... :)

```
The following partially installed packages will be configured:
  hotkey-setup 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up hotkey-setup (0.1-23ubuntu10) ...
/etc/init.d/hotkey-setup: 47: Syntax error: ";;" unexpected (expecting "fi")
invoke-rc.d: initscript hotkey-setup, action "start" failed.
dpkg: error processing hotkey-setup (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 hotkey-setup
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up hotkey-setup (0.1-23ubuntu10) ...
/etc/init.d/hotkey-setup: 47: Syntax error: ";;" unexpected (expecting "fi")
invoke-rc.d: initscript hotkey-setup, action "start" failed.
dpkg: error processing hotkey-setup (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 hotkey-setup
```

---

### Post by jmmL on 2009-04-06
I can confirm this. Has anyone filed a bug? 

Again, not a big deal though.

---

### Post by Justin Trouble on 2009-04-06
> **jmmL said:**
> I can confirm this. Has anyone filed a bug? 

Again, not a big deal though.

Yes, it's been reported: [https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/356157](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/356157)

---

### Post by philinux on 2009-04-06
Simple fix in script works.

---

### Post by rudenko_ruslan on 2009-04-06
[https://launchpad.net/ubuntu/jaunty/+source/hotkey-setup/0.1-23ubuntu11](https://launchpad.net/ubuntu/jaunty/+source/hotkey-setup/0.1-23ubuntu11)

Fixed?

---

### Post by zika on 2009-04-06
> **rudenko_ruslan said:**
> [https://launchpad.net/ubuntu/jaunty/+source/hotkey-setup/0.1-23ubuntu11](https://launchpad.net/ubuntu/jaunty/+source/hotkey-setup/0.1-23ubuntu11)
Fixed?
in file */etc/init.d/hotkey-setup* in line 47 add *fi* before ;; (closing of if-fi section) and redo *sudo apt-get update* ...
it should look like (if I'm right):
```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          hotkey-setup
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      1
# Short-Description: Set up laptop keys to generate keycodes.
### END INIT INFO

test -x /usr/sbin/dumpkeycodes || exit 0

xorg_driver() {
    vendor=$(lspci | grep VGA | head -1)
    case $vendor in
    *Intel*)
        driver=intel
        ;;
    *AMD*|*ATI*)
        driver=ati
        ;;
    esac
    echo $driver
}

do_video () {
    VIDEO=`xorg_driver`
    case $VIDEO in
    intel|ati)
        for x in /proc/acpi/video/*/DOS; do
        if [ -e "$x" ]; then
            echo -n 7 >$x;
        fi
        done
    ;;
    esac
}

case "$1" in
    start)

# This entire block does nothing on desktops right now
    if laptop-detect; then

    do_video
    
    fi**[COLOR=Red]<-----------this is the one ...[/COLOR]**
    ;;
    restart|force-reload)
    $0 stop || true
    $0 start
    ;;
esac

exit 0
```

---

### Post by emarkay on 2009-04-06
Also see this - just a FYI.
I presume it will be eventually autocirrected or do we need to do the fix as above?

---

### Post by amano on 2009-04-06
Hmm. I manually downloaded the "fixed" .deb file, but that didn't install either.

---

### Post by OrangeCrate on 2009-04-06
Have patience, it will correct itself with a future update...

---

### Post by Mr. Picklesworth on 2009-04-06
*Sigh* what ever happened to testing packages before uploading?


Thanks for the fix, Zika :)

---

### Post by novafluxx on 2009-04-06
Same bug here

---

### Post by zika on 2009-04-06
it just got repaired and available for upgrade ... :)

---

### Post by amano on 2009-04-06
> **OrangeCrate said:**
> Have patience, it will correct itself with a future update...

I wouldn't bet on this. The corrected package IS already uploaded. But it doesn't show up until after /etc/inid.d/hotkey-setup was edited manually (as suggested above).

---

### Post by kansasnoob on 2009-04-06
Well I had manually applied the patch and all seemed well but I then saw that the "patched version?" has now shown up in updates but I get this error:

[ATTACH]108889[/ATTACH]

So I need to do a bit more investigating. Maybe revert the patched file to it's original config???????????

Dunno yet.

I filed a new bug report:

[https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/356428](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/356428)

I may be away from my desk for a few hours!

---

### Post by nowardev on 2009-04-06
have you added fi?

---

### Post by OrangeCrate on 2009-04-06
> **amano said:**
> **I wouldn't bet on this**. The corrected package IS already uploaded. But it doesn't show up until after /etc/inid.d/hotkey-setup was edited manually (as suggested above).

I would. Do you really think that the final will go out with the new user having to manually update a file, before everything works on the upgrade? It will be fixed in due time. If you go to the launchpad page on it, and scroll down, you'll see that's it's already been assigned.

Edit:

It's done.

Steve Langasek:

> Sorry for this, folks. The 0.1-23ubuntu11 package corrects the original packaging error, but if you already have 0.1-23ubuntu10 installed you won't be able to upgrade to it. The 0.1-23ubuntu12 version will take care of letting you upgrade from the broken package if you have it installed; this has just been uploaded, so should become available from mirrors starting in** a little over an hour from now.**

[https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/356157](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/356157)

This ^ was posted 24 minutes ago, as I post this. As I said, just wait for it.

---

### Post by excogitation on 2009-04-06
> **zika said:**
> in file */etc/init.d/hotkey-setup* in line 47 add *fi* before ;; (closing of if-fi section) and redo *sudo apt-get update* ...


Just wanted to say thanks.

---

### Post by OrangeCrate on 2009-04-06
> **amano said:**
> **I wouldn't bet on this.** The corrected package IS already uploaded. But it doesn't show up until after /etc/inid.d/hotkey-setup was edited manually (as suggested above).

Referencing my previous post, 0.1-23ubuntu12 is now available for download through either the command line, or Update Manager.

Enjoy.

---

