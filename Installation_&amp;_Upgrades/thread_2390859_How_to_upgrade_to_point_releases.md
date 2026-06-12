---
title: "How to upgrade to point releases ?"
date: 2018-05-03
forum: Installation &amp; Upgrades
---

### Post by linuxyogi on 2018-05-03
Hi,

I am using Ubuntu 18.04.

When 18.04.1 comes out how do I upgrade my installation ?

Never done this before.

Will a apt-get dist-upgrade do it ?

---

### Post by Impavidus on 2018-05-03
Just install the normal upgrades. The point releases are nothing more than snapshots of the system at particular times. They're only relevant to the .iso images.

---

### Post by linuxyogi on 2018-05-03
> **Impavidus said:**
> Just install the normal upgrades. The point releases are nothing more than snapshots of the system at particular times. They're only relevant to the .iso images.

Understood. Thanks.

---

### Post by cruzer001 on 2018-05-19
> So my question is do I need to do anything special like installing something manually or will with the usual

Code:

apt-get update && apt-get dist-upgrade

take me to to 18.04.1 ? 

That will get you to 18.04.1; HWE will appear when 18.04.2 comes out.

---

### Post by missmoondog on 2018-05-19
> **cruzer001 said:**
> That will get you to 18.04.1; HWE will appear when 18.04.2 comes out.

which OP will get by simply installing normal updates also.

---

### Post by linuxyogi on 2018-05-19
Thanks for the confirmation.:D

---

### Post by linuxyogi on 2018-05-19
> **cruzer001 said:**
> That will get you to 18.04.1; HWE will appear when 18.04.2 comes out.

Very sorry. Missed your post. So what do I need to do to reach 18.04.2 ?

---

### Post by cruzer001 on 2018-05-19
> **linuxyogi said:**
> So what do I need to do to reach 18.04.2 ?

Wait for it :)

Point releases come out every 6 months.

---

### Post by linuxyogi on 2018-05-19
> **cruzer001 said:**
> Wait for it :)

Point releases come out every 6 months.

Wait for it and then run apt-get dist-upgrade ? 

That's all I want to know.

I am asking again because you wrote

> That will get you to 18.04.1; HWE will appear when 18.04.2 comes out.

---

### Post by cruzer001 on 2018-05-19
The software updater (gui) will get you there or using apt to update.  Either way will install a point release when its available.

HWE will need to be installed manually when 18.04.2 comes out.

---

### Post by linuxyogi on 2018-05-19
> **cruzer001 said:**
>  HWE will need to be installed manually when 18.04.2 comes out.

^^ This is what I am worried about. I have never done this before. 

If I dont install the HWE what will I miss ?

Will I still get security updates ? Is it absolutely necessary to install HWE ?

---

### Post by PaulW2U on 2018-05-19
> **linuxyogi said:**
> If I dont install the HWE what will I miss ?
Newer kernel and X support.
> **linuxyogi said:**
> Will I still get security updates ?
Of course, for three or five years depending on the flavour of Ubuntu that you have installed.
> **linuxyogi said:**
> Is it absolutely necessary to install HWE ?
No, I never have as my systems on which I have kept an LTS release have always worked as expected. I've never needed to consider installing the HWE stack.

---

### Post by QIII on 2018-05-19
Unless you need (or want) the HWE for some reason, you need not bother with it.  If you just continue with your updates you will be supported until 18.04.1 reaches EOL.

If your hardware works right now, there is no reason to fix what ain't broke.

---

### Post by linuxyogi on 2018-05-19
@[**[COLOR=#DD4814][B]PaulW2U**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1078994") @[**[COLOR=#990303][B]QIII**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=628170")

That's a relief. Thanks a lot[URL="https://ubuntuforums.org/member.php?u=628170"][B][COLOR=#990303][B]


[/B][/COLOR][/B][/URL]

---

### Post by cruzer001 on 2018-05-19
> If I dont install the HWE what will I miss ?

Will I still get security updates ? Is it absolutely necessary to install HWE ? 

The current kernel version that you are running is supported for the entire life of 18.04.  Thats 5 years.  It is not necessary to run HWE unless the need arises for maybe new hardware that is better supported with a newer kernel.  My equipment runs fine on the current kernel, I have no need for HWE.

---

### Post by linuxyogi on 2018-05-19
> **cruzer001 said:**
> The current kernel version that you are running is supported for the entire life of 18.04.  Thats 5 years.  It is not necessary to run HWE unless the need arises for maybe new hardware that is better supported with a newer kernel.  My equipment runs fine on the current kernel, I have no need for HWE.

Got it. Thanks.

---

### Post by missmoondog on 2018-05-20
> **PaulW2U said:**
> Newer kernel and X support.

Of course, for three or five years depending on the flavour of Ubuntu that you have installed.

No, I never have as my systems on which I have kept an LTS release have always worked as expected. I've never needed to consider installing the HWE stack.

I have never had HWE installed on any of my systems until just before 18.04 came out. Just happened to get a new computer and burned the last point release of 16.04 and saw that installed it automatically. didn't see or  notice any difference. the HWE kernel will show up in synaptic under new in repository after reloading. you have to choose to install it manually.

just thought i'd voice my experience even though i saw thread was marked as solved. :)

---

### Post by linuxyogi on 2018-08-07
Hi,

I am on

 ```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic
```

When I run [I]ubuntu-support-status I get

```
$ ubuntu-support-status
Support status summary of 'ubuntu':

You have 1688 packages (88.4%) supported until April 2023 (Canonical - 5y)
[COLOR=#ff0000]You have 145 packages (7.6%) supported until April 2021 (Community - 3y)[/COLOR]

You have 0 packages (0.0%) that can not/no-longer be downloaded
[COLOR=#ff0000]You have 76 packages (4.0%) that are unsupported
[/COLOR]

Run with --show-unsupported, --show-supported or --show-all to see more details
```

[COLOR=#ff0000][/COLOR]I am using Ubuntu 18.04 and not K/X/Lubuntu etc. So why the 3 years support period instead of 5 ?

What are these ? I installed them from the official repos (no PPAs)

```
$ ubuntu-support-status --show-unsupported
Support status summary of 'ubuntu':

You have 1688 packages (88.4%) supported until April 2023 (Canonical - 5y)
You have 145 packages (7.6%) supported until April 2021 (Community - 3y)

You have 0 packages (0.0%) that can not/no-longer be downloaded
You have 76 packages (4.0%) that are unsupported


No longer downloadable:


Unsupported: 
conky-all firejail firejail-profiles gimp gimp-data gkrellm handbrake 
hexchat hexchat-common hexchat-perl hexchat-plugins hexchat-python3 
libaudclient2 libavcodec-extra libavcodec-extra57 libbabl-0.1-0 
libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common 
libdata-random-perl libgegl-0.3-0 libgimp2.0 libgnome-2-0 
libgnome2-canvas-perl libgnome2-common libgnome2-gconf-perl 
libgnome2-perl libgnome2-vfs-perl libgnome2-wnck-perl 
libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 
libgnomeui-common libgnomevfs2-0 libgnomevfs2-common 
libgnomevfs2-extra libgsasl7 libgsoap-2.8.60 libgtk2-imageview-perl 
libgtk2-unique-perl libgtkimageview0 libhttp-server-simple-perl 
libimage-magick-perl libimage-magick-q16-perl libkyotocabinet16v5 
liblinear-tools libmailutils5 libmouse-perl libnet-dropbox-api-perl 
libnet-oauth-perl libntlm0 liborbit-2-0 libpath-class-perl 
libproc-processtable-perl libproc-simple-perl libsort-naturally-perl 
libtorrent-rasterbar9 libwww-mechanize-perl 
libx11-protocol-other-perl libxmmsclient6 mailutils mailutils-common 
ndiff nethogs pwgen qbittorrent shutter spectre-meltdown-checker 
spideroakone virtualbox virtualbox-dkms virtualbox-qt winff 
winff-data winff-gtk2 

``` 



[/I]

---

### Post by deadflowr on 2018-08-07
> I am using Ubuntu 18.04 and not K/X/Lubuntu etc. So why the 3 years support period instead of 5 ?

What are these ? I installed them from the official repos (no PPAs)

It tells you those are from the universe (community) repositories.
Only the packages from Canonical (main) are guaranteed 5 years of support.
I don't know if those universe packages are all only supported for 3 years, or if 3 years is just a generic catchall for all universe packages in the ubuntu-support-status command.
Meaning maybe some of those packages have longer support times, and some maybe have shorter support times.
In the past I've seen packages in universe supported for 9 months, 18 months, 3 years, 1 year, and 5 years, so...

FTR: the unsupported package list doe not necessarily mean unsupported, but only that support is indeterminate.
Basically it means there is no data within the packages metadata information about support time.

---

### Post by linuxyogi on 2018-08-07
In that case I will upgrade within 3 years coz using obsolete packages is something I want to avoid.

---

