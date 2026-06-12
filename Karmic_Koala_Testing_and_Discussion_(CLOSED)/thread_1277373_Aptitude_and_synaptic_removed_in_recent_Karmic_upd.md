---
title: "Aptitude and synaptic removed in recent Karmic update?"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by khughitt on 2009-09-28
I came back to my machine after the weekend and ran a update & dist-upgrade to find the following:

```

...
The following packages have unmet dependencies:
  aptitude: Depends: libapt-pkg-libc6.9-6-4.7 which is a virtual package.
  synaptic: Depends: libapt-inst-libc6.9-6-1.1 which is a virtual package.
            Depends: libapt-pkg-libc6.9-6-4.7 which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
aptitude
apturl
jockey-gtk
language-selector
software-properties-gtk
synaptic
tasksel
tasksel-data
ubuntu-minimal
ubuntu-standard

Install the following packages:
aptdaemon [0.10+bzr240-0ubuntu1 (karmic)]
python-aptdaemon [0.10+bzr240-0ubuntu1 (karmic)]

Score is -20

```

I know that the Software store is supposed to be released, and will unify the different package management tools, but shoudl synaptic, aptitude, and for that matter, ubuntu-standard & ubuntu-minimal be removed?

---

### Post by zika on 2009-09-28
> **pwnedd said:**
> I came back to my machine after the weekend and ran a update & dist-upgrade to find the following:

```

...
The following packages have unmet dependencies:
  aptitude: Depends: libapt-pkg-libc6.9-6-4.7 which is a virtual package.
  synaptic: Depends: libapt-inst-libc6.9-6-1.1 which is a virtual package.
            Depends: libapt-pkg-libc6.9-6-4.7 which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
aptitude
apturl
jockey-gtk
language-selector
software-properties-gtk
synaptic
tasksel
tasksel-data
ubuntu-minimal
ubuntu-standard

Install the following packages:
aptdaemon [0.10+bzr240-0ubuntu1 (karmic)]
python-aptdaemon [0.10+bzr240-0ubuntu1 (karmic)]

Score is -20

```I know that the Software store is supposed to be released, and will unify the different package management tools, but shoudl synaptic, aptitude, and for that matter, ubuntu-standard & ubuntu-minimal be removed?No, do not remove them, wait until dependencies are resolved ...

---

### Post by khughitt on 2009-09-28
> **zika said:**
> No, do not remove them, wait until dependencies are resolved ...

Thought so. Thanks :)

---

### Post by infamousrev on 2009-09-28
Aptitude finished building only seconds ago,

Too bad debootstrap does not warn and simply fails.

---

### Post by VMC on 2009-09-28
I just said no to all that and yes to keep current.
... I'll wait until I hear from "Captain Spock" :) .

---

### Post by dadedo123 on 2009-09-28
My update manager is asking me for Partial upgrading. Should I upgrade?

---

### Post by Slug71 on 2009-09-28
> **dadedo123 said:**
> My update manager is asking me for Partial upgrading. Should I upgrade?

No!

---

### Post by MacUntu on 2009-09-28
Wouldn't work anyway. ;)

---

### Post by dadedo123 on 2009-09-28
> **Slug71 said:**
> No!

Then should I wait for the Partial Upgrade to go away? Or what shall I do?

---

### Post by MacUntu on 2009-09-28
> **dadedo123 said:**
> Then should I wait for the Partial Upgrade to go away? Or what shall I do?

If you're using the main update server you should now be able to do the upgrade without removals.

---

### Post by zika on 2009-09-28
> **dadedo123 said:**
> Then should I wait for the Partial Upgrade to go away? Or what shall I do?Wait. It shouldn't take long and You do not have anything important waiting for You in upgrade anyway ...

---

### Post by BAMF1501 on 2009-09-28
my pc ask for a partial upgrade to i clickedd no

---

### Post by Starks on 2009-09-28
The dependencies should be fixed now.

---

### Post by philinux on 2009-09-28
> **BAMF1501 said:**
> my pc ask for a partial upgrade to i clickedd no

Good choice. Never do partials.

[http://ubuntuforums.org/showthread.php?t=1269009](http://ubuntuforums.org/showthread.php?t=1269009)

---

### Post by cyberkilla on 2009-09-28
I'm still being nagged to do a partial update btw.

Using "main server" repository.

---

### Post by kansasnoob on 2009-09-28
It "resolved" here on the US server after about an hour or so. I just ran apt-get update and then installed using the Update Manager gui.

---

### Post by philinux on 2009-09-28
> **cyberkilla said:**
> I'm still being nagged to do a partial update btw.

Using "main server" repository.

Ignore it and press cancel and update the other packages. Or use the terminal. If packages are being kept back there will be a good reason. Partial updates can really bork your system.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by jppr on 2009-09-28
> **philinux said:**
> Ignore it and press cancel and update the other packages. Or use the terminal. If packages are being kept back there will be a good reason. Partial updates can really bork your system.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

i always use aptitude, never apt-get :popcorn:

---

### Post by philinux on 2009-09-28
> **jppr said:**
> i always use aptitude, never apt-get :popcorn:

Like they used to say stick to one or the other.

---

### Post by dadedo123 on 2009-09-28
> **philinux said:**
> Ignore it and press cancel and update the other packages. Or use the terminal. If packages are being kept back there will be a good reason. Partial updates can really bork your system.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Am I okay running this command instead of using the update manager? 
When are Partial Upgrades safe to use?

---

### Post by mxboy15u on 2009-09-28
I did not look...aptitude is now gone for me. Is there any way to get it back?

---

### Post by kansasnoob on 2009-09-28
> **mxboy15u said:**
> I did not look...aptitude is now gone for me. Is there any way to get it back?

Is synaptic still there? If so use synaptic to install aptitude (maybe even check for broken packages).

If not use 'apt-get install --reinstall' for either or both.

I'd be tempted to just run the command(s):

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install --reinstall aptitude synaptic
```

---

### Post by zika on 2009-09-28
> **dadedo123 said:**
> Then should I wait for the Partial Upgrade to go away? Or what shall I do?Whenever there are some packages that are to be removed check changelog in synaptic to see if You are sure that You want to remove. You might want to accept removal only in case there is a major reshuffle and new package is taking over the old one. Generally never accept removal when there are unmet dependencies ... Wait until that conflict is resolved. There is never a simple answer to such a question I myself posted several times about some packages. I think I've learned a lesson but ... Even though I've been called "idiot" on one occasion I did not take it hard because we all learn ...

---

### Post by mxboy15u on 2009-09-28
That worked great, thanks for the tip, saved me a fresh install.

---

### Post by oboedad55 on 2009-09-28
I just did the upgrade and new updates with no apparent disaster. Synaptic is still there and Software Center has been renamed and moved to the Applications menu. I didn't see the previous posts until it was too late but everything seems okay so far.

---

### Post by VMC on 2009-09-28
> **dadedo123 said:**
> Am I okay running this command instead of using the update manager? 
When are Partial Upgrades safe to use?

I alway use aptitude. I don't have update manager even installed.

---

### Post by Reiger on 2009-09-28
I use:
```

sudo apt-get update && sudo aptitude safe-upgrade
```

This works reliably and in the case it does not work (fully) it will at least not do anything at all: basically it opts to upgrade that which safely can be upgraded and keep back the rest. (There are of course limits to that &#8216;safety&#8217;: upgrading boot loaders for instance is never guaranteed to be safe.)

---

### Post by cyberkilla on 2009-09-29
Every time I update, I'm asked to update the NVidia drivers (the new versions don't work for me). I suppose I'll have to do apt-pinning.

My workaround has been to unselect the four NVidia packages in update manager before installing the updates:) Of course, that doesn't work when a partial update is being demanded.

I've stopped the nvidia packages from upgrading with:
```
Package: nvidia-180-kernel-source
Pin: version 185.18.14-*
Pin-Priority: 1001

Package: nvidia-180-libvdpau
Pin: version 185.18.14-*
Pin-Priority: 1001

Package: nvidia-180-modaliases
Pin: version 185.18.14-*
Pin-Priority: 1001

Package: nvidia-glx-180
Pin: version 185.18.14-*
Pin-Priority: 1001
```

It's still a partial update though, as it's holding back python packages. I think I might install it anyway.

---

