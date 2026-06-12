---
title: "Installing language support in Ubuntu"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by FirefoxRocks on 2008-01-26
Ok I am trying to install the language packs for gnome, mozilla and openoffice zh, but I am having no luck.

Here is the terminal output:
> root@ubuntu-desktop:~#  sudo apt-get install language-pack-zh language-support-zh language-pack-gnome-zh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gimp-help-common gimp-help-zh-cn im-switch language-pack-gnome-zh-base language-pack-zh-base libchewing3 libchewing3-data
  mozilla-firefox-locale-zh-cn mozilla-firefox-locale-zh-tw openoffice.org-help-zh-cn openoffice.org-help-zh-tw
  openoffice.org-l10n-zh-cn openoffice.org-l10n-zh-tw scim-chewing scim-pinyin scim-tables-zh thunderbird-locale-zh-cn
  thunderbird-locale-zh-tw
Suggested packages:
  hunspell-dictionary-zh-cn myspell-dictionary-zh-cn openoffice.org-hyphenation-zh-cn openoffice.org2-thesaurus-zh-cn
  hunspell-dictionary-zh-tw myspell-dictionary-zh-tw openoffice.org-hyphenation-zh-tw openoffice.org2-thesaurus-zh-tw
Recommended packages:
  gimp-help-en
The following NEW packages will be installed:
  gimp-help-common gimp-help-zh-cn im-switch language-pack-gnome-zh language-pack-gnome-zh-base language-pack-zh
  language-pack-zh-base language-support-zh libchewing3 libchewing3-data mozilla-firefox-locale-zh-cn
  mozilla-firefox-locale-zh-tw openoffice.org-help-zh-cn openoffice.org-help-zh-tw openoffice.org-l10n-zh-cn
  openoffice.org-l10n-zh-tw scim-chewing scim-pinyin scim-tables-zh thunderbird-locale-zh-cn thunderbird-locale-zh-tw
0 upgraded, 21 newly installed, 0 to remove and 0 not upgraded.
Need to get 68.9MB of archives.
After unpacking, 154MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main language-pack-gnome-zh-base 1:7.10+20071012
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main language-pack-gnome-zh 1:7.10+20071120
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main language-pack-zh-base 1:7.10+20071012
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main language-pack-zh 1:7.10+20071120
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main gimp-help-common 2+0.12-1
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main gimp-help-zh-cn 2+0.12-1
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main im-switch 1.14
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main mozilla-firefox-locale-zh-cn 2.0.0.7+1-0ubuntu2
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main mozilla-firefox-locale-zh-tw 2.0.0.7+1-0ubuntu2
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main libchewing3-data 0.3.0-1
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main libchewing3 0.3.0-1
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main scim-chewing 0.3.1-2ubuntu2
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main scim-pinyin 0.5.91-0ubuntu12
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main scim-tables-zh 0.5.7-1ubuntu2
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main openoffice.org-l10n-zh-cn 1:2.3.0-1ubuntu2
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main openoffice.org-help-zh-cn 1:2.3.0-1ubuntu2
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main openoffice.org-l10n-zh-tw 1:2.3.0-1ubuntu2
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main openoffice.org-help-zh-tw 1:2.3.0-1ubuntu2
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main thunderbird-locale-zh-cn 1:2.0.0.0+1-0ubuntu1
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main thunderbird-locale-zh-tw 1:2.0.0.0+1-0ubuntu1
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main language-support-zh 1:7.10+20070626
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-zh-base/language-pack-gnome-zh-base_7.10+20071012_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-zh-base/language-pack-gnome-zh-base_7.10+20071012_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-zh/language-pack-gnome-zh_7.10+20071120_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-zh/language-pack-gnome-zh_7.10+20071120_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-zh-base/language-pack-zh-base_7.10+20071012_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-zh-base/language-pack-zh-base_7.10+20071012_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-zh/language-pack-zh_7.10+20071120_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-zh/language-pack-zh_7.10+20071120_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gimp-help/gimp-help-common_2+0.12-1_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gimp-help/gimp-help-common_2+0.12-1_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gimp-help/gimp-help-zh-cn_2+0.12-1_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gimp-help/gimp-help-zh-cn_2+0.12-1_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/i/im-switch/im-switch_1.14_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/i/im-switch/im-switch_1.14_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/m/mozilla-firefox-locale-all/mozilla-firefox-locale-zh-cn_2.0.0.7+1-0ubuntu2_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/m/mozilla-firefox-locale-all/mozilla-firefox-locale-zh-cn_2.0.0.7+1-0ubuntu2_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/m/mozilla-firefox-locale-all/mozilla-firefox-locale-zh-tw_2.0.0.7+1-0ubuntu2_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/m/mozilla-firefox-locale-all/mozilla-firefox-locale-zh-tw_2.0.0.7+1-0ubuntu2_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libc/libchewing/libchewing3-data_0.3.0-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libc/libchewing/libchewing3-data_0.3.0-1_i386.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libc/libchewing/libchewing3_0.3.0-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libc/libchewing/libchewing3_0.3.0-1_i386.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/s/scim-chewing/scim-chewing_0.3.1-2ubuntu2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/s/scim-chewing/scim-chewing_0.3.1-2ubuntu2_i386.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/s/scim-pinyin/scim-pinyin_0.5.91-0ubuntu12_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/s/scim-pinyin/scim-pinyin_0.5.91-0ubuntu12_i386.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/s/scim-tables/scim-tables-zh_0.5.7-1ubuntu2_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/s/scim-tables/scim-tables-zh_0.5.7-1ubuntu2_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-l10n-zh-cn_2.3.0-1ubuntu2_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-l10n-zh-cn_2.3.0-1ubuntu2_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-help-zh-cn_2.3.0-1ubuntu2_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-help-zh-cn_2.3.0-1ubuntu2_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-l10n-zh-tw_2.3.0-1ubuntu2_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-l10n-zh-tw_2.3.0-1ubuntu2_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-help-zh-tw_2.3.0-1ubuntu2_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org-l10n/openoffice.org-help-zh-tw_2.3.0-1ubuntu2_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird-locales/thunderbird-locale-zh-cn_2.0.0.0+1-0ubuntu1_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird-locales/thunderbird-locale-zh-cn_2.0.0.0+1-0ubuntu1_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird-locales/thunderbird-locale-zh-tw_2.0.0.0+1-0ubuntu1_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird-locales/thunderbird-locale-zh-tw_2.0.0.0+1-0ubuntu1_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-support-zh/language-support-zh_7.10+20070626_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-support-zh/language-support-zh_7.10+20070626_all.deb) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

How come it is unable to obtain the packages/archives?

---

### Post by Partyboi2 on 2008-01-26
can you open a terminal (Applications>Accessories>Terminal)
and post the output of this command
```
cat etc/apt/sources.list
```

---

### Post by zvacet on 2008-01-26
As Partyboi2 say chek that you have all repos open.system>administration>software sources<chek all boxes under ubuntu software tab and under updates tab.Reload.After that system>administration>language support>select language and download it.

---

