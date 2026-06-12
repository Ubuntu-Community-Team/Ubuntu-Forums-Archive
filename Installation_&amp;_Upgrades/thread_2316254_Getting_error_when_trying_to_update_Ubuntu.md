---
title: "Getting error when trying to update Ubuntu"
date: 2016-03-06
forum: Installation &amp; Upgrades
---

### Post by jay119 on 2016-03-06
user@ip-10-153-174-8:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apache2-utils apache2.2-bin firefox-locale-en g++-4.6 guile-1.8-libs libmpc2
  libstdc++6-4.6-dev linux-headers-3.2.0-37 linux-headers-3.2.0-37-virtual
  ttf-dejavu-core
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up keyboard-configuration (1.70ubuntu8) ...
iconv: error while loading shared libraries: libiconv.so.2: cannot open shared object file: No such file or directory
dpkg: error processing package keyboard-configuration (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 keyboard-configuration
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by grahammechanical on 2016-03-06
> 1 not fully installed or removed.

What were you doing that might have caused that comment? This will fix broken packages. Which may help.

```
sudo apt-get install -f
```

Regards.

---

### Post by ajgreeny on 2016-03-06
Which version of Ubuntu are you using?

I think the packages **linux-headers-3.2.0-37** and **linux-headers-3.2.0-37-virtual** were from 12.04, precise but just want to be certain as you may have upgraded to another version but left those header packages installed.

---

### Post by jay119 on 2016-03-07
I tried "sudo apt-get install -f", but still received the same error.

[**[COLOR=#C61919][B]ajgreeny**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=27747"): I am using Ubuntu 14.04.4 LTS (GNU/Linux 3.13.0-79-generic x86_64)

---

### Post by SeijiSensei on 2016-03-07
Did you run "sudo apt-get update" before "sudo apt-get upgrade"?  The update fetches the most current file lists from the repositories and should always be run before an upgrade.

Run the "update" command, then try the "upgrade" again.

---

### Post by jay119 on 2016-03-07
[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195"), thanks for the suggestion. 

I did run a update before upgrade.

---

### Post by Bashing-om on 2016-03-07
jay119; Hello ;

Need to find out why the system is complaining about " keyboard-configuration " .
> 
Setting up keyboard-configuration (1.70ubuntu8) ...
iconv: error while loading shared libraries: libiconv.so.2: cannot open shared object file: No such file or directory
dpkg: error processing package keyboard-configuration (--configure):
subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
keyboard-configuration
E: Sub-process /usr/bin/dpkg returned an error code (1)


We need to find out the origin of " libiconv.so.2 " What is it and where did it come from ? Presently I do not have a clue .

Keeping in mind that :
> 
The following packages were automatically installed and are no longer required:
apache2-utils apache2.2-bin firefox-locale-en g++-4.6 guile-1.8-libs libmpc2
libstdc++6-4.6-dev linux-headers-3.2.0-37 [color=red]linux-headers-3.2.0-37-virtual[/color]
ttf-dejavu-core

a virtual install may have something to do with this.

So what is installed for "keyboard-configuration" ?
```

dpkg -l keyboard-configuration
apt-cache policy keyboard-configuration

```

[INDENT][INDENT]sometime I wonder
[INDENT][INDENT][INDENT]other times I want to find out
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jay119 on 2016-03-07
Bashing-om, thanks for your reponse. This is what I get when I run the commands.

```
user@ip-10-153-174-8:~$ dpkg -l keyboard-configuration
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================

user@ip-10-153-174-8:~$ apt-cache policy keyboard-configuration
keyboard-configuration:
  Installed: 1.70ubuntu8
  Candidate: 1.70ubuntu8
  Version table:
 *** 1.70ubuntu8 0
        500 [http://us-east-1.ec2.archive.ubuntu.com/ubuntu/](http://us-east-1.ec2.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
iF  keyboard-confi 1.70ubuntu8  all          system-wide keyboard preferences
```

---

### Post by Bashing-om on 2016-03-07
jay119; Well ..

Tough to make out with the results NOT within code tags:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Is this what we are looking at ?
> 
[color=red]iF [/color]keyboard-confi 1.70ubuntu8 a
 where 1.70ubuntu8 is the correct version.
Then maybe see what the package manager does with terminal command:
```

sudo dpkg-reconfigure keyboard-configuration

```
see if the system will fix it for us, or give us a hint at what it needs .

[INDENT][INDENT]what does it take
[INDENT][INDENT][INDENT]to keep a package manager
[INDENT][INDENT][INDENT][INDENT]satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by SeijiSensei on 2016-03-07
In case you don't know, libiconv translates between character sets.  I can understand why a keyboard utility would need that library.  There's a command-line program called iconv as well; see "man iconv" for details.  I've used it to convert ISO-8859-1 files to UTF-8.

---

### Post by jay119 on 2016-03-08
Sorry, here are the results in tags:

```

user@ip-10-153-174-8:~/htdocs$ apt-cache policy keyboard-configuration
keyboard-configuration:
  Installed: 1.70ubuntu8
  Candidate: 1.70ubuntu8
  Version table:
 *** 1.70ubuntu8 0
        500 http://us-east-1.ec2.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```

```

user@ip-10-153-174-8:~/htdocs$ dpkg -l keyboard-configuration
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                           Version                      Architecture                 Description
+++-==============================================-============================-============================-=================================================================================================
iF  keyboard-configuration                         1.70ubuntu8                  all                          system-wide keyboard preferences

```

```

user@ip-10-153-174-8:~/htdocs$sudo dpkg-reconfigure keyboard-configuration
/usr/sbin/dpkg-reconfigure: keyboard-configuration is broken or not fully installed

```

---

### Post by Bashing-om on 2016-03-08
jay119; Hey, hey ... 

we have a solid clue .

Let's try the less invasive 1st.
How about:
```

sudo apt install --reinstall keyboard-configuration

```

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jay119 on 2016-03-08
This was the result, looks like there are some packages I should remove.
```

user@ip-10-153-174-8:~/htdocs$ sudo apt install --reinstall keyboard-configuration
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apache2-utils apache2.2-bin firefox-locale-en g++-4.6 guile-1.8-libs libmpc2
  libstdc++6-4.6-dev linux-headers-3.2.0-37 linux-headers-3.2.0-37-virtual
  ttf-dejavu-core
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for keyboard-configuration:amd64

```

---

### Post by Bashing-om on 2016-03-08
jay119; Yuk;

Houston, we have a problem:
> 
E: Internal Error, No file name for keyboard-configuration:amd64


does the control/config file exist ? - is it in a consistent state ?
```

cat /etc/default/keyboard

```
We do need to handle this carefully, package manager advises:
> 
 Package: keyboard-configuration
Priority: important
Section: utils


insure we look and know
[INDENT][INDENT][INDENT]before we leap
[/INDENT][/INDENT][/INDENT]

---

### Post by jay119 on 2016-03-08
Thank you, this is what I get.
```

user@ip-10-153-174-8:~/htdocs/sites$ cat /etc/default/keyboard
# Check /usr/share/doc/keyboard-configuration/README.Debian for
# documentation on what to do after having modified this file.

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""

# If you don't want to use the XKB layout on the console, you can
# specify an alternative keymap.  Make sure it will be accessible
# before /usr is mounted.
# KMAP=/etc/console-setup/defkeymap.kmap.gz

```

---

### Post by Bashing-om on 2016-03-08
jay119; Welp;

I see no problem there, looks good to me .

doing:
> 
apt-cache depends keyboard-configuration
apt-cache rdepends keyboard-configuration

I do not see that the following is too dicey .

Let's bite the bullet:
```

sudo dpkg -P keyboard-configuration
sudo apt install keyboard-configuration

```
IF 'dpkg' screams and hollers, we need to address what it is unhappy about prior to attempting to complete the removal AND before proceeding to get it properly installed.

[INDENT][INDENT][INDENT]when you are in the dark
[INDENT][INDENT][INDENT][INDENT]gotta get a feel
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jay119 on 2016-03-08
```

user@ip-10-153-174-8:~$ apt-cache depends keyboard-configuration
keyboard-configuration
  Depends: debconf
  Depends: liblocale-gettext-perl
  Conflicts: console-setup
  Conflicts: <console-setup:i386>
  Conflicts: console-setup-mini
  Conflicts: <console-setup-mini:i386>
  Replaces: console-setup
  Replaces: <console-setup:i386>
  Replaces: console-setup-mini
  Replaces: <console-setup-mini:i386>

```

```

user@ip-10-153-174-8:~$ apt-cache rdepends keyboard-configuration 
keyboard-configuration
Reverse Depends:
  xserver-xorg-core-lts-wily
  xserver-xorg-core-lts-vivid
  xserver-xorg-core-lts-utopic
  xserver-xorg-core
  live-config
  console-setup-mini
  xserver-xorg-core
  console-setup

```

```

user@ip-10-153-174-8:~$ sudo dpkg -P keyboard-configuration
(Reading database ... 107828 files and directories currently installed.)
Removing keyboard-configuration (1.70ubuntu8) ...
Purging configuration files for keyboard-configuration (1.70ubuntu8) ...

```

```

user@ip-10-153-174-8:~$ sudo apt install keyboard-configuration
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apache2-utils apache2.2-bin firefox-locale-en g++-4.6 guile-1.8-libs libmpc2
  libstdc++6-4.6-dev linux-headers-3.2.0-37 linux-headers-3.2.0-37-virtual
  ttf-dejavu-core
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  keyboard-configuration
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/556 kB of archives.
After this operation, 2,359 kB of additional disk space will be used.
Preconfiguring packages ...
iconv: error while loading shared libraries: libiconv.so.2: cannot open shared object file: No such file or directory
keyboard-configuration failed to preconfigure, with exit status 127
Selecting previously unselected package keyboard-configuration.
(Reading database ... 107813 files and directories currently installed.)
Preparing to unpack .../keyboard-configuration_1.70ubuntu8_all.deb ...
Unpacking keyboard-configuration (1.70ubuntu8) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up keyboard-configuration (1.70ubuntu8) ...
iconv: error while loading shared libraries: libiconv.so.2: cannot open shared object file: No such file or directory
dpkg: error processing package keyboard-configuration (--configure):
 subprocess installed post-installation script returned error exit status 127
Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
 keyboard-configuration
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2016-03-08
jay119; Yuk ..

In a pickle now, let is NOT reboot untill we have a fix !
Let's find out the why:
> 
iconv: error while loading shared libraries: libiconv.so.2: cannot open shared object file: No such file or directory
keyboard-configuration failed to preconfigure, with exit status 127


What info do we get from:
```

ldd $(which iconv)

```

see what we cad do to get it to configure.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by jay119 on 2016-03-08
```

user@ip-10-153-174-8:~$ ldd $(which iconv)
    linux-vdso.so.1 =>  (0x00007ffeafbbf000)
    libiconv.so.2 => not found
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f660de84000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f660e249000)

```

---

### Post by Bashing-om on 2016-03-08
jay119; UH huh ..

let's see what results:
```

sudo ldconfig -v
ldd $(which iconv)

```

see now if that sym link to /usr/local/lib/libiconv.so.2 gets established ??

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

### Post by jay119 on 2016-03-08
Here we go.

```
user@ip-10-153-174-8:~$ sudo ldconfig -v
/sbin/ldconfig.real: Path `/lib/x86_64-linux-gnu' given more than once
/sbin/ldconfig.real: Path `/usr/lib/x86_64-linux-gnu' given more than once
/usr/lib/x86_64-linux-gnu/libfakeroot:
    libfakeroot-0.so -> libfakeroot-tcp.so
/usr/local/lib:
/lib/x86_64-linux-gnu:
    libgcc_s.so.1 -> libgcc_s.so.1
    libply-boot-client.so.2 -> libply-boot-client.so.2.1.0
    libdl.so.2 -> libdl-2.19.so
    libcrypto.so.1.0.0 -> libcrypto.so.1.0.0
    libanl.so.1 -> libanl-2.19.so
    libntfs-3g.so.841 -> libntfs-3g.so.841.0.0
    librt.so.1 -> librt-2.19.so
    libnsl.so.1 -> libnsl-2.19.so
    libudev.so.1 -> libudev.so.1.3.5
    libsystemd-daemon.so.0 -> libsystemd-daemon.so.0.0.10
    libnss_dns.so.2 -> libnss_dns-2.19.so
    libpcsclite.so.1 -> libpcsclite.so.1.0.0
    libSegFault.so -> libSegFault.so
    libext2fs.so.2 -> libext2fs.so.2.4
    libc.so.6 -> libc-2.19.so
    libpcre.so.3 -> libpcre.so.3.13.1
    libreadline.so.5 -> libreadline.so.5.2
    libacl.so.1 -> libacl.so.1.1.0
    libpcprofile.so -> libpcprofile.so
    libusb-0.1.so.4 -> libusb-0.1.so.4.4.4
    libpamc.so.0 -> libpamc.so.0.82.1
    libgpg-error.so.0 -> libgpg-error.so.0.10.0
    libattr.so.1 -> libattr.so.1.1.0
    libcom_err.so.2 -> libcom_err.so.2.1
    libpam.so.0 -> libpam.so.0.83.1
    libiw.so.30 -> libiw.so.30
    liblzo2.so.2 -> liblzo2.so.2.0.0
    libmount.so.1 -> libmount.so.1.1.0
    libatm.so.1 -> libatm.so.1.0.0
    libpam_misc.so.0 -> libpam_misc.so.0.82.0
    libnewt.so.0.52 -> libnewt.so.0.52.15
    libwrap.so.0 -> libwrap.so.0.7.6
    libcgmanager.so.0 -> libcgmanager.so.0.0.0
    libresolv.so.2 -> libresolv-2.19.so
    libsepol.so.1 -> libsepol.so.1
    libfuse.so.2 -> libfuse.so.2.9.2
    libuuid.so.1 -> libuuid.so.1.3.0
    libcrypt.so.1 -> libcrypt-2.19.so
    libnih-dbus.so.1 -> libnih-dbus.so.1.0.0
    libprocps.so.3 -> libprocps.so.3.0.0
    libnss_files.so.2 -> libnss_files-2.19.so
    libply-splash-core.so.2 -> libply-splash-core.so.2.1.0
    libhistory.so.6 -> libhistory.so.6.3
    libnss_nisplus.so.2 -> libnss_nisplus-2.19.so
    libssl.so.1.0.0 -> libssl.so.1.0.0
    libparted.so.0 -> libparted.so.0.0.1
    libply-splash-graphics.so.2 -> libply-splash-graphics.so.2.1.0
    libtinfo.so.5 -> libtinfo.so.5.9
    libdevmapper.so.1.02.1 -> libdevmapper.so.1.02.1
    libpopt.so.0 -> libpopt.so.0.0.0
    libnss_nis.so.2 -> libnss_nis-2.19.so
    libutil.so.1 -> libutil-2.19.so
    libpng12.so.0 -> libpng12.so.0.50.0
    libkmod.so.2 -> libkmod.so.2.2.5
    libaio.so.1 -> libaio.so.1.0.1
    libnss_compat.so.2 -> libnss_compat-2.19.so
    libncursesw.so.5 -> libncursesw.so.5.9
    libsystemd-login.so.0 -> libsystemd-login.so.0.7.1
    libcidn.so.1 -> libcidn-2.19.so
    libblkid.so.1 -> libblkid.so.1.1.0
    libexpat.so.1 -> libexpat.so.1.6.0
    libudev.so.0 -> libudev.so.0.13.0
    liblzma.so.5 -> liblzma.so.5.0.0
    libnss_hesiod.so.2 -> libnss_hesiod-2.19.so
    libcap.so.2 -> libcap.so.2.24
    libbsd.so.0 -> libbsd.so.0.6.0
    libgcrypt.so.11 -> libgcrypt.so.11.8.2
    libpci.so.3 -> libpci.so.3.2.1
    libply.so.2 -> libply.so.2.1.0
    libhistory.so.5 -> libhistory.so.5.2
    libnl-3.so.200 -> libnl-3.so.200.16.1
    libnl-genl-3.so.200 -> libnl-genl-3.so.200.16.1
    libbz2.so.1.0 -> libbz2.so.1.0.4
    libpthread.so.0 -> libpthread-2.19.so
    libkeyutils.so.1 -> libkeyutils.so.1.4
/sbin/ldconfig.real: /lib/x86_64-linux-gnu/ld-2.19.so is the dynamic linker, ignoring

    ld-linux-x86-64.so.2 -> ld-2.19.so
    libss.so.2 -> libss.so.2.0
    libe2p.so.2 -> libe2p.so.2.3
    libselinux.so.1 -> libselinux.so.1
    libreadline.so.6 -> libreadline.so.6.3
    libglib-2.0.so.0 -> libglib-2.0.so.0.4002.0
    libdbus-1.so.3 -> libdbus-1.so.3.7.6
    libusb-1.0.so.0 -> libusb-1.0.so.0.1.0
    libslang.so.2 -> libslang.so.2.2.4
    libjson-c.so.2 -> libjson.so.0
    libnih.so.1 -> libnih.so.1.0.0
    libz.so.1 -> libz.so.1.2.8
    libBrokenLocale.so.1 -> libBrokenLocale-2.19.so
    libulockmgr.so.1 -> libulockmgr.so.1.0.1
    libmemusage.so -> libmemusage.so
    libaudit.so.1 -> libaudit.so.1.0.0
    libthread_db.so.1 -> libthread_db-1.0.so
    libm.so.6 -> libm-2.19.so
    libncurses.so.5 -> libncurses.so.5.9
/usr/lib/x86_64-linux-gnu:
    libformw.so.5 -> libformw.so.5.9
    libXrender.so.1 -> libXrender.so.1.3.0
    librtmp.so.0 -> librtmp.so.0
    libplc4.so -> libplc4.so
    libtsan.so.0 -> libtsan.so.0.0.0
    libsigsegv.so.2 -> libsigsegv.so.2.0.3
    libnspr4.so -> libnspr4.so
    librados.so.2 -> librados.so.2.0.0
    libck-connector.so.0 -> libck-connector.so.0.0.0
    libroken.so.18 -> libroken.so.18.1.0
    libsmime3.so -> libsmime3.so
    libXmuu.so.1 -> libXmuu.so.1.0.0
    libltdl.so.7 -> libltdl.so.7.3.0
    libgccpp.so.1 -> libgccpp.so.1.0.3
    libgnutls-openssl.so.27 -> libgnutls-openssl.so.27.0.0
    libplds4.so -> libplds4.so
    libboost_thread.so.1.54.0 -> libboost_thread.so.1.54.0
    libatomic.so.1 -> libatomic.so.1.0.0
    libkrb5.so.26 -> libkrb5.so.26.0.0
    libapt-pkg.so.4.12 -> libapt-pkg.so.4.12.0
    libdbus-glib-1.so.2 -> libdbus-glib-1.so.2.2.2
    libxcb.so.1 -> libxcb.so.1.1.0
    libssl3.so -> libssl3.so
    libaprutil-1.so.0 -> libaprutil-1.so.0.5.3
    libheimbase.so.1 -> libheimbase.so.1.0.0
    libmpfr.so.4 -> libmpfr.so.4.1.2
    libkrb5.so.3 -> libkrb5.so.3.3
    libasn1.so.8 -> libasn1.so.8.0.0
    libfontconfig.so.1 -> libfontconfig.so.1.8.0
    libicule.so.52 -> libicule.so.52.1
    libsemanage.so.1 -> libsemanage.so.1
    libldap_r-2.4.so.2 -> libldap_r-2.4.so.2.8.3
    libdb-5.1.so -> libdb-5.1.so
    libgcr-base-3.so.1 -> libgcr-base-3.so.1.0.0
    liblockfile.so.1 -> liblockfile.so.1.0
    libgomp.so.1 -> libgomp.so.1.0.0
    libexslt.so.0 -> libexslt.so.0.8.17
    libwind.so.0 -> libwind.so.0.0.0
    libgssapi_krb5.so.2 -> libgssapi_krb5.so.2.2
    libisl.so.10 -> libisl.so.10.2.2
    libmenu.so.5 -> libmenu.so.5.9
    libpolkit-agent-1.so.0 -> libpolkit-agent-1.so.0.0.0
    libapt-inst.so.1.4 -> libapt-inst.so.1.4.0
    libmenuw.so.5 -> libmenuw.so.5.9
    libgobject-2.0.so.0 -> libgobject-2.0.so.0.4002.0
    libustr-1.0.so.1 -> libustr-1.0.so.1.0.4
    libept.so.1.aptpkg4.12 -> libept.so.1.aptpkg4.12
    libgnutls.so.26 -> libgnutls.so.26.22.6
    libelf.so.1 -> libelf-0.158.so
    libsasl2.so.2 -> libsasl2.so.2.0.25
    libedit.so.2 -> libedit.so.2.0.47
    libfreetype.so.6 -> libfreetype.so.6.11.1
    libGeoIP.so.1 -> libGeoIP.so.1.6.0
    libdebconfclient.so.0 -> libdebconfclient.so.0.0.0
    libicutu.so.52 -> libicutu.so.52.1
    libp11-kit.so.0 -> libp11-kit.so.0.0.0
    libnfnetlink.so.0 -> libnfnetlink.so.0.2.0
    libexpatw.so.1 -> libexpatw.so.1.6.0
    libitm.so.1 -> libitm.so.1.0.0
    libX11.so.6 -> libX11.so.6.3.0
    libapparmor.so.1 -> libapparmor.so.1.1.0
    libicui18n.so.52 -> libicui18n.so.52.1
    libnssutil3.so -> libnssutil3.so
    libevent-2.0.so.5 -> libevent-2.0.so.5.1.9
    libhcrypto.so.4 -> libhcrypto.so.4.1.0
    libapr-1.so.0 -> libapr-1.so.0.5.1
    libpipeline.so.1 -> libpipeline.so.1.3.0
    libpciaccess.so.0 -> libpciaccess.so.0.11.1
    liblber-2.4.so.2 -> liblber-2.4.so.2.8.3
    libicutest.so.52 -> libicutest.so.52.1
    libmysqlclient.so.18 -> libmysqlclient_r.so.18.0.0
    libapt-private.so.0.0 -> libapt-private.so.0.0.0
    libgc.so.1 -> libgc.so.1.0.3
    libiculx.so.52 -> libiculx.so.52.1
    libmpc.so.3 -> libmpc.so.3.0.0
    libgmodule-2.0.so.0 -> libgmodule-2.0.so.0.4002.0
    libtasn1.so.6 -> libtasn1.so.6.2.0
    libgck-1.so.0 -> libgck-1.so.0.0.0
    libnss3.so -> libnss3.so
    libidn.so.11 -> libidn.so.11.6.11
    libunistring.so.0 -> libunistring.so.0.1.2
    libpython2.7.so.1.0 -> libpython2.7.so.1.0
    libyaml-0.so.2 -> libyaml-0.so.2.0.2
    libkyotocabinet.so.16 -> libkyotocabinet.so.16.13.0
    libgpm.so.2 -> libgpm.so.2
    libdrm.so.2 -> libdrm.so.2.4.0
    libicuuc.so.52 -> libicuuc.so.52.1
    libgthread-2.0.so.0 -> libgthread-2.0.so.0.4002.0
    libicudata.so.52 -> libicudata.so.52.1
    libxml2.so.2 -> libxml2.so.2.9.1
    libdrm_radeon.so.1 -> libdrm_radeon.so.1.0.1
    libboost_system.so.1.54.0 -> libboost_system.so.1.54.0
    libpolkit-backend-1.so.0 -> libpolkit-backend-1.so.0.0.0
    libk5crypto.so.3 -> libk5crypto.so.3.1
    libasan.so.0 -> libasan.so.0.0.0
    libsigc-2.0.so.0 -> libsigc-2.0.so.0.0.0
    libicuio.so.52 -> libicuio.so.52.1
    libXdmcp.so.6 -> libXdmcp.so.6.0.0
    libgio-2.0.so.0 -> libgio-2.0.so.0.4002.0
    libntlm.so.0 -> libntlm.so.0.0.19
    libnuma.so.1 -> libnuma.so.1
    libheimntlm.so.0 -> libheimntlm.so.0.1.0
    libcurl-gnutls.so.4 -> libcurl-gnutls.so.4.3.0
    libXext.so.6 -> libXext.so.6.4.0
    libkrb5support.so.0 -> libkrb5support.so.0.1
    libform.so.5 -> libform.so.5.9
    libgmp.so.10 -> libgmp.so.10.1.3
    libdb-5.3.so -> libdb-5.3.so
    libdrm_intel.so.1 -> libdrm_intel.so.1.0.0
    librbd.so.1 -> librbd.so.1.0.0
    libpcap.so.0.8 -> libpcap.so.1.5.3
    libcap-ng.so.0 -> libcap-ng.so.0.0.0
    libmagic.so.1 -> libmagic.so.1.0.0
    libdrm_nouveau.so.1 -> libdrm_nouveau.so.1.0.0
    libICE.so.6 -> libICE.so.6.3.0
    libcloog-isl.so.4 -> libcloog-isl.so.4.0.0
    libffi.so.6 -> libffi.so.6.0.1
    libpanel.so.5 -> libpanel.so.5.9
    libgdbm_compat.so.3 -> libgdbm_compat.so.3.0.0
    libquadmath.so.0 -> libquadmath.so.0.0.0
    libasprintf.so.0 -> libasprintf.so.0.0.0
    libaccountsservice.so.0 -> libaccountsservice.so.0.0.0
    libcurl.so.4 -> libcurl.so.4.3.0
    libboost_iostreams.so.1.54.0 -> libboost_iostreams.so.1.54.0
    libXt.so.6 -> libXt.so.6.0.0
    libfribidi.so.0 -> libfribidi.so.0.3.5
    libpcreposix.so.3 -> libpcreposix.so.3.13.1
    libpanelw.so.5 -> libpanelw.so.5.9
    libapt-inst.so.1.5 -> libapt-inst.so.1.5.0
    libstdc++.so.6 -> libstdc++.so.6.0.19
    libSM.so.6 -> libSM.so.6.0.1
    libtasn1.so.3 -> libtasn1.so.3.1.12
    libsqlite3.so.0 -> libsqlite3.so.0.8.6
    libtic.so.5 -> libtic.so.5.9
    libgnutls-extra.so.26 -> libgnutls-extra.so.26.22.6
    libhx509.so.5 -> libhx509.so.5.0.0
    libestr.so.0 -> libestr.so.0.0.0
    libgdbm.so.3 -> libgdbm.so.3.0.0
    libXau.so.6 -> libXau.so.6.0.0
    libmpc.so.2 -> libmpc.so.2.0.0
    libpolkit-gobject-1.so.0 -> libpolkit-gobject-1.so.0.0.0
    libxslt.so.1 -> libxslt.so.1.1.28
    libgssapi.so.3 -> libgssapi.so.3.0.0
/lib:
    libip6tc.so.0 -> libip6tc.so.0.1.0
    libxtables.so.10 -> libxtables.so.10.0.0
    libiptc.so.0 -> libiptc.so.0.0.0
    libip4tc.so.0 -> libip4tc.so.0.1.0
/usr/lib:
/sbin/ldconfig.real: Cannot stat /usr/lib/libiconv.so.2: No such file or directory
    libopcodes-2.24-system.so -> libopcodes-2.24-system.so
    libmu_imap.so.4 -> libmu_imap.so.4.0.0
    libguile-srfi-srfi-1-v-3.so.3 -> libguile-srfi-srfi-1-v-3.so.3.0.2
    libmu_mbox.so.4 -> libmu_mbox.so.4.0.0
    libmu_auth.so.4 -> libmu_auth.so.4.0.0
    libwhoopsie.so.0 -> libwhoopsie.so.0.0
    libpostfix-master.so.1 -> libpostfix-master.so.1.0.1
    libguilereadline-v-18.so.18 -> libguilereadline-v-18.so.18.0.0
    libdns.so.81 -> libdns.so.81.3.1
    libbind9.so.80 -> libbind9.so.80.0.3
    libisc.so.95 -> libisc.so.95.5.0
    libdns.so.100 -> libdns.so.100.2.2
    libpostfix-global.so.1 -> libpostfix-global.so.1.0.1
    libisccfg.so.90 -> libisccfg.so.90.1.0
    libperl.so.5.18 -> libperl.so.5.18.2
    libmu_dbm.so.4 -> libmu_dbm.so.4.0.0
    libguile-srfi-srfi-13-14-v-3.so.3 -> libguile-srfi-srfi-13-14-v-3.so.3.0.1
    liblwres.so.90 -> liblwres.so.90.0.7
    libmu_maildir.so.4 -> libmu_maildir.so.4.0.0
    libguile.so.17 -> libguile.so.17.4.0
    libgsasl.so.7 -> libgsasl.so.7.9.6
    libcwidget.so.3 -> libcwidget.so.3.0.0
    libmailutils.so.4 -> libmailutils.so.4.0.0
    libmu_mailer.so.4 -> libmu_mailer.so.4.0.0
    libgirepository-1.0.so.1 -> libgirepository-1.0.so.1.0.0
    libguile-srfi-srfi-4-v-3.so.3 -> libguile-srfi-srfi-4-v-3.so.3.0.1
    libbind9.so.90 -> libbind9.so.90.0.9
    libpostfix-tls.so.1 -> libpostfix-tls.so.1.0.1
    libguile-2.0.so.22 -> libguile-2.0.so.22.7.0
    liblwres.so.80 -> liblwres.so.80.0.1
    libxapian.so.22 -> libxapian.so.22.6.3
    libisccc.so.80 -> libisccc.so.80.0.0
    libmu_cfg.so.0 -> libmu_cfg.so.0.0.0
    libmu_sieve.so.4 -> libmu_sieve.so.4.0.0
    libmu_pop.so.4 -> libmu_pop.so.4.0.0
    libpostfix-dns.so.1 -> libpostfix-dns.so.1.0.1
    libisccfg.so.82 -> libisccfg.so.82.0.0
    libisc.so.83 -> libisc.so.83.0.1
    libisccc.so.90 -> libisccc.so.90.0.6
    libmu_py.so.4 -> libmu_py.so.4.0.0
    libguilereadline-v-17.so.17 -> libguilereadline-v-17.so.17.0.3
    libbfd-2.24-system.so -> libbfd-2.24-system.so
    libmu_scm.so.4 -> libmu_scm.so.4.0.0
    libguile-srfi-srfi-60-v-2.so.2 -> libguile-srfi-srfi-60-v-2.so.2.0.2
    libmu_mh.so.4 -> libmu_mh.so.4.0.0
    libpostfix-util.so.1 -> libpostfix-util.so.1.0.1
    libboost_iostreams.so.1.46.1 -> libboost_iostreams.so.1.46.1
    libmu_compat.so.0 -> libmu_compat.so.0.0.0

```
```

user@ip-10-153-174-8:~$ ldd $(which iconv)
    linux-vdso.so.1 =>  (0x00007ffcde52d000)
    libiconv.so.2 => not found
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f462c49d000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f462c862000)

```

---

### Post by Bashing-om on 2016-03-08
jay119; welp;

Going to have to get into a learning mode:
```

/sbin/ldconfig.real: Path `/lib/x86_64-linux-gnu' given more than once

-bk-

/sbin/ldconfig.real: Cannot stat /usr/lib/libiconv.so.2: No such file or directory

```
see if I can find out what is not going on.
------------------
EDIT, let's start down this rabbit hole:
```

cd /
sudo find ./ | grep libiconv.so.2

```
---------------------------

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by jay119 on 2016-03-08
Thank you for all your help, let me know what I can do next to get this resolved.

---

### Post by Bashing-om on 2016-03-08
jay119; Hey;

Has me guessing, and sure has my interest to discover what you have done that requires the libiconv.so.2 library.

see my edit on the prior thread. where is the library ( if any) installed ?
maybe all we need to do is tell the system where it is ???

[INDENT][INDENT]in for a learning experience
[/INDENT][/INDENT]

---

### Post by jay119 on 2016-03-09
Ok, here are the results.

```

user@ip-10-153-174-8:/$ sudo find ./ | grep libiconv.so.2
./opt/bitnami/common/lib/libiconv.so.2.5.1
./opt/bitnami/common/lib/libiconv.so.2

```

---

### Post by Bashing-om on 2016-03-09
jay119; OK ...

So what is the background on 'bitnami' ? Where did it come from, and how did you install it ?

is the symlink to libiconv.so.2.5.1 in place ?
show:
```

ls -al /opt/
ls -al /opt/bitnami/common/lib/libiconv.so.2

```

[INDENT][INDENT]what do we learn today
[/INDENT][/INDENT]

---

### Post by jay119 on 2016-03-09
I inherited this amazon (AWS) server, and bitnami is the Lamp stack installed on the server.

This is what I get when I ssh into the server for a welcome message:
```

Welcome to Ubuntu 14.04.4 LTS (GNU/Linux 3.13.0-79-generic x86_64)
       ___ _ _   _  _            _  
      | _ |_) |_| \| |__ _ _ __ (_) 
      | _ \ |  _| .` / _` | '  \| | 
      |___/_|\__|_|\_\__,_|_|_|_|_| 

  *** Welcome to the BitNami LAMP Stack 5.4.14-0 ***
  *** BitNami Wiki:   http://wiki.bitnami.com/ ***
  *** BitNami Forums: http://answers.bitnami.com/ ***
Last login: Wed Mar  9 13:53:20 2016 from 184-89-163-69.res.bhn.net


```

```

bitnami@ip-10-153-174-8:~$ ls -al /opt/
total 12
drwxr-xr-x  3 root root 4096 Apr 13  2013 .
drwxr-xr-x 22 root root 4096 Mar  6 18:21 ..
drwxr-xr-x 20 root root 4096 Apr 13  2013 bitnami

```

```

bitnami@ip-10-153-174-8:~$ ls -al /opt/bitnami/common/lib/libiconv.so.2
lrwxrwxrwx 1 root root 17 Apr 13  2013 /opt/bitnami/common/lib/libiconv.so.2 -> libiconv.so.2.5.1

```

---

### Post by Bashing-om on 2016-03-09
jay119; Thanks,

Just goes to show what I do not know .

OK; bitnami is legit, required, and wanted ..

so does the system have the path to bitnami's library ?
what returns:
```

echo $PATH

``` 'cause the library is there, and the required symlink FROM /opt is there . Does the system -still- know ?

Now as to how this library ties in with the keyboard configuration - why the package manager is unhappy ; I just have no idea.

[INDENT][INDENT]learning that why
[/INDENT][/INDENT]

---

### Post by jay119 on 2016-03-09
```

bitnami@ip-10-153-174-8:~$ echo $PATH
/opt/bitnami/frameworks/laravel/app/Console:/opt/bitnami/frameworks/cakephp/app/Console:/opt/bitnami/frameworks/codeigniter/bin:/opt/bitnami/frameworks/symfony/bin:/opt/bitnami/frameworks/zendframework/app/Console:/opt/bitnami/heroku/bin:/opt/bitnami/ruby/bin:/opt/bitnami/git/bin:/opt/bitnami/perl/bin:/opt/bitnami/varnish/bin:/opt/bitnami/sqlite/bin:/opt/bitnami/php/bin:/opt/bitnami/mysql/bin:/opt/bitnami/apache2/bin:/opt/bitnami/common/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

```

---

### Post by matt_symes on 2016-03-09
Hi

> **jay119 said:**
> I tried "sudo apt-get install -f", but still received the same error.

Try this. It should add the library to the cache.

```
echo /opt/bitnami/common/lib/ | sudo tee /etc/ld.so.conf.d/bitnami.conf
```

```
sudo ldconfig
```

```
sudo apt-get -f install
```

Kind regards

---

### Post by jay119 on 2016-03-09
```

bitnami@ip-10-153-174-8:~$ echo /opt/bitnami/common/lib/ | sudo tee /etc/ld.so.conf.d/bitnami.conf
/opt/bitnami/common/lib/

```
```

bitnami@ip-10-153-174-8:~$ sudo ldconfig

```
```

bitnami@ip-10-153-174-8:~$ sudo apt-get -f install
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by apt-get)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by apt-get)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by apt-get)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/x86_64-linux-gnu/libapt-private.so.0.0)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by /usr/lib/x86_64-linux-gnu/libapt-private.so.0.0)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/x86_64-linux-gnu/libapt-private.so.0.0)



```

---

### Post by jay119 on 2016-03-10
```

bitnami@ip-10-153-174-8:~$ echo /opt/bitnami/common/lib/ | sudo tee /etc/ld.so.conf.d/bitnami.conf
/opt/bitnami/common/lib/

```

```

bitnami@ip-10-153-174-8:~$ sudo ldconfig

```

```

bitnami@ip-10-153-174-8:~$ sudo apt-get -f install
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by apt-get)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by apt-get)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by apt-get)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/x86_64-linux-gnu/libapt-private.so.0.0)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by /usr/lib/x86_64-linux-gnu/libapt-private.so.0.0)
apt-get: /opt/bitnami/common/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/x86_64-linux-gnu/libapt-private.so.0.0)

```

---

### Post by Bashing-om on 2016-03-10
jay119; Oh Wow ;

This has gotten beyond my level of expertise .
To 'know' why so many versions of GLIBCXX_ seem to be required ......
And why from 3 different sources ...

I just do not have the experience with this server rendtion to even begin to understand what is required.

However, I do know we will want to know what is installed:
what is returned:
```

ls -al /opt/bitnami/common/lib/
file /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12
ls -al /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12

```

as one place to stab in an attempt to start connecting the dots.

[INDENT][INDENT]the package manager does not lie
[/INDENT][/INDENT]

---

### Post by jay119 on 2016-03-10
Thank you for all your help!

Will I break the server if I reboot it; as I think you mentioned in a previous message?

```

bitnami@ip-10-153-174-8:~$ ls -al /opt/bitnami/common/lib/
total 63620
drwxr-xr-x 11 root root     4096 Apr 13  2013 .
drwxr-xr-x 10 root root     4096 Apr 13  2013 ..
-rw-r--r--  1 root root     8351 Apr 12  2013 apr.exp
drwxr-xr-x  2 root root     4096 Apr 13  2013 apr-util-1
-rw-r--r--  1 root root     5531 Apr 12  2013 aprutil.exp
-rw-r--r--  1 root root      212 Apr 12  2013 charset.alias
drwxr-xr-x  2 root root     4096 Apr 13  2013 engines
drwxr-xr-x  2 root root     4096 Apr 13  2013 gettext
drwxr-xr-x  3 root root     4096 Apr 13  2013 icu
drwxr-xr-x  4 root root     4096 Apr 13  2013 ImageMagick-6.7.5
lrwxrwxrwx  1 root root       17 Apr 13  2013 libapr-1.so -> libapr-1.so.0.4.6
lrwxrwxrwx  1 root root       17 Apr 13  2013 libapr-1.so.0 -> libapr-1.so.0.4.6
-rwxr-xr-x  1 root root   266469 Apr 12  2013 libapr-1.so.0.4.6
lrwxrwxrwx  1 root root       21 Apr 13  2013 libaprutil-1.so -> libaprutil-1.so.0.4.1
lrwxrwxrwx  1 root root       21 Apr 13  2013 libaprutil-1.so.0 -> libaprutil-1.so.0.4.1
-rwxr-xr-x  1 root root   202166 Apr 12  2013 libaprutil-1.so.0.4.1
lrwxrwxrwx  1 root root       19 Apr 13  2013 libcharset.so -> libcharset.so.1.0.0
lrwxrwxrwx  1 root root       19 Apr 13  2013 libcharset.so.1 -> libcharset.so.1.0.0
-rw-r--r--  1 root root    13142 Apr 12  2013 libcharset.so.1.0.0
lrwxrwxrwx  1 root root       21 Apr 13  2013 libcouchbase.so -> libcouchbase.so.2.0.2
lrwxrwxrwx  1 root root       21 Apr 13  2013 libcouchbase.so.2 -> libcouchbase.so.2.0.2
-rwxr-xr-x  1 root root   169374 Apr 12  2013 libcouchbase.so.2.0.2
lrwxrwxrwx  1 root root       18 Apr 13  2013 libcrypto.so -> libcrypto.so.1.0.0
-r-xr-xr-x  1 root root  2079576 Apr 12  2013 libcrypto.so.1.0.0
lrwxrwxrwx  1 root root       16 Apr 13  2013 libcurl.so -> libcurl.so.4.2.0
lrwxrwxrwx  1 root root       16 Apr 13  2013 libcurl.so.4 -> libcurl.so.4.2.0
-rwxr-xr-x  1 root root   431263 Apr 12  2013 libcurl.so.4.2.0
lrwxrwxrwx  1 root root       17 Apr 13  2013 libexpat.so -> libexpat.so.1.5.2
lrwxrwxrwx  1 root root       17 Apr 13  2013 libexpat.so.1 -> libexpat.so.1.5.2
-rwxr-xr-x  1 root root   221426 Apr 12  2013 libexpat.so.1.5.2
lrwxrwxrwx  1 root root       18 Apr 13  2013 libexslt.so -> libexslt.so.0.8.15
lrwxrwxrwx  1 root root       18 Apr 13  2013 libexslt.so.0 -> libexslt.so.0.8.15
-rwxr-xr-x  1 root root   109912 Apr 12  2013 libexslt.so.0.8.15
lrwxrwxrwx  1 root root       20 Apr 13  2013 libfreetype.so -> libfreetype.so.6.8.0
lrwxrwxrwx  1 root root       20 Apr 13  2013 libfreetype.so.6 -> libfreetype.so.6.8.0
-rwxr-xr-x  1 root root   926240 Apr 12  2013 libfreetype.so.6.8.0
lrwxrwxrwx  1 root root       14 Apr 13  2013 libgd.so -> libgd.so.2.0.0
lrwxrwxrwx  1 root root       14 Apr 13  2013 libgd.so.2 -> libgd.so.2.0.0
-rwxr-xr-x  1 root root   309097 Apr 12  2013 libgd.so.2.0.0
-rwxr-xr-x  1 root root  1584812 Apr 12  2013 libgettextlib-0.18.1.so
lrwxrwxrwx  1 root root       23 Apr 13  2013 libgettextlib.so -> libgettextlib-0.18.1.so
lrwxrwxrwx  1 root root       21 Apr 13  2013 libgettextpo.so -> libgettextpo.so.0.5.1
lrwxrwxrwx  1 root root       21 Apr 13  2013 libgettextpo.so.0 -> libgettextpo.so.0.5.1
-rwxr-xr-x  1 root root   433517 Apr 12  2013 libgettextpo.so.0.5.1
-rwxr-xr-x  1 root root   367483 Apr 12  2013 libgettextsrc-0.18.1.so
lrwxrwxrwx  1 root root       23 Apr 13  2013 libgettextsrc.so -> libgettextsrc-0.18.1.so
lrwxrwxrwx  1 root root       15 Apr 13  2013 libgmp.so -> libgmp.so.3.5.0
lrwxrwxrwx  1 root root       15 Apr 13  2013 libgmp.so.3 -> libgmp.so.3.5.0
-rwxr-xr-x  1 root root   488080 Apr 12  2013 libgmp.so.3.5.0
lrwxrwxrwx  1 root root       15 Apr 13  2013 libhistory.so -> libhistory.so.5
lrwxrwxrwx  1 root root       17 Apr 13  2013 libhistory.so.5 -> libhistory.so.5.2
-r-xr-xr-x  1 root root    44338 Apr 12  2013 libhistory.so.5.2
lrwxrwxrwx  1 root root       17 Apr 13  2013 libiconv.so -> libiconv.so.2.5.1
lrwxrwxrwx  1 root root       17 Apr 13  2013 libiconv.so.2 -> libiconv.so.2.5.1
-rw-r--r--  1 root root  1023081 Apr 12  2013 libiconv.so.2.5.1
lrwxrwxrwx  1 root root       20 Apr 13  2013 libicudata.so -> libicudata.so.48.1.1
lrwxrwxrwx  1 root root       20 Apr 13  2013 libicudata.so.48 -> libicudata.so.48.1.1
-rw-r--r--  1 root root 18278140 Apr 12  2013 libicudata.so.48.1.1
lrwxrwxrwx  1 root root       20 Apr 13  2013 libicui18n.so -> libicui18n.so.48.1.1
lrwxrwxrwx  1 root root       20 Apr 13  2013 libicui18n.so.48 -> libicui18n.so.48.1.1
-rwxr-xr-x  1 root root  2756539 Apr 12  2013 libicui18n.so.48.1.1
lrwxrwxrwx  1 root root       18 Apr 13  2013 libicuio.so -> libicuio.so.48.1.1
lrwxrwxrwx  1 root root       18 Apr 13  2013 libicuio.so.48 -> libicuio.so.48.1.1
-rwxr-xr-x  1 root root    70783 Apr 12  2013 libicuio.so.48.1.1
lrwxrwxrwx  1 root root       18 Apr 13  2013 libicule.so -> libicule.so.48.1.1
lrwxrwxrwx  1 root root       18 Apr 13  2013 libicule.so.48 -> libicule.so.48.1.1
-rwxr-xr-x  1 root root   343972 Apr 12  2013 libicule.so.48.1.1
lrwxrwxrwx  1 root root       18 Apr 13  2013 libiculx.so -> libiculx.so.48.1.1
lrwxrwxrwx  1 root root       18 Apr 13  2013 libiculx.so.48 -> libiculx.so.48.1.1
-rwxr-xr-x  1 root root    69123 Apr 12  2013 libiculx.so.48.1.1
lrwxrwxrwx  1 root root       20 Apr 13  2013 libicutest.so -> libicutest.so.48.1.1
lrwxrwxrwx  1 root root       20 Apr 13  2013 libicutest.so.48 -> libicutest.so.48.1.1
-rwxr-xr-x  1 root root    85853 Apr 12  2013 libicutest.so.48.1.1
lrwxrwxrwx  1 root root       18 Apr 13  2013 libicutu.so -> libicutu.so.48.1.1
lrwxrwxrwx  1 root root       18 Apr 13  2013 libicutu.so.48 -> libicutu.so.48.1.1
-rwxr-xr-x  1 root root   186827 Apr 12  2013 libicutu.so.48.1.1
lrwxrwxrwx  1 root root       18 Apr 13  2013 libicuuc.so -> libicuuc.so.48.1.1
lrwxrwxrwx  1 root root       18 Apr 13  2013 libicuuc.so.48 -> libicuuc.so.48.1.1
-rwxr-xr-x  1 root root  1933402 Apr 12  2013 libicuuc.so.48.1.1
lrwxrwxrwx  1 root root       16 Apr 13  2013 libjpeg.so -> libjpeg.so.8.4.0
lrwxrwxrwx  1 root root       16 Apr 13  2013 libjpeg.so.8 -> libjpeg.so.8.4.0
-rwxr-xr-x  1 root root   351647 Apr 12  2013 libjpeg.so.8.4.0
lrwxrwxrwx  1 root root       20 Apr 13  2013 liblber-2.4.so.2 -> liblber-2.4.so.2.5.6
-rw-r--r--  1 root root    77178 Apr 12  2013 liblber-2.4.so.2.5.6
lrwxrwxrwx  1 root root       20 Apr 13  2013 liblber.so -> liblber-2.4.so.2.5.6
lrwxrwxrwx  1 root root       20 Apr 13  2013 libldap-2.4.so.2 -> libldap-2.4.so.2.5.6
-rw-r--r--  1 root root   377596 Apr 12  2013 libldap-2.4.so.2.5.6
lrwxrwxrwx  1 root root       22 Apr 13  2013 libldap_r-2.4.so.2 -> libldap_r-2.4.so.2.5.6
-rw-r--r--  1 root root   414376 Apr 12  2013 libldap_r-2.4.so.2.5.6
lrwxrwxrwx  1 root root       22 Apr 13  2013 libldap_r.so -> libldap_r-2.4.so.2.5.6
lrwxrwxrwx  1 root root       20 Apr 13  2013 libldap.so -> libldap-2.4.so.2.5.6
-rw-r--r--  1 root root  3712444 Apr 12  2013 libMagick++.a
-rw-r--r--  1 root root  6930522 Apr 12  2013 libMagickCore.a
-rwxr-xr-x  1 root root     1373 Apr 12  2013 libMagickCore.la
lrwxrwxrwx  1 root root       22 Apr 13  2013 libMagickCore.so -> libMagickCore.so.5.0.0
lrwxrwxrwx  1 root root       22 Apr 13  2013 libMagickCore.so.5 -> libMagickCore.so.5.0.0
-rwxr-xr-x  1 root root  4586334 Apr 12  2013 libMagickCore.so.5.0.0
-rwxr-xr-x  1 root root     1800 Apr 12  2013 libMagick++.la
lrwxrwxrwx  1 root root       20 Apr 13  2013 libMagick++.so -> libMagick++.so.5.0.0
lrwxrwxrwx  1 root root       20 Apr 13  2013 libMagick++.so.5 -> libMagick++.so.5.0.0
-rwxr-xr-x  1 root root  1822781 Apr 12  2013 libMagick++.so.5.0.0
-rw-r--r--  1 root root  2577522 Apr 12  2013 libMagickWand.a
-rwxr-xr-x  1 root root     1442 Apr 12  2013 libMagickWand.la
lrwxrwxrwx  1 root root       22 Apr 13  2013 libMagickWand.so -> libMagickWand.so.5.0.0
lrwxrwxrwx  1 root root       22 Apr 13  2013 libMagickWand.so.5 -> libMagickWand.so.5.0.0
-rwxr-xr-x  1 root root  1704485 Apr 12  2013 libMagickWand.so.5.0.0
drwxr-xr-x  2 root root     4096 Apr 13  2013 libmcrypt
lrwxrwxrwx  1 root root       18 Apr 13  2013 libmcrypt.so -> libmcrypt.so.4.4.8
lrwxrwxrwx  1 root root       18 Apr 13  2013 libmcrypt.so.4 -> libmcrypt.so.4.4.8
-rwxr-xr-x  1 root root   269672 Apr 12  2013 libmcrypt.so.4.4.8
lrwxrwxrwx  1 root root       21 Apr 13  2013 libpcreposix.so -> libpcreposix.so.0.0.1
lrwxrwxrwx  1 root root       21 Apr 13  2013 libpcreposix.so.0 -> libpcreposix.so.0.0.1
-rwxr-xr-x  1 root root    11094 Apr 12  2013 libpcreposix.so.0.0.1
lrwxrwxrwx  1 root root       16 Apr 13  2013 libpcre.so -> libpcre.so.1.0.1
lrwxrwxrwx  1 root root       16 Apr 13  2013 libpcre.so.1 -> libpcre.so.1.0.1
-rwxr-xr-x  1 root root   217536 Apr 12  2013 libpcre.so.1.0.1
lrwxrwxrwx  1 root root       18 Apr 13  2013 libpng15.so -> libpng15.so.15.9.0
lrwxrwxrwx  1 root root       18 Apr 13  2013 libpng15.so.15 -> libpng15.so.15.9.0
-rwxr-xr-x  1 root root   239998 Apr 12  2013 libpng15.so.15.9.0
lrwxrwxrwx  1 root root       11 Apr 13  2013 libpng.so -> libpng15.so
lrwxrwxrwx  1 root root       16 Apr 13  2013 libreadline.so -> libreadline.so.5
lrwxrwxrwx  1 root root       18 Apr 13  2013 libreadline.so.5 -> libreadline.so.5.2
-r-xr-xr-x  1 root root   468236 Apr 12  2013 libreadline.so.5.2
lrwxrwxrwx  1 root root       18 Apr 13  2013 libsasl2.so -> libsasl2.so.2.0.25
lrwxrwxrwx  1 root root       18 Apr 13  2013 libsasl2.so.2 -> libsasl2.so.2.0.25
-rwxr-xr-x  1 root root   152291 Apr 12  2013 libsasl2.so.2.0.25
lrwxrwxrwx  1 root root       15 Apr 13  2013 libssl.so -> libssl.so.1.0.0
-r-xr-xr-x  1 root root   458791 Apr 12  2013 libssl.so.1.0.0
lrwxrwxrwx  1 root root       18 Apr 13  2013 libstdc++.so -> libstdc++.so.6.0.3
lrwxrwxrwx  1 root root       18 Apr 13  2013 libstdc++.so.6 -> libstdc++.so.6.0.3
-rwxr-xr-x  1 root root  3964547 Apr 12  2013 libstdc++.so.6.0.3
lrwxrwxrwx  1 root root       16 Apr 13  2013 libtiff.so -> libtiff.so.5.0.6
lrwxrwxrwx  1 root root       16 Apr 13  2013 libtiff.so.5 -> libtiff.so.5.0.6
-rwxr-xr-x  1 root root   544750 Apr 12  2013 libtiff.so.5.0.6
lrwxrwxrwx  1 root root       16 Apr 13  2013 libxml2.so -> libxml2.so.2.7.8
lrwxrwxrwx  1 root root       16 Apr 13  2013 libxml2.so.2 -> libxml2.so.2.7.8
-rwxr-xr-x  1 root root  1953737 Apr 12  2013 libxml2.so.2.7.8
drwxr-xr-x  2 root root     4096 Apr 13  2013 libxslt-plugins
lrwxrwxrwx  1 root root       17 Apr 13  2013 libxslt.so -> libxslt.so.1.1.26
lrwxrwxrwx  1 root root       17 Apr 13  2013 libxslt.so.1 -> libxslt.so.1.1.26
-rwxr-xr-x  1 root root   332679 Apr 12  2013 libxslt.so.1.1.26
lrwxrwxrwx  1 root root       18 Apr 13  2013 libyaml-0.so.2 -> libyaml-0.so.2.0.2
-rwxr-xr-x  1 root root   190432 Apr 12  2013 libyaml-0.so.2.0.2
lrwxrwxrwx  1 root root       18 Apr 13  2013 libyaml.so -> libyaml-0.so.2.0.2
lrwxrwxrwx  1 root root       13 Apr 13  2013 libz.so -> libz.so.1.2.6
lrwxrwxrwx  1 root root       13 Apr 13  2013 libz.so.1 -> libz.so.1.2.6
-rwxr-xr-x  1 root root   119232 Apr 12  2013 libz.so.1.2.6
drwxr-xr-x  2 root root     4096 Apr 13  2013 pkgconfig
-rw-r--r--  1 root root  1015649 Apr 12  2013 preloadable_libiconv.so
-rw-r--r--  1 root root    66592 Apr 12  2013 preloadable_libintl.so
drwxr-xr-x  2 root root     4096 Apr 13  2013 sasl2
lrwxrwxrwx  1 root root       17 Apr 13  2013 terminfo -> ../share/terminfo
-rw-r--r--  1 root root      236 Apr 13  2013 xml2Conf.sh
-rw-r--r--  1 root root      242 Apr 13  2013 xsltConf.sh

```
```

bitnami@ip-10-153-174-8:~$ file /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12
/usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12: symbolic link to `libapt-pkg.so.4.12.0' 

```
```

bitnami@ip-10-153-174-8:~$ ls -al /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12
lrwxrwxrwx 1 root root 20 Jan 12 20:13 /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12 -> libapt-pkg.so.4.12.0

```

---

### Post by Bashing-om on 2016-03-10
jay119; Hey,

Not to leave ya in a lurch.

Thus far I still do not see the nature of the problem/
```

lrwxrwxrwx  1 root root       18 Apr 13  2013 libstdc++.so -> libstdc++.so.6.0.3
lrwxrwxrwx  1 root root       18 Apr 13  2013 libstdc++.so.6 -> libstdc++.so.6.0.3
-rwxr-xr-x  1 root root  3964547 Apr 12  2013 libstdc++.so.6.0.3
lrwxrwxrwx

```

where I see no problems. However. is the nature of the problem explained here :
[https://gcc.gnu.org/onlinedocs/libstdc++/faq.html#faq.how_to_set_paths](https://gcc.gnu.org/onlinedocs/libstdc++/faq.html#faq.how_to_set_paths)
[https://gcc.gnu.org/onlinedocs/libstdc++/manual/using_dynamic_or_shared.html#manual.intro.using.linkage.dynamic](https://gcc.gnu.org/onlinedocs/libstdc++/manual/using_dynamic_or_shared.html#manual.intro.using.linkage.dynamic)

As to rebooting, as we did :
> 
Code:
user@ip-10-153-174-8:~$ sudo dpkg -P keyboard-configuration
(Reading database ... 107828 files and directories currently installed.)
Removing keyboard-configuration (1.70ubuntu8) ...
Purging configuration files for keyboard-configuration (1.70ubuntu8) .

I am concerned that there now is no driver for the keyboard . I will be much relieved when " install keyboard-configuration " is completed.

[INDENT][INDENT]poke at it 'til something gives
[/INDENT][/INDENT]

---

### Post by jay119 on 2016-03-14
Sorry not sure what to do next?

---

### Post by Bashing-om on 2016-03-14
jay119; Well ..

Believe me there is a lot I do not know, here we are looking at this as a linking issue. I have no experience with this server set up, so I am flying by the seat of my pants .. Attempting to understand what is not taking place.

Let's look at what is:
```

sudo find / -name "libstdc++*"
apt-cache policy gcc

```

And try and determine what should be.

The linker, the linker ... 
[INDENT][INDENT]what is it doing ?
[/INDENT][/INDENT]

---

