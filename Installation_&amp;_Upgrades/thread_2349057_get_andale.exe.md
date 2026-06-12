---
title: "get andale.exe"
date: 2017-01-10
forum: Installation &amp; Upgrades
---

### Post by pedro_rodriguez2 on 2017-01-10
I am using Ubu 16.04
For a while now, when I update, I get a message about 'updating flash plugin'. A tarball is downloaded, unpacked, then it tries to get something called andale.exe from sourceforge. This never succeeds and I get a message &#8220;failed to download packages" I can click a button which tries again, but fails again. This has been going on for a while now.

Can I get this file from somewhere else?

---

### Post by howefield on 2017-01-11
If you tried to install ttf-mscorefonts-installer I'd suggest purging it and installing the 3.6 version of the package from an alternative source, eg

```
sudo apt purge ttf-mscorefonts-installer
```

to get rid of the current package

```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```

to download the 3.6 version of the package to your Downloads folder, and

```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

to install the new package.

---

### Post by santosh83 on 2017-01-11
> **howefield said:**
> If you tried to install ttf-mscorefonts-installer I'd suggest purging it and installing the 3.6 version of the package from an alternative source, eg

But why is this package broken on Ubuntu considering Debian is upstream and Ubuntu could always pull the non-broken version from the former?

---

### Post by howefield on 2017-01-11
> **santosh83 said:**
> But why is this package broken on Ubuntu considering Debian is upstream and Ubuntu could always pull the non-broken version from the former?

Ask the package maintainer.

I believe sourceforge (where the actual font files are downloaded from) changed the location rendering the package broken. I'm not really too interested in the "why" but there are a ton of bugs on launchpad that you could go read and add heat on, or you could simply not use the broken package.

---

### Post by pedro_rodriguez2 on 2017-01-11
Thank you very much! Worked like a dream! I always wonder how people know all these things, it's a mystery to me, but I very glad you do know!

I'll keep an eye on it at update time, see if the flash plugin installer throws up  any more problems.

---

### Post by howefield on 2017-01-11
> **pedro_rodriguez2 said:**
> Thank you very much! Worked like a dream! I always wonder how people know all these things, it's a mystery to me, but I very glad you do know!

I'll keep an eye on it at update time, see if the flash plugin installer throws up  any more problems.

You're welcome and glad it worked, if you get a prompt regarding flash don't worry, just post again and it will be a simple enough fix for that one too.

---

