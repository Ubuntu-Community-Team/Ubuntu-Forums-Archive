---
title: "Install Firefox3 on Ubuntu 11.04"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by kallunga on 2011-05-10
Hi guys,

I just upgraded to **Ubuntu 11.04** and can't find any friendly way to downgrade **Firefox 4** to **Firefox 3.6**.
Does anyone know how to do that?
Before anyone ask why: **Capybara** or **Selenium** Web driver doesn't work with Firefox 4, do the only way is downgrade Firefox or Ubuntu.

cheers

Leonardo

---

### Post by lovinglinux on 2011-05-10
You can download it from Mozilla and extract to your home directory. Make sure you get the version with the correct architecture.

See [http://www.webgapps.org/firefox/installing-other-versions](http://www.webgapps.org/firefox/installing-other-versions)

---

### Post by PsychoMike on 2011-05-28
Has anyone made any progress with this? I'm in more or less the same boat. I have a LOT of required extensions that aren't Firefox 4 compatible yet.

I downloaded the 3.6.17 installer from here:[http://www.mozilla.com/en-US/firefox/all-older.html](http://www.mozilla.com/en-US/firefox/all-older.html)

It's up and running and seems to work for the most part. But a lot of the button images in the interface are missing - back, forward, refresh, stop, close tab, etc. Going by the error messages I see in the console when launching Firefox it's a 32-vs-64 bit compatibility issue. I'm running a 64-bit system and the version Mozilla offers for download is 32-bit - or at least there's no 64-bit version on that page or anywhere else I can find. 

I've googled all over for the issue, and all the responses say it should work but I might need to install ia32-libs. Problem is, it's already installed. So it's either not working or being ignored.

I'm still very much hoping to find a proper PPA somewhere that is both locked at Firefox 3 and Natty-compatible, since that will hopefully take care of any dependency issues itself. Every PPA I've found is either running version 4 stable or newer, or else it's only runnable on Lucid or Maverick.

Hopefully someone has found a workable downgrade method?

---

### Post by lovinglinux on 2011-05-28
Mozilla doesn't release an official build of Firefox 64bit, so you have to use the builds available from the nightly repository.

[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-firefox-3.6.x/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-firefox-3.6.x/)

[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-firefox-3.6.x-l10n/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-firefox-3.6.x-l10n/)

---

### Post by PsychoMike on 2011-05-28
You are the *man*! It's working perfectly now. I've been googling this constantly for days and this is the only reference I've seen to a 64-bit Linux build in the nightlies at all, let alone a working link to it. Thanks a million.

---

### Post by lovinglinux on 2011-05-28
> **PsychoMike said:**
> You are the *man*! It's working perfectly now. I've been googling this constantly for days and this is the only reference I've seen to a 64-bit Linux build in the nightlies at all, let alone a working link to it. Thanks a million.

You are welcome :-)

---

### Post by kallunga on 2011-05-28
is it working with icons? really? I will try on Monday... 
thanks a lot

---

### Post by elsdyr on 2011-06-01
Thanks guys - works for me. Nice to have bartab and tree style tab back.

I still can't make a shortcut in Laucher though. I think it has something to with "firefox" is a shell script that launches firefox-bin.

---

### Post by lovinglinux on 2011-06-01
> **elsdyr said:**
> Thanks guys - works for me. Nice to have bartab and tree style tab back.

I still can't make a shortcut in Laucher though. I think it has something to with "firefox" is a shell script that launches firefox-bin.

They both work with Firefox 4.

[https://addons.mozilla.org/en-US/firefox/addon/tree-style-tab/](https://addons.mozilla.org/en-US/firefox/addon/tree-style-tab/)
[https://addons.mozilla.org/en-US/firefox/addon/bartab/versions/](https://addons.mozilla.org/en-US/firefox/addon/bartab/versions/)

---

