---
title: "can't install adobe reader in ubuntu"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by clapton on 2010-03-31
Hello people.
I'm trying install adobe reader without success.

I have all repositories uncommented at my sources.lst, but acroread doesn't appear.
I try use ubuntu center, I choose to install, and next nothing happens.

Any ideas?

---

### Post by 2hot6ft2 on 2010-03-31
Document viewer should open pdf's anyway but. you could try
```
sudo apt-get update
```
```
sudo apt-get install acroread
```
I don't know why it wouldn't show up.
Maybe try another server in synaptic

---

### Post by s.fox on 2010-03-31
Hello,

Try downloading the .deb from [here]("http://get.adobe.com/uk/reader/otherversions/").  Choose: Linux – x86 (.deb)

-Silver Fox

---

### Post by aysiu on 2010-03-31
You have to enable the Medibuntu repositories to get it to show up Synaptic:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by 2hot6ft2 on 2010-03-31
Ah, adobe is a restricted format since adobe is closed source so the medibuntu probably needs to be enabled since that's where it's fonts package is
This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install acroread
```

---

### Post by clapton on 2010-03-31
> **2hot6ft2 said:**
> Document viewer should open pdf's anyway but. you could try
```
sudo apt-get update
```
```
sudo apt-get install acroread
```
I don't know why it wouldn't show up.
Maybe try another server in synaptic

I already tried. Don't find this package.

---

### Post by aysiu on 2010-03-31
> **clapton said:**
> I already tried. Don't find this package.
That's because you have to add the Medibuntu repositories. See my earlier post.

---

### Post by clapton on 2010-04-01
> **aysiu said:**
> That's because you have to add the Medibuntu repositories. See my earlier post.

Don't work.
I'm a ubuntu 10.04 user... I think this is the problem.

---

### Post by jstnmarsh on 2010-04-01
Different versions of Ubuntu requires a little different sources to set up. I suggest you to wait for sometime and then try installing it again. I have heard of some problem that prevents the proper installation of Adobe Reader, I would prefer to wait for sometime until the proper updates are available.

---

### Post by clapton on 2010-04-01
> **jstnmarsh said:**
> Different versions of Ubuntu requires a little different sources to set up. I suggest you to wait for sometime and then try installing it again. I have heard of some problem that prevents the proper installation of Adobe Reader, I would prefer to wait for sometime until the proper updates are available.

I think that is the best away...
I'm writing a thesis in LaTeX with some features at pdf, Adobe feets better.
I can't find KPDF at repositories too...

---

### Post by aysiu on 2010-04-01
> **clapton said:**
> Don't work.
I'm a ubuntu 10.04 user... I think this is the problem.
I've moved your thread then.

By the way, it does work. I'm using 10.04 also. The Medibuntu for that is *lucid* (not *karmic* or *jaunty*).

---

### Post by clapton on 2010-04-02
> **aysiu said:**
> I've moved your thread then.

By the way, it does work. I'm using 10.04 also. The Medibuntu for that is *lucid* (not *karmic* or *jaunty*).

Hmm, with didn't work.
I'm 64 bits user. Is this a bug?

---

### Post by knarf on 2010-04-02
> **clapton said:**
> Hello people.
I'm trying install adobe reader without success.

I have all repositories uncommented at my sources.lst, but acroread doesn't appear.
I try use ubuntu center, I choose to install, and next nothing happens.

Any ideas?

That's a feature, not a bug.

---

### Post by zenarcher on 2010-04-02
I'm also a 64 bit user and I don't think Acroreader is available yet for Lucid, or at least I've not been able to locate it.  And, I do have Medibuntu enabled.  There is a file for Acroreader fonts available, but no 64 bit package for Acroreader.

Cheers,
zenarcher

---

### Post by clapton on 2010-04-02
> **zenarcher said:**
> I'm also a 64 bit user and I don't think Acroreader is available yet for Lucid, or at least I've not been able to locate it.  And, I do have Medibuntu enabled.  There is a file for Acroreader fonts available, but no 64 bit package for Acroreader.

Cheers,
zenarcher

Exactly the same. I don't need the fonts without reader.

---

### Post by Bluesan on 2010-04-02
> **clapton said:**
> Hello people.
I'm trying install adobe reader without success.

I have all repositories uncommented at my sources.lst, but acroread doesn't appear.
I try use ubuntu center, I choose to install, and next nothing happens.

**Any ideas?**

Confirming your problem...

64 bit here too. Acroread is installed on my 32 bit machine at the office, but it's no where to be found on my 64 bit box here at home (both running Lucid). I'm assuming it'll show up prior to the final...

---

### Post by aysiu on 2010-04-02
Someone filed a bug report on it:
[https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/532077](https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/532077)

---

