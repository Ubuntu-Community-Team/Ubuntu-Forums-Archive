---
title: "Are the Hardy repositories completely busy?"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by negora on 2008-05-11
Hi there:

My network configuration is ok. I can download as fast as my line is able. However, this story changes when it's about downloading something from any Ubuntu repository.

If I try to update the list or download anything, via apt-get, aptitude or adept manager, the downloads get cut and resumed every time, repeatly. It take ages to do a simple update of the packages list.

I've tryed different mirros: From my country, from the States, from Qatar... And the result is the same. I never got this problem with Edgy, Feisty or Gutsy. I've tested all this with clean installations of these distributions:

Ubuntu v. 8.04
Ubuntu v. 8.04 (64 bits)
Kubuntu v. 8.04 (64 bits)
Kubuntu v. 8.04 KDE Remix
Kubuntu v. 8.04 KDE Remix (64 bits)

But nothing changes. Is it a general issue? Thank you.

---

### Post by inportb on 2008-05-11
Yeah, I'm seeing a similar effect. It might be the busy servers.

---

### Post by negora on 2008-05-12
Thanks for answering :D . However, there're two matters about this issue which I can't understand:

1 - Why do this only affects to apt-get or any application which use it in its background? I've tryed to access the same repositories with Mozilla Firefox and donwload content by hand and everything is fine :S .

2 - If they were busy, Shouldn't we ALL suffer the same problem?

Thanks again ;) .

---

### Post by negora on 2008-05-12
Well, I've came to the conclusion of this problem... At least as long as there're FTP repositories.

First of all, I must state that "apt-get" never gave me any error. The download speed   fall to 0 KB/seg and, after minutes waiting, it resumed again... Until the next stop.

Editing the "sources.list" file, I've remembered that using Dapper, Feisty and Gutsy, I always used FTP servers instead of HTTP ones. Indeed, Synaptic and Adept Manager allowed that. But in the version v. 8.04 both of them forced it to be HTTP always. I've decided to test something: Replacing every line by the FTP server which I always used (ftp.udc.es). And that worked!

So, if with older versions never failed to me, it was because that change to FTP.

Could a transparent proxy-cache cause this? My ISP has one put and it's a pain in the ***. It has caused me many head aches. However, Why do Firefox download from the same repositories properly? Is there something in the apt-get internal behaviour which could conflict with a proxy-cache? Maybe the PGP checking?

I'm not sure if the mentioned proxy-cache is guilty in this case, but it's obvious that  it has something to do with the HTTP petitions and the mecanism used by this app.

Please, if someone has an opinion about this, I'm pleased to hear. Thank you very much.

---

### Post by inportb on 2008-05-12
Well, I usually have my local mirror on my sources.list, so it's usually pretty fast. It also means packages are sometimes delayed, but I can live with that.

---

### Post by negora on 2008-05-12
**inportdb:** I know that maybe you're busy but, Could you check if using a "sources.list" like the one below works for you?:


deb [ftp://ftp.udc.es/ubuntu/](ftp://ftp.udc.es/ubuntu/) hardy main restricted universe multiverse
deb-src [ftp://ftp.udc.es/ubuntu/](ftp://ftp.udc.es/ubuntu/) hardy main restricted universe multiverse

deb [ftp://ftp.udc.es/ubuntu/](ftp://ftp.udc.es/ubuntu/) hardy-updates main restricted universe multiverse
deb-src [ftp://ftp.udc.es/ubuntu/](ftp://ftp.udc.es/ubuntu/) hardy-updates main restricted universe multiverse

deb [ftp://ftp.udc.es/ubuntu/](ftp://ftp.udc.es/ubuntu/) hardy-security main restricted universe multiverse
deb-src [ftp://ftp.udc.es/ubuntu/](ftp://ftp.udc.es/ubuntu/) hardy-security main restricted universe multiverse

deb [ftp://ftp.udc.es/ubuntu/](ftp://ftp.udc.es/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [ftp://ftp.udc.es/ubuntu/](ftp://ftp.udc.es/ubuntu/) hardy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner


Thank you.

PD: List edited.

---

