---
title: "Error Message while updating Firefox"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by Oldhacker on 2011-06-23
Using Update Manager this morning, I received the following error message while it was updating Firefox:

An error occured:

E: /var/cache/apt/archives/ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb: trying to overwrite '/etc/xul-ext/ubufox.js', which is also in package xul-ext-ubufox 0

What action should I take now?

---

### Post by Korcia on 2011-06-23
I've got the same error.

---

### Post by Quake on 2011-06-23
I get the same error...

---

### Post by alexyz on 2011-06-23
same here, it appears to be the firefox 4.0/5.0 mozillateam ppa.  the package ubufox is broken.  I don't see any problems though.

---

### Post by mikyul on 2011-06-23
Same here:

Unpacking replacement ubufox ...
dpkg: error processing /var/cache/apt/archives/ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb (--unpack):
 trying to overwrite '/etc/xul-ext/ubufox.js', which is also in package xul-ext-ubufox 0:0.9-0ubuntu1~mfs~lucid1
Errors were encountered while processing:
 /var/cache/apt/archives/ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by orthopteroid on 2011-06-23
I opened synaptic, marked xul-ext-ubufox for removal, ubufox for upgrade and applied changes. No remaining conflicts and firefox appears to still be working.

---

### Post by d-r-i-v-e on 2011-06-23
> **orthopteroid said:**
> I opened synaptic, marked xul-ext-ubufox for removal, ubufox for upgrade and applied changes. No remaining conflicts and firefox appears to still be working.

Thank you. Your reply was helpful.
xul-ext-ubufox is a minor and not essential extension.

---

### Post by a_guerere on 2011-06-23
Conflict dissapears when using @orthopteroid method but firefox did not upgrade until I used 'sudo apt-get install firefox' which removed firefox-globalmenu and upgraded the firefox package to firefox 5.0+build1+nobinonly-0ubuntu0.10.04.1~mfs1 .

Checked and firefox was indeed upgraded to version 5.0, and appears to be working fine.

---

### Post by Marzata on 2011-06-23
Thank you very much! What exacly xul-ext-ubufox is doing?

---

### Post by Rolandmaffia on 2011-06-23
Thanks, worked for me in Ubuntu 10.04.

---

### Post by alexyz on 2011-06-23
> **Marzata said:**
> Thank you very much! What exacly xul-ext-ubufox is doing?

here's a description from [http://packages.ubuntu.com/maverick/xul-ext-ubufox](http://packages.ubuntu.com/maverick/xul-ext-ubufox)

```
Adds Ubuntu-specific modifications to Firefox.

Integrates the browser with Ubuntu to:

 * Enable searching for missing plugins from Ubuntu software catalog
 * Add the following options to the Help menu
   - Get help on-line
   - Help translating Firefox
   - Ubuntu Release Notes
 * Set homepage to Ubuntu Start Page
 * Display a restart notification after upgrading Firefox
 * Add ask.com to the search engines.

You can uninstall this if you prefer to use a pristine Firefox install. 

```

---

### Post by bsw4h on 2011-06-25
> **Oldhacker said:**
> Using Update Manager this morning, I received the following error message while it was updating Firefox:

An error occured:

E: /var/cache/apt/archives/ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb: trying to overwrite '/etc/xul-ext/ubufox.js', which is also in package xul-ext-ubufox 0

What action should I take now?
you will find the solution here

[http://ubuntu4beginners.blogspot.com/2011/06/firefox-5-stable-arrives-in-official.html](http://ubuntu4beginners.blogspot.com/2011/06/firefox-5-stable-arrives-in-official.html)

---

### Post by ervin23 on 2011-06-27
Perfect & thx :-)

---

### Post by ervin23 on 2011-06-27
> **orthopteroid said:**
> I opened synaptic, marked xul-ext-ubufox for removal, ubufox for upgrade and applied changes. No remaining conflicts and firefox appears to still be working.

Perfect :-)

---

### Post by CycleNutz on 2011-07-01
> **orthopteroid said:**
> I opened synaptic, marked xul-ext-ubufox for removal, ubufox for upgrade and applied changes. No remaining conflicts and firefox appears to still be working.

Thank you very much for your help. :P

---

