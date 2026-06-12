---
title: "Verifying .iso on windows using HashTab"
date: 2022-08-02
forum: Installation &amp; Upgrades
---

### Post by phatman012 on 2022-08-02
Hello,
Can someone tell me how I can verify a download on a windows installation using HashTab please?
Specifically, how can I get the SHA256 or equivalent files to compare it with?
I'm familiar with this method and would rather use it than install linux on windows shell type software.

Thanks in advance,

---

### Post by phatman012 on 2022-08-02
ps I already downloaded the iso, it is:
[ubuntu-22.04-desktop-amd64.iso]("https://mirrors.up.pt/pub/ubuntu-releases/22.04/ubuntu-22.04-desktop-amd64.iso")

---

### Post by phatman012 on 2022-08-02
I think I found them, here:
[https://releases.ubuntu.com/jammy/](https://releases.ubuntu.com/jammy/)

But they are failing the comparison. 

[https://ibb.co/V3y6Tww](https://ibb.co/V3y6Tww)

Any thoughts? 
Am I using the wrong files?

Thanks in advance for looking

---

### Post by sudodus on 2022-08-02
It seems to me that you have the correct sha256sum, but the iso file seems bad. This can happen.

If you wish you can check with some other tools in Windows

[https://rufus.ie](https://rufus.ie) - click on the circle-with-tick-inside icon

[https://www.md5summer.org/](https://www.md5summer.org/)

I am afraid, that you must repeat the download. It is usually more reliable to use a torrent because checksums are used during the whole torrent process, but a conventional download will probably succeed next time, if you have a fairly stable internet connection.

I created an md5sum for you to check with md5summer: 7621da10af45a031ea9a0d1d7fea9643
```

<<< '7621da10af45a031ea9a0d1d7fea9643  ubuntu-22.04-desktop-amd64.iso' md5sum -c
ubuntu-22.04-desktop-amd64.iso: OK

```

Usually you find the sha256sums in the same directory as the iso files, in this case

[https://releases.ubuntu.com/22.04/](https://releases.ubuntu.com/22.04/)

---

### Post by ActionParsnip on 2022-08-03
For Windows:

[https://askubuntu.com/questions/607813/ubuntu-md5-verify-from-windows](https://askubuntu.com/questions/607813/ubuntu-md5-verify-from-windows)

Or from Ubuntu:
[https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview](https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview)

If you use Torrents, you don't have to verify as the torrent protocol checks the file for you :)

---

### Post by phatman012 on 2022-08-06
> **ActionParsnip said:**
> For Windows:

[https://askubuntu.com/questions/607813/ubuntu-md5-verify-from-windows](https://askubuntu.com/questions/607813/ubuntu-md5-verify-from-windows)

Or from Ubuntu:
[https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview](https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview)

If you use Torrents, you don't have to verify as the torrent protocol checks the file for you :)

Thanks for the replies!  :o

---

