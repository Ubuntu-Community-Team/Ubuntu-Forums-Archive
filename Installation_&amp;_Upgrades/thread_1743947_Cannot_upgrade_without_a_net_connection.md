---
title: "Cannot upgrade without a net connection"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Fibonacci on 2011-04-29
Hello.

I currently have a very spotty and unreliable network connection, yet I'm trying to upgrade to Natty – from an alternate installer CD.
When running cdromupgrade, I first get this message:

> Include latest updates from the Internet?

The upgrade system can use the internet to automatically download the latest updates and install them during the upgrade.  If you have a network connection this is highly recommended.

The upgrade will take longer, but when it is complete, your system will be fully up to date.  You can choose not to do this, but you should install the latest updates soon after upgrading.
**If you answer 'no' here, the network is not used _at all._**

(emphasis added)

Then, I answer 'no', of course.

Shortly thereafter I get the following error message:

> Error authenticating some packages

It was not possible to authenticate some packages. **This may be a transient network problem**. You may want to try again later. See below for a list of unauthenticated packages.

amule
amule-common
[800 lines omitted]
zlib1g-dev

Yes I've got a network problem, and it doesn't look like it's transient. But I thought the network would not be used? That was the whole point of downloading the CD.

I've been at it for about 24 hours. How can I upgrade then?

---

### Post by prshah on 2011-04-29
> **Fibonacci said:**
> Shortly thereafter I get the following error message:

In this particular case, the error is probably because the CD has errors. It has nothing to do with the Internet. Perform a media check to ensure the CD is proper (or check dmesg log for multiple entries of cd drive errors).

If the media check shows a fully working CD, then perform a MD5SUM check to ensure that the CD image has not been compromised.

Another point you will want to consider: Even after upgrading from an alternate CD, you will still have to download about 500+ MB updates. You may be better off upgrading directly from the Internet.

---

### Post by cariboo on 2011-04-30
You can do an in place install from the Live CD, you don't need a network connection to do it.

---

### Post by Fibonacci on 2011-04-30
> **prshah said:**
> In this particular case, the error is probably because the CD has errors. It has nothing to do with the Internet. Perform a media check to ensure the CD is proper (or check dmesg log for multiple entries of cd drive errors).

There seems to be one error only in dmesg. The CDROM integrity test was successful, though.

> **prshah said:**
> If the media check shows a fully working CD, then perform a MD5SUM check to ensure that the CD image has not been compromised.

The image is OK. I'm re-burning it just in case.

> **prshah said:**
> Another point you will want to consider: Even after upgrading from an alternate CD, you will still have to download about 500+ MB updates. You may be better off upgrading directly from the Internet.

I know, but that can wait until I get a decent net connection. I just want (for the time being) an update where "the network is not used at all."

> **cariboo907 said:**
> You can do an in place install from the Live CD, you don't need a network connection to do it.

Yes, I would have to wipe my main partition for that, too. In that case I'd rather stick with Maverick, thank you very much.

---

### Post by Bucky Ball on 2011-04-30
Another point to ponder: I hope you have some time on your hands as the forums are crawling with 11.04 problems and you may need a reliable internet connection to start fixing any you encounter (or to find out how to) regardless of how you get 11.04 on there.

If the 11.04 upgrade screws your computer you won't have Maverick to fall back on and without an internet connection you may effectively have a big doorstop. Good luck. ;)

---

### Post by Fibonacci on 2011-04-30
> **Bucky Ball said:**
> Another point to ponder: I hope you have some time on your hands as the forums are crawling with 11.04 problems and you may need a reliable internet connection to start fixing any you encounter (or to find out how to) regardless of how you get 11.04 on there.

If the 11.04 upgrade screws your computer you won't have Maverick to fall back on and without an internet connection you may effectively have a big doorstop. Good luck. ;)

Got a laptop to work on if anything goes wrong. Thank you for your good wishes.

---

### Post by prshah on 2011-04-30
> **Fibonacci said:**
> The CDROM integrity test was successful, though. The image is OK. I'm re-burning it just in case.

I just want (for the time being) an update where "the network is not used at all."

In an alternate CD upgrade scenario, the net is not used at all. The message about a transient network error is simply a stock error message. The actual error is simply that the packages on the CD cannot be authenticated.

This means that the installer has no way of knowing if the packages are genuine or not. When using an ISO image, usually, the GPG key is in the root of the CDROM. This "key" is used to authenticate the packages. Usually, an error revolving around this key (Eg read error) will produce such a message.

You can manually add your CD to the repos using the apt-cdrom add command, but it should not be necessary. However, if the errors persist, you can try this; if you get a similar error then you may have to try a new image.

---

### Post by Fibonacci on 2011-05-11
> **prshah said:**
> In an alternate CD upgrade scenario, the net is not used at all. The message about a transient network error is simply a stock error message. The actual error is simply that the packages on the CD cannot be authenticated.

This means that the installer has no way of knowing if the packages are genuine or not. When using an ISO image, usually, the GPG key is in the root of the CDROM. This "key" is used to authenticate the packages. Usually, an error revolving around this key (Eg read error) will produce such a message.

You can manually add your CD to the repos using the apt-cdrom add command, but it should not be necessary. However, if the errors persist, you can try this; if you get a similar error then you may have to try a new image.

Well, I finally have a decent internet connection. But I'm trying to upgrade using the CD only, and I still get the same error message.
The image is good, as checked by md5sum, so a new image would make no difference.
Re-burning it to a CD and adding it with apt-cdrom doesn't work.
Directly mounting the image and updating from that doesn't work.

I get different errors both on my desktop and on my laptop, but neither can be updated at all from the CD.
I don't know what else to try before concluding that updating using the CD is broken.

---

### Post by Fibonacci on 2011-05-17
Is it utterly broken then?

---

### Post by Fibonacci on 2011-06-17
Bump.

---

