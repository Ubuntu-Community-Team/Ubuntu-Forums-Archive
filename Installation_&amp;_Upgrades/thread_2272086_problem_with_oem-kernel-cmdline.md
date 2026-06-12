---
title: "problem with oem-kernel-cmdline"
date: 2015-04-03
forum: Installation &amp; Upgrades
---

### Post by Prem_Reginald on 2015-04-03
Hi,

I am having a problem in removing oem-kernel-cmdline. I am not able to update my software's as it request me to conduct a partial upgrade. And when I do so, Ubuntu is having a problem to remove oem-kernel-cmdline. That did not bother me so much. However, now that I am just merely trying to install a music player, and this same package in being a menace.

I have attached an image of the problem for your troubleshooting.

[ATTACH=CONFIG]261080[/ATTACH]

Thank you very much.

---

### Post by Prem_Reginald on 2015-04-04
```
prem@prem-dell:~$ sudo apt-get autoremoveReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  oem-kernel-cmdline
0 upgraded, 0 newly installed, 1 to remove and 24 not upgraded.
1 not fully installed or removed.
After this operation, 42.0 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 244530 files and directories currently installed.)
Removing oem-kernel-cmdline (1.4kittyhawk7) ...
postrm called with unknown argument `remove'
dpkg: error processing package oem-kernel-cmdline (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 oem-kernel-cmdline
E: Sub-process /usr/bin/dpkg returned an error code (1)
prem@prem-dell:~$ 
```

---

### Post by ian-weisser on 2015-04-04
> **Prem_Reginald said:**
> However, now that I am just merely trying to install a music player
Your system has been trying to tell you that it has a serious problem and needs your help.
It cannot install, uninstall, nor update *anything* until you fix the problem.

> **Prem_Reginald said:**
> 0 upgraded, 0 newly installed, 1 to remove and **24 not upgraded**.
You are not receiving security updates because of this issue.


> **Prem_Reginald said:**
> dpkg: error processing package **oem-kernel-cmdline** (--remove):
 subprocess installed post-removal script returned error exit status 1

oem-kernel-cmdline is not an Ubuntu package.
Wherever you got that package from, you should probably tell the author or maintainer that it's broken and cannot be uninstalled. They may not know.

You should look at the post-removal script in /var/lib/dpkg/info/oem-kernel-cmdline.postrm . Post it here. Might be a simple typo or easy fix.

---

### Post by ruffwuk on 2015-05-27
I am getting the exact error on my new 2015 Dell  XPS13 Ubuntu  Laptop.  How do I fix this?

---

### Post by ian-weisser on 2015-05-27
By contacting Dell Support, if Dell provided that broken OEM package.

If you believe Dell didn't provide it, then please show us the contents of /var/lib/dpkg/info/oem-kernel-cmdline.postrm

---

### Post by jethro2 on 2015-05-29
I've got the same problem and I'm also using a new Dell XPS 13. Going by the contents of the postinst file, only a simple command was added to the grub config to rename the recovery mode to safe mode. Is it safe to assume that the removal of the package may not need additional processing then?

Anyway, here's the postrm file:


```

#!/bin/bash
set -e

# for debconf db_xxx commands
. /usr/share/debconf/confmodule

running_in_container()
{
    type running-in-container >/dev/null 2>&1 && running-in-container >/dev/null
}

case $1 in
    configure|reconfigure)
        config_file="/etc/default/grub.d/51_oem-grub-recovery-title.cfg"
        if [ -f $config_file ]; then
            rm -f $config_file
        fi

       if [ -e /boot/grub/grub.cfg ] && ! ( ischroot || running_in_container ) ; then
            # don't run update-grub on LiveCD, live-build chroot or any other containers
            update-grub || true
        fi        ;;

    abort-upgrade|abort-remove|abort-deconfigure)
        ;;
    *)
        echo "postrm called with unknown argument \`$1'" >&2
        exit 1
       ;;
esac

# Automatically added by dh_installdebconf
if [ "$1" = purge ] && [ -e /usr/share/debconf/confmodule ]; then
        . /usr/share/debconf/confmodule
        db_purge
fi
# End automatically added section
```

---

### Post by ruffwuk on 2015-05-29
I have th same thing as jethro2...  I suppose it must be a Dell package.  I will try to contact them and see if I can't get some kind of resolution.  Wish me luck!

I also tried this link and it worked for me , so try it in yours... remove those oem-kernel-cmdline files from the /var/lib/dpkg directory.


[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19634298](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19634298)

---

### Post by jethro2 on 2015-06-01
Well that did the trick but it's not really a great solution I guess.

I noticed that there's another variant of the oem-kernel-cmdline package included in another fix regarding the suspend issue: [http://www.dell.com/support/article/us/en/19/SLN297551/en](http://www.dell.com/support/article/us/en/19/SLN297551/en)
It includes the recovery name change, adds some additional parameters to the grub config and has a different postrm file which has no such abort clause. So far it works fine.

Contents of the new postrm:
```
#!/bin/bashset -e


# for debconf db_xxx commands
. /usr/share/debconf/confmodule


running_in_container()
{
    type running-in-container >/dev/null 2>&1 && running-in-container >/dev/null
}


case $1 in
    configure|reconfigure)
        config_file="/etc/default/grub.d/51_oem-grub-recovery-title.cfg"
        if [ -f $config_file ]; then
            rm -f $config_file
        fi


        if [ -e /boot/grub/grub.cfg ] && ! ( ischroot || running_in_container ) ; then
            # don't run update-grub on LiveCD, live-build chroot or any other containers
            update-grub || true
        fi
        ;;
    *)
        exit 0
        ;;
esac




# Automatically added by dh_installdebconf
if [ "$1" = purge ] && [ -e /usr/share/debconf/confmodule ]; then
        . /usr/share/debconf/confmodule
        db_purge
fi
# End automatically added section



```

---

### Post by ruffwuk on 2015-06-04
Thanks, I will try that as well.  

I just moved the files into my home folder, so I will put them back and follow the link & code you suggested.

---

### Post by vaibhav8275 on 2015-07-22
> **ruffwuk said:**
> I have th same thing as jethro2...  I suppose it must be a Dell package.  I will try to contact them and see if I can't get some kind of resolution.  Wish me luck!

I also tried this link and it worked for me , so try it in yours... remove those oem-kernel-cmdline files from the /var/lib/dpkg directory.


[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19634298](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19634298)

Thanks Dude yoour suggetion works.
Hey Guys just use below command:

```

sudo mv /var/lib/dpkg/info/oem-kernel-cmdline.* /var/lib/dpkg/info/old-oem/

```

---

### Post by jamie_le_notre on 2016-03-19
I had this exact problem on a dell inspiron15-3000 ubuntu edition. The solution of removing all the oem-kernel* files worked for me.

This is what I believe actually caused the issue.

I had to reinstall from the dell recovery, after the reinstall a beife message flashed on the screen too quick for me to read. Once I'd logged in after the install I did a full update. Every time I re-started from thta point there was a brief flash of message. I had to reboot several times to read the whole thing.

After a dell recovery the message says that the machine is in manufacturer mode and fn-x needs to be pressed to send it into end user mode.

After pressing the fn-x the machine booted fine but then the oem-kernel-cmdline issue occurred

My believe is is that on doing a recovery you must do the fn-x and then upgrade.

Anyway the removing of the oem-kernel files worked for me

---

