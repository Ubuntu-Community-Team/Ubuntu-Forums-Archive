---
title: "apt-get  lzma: Decoder error"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by bogaczew on 2010-10-08
i'm using ubuntu 10.04 64bit. for few days i have problem with installing/updating packages. today i reinstalled my ubuntu, and on fresh system i got again decompress error.

```
Rozpakowanie libqt4-xmlpatterns (z .../libqt4-xmlpatterns_4%3a4.6.2-0ubuntu5.1_amd64.deb) ...
lzma: Decoder error
dpkg-deb: podproces <dekompresja> zwróci&#322; kod b&#322;&#281;du 1
dpkg: b&#322;&#261;d przetwarzania /var/cache/apt/archives/libqt4-xmlpatterns_4%3a4.6.2-0ubuntu5.1_amd64.deb (--unpack):
 krótki odczyt w buffer_copy (uruchomiony dpkg-deb podczas "./usr/lib/libQtXmlPatterns.so.4.6.2")
```

message above says more less 'unpacking lib... lzma: decoder error, short buffer'. when i delete this package from /var/cache/apt.... and install it again with new download from repo, it runs with no error. questions:
1) does anyone have similiar errors, or it's just me, and i should search for answer on my local configuration?
2) it seems that apt-get sometimes dosen't download whole package. what does it use to download packages, wget? it should handle packet drops etc.

---

