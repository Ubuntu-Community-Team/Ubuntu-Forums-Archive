---
title: "Newbie-ish... trying to upgrade to 18.4 but fails..."
date: 2019-04-02
forum: Installation &amp; Upgrades
---

### Post by cosimomo on 2019-04-02
I am trying to upgrade and have been failing since 18.4 was released(I haven't bothered to upgrade seriously till now).I have synced Opera to my mobile and uninstalled on my Lenovo T-450. When I try to upgrade I get the following error and it reverts back to 17.1

W: Target Packages (non-free/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:1W: Target Packages (non-free/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:1
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:1
W: Target Translations (non-free/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:1
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:1
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:1
W: Target DEP-11 (non-free/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:1
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:1
W: Target Packages (non-free/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:2
W: Target Packages (non-free/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:2
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:2
W: Target Translations (non-free/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:2
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:2
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:2
W: Target DEP-11 (non-free/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:2
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/opera-stable.list:4 and /etc/apt/sources.list.d/opera.list:2


How do I get this resolved so I can upgrade to 18.4 and reinstall Opera... Thanks

---

### Post by Impavidus on 2019-04-02
Those are warnings, not errors, so I'm not sure they are the cause of your problem.

There's a problem in the configuration of the repository for opera. As you already removed opera, there's no need to keep the repository configured. Just remove it:```
sudo rm /etc/apt/sources.list.d/opera.list
```After upgrading, restore in the same way you initially added this repository (probably by just following the installation instructions for opera).

17.10 reached end of life in July 2018. You're trying to do an end-of-life upgrade. Before attempting a release upgrade, your system should be fully updated with the latest software of your current release. As 17.10 is no longer supported, it cannot be updated. That may be the source of your problem. The best way to solve this is a fresh install.

I can't say why you couldn't upgrade to 18.04 between April and July last year. There may have been a small and easy to fix problem. But by not solving this problem before 17.10 went unsupported, it turned into a big problem.

If you really want to try an end-of-life upgrade, read this guide: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades). But I think a fresh install is easier and more reliable.

---

### Post by Autodave on 2019-04-02
+1 with Impavidus: save yourself a lot of anguish and time and just do a clean install of 18.04.

  	 	 	 	   Every 2 years, a long term service release is made.  18.04 was the last one: released during the 4th month of 2018, hence the name 18.04.  The next LTS release will be in 2020 during the 4th month.  In the meantime, a new, short term release will be issued every 6 months.  These short term releases are only supported until the next short term release. However, the LTS releases are supported for 5 years.  It is always best to stick with the LTS releases. When it comes time to upgrade one of those, I have always found it easier and quicker to just backup what I need to keep, wipe out what is there, and do a clean install.

---

### Post by cosimomo on 2019-04-03
Thanks for your replies...

So I tried upgrading with a new iso to 18.04 , but since Im a newbie I have run into problems restoring my files... A friend set me up originally so I am not so good at navigating and terminal, and apparently installation... I guess I will need to start a new thread on this one unless you have some insight as to why my drives are full and cannot restore my files

Thanks again for your time and help

---

### Post by cosimomo on 2019-04-03
After a few attempts and false starts I have successfully installed 18.04 and everything seems to be working at this time. Thanks again for your support...:D

---

