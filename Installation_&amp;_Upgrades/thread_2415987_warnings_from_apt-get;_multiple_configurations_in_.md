---
title: "warnings from apt-get; multiple configurations in /etc/apt/sources.list"
date: 2019-04-03
forum: Installation &amp; Upgrades
---

### Post by huff2 on 2019-04-03
Hi Everyone!

I recently ran sudo apt-get update and received multiple warning lines: 

```
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target Translations (contrib/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target DEP-11 (contrib/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target DEP-11 (contrib/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target DEP-11-icons-small (contrib/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target CNF (contrib/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target CNF (contrib/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
N: Skipping acquire of configured file 'contrib/binary-i386/Packages' as repository 'https://download.virtualbox.org/virtualbox/debian bionic InRelease' doesn't support architecture 'i386'
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target Translations (contrib/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target DEP-11 (contrib/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target DEP-11 (contrib/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target DEP-11-icons-small (contrib/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target CNF (contrib/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
W: Target CNF (contrib/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:55
```


I understand that I am being told that I have multiple configurations of the same thing in my /etc/apt/sources.list (sources that apt uses to pull from). My question: should i go through sources.list and delete these? 

If I make a mistake, how can I get the default list of trusted sources to basically "start over"?

Thanks!

---

### Post by huff2 on 2019-04-03
Solved: I just deleted the duplicate lines in /etc/apt/sources.list

---

