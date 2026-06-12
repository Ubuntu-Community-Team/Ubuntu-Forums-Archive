---
title: "Simple yes or no about LTS"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by 98cwitr on 2010-03-26
Although I installed 10.04 LTS, I will be able to upgrade to "non-LTS" releases in the future via upgrade manager?

---

### Post by 2hot6ft2 on 2010-03-26
> **98cwitr said:**
> Although I installed 10.04 LTS, I will be able to upgrade to "non-LTS" releases in the future via upgrade manager?

yes

---

### Post by slakkie on 2010-03-26
Simple answer: No, the default will make sure you upgrade LTS to LTS.

The longer answer, yes, since you can define it in the file /etc/update-manager/release-upgrades. set prompt to normal will allow you to upgrade to any release.

---

### Post by 98cwitr on 2010-03-27
^^^that's how I figured it. Thanks. As long as I dont have to lay my image back down on the HD Ill be happy ;)

file is:
> # default behavior for the release upgrader
#

[DEFAULT]
# default prompting behavior, valid options:
#  never  - never prompt for a new distribution version
#  normal - prompt if a new version of the distribution is available
#  lts    - prompt only if a LTS version of the distribution is available
Prompt=normal

was *Prompt=lts*

---

### Post by Phrea on 2010-03-27
I've been meaning to ask the same question. :)
Good to see that if we want, we can indeed upgrade to a non-lts version.

---

