---
title: "oneiric distr upgrade add certificate error"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by masuch on 2011-10-14
Hi,

There is some problem with adding certificates.
Should I be worried of it and how to solve it?

Part of term.log file:
  error adding /etc/ssl/certs/Comodo_Secure_Services_root.pem
  error adding /etc/ssl/certs/Comodo_Trusted_Services_root.pem
  error adding /etc/ssl/certs/DST_ACES_CA_X6.pem
  error adding /etc/ssl/certs/DST_Root_CA_X3.pem
  error adding /etc/ssl/certs/DigiCert_Assured_ID_Root_CA.pem
  error adding /etc/ssl/certs/DigiCert_Global_Root_CA.pem
  error adding /etc/ssl/certs/DigiCert_High_Assurance_EV_Root_CA.pem
  error adding /etc/ssl/certs/Digital_Signature_Trust_Co._Global_CA_1.pem
  error adding /etc/ssl/certs/Digital_Signature_Trust_Co._Global_CA_3.pem

thanks,
m.

---

### Post by Mister X on 2011-10-14
same error here

---

### Post by chillywillyhoe on 2011-10-14
same for me also

---

### Post by trundlenut on 2011-10-14
I noticed this too, doesn't seem to have caused any issues yet though.

---

### Post by schlameel on 2011-10-14
It looks like someone has filed a [bug report]("https://bugs.launchpad.net/bugs/873517"), but there is no response yet.

I got the same error, BTW.

---

### Post by zhogan85 on 2011-10-15
I'm getting the same errors during install too, hmm....

---

### Post by soyatti on 2011-10-16
same here

---

### Post by leonsmith on 2011-10-16
Same errors. Any resolutions yet ?

---

### Post by scpatl4now on 2011-10-16
+1   same errors

---

### Post by ruppgeoff on 2011-10-16
Same errors here...

---

### Post by Fir3chi3f on 2011-10-16
Same error, but has anyone noticed a problem afterward? I'm still upgrading.

---

### Post by zhogan85 on 2011-10-17
> **Fir3chi3f said:**
> Same error, but has anyone noticed a problem afterward? I'm still upgrading.

No, I've not noticed any issues as of yet, so it may be no problem after all, just a little disconcerting when you're a couple hours into the install and see so many errors popping up. I'd be curious though, if one of the many Ubuntu gurus around here were able to offer any insight into what these errors mean.

---

### Post by Tanker Bob on 2011-10-17
Same errors here. It looks like the error that one gets with duplicate certificates. I haven't had any issues since upgrading, so I'm inclined to believe that the "new" certificates were actually duplicates for those already installed. Could be wrong, though.

---

### Post by crgutierrez on 2011-10-17
same error.........:(

---

### Post by scpatl4now on 2011-10-17
> **Fir3chi3f said:**
> Same error, but has anyone noticed a problem afterward? I'm still upgrading.

It seems I have had a problem.  HP keeps trying to download software for my printer and it errors out saying I dont have a valid certificate

---

### Post by masuch on 2011-10-18
Hi,

I hope this should help:
sudo apt-get install ca-certificates-java

---

### Post by Quincy5 on 2011-10-20
I also have the same errors. Still upgrading and a bit worried, but I will keep masuch's suggestion in mind if any issues pop up.

---

### Post by Jaybyrrd on 2011-10-23
Same error here as well, but Eric Larson seems to have given what may be the best fix (I am waiting for the upgrade to complete and then I am following his instructions)

> 
The fix for me seemed to be reconfiguring and re-adding all the certs. I made a mistake and removed them all first and then added them back, so I'm not sure if the removal then addition is what fixed the issue.

When I say "reconfigure" I do mean running: dpkg-reconfigure ca-certificates and selecting all the certs in the dialog that comes up.


So gonna try it in approximately 22 minutes.

---

### Post by Tanker Bob on 2011-10-23
The reconfigure seems to have worked here. Thanks!

---

### Post by masuch on 2011-10-28
This could be useful as well (some of that has been already mentioned in previous replies) :
[https://help.ubuntu.com/community/OpenSSL#SSL%20Certificates](https://help.ubuntu.com/community/OpenSSL#SSL%20Certificates)
[http://packages.ubuntu.com/oneiric/ca-certificates](http://packages.ubuntu.com/oneiric/ca-certificates)

---

### Post by helpee on 2012-04-13
I'm Glad that stuff wouldn't download!

Why does everyone and their mother want me to automatically trust their ssl certificates by default in the first place? What if I don't Want to trust whoever makes "Japanese_Government.pem"? 

Come on, Ubuntu, you're better than that.

---

### Post by raja.genupula on 2012-04-13
hey may i help you ?

---

