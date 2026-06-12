---
title: "sudo apt-get error (broken libraries)"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by scuba123 on 2008-07-28
Hi Everyone,

I have a problem regarding to "sudo apt-get". If I ran it, I received the following error messages:
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
apt-get: relocation error: /usr/lib/libapt-pkg-libc6.7-6.so.4.6: symbol _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_PKS3_i, version GLIBCXX_3.4.9 not defined in file libstdc++.so.6 with link time reference

I have tried with the following commands but still have no luck: 
sudo ln -s /usr/lib/libstdc++.so.6 /usr/local/lib/
sudo apt-get install -f
sudo dpkg --configure -a
Please help. Your effort is highly appreciated. Thanks in advance.

scuba123

---

### Post by Partyboi2 on 2008-07-30
Try what is suggested in this [[COLOR=Blue]bug report[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/180160").

---

### Post by scuba123 on 2008-07-30
Hello Partyboi2,

Thanks for your reply. I followed the listed suggestion on the link. Let me paste the suggestions:
$ ldconfig -p |grep libstdc++

         libstdc++.so.6 (libc6) => /usr/lib/libstdc++.so.6
         libstdc++.so.6 (libc6) => /usr/local/lib/libstdc++.so.6
$ diff /usr/lib/libstdc++.so.6 /usr/local/lib/libstdc++.so.6
   Binary files /usr/lib/libstdc++.so.6 and /usr/local/lib/libstdc++.so.6
differ
The two files are different which means there are two different versions gcc
in the system? I found a gcc directory under /usr/local

Then : $ cat /etc/ld.so.conf.d/libc.conf
# libc default configuration
/usr/local/lib

I added /usr/lib to the file and then run :
$sudo ldconfig
---------------------------------------
Then I restarted my pc. When I re-tried to run "sudo apt-get", I still received the following error messages:
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
apt-get: relocation error: /usr/lib/libapt-pkg-libc6.7-6.so.4.6: symbol _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_PKS3_i, version GLIBCXX_3.4.9 not defined in file libstdc++.so.6 with link time reference
------------------------
Do you have any other suggestions? Please help. Thanks alot.

Regards,

scuba123

---

### Post by semem on 2010-02-24
I had the same problem. I installed the second gcc and then couldn't use apt-get and some other programs. 

To repair this problem I added in libc.conf line /usr/lib and COMMENT!!! default line /usr/local/lib. It seems it helped me.

P.S.: with two lines /usr/local/lib and /usr/lib in libc.conf it doesn't work

Have fun,
Dima

---

### Post by botcser on 2012-11-17
> **semem said:**
> I had the same problem. I installed the second gcc and then couldn't use apt-get and some other programs. 

To repair this problem I added in libc.conf line /usr/lib and COMMENT!!! default line /usr/local/lib. It seems it helped me.

P.S.: with two lines /usr/local/lib and /usr/lib in libc.conf it doesn't work

Have fun,
Dima

Thx you, its real work!
(then need to run "ldconfig")

---

