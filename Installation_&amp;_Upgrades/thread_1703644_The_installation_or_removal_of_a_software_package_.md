---
title: "The installation or removal of a software package failed."
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by koolashwin on 2011-03-09
i get this error whenever i update or install/uninstall a package
pls help me with this..


Package operation failed
The installation or removal of a software package failed.

installArchives() failed: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 197111 files and directories currently installed.)
Removing grub-customizer ...
Removing hwinfo ...
Removing libhd16 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/usr/bin/mandb: can't set the locale; make sure $LC_* and $LANG are correct
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Rebuilding /usr/share/applications/desktop.en_IN.ISO8859-1.cache...
WARNING: System locale is invalid
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Setting up linux-image-2.6.35-27-generic (2.6.35-27.48) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-27-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
 * dkms: running auto installation service for kernel 2.6.35-27-generic

 *       bcmwl (5.60.48.36+bdcom)...
   ...done.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
/etc/default/grub: 1: If: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-27-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-27-generic; however:
  Package linux-image-2.6.35-27-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.27.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 linux-image-2.6.35-27-generic
 linux-image-generic
 linux-generic
Setting up linux-image-2.6.35-27-generic (2.6.35-27.48) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-27-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
 * dkms: running auto installation service for kernel 2.6.35-27-generic

 *       bcmwl (5.60.48.36+bdcom)...
   ...done.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
/etc/default/grub: 1: If: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-27-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-27-generic; however:
  Package linux-image-2.6.35-27-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.27.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured

---

### Post by IcarusR on 2011-03-09
You need to set the 'local' setting & then try again, see this thread...

[http://ubuntuforums.org/showthread.php?t=1346581]("http://ubuntuforums.org/showthread.php?t=1346581")

---

### Post by koolashwin on 2011-03-11
Its not working....... Im still getting the same error...... but the packages are getting installed......

---

