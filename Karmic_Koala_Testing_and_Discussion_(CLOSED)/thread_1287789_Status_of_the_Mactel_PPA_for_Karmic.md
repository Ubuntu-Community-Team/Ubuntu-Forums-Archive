---
title: "Status of the Mactel PPA for Karmic?"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bdash on 2009-10-10
Hi,

I recently installed Karmic on a MacBook Pro 5,5. I turned to the Mactel PPA but I saw that half the packages are not ready.

What's the status? Do we need to wait for the final release of Karmic to get the same support as Jaunty?

[https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa)

---

### Post by alexmurray on 2009-10-11
From what I can see, Karmic doesn't need anything from the mactel repo on my MBP5,1 - the version of applesmc for example in the repo is the same (if not actually older) than the one in the kernel shipped in Karmic. Perhaps some quirks are needed though to enable the keyboard backlight keys since for me this is the only thing that doesn't work out of the box (and since this isn't really a showstopper for me I haven't bothered to investigate how to get it working).

---

### Post by bdash on 2009-10-11
Currently I'm on an MBP5,5 and what's not working is:
* LCD backlight (can't ajust brightness)
* Special keys on the keyboard (to ajust brightness in particular)
* Switch the fn key to use the F1-F12 keys by default
* Sound

I've read some threads involving either using the Jaunty Mactel PPA or installing packages manually, but for now I don't want to do it unless I'm sure there is no clean way to do it (e.g. only with official repos, or by adding a well maintained repo).

After Karmic is officially released if there is still no clean way to get my stuff working I'll do it the "manual" way.

---

### Post by ercoppa on 2009-10-11
On a Macbook 5,1 (not Pro) I need the package nvidia_bl for karmic.

Greets.

---

### Post by CoreyB. on 2009-10-11
To me it looks like there are some packages available for karmic.

[http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages]("http://ppa.launchpad.net/mactel-support/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages")

Including one for keyboard hotkeys.

---

### Post by _mario_ on 2009-10-12
> **ercoppa said:**
> On a Macbook 5,1 (not Pro) I need the package nvidia_bl for karmic.

Greets.

uploaded new versions of mbp_nvidia_bl and nvidia_bl for karmic.

nvidia_bl should work on all models incorporating Nvidia graphics chips. mbp_nvidia_bl currently supports MacBook 5,1 and 5,2, MacBook Air 2,1, and MacBook Pro 3,1, 3,2, 4,1, 5,1, 5,2, and 5,5. Do the numbers in between also exist? E.g. MacBook Pro 5,3, and 5,4? Or MacBook 5,3, ...?

ciao,
Mario

---

### Post by e-rebus on 2009-10-12
> **_mario_ said:**
> uploaded new versions of mbp_nvidia_bl and nvidia_bl for karmic.

nvidia_bl should work on all models incorporating Nvidia graphics chips. mbp_nvidia_bl currently supports MacBook 5,1 and 5,2, MacBook Air 2,1, and MacBook Pro 3,1, 3,2, 4,1, 5,1, 5,2, and 5,5. Do the numbers in between also exist? E.g. MacBook Pro 5,3, and 5,4? Or MacBook 5,3, ...?

ciao,
Mario

I am on Macbook Pro 5,3, so it does exist and mbp_nvidia_bl works fine on it giving me the ability to change LCD brightness with F1/F2 hotkeys.

---

### Post by bdash on 2009-10-13
Hi Mario,

It's good to hear from the Mactel team!

> **_mario_ said:**
> uploaded new versions of mbp_nvidia_bl and nvidia_bl for karmic.


Actually I don't see them here:
[https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=karmic)

Am I missing something? Is there another PPA I should be using?

---

### Post by undoIT on 2009-10-14
> **_mario_ said:**
> uploaded new versions of mbp_nvidia_bl and nvidia_bl for karmic.

nvidia_bl should work on all models incorporating Nvidia graphics chips. mbp_nvidia_bl currently supports MacBook 5,1 and 5,2, MacBook Air 2,1, and MacBook Pro 3,1, 3,2, 4,1, 5,1, 5,2, and 5,5. Do the numbers in between also exist? E.g. MacBook Pro 5,3, and 5,4? Or MacBook 5,3, ...?

ciao,
Mario

Hi Mario. Where where these uploaded?

---

### Post by undoIT on 2009-10-14
Okay. I figured out that I need the Jaunty sources to get the brightness controls working with Macbook 5,1 (in addition to pommed from Karmic sources, not sure if pommed is needed).

```
deb http://ppa.launchpad.net/mactel-support/ubuntu jaunty main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu jaunty main
```

Then from the Jaunty repos installed:

```
sudo apt-get install nvidia-bl-dkms
```

Then added:

```
gksudo gedit /etc/modules
```
> nvidia_bl shift=5
coretemp
applesmc 

To make the brightness settings stick between reboots:

```
gksudo gedit /etc/init.d/backlight-set
```
> #! /bin/sh

case "$1" in
    start)
        echo `cat /root/.backlight` > /sys/class/backlight/nvidia_backlight/brightness
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        cat /sys/class/backlight/nvidia_backlight/actual_brightness > /root/.backlight
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```
sudo update-rc.d backlight-set defaults
```
```
sudo chmod +x /etc/init.d/backlight-set
```

Now the only things left are that the keyboard backlight always resets to 50%, I can't turn it off.

Also, the trick for swapping the fnmode so that fn key is used for keyboard shortcuts (brightness adjustment etc) no longer works. I tried this:

```
gksudo gedit /etc/modprobe.d/options
```
> options hid_apple fnmode=2
```
sudo update-initramfs -u -v -k `uname -r`
```

and then reboot.

Anybody know how to get this working?

---

### Post by _mario_ on 2009-10-16
> **bdash said:**
> Hi Mario,

It's good to hear from the Mactel team!

Actually I don't see them here:
[https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=karmic)

Am I missing something? Is there another PPA I should be using?

yes. there appears to be a problem. i don't get notifications via e-mail after uploading nor do those packages appear. please, stick to the jaunty packages for now.

ciao,
Mario

---

### Post by _mario_ on 2009-10-16
> **undoIT said:**
> Okay. I figured out that I need the Jaunty sources to get the brightness controls working with Macbook 5,1 (in addition to pommed from Karmic sources, not sure if pommed is needed).


you shouldn't need pommed anymore.

> **undoIT said:**
> 
Then added to /etc/modules:
```

nvidia_bl shift=2

```


you don't need the shift option anymore. it was only required for intrepid.

> **undoIT said:**
> 
Also, the trick for swapping the fnmode so that fn key is used for keyboard shortcuts (brightness adjustment etc) no longer works. I tried this in /etc/modprobe.d/options:
```

options hid_apple fnmode=2

```
Anybody know how to get this working?


yes. the module hid**_**apple has been renamed to hid**-**apple in the meanwhile.

ciao,
Mario

---

### Post by undoIT on 2009-10-16
> **_mario_ said:**
> you shouldn't need pommed anymore.

you don't need the shift option anymore. it was only required for intrepid.

yes. the module hid**_**apple has been renamed to hid**-**apple in the meanwhile.

ciao,
Mario

aha, as a web developer i prefer hyphens over underscores as well ;)

after uninstalling pommed, screen and keyboad brightness adjustments do not work. it looks like options hid_apple fnmode=2 is required at least on macbook 5,1 because it started working again after i added this. keyboard backlight is stuck on with no adjustment.

glad that pommed is not required. it seemed to be causing a lot of wakeups. is there a way to manually turn off the keyboard backlight?

---

### Post by _mario_ on 2009-10-20
> **undoIT said:**
> 
after uninstalling pommed, screen and keyboad brightness adjustments do not work.

you're right. neither the brightness keys nor the media player keys do work anymore after upgrading to karmic.

> **undoIT said:**
> 
is there a way to manually turn off the keyboard backlight?

not using the function keys. but in the meantime you can use the attached script.

ciao,
Mario

---

### Post by Hiram on 2009-10-23
> **_mario_ said:**
> you don't need the shift option anymore. it was only required for intrepid.

ciao,
Mario

In my experience it works better when using shift=5 the max brightness is way better. but i think that is something to experiment with.


The guide above installs more then needed btw. In karmic everything is already working except the backlight. You only need nvidia_bl from jaunty and the part about /etc/modules

---

### Post by undoIT on 2009-10-23
> **Hiram said:**
> In my experience it works better when using shift=5 the max brightness is way better. but i think that is something to experiment with.


The guide above installs more then needed btw. In karmic everything is already working except the backlight. You only need nvidia_bl from jaunty and the part about /etc/modules

indeed. i uninstalled applesmc-dkms and hal-applesmc. everything is still working so i guess you just need the lines in /etc/modules to get the sensors properly recognized.

i didn't notice much of a difference with shift=5. is t just that the brightness adjustment has a finer-grain?

---

### Post by kosumi68 on 2009-10-24
> 
Also, the trick for swapping the fnmode so that fn key is used for keyboard shortcuts (brightness adjustment etc) no longer works. I tried this:

```
gksudo gedit /etc/modprobe.d/options
```

```
sudo update-initramfs -u -v -k `uname -r`
```

and then reboot.

Anybody know how to get this working?


With pommed installed, you also need to change /etc/pommed.conf to use the right fnmode settings.

---

