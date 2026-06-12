---
title: "Probleme with xserver and maybe broken libarys"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by lmandrake on 2007-05-02
Hello,

I just install Xubuntu 7.04 from the livecd on my soon to be htpc. The old dvd drive took a long time for the installation but there where not errors reported.

After the installation apt bugged me with a lot "Segmentation fault" core dumped" messages. After I reinstalled apt and copied a clean sources.list it's now working. I installed a couple packages with apt-get and now I get many messages like "ldconfig: /usr/lib/libanthy.so.0 is not an ELF file - it has the wrong magic bytes at the start."

My xserver is also not starting. The log looks fine (see attachment) and even the nvidia logo from the restricted driver is shown. But after that I fall back to the console and "Segmentation fault" core dumped" is shown again. I did a fsck which reported no errors. I think this is all related to this ELF error messages; for example starting mplayer just gives me "mplayer: error while loading shared libraries: /usr/lib/libatk-1.0.so.0: invalid ELF header" but I don't know what to do. Is there a simple solution? Or should I reinstall the system using another drive?

Thank you in advance

Cheers
lamdnrake

---

