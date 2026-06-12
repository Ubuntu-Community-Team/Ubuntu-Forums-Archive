---
title: "Can't download Restricted Extras on 12.04.1"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by aisajib on 2012-11-01
I'm trying to install Ubuntu Restricted Extras via Software Manager and terminal but I'm failing. It started to download. I then went out for a while and on return I saw the download failed.

This is what I'm getting when trying to install:


"To install ubuntu restricted extras, these items must be removed:
Libav codec library
Libav utility library"

There's a continue anyway button. I click that, the download starts and stops right away giving me this error:

[B]Please check your Internet connection:

Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/pool/universe/f/freepats/freepats_20060219-1_all.deb](http://bd.archive.ubuntu.com/ubuntu/pool/universe/f/freepats/freepats_20060219-1_all.deb) Size mismatch[/B]

What the heck? I am connected to the Internet and my browser and other apps (oDesk Team) are working nice.

What am I missing?

---

### Post by ashickur.noor on 2012-11-01
ah, 

Change the download source to main server or other. To do that from Software Center--> **Edit**-->**Software Source**, from there **Ubuntu Software** Tab **Download From, **choose your server.

---

### Post by aisajib on 2012-11-01
Thanks!

I didn't really need to do that, though. Apparently it was Qubee. I activated VPN and it worked.

---

