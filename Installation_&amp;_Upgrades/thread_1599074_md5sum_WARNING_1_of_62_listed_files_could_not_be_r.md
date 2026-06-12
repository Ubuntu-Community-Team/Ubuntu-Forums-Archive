---
title: "md5sum: WARNING: 1 of 62 listed files could not be read"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by wcorey on 2010-10-17
In order to upgrade a machine that can not successfully upgrade to 10.4 I downloaded and burned the 10.04.1 iso image off the ubuntu alternate download site. In my first attempt I unsuccessfully burned the image with it failing at the very end. I did perform an md5sum on it and received the precise output I got from my second burn attenpt which DID complete successfully. Here is the output:

md5sum: ./casper/filesystem.squashfs: Input/output error
./casper/filesystem.squashfs: FAILED open or read
md5sum: WARNING: 1 of 62 listed files could not be read


I did research this last night and it seems the common wisdom was to reburn the iso (which I did twice) or copy down the iso again. This I also did and it came down precisely, bit for bit, the same as the first one. Here are the two cksums

walt@cor720:~$ cksum /tmp/ubuntu-10.04.1-desktop-amd64.iso
[COLOR="Blue"]1873051951 719472640[/COLOR] /tmp/ubuntu-10.04.1-desktop-amd64.iso
walt@cor720:~$ cksum Desktop/ubuntu-10.04.1-desktop-amd64.iso
[COLOR="Blue"]1873051951 719472640[/COLOR] Desktop/ubuntu-10.04.1-desktop-amd64.iso

The precise image is found on page 
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

And the iso itself is:
ubuntu-10.04.1-desktop-amd64.iso.torrent


Is there something wrong with this image on the website or is the error about 1 file being unreadable (could that also mean missing?) be erroneous?

I would hate to start an install with a questionable source only to have it die at an unrecoverable point.

Thanks,

Walt

---

### Post by Frogs Hair on 2010-10-17
Some suggest burning the disc at the slowest possible speed in order to avoid file corruption during the burn. I used the same mirror without issue . You may want to try a different computer if possible.

---

### Post by wcorey on 2010-10-17
What I didn't say was I also downloaded and successfully burned (and checked) the 10.10 server iso. 

When you said you downloaded the same iso and it was OK, did you mean it worked OK or md5sum ran OK?

Thank you, btw, for your quick reply.

Walt

---

