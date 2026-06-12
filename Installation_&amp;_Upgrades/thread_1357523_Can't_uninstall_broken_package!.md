---
title: "Can't uninstall broken package!"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by Vincent Vespa on 2009-12-17
Hello there!  I'm decently new to Ubuntu and I could really use a dumbed down solution to this problem.  :D

I recently tried to install a printer (Epson Stylus NX110) to my computer and it seems the driver I used ended up being a broken package...  Or something like that.  It might have something to do with me using the driver for the NX105 since there wasn't one for the NX110...  In any case, I have an angry looking red circle on my panel.

I've tried to remove the package using Synaptic...  It couldn't do it...  The error was:
E: pips-snx110: subprocess installed pre-removal script returned error exit status 1

Next I tried removing it in a terminal using the "sudo apt-get install -f" thing.  It failed there giving me:
```
Removing pips-snx110 ...
dpkg: error processing pips-snx110 (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 pips-snx110
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I also tried to remove all of the files manually ("dkpg -L pips-snx110") but that didn't do a thing.

I'm at a loss here.  Any help you guys can give me would be greatly appreciated!
-Vincent Vespa

---

### Post by nibirumarduk on 2009-12-17
Try this:

sudo nano /var/lib/dpkg/info/pips-snx110.prerm
append "exit 0" after "set -e" (Ignore quotes)

Save the change by pressing Ctrl + O

Exit nano with Ctrl + X

Then proceed to configure all partially installed packages with the following command.
sudo dpkg --configure -a or sudo dpkg --configure --pending

Hope this helps.

As a rule of thumb, for such package script problems of "<package_name>", you should look into the particular buggy package script. They can be any of the following:

"/var/lib/dpkg/info/<package_name>.preinst"
"/var/lib/dpkg/info/<package_name>.postinst"
"/var/lib/dpkg/info/<package_name>.prerm"
"/var/lib/dpkg/info/<package_name>.postrm"
Edit the offending package script from the root using following techniques.

In your instance, it happens to be the prerm script as evidenced in this part of the error message:
"subprocess installed pre-removal script"

Possible remedial actions:
1.
disable the offending line by preceding "#"

or

2.
force to return success by appending the offending line with "|| true"

or 

3.
or open up the offending script file e.g. .preinst and append "exit 0" after "set -e", save the change, exit editor.
Configure all partially installed packages with the following command sudo dpkg --configure -a or sudo dpkg --configure --pending.

For a more in-depth understanding as to what these package scripts are and what they do. They are as follow:

preinst
This script executes before that package will be unpacked from its Debian archive (".deb") file. Many 'preinst' scripts stop services for packages which are being upgraded until their installation or upgrade is completed (following the successful execution of the 'postinst' script).

postinst
This script typically completes any required configuration of the package foo once foo has been unpacked from its Debian archive (".deb") file. Often, 'postinst' scripts ask the user for input, and/or warn the user that if he accepts default values, he should remember to go back and re-configure that package as the situation warrants. Many 'postinst' scripts then execute any commands necessary to start or restart a service once a new package has been installed or upgraded.

prerm
This script typically stops any daemons which are associated with a package. It is executed before the removal of files associated with the package.

postrm
This script typically modifies links or other files associated with foo, and/or removes files created by the package.
Currently all of the control files can be found in directory /var/lib/dpkg/info. The files relevant to package foo begin with the name "foo" and have file extensions of "preinst", "postinst", etc., as appropriate. The file foo.list in that directory lists all of the files that were installed with the package foo. (Note that the location of these files is a dpkg internal; you should not rely on it.)

---

### Post by Vincent Vespa on 2009-12-17
Awesome!  Thanks for the help!  I really appreciate it!

You are a gentleman and a scholar, good sir!

---

### Post by nibirumarduk on 2009-12-17
> **Vincent Vespa said:**
> Awesome!  Thanks for the help!  I really appreciate it!

Glad it turned out fine for you. :)

> You are a gentleman and a scholar, good sir!

Hmmm I wish I were but the last I checked, don't think I'm either :P

---

### Post by oddonto on 2010-01-25
Helped me too!! I was so lost. Thank You thank you!

---

### Post by skitter.rusty on 2010-02-01
Thank You so much!! Fixed my problem. They really need to fix that file.

---

### Post by jaiterry on 2010-02-17
Hi,

I have the same issue but none of the posted solutions worked for me. In particular I edit the script but when I run "sudo dpkg --configure -a or sudo dpkg --configure --pending" nothing happens. And even when I run synaptic and attempt to uninstall the broken pips-snx110 software (with the prerm script altered), I still get the same error

Any other advice? This is preventing me from installing any new packages!

I'm running Karmic Koala. 

Modified script below
cat /var/lib/dpkg/info/pips-snx110.prerm
#!/bin/sh
# prerm script for pips-snx110
#
# see: dh_installdeb(1)

set -e exit 0

# summary of how this script can be called:
#        * <prerm> `remove'
#        * <old-prerm> `upgrade' <new-version>
#        * <new-prerm> `failed-upgrade' <old-version>
#        * <conflictor's-prerm> `remove' `in-favour' <package> <new-version>
#        * <deconfigured's-prerm> `deconfigure' `in-favour'
#          <package-being-installed> <version> `removing'
#          <conflicting-package> <version>
# for details, see [http://www.debian.org/doc/debian-policy/](http://www.debian.org/doc/debian-policy/) or
# the debian-policy package


case "$1" in
    remove|upgrade|deconfigure)

    Get_cups_filelist=
    if dpkg -p cups >/dev/null 2>&1 ; then
        Get_cups_filelist="dpkg -L cups"
    elif dpkg -p cupsys >/dev/null 2>&1 ; then
        Get_cups_filelist="dpkg -L cupsys"
    fi

    installdir=
    cupsdefault_ppdfiles="epson9.ppd epson24.ppd deskjet.ppd zebra.ppd"
    for cupsdefaultppd in $cupsdefault_ppdfiles; do
        cupsppddir=`$Get_cups_filelist | grep $cupsdefaultppd 2>/dev/null`
        if test "x" != "x$cupsppddir" ; then
            case "$cupsppddir" in
                /usr/share/ppd/*)
                    installdir=/usr/share/ppd
                    break;
                    ;;
                /opt/share/ppd/*)
                    installdir=/opt/share/ppd
                    break;
                    ;;
                /usr/share/cups/model/*)
                    installdir=/usr/share/cups/model
                    break;
                    ;;
                *)
                    echo "prerm failed to uninstall PPD file" >&2
                    exit 1
                    ;;
            esac

            if test "x" != "x$installdir" ; then
                break;
            fi
        fi
    done

    installed_ppdfiles=`ls -f /usr/local/EPAva/printer/snx110/*.ppd`

    if test "x" != "x$installdir" ; then
        for ppd in $installed_ppdfiles; do
            filename=`basename $ppd`
            rm -f $installdir/$filename
        done
    else 
        echo "prerm failed to uninstall PPD file" >&2
        exit 1
    fi

    /usr/local/EPAva/core/printersetup -d -p snx110 -s cups 2>&1 >/dev/null
    rm -f /usr/share/cups/model/eksnx110.ppd
    rm -f /usr/share/cups/model/eksnx115.ppd 
    rm -f /usr/share/cups/model/ekstx110.ppd
    rm -f /usr/share/cups/model/ekstx115.ppd 
    rm -f /usr/share/cups/model/ekssx110.ppd
    rm -f /usr/share/cups/model/ekssx115.ppd 
    rm -f /usr/share/cups/model/ekstx111.ppd
    rm -f /usr/share/cups/model/ekstx112.ppd
    rm -f /usr/share/cups/model/ekstx113.ppd

    ;;

    failed-upgrade)
    ;;

    *)
        echo "prerm called with unknown argument \`$1'" >&2
        exit 1
    ;;
esac

# dh_installdeb will replace this with shell code automatically
# generated by other debhelper scripts.



exit 0


Thanks!

---

### Post by jaiterry on 2010-02-22
Any advice? I'd love to get rid of the big red dot in the app panel...

---

### Post by skitter.rusty on 2010-02-22
I really don't know how to fix it. Someone would... But by the time you figure out how to fix it you probably could have reinstalled Ubuntu. I just followed the instructions by nibirumarduk.

---

### Post by band1t on 2010-03-06
> **skitter.rusty said:**
> I really don't know how to fix it. Someone would... But by the time you figure out how to fix it you probably could have reinstalled Ubuntu. I just followed the instructions by nibirumarduk.

I have the same problem but uninstalling don't fix it since I need to install the printer(epson stylus sx115)

I edit the file with exit 0 and run the commands but I get:

ldconfig deferred processing now taking place
Error processing:
 pips-snx110

Does anyone know what to do?

---

### Post by sinnadyr on 2010-08-22
I had the same problem, even after editing the script. What I did was edit the .posting, .postrm and .prerm scripts, run the package installer and it finally worked.

---

### Post by tonyt3 on 2010-08-29
Hi,  could you offer some advice on how to uninstall an entire Ubuntu installation?  I often want to install a different flavor (such as Mint) or try KDE, and the only installation option (easy version) is to put them all on side-by-side.  I'd like to remove one and replace it with another.  The main problem here is that this is a dual-boot with Win XP and I don't want to blow it away.  Many thanks,
Tony

======

later:  over on the tips and tutorials forum -- found a piece on gparted, specifically for removing the ubuntu installation:

<http://ubuntuforums.org/showthread.php?t=508927&highlight=parted>

---

