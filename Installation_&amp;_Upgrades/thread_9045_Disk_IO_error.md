---
title: "Disk I/O error"
date: 2004-12-23
forum: Installation &amp; Upgrades
---

### Post by YorHel on 2004-12-23
hi

I got some problems while installing ubuntu in the "Copying remaining packages to hard disk"-stage. It takes ages when it's trying to copy "slang1", and in the system-log (Alt+F4) I found some disk errors (just typed from the screen, couldn't copy-past):
```

hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
end_request: Disk I/O error

```

when googling, I found that this could be a DMA problem, but how can I disable DMA in the installation, or are there any other solutions?

some system specs:
Intel Pentium 4 2.8 Ghz
Asus Motherboard
1024 MB RAM
120GB SATA Seagate & a 200GB Western Digital (ubuntu is going to that 120GB one)
Gforce FX 5200

---

### Post by diebels on 2004-12-23
After the install program have set up your cd-rom, [alt]+[f2], hdparm -d 0 /dev/cdroms/something. Your install-cd could be corrupted. Run md5sum on it.

---

### Post by YorHel on 2004-12-23
hmm, you were right... checksums didn't match, I thought I had checked that... whatever, just a little CD-scratch in enough for a corrupted CD.
Burnt a new CD, and installation worked, thanks :)

---

