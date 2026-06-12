---
title: "Proxy authorization in ubuntu 11.04"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by huu2011 on 2011-10-30
Hello all,
Good day.
I have installed desktop ubuntu 11.04 on 64 bit.have problem downloading third part software and others.whenever I try I get below error.
I can access internet through my proxy at university but after setting in system setting.

W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/oneiric/partner/source/Sources)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources)  407  Proxy Authentication Required ( Forefront TMG requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Thank you for your help
huu

---

### Post by Paddy Landau on 2011-10-30
When you say "downloading", are you referring to using the software manager to download and install?

I see that you are using Natty 11.04, but the lines you have given us show either Oneiric (11.10) or Maverick (10.10). They should all show Natty.

If I have understood you correctly, then open Ubuntu Software Centre > Edit > Software Sources > Other Software. Look down the list and search for anything that says *oneiric* or *maverick*. Edit those lines and change to *natty*.

---

