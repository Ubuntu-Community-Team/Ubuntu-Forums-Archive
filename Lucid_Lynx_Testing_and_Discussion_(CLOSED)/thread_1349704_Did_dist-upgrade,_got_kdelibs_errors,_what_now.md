---
title: "Did dist-upgrade, got kdelibs errors, what now?"
date: 2009-12-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Anagonda on 2009-12-08
Ok, so the thing is: I have had some big problems with flash and now I wanted to try newest ubuntu.

I changed sources.list as usual, did update & dist-upgrade.
But dist-upgrade stopped on:
```

Processing triggers for desktop-file-utils ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs5_4%3a4.3.80-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now if I try re-running dist-upgrade I get:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kdebase-runtime: Depends: kdelibs5 (>= 4:4.3.80) but 4:4.3.2-0ubuntu7 is installed
                   Recommends: pmount but it is not installed or
                               kfreebsd-gnu but it is not installable or
                               hurd but it is not installable
  kdelibs-bin: Depends: kdelibs5 (= 4:4.3.80-0ubuntu1) but 4:4.3.2-0ubuntu7 is installed
  kdepim-runtime: Depends: kdelibs5 (>= 4:4.3.80) but 4:4.3.2-0ubuntu7 is installed
                  Depends: kdepimlibs5 (>= 4:4.3.80) but 4:4.3.2-0ubuntu1 is installed
  libplasma3: Depends: kdelibs5 (>= 4:4.3.80) but 4:4.3.2-0ubuntu7 is installed
  pulseaudio-esound-compat: Depends: libpulse0 (= 1:0.9.21-0ubuntu1) but 1:0.9.19-0ubuntu4 is installed
  pulseaudio-module-bluetooth: Depends: libpulse0 (= 1:0.9.21-0ubuntu1) but 1:0.9.19-0ubuntu4 is installed
  pulseaudio-module-gconf: Depends: libpulse0 (= 1:0.9.21-0ubuntu1) but 1:0.9.19-0ubuntu4 is installed
  pulseaudio-module-lirc: Depends: libpulse0 (= 1:0.9.21-0ubuntu1) but 1:0.9.19-0ubuntu4 is installed
  pulseaudio-module-x11: Depends: libpulse0 (= 1:0.9.21-0ubuntu1) but 1:0.9.19-0ubuntu4 is installed
E: Unmet dependencies. Try using -f.

```

And when I run "apt-get -f install" I get the same error as dist-upgrade gave me on first time.

I'm running karmic, with gnome. I use only E16, but I have all gnome apps etc installed. I have some kde apps too(like k3b). Is this error because of that?

So, what to do? Can I reboot? At the moment I don't have time to sit by my computer, so thats why I'm already asking.

---

### Post by alphacrucis2 on 2009-12-08
> **Anagonda said:**
> Ok, so the thing is: I have had some big problems with flash and now I wanted to try newest ubuntu.

I changed sources.list as usual, did update & dist-upgrade.
But dist-upgrade stopped on:
```

Processing triggers for desktop-file-utils ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs5_4%3a4.3.80-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now if I try re-running dist-upgrade I get:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kdebase-runtime: Depends: kdelibs5 (>= 4:4.3.80) but 4:4.3.2-0ubuntu7 is installed
                   Recommends: pmount but it is not installed or
                               kfreebsd-gnu but it is not installable or
                               hurd but it is not installable
  kdelibs-bin: Depends: kdelibs5 (= 4:4.3.80-0ubuntu1) but 4:4.3.2-0ubuntu7 is installed
  kdepim-runtime: Depends: kdelibs5 (>= 4:4.3.80) but 4:4.3.2-0ubuntu7 is installed
                  Depends: kdepimlibs5 (>= 4:4.3.80) but 4:4.3.2-0ubuntu1 is installed
  libplasma3: Depends: kdelibs5 (>= 4:4.3.80) but 4:4.3.2-0ubuntu7 is installed
  pulseaudio-esound-compat: Depends: libpulse0 (= 1:0.9.21-0ubuntu1) but 1:0.9.19-0ubuntu4 is installed
  pulseaudio-module-bluetooth: Depends: libpulse0 (= 1:0.9.21-0ubuntu1) but 1:0.9.19-0ubuntu4 is installed
  pulseaudio-module-gconf: Depends: libpulse0 (= 1:0.9.21-0ubuntu1) but 1:0.9.19-0ubuntu4 is installed
  pulseaudio-module-lirc: Depends: libpulse0 (= 1:0.9.21-0ubuntu1) but 1:0.9.19-0ubuntu4 is installed
  pulseaudio-module-x11: Depends: libpulse0 (= 1:0.9.21-0ubuntu1) but 1:0.9.19-0ubuntu4 is installed
E: Unmet dependencies. Try using -f.

```

And when I run "apt-get -f install" I get the same error as dist-upgrade gave me on first time.

I'm running karmic, with gnome. I use only E16, but I have all gnome apps etc installed. I have some kde apps too(like k3b). Is this error because of that?

So, what to do? Can I reboot? At the moment I don't have time to sit by my computer, so thats why I'm already asking.

Wait a couple of days. There are dependency conflicts in the Lucid repos at present as they setting up for the first alpha.

---

### Post by slakkie on 2009-12-08
You should have waited a day or so :)

---

### Post by Gina on 2009-12-09
Yes, there are lots of known problems at present being hurriedly fixed for the Alpha 1 due for release late tomorrow.  Meanwhile lots of packages are being held back.

---

### Post by Anagonda on 2009-12-09
Hehe, our house just had a electric cutout, so computer got down too...

Well, first boot just went black after grub.
Second boot with older kernel, "No /dev found", niiice...
Third boot in recovery mode, got to somekind of recovery screen, but boot errors kept coming over it, so I didn't see anything. I had no idea where to go, so I took few steps down and pressed enter. Luckily I hit somekind of recover packages or something. It took like 40min and after that it freezed. So boot again, now normal boot worked, but got me to the normaal console(no X).

There where no network, so ifup, but it said that can't find command. Luckily again, ifconfig eth0 up worked and after that I had to get a ip address with dhclient eth0
After that I just typed apt-get update & apt-get -f install This took like 1 hour!

It worked almost, now I'm in gnome(lost some of E16 configs and haven't yet recovered them). But I have no working nvidia drivers, so this is somekind of generic driver. Works, but is slow as hell and graphics suck.

So, I'm almost happy already. Wrote this only because if there are anyother that has the same problems.

---

