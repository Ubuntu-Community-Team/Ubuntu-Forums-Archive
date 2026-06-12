---
title: "qbittorrent wont start"
date: 2015-10-25
forum: Installation &amp; Upgrades
---

### Post by night116 on 2015-10-25
just upgraded to ubuntu 15.10 and now my qbittorrent wont start, tried sudo and got the following message.

*** stack smashing detected ***: qbittorrent terminated


*************************************************************
Catching SIGABRT, please report a bug at [http://bug.qbittorrent.org](http://bug.qbittorrent.org)
and provide the following backtrace:
qBittorrent version: v3.2.4
stack trace:
  /lib/x86_64-linux-gnu/libc.so.6 : gsignal()+0x37  [0x7f182f367267]
  /lib/x86_64-linux-gnu/libc.so.6 : abort()+0x16a  [0x7f182f368eca]
  /lib/x86_64-linux-gnu/libc.so.6 : ()+0x78c53  [0x7f182f3aac53]
  /lib/x86_64-linux-gnu/libc.so.6 : __fortify_fail()+0x5c  [0x7f182f44ae8c]
  /lib/x86_64-linux-gnu/libc.so.6 : __fortify_fail()+0  [0x7f182f44ae30]
  qbittorrent : QBtSession::setDownloadRateLimit(long)+0x6b  [0x4919ab]
  qbittorrent : QBtSession::configureSession()+0xa40  [0x49f400]
  qbittorrent : QBtSession::QBtSession()+0x660  [0x4a6430]
  qbittorrent : QBtSession::instance()+0x2b  [0x4a690b]
  qbittorrent : Application::exec(QStringList const&)+0x25  [0x48d165]
  qbittorrent : main()+0x596  [0x485816]
  /lib/x86_64-linux-gnu/libc.so.6 : __libc_start_main()+0xf0  [0x7f182f352a40]
  qbittorrent : _start()+0x29  [0x48a769]

---

### Post by night116 on 2015-10-25
found and fixed issues with the following and all is good.
sudo add-apt-repository ppa:qbittorrent-team/qbittorrent-stable
sudo apt-get update && sudo apt-get install qbittorrent

---

