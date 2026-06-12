---
title: "Package broken and prevents updates."
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Toadinator on 2009-04-08
I performed an update recently and as it was installing openoffice.org-emailmerge, the whole system froze. I'm not allowed to install or update any more packages until this package is fixed or removed or something, but it won't let me do anything about it! I went into recovery mode and hit the dpkg option to see if that would fix anything, but I get a message saying something about a "recursive fault" that its fixing, but a reboot's needed or something remotely similar to that along with a bunch of unintelligible numbers and letters above it. Any advice?

---

### Post by Toadinator on 2009-04-09
bump... this is a serious problem for me, guys.

---

### Post by Therion on 2009-04-09
Open Synaptic.

Go to **Edit** and then **Fix Broken Packages**. 

Click on **Apply Marked Changes** from the menu, confirm and **Apply**.

---

### Post by Toadinator on 2009-04-09
> **Therion said:**
> Open Synaptic.

Go to **Edit** and then **Fix Broken Packages**. 

Click on **Apply Marked Changes** from the menu, confirm and **Apply**.

Same problem as before. And what I mean by my whole desktop crashing is nothing responds... at all... even ctrl+alt+backspace wont work right (freezes mid-way).

---

### Post by knattlhuber on 2009-04-10
Can you please post the error message you mentioned above that you are getting?

---

### Post by n3had on 2009-04-10
> **Toadinator said:**
> Same problem as before. And what I mean by my whole desktop crashing is nothing responds... at all... even ctrl+alt+backspace wont work right (freezes mid-way).

try this ```
sudo apt-get update

sudo apt-get -f dist-upgrade
```

---

### Post by Toadinator on 2009-04-10
> **n3had said:**
> try this ```
sudo apt-get update

sudo apt-get -f dist-upgrade
```

```
ryan@sloshy:~$ E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

---

### Post by chrisccoulson on 2009-04-11
The error message tells you how to fix it. Have you tried running what was suggested in the error message?

---

### Post by Toadinator on 2009-04-11
> **chrisccoulson said:**
> The error message tells you how to fix it. Have you tried running what was suggested in the error message?

well yeah, and again that freezes the system.

---

### Post by knattlhuber on 2009-04-11
Can you please do

```
ls /var/lib/dpkg/info | grep openoffice.org-emailmerge
```

and post the output.

---

### Post by Toadinator on 2009-04-11
> **knattlhuber said:**
> Can you please do

```
ls /var/lib/dpkg/info | grep openoffice.org-emailmerge
```

and post the output.

```
ryan@sloshy:~$ ls /var/lib/dpkg/info | grep openoffice.org-emailmerge
openoffice.org-emailmerge.list
openoffice.org-emailmerge.md5sums
openoffice.org-emailmerge.postinst
openoffice.org-emailmerge.preinst
openoffice.org-emailmerge.prerm
ryan@sloshy:~$
```

...don't ask about the "sloshy" part.

---

### Post by Toadinator on 2009-04-11
Oh and by the way, the error when on recovery mode says "Fixing recursive fault but reboot is needed!".

---

### Post by knattlhuber on 2009-04-11
Great, thank you.
openoffice.org-emailmerge.prerm is a script that is run when removing the openoffice.org-emailmerge package. I suspect that there's something in the script that makes your computer crash when you try to remove the package. Can you do
```
cat /var/lib/dpkg/info/openoffice.org-emailmerge.prerm
```
and post the output?

---

### Post by Toadinator on 2009-04-11
```
ryan@sloshy:~$ cat /var/lib/dpkg/info/openoffice.org-emailmerge.prerm
#!/bin/sh

set -e

# prerm script for openoffice.org-emailmerge

THIS_PACKAGE=openoffice.org-emailmerge
THIS_SCRIPT=prerm

LIBSUFFIX=li
PLATFORMID=linux_x86

# vim:set ai et sts=2 sw=2 tw=0:

# Query the terminal to establish a default number of columns to use for
# displaying messages to the user.  This is used only as a fallback in the
# event the COLUMNS variable is not set.  ($COLUMNS can react to SIGWINCH while
# the script is running, and this cannot, only being calculated once.)
DEFCOLUMNS=$(stty size 2> /dev/null | awk '{print $2}') || true
if ! expr "$DEFCOLUMNS" : "[[:digit:]]\+$" > /dev/null 2>&1; then
  DEFCOLUMNS=80
fi

message() {
	echo "$*" | fmt -t -w ${COLUMNS:-$DEFCOLUMNS} >&2
}

# Prepare to move a conffile without triggering a dpkg question
prep_rm_conffile() {
    CONFFILE="$1"

    if [ -e "$CONFFILE" ]; then
        md5sum="`md5sum \"$CONFFILE\" | sed -e \"s/ .*//\"`"
        old_md5sum="`dpkg-query -W -f='${Conffiles}' $2 | grep $CONFFILE | awk '{print $2}'`"
        if [ "$md5sum" = "$old_md5sum" ]; then
            mv "$CONFFILE" "$CONFFILE.${THIS_PACKAGE}-tmp"
        fi
    fi
}

rm_conffile_commit() {
  CONFFILE="$1"

  if [ -e $CONFFILE.${THIS_PACKAGE}-tmp ]; then
    rm $CONFFILE.${THIS_PACKAGE}-tmp
  fi
}

# Remove a no-longer used conffile
rm_conffile() {
    CONFFILE="$1"

    if [ -e "$CONFFILE" ]; then
        md5sum="`md5sum \"$CONFFILE\" | sed -e \"s/ .*//\"`"
        old_md5sum="`dpkg-query -W -f='${Conffiles}' $2 | grep $CONFFILE | awk '{print $2}'`"
        if [ "$md5sum" != "$old_md5sum" ]; then
            echo "Obsolete conffile $CONFFILE has been modified by you."
            echo "Saving as $CONFFILE.dpkg-bak ..."
            mv -f "$CONFFILE" "$CONFFILE".bak
        else
            echo "Removing obsolete conffile $CONFFILE ..."
            rm -f "$CONFFILE"
        fi
    fi
}

flush_unopkg_cache() {
	/usr/lib/openoffice/program/unopkg list --shared > /dev/null 2>&1
}

remove_extension() {
  if /usr/lib/openoffice/program/unopkg list --shared $1 >/dev/null; then
    echo -n "Removing extension $1..."
    INSTDIR=`mktemp -d`
    /usr/lib/openoffice/program/unopkg remove --shared $1 \
      "-env:UserInstallation=file://$INSTDIR" \
      '-env:UNO_JAVA_JFW_INSTALL_DATA=$OOO_BASE_DIR/share/config/javasettingsunopkginstall.xml' \
      "-env:JFW_PLUGIN_DO_NOT_CHECK_ACCESSIBILITY=1"
    if [ -n $INSTDIR ]; then rm -rf $INSTDIR; fi
    echo " done."
    flush_unopkg_cache
  fi
}

add_extension() {
  echo -n "Adding extension $1..."
  INSTDIR=`mktemp -d`
  /usr/lib/openoffice/program/unopkg add --shared $1 \
    "-env:UserInstallation=file:///$INSTDIR" \
    '-env:UNO_JAVA_JFW_INSTALL_DATA=$OOO_BASE_DIR/share/config/javasettingsunopkginstall.xml' \
    "-env:JFW_PLUGIN_DO_NOT_CHECK_ACCESSIBILITY=1"
  if [ -n $INSTDIR ]; then rm -rf $INSTDIR; fi
  echo " done."
}

VER=


case "$1" in
	remove)
		remove_extension org.openoffice.legacy.mailmerge.py
	;;
esac



exit 0
ryan@sloshy:~$ 

```

---

### Post by knattlhuber on 2009-04-11
Let's move this script to your Desktop for now and then try to remove the package:

```
sudo mv openoffice.org-emailmerge.prerm ~/Desktop
sudo dpkg -r --force-all openoffice.org-emailmerge

```

Mind you, that error message "Fixing recursive fault but reboot is needed" indicates that the problem probably lies elsewhere (a kernel module). Do you have another kernel installed that you can fall back on (i.e. is there another kernel in the grub menu)?

---

### Post by Toadinator on 2009-04-11
> **knattlhuber said:**
> Let's move this script to your Desktop for now and then try to remove the package:

```
sudo mv openoffice.org-emailmerge.prerm ~/Desktop
sudo dpkg -r --force-all openoffice.org-emailmerge

```

Mind you, that error message "Fixing recursive fault but reboot is needed" indicates that the problem probably lies elsewhere (a kernel module). Do you have another kernel installed that you can fall back on (i.e. is there another kernel in the grub menu)?

Thank you SO MUCH! Moving the remove script worked beautifully and now I can upgrade my packages! You are a saint, sir, you really are!

---

### Post by spike_naples on 2009-04-12
Could it be that you have a hardware problem? I had a similar incident before and found out I had a faulty motherboard. I bought a new one since and have happily been using Ubuntu.

---

