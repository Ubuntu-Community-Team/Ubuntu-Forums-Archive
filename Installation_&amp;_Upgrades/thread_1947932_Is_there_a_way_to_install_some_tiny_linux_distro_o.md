---
title: "Is there a way to install some tiny linux distro on M2 256MB card and boot from it?"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by qwxy on 2012-03-27
Hello.

A few monts ago I had a hard disk crash. Ive lost 80 GB of data.
Ive planned installing Windows XP on my 8 GB USB stick and booting it instead of the hard drive. Ive heard that USB ceases to function after 100000 writes. Assuming that Windows XP uses 2 writes per second, that would be enough for approx. 60 days of use. I am wondering how much writes per second LUbuntu 10.04.3 uses?  Also, what is a lifetime of M2 256MB memory card and is there any way to install and boot some linux distro from my M2 256MB memory card using M2 Adaptor?

Ive been googling the Internet and I couldnt find a lot of info about this.

Sorry if Ive posted this on the wrong place.

Someone please help.
Thanks in advance.

---

### Post by oldfred on 2012-03-28
I think you are low on your life estimate. I have seen calculations of closer to 3 to 5 years or about the same as a rotating drive. But you can in Linux add some settings to minimize writes.

Often the small lightweight versions run in RAM memory so not a lot of writing occurs as the system is run.

You may not be able to boot the full installs but the liveCD versions may work of some of the smaller systems. My puppy install looks like it is 274MB, but as an install to a hard drive I had to extract lupu-511.sfs which is 125MB so I think that is double counted.

Some other lightweight versions beside puppy & lubuntu are knoppix and slitaz.

Windows will not do a full install to a USB, you can only create an installer on a USB.

---

