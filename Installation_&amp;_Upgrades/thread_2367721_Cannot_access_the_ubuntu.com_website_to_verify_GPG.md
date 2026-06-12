---
title: "Cannot access the ubuntu.com website to verify GPG (PGP?) keys"
date: 2017-08-02
forum: Installation &amp; Upgrades
---

### Post by AbleTassie on 2017-08-02
Apparently I am having a problem accessing the keyserver at Ubuntu.com, requests repeatedly "time out."Apparently others are not having the problem and it is peculiar to my PC. I downloaded an iso of Ubuntu 16.04.2 today and checked the SHA256SUM and got a SUM back, But I cannot verify the GPG (PGP?) keys.  

When I try to follow the protocol here [https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto) I cannot get beyond  the step "Obtain the Public Key from the Ubuntu KeyServer" it times out (see  Terminal output below).

I can visit the website [http://keyserver.ubuntu.com/](http://keyserver.ubuntu.com/)  in my browser and I can see "SKS OPenPGP Public Key Server" on that page. But I cannot ping the server and when I run the command: dig +short keyserver.ubuntu.com the output below on the last line

QUESTION:  Can anybody advise me what is wrong?

Thank you,

Able[B]

Terminal from checking SHA256SUM and trying to verify PGP keys, etc.:[/B]

name@name-Lenovo-IdeaPad-Y510:~$ cd

 name@name-Lenovo-IdeaPad-Y510:~$ cd Downloads
 name@name-Lenovo-IdeaPad-Y510:~/Downloads$ sha256sum -b *.iso
 0f3086aa44edd38531898b32ee3318540af9c643c27346340deb2f9bc1c3de7e *ubuntu-16.04.2-desktop-amd64.iso
 name@name-Lenovo-IdeaPad-Y510:~/Downloads$  gpg --verify SHA256SUMS.gpg SHA256SUMS
 gpg: Signature made Thu 16 Feb 2017 04:04:27 PM PST using DSA key ID FBB75451
 gpg: Can't check signature: public key not found
 gpg: Signature made Thu 16 Feb 2017 04:04:27 PM PST using RSA key ID EFE21092
 gpg: Can't check signature: public key not found
 name@name-Lenovo-IdeaPad-Y510:~/Downloads$ gpg --keyserver hkp://keyserver.ubuntu.com --recv-keys 0xFBB75451 0xEFE21092
 gpg: requesting key FBB75451 from hkp server keyserver.ubuntu.com
 gpg: requesting key EFE21092 from hkp server keyserver.ubuntu.com
 gpg: keyserver timed out
 gpg: keyserver receive failed: keyserver error
 name@name-Lenovo-IdeaPad-Y510:~/Downloads$  ping keyserver.ubuntu.com
 PING keyserver.ubuntu.com (91.189.90.55) 56(84) bytes of data.
 ping: sendmsg: Operation not permitted
 ping: sendmsg: Operation not permitted
 ping: sendmsg: Operation not permitted
 ping: sendmsg: Operation not permitted
 ping: sendmsg: Operation not permitted
 ping: sendmsg: Operation not permitted
 name@name-Lenovo-IdeaPad-Y510:~$ dig +short keyserver.ubuntu.com

 91.189.90.55
 91.189.89.49
 name@name-Lenovo-IdeaPad-Y510:~$

---

### Post by sudodus on 2017-08-02
Maybe there was a temporary error. It works for me now to get the keys.

---

### Post by AbleTassie on 2017-08-02
> **sudodus said:**
> Maybe there was a temporary error. It works for me now to get the keys.  Thanks sudodus,  No I think it is my OS. I just switched from the HDD to a pen drive USB and was able to ping and access the site and go through the verification protocol here [https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto) without problems. But last night and this am I could not access with my HDD Lubuntu.   When I boot into Lubuntu on the HDD I am getting a long list of apparent problems instead of just "/dev/sda1: clean, 184181/303334976 files, 4052381/121312000 blocks"  So I am not sure what the problem is. But it looks like it's the HDD OS Lubuntu, corrupted perhaps in some way.                   Thanks,    A.

---

### Post by AbleTassie on 2017-08-02
PS I thought the problem might have something to do with Firejailing Firefox. But I was able to ping the server and also go through the protocol above when using the pen drive OS, even though Firefox was Firejailed.   Thanks,  A.

---

