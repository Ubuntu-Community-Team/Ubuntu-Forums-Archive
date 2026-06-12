---
title: "dual boot: boot option screen"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by simontepper on 2010-10-03
**Boot screen: ever increasing options **
[INDENT] I don't know whether this is the right place to ask this question but here goes:
 
I've installed Windows 7 Ultimate on a notebook which previously ran Vista. No problems there .....
 
I've now installed Ubuntu (now updated to 10.04) so that it can boot to  either OS. It all works fine and when I first power up, I get a screen  which invites me to select the OS I want to use. There are however two  problems:
 
1) it defaults to Ubuntu (whereas I would prefer it to default to Windows 7 (it's a work laptop and most of the applications are Windows-specific), and

2) the list of choices is getting increasingly complex with an expanding  list of choices (with each major update of Ubuntu adding more); it even  seems to include an option to go back to Vista!
 
As long as I move down the list and make the right selection quite  speedily, I get to where I want to be (though, as I say, I would like to  change the default option).
 
Is there any way I can edit/shorten this list without damaging the functionality and how can I change that default?
 
Any suggestions/help would be very much appreciated.[/INDENT]

---

### Post by wilee-nilee on 2010-10-03
> **simontepper said:**
> [B]
 
I've now installed Ubuntu (now updated to 10.04) so that it can boot to  either OS. It all works fine and when I first power up, **I get a screen  which invites me to select the OS I want to use. There are however two  problems:** 
[B]
Which Bootloader screen MS or Grub?[/B]
 
1) it defaults to Ubuntu (whereas I would prefer it to default to Windows 7 (it's a work laptop and most of the applications are Windows-specific), and

As long as I move down the list and make the right selection quite  speedily, I get to where I want to be (though, as I say, I would like to  change the default option).
[/INDENT]

If you hit one of the arrow keys to choose a line the timer stops, the default is 10 seconds to choose.

Please be specific about the type of installs just to be sure. Was Ubuntu installed from a booted live cd or usb, or a installed from a live MS environment. It sounds like a standard dual boot but personally I like to know for sure.;)

---

### Post by mikewhatever on 2010-10-03
> **simontepper said:**
> [B]

  ...
 
1) it defaults to Ubuntu (whereas I would prefer it to default to Windows 7 (it's a work laptop and most of the applications are Windows-specific), and

Several threads explain how to do it (see the links).
[http://ubuntuforums.org/showthread.php?t=1530315&highlight=grub+entry](http://ubuntuforums.org/showthread.php?t=1530315&highlight=grub+entry)
[http://ubuntuforums.org/showthread.php?t=1579420&highlight=grub+entry](http://ubuntuforums.org/showthread.php?t=1579420&highlight=grub+entry)
Some guides mention the startupmanager program, but I'm not sure it works.

> 2) the list of choices is getting increasingly complex with an expanding  list of choices (with each major update of Ubuntu adding more); it even  seems to include an option to go back to Vista!
As long as I move down the list and make the right selection quite  speedily, I get to where I want to be (though, as I say, I would like to  change the default option).
 
Is there any way I can edit/shorten this list without damaging the functionality and how can I change that default?

Every time the kernel version gets bumped, a new boot entry is created. Guess that's what you mean by 'major update', right? It's a good idea to remove the older kernels once in a while, since they are probably never used and just take up disk space. Post the output of the **dpkg -l | grep linux-image** command, and I'll tell you how to remove the old ones. The boot menu will be updated in the process.

---

### Post by nikefalcon on 2010-10-03
Hello 'simontepper',

Welcome to the world of Ubuntu, and Ubuntuforums.
I shall assume that you can access the internet from Ubutnu, so lets keep out the command line stuff. Open "Ubuntu Software Center" from the main menu and search for and install "StartUp-Manager".
If you are comfortable using the terminal:
```
sudo apt-get install startupmanager
```
Next, go to "Administration" in the main menu and click on Starup-manager; there you should find an option to change your default OS.You can also lower the timeout value if you wish.

Hope this was useful.

---

### Post by drs305 on 2010-10-03
Startup-Manager can set the default OS, even with Grub2.

Removing extra kernels is easily accomplished with Ubuntu Tweak. When a kernel is removed it is also removed from the Grub menu.

This thread discusses SUM, but also read the section on "Removing older kernels", especially the Ubuntu Tweak paragraphs.
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

If you really want to get into the nuts & bolts of the Grub2 files, refer to the links in my signature line for G2-Basics and G2-Tweaks.

---

### Post by simontepper on 2010-10-04
Wow, thanks, everyone, for all your help. Sadly, it's now the working day and I'll have to postpone trying these things out until later, but thanks again .... as a complete novice in these things, it's reassuring to know that there is a community out there ready to offer such sound advice.

---

### Post by simontepper on 2010-10-04
> **drs305 said:**
> Startup-Manager can set the default OS, even with Grub2.

Removing extra kernels is easily accomplished with Ubuntu Tweak. When a kernel is removed it is also removed from the Grub menu.

This thread discusses SUM, but also read the section on "Removing older kernels", especially the Ubuntu Tweak paragraphs.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

If you really want to get into the nuts & bolts of the Grub2 files, refer to the links in my signature line for G2-Basics and G2-Tweaks.


Hmm .. I've followed the advice in [http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177) and also in Grub 2 Title Tweaks ([http://ubuntuforums.org/showthread.php?t=1287602]("http://ubuntuforums.org/showthread.php?t=818177")), and it's all worked, other than for one small thing that's baffled me: first time I re-booted, I got just the two kernels listed 2.6.32.25 and 24 (with their recovery mode listings). The second time (and now each time) it repeats those two listings, so I now get
2.6.32.25
2.6.32.25 (recovery mode)
2.6.32.24
2.6.32.24 (recovery mode)
2.6.32.25
2.6.32.25 (recovery mode)
2.6.32.24
2.6.32.24 (recovery mode)
the MemTest 86+ and the Windows stuff

Asa  total beginner in all this, it's quite likely that I've done something daft but I'm mystified by it; I can't see where I've gone wrong!

Does this make any sense?

---

### Post by drs305 on 2010-10-04
> **simontepper said:**
> 
Asa  total beginner in all this, it's quite likely that I've done something daft but I'm mystified by it; I can't see where I've gone wrong!

Does this make any sense?

Does the list grow longer on each reboot?

Assuming you tried to change the /etc/grub.d/10_linux file to limit the displayed kernels, if you'll just attach or post the file contents I'll take a look at it and see what might have happened. 

If it was a different file, just post that one instead and tell me what you were trying to do.

---

### Post by simontepper on 2010-10-04
Thank you; it's very good of you to look at this for me.

The contents of the /etc/grub.d/10_linux file are as follows:
```

#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
bindir=${exec_prefix}/bin
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

export TEXTDOMAIN=grub
export TEXTDOMAINDIR=@LOCALEDIR@

CLASS="--class gnu-linux --class gnu --class os"

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
  CLASS="--class $(echo ${GRUB_DISTRIBUTOR} | tr '[A-Z]' '[a-z]' | cut -d' ' -f1) ${CLASS}"
fi

# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac

if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || [ "`grub-probe -t abstraction --device ${GRUB_DEVICE} | sed -e 's,.*\(lvm\).*,\1,'`" = "lvm"  ] ; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"
  if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
    recordfail
EOF
  save_default_entry | sed -e "s/^/\t/"

  if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
      cat << EOF
    set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
    echo    '$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
EOF
  fi
  cat << EOF
    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
    echo    '$(gettext_quoted "Loading initial ramdisk ...")'
EOF
  fi
  if test -n "${initrd}" ; then
    cat << EOF
    initrd    ${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
prepare_boot_cache=

# Added to limit number of Linux kernels displayed.
COUNTER=0
LINUX_KERNELS_DISPLAYED=2
#

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"


  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
       "initrd-${version}" "initrd.img-${alt_version}" \
       "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" true \
    "single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`

# Added to limit number of Linux kernels displayed.
COUNTER=`expr $COUNTER + 1`
if [ $COUNTER -eq $LINUX_KERNELS_DISPLAYED ]; then
list=""
fi
#

done


```


Simon

---

### Post by simontepper on 2010-10-04
I've just read somewhere that the OS Prober also finds additional entries and adds them to the menu. Could I have unwittingly made any changes to it when I was backing it up? (I would attach it, but each time I've tried to attach either it or (as in the previous post) the 10_linux file, the attachment window says 'invalid file'. Is there a way to attach it easily (I'm loathe to post yet another 240+ lines of code!)

---

### Post by drs305 on 2010-10-04
First, thanks for posting the file contents. As a forum moderator, I was able to edit your post to include the contents within [noparse]```

```[/noparse] tags. You can get the code tags when you are creating the post by pressing the # icon in the post's menu; or you can type them manually. 

I copied your 10_linux file into my system and it ran correctly. I have a suspicion of what happened: Did you make a backup copy of your 10_linux file and leave it in the /etc/grub.d folder?  

When you update-grub, it is going to run all scripts in the /etc/grub.d folder which are executable. So you can either move backup copies to another folder or make them unexecutable by changing the properties via a root file browser or running the code:
```
sudo chmod -x /etc/grub.d/<filename>
```

If that is what you did, change the properties and then run "sudo update-grub" again. 

It isn't necessary to reboot to see if it fixed it. You can always inspect your /boot/grub/grub.cfg file or you can run this command to see what menuentries you ended up with:```

grep menuentry /boot/grub/grub.cfg
```

---

### Post by simontepper on 2010-10-05
Fantastic ... that's worked perfectly. I can't thank you enough. (I have all sorts of other questions about whether I need the memtest86+ listing and other things, but for the moment I might be tempted to leave things be while I read around the topic. Having been a Windows user for its entire history, it's fascinating but a little frustrating at times to get to grips with another OS. It's great to know that there is such good help out there!

---

### Post by drs305 on 2010-10-05
> **simontepper said:**
> I have all sorts of other questions about whether I need the memtest86+ listing and other things ...

Glad you resolved this issue. :-)  

If you don't have any other questions about this topic would you please mark this thread SOLVED via the 'Thread Tools' link near the top right of the first post? It helps both users and those providing assistance.

A very brief section of the following post tells you about removing the memtest86+ option if you don't want it. Look at the section "Built-In Settings and Non-Tweak Ways to Limit Menu Entries":
[Grub 2 Title Tweaks Thread]("http://ubuntuforums.org/showthread.php?t=1287602")
You probably won't want to look at the rest - it will make your head explode!

---

### Post by simontepper on 2010-10-05
wilco ... over and out!

---

