---
title: "Dansguardian"
date: 2005-04-01
forum: Installation &amp; Upgrades
---

### Post by teumima on 2005-04-01
Anyone out there use Dansguardian with Ubuntu?

I can't get it to work.

---

### Post by mhancoc7 on 2005-11-12
Here is a really straight forward How To:

[http://www.vollmar.ch/dansguardian-e.html]("http://www.vollmar.ch/dansguardian-e.html")

God Bless, Jereme

---

### Post by Vulpus on 2005-12-08
[QUOTE=mhancoc7]Here is a really straight forward How To:

[http://www.vollmar.ch/dansguardian-e.html]("http://www.vollmar.ch/dansguardian-e.html")

God Bless, Jereme[/QUOTE]

I think "really straight forward" is stretching it a bit.  It is really straightforward compared with something that is really, really, really complicated.;)

---

### Post by mhancoc7 on 2005-12-08
Vulpus:

> I think "really straight forward" is stretching it a bit. It is really straightforward compared with something that is really, really, really complicated

Have you had trouble with it? I guess I should have sayed that I found it to be straight forward. :) 

God Bless, Jereme

---

### Post by Vulpus on 2005-12-09
The problem i have had is that it doesnt work.  i.e. it doesnt block undesirable websites.  I am going to give it another go as I have probably missed something but I do not think it is straightforward.  I use ContentProtect on Windows and THAT is straightforward.  though to be fair there have been some bugs in that.  Such as taking 99% of system resources.  

I am willing to work a bit harder with Linux but Dansguardian just seems REALLY complicated to set up.

---

### Post by mhancoc7 on 2005-12-09
You must have missed a step or something. I have it setup and it is almost too draconian.
I had to tweak it a little so I could download zip/tar files and such.

The one thing that I don't like is that it is really easy to turn off.

Good Luck, Jereme

---

### Post by Darrious on 2006-10-07
I'm having a particular problem with it. It conflicts with the Package libpt3-mt

---

### Post by tonhou on 2006-10-07
You could try here for a comprehensive howto:

[http://www.ubuntuforums.org/showthread.php?t=207008](http://www.ubuntuforums.org/showthread.php?t=207008)

--Tony

---

### Post by renohal29 on 2007-04-23
First of all, this is a very good program for someone that could use something like this. I personally don't really need it, but I really recommend it to someone who does. I installed Dansguardian on this computer(friends)  without any problem by using the "install_me" script in the /install_dansguardian_gui_edgy file. I also installed it on my computer to play around with it and then decided to removed it. I removed Dansguardian and Tinyproxy. Now Firefox's settings are locked to the proxy settings and can't get any webpages. Nothing will connect to the internet now exept the update applet. Apt-get can't resolve anything, either. I tried installing Dansguardian manually and after getting Zlib, Pcea, and making links to lib files that dansguardian wanted, I now get this:

 ```
*** glibc detected *** dansguardian: free(): invalid pointer: 0x080d7894 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d1c7cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7d1fe30]
/lib/tls/i686/cmov/libc.so.6(regfree+0x3d)[0xb7d5123d]
dansguardian[0x8070ce0]
dansguardian[0x8085bbe]
dansguardian[0x80a567e]
dansguardian[0x80a5e40]
dansguardian[0x80abb3e]
dansguardian[0x808d9cd]
dansguardian[0x8091e71]
dansguardian[0x80a95d5]
dansguardian[0x80a9769]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7ccaebc]
dansguardian(__gxx_personality_v0+0x141)[0x804b221]
======= Memory map: ========
08048000-080c7000 r-xp 00000000 08:02 245750     /usr/local/sbin/dansguardian
080c7000-080c8000 rw-p 0007f000 08:02 245750     /usr/local/sbin/dansguardian
080c8000-080eb000 rw-p 080c8000 00:00 0          [heap]
b7a00000-b7a21000 rw-p b7a00000 00:00 0
b7a21000-b7b00000 ---p b7a21000 00:00 0
b7ba0000-b7bdb000 r--p 00000000 08:02 178968     /usr/lib/locale/en_US.utf8/LC_CTYPE
b7bdb000-b7bdc000 r--p 00000000 08:02 178984     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7bdc000-b7bdd000 r--p 00000000 08:02 179024     /usr/lib/locale/en_US.utf8/LC_TIME
b7bdd000-b7cb4000 r--p 00000000 08:02 178978     /usr/lib/locale/en_US.utf8/LC_COLLATE
b7cb4000-b7cb5000 rw-p b7cb4000 00:00 0
b7cb5000-b7df0000 r-xp 00000000 08:02 1068850    /lib/tls/i686/cmov/libc-2.5.so
b7df0000-b7df1000 r--p 0013b000 08:02 1068850    /lib/tls/i686/cmov/libc-2.5.so
b7df1000-b7df3000 rw-p 0013c000 08:02 1068850    /lib/tls/i686/cmov/libc-2.5.so
b7df3000-b7df7000 rw-p b7df3000 00:00 0
b7df7000-b7e02000 r-xp 00000000 08:02 1036347    /lib/libgcc_s.so.1
b7e02000-b7e03000 rw-p 0000a000 08:02 1036347    /lib/libgcc_s.so.1
b7e03000-b7e28000 r-xp 00000000 08:02 1068854    /lib/tls/i686/cmov/libm-2.5.so
b7e28000-b7e2a000 rw-p 00024000 08:02 1068854    /lib/tls/i686/cmov/libm-2.5.so
b7e2a000-b7f09000 r-xp 00000000 08:02 129877     /usr/lib/libstdc++.so.6.0.8
b7f09000-b7f0c000 r--p 000de000 08:02 129877     /usr/lib/libstdc++.so.6.0.8
b7f0c000-b7f0e000 rw-p 000e1000 08:02 129877     /usr/lib/libstdc++.so.6.0.8
b7f0e000-b7f14000 rw-p b7f0e000 00:00 0
b7f14000-b7f27000 r-xp 00000000 08:02 129594     /usr/lib/libz.so.1.2.3
b7f27000-b7f28000 rw-p 00012000 08:02 129594     /usr/lib/libz.so.1.2.3
b7f28000-b7f47000 r-xp 00000000 08:02 131108     /usr/lib/libpcre.so.3.12.0
b7f47000-b7f48000 rw-p 0001f000 08:02 131108     /usr/lib/libpcre.so.3.12.0
b7f48000-b7f49000 r-xp 00000000 08:02 131109     /usr/lib/libpcreposix.so.3.12.0
b7f49000-b7f4a000 rw-p 00000000 08:02 131109     /usr/lib/libpcreposix.so.3.12.0
b7f4a000-b7f4b000 rw-p b7f4a000 00:00 0
b7f4b000-b7f4c000 r--p 00000000 08:02 179025     /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f4c000-b7f4d000 r--p 00000000 08:02 194344     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f4d000-b7f4e000 r--p 00000000 08:02 179095     /usr/lib/locale/en_US.utf8/LC_PAPER
b7f4e000-b7f4f000 r--p 00000000 08:02 179026     /usr/lib/locale/en_US.utf8/LC_NAME
b7f4f000-b7f50000 r--p 00000000 08:02 179027     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f50000-b7f51000 r--p 00000000 08:02 179028     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f51000-b7f52000 r--p 00000000 08:02 179029     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f52000-b7f59000 r--s 00000000 08:02 32385      /usr/lib/gconv/gconv-modules.cache
b7f59000-b7f5a000 r--p 00000000 08:02 179030     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f5a000-b7f5b000 rw-p b7f5a000 00:00 0
b7f5b000-b7f74000 r-xp 00000000 08:02 1037533    /lib/ld-2.5.so
b7f74000-b7f76000 rw-p 00019000 08:02 1037533    /lib/ld-2.5.so
bfd37000-bfd4c000 rw-p bfd37000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
```

One thing I forgot to mention is I tried installing Tinyproxy first to see if I can get some kind of an Internet connection, but when i try to view a webpage, it shows tinyproxy's unable to connect page. The proxy in the tinyproxy.conf file is set to 8080 (port firefox is locked to). I changed the user and group from nobody to root as mentioned on tinyproxy's site(I think it was that site). Nothing is working. I have it setup so much the way I want it, I really don't want to reinstall. Just doesn't seem worth it. I that's too much the easy way out, I think :p I'm sure if I could just get an Internet connection with tinyproxy, I can fix the rest of this mess.

Any help would be appreciated!

---

### Post by eschuch on 2007-09-13
remove  the /etc/firefox/* config files.

---

