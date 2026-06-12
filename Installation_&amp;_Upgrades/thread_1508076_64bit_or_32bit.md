---
title: "64bit or 32bit"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by mnpilgrim on 2010-06-12
I am a bit confused as a new user of Ubuntu 10.4. When I downloaded the ISO from Ubuntu, I was told to install 32 bit which was "recommended for daily computer use". I took their recommendation literally and have installed the 32 bit OS.

Then I read the following from Ubuntu documentation " If your system is 64 bit capable, we recommend installing it".

See:

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

[www.ubuntu.com/desktop/get-ubuntu/download](www.ubuntu.com/desktop/get-ubuntu/download)

What gives?

---

### Post by llawwehttam on 2010-06-12
don't worry about it.

64 bit gives some computers a faster experience but If 32 bit is running fine for you don't bother.

I use 64 bit and it is slightly faster but not noticeably.

---

### Post by quadproc on 2010-06-12
> **mnpilgrim said:**
> I am a bit confused as a new user of Ubuntu 10.4. When I downloaded the ISO from Ubuntu, I was told to install 32 bit which was "recommended for daily computer use". I took their recommendation literally and have installed the 32 bit OS.

Then I read the following from Ubuntu documentation " If your system is 64 bit capable, we recommend installing it".

The suggested installation choice documentation that you read is a bit dated now.  These days, most software is available for 64 bit processors and Ubuntu certainly is.

The Intel/AMD 64 bit processors will run 32 bit operating systems and applications so you can use the 32 bit Ubuntu if you like, but there are a few restrictions.  For example, the maximum file size is 4 GB, the maximum amount of memory that can be used is 4 GB, the maximum disk size is either 1 or 2 TB (I forget which), and so on.

Presently, a small amount of applications software is available which _requires_ a 64 bit processor and will not run on a 32 bit system.  As time passes, this will become more commponplace.  And the 32 bit software will become legacy and support for it will fade and finally vanish.

I suggest that you plan to change to 64 bit software at a future date when it is convenient for you, perhaps when you wish to install a new release.  In the meanwhile a 32 bit operating system will probably work well for you.

quadproc

---

### Post by danzvash on 2010-06-12
> **quadproc said:**
>   For example, the maximum file size is 4 GB, the maximum amount of memory that can be used is 4 GB, the maximum disk size is either 1 or 2 TB (I forget which), and so on.
quadproc
// tyre screech
Actually ... There's no such limit on file size with 32bit Linux: file size maximum is filesystem-dependent, which with ext4 is 16TiB. Max memory limit per process of 4Gb can be overcome if necessary (unlikely for 99.9% of installations) by enabling PAE in kernel. Maximum disk size is limited by hardware rather than by Linux.

So these are not real advantages of 64bit over 32 bit Ubuntu. Just to be clear ;-)

---

