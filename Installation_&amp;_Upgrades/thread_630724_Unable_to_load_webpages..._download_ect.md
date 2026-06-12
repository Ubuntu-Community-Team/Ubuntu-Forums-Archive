---
title: "Unable to load webpages... download ect"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by Scatterit on 2007-12-03
Ok i sent out a post i think a week ago asking for help because i thought i couldnt access the internet after installing gusty...

This was slight wrong... It detects my internet automatically, however i cannot download, access any webpages but if i test a ping its working fine...

Im using a wire to connect to my d-link router, thanks in advance...

---

### Post by twist2b on 2007-12-03
ok, you need to post your specs.... also try, 

sudo apt-get update

also try installing KDE
are you using gnome?

---

### Post by Scatterit on 2007-12-03
Im using an asus A7V600-X {SocketA(462)}, 1.5 gb ram

Dual booting with gusty and windows media centre

Fiesty Fawn installed without any rouble... i could access the internet well as soon as i turned on my pc... since i installed gusty the internet gven up on me :@ grr..

Thankyou for the reply..

---

### Post by Scatterit on 2007-12-03
A7V600-X = motherboard... if theres anything else u need ill find it...

---

### Post by s.collins8 on 2007-12-28
I'm having the same problem. I installed ubuntu 7.10 on my Dell Precision M90. I previously had 7.10 installed on my computer via the upgrade application but due to a hard disc corruption caused by windows accessing my linux partition I had to reformat the linux partition and reinstall ubuntu from a CD.

Since then I can ping internet locations such as [www.gooogle.com](www.gooogle.com), however when I open firefox I cannot download the google web page.
Note I have the same problem running the live CD also.

---

### Post by Partyboi2 on 2007-12-28
You could try turning off ipv6 in firefox, same people have had sucess with this option.
To do that in the address bar of firefox type
```
about:config
```
then in the filter field type
```
ipv6
```
then double click on
```
network.dns.disableIPv6
```
So that it now says "true"

---

### Post by s.collins8 on 2007-12-28
Cheers,

That fixed the problem.

Many Thanks and Merry Christmas

---

### Post by Scatterit on 2008-01-02
Thankyou Partyboi2 I didnt think anyone would reply to that after 2 - 4 days of that being posted...

One last things tho... yes firefox is not allowing me to view webpages however I cant connect to pidgin or connect for new updates...

Thankyou for the reply

Cheers :)

---

### Post by Partyboi2 on 2008-01-02
Are you using a router? Or proxy?

---

### Post by Scatterit on 2008-01-03
D-Link Router with a cable

---

### Post by Partyboi2 on 2008-01-03
Try
[http://ubuntuforums.org/showthread.php?t=647333&highlight=dns](http://ubuntuforums.org/showthread.php?t=647333&highlight=dns)

---

### Post by Scatterit on 2008-01-04
Sorry no this did not work :confused:

---

