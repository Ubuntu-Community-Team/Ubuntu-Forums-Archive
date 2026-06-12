---
title: "One more question before installing Ubuntu"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by tico on 2006-02-28
I've decided to install Ubuntu using Win XP on a dual boot system. I've go a question before doing so. I use Firefox, Thunderbird and OpenOffice in my Win XP. Everything is configured and personalized. So, here is the point: I'd like to use the same configuration/personalized options in Windows and Ubuntu, in other words, I'd like to have the same mailbox used by Win and Ubuntu, the same OOo templates, the same bookmarks etc. So, if I use Thunderbird in Win XP and receive some mails, then I go to Ubuntu, I have the same mails, because the mailbox I use in Win XP is the same I use in Ubuntu. And this for OOo and Firebird config. Is this possible?

TIA

---

### Post by rfruth on 2006-02-28
I know Firefox and Thunderbird each have a profile that can be moved / shared
[http://kb.mozillazine.org/Moving_your_profile_folder]("http://kb.mozillazine.org/Moving_your_profile_folder")
not sure about OOO, good luck !

---

### Post by tico on 2006-02-28
Thanks! Hope somebody will help with OOo2.

---

### Post by mrhelpman on 2006-03-01
You will have to be careful about how you configure your partitions and remember that ubuntu can not write to an ntfs partition. So if your configuration files/mails boxes etc are on an ntfs partition then ubuntu will be able to read them but not update them. You may want to move such data to a separate FAT32 partition that both Ubuntu and Windows XP can write to.

---

