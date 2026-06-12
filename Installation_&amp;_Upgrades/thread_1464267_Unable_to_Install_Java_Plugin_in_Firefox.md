---
title: "Unable to Install Java Plugin in Firefox"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by malikussaid on 2010-04-28
*Good Morning*,

I am is Ubuntu 9.10 user, while I have installed the "kubuntu-desktop" package, I still used GNOME as my main Window Manager.

Few days ago, because of out-of-date Firefox on Repository (I run "sudo apt-get update" 5 minutes before I post this, and the available stable Firefox version is 3.5.9, while the 3.6.5 is Namoroka, not a RTM one), I download Firefox and Thunderbird from their site, extract the contents (to "/usr/lib/firefox-3.6.3" and "/usr/lib/thunderbird 3.0.4", respectively) and make soft link in "/usr/bin" which points to "/usr/lib/firefox-3.6.3/firefox.sh".

So now, I want to install OpenJDK as an alternative to Sun's Java. I had downloaded it, and copied the "libjavaplugin-oji.so" to the firefox plugin folder, and still can't find the Java plugin in "about:plugins".

I then chown the "libjavaplugin-oji.so" to "malikussaid:malikussaid", and still not work. After that I chmod 777 the "libjavaplugin-oji.so" and still not work.

Here is the result of "ls -l" on the terminal :

```
malikussaid@malikussaid-desktop:/usr/lib/firefox-3.6.3/plugins$ ls -l
total 16
lrwxrwxrwx 1 malikussaid malikussaid    57 2010-04-24 21:12 libjavaplugin_oji.so -> /usr/lib/jre1.6.0_20/plugin/i386/ns7/libjavaplugin_oji.so
-rwxr-xr-x 1 root        root        15716 2010-04-01 22:53 libnullplugin.so
```

Any suggestion?

*Thanks in advance*,
[RIGHT]Malikussaid
[/RIGHT]

---

