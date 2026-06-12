---
title: "firefox-3.5 not working after Karmic upgrade"
date: 2009-09-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ramsayeg on 2009-09-09
Hello,

I've just finished upgrading Ubuntu 9.4 to 9.10 after around two months of playing around with the system. I tried to execute firefox 3.5 and it didn't work, unlike firefox 3 and opera -- both of them work well.

when I try running firefox-3.5 from the terminal I get the following error:

ramsayeg@r510:~$ firefox-3.5 &
[1] 6261
ramsayeg@r510:~$ Couldn't load XPCOM.

Any help getting it back up is appreciated.

also note that I upgraded to the latest build from the firefox repo.

---

### Post by XDevHald on 2009-09-09
Does your Applications drop down in Internet have the shortcut and if so what does the error give if you click it? I am running Karmic as well and not experiencing this issue. If at all possible, remove and re-install firefox 3.5 and see how that works from there. I see that you have not provided you have done this and if you have let us know.

"Couldn't load XPCOM" means it has a broken depency for Firefox and needs to be reinstated for it to be put back into use. This is a small developer term just telling you to re-install.

Let us know how it goes.

---

### Post by ramsayeg on 2009-09-10
> **Steven Myers said:**
> Does your Applications drop down in Internet have the shortcut and if so what does the error give if you click it? I am running Karmic as well and not experiencing this issue. If at all possible, remove and re-install firefox 3.5 and see how that works from there. I see that you have not provided you have done this and if you have let us know.

"Couldn't load XPCOM" means it has a broken depency for Firefox and needs to be reinstated for it to be put back into use. This is a small developer term just telling you to re-install.

Let us know how it goes.


First of all, when I try running the application from the drop-down menu it loads for a while and then force quits, it's not giving me any error whatsoever.

I tried to remove it using sudo apt-get --purge remove firefox-3.5, and then re-installing it using sudo apt-get install firefox-3.5.

Still, it gives me the same error:

ramsayeg@r510:~$ firefox-3.5 &
Couldn't load XPCOM.
[1] 15908
[1]+  Exit 1                  firefox-3.5
ramsayeg@r510:~$ 

it might me worth mentioning that the command firefox also gives me the same error:

ramsayeg@r510:~$ firefox &
[1] 15934
ramsayeg@r510:~$ Couldn't load XPCOM.

[1]+  Exit 1                  firefox
ramsayeg@r510:~$ 

the only command that's working properly at the moment is firefox-3.0. is it possible something got messed up during the upgrade because firefox-3.5 was already installed before?

---

### Post by ramsayeg on 2009-09-10
updating as I go -- I removed everything firefox related by using apt-get remove firefox*. Now that I try using apt-get install firefox*, it gives me the following error:

The following packages have unmet dependencies:
  firefox-3.0: Conflicts: firefox-libthai
E: Broken packages


when I try installing firefox-libthai:

The following packages have unmet dependencies:
  firefox-libthai: Depends: firefox-3.0 but it is not going to be installed
E: Broken packages

---

### Post by ramsayeg on 2009-09-11
Can someone please help? sorry for the bump.

---

### Post by phillw on 2009-09-11
Had a look round, this thread my be of help ....

[http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way](http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way)

As may this one ....

[http://ubuntumanual.org/posts/183/install-or-upgrade-to-firefox-3-5-rc2-in-ubuntu-karmic-jaunty-intrepid-hardy](http://ubuntumanual.org/posts/183/install-or-upgrade-to-firefox-3-5-rc2-in-ubuntu-karmic-jaunty-intrepid-hardy)

I'm chomping at the bit to switch over to koala, but I've promised myself I'll w8 until the 1st w/end in October.

Hope the two threads are of help

Phill.

---

### Post by XDevHald on 2009-09-11
Hey ram, 

Sorry for the delay, life had me busy for awhile. As for the broken packages these can be fixed in Synaptic. If need be, fix the broken packages and remove them and firefox will follow with it. Follow the information phillw gave as they point a little more to your issue with Karmic+Firefox.

I am sitting on Jaunty right now as I pulled away from the alpha testing and will sit in when beta starts up in 6 days. As a recommendation, backup your files and get back on Jaunty and enjoy a stable candidate before Karmic goes full release on the 29th of next month this way you have something to use that is stable for the time being.

---

### Post by ramsayeg on 2009-09-13
> **phillw said:**
> Had a look round, this thread my be of help ....

[http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way](http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way)

As may this one ....

[http://ubuntumanual.org/posts/183/install-or-upgrade-to-firefox-3-5-rc2-in-ubuntu-karmic-jaunty-intrepid-hardy](http://ubuntumanual.org/posts/183/install-or-upgrade-to-firefox-3-5-rc2-in-ubuntu-karmic-jaunty-intrepid-hardy)

I'm chomping at the bit to switch over to koala, but I've promised myself I'll w8 until the 1st w/end in October.

Hope the two threads are of help

Phill.

Thank you, and Steven as well. I used the ubuntuzilla script from the first link and installed firefox-3.5, surprisingly it now works perfectly :).

---

### Post by XDevHald on 2009-09-13
Excellent to hear! Mods can you please place this as [SOLVED]

Thanks and enjoy your desktop ramsayeg.

---

### Post by ernstblaauw on 2009-09-25
I'm also having this issue. but I really like to have the repository version of Firefox, so I don;t need to be concerned about upgrades of Firefox. So, my question is: did you find a solution to this problem, other than using the ubuntuzilla script?

---

