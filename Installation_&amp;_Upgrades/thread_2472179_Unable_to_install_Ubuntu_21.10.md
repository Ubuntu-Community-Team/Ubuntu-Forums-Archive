---
title: "Unable to install Ubuntu 21.10"
date: 2022-02-20
forum: Installation &amp; Upgrades
---

### Post by GirishSharma on 2022-02-20
I just downloaded [https://releases.ubuntu.com/21.10/ubuntu-21.10-desktop-amd64.iso](https://releases.ubuntu.com/21.10/ubuntu-21.10-desktop-amd64.iso) and verified its [COLOR=#111111][FONT=Ubuntu]SHA256 checksum. Burned a blank DVD by using brasero without any error. When I tried to install after around 10 minutes I got failed to start installer message and after around 5 minutes, it showed me a desktop with installation option, but nothing happened when I tried to proceed for installation.  Very frustrating and idiot way to install the OS.  First time, I am really very sad by Ubuntu [/FONT][/COLOR]:(

Anyone please help me to get me install 21.10.

---

### Post by oldfred on 2022-02-20
What brand/model system?
That seems very slow, I had similar issues trying to install Ubuntu to a very old system. 
That older system needed a lighter weight flavor.
And actually for that system, both server install and then a lightweight gui works, but the mid-weight Kubuntu also worked. I prefered Kubuntu as I use it on my newer systems also.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

---

### Post by Impavidus on 2022-02-20
It could be a problem with the dvd drive too. Systems with a dvd drive are getting old and old drives may get dirty and unreliable.

---

### Post by GirishSharma on 2022-02-21
Finally, I drop my idea to go with 21.10. I found an old DVD of 16.04.3 LTS and it worked without any error.  So there is no issue with my DVD drive, even it successfully worked with a DVD which I wrote around 2 year back. Today's new developers need to understand that make the things simple as much as you can and before launching to public, just confirm that what ever you are going to publish, is it working or not, at lease once for sure. Github is another place, where they have uploaded many code, apps, but when a person wish to test, finally, he has to drop his idea because there is no step by step installation instructions, they have just flooded with code.

---

### Post by ajgreeny on 2022-02-21
16.04 is now out of support so if you haven't signed up to the Extended Security Maintenance (ESM) which is available for that version, you will get no more updates/upgrades of packages, nor will you be able to install any applications in the usual way.
Without that system enabled, 16.04 is a huge security risk not only to you but to all other computer users on the internet, so please, do not continue with 16.04 without signing up to ESM at [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

In spite of your comments about checking the SHA256 checksum, I would still suspect that your DVD of 21.10 was not burned totally successfully, thus causing the problem.

I suggest you try using a live-install USB thumb-drive, still using the 21.10 iso you downloaded, instead of a DVD; it is likely to be faster both running live and installing the system to your computer. Then in a couple of months, or just before 21.10 loses its support you can upgrade the system to the latest LTS version 22.04 which will be supported until 2027

---

### Post by ActionParsnip on 2022-02-21
You could try 22.04. It is due for release soon and you will update to the release candidate when it is available fully

---

### Post by ajgreeny on 2022-02-22
> **ActionParsnip said:**
> You could try 22.04. It is due for release soon and you will update to the release candidate when it is available fully
Agreed, as long as you are prepared for a few odd mishaps along the way.

I have been dual booting Xubuntu 20.04 with Xubuntu 22.04 for a long time now without any big problems arising so I suspect from now that the coming weeks will also be similarly trouble-free.
If you're not sure about your capabilities to right any wrongs that happen in that developer version, install 20.04 which is wonderfully stable and trouble free for most users; my Xubuntu 20.04 certainly has been.

---

### Post by GirishSharma on 2022-02-22
> **ajgreeny said:**
> 16.04 is now out of support so if you haven't signed up to the Extended Security Maintenance (ESM) which is available for that version, you will get no more updates/upgrades of packages, nor will you be able to install any applications in the usual way.
Without that system enabled, 16.04 is a huge security risk not only to you but to all other computer users on the internet, so please, do not continue with 16.04 without signing up to ESM at [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

In spite of your comments about checking the SHA256 checksum, I would still suspect that your DVD of 21.10 was not burned totally successfully, thus causing the problem.

I suggest you try using a live-install USB thumb-drive, still using the 21.10 iso you downloaded, instead of a DVD; it is likely to be faster both running live and installing the system to your computer. Then in a couple of months, or just before 21.10 loses its support you can upgrade the system to the latest LTS version 22.04 which will be supported until 2027

There are two questions from your reply :

1.>I would still suspect that your DVD of 21.10 was not burned totally successfully, thus causing the problem.
How do I check that my burnt DVD is ok. There is SHA256 for iso but how do I check that my DVD is burnt ok, any SHA256 for burnt DVD ?

2.>I suggest you try using a live-install USB thumb-drive, still using the 21.10 iso you downloaded
What is live-install USB thumb-drive? Will you please elaborate more.

---

### Post by tea for one on 2022-02-22
> **GirishSharma said:**
> What is live-install USB thumb-drive? Will you please elaborate more.

You use a USB stick (also known as thumb drive or flash drive) instead of a DVD.
More info here [https://ubuntu.com/tutorials/install-ubuntu-desktop#3-create-a-bootable-usb-stick](https://ubuntu.com/tutorials/install-ubuntu-desktop#3-create-a-bootable-usb-stick)

In post no 2, you were asked to supply details of your PC because it is entirely possible that Ubuntu may not be the best choice.
A lighter flavour of the Ubuntu family may perform better.

---

### Post by Impavidus on 2022-02-22
1: A dvd drive with a dvd inside is a file. Everything is a file, unless it's a process. You can find this file somewhere in /dev. With a bit of luck it has a recognisable name. You can run a sha256 check on that file.

2: A live usb is just like a live dvd, but now on a usb drive. They are faster, reusable, can provide persistent storage and are compatible with computers that have no dvd drive (like most computers nowadays). Only very old computers (15 years or more) can't boot from usb; on those you still need a dvd.

---

