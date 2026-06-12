---
title: "Cannot update Ubuntu to latest version"
date: 2021-11-18
forum: Installation &amp; Upgrades
---

### Post by YourSurrogateGod on 2021-11-18
Basically, I got around to finally updating my OS and this is what I saw:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/netplan.io/libnetplan0_0.103-0ubuntu5%7e21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/netplan.io/netplan.io_0.103-0ubuntu5%7e21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/fonts-opensymbol_102.12%2bLibO7.1.6-0ubuntu0.21.04.1_all.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libuno-sal3_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libuno-salhelpergcc3-3_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libuno-cppu3_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libuno-cppuhelpergcc3-3_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/ure_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/uno-libs-private_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libuno-purpenvhelpergcc3-3_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-calc_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-impress_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-draw_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-math_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-help-en-us_7.1.6-0ubuntu0.21.04.1_all.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-help-common_7.1.6-0ubuntu0.21.04.1_all.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-common_7.1.6-0ubuntu0.21.04.1_all.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-gnome_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-gtk3_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/python3-uno_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-base-core_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-writer_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-core_7.1.6-0ubuntu0.21.04.1_amd64.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-style-colibre_7.1.6-0ubuntu0.21.04.1_all.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-style-breeze_7.1.6-0ubuntu0.21.04.1_all.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-style-elementary_7.1.6-0ubuntu0.21.04.1_all.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-style-yaru_7.1.6-0ubuntu0.21.04.1_all.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-ogltrans_7.1.6-0ubuntu0.21.04.1_all.deb
  404  Not Found [IP: 91.189.91.39 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-pdfimport_7.1.6-0ubuntu0.21.04.1_all.deb
  404  Not Found [IP: 91.189.91.39 80]
```

I don't understand... I have an internet connection, I can get to ubuntu.com, so why can't I download these packages?

---

### Post by Frogs Hair on 2021-11-18
Could be a temporary problem. You could select a different download server in Software  & Updates .

---

### Post by MAFoElffen on 2021-11-19
If you ping  these two, what do you get?
```

ping -c 3 us.archive.ubuntu.com
ping -c 3 91.189.91.39

```
If the first fails, then second succeeds... That are the same, which would mean you need to look at your DNS...

---

