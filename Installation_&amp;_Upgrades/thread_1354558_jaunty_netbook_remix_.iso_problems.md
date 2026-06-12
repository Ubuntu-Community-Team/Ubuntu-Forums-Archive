---
title: "jaunty netbook remix .iso problems"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by thumpszilla on 2009-12-14
I have been trying to get an iso of jaunty netbook remix so I can install to usb flash drive. My wife really wants to try it on her Dell mini 9 before she commits to it. I downloaded the .img from [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/) and tried several tutorials using several differnt programs to make the .iso but it always fails because of errors. I am trying to convert this on a system with jaunty xubuntu jaunt desktop. Is there anywhere I can just download the .iso form of this? 

As always thanks for any help you can give.

---

### Post by mikewhatever on 2009-12-14
Jaunty had UNR packaged as .img and I don't think there is an iso available. Regardless, you should be able to write to a usb with usb-imagewriter from Jaunty's repositories. If you want it as .iso, get Karmic instead of Jaunty.

---

### Post by thumpszilla on 2009-12-14
yes I tried image writer but it would not read the .img files I always got errors and it will not complete.

---

### Post by benjaminsuman on 2009-12-14
Have you tried the Karmic UNR release?

---

### Post by snowpine on 2009-12-14
If I understand correctly that Xubuntu Jaunty is already installed, all you need to do is follow the tutorial in the link below, but change the very last part of the line from "sudo apt-get install ubuntu-desktop" to "sudo apt-get install ubuntu-netbook-remix"

[http://www.psychocats.net/ubuntu/puregnomejaunty](http://www.psychocats.net/ubuntu/puregnomejaunty)

---

### Post by thumpszilla on 2009-12-14
> **benjaminsuman said:**
> Have you tried the Karmic UNR release?
 No I do not want karmic on it. 


> If I understand correctly that Xubuntu Jaunty is already installed, all you need to do is follow the tutorial in the link below, but change the very last part of the line from "sudo apt-get install ubuntu-desktop" to "sudo apt-get install ubuntu-netbook-remix"

[http://www.psychocats.net/ubuntu/puregnomejaunty](http://www.psychocats.net/ubuntu/puregnomejaunty)[]("http://www.psychocats.net/ubuntu/puregnomejaunty")
No currently the netbook has xp. I want to install jaunty netbook remix to an external drive or usb flash drive. I guess I will try your method though.

---

### Post by snowpine on 2009-12-15
> **thumpszilla said:**
> 
No currently the netbook has xp. I want to install jaunty netbook remix to an external drive or usb flash drive. I guess I will try your method though.

I misunderstood your comment "I am trying to convert this on a system with jaunty xubuntu jaunt desktop."

In that case, I suggest following the official instructions from the ubuntu wiki: [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

If that doesn't work, please be more specific than "it always fails because of errors"; i.e. copy and paste the actual errors here so people can help you. :)

---

### Post by thumpszilla on 2009-12-17
Well I downloaded the image writer tool for windows popped that and the netbook remix.img on a flash drive and installed to the flash drive off a windows pc. Worked like a charm and the wife has now went full linux and loving it. Thanks for all the help.

---

