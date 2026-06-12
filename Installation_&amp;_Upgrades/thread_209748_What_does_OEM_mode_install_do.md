---
title: "What does OEM mode install do?"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by richardq on 2006-07-05
What does the OEM mode for install from the alternate-iso do? I am having trouble installing Dapper and I might be having video card troubles (xserver-xorg configuration blanks my screen during the normal install). I'm wondering if the oem install is something like the safe graphics install choice on the desktop iso.

Is there any place that actually describes what the different install choices on the desktop and alternate iso's really mean? I can't find any specific info in the Ubuntu documentation.

---

### Post by christhemonkey on 2006-07-05
From [this]("http://business.newsforge.com/article.pl?sid=05/11/15/2130234&from=rss") page:
> OEMs in this sense are original equipment manufacturers -- vendors of pre-built computer hardware systems -- complete PCs and servers, not to be confused with hardware manufacturers. Often referred to colloquially as "white box" vendors, OEMs include a range of PC makers, from one-man garage PC shops to customization-friendly Web stores to high-volume business suppliers.

Using the OEM installation option, computer resellers can pre-install and verify Ubuntu on machines slated for sale or redistribution, but leave select configuration details, locale and language preferences, and user account creation to the retail purchaser.

---

### Post by wallijonn on 2006-07-06
Be careful that you do not create a user account when you first log in into the OEM account. The new account will not have all the admin utilities in the menu (SPM, for one (of about 6 programs)). Even if you logout of the new account and re-login into the OEM account and you issue the [color=red]sudo oem-config-prepare[/color] command, the OEM account will keep working like an administrator / root account and the new account will function as a restricted / limited user account.

---

