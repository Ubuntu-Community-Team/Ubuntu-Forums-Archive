---
title: "How does Ubuntu update?"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by tbnext on 2008-05-14
what transfer protocol does ubuntu use to download update packages? I work for a university and they're cracking down on downloads and need to know how to identify ubuntu update activity to not ban users who are lawfully updating their machines. 

basically when I do a:

$apt-get update
$apt-get upgrade

how does ubuntu get the update info? ftp? bit-torrent? if you know port info and packet size that would be helpful also, but transfer method is the most important part. Thanks in advance.

---

### Post by Thirtysixway on 2008-05-14
I believe it uses http.  It connects to [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

---

### Post by macaholic on 2008-05-14
Depends on what server you are downloading from. I believe the main servers use http, but many of the mirrors use ftp. It does not use bittorent for updates, bittorent is used only for cd downloads.

---

### Post by tbnext on 2008-05-14
I guess i should have thought about that before posting the question, i guess whatever is in sources will tell me if they're http or ftp, thanks for the quick replies.

---

### Post by MaindotC on 2008-05-14
> **Thirtysixway said:**
> I believe it uses http.  It connects to [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

Thirtysixway please don't advise people using "I believe".  If you have an answer, please state it and support your answer instead of speaking in uncertainties.

I did the update, upgrade and even downloaded an update while sniffing the traffic.  It is HTTP.  Here's a picture for your administrator's records and I can send you the .cap file as well.

---

### Post by tbnext on 2008-05-15
Thanks, that wireshark screenshot is exactly what i needed.

---

