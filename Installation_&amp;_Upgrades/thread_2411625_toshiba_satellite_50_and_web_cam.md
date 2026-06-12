---
title: "toshiba satellite 50 and web cam"
date: 2019-02-01
forum: Installation &amp; Upgrades
---

### Post by hsaptus on 2019-02-01
Hello,
after upgrading for 18.04 my laptop cam isn't working. And no device as such is present. Any ideas how to solve it?
hank you in advance.

---

### Post by Topsiho on 2019-02-02
A device that is not present can not be made to work. So first of all you should add an external webcam to your laptop.
Does your laptop have a 64 bit processor? I used to have a Toshiba Satellite A50 (bought in 2005), and I think it was 32-bits. Does it work with 18.04?
Next you should have a program that works with the webcam. Try install cheese (name of program is cheese).

Topsiho

---

### Post by hsaptus on 2019-02-09
Sorry for the late reply. It was one of those weeks. It's a 64 processor and well it worked with previous versions of Ubuntu and with Windows.

hsa@SATELLITE-S50-B:~$ lsmod | ack '^video\b'
video                  45056  2 toshiba_acpi,i915

and yet when ever I try to use cheese for instance I get the no device as such present.

---

### Post by Topsiho on 2019-02-09
I found with duckduckgo that Toshiba Satellite is the name of quite a number of laptops, that are still sold, so my assumption that you have the same laptop that I possessed is not correct. I had a now very old laptop, from 2005, wit a non-pae 32 bit processor, and no webcam, with RAM that I extended to 1,5 GB. It had become way to slow for even the lighter versions of Ubuntu, LU- and Xubuntu, and other.

Topsiho

---

### Post by hsaptus on 2019-02-09
yes, it's a solid brand and this one it's an i7. I usually test everything before upgrading, but some how I spiked the cam. My bad. I have checked everything online about it and I do see it in my computer, so i am gessing it's a glitch with this kernel.

---

