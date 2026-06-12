---
title: "Uprading from 13.10 error message 'The method driver could not be found'"
date: 2014-07-27
forum: Installation &amp; Upgrades
---

### Post by Nir_Halfon on 2014-07-27
Hello,

I am fairly new to Ubuntu. I have been trying to upgrade to 14.04 and keep getting the following error message:

E:The method driver /usr/lib/apt/methods/htto could not be found.

Please can anyone help.

Thanks.

---

### Post by Bucky Ball on 2014-07-27
Welcome. Are you being offered the upgrade in Software Updater? How are you trying to upgrade?

PS: Right sub-forum. ;)

---

### Post by Nir_Halfon on 2014-07-27
Thanks,

Yes, The software updater window comes up and I follow the steps. Following the download of the 2 files for the release tool the error message appears when 'setting new software channels'.

Nir

---

### Post by Bucky Ball on 2014-07-27
Uh huh. Have you manually installed any third-party PPAs in your software sources? If you have, disable them and just leave the offical Ubuntu ones.

Sounds like it might be getting stuck on a PPA. Not an uncommon occurence with the upgrade.

* Incidentally, you have hit it right at the release of 14.04.1, which has been held back as there is an issue (which I don't think will affect you). The confusion there may have something to do with it, but try the suggestion I gave regarding PPAs and try again.

---

### Post by coffeecat on 2014-07-27
I think you'll find that is /usr/lib/apt/methods/http, not /usr/lib/apt/methods/htto. Have a look here:

[http://askubuntu.com/questions/165676/how-do-i-fix-a-e-the-method-driver-usr-lib-apt-methods-http-could-not-be-foun](http://askubuntu.com/questions/165676/how-do-i-fix-a-e-the-method-driver-usr-lib-apt-methods-http-could-not-be-foun)

It might be worth checking the last suggestion first - check to see that you do have the /usr/lib/apt/methods/http binary file.

---

### Post by Nir_Halfon on 2014-07-28
Thank you,

In the 'software and updates' menu, under 'other software' tab, I disabled all the packages which were 'universe' and 'multiverse'. I think it worked, the result was that there was a partial upgrade. Not sure what that means.

Coffecat- I thought that a typo might be the problem. But couldn't find how to change it. Thanks for the article. I hope everything is sorted now.

Thanks,
Nir

---

