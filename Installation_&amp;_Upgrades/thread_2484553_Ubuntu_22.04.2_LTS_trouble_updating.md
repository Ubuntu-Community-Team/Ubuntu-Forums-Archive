---
title: "Ubuntu 22.04.2 LTS trouble updating"
date: 2023-03-02
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2023-03-02
Get this message: 
[IMG]https://i.postimg.cc/pr8bQ40H/image-2023-03-02-145545561.png[/IMG]

Click on, Install now, and it always fails but a few minutes later get the same message to update again. Try to and it fails repeatedly.

Auto updater/installer for 22.04 has been giving me problems since going to 22.04. This never happened with 20.04 LTS which installed updates very smoothly.

On 22.04 have been using ' sudo apt update ' and ' sudo apt upgrade ' for updates which works better but have to do it all manually now.

Why won't auto updater/installer work as smoothly for 22.04 as it did for 20.04?
In Software and Updates > Updates, all was selected to automatically check for updates but it doesn't do that for 22.04 and won't install many updates after downloading them.

Help?

Also when going into Ubuntu Software Store, it show a red dot indicating there are updates for chromium browser. I click on Update All and get a message in a little black bax saying: Unable to update chromiun: snap has no updates available

Help?

---

### Post by monkeybrain20122 on 2023-03-02
It is a feature, not a bug.  It can be confusing.

[https://ubuntu.com/server/docs/about-apt-upgrade-and-phased-updates](https://ubuntu.com/server/docs/about-apt-upgrade-and-phased-updates)

---

### Post by cybrsaylr on 2023-03-02
Thanks monkeybrain, it is confusing. 

Also in Software & Updates > Other Software, I can't add any other, 'https://ppa. launchpadcontent' stuff anymore. It appears all is blocked from doing so now. in 20.04 I had several entries listed there as other ppas were added. In 22.04 there are only two listed and it seems no more can be added for like, Skype, Chrome and Opera browsers and anything else I may want to add in the future.

Very confused?

---

### Post by monkeybrain20122 on 2023-03-02
I have no problems adding ppas. Can you give more details?

---

### Post by cybrsaylr on 2023-03-02
It's hard to do as in 20.04 when adding new apps/programs this was all done automatically. I never had to manually add the associated ppa into Software & Updates > Other Software. Now in 22.04 when trying to manually add a ppa it never went through or showed it was even possible. 

Suspect I was not doing it with the right code.

---

### Post by cybrsaylr on 2023-03-02
Here's the example for 20.04:
[IMG]https://i.postimg.cc/76JLCx2P/20-04-Software-Updates.png[/IMG]

And 22.04 currently:
[IMG]https://i.postimg.cc/NGWHknsP/image-2023-03-02-160555575.png[/IMG]

In both cases all ppas were auto added. I never manually added them.

---

### Post by monkeybrain20122 on 2023-03-02
That is very odd. I added all ppas myself from a fresh install of Ubuntu. How did you install Ubuntu? Which flavor is it? e.g LXLE (a respin of Lubuntu) added a lot of ppas by default (which is a very bad idea IMO) and some Ubuntu OEMs would activate their own ppas (e.g system 76, but those are for hardware tweaks and patches)

---

### Post by ajgreeny on 2023-03-02
Forget using the GUI means of updating for the moment and run command ```
sudo apt update
``` and please show us the complete terminal output including the command to make sure we get everything.
Please also use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by cybrsaylr on 2023-03-02
Installed Ubuntu 22.04.2 LTS 64 bit, GNOME Version 42.5, Windowing System Wayland, off an ISO file, I burned to DVD using Brasero. Brasero auto checksum test found no errors when run.

---

### Post by cybrsaylr on 2023-03-02
> **ajgreeny said:**
> Forget using the GUI means of updating for the moment and run command ```
sudo apt update
``` and please show us the complete terminal output including the command to make sure we get everything.
Please also use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

Here you go ajgreeny:

```

$ sudo apt update

Hit:1 https://mirror.clarkson.edu/ubuntu jammy InRelease
Hit:2 http://archive.ubuntu.com/ubuntu jammy InRelease
Get:3 https://mirror.clarkson.edu/ubuntu jammy-updates InRelease [119 kB]
Get:4 https://mirror.clarkson.edu/ubuntu jammy-backports InRelease [107 kB]
Get:5 https://mirror.clarkson.edu/ubuntu jammy-security InRelease [110 kB]
Hit:6 https://deb.opera.com/opera-stable stable InRelease
Hit:7 https://ppa.launchpadcontent.net/aud...der/ppa/ubuntu jammy InRelease
Get:8 https://mirror.clarkson.edu/ubuntu jammy-updates/main Sources [362 kB]
Get:9 https://mirror.clarkson.edu/ubuntu jammy-updates/universe Sources [208 kB]
Get:10 https://mirror.clarkson.edu/ubuntu jammy-updates/main i386 Packages [455 kB]
Get:11 https://mirror.clarkson.edu/ubuntu jammy-updates/main amd64 Packages [939 kB]
Get:12 https://mirror.clarkson.edu/ubuntu jammy-updates/main Translation-en [203 kB]
Get:13 https://mirror.clarkson.edu/ubuntu jammy-updates/main amd64 DEP-11 Metadata [102 kB]
Get:14 https://mirror.clarkson.edu/ubuntu jammy-updates/universe amd64 Packages [877 kB]
Get:15 https://mirror.clarkson.edu/ubuntu jammy-updates/universe i386 Packages [600 kB]
Get:16 https://mirror.clarkson.edu/ubuntu jammy-updates/universe Translation-en [172 kB]
Get:17 https://mirror.clarkson.edu/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [269 kB]
Get:18 https://mirror.clarkson.edu/ubuntu jammy-updates/universe amd64 c-n-f Metadata [17.9 kB]
Get:19 https://mirror.clarkson.edu/ubuntu jammy-updates/multiverse amd64 DEP-11 Metadata [940 B]
Get:20 https://mirror.clarkson.edu/ubuntu jammy-backports/main amd64 DEP-11 Metadata [7,984 B]
Get:21 https://mirror.clarkson.edu/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [12.5 kB]
Get:22 https://mirror.clarkson.edu/ubuntu jammy-security/main Sources [159 kB]
Hit:23 https://ppa.launchpadcontent.net/nic.../stable/ubuntu jammy InRelease
Get:24 https://mirror.clarkson.edu/ubuntu jammy-security/main amd64 Packages [680 kB]
Get:25 https://mirror.clarkson.edu/ubuntu jammy-security/main i386 Packages [265 kB]
Get:26 https://mirror.clarkson.edu/ubuntu jammy-security/main Translation-en [139 kB]
Get:27 https://mirror.clarkson.edu/ubuntu jammy-security/main amd64 DEP-11 Metadata [41.5 kB]
Get:28 https://mirror.clarkson.edu/ubuntu jammy-security/main amd64 c-n-f Metadata [8,524 B]
Get:29 https://mirror.clarkson.edu/ubuntu jammy-security/universe i386 Packages [512 kB]
Get:30 https://mirror.clarkson.edu/ubuntu jammy-security/universe amd64 Packages [696 kB]
Get:31 https://mirror.clarkson.edu/ubuntu jammy-security/universe amd64 DEP-11 Metadata [17.1 kB]
Get:32 https://mirror.clarkson.edu/ubuntu jammy-security/universe amd64 c-n-f Metadata [13.5 kB]
Fetched 7,092 kB in 2s (3,348 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
28 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

---

### Post by ajgreeny on 2023-03-02
Well, there are no errors showing in that output, so now as a follow-up run command ```
apt list --upgradable && sudo apt full-upgrade
``` and once again show us the full output in code tags which will show us the packages upgradable but then show us which ones are being held back by **"phased updates"**.

---

### Post by cybrsaylr on 2023-03-02
Here you go:
```

$ apt list --upgradable && sudo apt full-upgrade
Listing... Done
chromium-codecs-ffmpeg-extra/jammy-updates 1:85.0.4183.83-0ubuntu2.22.04.1 amd64 [upgradable from: 1:85.0.4183.83-0ubuntu2]
evince-common/jammy-updates,jammy-updates 42.3-0ubuntu3 all [upgradable from: 42.3-0ubuntu2]
evince/jammy-updates 42.3-0ubuntu3 amd64 [upgradable from: 42.3-0ubuntu2]
gir1.2-pango-1.0/jammy-updates 1.50.6+ds-2ubuntu1 amd64 [upgradable from: 1.50.6+ds-2]
gnome-remote-desktop/jammy-updates 42.7-0ubuntu1 amd64 [upgradable from: 42.3-0ubuntu1]
grub-efi-amd64-bin/jammy-updates 2.06-2ubuntu14.1 amd64 [upgradable from: 2.06-2ubuntu14]
grub-efi-amd64-signed/jammy-updates 1.187.3~22.04.1+2.06-2ubuntu14.1 amd64 [upgradable from: 1.187.2+2.06-2ubuntu14]
libevdocument3-4/jammy-updates 42.3-0ubuntu3 amd64 [upgradable from: 42.3-0ubuntu2]
libevview3-3/jammy-updates 42.3-0ubuntu3 amd64 [upgradable from: 42.3-0ubuntu2]
libmbim-glib4/jammy-updates 1.28.0-1~ubuntu20.04.1 amd64 [upgradable from: 1.26.2-1build1]
libmbim-proxy/jammy-updates 1.28.0-1~ubuntu20.04.1 amd64 [upgradable from: 1.26.2-1build1]
libmm-glib0/jammy-updates 1.20.0-1~ubuntu22.04.1 amd64 [upgradable from: 1.18.6-1]
libpango-1.0-0/jammy-updates 1.50.6+ds-2ubuntu1 amd64 [upgradable from: 1.50.6+ds-2]
libpangocairo-1.0-0/jammy-updates 1.50.6+ds-2ubuntu1 amd64 [upgradable from: 1.50.6+ds-2]
libpangoft2-1.0-0/jammy-updates 1.50.6+ds-2ubuntu1 amd64 [upgradable from: 1.50.6+ds-2]
libpangoxft-1.0-0/jammy-updates 1.50.6+ds-2ubuntu1 amd64 [upgradable from: 1.50.6+ds-2]
libqmi-glib5/jammy-updates 1.32.0-1ubuntu0.22.04.1 amd64 [upgradable from: 1.30.4-1]
libqmi-proxy/jammy-updates 1.32.0-1ubuntu0.22.04.1 amd64 [upgradable from: 1.30.4-1]
libsasl2-2/jammy-updates 2.1.27+dfsg2-3ubuntu1.2 amd64 [upgradable from: 2.1.27+dfsg2-3ubuntu1.1]
libsasl2-modules-db/jammy-updates 2.1.27+dfsg2-3ubuntu1.2 amd64 [upgradable from: 2.1.27+dfsg2-3ubuntu1.1]
libsasl2-modules-gssapi-mit/jammy-updates 2.1.27+dfsg2-3ubuntu1.2 amd64 [upgradable from: 2.1.27+dfsg2-3ubuntu1.1]
libsasl2-modules/jammy-updates 2.1.27+dfsg2-3ubuntu1.2 amd64 [upgradable from: 2.1.27+dfsg2-3ubuntu1.1]
modemmanager/jammy-updates 1.20.0-1~ubuntu22.04.1 amd64 [upgradable from: 1.18.6-1]
python3-software-properties/jammy-updates,jammy-updates 0.99.22.6 all [upgradable from: 0.99.22.5]
shim-signed/jammy-updates 1.51.3+15.7-0ubuntu1 amd64 [upgradable from: 1.51+15.4-0ubuntu9]
software-properties-common/jammy-updates,jammy-updates 0.99.22.6 all [upgradable from: 0.99.22.5]
software-properties-gtk/jammy-updates,jammy-updates 0.99.22.6 all [upgradable from: 0.99.22.5]
sudo/jammy-security 1.9.9-1ubuntu2.3 amd64 [upgradable from: 1.9.9-1ubuntu2.2]
N: Ignoring '99fix-opera' in directory '/etc/apt/apt.conf.d/' as it is not a regular file

```

---

### Post by ian-weisser on 2023-03-03
You did half of what was asked. Don't forget to do the rest.

> **ajgreeny said:**
> ...then show us which ones are being held back by **"phased updates"**.

---

### Post by cybrsaylr on 2023-03-03
ian-weisser, how do I do the rest?

Never did this before.

---

### Post by ian-weisser on 2023-03-03
For each package on the list, check 

```
apt policy <package_name>
``` 


Here's an example on a 22.10 system:

```

$ apt policy libsasl2-2
libsasl2-2:
  Installed: 2.1.27+dfsg2-3ubuntu1.2
  Candidate: 2.1.27+dfsg2-3ubuntu1.2
  Version table:
 *** 2.1.27+dfsg2-3ubuntu1.2 500 **(phased 60%)**
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.1.27+dfsg2-3ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

See the part that I've bolded "**(phased 60%)**"?
That means Phased Updates. Simply wait another week or so, and those will upgrade normally. You need to nothing about them at all. Just be patient.
Packages that are NOT phasing will simply be blank in that space. "(phased 0%)" still means Phased Updates.

@ajgreeny asked to see which of those packages are phasing, and which of those packages aren't.

---

### Post by ubfan1 on 2023-03-03
The list of phased packages may be found at [https://people.canonical.com/~ubuntu-archive/phased-updates.html?_ga=2.113925767.1817332164.1677868581-1554721453.1596563830](https://people.canonical.com/~ubuntu-archive/phased-updates.html?_ga=2.113925767.1817332164.1677868581-1554721453.1596563830)

---

### Post by ajgreeny on 2023-03-03
Just run again the second part of that command I gave you, ie ```
sudo apt full-upgrade
```which will tell you what it is going to do by listing all packages previously listed for upgrade but also showing which are going to be held-back

---

### Post by monkeybrain20122 on 2023-03-03
See this [thread]("https://ubuntuforums.org/showthread.php?t=2477612") on phased updates



I still find this part very odd. 

> In both cases all ppas were auto added. I never manually added them. 						

Any explanation?

---

### Post by cybrsaylr on 2023-03-04
> **ajgreeny said:**
> Just run again the second part of that command I gave you, ie ```
sudo apt full-upgrade
```which will tell you what it is going to do by listing all packages previously listed for upgrade but also showing which are going to be held-back

Ok do that and got this:

```

$ sudo apt full-upgrade

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libopenexr25
Learn more about Ubuntu Pro at https://ubuntu.com/pro
The following packages have been kept back:
  gnome-remote-desktop grub-efi-amd64-bin grub-efi-amd64-signed
  python3-software-properties shim-signed software-properties-common
  software-properties-gtk tcpdump ubuntu-advantage-tools
The following packages will be upgraded:
  chromium-codecs-ffmpeg-extra evince evince-common gir1.2-pango-1.0
  libevdocument3-4 libevview3-3 libmbim-glib4 libmbim-proxy libmm-glib0
  libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpangoxft-1.0-0
  libqmi-glib5 libqmi-proxy libsasl2-2 libsasl2-modules libsasl2-modules-db
  libsasl2-modules-gssapi-mit modemmanager
20 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 0 B/3,667 kB of archives.
After this operation, 1,054 kB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

Left all at that and did not click Y to continue.

---

### Post by ajgreeny on 2023-03-05
That output (see below) shows, as I thought it would, that you have 9 packages that have been held back by the Phased Updates system which is explaiened more in that link in monkeybrain20212's post above and 20 that have been upgraded.
```
The following packages have been kept back:
  gnome-remote-desktop grub-efi-amd64-bin grub-efi-amd64-signed
  python3-software-properties shim-signed software-properties-common
  software-properties-gtk tcpdump ubuntu-advantage-tools
The following packages will be upgraded:
  chromium-codecs-ffmpeg-extra evince evince-common gir1.2-pango-1.0
  libevdocument3-4 libevview3-3 libmbim-glib4 libmbim-proxy libmm-glib0
  libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpangoxft-1.0-0
  libqmi-glib5 libqmi-proxy libsasl2-2 libsasl2-modules libsasl2-modules-db
  libsasl2-modules-gssapi-mit modemmanager
20 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
```
Just accept that those packages will be held back but continue with he updates and all should be fine; that is how I have been acting when notified of held back packages for a long time now and it has not caused any problems.

---

### Post by cybrsaylr on 2023-03-06
> **ajgreeny said:**
> 
Just accept that those packages will be held back but continue with he updates and all should be fine; that is how I have been acting when notified of held back packages for a long time now and it has not caused any problems.

OK did that and get this:
```
The following packages have been kept back:
  gnome-remote-desktop grub-efi-amd64-bin grub-efi-amd64-signed
  python3-software-properties software-properties-common
  software-properties-gtk systemd-hwe-hwdb
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```

Then went into Ubuntu Software to check if up to date, and get this:
[IMG]https://i.postimg.cc/W1rWgPxT/Screenshot-from-2023-03-06-10-59-01.png[/IMG]

Click on 'Update All' and get this message:

[IMG]https://i.postimg.cc/5tWxSb03/image-2023-03-06-110617114.png[/IMG]

Very confused.....

---

### Post by ajgreeny on 2023-03-06
Your confusion is now all related to the three snap packaged applications, chromium, opera and core20, none of which I use.
I have completely removed the snap infrastructure from my machines so I can not help you in detail other than to say that as far as I'm aware, all snap applications are upgraded automatically, though I am not sure how often.

It looks as if you can run ***sudo snap refresh*** to update all your snap applications but you will have to be certain that they are all closed down or will not update.

PS:
I have never used Ubuntu-Software GUI to install, remove or update anything but it checks everything including snaps as well as applications installed using the .deb packages from repos unlike when using ***sudo apt update*** which ignores snaps.

---

### Post by ian-weisser on 2023-03-06
On a stock install of Ubuntu, snapd checks for updates four times each day.

If an update is discovered and the application is NOT running, snapd will automatically download and install the update. You won't even notice the update, but it's there.

If an update is discovers AND the application is running, you will get a notification to terminate the application. Your image shows a bunch of Opera processes running, so that application clearly cannot be updated.

One you Quit the browser, run ```
sudo snap refresh
``` to update Opera. It won't update automatically because that check is already past.

---

### Post by cybrsaylr on 2023-03-07
Thanks ajgreeny and ian-weisser 

Ran 'sudo snap refresh ' and will see how it goes now.

Did not know about... If an update is discovers AND the application is running, you will get a notification to terminate the application. 

Thanks for that info.

---

