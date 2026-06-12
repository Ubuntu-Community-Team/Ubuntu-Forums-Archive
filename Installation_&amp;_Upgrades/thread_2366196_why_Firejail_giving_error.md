---
title: "why Firejail giving error?"
date: 2017-07-14
forum: Installation &amp; Upgrades
---

### Post by bijaydeyp on 2017-07-14
Hi all
I am a home-user & have installed Firejail 'firejail_0.9.40-3_i386.deb' with Gdebi installer. when launching Firefox via Terminal , it gives following errors...

$firejail firefox
Reading profile /etc/firejail/firefox.profile
Reading profile /etc/firejail/disable-common.inc
Reading profile /etc/firejail/disable-programs.inc
Reading profile /etc/firejail/disable-devel.inc
Reading profile /etc/firejail/whitelist-common.inc
Parent pid 2212, child pid 2213
Blacklist violations are logged to syslog

Child process initialized

(firefox:2): GLib-GObject-CRITICAL **: g_object_ref: assertion 'object->ref_count > 0' failed

(firefox:2): GLib-GObject-CRITICAL **: g_object_unref: assertion 'object->ref_count > 0' failed

(firefox:2): GLib-GObject-CRITICAL **: g_object_ref: assertion 'object->ref_count > 0' failed

(firefox:2): GLib-GObject-CRITICAL **: g_object_unref: assertion 'object->ref_count > 0' failed
|
|
|
|
_After closing Firefox it's showing again_ .....

(firefox:2): GLib-GObject-CRITICAL **: g_object_ref: assertion 'object->ref_count > 0' failed

(firefox:2): GLib-GObject-CRITICAL **: g_object_unref: assertion 'object->ref_count > 0' failed

(firefox:2): GLib-GObject-CRITICAL **: g_object_ref: assertion 'object->ref_count > 0' failed

(firefox:2): GLib-GObject-CRITICAL **: g_object_unref: assertion 'object->ref_count > 0' failed

(firefox:2): GLib-GObject-CRITICAL **: g_object_ref: assertion 'object->ref_count > 0' failed

(firefox:2): GLib-GObject-CRITICAL **: g_object_unref: assertion 'object->ref_count > 0' failed

(firefox:2): GLib-GObject-CRITICAL **: g_object_ref: assertion 'object->ref_count > 0' failed

(firefox:2): GLib-GObject-CRITICAL **: g_object_unref: assertion 'object->ref_count > 0' failed

(firefox:2): GLib-GObject-CRITICAL **: g_object_ref: assertion 'object->ref_count > 0' failed

(firefox:2): GLib-GObject-CRITICAL **: g_object_unref: assertion 'object->ref_count > 0' failed

Parent is shutting down, bye...

------------------------------------------------------------------------------------------------------
my question: did the installations of Firejail/Firefox go wrong? or it has a bug? (ref-  [https://people.canonical.com/~ubuntu-security/cve/2017/CVE-2017-5940.html](https://people.canonical.com/~ubuntu-security/cve/2017/CVE-2017-5940.html))  how can I fix it? also how to verify correct installation?

my system: Ubuntu 14.04 32-bit. Linux 4.4.0-83-generic.

---

### Post by vasa1 on 2017-07-14
I think it has more to do with Firefox than with firejail. You could test that yourself by running Firefox without firejail and seeing what appears in the terminal.

If, Firefox (both normal and firejailed) are running to your satisfaction, you can probably ignore the terminal output despite the "critical"!

See [https://askubuntu.com/questions/422254/why-are-there-so-many-console-messages-from-gtk-applications](https://askubuntu.com/questions/422254/why-are-there-so-many-console-messages-from-gtk-applications)

---

### Post by bijaydeyp on 2017-07-18
oh! I got it.:P

---

