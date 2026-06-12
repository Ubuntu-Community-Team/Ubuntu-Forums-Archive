---
title: "Problem with upload"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Artoo on 2010-02-22
Hello guys, I started having problem with upload right after updating my Karmic to Lucid Lynx, with Alpha 1 + 2 weeks daily CD. I do daily updates, and the problem still persists.

On sites like speedtest.net, download test works ok, but it times out on upload. It's not a flash bug, as it doesn't work on similar sites using java (sun version, on both firefox and chromium dailies). The only indicator of what could be wrong, is a repeating bug in wireshark log during upload test: "[TCP Retransmission] [TCP segment of a reassembled PDU]". What's odd is that normal http upload (like google docs) works ok.
Other indicators are: no upload in dropbox, amsn not able to connect (newest svn), no outgoing messages in gajim (clean xml console) and uploading files to external server through scp or filezilla resulting in 0 byte size files.

Things I know about this bug: it's started on transition to Lucid from Karmic, it's not my ISP or router issue (Windows 7 on same machine works ok), it doesn't matter whether I connect through ethernet or wifi (doesn't work either way), it's not a NetworkManager issue (tried with wicd too), and that it's gotta be something on system level, because same things (0 bytes files, no flash/java upload) happen on a clean WindowsXP installation inside VirtualBox.

I echoed all of /proc/sys/net values to their defaults, and I'm out of ideas. Is there a way to debug it further and find the possible culprit?

Relevant specs are: 2.6.32-14-generic x64 kernel, Intel 5100 WiFi and up-to-date Lucid packages.

---

