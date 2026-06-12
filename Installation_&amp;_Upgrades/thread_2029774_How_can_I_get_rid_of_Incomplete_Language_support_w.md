---
title: "How can I get rid of Incomplete Language support warning with mini.iso?"
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by dlpartain on 2012-07-20
Greetings,

Please excuse the length of this message; it feels important to give the background before the question.

I'm doing some work with automated installs of Ubuntu (64-bit 12.04) and am currently doing something along the lines of the following.

1. Boot from mini.iso (the minimal ISO image) so that, when complete, the install is entirely updated.

2. Change the boot menu in mini.iso with something along the lines of:

append preseed/url=http://my-install-server/preseedfile.txt debian-installer/locale=en_US preseed/ locale=en_US keyboard-configuration/layoutcode=us console-setup/ask_detect=false netcfg/choose_interface=auto initrd=initrd.gz priority=high -- 

The result is that a preseed file is fetched on boot from that URL ([http://my-install-server/preseedfile.txt](http://my-install-server/preseedfile.txt)) with all the debconf settings I use during the installation.  Virtually everything is automated now.

3. In the preseed file, I have something like:

d-i preseed/late_command string in-target wget --no-proxy -q \
 -O /tmp/postinstall.sh [http://my-install-server/post-script](http://my-install-server/post-script) | logger;\
 in-target chmod +x /tmp/postinstall.sh; \
 in-target /tmp/postinstall.sh | logger;\
 in-target rm -f /tmp/postinstall.sh;

This allows me to do stuff at the end of the preseed-based installation.  Mostly, this works very well.

My problem:

When the installation is finished and I log in, I get a popup that has:

<popup>
Incomplete Language Support

The language support files for your selected language seem to be 
incomplete. (Rest deleted)
</popup>

Even if I "Run this action now" and apply it system-wide, the popup will appear for every user on the system.  This is rather annoying, particularly since there is no problem with the language support files!  If I run:

# check-language-support

It returns nothing.  Nothing is missing.  Running this command does not prevent the popup, though.

In digging further, I looked in /var/log/installer/syslog (which has the result from installation), and I see:

in-target: Unable to locate package language-support-en
in-target:
pkgsel: finishing up
dpkg-query -W language-pack-en language-pack-gnome-en language-support-en failed; assuming incomplete language support

The reason that language-support-en isn't located is that it's no longer a package in precise (and wasn't in oneiric either).   [http://packages.ubuntu.com/search?searchon=names&keywords=language-support-en](http://packages.ubuntu.com/search?searchon=names&keywords=language-support-en) will show what I mean.

I can't find where this dpkg-query command is run, and I'm a bit at a loss as to how to get rid of this warning / popup.

I have previously based the above on the alternative CD iso image, and no such popups appeared, so I believe this is a mini.iso problem.  I further believe I'm getting bitten by [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/931191](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/931191) but hope someone here might have ideas on how to proceed.  Responses on the bug artifact would be great, too, since I'm not the only one affected :)

Does anyone have further ideas where I should look to track this down?

Cheers,

David

---

### Post by dino99 on 2012-07-20
maybe you can get around looking at this block:

5.3.1.1. Using boot parameters to answer questions
([http://d-i.alioth.debian.org/tmp/en.i386/ch05s03.html](http://d-i.alioth.debian.org/tmp/en.i386/ch05s03.html))

but this page seems better: (see : localization)

[http://www.debian.org/releases/stable/s390/apbs04.html.en](http://www.debian.org/releases/stable/s390/apbs04.html.en)

---

### Post by dlpartain on 2012-07-20
Hi!

Thank you for taking time to respond!

I use the kinds of things in both of these lengths rather extensively already.  For example, the keyboard is set by boot parameters, and partitioning (including disk encryption) is handled by debconf parameters like those in the second link you included.  

I'm afraid I don't understand, though, how I might solve this particular problem using either. Could you perhaps elaborate a bit?

Thanks.

David

[]("http://www.debian.org/releases/stable/s390/apbs04.html.en")

---

### Post by tokarbol on 2012-07-20
Hi,

Looking at the snippets of automation, I can't much say if it has anything to do with your scripts. Do you experience the same if you use the mini-iso without preseeding?

I believe I saw this error message before Precise was released. Are you using an up-to-date mini-iso image?

Cheers,
Ballock

---

### Post by dlpartain on 2012-07-20
Hi,

Thanks for the ideas.  I just verified that I'm running the latest mini.iso (from [http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/)) but with the alterations to the boot menu as I described.

I've downloaded a new copy which I haven't changed at all and fired up an installation in virtualbox.  I installed from the same (internal) mirror.    (The install takes forever since it seems to be trying to connect outside the company but since you have to go through a proxy and it doesn't understand that, it has to time out before continuing...)  I've done nothing else to customize it whatsoever, and I installed the "Ubuntu desktop".  Other values were identical to what I would have done with preseeding (host name and stuff).

The install has the exact same error in /var/log/installer/syslog:

pkgsel: finishing up
pkgsel: dpkg-query -W language-pack-en language-pack-gnome-en language-support-en failed; assuming incomplete language support

and the popup appeared.  No different than the customized thing I'm doing.  This is a good thing since it'll make it easier to reproduce.  It's a bad thing since that kinda shows it's not my fault and I consequently cannot really fix it myself :-)

Yes, I believe this error was around in Oneiric as well, though I was using the alternative cd as a base at the time and it didn't / doesn't have this problem.

Cheers,

David

---

### Post by tokarbol on 2012-07-23
I have just tried my preseeded installation.

In the installer log  I can see I have the same pkgsel error about incomplete language  support, however check-language-support returns a number of packages  with package locales (firefox-locale-en, myspell, wbritish, wamerican,  18 packages). Interesting is that if I run "check-language-support -l  en", I get 19 packages. However, I do not experience the pop-up warning  about missing language support. Is it during the first log in? Or do I  need to wait for it?

See if you have:
d-i pkgsel/install-language-support boolean true
in your preseed file.

If  that does not help, some proxy settings might be at fault. We have  recently bumped into msttcorefonts problem where it fails to download  due to the use of update-notifier, which does not respect apt proxy  settings. You can try to see if the same error message happens in a  network connected directly to the Internet.

Anyway, we are using a  CFEngine bundle that installs the laguage support files using the  check-language-support utility. We get the list using:
locales=`( check-language-support -l "$1"; check-language-support ) | sort -u`
where $1 is the country code.

---

### Post by dlpartain on 2012-07-23
Hi!

Thanks for the continuing dialog!   The pop-up appears after a couple of minutes the first time I log in.

Is your preseeding-based install using mini.iso or some other iso image?  The pop-up only seems to appear with mini.iso.

When I run 'check-language-support' it returns nothing.  It doesn't think anything is missing. :-)

> See if you have:
> d-i pkgsel/install-language-support boolean true
> in your preseed file.

That's not in my preseed file, so I'll give that a whirl!

> If  that does not help, some proxy settings might be at fault. We have  recently
> bumped into msttcorefonts problem where it fails to download  due to the use
> of update-notifier, which does not respect apt proxy  settings. 

We're not having any trouble with msttcorefonts.  We have the following, which seems to deal with that problem (unless I'm missing something):

ttf-mscorefonts-installer msttcorefonts/http_proxy string [http://my-corp-proxy:8080](http://my-corp-proxy:8080)

Cheers,

David

---

### Post by tokarbol on 2012-07-23
Hello,

Yes, we are using the mini-iso. I am reading my CFEngine rules for this and I can see the package language-selector-common, so I guess it is or it was required for 10.04 to properly report language support packages. You can try to see if you have that installed.

Regarding msttcorefonts, the template "msttcorefonts/http_proxy" is no longer in the package, so your preseed entry does nothing for precise. If it still works, then perhaps it takes the proxy from an environment variable or downloads it in user-space where the proxy is configured from, say, DHCP.[]("http://my-corp-proxy:8080")

Cheers,
Ballock

---

### Post by dlpartain on 2012-07-24
Hi Ballock!

Thanks for the response.  A brief report:

d-i pkgsel/install-language-support boolean true

didn't improve the situation, unfortunately.

> Yes, we are using the mini-iso.

Interesting... If you grab the current mini.iso and install a plain-ol'-vanilla installation, do you get the language popup?  I do...

> I am reading my CFEngine rules for this
> and I can see the package language-selector-common, so I guess it is or
> it was required for 10.04 to properly report language support packages.
> You can try to see if you have that installed.

# dpkg --list | grep language-selector-common
ii  language-selector-common   0.79  Language selector for Ubuntu

Seems to be there.

> Regarding msttcorefonts, the template "msttcorefonts/http_proxy" is no
> longer in the package, so your preseed entry does nothing for precise.

You're more up-to-date than I am :-)

> If it still works, then perhaps it takes the proxy from an environment variable
> or downloads it in user-space where the proxy is configured from, say, DHCP.

Yep, that must be it.  I have:

export http_proxy="http://my-corp-proxy:8080"
export https_proxy="http://my-corp-proxy:8080"
export no_proxy="localhost,127.0.0.0/8,my-install-server"
apt-get -y install ubuntu-restricted-extras

For msttcorefonts, the http_proxy seems to work.

In any case,  I still want to know who's doing this:

in-target: Unable to locate package language-support-en
pkgsel: finishing up
pkgsel: dpkg-query -W language-pack-en language-pack-gnome-en language-support-en failed; assuming incomplete language support

Since I believe that's the reason I'm seeing this.  Haven't found it yet.

Cheers,

David

---

### Post by tokarbol on 2012-07-25
>> d-i pkgsel/install-language-support boolean true

> didn't improve the situation, unfortunately.

> In any case,  I still want to know who's doing this:
> 
> in-target: Unable to locate package language-support-en
> pkgsel: finishing up
> pkgsel: dpkg-query -W language-pack-en language-pack-gnome-en language-support-en failed; assuming incomplete language support
> 
> Since I believe that's the reason I'm seeing this.  Haven't found it yet.

Well, this seems to be pretty easy:
apt-get source pkgsel
and you will get pkgsel and its scripts.

I have just had a look at it and there is a question template you might be interested with:
```
Template: pkgsel/ignore-incomplete-language-support
Type: boolean
Default: false
Description: for internal use; can be preseeded
 Do not warn the end user if the language packs could not be installed.

```
You should be able to preseed it with:
d-i pkgsel/ignore-incomplete-language-support boolean true

I have not tested the mini-iso without preseed yet.

Cheers,
Ballock

---

### Post by tokarbol on 2012-07-25
> **dlpartain said:**
> 
Thanks for the ideas.  I just verified that I'm running the latest mini.iso (from [http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/)) but with the alterations to the boot menu as I described.
David
Oh, did you notice there is an updated installer image available:
[http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/installer-amd64/20101020ubuntu136.1/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/installer-amd64/20101020ubuntu136.1/images/netboot/mini.iso)

Cheers,
Ballock

---

### Post by tokarbol on 2012-07-25
I have just installed using the precise mini-iso image and I am getting the pop-up message, so I can reproduce it without proxy as well.

However, check-language-language-support reports the same 18 packages as it used to report with our preseeded installation.

---

### Post by tokarbol on 2012-07-25
In pkgsel source in debian/postinst lines 410+ you can find the actual check and it seems that the template
pkgsel/ignore-incomplete-language-support is being used, so you can actually use it to just dismiss the warning.

Lines 365 sets the puts the "language-support-en" package to the env variable that is used afterwards, however this line is only executed if "chroot /target which check-language-support" executed in line 234 fails to run.

This in turn must be because at this point in the installation process, the package language-selector-common is not installed yet. Although line 232 installs it, but it only does it for a full cdrom install....

Ok, not true. I am looking at my installer.log and line 3185 installs language-selector-common while pkgsel fires up the check in line 12k....

So to me it seems that for some reason either:
a) $check_language_support is not set as per line 227
b) check-language-support returns a wrong list of packages, at least while being run by pkgsel.

---

### Post by aimwin on 2012-07-25
> **dlpartain said:**
> Greetings,

............................................
<popup>
Incomplete Language Support
.....................(Rest deleted)


I have the same issue with my new Ubuntu 12.04 LTS after fresh installation.
But not with other realeases.

I belive it is a bug.
(Or, it is a build in new feature of installation process,
anyone from developer team can comment?)

But if we installed and/or deleted language packs we want,
after that pop up message,
the normal usasge of 12.04 never show up again.
even after reboot.
This include in my Live USB 12.04.
How ever after new Installations we always have that.

So it is not considered a bug for normal user.

But on other release you will only got that message if you run the language pack to install the additional language.
So if that pop up is not a new feature of 12.04 LTS, 
then I will consider it is a small bug.

Please try to use 10.04 or 11.04 and see if it produce the same error or not.

Both of those 2 releases are pretty solid now with very few crashes.
And don't have that error message.

---

### Post by dlpartain on 2012-07-25
Hi all,

Thanks for all the traffic.  Ballock, you've saved the day :-)

It appears that adding this to my preseed input gets rid of the popup!

d-i pkgsel/ignore-incomplete-language-support boolean true

In fact, what I have is:

d-i pkgsel/install-language-support boolean true
d-i pkgsel/ignore-incomplete-language-support boolean true

Furthermore, 

check-language-support

shows nothing missing.  Also, I looked in /var/log/installer/syslog and see:

in-target: Rebuilding /usr/share/applications/bamf.index...
in-target: Reading package lists...
Building dependency tree...
In-target: Reading state information...
in-target: E
in-target: Unable to locate package language-support-en
pkgsel: finishing up

but nothing about any assumptions of incomplete language support.  So... I think that you've solved it!  Thank you very much!

My take on where the bug is... The offending place in pkgsel postint that seems to look for the missing file is at around line 463:

                if $check_language_support; then
                        packs="$(chroot /target check-language-support -l "$lp" || true)"
                else
                        packs="language-support-$lp"
                fi

Since there is no such package as language-support-en in the Ubuntu repos anymore, searches for it are going to fail, at which point the install marks itself as having incomplete language support.  I'll report this...

Cheers,

David

---

### Post by dlpartain on 2012-07-25
Hi,

> I'll report this...

I've done so.  It's at [https://bugs.launchpad.net/ubuntu/+source/pkgsel/+bug/1028910](https://bugs.launchpad.net/ubuntu/+source/pkgsel/+bug/1028910)

Cheers,

David

---

### Post by bubbajunk on 2012-07-26
Excuse me for the total newbie question, but is it possible to enter the "d-i pkgsel/ignore-incomplete-language-support boolean true" string to the boot option command line when booting from the mini.iso file? I'm wondering if there is a way to get around having to create the config file for just this one change.

---

### Post by botdfismyaddiction on 2012-07-26
I also get this popup after a standard install with the LiveCD... it says during the install that its getting language support, and after my install was done it still shows the message to download additional languages, I just closed the message and moved on, but with several systems, I can see how annoying that would be.

---

