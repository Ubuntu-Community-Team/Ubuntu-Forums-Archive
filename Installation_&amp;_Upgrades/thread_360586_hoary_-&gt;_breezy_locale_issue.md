---
title: "hoary -&gt; breezy locale issue"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by barry.rhodes@uklidian.com on 2007-02-13
This is a re-post as I've had no responses at all to my posting from 6 hours ago and I'm a  little desperate. I'm really hoping that someone can help me with this one. 

FYI I'm on a Dell Inspiron 8000 laptop, just Ubuntu, no windows or other OS installed. Current kernel is 2.6.10-6-386.

I've been using 5.04 (Hoary) for quite a while now, and been doing regular updates via synaptic. Rock solid - no problems. I have added extra packages and I do updates via synaptic. But always with the Hoary universe. I then decided this week (I know, 12 months too late) to move up to 6.10 (Edgy). Not in one jump, I decided to go to 5.10 first, as recommended on the upgrade pages on ubuntu.com.

I upgraded by pointing synaptic to the breezy repository. Synaptic did the download and unpack no problem. When it moved to do the install, it got half way though and then had to stop on a fatal problem - locale not found.

Since then I can't start X.

FYI, I followed the advice on the post install notes at [https://help.ubuntu.com/community/BreezyUpgradeNotes](https://help.ubuntu.com/community/BreezyUpgradeNotes)

and I ran

dpkg-reconfigure xserver-xorg

which  didn't fix things. I was logged in as root when I did this and the above command  replied with ...

# dpkg-reconfigure xserver-xorg
perl: warning: Setting locale failed
perl: Please check that your locale settings :
LANGUAGE = "en_GB: en_GB: en_US: en",
LC_ALL = (unset),
LANG = "en_GB"
are supported and installed on your system
perl: falling back to standard locale ("C")
locale : Cannot set LC_CTYPE to default locale: No such file or directory
locale : Cannot set LC_MESSAGES to default locale: No such file or directory
locale : Cannot set LC_ALL to default locale : No such file or directory

I've made no changes to the system since then myself. Bottom line is that my X server can't start. I think this is due to a locale problem. Can someone advise please. FYI I have terminal based access and my wireless lan and everything else seems to work. I'm not actually sure what I have now - hoary or breezy !

regards

Barry

---

### Post by ExemplarUbuntu on 2007-02-28
I had the same problem ages ago. have a look at my thread:

[http://www.ubuntuforums.org/showthread.php?t=85319](http://www.ubuntuforums.org/showthread.php?t=85319)

it might be useful.

---

