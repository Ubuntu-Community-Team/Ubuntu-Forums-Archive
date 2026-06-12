---
title: "LiveCD 10.04 : Kernel panic : not syncing. Attempted to kill init !"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by Lorenzaccio on 2011-05-30
Hi everyone,

I'm using Ubuntu since the 9.04 release ands I wanted to make a clean install of the 10.04 release.

So I downloaded the ISO image (ubuntu-10.04.2-desktop-amd64.iso) in order to make a liveCD.

I run md5sum on the downloaded file, its result matches the md5 hash of the ubuntu hashtable site.

The problem arises when I try to burn the image onto a CD. So far, I've tried with :

- Brasero, which failed to complete ;
- ISORecorder on Windows : the burning seemed to have succeeded, but when I boot on the CD, I get the error message of the title ;
- Nero, on another computer, with checksum control at the end, which failed with many sector read errors.

I always chose to burn the image, at the lowest speed available.

When I run md5sum on /dev/scd0 (for each CD), I get this message : I/O Error

What's my problem ?

---

### Post by mörgæs on 2011-05-30
Hi, welcome to the fora.

Have you tried 'burning' the ISO image to a USB stick with Unetbootin?

---

### Post by Lorenzaccio on 2011-05-30
No I haven't yet because :
- I'm not sure my BIOS supports booting on USB (how do I check ?)
- I don't have a spare USB stick I can use right now (I'll have to buy one)

But I'll come to that if I have to.

Also, do you have any suggestion for the stick's brand ?

---

### Post by mörgæs on 2011-05-30
You can enter BIOS during boot and see which options are available in the boot sequence. It might be necessary to update the BIOS.

I don't know of any difference between the brands. Just buy a plain USB stick without any software installed and you should be fine.

---

### Post by Lorenzaccio on 2011-05-31
Well, before buying a stick, I attempted one last time to burn a DVD, but this time, I went on the Ubuntu official site, and chose to open the image with brasero.

So after the download, brasero fires up and burns my DVD.
The burning went without problem, but when brasero tried to do the checksum control, it failed.

Nonetheless, I tried to boot on this DVD, and it worked (I could test Ubuntu 10.04, opened some applications, exited nicely).

Now my question is : will the installation work well, even without this checksum control ?

---

### Post by mörgæs on 2011-05-31
I recommend using Brasero as little as possible. Gnomebaker is more reliable.

If you can boot the DVD, there is no need for checksum validation. 

For future reference, here is how to do it:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Lorenzaccio on 2011-05-31
Thanks for the advice.

I've heard of Gnomebaker, but I can't donwload it from the repos (main, universe and multiverse) for my 9.04 version of ubuntu, they seem to be unavailable

---

