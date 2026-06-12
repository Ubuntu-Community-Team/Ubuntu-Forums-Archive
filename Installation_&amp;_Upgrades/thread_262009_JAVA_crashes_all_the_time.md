---
title: "JAVA crashes all the time"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by ashrack on 2006-09-21
Whenever I access this page JAVA crashes:
[www.chat386.com](www.chat386.com)
but other pages work fine.

and here's the error log:
```
firefox
GTK Accessibility Module initialized

(Gecko:5313): GLib-GObject-WARNING **: gsignal.c:1017: unable to lookup signal "activate" of unloaded type `MaiAtkObject'

(Gecko:5313): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `signal_id > 0' failed
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb19f8b02, pid=5326, tid=2976021424
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x34b02]
#
# An error report file with more information is saved as hs_err_pid5326.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
INTERNAL ERROR on Browser End: Write failed. send_msg

System error?:: Broken pipe

```
I can confirm this bug from 6PCs running UBUNTU DAPPER with all of updates

---

### Post by ashrack on 2006-09-23
could U at least click on this link
[www.chat386.com](www.chat386.com)
and tell me whether it crashed your browser or not and also specify which browser U are using.

---

### Post by wpshooter on 2006-09-23
Ashrack:

When I click on it what it tells me is that I need a JAVA plugin in order to run it properly on Firefox.  When I click on the button that it provides me to use to install JAVA, it comes back and says that it can not do it automaticallly and that I will have to download and install it manually.

Please note that I have tried following the instructions that are given in the manual download on the JAVA site and I have never been able to get this to sucessfully work.

I have also, tried to install the JAVA program thru the AUTOMATIX program but it also did not install everything that was needed to get JAVA to function correctly with Firefox.

BOY, I SURE WISH SOMEBODY WOULD FIX THIS.

Good luck.

---

### Post by samlalani on 2006-09-23
My firefox doesn't crash, it just says I need the Java plugin.  I tried following the instructions, including putting a symbolic link to libjavaplugin_oji.so in my firefox/plugins directory.  However, firefox still does not see the Java plugin.  When I go to about:plugins, it tell me: No plug-ins are installed.  I have restarted the computer and it still tells me I have no plug-ins.

---

### Post by ashrack on 2006-09-24
do only thing I did do get JAVA working in DAPPER was:
```
aptitude install sun-java5-plugin
```
and JAVA started working in FF and EPIPHANY!

But what about U other ppl, who have functional JAVA in FF, does it crash for U when U click on the afore mentined link or not!
I really need your feedback

---

### Post by shoagun on 2006-09-26
ashrack,

when I click on the link firefox starts to open the page and then closes.  in general, i've been having lots of trouble with firefox crashing at certain pages.

---

### Post by ashrack on 2006-09-27
The same as for me! 
We should file a bug report! But dont know whether on JAVA or on UBUNTUs LUNCHPAD.
Any ideas_

---

### Post by Will5639 on 2006-10-16
> **ashrack said:**
> The same as for me! 
We should file a bug report! But dont know whether on JAVA or on UBUNTUs LUNCHPAD.
Any ideas_

Similar problems here....

Normally Java works fine, but when an IRC-Applet is thrown into the mix it crashes.

Does Java-Linux have IRC support?

---

