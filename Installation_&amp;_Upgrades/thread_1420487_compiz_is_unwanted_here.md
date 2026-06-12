---
title: "compiz is unwanted here"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by rgrig on 2010-03-03
I do not want compiz. After every upgrade I have to uninstall it. Is there a way to not have it 'upgraded' in the first place?

Is there a way to find out what *new* packages an upgrade will install?

---

### Post by yogesh.girikumar on 2010-03-03
Hi,


       You can do that in two different ways.


       One way is to lock a particular version using synaptic.
       
[LIST=1]
[*]Go-to synaptic package manager System -> Administration -> Synaptic Package Manager.
[*]Uninstall the compiz package.
[*]Click on the package and lock the version by Clicking on the "Package" menu and checking the checkbox for "Lock Version"
[/LIST]
       Another way of doing this is by using the wajig package.

[LIST=1]
[*]   Install wajig ```
$ sudo apt-get install wajig
```
[*]Uninstall the specific package. In your case, compiz. ```
$ sudo apt-get remove compiz
```
[*]Then you can use wajig to 'hold' the package.```
$ sudo wajig hold <package>
```
[/LIST]

To unhold a package, do:
```
$ sudo wajig unhold <package>
```      Also See: [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin)
[URL="http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin"]
[/URL]
       Hope this helps.

---

### Post by mikewhatever on 2010-03-03
> **rgrig said:**
> I do not want compiz. After every upgrade I have to uninstall it. Is there a way to not have it 'upgraded' in the first place?

Is there a way to find out what *new* packages an upgrade will install?

Well, don't use it then. Even if installed, you don't have to use it or worry about it being upgraded.

---

### Post by yogesh.girikumar on 2010-03-03
Hi,
To add to my earlier post: 

Add these following lines to your /etc/apt/preferences file.

Setting a negative pin priority will prevent the package from ever being installed. So you can do that for every release of ubuntu. Now I am assuming you are on a hardy installation,

   So doing:
```
Package: compiz
Pin: release a=hardy
Pin Priority: -21

Package: compiz
Pin: release a=intrepid
Pin Priority: -22

Package: compiz
Pin: release a=jaunty
Pin Priority: -23

Package: compiz
Pin: release a=karmic
Pin Priority: -24
```      Should prevent any version of compiz ( hardy - karmic ) from getting installed. 

    Also see: [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

HTH[URL="https://help.ubuntu.com/community/PinningHowto"]
[/URL]

---

### Post by rgrig on 2010-03-03
Thanks Yogesh, especially for the link. That's exactly what I wanted to know.

---

