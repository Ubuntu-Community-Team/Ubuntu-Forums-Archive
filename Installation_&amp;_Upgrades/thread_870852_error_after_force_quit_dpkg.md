---
title: "error after force quit dpkg"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by ray74 on 2008-07-26
hello there
i was trying to install the Chinese language support(language-pack-zh-base) but it stopped while installing the openoffice.org-help-en-gb

so i force quit the language support updating. but now when i open the synapic package manage, it told me to run"dpkg --configure -a". I did so, but the system stops here:

ray@ray:~$ sudo dpkg --configure -a
Setting up openoffice.org-l10n-en-us (1:2.3.0-1ubuntu5.4) ...

Setting up openoffice.org-help-en-gb (1:2.3.0-1ubuntu2) ...

Setting up language-pack-zh-base (1:7.10+20080205) ...
Generating locales...
  zh_CN.UTF-8... 

i tried to delete the files in the /var/lib/dpkg/updates. but anytime when i use apt, it still tries to install this language-pack-zh-base.

i am quite a newbie for ubuntu and thanks for you guys to help me out!

---

### Post by ray74 on 2008-07-26
i am under Gusty 7.10 and everything else seems to be fine. thanks.

---

### Post by littlepan on 2008-08-13
I have the very same problem with you. Neither could I solve it. Have you solved it yet?

---

