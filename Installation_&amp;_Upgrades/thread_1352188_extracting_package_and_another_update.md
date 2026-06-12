---
title: "extracting package and another update"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by new fish on 2009-12-11
Dear Ubuntu guru and friends,

I am newbie on Ubuntu and I am using Ubuntu Koala right now, and it is freaking awesome. I don't use Windows anymore. 

However, I have an issue on slow internet connection. I've already installed several additional software by apt-get or donwload the deb files and I have updated my Ubuntu several times.

Right now, I engage my sister and other family to use Ubuntu. How do I extract/get/acquire whatever package I've installed on my laptop, and then copy it to say it flash disk, and apply it to my sister's computer.

Let's say I've already installed ubuntu-restricted-extras on my ubuntu for multimedia, which is about (I think)75 MB. 
1. How do I apply the same thing on my sister's laptop or other computer by getting whatever files I need or needed from my computer and applying it to my sister's laptop or other computer instead of using Internet from my sister's laptop directly
Beside it is very slow, and I have to pay extra on the connection fee.

2. I noticed that when installing something on Ubuntu, (especially using apt-get install), computer not only download the package of software we want to install, it will also download and install the other packages that may be required when running the software. So how do I know the other packages or libraries or whatever I need to install a software, and then move it to flashdisk and install it on another comp (I think the point is the same as #1)

is there any GUI software to do this job? or from command line? both are fine with me.

I hope you guys understand what I wrote,my English is not very good,though. it's hard to tell what's on my mind.

## NB: My laptop and my sister's laptop are from the same manufacturer, and both x86.  The internet connection is about 5 kbps when traffic is busy, maybe 15 kbps when midnight

Thank guys

---

### Post by Borrot on 2009-12-11
Hmm.. I'm not sure if I know what meant but I think I am.. Your problem is that your internet connection is to slow so your family members can't download packages/files from the internetT(right or wrong?).. You want to transfer this packages/files to their(in this case your sisters) computer. I would recommend you to use a USB Flash drive if the packages/files aren't too big. If they are, consider using a DVD/CD to burn the files on using the pre-installed program "Brasero"..

If you have to zip the files, use you can search for it in the "Software Center" if your connection isn't too slow..

If you just get out 5-15 **k**bit/s I think that you/your family should consider to buy a better internet speed.

---

### Post by halj32 on 2009-12-11
u should try APTonCD
it will make a copy of evey package youve installed and burn it to a cd or dvd

---

### Post by new fish on 2009-12-11
Thanks Borrot, but I think you interpret my question in different direction. I have installed ubuntu on my sister's laptop. fresh install. Meanwhile, on my laptop, I have updated and installed several additional softwares. Now, the problem is I have to move things I've added / updated on my laptop to her laptop or other computer. 
Thanks halj32, I've already got a peek on APTonCD on sourceforge (I supposed this is what you mean), and I think this is the one I look for. Anyway, I have to try it first.

---

### Post by oldos2er on 2009-12-11
If this is the same version of Ubuntu on both computers, you can copy the contents of /var/cache/apt/archives onto a flash drive and install them onto your sister's computer using gdebi or dpkg.

---

### Post by new fish on 2009-12-16
Thanks Ann, it's really clear now, if I want all the same packages/softwares installed on other computer(same architectures and same Ubuntu version), I could copy all files on /var/cache/apt/archives and installed it

Instead of installing all the same packages, I can use AptonCD, which the basically does the same procedures with copying all the files on folder I described above, but plus GUI and we can choose what packages we want to install and not to.

I understand now. Thanks all guys

---

