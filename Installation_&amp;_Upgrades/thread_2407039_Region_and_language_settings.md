---
title: "Region and language settings"
date: 2018-11-29
forum: Installation &amp; Upgrades
---

### Post by jdeca57 on 2018-11-29
After an installation of Ubuntu 18.10 with language English / US, keyboard Qwerty / US and living near Brussels I encounter a strange problem: The language of the calendar settings are in German. All the rest is English, like I wanted. In settings / Region and language under formats I see that my format is Belgien (German for Belgium) and there are no other choices for Belgium. Of course, if I choose as format United states the language is English but then the calendar goes to the MM/DD format and here it’s the DD/MM so I could opt for an Australian format but then there is a comma problem in numbers.
So my question is: how do I get Belgian format settings and keep the language English?

---

### Post by jdeca57 on 2018-11-30
I solved this by making a custom locale based op what I found in /usr/share/i18n/locales and after translating the weekdays and months compile it with localedef as shown in "https://unix.stackexchange.com/questions/136920/set-custom-locales-in-gnome3-on-fedora-20"

---

