---
title: "latest flash player?"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by jrm91 on 2010-01-05
I can't watch some youtube videos but others I can, but when I go on other websites such as myspace music pages it says I need to install the latest version of flash which I am positive I have done. Firefox had a tab come down from the top of the browser asking if I wanted to install the missing plugins and I did that already and don't know what else to try. Before I installed the plugins it wouldn't let me watch any youtube videos at all but after I installed the plugins it will let me watch some of them but with really choppy playback.

---

### Post by phillw on 2010-01-05
Hi & welcome to the forums.

I'd start off with these, to ensure you have the latest flash plugins ..

```

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
``` You didn't say what type of processor you have (32 bit or 64 bit) there *may* be a newer flash available - But that's a good place to start.

For things FFox, this thread is pretty awesome & worth bookmarking --> [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

lovinglinux is real nice guy & that is an excellent thread for asking questions on.

Regards,

Phill.

---

### Post by jrm91 on 2010-02-03
> **phillw said:**
> Hi & welcome to the forums.

I'd start off with these, to ensure you have the latest flash plugins ..

```

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
``` You didn't say what type of processor you have (32 bit or 64 bit) there *may* be a newer flash available - But that's a good place to start.

For things FFox, this thread is pretty awesome & worth bookmarking --> [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

lovinglinux is real nice guy & that is an excellent thread for asking questions on.

Regards,

Phill.

well I put that in the terminal and it just tells me that I already have it. and when I go to the add/remove programs it says I have flash 10 but some websites tell me that I need it in order to watch videos or play music. i just don't understand.

---

