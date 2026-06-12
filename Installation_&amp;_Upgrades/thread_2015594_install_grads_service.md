---
title: "install grads service"
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by xolio on 2012-07-03
Hello,

I have a webserver which is running linux ubuntu 8.04.4.
I would like to install the grads service on my server but I have no idea how to.
By searching on google I found answers like "sudo apt-get install grads" but it tells me the package cant be found. After some time I decided I better ask here before I do something wrong.

I am talking about this: [http://www.iges.org/grads/downloads.html](http://www.iges.org/grads/downloads.html)

Actually I wanna work with openGrads PHP ([http://opengrads.org/wiki/index.php?title=PHP_Interface_to_GrADS](http://opengrads.org/wiki/index.php?title=PHP_Interface_to_GrADS)).
I have a lot of experience with php, but barely experience with ubuntu server stuff.

Maybe someone could help me doing the first step. That would be great, I really would appreciate it! :)

thanks in advance, Alex

---

### Post by gordintoronto on 2012-07-03
The version of Ubuntu you are using is quite old. grads is in the repositories for Ubuntu 12.04, and perhaps some earlier versions. Oh, it's probably in the "partner" repository, which is not enabled by default. It's possible you can install it by adding:
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) hardy partner

to your sources list, following the instructions here:
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by xolio on 2012-07-04
Hi,

thanks for your response.

I added this to my sources list successfully.
But now I still dont know how i can install grads?

Maybe I have to install it in some manually way or wont it work with my unbuntu version?

---

### Post by coffeecat on 2012-07-04
According to [noparse]packages.ubuntu.com[/noparse], grads is in the Universe repository but is only available for 10.04 and later:

[http://packages.ubuntu.com/search?keywords=grads&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=grads&searchon=names&suite=all&section=all)

So it looks as though you won't find a repo version of grads for 8.04. 

I'm sorry I can't help further with grads for 8.04, but a thought for you. 8.04 on the server has less than a year's support left so you will need to think about upgrading to 10.04 or 12.04 within the year anyway. At least if you upgrade you will be able to install a repo version of grads.

---

### Post by xolio on 2012-07-05
well, I updated to 10.04 and that helped. now the apt-get thing worked.

Thanks a lot! :)

---

