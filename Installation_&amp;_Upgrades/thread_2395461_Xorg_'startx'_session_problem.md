---
title: "Xorg? 'startx' session problem"
date: 2018-07-02
forum: Installation &amp; Upgrades
---

### Post by yarooh on 2018-07-02
Hello to Everyone,
I am on ubuntu 18.04 based on Openbox only. I have no display/login manager. I log into system by typing 'startx'. I just run sudo apt upgrade and something went wrong. Now to log in after booting up the system when I run 'startx' nothing happens - I need to press Ctrl+ C and run 'startx' several times to succeed.How can I fix this?
Thank you for advance.

---

### Post by ubfan1 on 2018-07-02
What errors show up in the /var/log/Xorg.0.log (or older log file like Xorg.1.log) ?  They should be tagged with a "EE".

---

### Post by yarooh on 2018-07-03
Thanks for reply ubfan1.
There are no any errors. Actually my problem looks the same like in post
[https://ubuntuforums.org/showthread.php?t=2395452](https://ubuntuforums.org/showthread.php?t=2395452)
what means that if I run "startx" and wait, then after 2-3 minutes the system starts up.

Presently I upgraded the kernel up to 4.17.3-041703-generic and the still after hit 'startx' I need to wait 2-3 minutes before system starts.

Does anyone have any idea how to fix this or I must do a fresh install again and do not do the upgrades on kernel?

---

### Post by Bashing-om on 2018-07-03
yarooh; Hummmm ...

Could be any number of factors .
Any hints:
```

journalctl -b -0
systemd-analyze blame
systemd-analyze critical-chain

```

what DE are you booting up ?
```

systemctl status gdm
echo $XDG_SESSION_TYPE

```

[INDENT]inquiring minds want to know
[/INDENT]

---

### Post by yarooh on 2018-07-03
Hello Bashing-om,
I have only Openbox WM and based on it I am building my DE. presently I have no any display/login manager.

systemd-analyze blame

```

          5.096s apt-daily.service
           921ms systemd-resolved.service
           872ms systemd-timesyncd.service
           599ms udisks2.service
           482ms systemd-logind.service
           379ms systemd-journal-flush.service
           376ms motd-news.service
           330ms nvidia-persistenced.service
           265ms dev-sda2.device
            96ms networkd-dispatcher.service
            90ms systemd-udev-trigger.service
            89ms upower.service
            77ms keyboard-setup.service
            55ms systemd-journald.service
            48ms ModemManager.service
            39ms apparmor.service
            37ms accounts-daemon.service
            34ms systemd-fsck@dev-disk-by\x2duuid-5611\x2dBD65.service
            34ms ufw.service
            34ms systemd-fsck@dev-disk-by\x2duuid-de2c2634\x2de397\x2d4c89\x2d94c7\x2dd5e8f3db8124.service
            32ms dev-mqueue.mount
            32ms dev-hugepages.mount
            29ms systemd-networkd.service
            29ms apport.service
            29ms user@1000.service
            28ms avahi-daemon.service
            27ms wpa_supplicant.service
            26ms grub-common.service
            25ms boot-efi.mount
            25ms systemd-tmpfiles-clean.service
            23ms systemd-remount-fs.service
            22ms rsyslog.service
            18ms systemd-modules-load.service
            17ms kmod-static-nodes.service
            17ms alsa-restore.service
            17ms systemd-tmpfiles-setup-dev.service
            16ms systemd-udevd.service
            16ms sys-kernel-debug.mount
            15ms plymouth-read-write.service
            14ms polkit.service
            12ms plymouth-quit.service
            12ms systemd-sysctl.service
            11ms dev-disk-by\x2duuid-ce34a78d\x2dcce3\x2d4568\x2d8b39\x2d29ea78b1190d.swap
             9ms home.mount
             8ms systemd-tmpfiles-setup.service
             5ms sys-kernel-config.mount
             5ms systemd-random-seed.service
             5ms sys-fs-fuse-connections.mount
             4ms ureadahead-stop.service
             4ms console-setup.service
             4ms systemd-user-sessions.service
             3ms systemd-update-utmp-runlevel.service
             3ms systemd-update-utmp.service
             2ms plymouth-quit-wait.service
             2ms setvtrgb.service

```
systemd-analyze critical-chain
```

The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @2.137s

&#9492;&#9472;udisks2.service @1.537s +599ms
  &#9492;&#9472;basic.target @1.510s
    &#9492;&#9472;sockets.target @1.509s
      &#9492;&#9472;avahi-daemon.socket @1.507s
        &#9492;&#9472;sysinit.target @1.502s
          &#9492;&#9472;systemd-timesyncd.service @628ms +872ms
            &#9492;&#9472;systemd-tmpfiles-setup.service @616ms +8ms
              &#9492;&#9472;systemd-journal-flush.service @235ms +379ms
                &#9492;&#9472;systemd-journald.service @177ms +55ms
                  &#9492;&#9472;syslog.socket @160ms
                    &#9492;&#9472;system.slice @135ms
                      &#9492;&#9472;-.slice @117ms

```

And by the way - after first boot and login whenever I log out and log in system starts strightaway.

And journalctl -b -0 is here:

[https://paste.ubuntu.com/p/GdzH3Kv96Z/plain/](https://paste.ubuntu.com/p/GdzH3Kv96Z/plain/)

I did netinstall without any DE.

In the outcome of: systemd-analyze blame there is the line shows:
26ms grub-common.service
however I removed any grub file including grub-common.
When I launched systemctl status grub-common.service- this shows that this service is loaded and active? How come?
Is it right?

---

### Post by Bashing-om on 2018-07-03
yarooh; Well ....


Are the system's packages now in a consistent state ?
Any errors:
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg -C

```

I do see a few things will bear looking into.

1st: is fsck running ... does the file system check happen at each boot ??

2nd: How did you install the nvidia driver ? And why a proprietary driver with no GUI ?

3rd: raid array ? how is it set up as we have the system screaming:
> 
lip 03 20:32:27 ubuntu udisksd[662]: failed to load module mdraid: libbd_mdraid.so.2: cannot open shared object file: No such file or directory


4th: samba: configured properly ? as we have a lot of:
> 
lip 03 20:46:22 ubuntu gvfsd[915]: mkdir failed on directory /var/cache/samba: Brak dostÄ™pu


5th: A long delay in starting the terminal - almost 5 seconds - ??
> 
lip 03 20:35:41 ubuntu systemd[818]: Started GNOME Terminal Server.
lip 03 20:40:32 ubuntu dbus-daemon[888]: [session uid=1000 pid=888] Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-m


But overall the system starts up rather quick at about 45 seconds ,,, not too shabby

[INDENT][INDENT]look'n to learn the why
[/INDENT][/INDENT]

---

### Post by yarooh on 2018-07-03
Bashing-om - thanks for reply.
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg -C

```
gone smoothly.

After I press power button on my machine there is an about 4-5 sec listings
then I reach the point where system asks me for login and password.
After I loged in, in console mode I run 'startx'
Then I need to wait approx. 2 minutes an 9 sec until my desktop show up.
Before upgrading the kernel my start up process from pressing button to display the desktop took me an about 18 seconds including entering login an password and run 'startx'.
I installed nvidia in this way:
```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo ubuntu-drivers autoinstall

```

I have a GUI - Openbox with compton etc.
I did not use raid. My partitions looks like that:
/dev/sda1 fat32 680MB esp, efi
/dev/sda2 ext4 41 GB root
/dev/sda3 swap 6G
/dev/sda4 ext4 home rest of the disk space

During the installation I am pretty sure I ticked out and did not install SAMBA. Definitely I did not do anything with samba.

This 45 seconds - it is not right time waiting to display a desktop with icons etc.

---

### Post by Bashing-om on 2018-07-03
yarooh; welll ...

I do have an 18.04 - minimal - install . Later this eve when I re-boot the system will boot back up in the minimal install and see what the differences are in my boot log.
And yes, the boot time does not reflect the time to start the GUI once the kernel has booted up.

Any hints in:
```

cat ~/.xsession-errors

```

[INDENT][INDENT]can not make a call - yet
[/INDENT][/INDENT]

---

### Post by yarooh on 2018-07-03
Bashing-om
Here You Are.
[https://paste.ubuntu.com/p/chc2kJtqYV/plain/](https://paste.ubuntu.com/p/chc2kJtqYV/plain/)

---

### Post by Bashing-om on 2018-07-03
> **yarooh said:**
> Bashing-om
Here You Are.
[https://paste.ubuntu.com/p/chc2kJtqYV/plain/](https://paste.ubuntu.com/p/chc2kJtqYV/plain/)

Ouch ! Has to be the strangest .xsession-errors file I have ever seen.

More to come in my next post as I attempt to digest what the system says .

[INDENT][INDENT]yukkie-poo
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2018-07-03
yarooh; Ho-kay ... not

Groping in the dark .. As I have never used Openbox ->
But, let's begin dissecting :)

from all the autostart errors what is in the autostart directory ?
post back:
```

ls -al /etc/xdg/autostart/

```

samba:
```

systemctl status smbd
samba-tool user list
ls -al /etc/samba/smb.conf

```

Any idea of what " Zasoby chwilowo niedost&#281;pne " refer to ? - Fatal IO error - is very UNgood .. file system/hardware issues ??
> 
pcmanfm: Fatal IO error 11 (Zasoby chwilowo niedost&#281;pne) on X server :0.


What is this .. can you translate the error for us ?
> 
Message: Nie mo&#380;na znale&#378;&#263; prawid&#322;owego pliku menu "/var/lib/openbox/debian-menu.xml"



And last but not least, as you start the display with 'startx' ... anything extraordinary in the config file ?
```

cat /usr/bin/startx

```
see where the startx file points us to.


[INDENT][INDENT]who knows, how or where this will end
[/INDENT][/INDENT]

---

### Post by yarooh on 2018-07-04
Thank you Bashing-om. I really appreciate for you help.


ls -al /etc/xdg/autostart/ is:
```

razem 20
drwxr-xr-x  2 root root 4096 lip  4 12:28 .
drwxr-xr-x 12 root root 4096 cze 30 11:31 ..
-rw-r--r--  1 root root  279 cze  8  2017 gsettings-data-convert.desktop
-rw-r--r--  1 root root  242 mar 22 14:15 nvidia-settings-autostart.desktop
-rw-r--r--  1 root root  369 kwi  3 16:50 print-applet.desktop

```

systemctl status smbd is:
```

Unit smbd.service could not be found.

```

samba-tool user list is:
```

Command 'samba-tool' not found, but can be installed with:
sudo apt install samba-common-bin

```

ls -al /etc/samba/smb.conf is:
ls: no access to '/etc/samba/smb.conf': There is no such file or directory

" Zasoby chwilowo niedost&#281;pne " refer to ? - Fatal IO error  means
" Sources temporarily inaccessible " 

Message: Nie mo&#380;na znale&#378;&#263; prawid&#322;owego pliku menu "/var/lib/openbox/debian-menu.xml" means
Message: Proper menu file cannot be found "/var/lib/openbox/debian-menu.xml" - I do not think it really matters because some steps earlier I installed this debian menu and still this did not help.

And what is more, I found that after run startx I have to wait 2 minutes and a few seconds unless I type anything i.e. blalallala then system starts immediately :)

and here is my 
cat /usr/bin/startx
```

#!/bin/sh

#
# This is just a sample implementation of a slightly less primitive
# interface than xinit. It looks for user .xinitrc and .xserverrc
# files, then system xinitrc and xserverrc files, else lets xinit choose
# its default. The system xinitrc should probably do things like check
# for .Xresources files and merge them in, start up a window manager,
# and pop a clock and several xterms.
#
# Site administrators are STRONGLY urged to write nicer versions.
#

unset DBUS_SESSION_BUS_ADDRESS
unset SESSION_MANAGER
userclientrc=$HOME/.xinitrc
sysclientrc=/etc/X11/xinit/xinitrc

userserverrc=$HOME/.xserverrc
sysserverrc=/etc/X11/xinit/xserverrc
defaultclient=/usr/bin/xterm
defaultserver=/usr/bin/X
defaultclientargs=""
defaultserverargs=""
defaultdisplay=":0"
clientargs=""
serverargs=""
vtarg=""
enable_xauth=1


# Automatically determine an unused $DISPLAY
d=0
while true ; do
    [ -e "/tmp/.X$d-lock" -o -S "/tmp/.X11-unix/X$d" ] || break
    d=$(($d + 1))
done
defaultdisplay=":$d"
unset d

whoseargs="client"
while [ x"$1" != x ]; do
    case "$1" in
    # '' required to prevent cpp from treating "/*" as a C comment.
    /''*|\./''*)
 if [ "$whoseargs" = "client" ]; then
     if [ x"$client" = x ] && [ x"$clientargs" = x ]; then
  client="$1"
     else
  clientargs="$clientargs $1"
     fi
 else
     if [ x"$server" = x ] && [ x"$serverargs" = x ]; then
  server="$1"
     else
  serverargs="$serverargs $1"
     fi
 fi
 ;;
    --)
 whoseargs="server"
 ;;
    *)
 if [ "$whoseargs" = "client" ]; then
     clientargs="$clientargs $1"
 else
     # display must be the FIRST server argument
     if [ x"$serverargs" = x ] && \
   expr "$1" : ':[0-9][0-9]*$' > /dev/null 2>&1; then
  display="$1"
     else
  serverargs="$serverargs $1"
     fi
 fi
 ;;
    esac
    shift
done

# process client arguments
if [ x"$client" = x ]; then
    client=$defaultclient

    # For compatibility reasons, only use startxrc if there were no client command line arguments
    if [ x"$clientargs" = x ]; then
        if [ -f "$userclientrc" ]; then
            client=$userclientrc
        elif [ -f "$sysclientrc" ]; then
            client=$sysclientrc
        fi
    fi
fi

# if no client arguments, use defaults
if [ x"$clientargs" = x ]; then
    clientargs=$defaultclientargs
fi

# process server arguments
if [ x"$server" = x ]; then
    server=$defaultserver


    # When starting the defaultserver start X on the current tty to avoid
    # the startx session being seen as inactive:
    # "https://bugzilla.redhat.com/show_bug.cgi?id=806491"
    tty=$(tty)
    if expr match "$tty" '^/dev/tty[0-9]\+$' > /dev/null; then
        tty_num=$(echo "$tty" | grep -oE '[0-9]+$')
        vtarg="vt$tty_num -keeptty"
    fi


    # For compatibility reasons, only use xserverrc if there were no server command line arguments
    if [ x"$serverargs" = x -a x"$display" = x ]; then
 if [ -f "$userserverrc" ]; then
     server=$userserverrc
 elif [ -f "$sysserverrc" ]; then
     server=$sysserverrc
 fi
    fi
fi

# if no server arguments, use defaults
if [ x"$serverargs" = x ]; then
    serverargs=$defaultserverargs
fi

# if no vt is specified add vtarg (which may be empty)
have_vtarg="no"
for i in $serverargs; do
    if expr match "$i" '^vt[0-9]\+$' > /dev/null; then
        have_vtarg="yes"
    fi
done
if [ "$have_vtarg" = "no" ]; then
    serverargs="$serverargs $vtarg"
fi

# if no display, use default
if [ x"$display" = x ]; then
    display=$defaultdisplay
fi

if [ x"$enable_xauth" = x1 ] ; then
    if [ x"$XAUTHORITY" = x ]; then
        XAUTHORITY=$HOME/.Xauthority
        export XAUTHORITY
    fi

    removelist=

    # set up default Xauth info for this machine

    # check for GNU hostname
    if hostname --version > /dev/null 2>&1; then
        if [ -z "`hostname --version 2>&1 | grep GNU`" ]; then
            hostname=`hostname -f`
        fi
    fi

    if [ -z "$hostname" ]; then
        hostname=`hostname`
    fi

    authdisplay=${display:-:0}

    mcookie=`/usr/bin/mcookie`







    if test x"$mcookie" = x; then
        echo "Couldn't create cookie"
        exit 1
    fi
    dummy=0

    # create a file with auth information for the server. ':0' is a dummy.
    xserverauthfile=`mktemp --tmpdir serverauth.XXXXXXXXXX`
    trap "rm -f '$xserverauthfile'" HUP INT QUIT ILL TRAP KILL BUS TERM
    xauth -q -f "$xserverauthfile" << EOF
add :$dummy . $mcookie
EOF




    serverargs=${serverargs}" -auth "${xserverauthfile}


    # now add the same credentials to the client authority file
    # if '$displayname' already exists do not overwrite it as another
    # server man need it. Add them to the '$xserverauthfile' instead.
    for displayname in $authdisplay $hostname$authdisplay; do
        authcookie=`xauth list "$displayname" \
        | sed -n "s/.*$displayname[[:space:]*].*[[:space:]*]//p"` 2>/dev/null;
        if [ "z${authcookie}" = "z" ] ; then
            xauth -q << EOF
add $displayname . $mcookie
EOF
        removelist="$displayname $removelist"
        else
            dummy=$(($dummy+1));
            xauth -q -f "$xserverauthfile" << EOF
add :$dummy . $authcookie
EOF
        fi
    done
fi




xinit "$client" $clientargs -- "$server" $display $serverargs

retval=$?

if [ x"$enable_xauth" = x1 ] ; then
    if [ x"$removelist" != x ]; then
        xauth remove $removelist
    fi
    if [ x"$xserverauthfile" != x ]; then
        rm -f "$xserverauthfile"
    fi
fi





if command -v deallocvt > /dev/null 2>&1; then
    deallocvt
fi
exit $retval

```

---

### Post by VMC on 2018-07-04
Output: 'cat .xinitrc'

I'm on xfce:
```
$ cat .xinitrc
exec startxfce4

```

---

### Post by yarooh on 2018-07-04
cat ~/.xinitrc
```

#!/bin/sh

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession &
exec openbox-session 

```

cat /etc/X11/Xsession

```

#!/bin/sh
#
# /etc/X11/Xsession
#
# global Xsession file -- used by display managers and xinit (startx)

# $Id: Xsession 967 2005-12-27 07:20:55Z dnusinow $

set -e

PROGNAME=Xsession

message () {
  # pretty-print messages of arbitrary length; use xmessage if it
  # is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2
  if [ -n "$DISPLAY" ] && which xmessage > /dev/null 2>&1; then
    echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} | xmessage -center -file -
  fi
}

message_nonl () {
  # pretty-print messages of arbitrary length (no trailing newline); use
  # xmessage if it is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2;
  if [ -n "$DISPLAY" ] && which xmessage > /dev/null 2>&1; then
    echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} | xmessage -center -file -
  fi
}

errormsg () {
  # exit script with error
  message "$*" 
  exit 1
}

internal_errormsg () {
  # exit script with error; essentially a "THIS SHOULD NEVER HAPPEN" message
  # One big call to message() for the sake of xmessage; if we had two then
  # the user would have dismissed the error we want reported before seeing the
  # request to report it.
  errormsg "$*" \
           "Please report the installed version of the \"x11-common\"" \
           "package and the complete text of this error message to" \
           "<debian-x@lists.debian.org>."
}

# initialize variables for use by all session scripts

OPTIONFILE=/etc/X11/Xsession.options

SYSRESOURCES=/etc/X11/Xresources
USRRESOURCES=$HOME/.Xresources

SYSSESSIONDIR=/etc/X11/Xsession.d
USERXSESSION=$HOME/.xsession
USERXSESSIONRC=$HOME/.xsessionrc
ALTUSERXSESSION=$HOME/.Xsession
ERRFILE=$HOME/.xsession-errors

# attempt to create an error file; abort if we cannot
if (umask 077 && touch "$ERRFILE") 2> /dev/null && [ -w "$ERRFILE" ] &&
  [ ! -L "$ERRFILE" ]; then
  chmod 600 "$ERRFILE"
elif ERRFILE=$(tempfile 2> /dev/null); then
  if ! ln -sf "$ERRFILE" "${TMPDIR:=/tmp}/xsession-$USER"; then
    message "warning: unable to symlink \"$TMPDIR/xsession-$USER\" to" \
             "\"$ERRFILE\"; look for session log/errors in" \
             "\"$TMPDIR/xsession-$USER\"."
  fi
else
  errormsg "unable to create X session log/error file; aborting."
fi

# truncate ERRFILE if it is too big to avoid disk usage DoS
if [ "`stat -c%s \"$ERRFILE\"`" -gt 500000 ]; then
  T=`mktemp -p "$HOME"`
  tail -c 500000 "$ERRFILE" > "$T" && mv -f "$T" "$ERRFILE" || rm -f "$T"
fi

exec >>"$ERRFILE" 2>&1

echo "$PROGNAME: X session started for $LOGNAME at $(date)"

# sanity check; is our session script directory present?
if [ ! -d "$SYSSESSIONDIR" ]; then
  errormsg "no \"$SYSSESSIONDIR\" directory found; aborting."
fi

# Attempt to create a file of non-zero length in /tmp; a full filesystem can
# cause mysterious X session failures.  We do not use touch, :, or test -w
# because they won't actually create a file with contents.  We also let standard
# error from tempfile and echo go to the error file to aid the user in
# determining what went wrong.
WRITE_TEST=$(tempfile)
if ! echo "*" >>"$WRITE_TEST"; then
  message "warning: unable to write to ${WRITE_TEST%/*}; X session may exit" \
          "with an error"
fi
rm -f "$WRITE_TEST"

# use run-parts to source every file in the session directory; we source
# instead of executing so that the variables and functions defined above
# are available to the scripts, and so that they can pass variables to each
# other
SESSIONFILES=$(run-parts --list $SYSSESSIONDIR)
if [ -n "$SESSIONFILES" ]; then
  set +e
  for SESSIONFILE in $SESSIONFILES; do
    . $SESSIONFILE
  done
  set -e
fi

exit 0

# vim:set ai et sts=2 sw=2 tw=80:

```

---

### Post by VMC on 2018-07-04
Maybe some log files would reveal the issue. "/var/log/etc", journalctl. Look into systemctl status.

---

### Post by Bashing-om on 2018-07-04
Hummmm ......

Nothing there to point to the issues that yarooh is experiencing .

As VMC suggests, let's look into the /var/log/ files to see if there are any hints there .

[INDENT][INDENT]stumped
[INDENT][INDENT]look'n for a way forward
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by yarooh on 2018-07-04
Xorg.0.log
```

[   196.073] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[   196.073] X Protocol Version 11, Revision 0
[   196.073] Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
[   196.073] Current Operating System: Linux ubuntu 4.17.4-041704-generic #201807031235 SMP Tue Jul 3 12:37:29 UTC 2018 x86_64
[   196.073] Kernel command line: \\boot\vmlinuz-4.17.4-041704-generic ro root=UUID=806b9076-2087-4efd-af56-88b584555e3c initrd=boot\initrd.img-4.17.4-041704-generic
[   196.073] Build Date: 13 April 2018  08:07:36PM
[   196.073] xorg-server 2:1.19.6-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[   196.073] Current version of pixman: 0.34.0
[   196.073]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   196.073] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   196.073] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul  4 22:26:27 2018
[   196.076] (==) Using config file: "/etc/X11/xorg.conf"
[   196.076] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   196.078] (==) ServerLayout "Layout0"
[   196.078] (**) |-->Screen "Screen0" (0)
[   196.078] (**) |   |-->Monitor "Monitor0"
[   196.078] (**) |   |-->Device "Device0"
[   196.078] (**) |-->Input Device "Keyboard0"
[   196.078] (**) |-->Input Device "Mouse0"
[   196.078] (**) Option "Xinerama" "0"
[   196.078] (==) Automatically adding devices
[   196.078] (==) Automatically enabling devices
[   196.078] (==) Automatically adding GPU devices
[   196.078] (==) Automatically binding GPU devices
[   196.078] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   196.079] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   196.079]     Entry deleted from font path.
[   196.079] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   196.079]     Entry deleted from font path.
[   196.079] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   196.079]     Entry deleted from font path.
[   196.079] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   196.079]     Entry deleted from font path.
[   196.079] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   196.079]     Entry deleted from font path.
[   196.079] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   196.079] (==) ModulePath set to "/usr/lib/xorg/modules"
[   196.079] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   196.079] (WW) Disabling Keyboard0
[   196.079] (WW) Disabling Mouse0
[   196.080] (II) Loader magic: 0x55d12ff1e020
[   196.080] (II) Module ABI versions:
[   196.080]     X.Org ANSI C Emulation: 0.4
[   196.080]     X.Org Video Driver: 23.0
[   196.080]     X.Org XInput driver : 24.1
[   196.080]     X.Org Server Extension : 10.0
[   196.080] (++) using VT number 1

[   196.082] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_31
[   196.082] (II) xfree86: Adding drm device (/dev/dri/card0)
[   196.083] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 11 paused 0
[   196.085] (**) OutputClass "nvidia" ModulePath extended to "/usr/lib/x86_64-linux-gnu/nvidia/xorg,/usr/lib/xorg/modules"
[   196.087] (--) PCI:*(0:3:0:0) 10de:13c2:1462:3160 rev 161, Mem @ 0xee000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[   196.087] (II) LoadModule: "glx"
[   196.087] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/libglx.so
[   196.128] (II) Module glx: vendor="NVIDIA Corporation"
[   196.128]     compiled for 4.0.2, module version = 1.0.0
[   196.128]     Module class: X.Org Server Extension
[   196.128] (II) NVIDIA GLX Module  396.24.02  Thu May 24 03:07:35 PDT 2018
[   196.129] (II) LoadModule: "nvidia"
[   196.129] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/nvidia_drv.so
[   196.135] (II) Module nvidia: vendor="NVIDIA Corporation"
[   196.135]     compiled for 4.0.2, module version = 1.0.0
[   196.135]     Module class: X.Org Video Driver
[   196.136] (II) NVIDIA dlloader X Driver  396.24.02  Thu May 24 02:43:15 PDT 2018
[   196.136] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   196.137] (II) systemd-logind: releasing fd for 226:0
[   196.138] (II) Loading sub module "fb"
[   196.138] (II) LoadModule: "fb"
[   196.138] (II) Loading /usr/lib/xorg/modules/libfb.so
[   196.139] (II) Module fb: vendor="X.Org Foundation"
[   196.139]     compiled for 1.19.6, module version = 1.0.0
[   196.139]     ABI class: X.Org ANSI C Emulation, version 0.4
[   196.139] (II) Loading sub module "wfb"
[   196.139] (II) LoadModule: "wfb"
[   196.139] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   196.140] (II) Module wfb: vendor="X.Org Foundation"
[   196.140]     compiled for 1.19.6, module version = 1.0.0
[   196.140]     ABI class: X.Org ANSI C Emulation, version 0.4
[   196.140] (II) Loading sub module "ramdac"
[   196.140] (II) LoadModule: "ramdac"
[   196.140] (II) Module "ramdac" already built-in
[   196.143] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   196.143] (==) NVIDIA(0): RGB weight 888
[   196.143] (==) NVIDIA(0): Default visual is TrueColor
[   196.143] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   196.143] (II) Applying OutputClass "nvidia" options to /dev/dri/card0
[   196.143] (**) NVIDIA(0): Option "Stereo" "0"
[   196.143] (**) NVIDIA(0): Option "SLI" "Off"
[   196.143] (**) NVIDIA(0): Option "MultiGPU" "Off"
[   196.143] (**) NVIDIA(0): Option "BaseMosaic" "off"
[   196.143] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration"
[   196.143] (**) NVIDIA(0): Stereo disabled by request
[   196.143] (**) NVIDIA(0): NVIDIA SLI disabled.
[   196.143] (**) NVIDIA(0): NVIDIA Multi-GPU disabled.
[   196.143] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
[   196.143] (**) NVIDIA(0): Enabling 2D acceleration
[   196.639] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:3:0:0
[   196.639] (--) NVIDIA(0):     CRT-0
[   196.639] (--) NVIDIA(0):     DFP-0 (boot)
[   196.639] (--) NVIDIA(0):     DFP-1
[   196.639] (--) NVIDIA(0):     DFP-2
[   196.639] (--) NVIDIA(0):     DFP-3
[   196.639] (--) NVIDIA(0):     DFP-4
[   196.641] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 970 (GM204-A) at PCI:3:0:0 (GPU-0)
[   196.641] (--) NVIDIA(0): Memory: 4194304 kBytes
[   196.641] (--) NVIDIA(0): VideoBIOS: 84.04.36.00.f1
[   196.641] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   196.717] (--) NVIDIA(GPU-0): CRT-0: disconnected
[   196.717] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[   196.717] (--) NVIDIA(GPU-0): 
[   196.810] (--) NVIDIA(GPU-0): Idek Iiyama PL1980 (DFP-0): connected
[   196.810] (--) NVIDIA(GPU-0): Idek Iiyama PL1980 (DFP-0): Internal TMDS
[   196.810] (--) NVIDIA(GPU-0): Idek Iiyama PL1980 (DFP-0): 330.0 MHz maximum pixel clock
[   196.810] (--) NVIDIA(GPU-0): 
[   196.810] (--) NVIDIA(GPU-0): DFP-1: disconnected
[   196.810] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[   196.810] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[   196.810] (--) NVIDIA(GPU-0): 
[   196.810] (--) NVIDIA(GPU-0): DFP-2: disconnected
[   196.810] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[   196.810] (--) NVIDIA(GPU-0): DFP-2: 960.0 MHz maximum pixel clock
[   196.810] (--) NVIDIA(GPU-0): 
[   196.810] (--) NVIDIA(GPU-0): DFP-3: disconnected
[   196.810] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[   196.810] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock
[   196.810] (--) NVIDIA(GPU-0): 
[   196.810] (--) NVIDIA(GPU-0): DFP-4: disconnected
[   196.810] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[   196.810] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[   196.810] (--) NVIDIA(GPU-0): 
[   196.812] (II) NVIDIA(0): Validated MetaModes:
[   196.812] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[   196.812] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
[   196.814] (--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
[   196.814] (--) NVIDIA(0):     option
[   196.814] (--) Depth 24 pixmap format is 32 bpp
[   196.815] (II) NVIDIA: Using 6144.00 MB of virtual memory for indirect memory
[   196.815] (II) NVIDIA:     access.
[   196.817] (II) NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
[   196.817] (II) NVIDIA(0):     may not be running or the "AcpidSocketPath" X
[   196.817] (II) NVIDIA(0):     configuration option may not be set correctly.  When the
[   196.817] (II) NVIDIA(0):     ACPI event daemon is available, the NVIDIA X driver will
[   196.817] (II) NVIDIA(0):     try to use it to receive ACPI event notifications.  For
[   196.817] (II) NVIDIA(0):     details, please see the "ConnectToAcpid" and
[   196.817] (II) NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
[   196.817] (II) NVIDIA(0):     Config Options in the README.
[   196.829] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[   196.873] (==) NVIDIA(0): Disabling shared memory pixmaps
[   196.873] (==) NVIDIA(0): Backing store enabled
[   196.873] (==) NVIDIA(0): Silken mouse enabled
[   196.873] (**) NVIDIA(0): DPMS enabled
[   196.874] (II) Loading sub module "dri2"
[   196.874] (II) LoadModule: "dri2"
[   196.874] (II) Module "dri2" already built-in
[   196.874] (II) NVIDIA(0): [DRI2] Setup complete
[   196.874] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[   196.874] (--) RandR disabled
[   196.876] (II) SELinux: Disabled on system
[   196.876] (II) Initializing extension GLX
[   196.876] (II) Indirect GLX disabled.
[   196.923] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   196.923] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[   196.923] (II) LoadModule: "libinput"
[   196.923] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[   196.926] (II) Module libinput: vendor="X.Org Foundation"
[   196.926]     compiled for 1.19.6, module version = 0.27.1
[   196.926]     Module class: X.Org XInput Driver
[   196.926]     ABI class: X.Org XInput driver, version 24.1
[   196.926] (II) Using input driver 'libinput' for 'Power Button'
[   196.927] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 37 paused 0
[   196.927] (**) Power Button: always reports core events
[   196.927] (**) Option "Device" "/dev/input/event2"
[   196.927] (**) Option "_source" "server/udev"
[   196.927] (II) event2  - Power Button: is tagged by udev as: Keyboard
[   196.927] (II) event2  - Power Button: device is a keyboard
[   196.927] (II) event2  - Power Button: device removed
[   196.927] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   196.927] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   196.927] (**) Option "xkb_model" "pc105"
[   196.927] (**) Option "xkb_layout" "pl"
[   196.940] (II) event2  - Power Button: is tagged by udev as: Keyboard
[   196.940] (II) event2  - Power Button: device is a keyboard
[   196.940] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   196.940] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[   196.940] (II) Using input driver 'libinput' for 'Power Button'
[   196.941] (II) systemd-logind: got fd for /dev/input/event0 13:64 fd 40 paused 0
[   196.941] (**) Power Button: always reports core events
[   196.941] (**) Option "Device" "/dev/input/event0"
[   196.941] (**) Option "_source" "server/udev"
[   196.941] (II) event0  - Power Button: is tagged by udev as: Keyboard
[   196.941] (II) event0  - Power Button: device is a keyboard
[   196.941] (II) event0  - Power Button: device removed
[   196.941] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[   196.941] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   196.941] (**) Option "xkb_model" "pc105"
[   196.941] (**) Option "xkb_layout" "pl"
[   196.942] (II) event0  - Power Button: is tagged by udev as: Keyboard
[   196.942] (II) event0  - Power Button: device is a keyboard
[   196.942] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   196.942] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[   196.942] (II) Using input driver 'libinput' for 'Sleep Button'
[   196.943] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 41 paused 0
[   196.943] (**) Sleep Button: always reports core events
[   196.943] (**) Option "Device" "/dev/input/event1"
[   196.943] (**) Option "_source" "server/udev"
[   196.943] (II) event1  - Sleep Button: is tagged by udev as: Keyboard
[   196.943] (II) event1  - Sleep Button: device is a keyboard
[   196.943] (II) event1  - Sleep Button: device removed
[   196.943] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[   196.943] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[   196.943] (**) Option "xkb_model" "pc105"
[   196.943] (**) Option "xkb_layout" "pl"
[   196.943] (II) event1  - Sleep Button: is tagged by udev as: Keyboard
[   196.943] (II) event1  - Sleep Button: device is a keyboard
[   196.944] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event14)
[   196.944] (II) No input driver specified, ignoring this device.
[   196.944] (II) This device may have been added with another device file.
[   196.944] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event15)
[   196.944] (II) No input driver specified, ignoring this device.
[   196.944] (II) This device may have been added with another device file.
[   196.944] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event16)
[   196.944] (II) No input driver specified, ignoring this device.
[   196.944] (II) This device may have been added with another device file.
[   196.945] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event17)
[   196.945] (II) No input driver specified, ignoring this device.
[   196.945] (II) This device may have been added with another device file.
[   196.945] (II) config/udev: Adding input device Holtek USB Gaming Mouse (/dev/input/event5)
[   196.945] (**) Holtek USB Gaming Mouse: Applying InputClass "libinput keyboard catchall"
[   196.945] (II) Using input driver 'libinput' for 'Holtek USB Gaming Mouse'
[   196.945] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 42 paused 0
[   196.945] (**) Holtek USB Gaming Mouse: always reports core events
[   196.945] (**) Option "Device" "/dev/input/event5"
[   196.945] (**) Option "_source" "server/udev"
[   196.946] (II) event5  - Holtek USB Gaming Mouse: is tagged by udev as: Keyboard
[   196.946] (II) event5  - Holtek USB Gaming Mouse: device is a keyboard
[   196.946] (II) event5  - Holtek USB Gaming Mouse: device removed
[   196.946] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-5/3-5:1.0/0003:04D9:A067.0001/input/input5/event5"
[   196.946] (II) XINPUT: Adding extended input device "Holtek USB Gaming Mouse" (type: KEYBOARD, id 9)
[   196.946] (**) Option "xkb_model" "pc105"
[   196.946] (**) Option "xkb_layout" "pl"
[   196.946] (II) event5  - Holtek USB Gaming Mouse: is tagged by udev as: Keyboard
[   196.946] (II) event5  - Holtek USB Gaming Mouse: device is a keyboard
[   196.947] (II) config/udev: Adding input device Holtek USB Gaming Mouse (/dev/input/event6)
[   196.947] (**) Holtek USB Gaming Mouse: Applying InputClass "libinput pointer catchall"
[   196.947] (**) Holtek USB Gaming Mouse: Applying InputClass "libinput keyboard catchall"
[   196.947] (II) Using input driver 'libinput' for 'Holtek USB Gaming Mouse'
[   196.947] (II) systemd-logind: got fd for /dev/input/event6 13:70 fd 43 paused 0
[   196.947] (**) Holtek USB Gaming Mouse: always reports core events
[   196.947] (**) Option "Device" "/dev/input/event6"
[   196.947] (**) Option "_source" "server/udev"
[   196.947] (II) event6  - Holtek USB Gaming Mouse: is tagged by udev as: Keyboard Mouse
[   196.947] (II) event6  - Holtek USB Gaming Mouse: device is a pointer
[   196.948] (II) event6  - Holtek USB Gaming Mouse: device is a keyboard
[   196.948] (II) event6  - Holtek USB Gaming Mouse: device removed
[   196.948] (II) libinput: Holtek USB Gaming Mouse: needs a virtual subdevice
[   196.948] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-5/3-5:1.1/0003:04D9:A067.0002/input/input6/event6"
[   196.948] (II) XINPUT: Adding extended input device "Holtek USB Gaming Mouse" (type: MOUSE, id 10)
[   196.948] (**) Option "AccelerationScheme" "none"
[   196.948] (**) Holtek USB Gaming Mouse: (accel) selected scheme none/0
[   196.948] (**) Holtek USB Gaming Mouse: (accel) acceleration factor: 2.000
[   196.948] (**) Holtek USB Gaming Mouse: (accel) acceleration threshold: 4
[   196.948] (II) event6  - Holtek USB Gaming Mouse: is tagged by udev as: Keyboard Mouse
[   196.948] (II) event6  - Holtek USB Gaming Mouse: device is a pointer
[   196.948] (II) event6  - Holtek USB Gaming Mouse: device is a keyboard
[   196.948] (II) config/udev: Adding input device Holtek USB Gaming Mouse (/dev/input/mouse0)
[   196.948] (II) No input driver specified, ignoring this device.
[   196.948] (II) This device may have been added with another device file.
[   196.949] (II) config/udev: Adding input device SONiX USB Keyboard (/dev/input/event3)
[   196.949] (**) SONiX USB Keyboard: Applying InputClass "libinput keyboard catchall"
[   196.949] (II) Using input driver 'libinput' for 'SONiX USB Keyboard'
[   196.949] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 44 paused 0
[   196.949] (**) SONiX USB Keyboard: always reports core events
[   196.949] (**) Option "Device" "/dev/input/event3"
[   196.949] (**) Option "_source" "server/udev"
[   196.950] (II) event3  - SONiX USB Keyboard: is tagged by udev as: Keyboard
[   196.950] (II) event3  - SONiX USB Keyboard: device is a keyboard
[   196.950] (II) event3  - SONiX USB Keyboard: device removed
[   196.950] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.0/0003:0C45:760B.0004/input/input3/event3"
[   196.950] (II) XINPUT: Adding extended input device "SONiX USB Keyboard" (type: KEYBOARD, id 11)
[   196.950] (**) Option "xkb_model" "pc105"
[   196.950] (**) Option "xkb_layout" "pl"
[   196.950] (II) event3  - SONiX USB Keyboard: is tagged by udev as: Keyboard
[   196.950] (II) event3  - SONiX USB Keyboard: device is a keyboard
[   196.950] (II) config/udev: Adding input device SONiX USB Keyboard (/dev/input/event4)
[   196.950] (**) SONiX USB Keyboard: Applying InputClass "libinput keyboard catchall"
[   196.950] (II) Using input driver 'libinput' for 'SONiX USB Keyboard'
[   196.951] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 45 paused 0
[   196.951] (**) SONiX USB Keyboard: always reports core events
[   196.951] (**) Option "Device" "/dev/input/event4"
[   196.951] (**) Option "_source" "server/udev"
[   196.951] (II) event4  - SONiX USB Keyboard: is tagged by udev as: Keyboard
[   196.951] (II) event4  - SONiX USB Keyboard: device is a keyboard
[   196.951] (II) event4  - SONiX USB Keyboard: device removed
[   196.951] (II) libinput: SONiX USB Keyboard: needs a virtual subdevice
[   196.951] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.1/0003:0C45:760B.0005/input/input4/event4"
[   196.951] (II) XINPUT: Adding extended input device "SONiX USB Keyboard" (type: MOUSE, id 12)
[   196.951] (**) Option "AccelerationScheme" "none"
[   196.951] (**) SONiX USB Keyboard: (accel) selected scheme none/0
[   196.951] (**) SONiX USB Keyboard: (accel) acceleration factor: 2.000
[   196.951] (**) SONiX USB Keyboard: (accel) acceleration threshold: 4
[   196.951] (II) event4  - SONiX USB Keyboard: is tagged by udev as: Keyboard
[   196.951] (II) event4  - SONiX USB Keyboard: device is a keyboard
[   196.952] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event10)
[   196.952] (II) No input driver specified, ignoring this device.
[   196.952] (II) This device may have been added with another device file.
[   196.952] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event11)
[   196.952] (II) No input driver specified, ignoring this device.
[   196.952] (II) This device may have been added with another device file.
[   196.952] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event12)
[   196.952] (II) No input driver specified, ignoring this device.
[   196.952] (II) This device may have been added with another device file.
[   196.952] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event13)
[   196.952] (II) No input driver specified, ignoring this device.
[   196.952] (II) This device may have been added with another device file.
[   196.952] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event7)
[   196.952] (II) No input driver specified, ignoring this device.
[   196.952] (II) This device may have been added with another device file.
[   196.952] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event8)
[   196.952] (II) No input driver specified, ignoring this device.
[   196.952] (II) This device may have been added with another device file.
[   196.953] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event9)
[   196.953] (II) No input driver specified, ignoring this device.
[   196.953] (II) This device may have been added with another device file.
[   196.955] (**) Holtek USB Gaming Mouse: Applying InputClass "libinput pointer catchall"
[   196.955] (**) Holtek USB Gaming Mouse: Applying InputClass "libinput keyboard catchall"
[   196.955] (II) Using input driver 'libinput' for 'Holtek USB Gaming Mouse'
[   196.955] (II) systemd-logind: returning pre-existing fd for /dev/input/event6 13:70
[   196.955] (**) Holtek USB Gaming Mouse: always reports core events
[   196.955] (**) Option "Device" "/dev/input/event6"
[   196.955] (**) Option "_source" "_driver/libinput"
[   196.955] (II) libinput: Holtek USB Gaming Mouse: is a virtual subdevice
[   196.955] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-5/3-5:1.1/0003:04D9:A067.0002/input/input6/event6"
[   196.955] (II) XINPUT: Adding extended input device "Holtek USB Gaming Mouse" (type: KEYBOARD, id 13)
[   196.955] (**) Option "xkb_model" "pc105"
[   196.955] (**) Option "xkb_layout" "pl"
[   196.955] (**) SONiX USB Keyboard: Applying InputClass "libinput keyboard catchall"
[   196.955] (II) Using input driver 'libinput' for 'SONiX USB Keyboard'
[   196.955] (II) systemd-logind: returning pre-existing fd for /dev/input/event4 13:68
[   196.955] (**) SONiX USB Keyboard: always reports core events
[   196.955] (**) Option "Device" "/dev/input/event4"
[   196.955] (**) Option "_source" "_driver/libinput"
[   196.955] (II) libinput: SONiX USB Keyboard: is a virtual subdevice
[   196.955] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.1/0003:0C45:760B.0005/input/input4/event4"
[   196.955] (II) XINPUT: Adding extended input device "SONiX USB Keyboard" (type: KEYBOARD, id 14)
[   196.955] (**) Option "xkb_model" "pc105"
[   196.955] (**) Option "xkb_layout" "pl"
[   197.317] (--) NVIDIA(GPU-0): CRT-0: disconnected
[   197.317] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[   197.317] (--) NVIDIA(GPU-0): 
[   197.410] (--) NVIDIA(GPU-0): Idek Iiyama PL1980 (DFP-0): connected
[   197.410] (--) NVIDIA(GPU-0): Idek Iiyama PL1980 (DFP-0): Internal TMDS
[   197.410] (--) NVIDIA(GPU-0): Idek Iiyama PL1980 (DFP-0): 330.0 MHz maximum pixel clock
[   197.410] (--) NVIDIA(GPU-0): 
[   197.410] (--) NVIDIA(GPU-0): DFP-1: disconnected
[   197.410] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[   197.410] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[   197.410] (--) NVIDIA(GPU-0): 
[   197.410] (--) NVIDIA(GPU-0): DFP-2: disconnected
[   197.410] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[   197.410] (--) NVIDIA(GPU-0): DFP-2: 960.0 MHz maximum pixel clock
[   197.410] (--) NVIDIA(GPU-0): 
[   197.410] (--) NVIDIA(GPU-0): DFP-3: disconnected
[   197.410] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[   197.410] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock
[   197.410] (--) NVIDIA(GPU-0): 
[   197.410] (--) NVIDIA(GPU-0): DFP-4: disconnected
[   197.410] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[   197.410] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[   197.410] (--) NVIDIA(GPU-0): 



```

syslog
[https://paste.ubuntu.com/p/9ZPdFnvpR8/plain/](https://paste.ubuntu.com/p/9ZPdFnvpR8/plain/)

kern.log
[https://paste.ubuntu.com/p/GnTd6DXkm4/plain/](https://paste.ubuntu.com/p/GnTd6DXkm4/plain/)

journalctl -b
[https://paste.ubuntu.com/p/BfXWvzMp2h/]("https://paste.ubuntu.com/p/BfXWvzMp2h/plain/")

---

### Post by Bashing-om on 2018-07-04
yarooh; welp -

And again, why is the system running file system checks ??
> 
4 22:23:15 ubuntu systemd-fsck[469]: fsck.fat 4.1 (2017-01-24)
Jul  4 22:23:15 ubuntu systemd-fsck[469]: /dev/sda1: 4 files, 15987/165560 clusters

However, I do not see the system reporting any file system issues. None - seems then the issues you have must be in user space.
I will have to ponder on what config files can cause these issues and delays .


And not that it matters, but nvidia recommends the 390 version driver rather than 396 for your graphic's card - though 396 "should" work .
[http://www.nvidia.com/download/driverResults.aspx/134859/en-us](http://www.nvidia.com/download/driverResults.aspx/134859/en-us)

[INDENT][INDENT]still without a clue[/INDENT][/INDENT]

---

### Post by VMC on 2018-07-04
kernlog and journal is unviewable.

---

### Post by Bashing-om on 2018-07-04
@ VMC Yeah -
to view remove 'plain' from the URL.

[INDENT][INDENT]glad for help
[/INDENT][/INDENT]

---

### Post by VMC on 2018-07-04
What is the mount point:
```
[COLOR=#000000]lip 04 22:23:16 ubuntu udisksd[659]: mountpoint /media/zolo/AL-X86_64 is invalid, cannot recover the canonical path [/COLOR]Cleaning up mount point /media/zolo/AL-X86_64 (device 11:0 is not mounted)
mountpoint /media/zolo/5A30-B09C is invalid, cannot recover the canonical path 
Cleaning up mount point /media/zolo/5A30-B09C (device 8:49 is not mounted)
```

Also something amiss here
```
** (process:1734): WARNING **: 18:09:13.815: xdg-autostart.vala:125: Error: Error opening directory ?/home/zolo/.config/autostart?: No such file or directory
** Message: 18:09:13.815: xdg-autostart.vala:39: Processing /etc/xdg/autostart/nvidia-settings-autostart.desktop file.
** Message: 18:09:13.816: xdg-autostart.vala:94: Launching: sh -c '/usr/bin/nvidia-settings --load-config-only' (nvidia-settings-autostart.desktop)
** Message: 18:09:13.816: xdg-autostart.vala:39: Processing /etc/xdg/autostart/gnome-keyring-ssh.desktop file.
** Message: 18:09:13.816: xdg-autostart.vala:64: Not found in OnlyShowIn list, aborting.
** Message: 18:09:13.816: xdg-autostart.vala:39: Processing /etc/xdg/autostart/xdg-user-dirs.desktop file.
** Message: 18:09:13.816: xdg-autostart.vala:94: Launching: xdg-user-dirs-update (xdg-user-dirs.desktop)
** Message: 18:09:13.816: xdg-autostart.vala:39: Processing /etc/xdg/autostart/gnome-keyring-pkcs11.desktop file.
** Message: 18:09:13.816: xdg-autostart.vala:64: Not found in OnlyShowIn list, aborting.
** Message: 18:09:13.816: xdg-autostart.vala:39: Processing /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop file.
** Message: 18:09:13.816: xdg-autostart.vala:64: Not found in OnlyShowIn list, aborting.
** Message: 18:09:13.816: xdg-autostart.vala:39: Processing /etc/xdg/autostart/pulseaudio.desktop file.
** Message: 18:09:13.820: xdg-autostart.vala:94: Launching: start-pulseaudio-x11 (pulseaudio.desktop)
** Message: 18:09:13.820: xdg-autostart.vala:39: Processing /etc/xdg/autostart/xfsettingsd.desktop file.
** Message: 18:09:13.820: xdg-autostart.vala:64: Not found in OnlyShowIn list, aborting.
** Message: 18:09:13.820: xdg-autostart.vala:39: Processing /etc/xdg/autostart/gnome-keyring-secrets.desktop file.
** Message: 18:09:13.820: xdg-autostart.vala:64: Not found in OnlyShowIn list, aborting.
** Message: 18:09:13.820: xdg-autostart.vala:39: Processing /etc/xdg/autostart/at-spi-dbus-bus.desktop file.
** Message: 18:09:13.820: xdg-autostart.vala:94: Launching: /usr/lib/at-spi2-core/at-spi-bus-launcher --launch-immediately (at-spi-dbus-bus.desktop)
** Message: 18:09:13.825: x-terminal-emulator has very limited support, consider choose another terminal
Failed to connect to session manager: Nie uda&#322;o si&#281; po&#322;&#261;czy&#263; z menad&#380;erem sesji: SESSION_MANAGER environment variable not defined
```

Try booting with "quiet splash" remove from linux line, and look for error messages.
Then if unsuccessful add "nomodeset" to end of linux, and see if you can then boot.

---

### Post by apeitheo2 on 2018-07-05
```
sudo apt install haveged
sudo systemctl enable haveged
```
It looks like you're having the same problem as I posted here: [https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13781140#post13781140](https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13781140#post13781140)

It's a bug in the recent 4.15.0-24 kernel. It should be fixed soon, I hope, but in the meantime, installing and enabling haveged as shown above should resolve the issue.

Good luck.

---

### Post by yarooh on 2018-07-06
Sorry Guys for late response but all day yesterday I spent in hospital in orthognathic surgery department - really nightmare.
Despite presently the kernel I use is :  4.17.4-041704-generic
The solution advised by apeitheo2 solved the problem. System starts strightaway.
I must admit that on the same beginning I mindlessly upgraded the kernel and nvidia-driver because I prefer LTS setting. So now I will do a fresh install and will keep LTS settings.

There is a great experience to use Ubuntu especially because - ITS COMMUNITY - the strongest advantage this distro.

It is good to know that I can build great system based on Ubuntu and if something goes wrong I will obtain a help.

That is why MANY THANKS FOR ALL OF YOU, FOR YOUR TIME AND HELP.
Best regards
yarooch

---

### Post by Bashing-om on 2018-07-06
yarooh - Great !

Pleased there is resolution . Glad that you followed through and provided the confirmation.

     - just keep on keep'n on -

---

