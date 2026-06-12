---
title: "Auto install with subiquity"
date: 2018-05-01
forum: Installation &amp; Upgrades
---

### Post by dominicl on 2018-05-01
I'm trying to auto install the 18.04 server iso image.  The new 18.04 comes with subiquity and it seems the kickstart and preseed is no longer working. ie. Setting the boot option preseed/url=http://... or ks=http://.... which used to work on 16.04 is no longer working, and the subiquity still showing up and ask for manual input.

I tried to look up the documentation, but the latest LTS (which refers as 18.04 now) doesn't mention anything about how to set the subiquity file in the boot option, and still referring the preseed / kickstart way of doing thing, it seems to be identical to the old 16.04 page:
[https://help.ubuntu.com/lts/installation-guide/amd64/ch05s03.html](https://help.ubuntu.com/lts/installation-guide/amd64/ch05s03.html)

Also, I'm not sure about the new file format to set into the subiquity?  It seems to be something like this?
[https://github.com/CanonicalLtd/subiquity/blob/master/examples/answers.yaml](https://github.com/CanonicalLtd/subiquity/blob/master/examples/answers.yaml)

---

### Post by dominicl on 2018-05-01
Answering my own question, it seems we have to use the [ubuntu-18.04-server-amd64.iso]("http://cdimage.ubuntu.com/ubuntu/releases/18.04/release/ubuntu-18.04-server-amd64.iso") from [http://cdimage.ubuntu.com/ubuntu/releases/18.04/release/](http://cdimage.ubuntu.com/ubuntu/releases/18.04/release/) instead of [ubuntu-18.04-live-server-amd64.iso]("http://releases.ubuntu.com/18.04/ubuntu-18.04-live-server-amd64.iso") from [http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/).  The cdimage link has the image that still has the old debian-installer instead of the subiquity.
[COLOR=#000000][/COLOR]

---

### Post by zhb on 2018-05-02
There is a answer file about the installer questions  , which can control the process of installation 
the postion is 
/subiquity_config/answers.yaml

you can download the example  file  of answers.yaml  at  here :  

[https://github.com/CanonicalLtd/subiquity/blob/master/examples/answers.yaml](https://github.com/CanonicalLtd/subiquity/blob/master/examples/answers.yaml)

but how to add the file anwers.yaml  to the postion /subiquity_config/ ,  I also don't know . does  anyone know it ?

---

### Post by wildmanne39 on 2018-05-02
Hello and welcome to the forum, if you need support please start your own thread instead of asking for help in someone else's thread.

Thanks

---

### Post by zhb on 2018-05-03
[COLOR=#000000]you can download the example file of answers.yaml at here : [/COLOR]

[https://github.com/CanonicalLtd/subiquity/blob/master/examples/answers.yaml](https://github.com/CanonicalLtd/subiquity/blob/master/examples/answers.yaml)

(1) you can unsquash  the file   casper/filesystem.squashfs  in the  ubuntu-18.04-live-server-amd64.iso  , and get the folder  " squashfs-root",   then mkdir subiquity_config in the folder  of squashfs-root

(2) copy the answers.yaml   into the  squashfs-root/subiquity_config/

(3) repacking the folder  squashfs-root  into   filesystem.squashfs by using mksquashfs command  , and repacking the  ubuntu-18.04-live-server-amd64.iso by using genisoimage command

---

### Post by codejamninja on 2018-05-22
How would you add ubiquity/success_command with subiquity?

---

### Post by q2dg on 2018-10-18
Why this information isn't available in official README??

On the other hand, I second codejamninja question: if there's no ubiquity/success_command equivalent in subiquity the usefulness of doing an unattended installation is very low because, after grabbing right repositories, desktop systems can't be installed with it.

---

### Post by lizaoreo2 on 2019-02-05
> **zhb said:**
> [COLOR=#000000]you can download the example file of answers.yaml at here : [/COLOR]

[https://github.com/CanonicalLtd/subiquity/blob/master/examples/answers.yaml](https://github.com/CanonicalLtd/subiquity/blob/master/examples/answers.yaml)

(1) you can unsquash  the file   casper/filesystem.squashfs  in the  ubuntu-18.04-live-server-amd64.iso  , and get the folder  " squashfs-root",   then mkdir subiquity_config in the folder  of squashfs-root

(2) copy the answers.yaml   into the  squashfs-root/subiquity_config/

(3) repacking the folder  squashfs-root  into   filesystem.squashfs by using mksquashfs command  , and repacking the  ubuntu-18.04-live-server-amd64.iso by using genisoimage command

Does the answers.yaml replace the need for editing txt.cfg, grub.cfg, and creating the preseed files?  Or is it used inline with those things?

---

