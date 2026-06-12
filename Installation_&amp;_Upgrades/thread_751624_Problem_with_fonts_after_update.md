---
title: "Problem with fonts after update"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by marlon89br on 2008-04-10
Hi everyone, my first post here

Yesterday at night I made an update on my Gutsy... After it, all the new applications that I opened had squares in the fonts... after rebooting, all the system became that way, including Gnome and its applications. But some of them are normal, such as the terminal emulator, OpenOffice and Skype.

Please help me!! I didn't made mistakes, I just updated the system with update-manager :confused:
I'm not at home now, but I've found a log in /var/log/apt/ that showed me the packages updated

One of them was ghost-script, and it altered packages like truetype, type1, type3...
Is there a way to revert the packages to a former version?

Thanks for helping me...
Márlon

---

### Post by marlon89br on 2008-04-11
Posting the fragment of /var/log/apt/term.log that refers to that update:

```


Log started: 2008-04-09  20:11:56
(Reading database ... 112822 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.48.0.2+really0ubuntu12.2 (using .../flashplugin-nonfree_9.0.124.0ubuntu1~gutsy1_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Preparing to replace libgs8 8.61.dfsg.1~svn8187-0ubuntu3.3 (using .../libgs8_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb) ...
Unpacking replacement libgs8 ...
Preparing to replace ghostscript 8.61.dfsg.1~svn8187-0ubuntu3.3 (using .../ghostscript_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb) ...
Cleaning up font configuration of gs...
Cleaning up category psprint..
Cleaning up category cmap..
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category gsfontderivative..
Cleaning up category type3..
Cleaning up category type1..
Unpacking replacement ghostscript ...
Preparing to replace ghostscript-x 8.61.dfsg.1~svn8187-0ubuntu3.3 (using .../ghostscript-x_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb) ...
Unpacking replacement ghostscript-x ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu1~gutsy1) ...
Downloading...
--20:12:01--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.166.70
Connecting to fpdownload.macromedia.com|72.246.166.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,044,538 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%   42.20 KB/s
   50K .......... .......... .......... .......... ..........  3%  104.98 KB/s
  100K .......... .......... .......... .......... ..........  5%  108.25 KB/s
  150K .......... .......... .......... .......... ..........  6%  104.13 KB/s
  200K .......... .......... .......... .......... ..........  8%  106.61 KB/s
  250K .......... .......... .......... .......... .......... 10%  102.30 KB/s
  300K .......... .......... .......... .......... .......... 11%  107.32 KB/s
  350K .......... .......... .......... .......... .......... 13%  105.93 KB/s
  400K .......... .......... .......... .......... .......... 15%  106.35 KB/s
  450K .......... .......... .......... .......... .......... 16%  103.38 KB/s
  500K .......... .......... .......... .......... .......... 18%  107.66 KB/s
  550K .......... .......... .......... .......... .......... 20%  105.09 KB/s
  600K .......... .......... .......... .......... .......... 21%  104.79 KB/s
  650K .......... .......... .......... .......... .......... 23%  105.33 KB/s
  700K .......... .......... .......... .......... .......... 25%  101.21 KB/s
  750K .......... .......... .......... .......... .......... 26%  105.99 KB/s
  800K .......... .......... .......... .......... .......... 28%  106.38 KB/s
  850K .......... .......... .......... .......... .......... 30%  104.62 KB/s
  900K .......... .......... .......... .......... .......... 31%  108.68 KB/s
  950K .......... .......... .......... .......... .......... 33%  102.88 KB/s
 1000K .......... .......... .......... .......... .......... 35%  106.86 KB/s
 1050K .......... .......... .......... .......... .......... 36%  106.40 KB/s
 1100K .......... .......... .......... .......... .......... 38%  105.93 KB/s
 1150K .......... .......... .......... .......... .......... 40%  104.19 KB/s
 1200K .......... .......... .......... .......... .......... 42%  105.90 KB/s
 1250K .......... .......... .......... .......... .......... 43%  105.51 KB/s
 1300K .......... .......... .......... .......... .......... 45%  106.89 KB/s
 1350K .......... .......... .......... .......... .......... 47%  105.81 KB/s
 1400K .......... .......... .......... .......... .......... 48%  106.04 KB/s
 1450K .......... .......... .......... .......... .......... 50%  104.21 KB/s
 1500K .......... .......... .......... .......... .......... 52%  106.35 KB/s
 1550K .......... .......... .......... .......... .......... 53%  106.44 KB/s
 1600K .......... .......... .......... .......... .......... 55%  105.48 KB/s
 1650K .......... .......... .......... .......... .......... 57%  106.83 KB/s
 1700K .......... .......... .......... .......... .......... 58%  102.90 KB/s
 1750K .......... .......... .......... .......... .......... 60%  106.83 KB/s
 1800K .......... .......... .......... .......... .......... 62%  107.78 KB/s
 1850K .......... .......... .......... .......... .......... 63%  104.84 KB/s
 1900K .......... .......... .......... .......... .......... 65%  106.14 KB/s
 1950K .......... .......... .......... .......... .......... 67%  105.04 KB/s
 2000K .......... .......... .......... .......... .......... 68%  106.38 KB/s
 2050K .......... .......... .......... .......... .......... 70%  105.31 KB/s
 2100K .......... .......... .......... .......... .......... 72%  106.63 KB/s
 2150K .......... .......... .......... .......... .......... 73%  103.76 KB/s
 2200K .......... .......... .......... .......... .......... 75%  105.92 KB/s
 2250K .......... .......... .......... .......... .......... 77%  106.35 KB/s
 2300K .......... .......... .......... .......... .......... 79%  106.92 KB/s
 2350K .......... .......... .......... .......... .......... 80%  104.62 KB/s
 2400K .......... .......... .......... .......... .......... 82%  105.03 KB/s
 2450K .......... .......... .......... .......... .......... 84%  106.38 KB/s
 2500K .......... .......... .......... .......... .......... 85%  106.36 KB/s
 2550K .......... .......... .......... .......... .......... 87%  106.90 KB/s
 2600K .......... .......... .......... .......... .......... 89%  105.34 KB/s
 2650K .......... .......... .......... .......... .......... 90%  104.33 KB/s
 2700K .......... .......... .......... .......... .......... 92%  105.90 KB/s
 2750K .......... .......... .......... .......... .......... 94%  106.83 KB/s
 2800K .......... .......... .......... .......... .......... 95%  106.30 KB/s
 2850K .......... .......... .......... .......... .......... 97%  103.00 KB/s
 2900K .......... .......... .......... .......... .......... 99%  106.38 KB/s
 2950K .......... .......... ...                             100%  111.55 KB/s

20:12:36 (103.05 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3044538/3044538]

Download done.
Flash Plugin installed.

Setting up libgs8 (8.61.dfsg.1~svn8187-0ubuntu3.4) ...

Setting up ghostscript (8.61.dfsg.1~svn8187-0ubuntu3.4) ...
Updating font configuration of gs...
Cleaning up category psprint..
Cleaning up category cmap..
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category gsfontderivative..
Cleaning up category type3..
Cleaning up category type1..
Updating category type1..
Updating category type3..
Updating category gsfontderivative..
Updating category truetype..
Updating category cid..
Updating category cmap..
Updating category psprint..
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.

Setting up ghostscript-x (8.61.dfsg.1~svn8187-0ubuntu3.4) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Log ended: 2008-04-09  20:12:45


```

I've tried to do this:
```
sudo apt-get --reinstall ghostscript
```
But it didn't work :(.

Does anyone have any suggestions?

---

### Post by marlon89br on 2008-04-12
UP!
Please, I don't want to reinstall my Ubuntu...

---

