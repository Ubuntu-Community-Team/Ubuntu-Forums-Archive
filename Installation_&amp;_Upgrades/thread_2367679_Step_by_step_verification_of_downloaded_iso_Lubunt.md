---
title: "Step by step verification of downloaded iso Lubuntu 16.04.2"
date: 2017-08-02
forum: Installation &amp; Upgrades
---

### Post by AbleTassie on 2017-08-02
I downloaded a copy of Lubuntu 16.04.2 on July 17, 2017. I think it was from this site [http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/) . I've already made a complete install on a pen drive with it.

 I checked the SHA256SUM and another similar SUM and they were fine, I am thinking of giving a complete install of this iso on a pen drive to a friend and want to make sure it is OK. 

Can I still check the GPG signatures for this download, or do I need to download a fresh copy? 

I  am unsure of how to  check the GPG signatures. It looks like it depends on having current keys and I do not know where to get the keys.

Can anybody give me or point me to  a step  by step  explanation of checking the GPG signatures associated with this download or a similar one?

I read about a hack of the Linux Mint  website about 1 1/2 years ago and  it makes me feel uncomfortable.

Thanks,

A.

---

### Post by BenginM on 2017-08-02
Hiya , I believe you're lookin' for [This]("https://help.ubuntu.com/community/VerifyIsoHowto")

---

### Post by AbleTassie on 2017-08-02
> **AbleTassie said:**
> I downloaded a copy of Lubuntu 16.04.2 on July 17, 2017. I think it was from this site [http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/) . I've already made a complete install on a pen drive with it.



I checked the SHA256SUM again for the iso I already made a full install on a pen drive and it is: 84ad81825c66b182413007f20d047d34ac7f528079857399a7b529a93edcddfc 
If I Google that SUM I get two hits: [http://iso.linuxquestions.org/ubuntu/ubuntu-16.04.2/](http://iso.linuxquestions.org/ubuntu/ubuntu-16.04.2/) and [http://ftp.uni-kl.de/pub/linux/ubuntu-dvd/lubuntu/releases/16.04/release/SHA256SUMS](http://ftp.uni-kl.de/pub/linux/ubuntu-dvd/lubuntu/releases/16.04/release/SHA256SUMS)

The links above seem to tell me I got the iso that I have from a mirror.

But the SUM I have is not in the downloaded SHA256SUMS document at [http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/). In fact the six 256 SUMs in that SHA256SUM document are given below under my name and you can see none end in "ddfc" as my SUM does. 

QUESTION: If the iso I have already installed is legitimate, where is the SHA256SUMS.gpg for it? 

Thanks,

A.


**Six SHA256SUMs in SHA256SUMS document at [http://releases.ubuntu.com/16.04/:](http://releases.ubuntu.com/16.04/:)**

0f3086aa44edd38531898b32ee3318540af9c643c27346340deb2f9bc1c3de7e *ubuntu-16.04.2-desktop-amd64.iso
aaed1111f4cde22bc62858f20a8f8a323baef1192044ea875bc27499ca8bd02d *ubuntu-16.04.2-desktop-i386.iso
737ae7041212c628de5751d15c3016058b0e833fdc32e7420209b76ca3d0a535 *ubuntu-16.04.2-server-amd64.img
737ae7041212c628de5751d15c3016058b0e833fdc32e7420209b76ca3d0a535 *ubuntu-16.04.2-server-amd64.iso
736f2c5700313494a2282092ca0f8b0048883ed48c5fdcf585d6e1852a3a110f *ubuntu-16.04.2-server-i386.img
736f2c5700313494a2282092ca0f8b0048883ed48c5fdcf585d6e1852a3a110f *ubuntu-16.04.2-server-i386.iso

---

### Post by deadflowr on 2017-08-02
wrong release
You have Lubuntu not Ubuntu
Lubuntu iimages are never in the Ubuntu image section
try:
[http://cdimage.ubuntu.com/lubuntu/releases/16.04.2/release/]("http://cdimage.ubuntu.com/lubuntu/releases/16.04.2/release/")

---

### Post by sudodus on 2017-08-02
But those checksums belong to Ubuntu desktop and Ubuntu server.

Your Lubuntu iso file and its checksum is correct. It is found at

[cdimage.ubuntu.com/lubuntu/releases/16.04.2/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04.2/release/)

in the file [SHA256SUMS](http://cdimage.ubuntu.com/lubuntu/releases/16.04.2/release/SHA256SUMS)

and I have checked that it is correct (tested with my copy of the iso file),

```
echo '84ad81825c66b182413007f20d047d34ac7f528079857399a7b529a93edcddfc *lubuntu-16.04.2-desktop-amd64.iso'  | sha256sum -c
lubuntu-16.04.2-desktop-amd64.iso: OK

```

---

### Post by AbleTassie on 2017-08-02
deadflowr and Sudodus,

Thanks for checking the SHA256SUM of my Lubuntu iso. 

This article has started me worrying. _Why the Linux Mint hack is an indicator of a larger problem_
[URL="http://www.techrepublic.com/article/why-the-linux-mint-hack-is-an-indicator-of-a-larger-problem/"]
http://www.techrepublic.com/article/why-the-linux-mint-hack-is-an-indicator-of-a-larger-problem/[/URL]

So I wanted to be conscientious, but I am having trouble checking GPG (or PGP?) signatures myself for some reason. See my most recent post _Cannot Access the ubuntu.com website to verify GPG (PGP?) keys _here: 
[https://ubuntuforums.org/showthread.php?t=2367721](https://ubuntuforums.org/showthread.php?t=2367721) 

A.

---

### Post by AbleTassie on 2017-08-03
Thanks to everybody. I will mark SOLVED.

A.

---

