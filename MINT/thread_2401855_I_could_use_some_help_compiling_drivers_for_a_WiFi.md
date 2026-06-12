---
title: "I could use some help compiling drivers for a WiFi adapter"
date: 2018-09-23
forum: MINT
---

### Post by drpeppercan on 2018-09-23
Specs: LM Sylvia - Mate

This are the [instructions]("https://github.com/diederikdehaas/rtl8812AU#dkms").
I already installed dkms.

But this is what I'm getting with the first command line: 
```
**sudo DRV_NAME=rt18812AU**
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] file ...

```

I don't suppose this is what I should be getting, right?

Thanks

---

### Post by sisco311 on 2018-09-23
You don't have to put sudo in front of the commands. Just copy/paste the second set of commands which are prefixed with the $ sign.

---

### Post by drpeppercan on 2018-09-23
Ok, that helped. For some time.
When I tried 
```
sudo /usr/src/${DRV_NAME}-${DRV_VERSION}
```

I got: 

```
sudo: /usr/src/rt18812AU-4.3.20: command not found
```

What gives?

---

### Post by jeremy31 on 2018-09-23
Those instructions are messed up
```
DRV_NAME=rtl8812AU
DRV_VERSION=4.3.20
sudo dkms add -m ${DRV_NAME} -v ${DRV_VERSION}
sudo dkms build -m ${DRV_NAME} -v ${DRV_VERSION}
sudo dkms install -m ${DRV_NAME} -v ${DRV_VERSION}
```

---

### Post by drpeppercan on 2018-09-23
Thank you so much jeremy31!
I am so glad it wasn't all on me!
I'll try it asap!

---

### Post by drpeppercan on 2018-09-23
```
sudo dkms add -m ${DRV_NAME} -v ${DRV_VERSION}
[sudo] password for javier: 
Error! Could not find module source directory.
Directory: /usr/src/rt18812AU-4.3.20 does not exist.
```

Then I expanded the "rtl8812AU-driver-4.3.20.zip" file. And went inside its directory. From that directory I opened a terminal with "Open in terminal".
And tried that command line again:

```
sudo dkms add -m ${DRV_NAME} -v ${DRV_VERSION}
[sudo] password for javier: 
Error! Invalid number of arguments passed.
Usage: add <module>/<module-version> or
       add -m <module>/<module-version> or
       add -m <module> -v <module-version>



```

Next try I replaced the "$" for a space in "-v {DRV_VERSION}"
```
javier@javier-linuxmint ~/Downloads/rtl8812AU-driver-4.3.20 $ sudo dkms add -m ${DRV_NAME} **[COLOR=#ff0000]-v {DRV_VERSION}[/COLOR]**
: I do not know how to handle {DRV_VERSION}.
Error! Invalid number of arguments passed.
Usage: add <module>/<module-version> or
       add -m <module>/<module-version> or
       add -m <module> -v <module-version>

```

Next I replaced the "_" for a "-":
```
javier@javier-linuxmint ~/Downloads/rtl8812AU-driver-4.3.20 $ sudo dkms add -m ${DRV_NAME} -v {DRV[COLOR=#ff0000]**-**[/COLOR]VERSION}
: I do not know how to handle {DRV-VERSION}.
Error! Invalid number of arguments passed.
Usage: add <module>/<module-version> or
       add -m <module>/<module-version> or
       add -m <module> -v <module-version>

```
What's next?

---

### Post by jeremy31 on 2018-09-23
Let's try going into the downloads folder and renaming that folder to just rtl8812AU instead of rtl8812AU-driver-4.3.20
then go into the directory, open the dkms.conf file and lets change a line
```
PACKAGE_VERSION="#MODULE_VERSION#"
```
Make that be
```
PACKAGE_VERSION=4.3.20
```
Save and exit, open terminal and do
```
cd Downloads
sudo dkms add ./rtl8812AU
sudo dkms install rtl8812AU/4.3.20

```
If no errors reboot

---

### Post by drpeppercan on 2018-09-23
So I guess it worked!

```
sudo dkms install rtl8812AU/4.3.20

Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
'make' KVER=4.15.0-34-generic.......................
cleaning build area....


DKMS: build completed.


8812au.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-34-generic/updates/dkms/


depmod..........


DKMS: install completed.



```

I'll reboot now.

So I guess the WiFi adapter should be recognized and work when I'm back...
I'll let you know.

---

### Post by drpeppercan on 2018-09-23
Hopefully there's still something else to do, because I rebooted, then plugged the new USB WiFi adapter, and still is not recognized. Just nothing happens.
Other than addressing this to the manufacturer's forum, do you have any other ideas jeremy31 ?

Thanks a lot for your help jeremy31 :)

---

### Post by jeremy31 on 2018-09-23
Is Secure Boot disabled?  Check ```
mokutil --sb-state
```

---

### Post by drpeppercan on 2018-09-23
```
mokutil --sb-state
EFI variables are not supported on this system
```

I think it's not

---

### Post by jeremy31 on 2018-09-23
See the wifi script link in my signature and post results

---

### Post by drpeppercan on 2018-09-23
Ok.
I suppose I should plug the new USB WiFi adapter before running the script, right?

---

### Post by drpeppercan on 2018-09-23
Silly me!
I can't plug the new adapter for this, then I would disconnect :(

But here's my report: [https://pastebin.com/WtpKKXMF](https://pastebin.com/WtpKKXMF)
Btw, for whatever is worth, I went to the manufacturer's site. He has this [ZIP file with an .sh file inside]("http://www.edup-link.com/download/download-11-746.html"). That should be easier, right?

---

### Post by jeremy31 on 2018-09-24
Plug the new adapter in and post results for ```
lsusb
```

---

### Post by drpeppercan on 2018-09-24
I have another one plugged at the moment. Should I plug the new one alongside it?

---

### Post by jeremy31 on 2018-09-24
Yes, I would like to see the USB ID for that wifi

---

### Post by drpeppercan on 2018-09-24
```
lsusb
Bus 003 Device 004: ID 0bda:0811 Realtek Semiconductor Corp. 
Bus 003 Device 003: ID 0846:9040 NetGear, Inc. WNA1000 Wireless-N 150 [Atheros AR9170+AR9101]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1bcf:0053 Sunplus Innovation Technology Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```

#3 is the old WiFi adapter, NetGear
#4 I believe is the mouse. I am not certain because the mouse doesn't have a brand printed. 
But I found a screenshot (see attached img) of a similar USBs list, except that one does show at the end of the text line "optical mouse". So, chances are my mouse if made/sold, by Sunplus Innovation Tech too.

But I don't see where the Edup-Link Wifi adapter is. It is not showing a light, as the old one. But it does when it is with Windows 10.

[ATTACH=CONFIG]281177[/ATTACH]

---

### Post by drpeppercan on 2018-09-24
Also, I just tried installing "[ac6607 Linux.zip]("http://www.edup-link.com/download/download-11-746.html")" , but it yielded this errors:

```

[COLOR=#ff0000]**error**[/COLOR]: &#8216;_timer {aka struct timer_list}&#8217; has no member named &#8216;data&#8217;
  ptimer->data = (unsigned long)cntx;
        ^
/home/javier/Downloads/ac6607/RTL88x2BU_WiFi_linux_v5.2.4.1_22719_COEX20170518-4444.20170613/driver/rtl88x2BU_WiFi_linux_v5.2.4.1_22719.20170613_COEX20170518-4444/include/osdep_service_linux.h:283:2: error: implicit declaration of function &#8216;init_timer&#8217; [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^
In file included from /home/javier/Downloads/ac6607/RTL88x2BU_WiFi_linux_v5.2.4.1_22719_COEX20170518-4444.20170613/driver/rtl88x2BU_WiFi_linux_v5.2.4.1_22719.20170613_COEX20170518-4444/include/drv_types.h:27:0,
                 from /home/javier/Downloads/ac6607/RTL88x2BU_WiFi_linux_v5.2.4.1_22719_COEX20170518-4444.20170613/driver/rtl88x2BU_WiFi_linux_v5.2.4.1_22719.20170613_COEX20170518-4444/core/rtw_cmd.c:17:
/home/javier/Downloads/ac6607/RTL88x2BU_WiFi_linux_v5.2.4.1_22719_COEX20170518-4444.20170613/driver/rtl88x2BU_WiFi_linux_v5.2.4.1_22719.20170613_COEX20170518-4444/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/home/javier/Downloads/ac6607/RTL88x2BU_WiFi_linux_v5.2.4.1_22719_COEX20170518-4444.20170613/driver/rtl88x2BU_WiFi_linux_v5.2.4.1_22719.20170613_COEX20170518-4444/include/osdep_service.h:355:2: [COLOR=#ff0000]**error**[/COLOR]: implicit declaration of function &#8216;allow_signal&#8217; [-Werror=implicit-function-declaration]
  allow_signal(SIGTERM);



```

---

### Post by jeremy31 on 2018-09-24
Don't try to install any more drivers, but do a ```
modprobe -c | grep -i 0bda | grep 0811
```
See what it shows for results

---

### Post by drpeppercan on 2018-09-24
It didn't do a thing.

---

### Post by jeremy31 on 2018-09-24
Ok, we need to use different source code, with the old wifi dongle 
```
sudo apt install git
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
sudo make -f Makefile.dkms install
```

Reboot and the new dongle should function

---

### Post by drpeppercan on 2018-09-24
YES!!!!!!
Thank you so much jeremy31 :)

So, should I need to do this again in the future, all I need to do is the commands in your last post?

---

### Post by jeremy31 on 2018-09-24
If you happen to install a new kernel version, you might need to download a newer version from git but I would doubt you will have any issues with the 4.15 kernels and the wifi should work after rebooting into a newer 4.15 kernel without having to recompile since dkms is used.

---

### Post by drpeppercan on 2018-09-24
Ok.
Thanks a bunch again jeremy31 :)

Cheers!

---

