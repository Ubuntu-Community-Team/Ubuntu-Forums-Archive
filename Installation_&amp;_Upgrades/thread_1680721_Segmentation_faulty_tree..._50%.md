---
title: "Segmentation faulty tree... 50%"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by myth1914 on 2011-02-03
Here's the symptom:

```
root@MasterBedroom:~# apt-get upgrade
Reading package lists... Done
Segmentation faulty tree... 50%

```

dmesg gives me:

```
update-manager[2026]: segfault at 7f794459fa8c ip 00007f79302e063a sp 00007fffb8cf3130 error 4 in libapt-pkg.so.4.10.1[7f7930297000+f9000]
[  195.253399] synaptic[2033]: segfault at 7f76a210da8c ip 00007f769379c63a sp 00007fffbfebabe0 error 4 in libapt-pkg.so.4.10.1[7f7693753000+f9000]
[  234.162182] apt-get[2066]: segfault at 7f1d86c1ca8c ip 00007f1d6cea863a sp 00007fff00b76310 error 4 in libapt-pkg.so.4.10.1[7f1d6ce5f000+f9000]
[  376.792251] apt-get[2100]: segfault at 7f7c17085a8c ip 00007f7bfd31163a sp 00007fff71b863b0 error 4 in libapt-pkg.so.4.10.1[7f7bfd2c8000+f9000]

```

This is what fixed it: ```
sudo rm /var/cache/apt/*.bin
```  

I was then able to open synaptic to repair the broken packages.

Took me a while to come across it so I thought I'd put it out there for the next person.

---

### Post by erikthedrink on 2011-02-27
:KSThanks.  This worked great.  Neither my synaptic package manager nor my update manager were working.

---

### Post by Charles07 on 2011-04-03
This has solved my problem...twice now.

Thanks a million!

---

### Post by tuxwrench on 2011-04-05
really appreciate this

---

### Post by jtgeibel on 2011-04-10
Thank you!  This worked for me as well.

---

### Post by olexiyb on 2011-05-22
worked for me as well

---

### Post by rherzog on 2011-11-19
Thanks for telling me how to get rid of this error. :guitar:

---

### Post by CHPbuntu on 2012-05-22
Cool! fixed my problems with software on Kubuntu 10.04! I was wondering what the error was, what I had done this time:smile:, and how I coud fix it. Thanks for posting the fix.

---

### Post by freek_zero on 2012-07-17
Thanks, you saved what little hair I had left from being ripped out.

---

