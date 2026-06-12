---
title: "Miscarried upgrading to 11.10"
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by cantave on 2012-02-15
I've been using Ubuntu as a Windows application since May 2011. It's  great compared to Windows. Today I've finally accepted Ubuntu Update  Manager's persistent suggestion to upgrade to 11.10. 

Unfortunately  the process froze in the "Installing" step, and eventually I've been  forced to restart my laptop. After going back to Ubuntu and opening up  Update Manager again, I've found it tells me this upgrade is only  partial, as some files were not installed (but it does not give me the  option to install the missing files). Now desktop looks like Ubuntu has  been upgraded (different visualization of bars, etc.), but I'm unable to  use pointer/mouse at all. By using keyboard I've been  able to transfer my most important documents to the Windows section, in  case I must uninstall Ubuntu completely and install it again. Of  course my dear Ubuntu cannot be operative like it is now, semi-paralytic.

What would you, wise Ubuntu people, recommand me to get out of this sticky patch?

Should  I remove installation and install Ubuntu 11.10 again from scratch? But then  what will happen to all my Ubuntu programs and applications --Spotify, Calibre, LaTex, etc.? Will they disappear with uninstallation?

Or  should I try to save the day by giving the system some commands via  Terminal? I'm not afraid of it (as a girl in the 80's I used programs MS  DOS-based), but I'm afraid I would need concrete instructions, as I'm a  simple user, therefore software-illiterate.

I miss my Ubuntu and would like very much to be able to get back to it again. Many, many thanks in advance for your help.

Rosanna

---

### Post by zvacet on 2012-02-16
Try in terminal

```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

