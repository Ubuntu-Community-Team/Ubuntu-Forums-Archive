---
title: "acroread installation"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by infestor on 2010-03-22
i use lucid x64 and i have enabled lucid-partner repos but cannot find the package acroread. any ideas?

---

### Post by collinp on 2010-03-22
I *think* it would be listed in this search result, and from it's results, acroread is only in Dapper's repos:
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=acroread](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=acroread)

Correct me if I'm wrong.

---

### Post by ajgreeny on 2010-03-22
Just out of interest, do you specifically need acroread?  I have not used it at all in ubuntu and have never missed it at all.

---

### Post by MacUntu on 2010-03-22
IMHO PDFs look much better with Adobe Reader than with Evince.

---

### Post by infestor on 2010-03-22
> **MacUntu said:**
> IMHO PDFs look much better with Adobe Reader than with Evince.
^this and in some pdfs i cannot click on the links with evince or okular or xpdf.

---

### Post by ronacc on 2010-03-22
you can get it straight from adobe [http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/) . Several features especialy in pdf's made with later versions of acrobat don't work or work right in Evince .

---

### Post by wilee-nilee on 2010-03-22
Canonical was the repo for it do you have that ticked on in software sources. It is in my synaptic but I have medibuntu added which is where I think acroread was before.

---

### Post by coffeecat on 2010-03-22
Acroread was in Medibuntu 2-3 releases ago, but moved to the Partner repository somewhere around the Jaunty-Karmic time. I certainly installed Acroread from the Partner repo in Karmic. I seem to remember it didn't appear in the repository until a little after Karmic went final, so the same may be true with Lucid. A matter of being patient, I suspect.

---

### Post by ronacc on 2010-03-22
You can go here to search for ppa's [ https://launchpad.net/ubuntu/+ppas ]( https://launchpad.net/ubuntu/+ppas )  enter acroread in the search box and it will return any ppa that has acroread files in it . IIRC this is the one I used [ https://launchpad.net/~portis25/+archive/ppa?field.series_filter=lucid ]( https://launchpad.net/~portis25/+archive/ppa?field.series_filter=lucid ) .

---

### Post by nanog on 2010-03-22
Its in the canonical partner repos. Those repos only go live on release but the karmic version works fine.

Other reason to use acrobat reader: 

1) snapshot tool (essential in an enterprise setting).

2) cut and paste of columnar text.

3) evince often cannot open large (100 meg+ size) pdfs.

4) far better font handling. 

5) hyperlinks and menu structures work.

6) complex forms work.


i could go on...

---

### Post by nanog on 2010-03-22
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

---

### Post by wilee-nilee on 2010-03-22
It's
[ATTACH]151112[/ATTACH]

---

### Post by philinux on 2010-03-23
> **infestor said:**
> i use lucid x64 and i have enabled lucid-partner repos but cannot find the package acroread. any ideas?

Just edit your sources and change lucid to karmic for the partner repo.

It's always like this. The partner repo doesn't seem to get packages until release date.

---

### Post by infestor on 2010-03-23
> **ronacc said:**
> You can go here to search for ppa's [ https://launchpad.net/ubuntu/+ppas ]( https://launchpad.net/ubuntu/+ppas )  enter acroread in the search box and it will return any ppa that has acroread files in it . IIRC this is the one I used [ https://launchpad.net/~portis25/+archive/ppa?field.series_filter=lucid ]( https://launchpad.net/~portis25/+archive/ppa?field.series_filter=lucid ) .

i guess that ppa would do instead of using karmic's repos or etc.. nice and easy :) thanks

---

