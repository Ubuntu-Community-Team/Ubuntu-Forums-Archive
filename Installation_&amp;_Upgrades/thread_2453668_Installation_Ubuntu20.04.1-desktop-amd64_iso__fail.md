---
title: "Installation: Ubuntu20.04.1-desktop-amd64 iso  fails on sha256sum test"
date: 2020-11-15
forum: Installation &amp; Upgrades
---

### Post by AUROBINDO MAJUMDAR on 2020-11-15
I downloaded ubuntu-20.04.1-desktop-amd64.iso. I am from India and the browser shows that the download was from 'tifr.rs.in' -- your mirror in India?. I have downloaded twice on 14 Nov .  Signature verification of the check sum file SHA256SUMS file is OK, but the command " sha256sum -c SHA256SUMS 2>&1" outputs  error message -> "ubuntu-20.04.1-desktop-amd64.iso: FAILED".  Looks  like the mirror is broken. Earlier, I tried to upgrade from 18.04,  but it did not work and I had to re-install Ubuntu 18.04.4. If I try to upgrade again I may have a non-working installation again.

---

### Post by TheFu on 2020-11-15
Please post the exact command and the exact output, and please wrap that in code tags.
We assume you've done a quick check that the ISO file is about the correct size, yes?

```
$ sha256sum -c ubuntu-mate-20.04-desktop-amd64.SHA256 
sha256sum: ubuntu-mate-20.04-desktop-amd64.SHA256: no properly formatted SHA256 checksum lines found
```

That isn't the correct way.  I don't know how other people do it, but I do this:
```
$ sha256sum ubuntu-mate-20.04-desktop-amd64.**iso**
a298764d9d2615c6fc5e99c7dddd9d7687f885821e6915c57daf9747b9c33445  ubuntu-mate-20.04-desktop-amd64.iso

$ more ubuntu-mate-20.04-desktop-amd64.**SHA256** 
a298764d9d2615c6fc5e99c7dddd9d7687f885821e6915c57daf9747b9c33445
```
That's 2 separate commands.  Then using my eyes, I check that the command output shows the same sha256sum, as it does above. Simple because I don't have to remember any magical incantation, just that **sha256{tab}** will get the correct program.

And to be extremely clear, both files used have to be in the CWD.
[LIST]
[*]ubuntu-mate-20.04-desktop-amd64.iso
[*]ubuntu-mate-20.04-desktop-amd64.SHA256
[/LIST]

Don't worry that I'm using Mate version. This works for any distro, just change the filenames appropriately.

---

### Post by AUROBINDO MAJUMDAR on 2020-11-16
Thanks., but it did not work with iso image I had downloaded. I tried another mirror in India and that too failed checksum verification. Finally,  downloaded  via torrent and the sha256sum was OK.

---

### Post by TheFu on 2020-11-16
If the sha256sum doesn't match, then it is a bad download.

Seems you got a good one, so if this is solved, help the community out and use the "Thread Tools" button near the top to mark it that way. That way people searching for solutions will find this easier.  Good thread title, BTW.

---

### Post by ajgreeny on 2020-11-16
It sounds as if downloading using a torrent client would be a better way for you to get the iso files, particularly if your network is poor.

A torrent client (transmission is the default in all Ubuntu systems) will take a failures of network in its stride and checks each packet of the large file as it is downloaded; if it detects a bad packet it will download that part again.

---

