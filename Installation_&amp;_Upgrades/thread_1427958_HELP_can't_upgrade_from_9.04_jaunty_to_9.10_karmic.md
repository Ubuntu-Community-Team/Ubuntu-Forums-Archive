---
title: "HELP: can't upgrade from 9.04 jaunty to 9.10 karmic"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by blackblood357 on 2010-03-12
I need your help experts!!,

i used the Update Manager to upgrade from 9.04 to 9.10..
then it said:

[B]NO VALID MIRROR  FOUND

While scanning your repository information no mirror entry for the upgrade was found. This can happen if you run a internal mirror or if the mirror information is out of date.

Do you want to rewrite your 'sources.list' file anyway? If you choose 'Yes' here it will update all 'jaunty' to 'karmic' entries.
If you select 'No' the upgrade will cancel.[/B]

What does this mean?
I choose yes, then is said that there's something wrong with the network I'm connected to..then it closes..the upgrade failed.:sad:

---

### Post by ghostborg on 2010-03-12
The sources list is where your addresses of the software repositories are stored.
It seems to be indicating that it is going to replace your old list with the default Karmic one, as if it where a new install. You will loose any custom ones that you added yourself.

I have never experienced the message you have but when I upgrade it usually tells me its going to disable some of my sources while upgrading.

---

### Post by tachuela on 2010-03-12
I'ts an easy way out.

---

### Post by slakkie on 2010-03-12
Could you post the contents of the file /etc/apt/sources.list

---

