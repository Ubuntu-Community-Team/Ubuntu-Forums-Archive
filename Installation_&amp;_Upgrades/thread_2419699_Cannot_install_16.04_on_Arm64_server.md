---
title: "Cannot install 16.04 on Arm64 server"
date: 2019-05-25
forum: Installation &amp; Upgrades
---

### Post by dataradical on 2019-05-25
Hi

I have some Gigabyte R181-T90 and R281-T91 servers with ARM CPUs.

I've tried to install via USB, but the install fails after the boot menu where I select to install Ubuntu. The error message appears to be related to accessing either the USB stick or the hard drive.

As I've not installed before on these servers, my guess is that I'm getting something wrong.
Browsing around a bit, I found an older article mentioning that on such ARM servers, it cannot be installed via USB drive or CD, but needs to be via TFTP. Is that true ?


/Jesper

---

### Post by dino99 on 2019-05-25
Arm hardware was not well supported some times ago; you should try 18.04 lts instead at least to get the better support..

---

### Post by C.S.Cameron on 2019-05-25
Are you using the version of Ubuntu Server at: [https://www.ubuntu.com/download/server/arm](https://www.ubuntu.com/download/server/arm)

---

### Post by dataradical on 2019-05-25
Yes, I'm using the one called ubuntu-16.04.6-server-arm64.iso. I also tried ubuntu-18.04.2-server-arm64.iso

Both can boot to the initial GRUB menu, but after selecting install it will only continue shortly and then stops.

---

### Post by dataradical on 2019-05-25
I tried both 16.04 and 18.04. Both fail the same way.

My thinking is that it may be something specific around UEFI boot that may need to be configured, or (as I found in some old article) that for these servers, only TFTP boot is supported during install

---

