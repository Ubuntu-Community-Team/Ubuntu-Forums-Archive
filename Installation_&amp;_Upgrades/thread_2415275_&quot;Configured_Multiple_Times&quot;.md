---
title: "&quot;Configured Multiple Times&quot;"
date: 2019-03-23
forum: Installation &amp; Upgrades
---

### Post by issamabbasi on 2019-03-23
Hello.

I use Xubuntu on my chromebook and it's been great! However i messed with the repositories and now this shows up whenever i try to apt update:
```
W: Skipping acquire of configured file 'multiverse/source/Sources' as repository 'http://archive.canonical.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:40 and /etc/apt/sources.list:46
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:41 and /etc/apt/sources.list:46
```

thank you.

---

### Post by again? on 2019-03-23
Reset your sources back to default as shown [**here**]("https://ubuntuforums.org/showthread.php?t=2414194&p=13843080#post13843080").

---

### Post by yancek on 2019-03-23
The problem is pretty obvious, you have a lot of problem entries in your /etc/apt/sources.list which you need to either change as suggested above or manually make the corrections to that file.

---

