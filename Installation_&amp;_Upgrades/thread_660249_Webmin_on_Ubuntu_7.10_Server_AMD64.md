---
title: "Webmin on Ubuntu 7.10 Server AMD64"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by westsyde on 2008-01-06
Trying to install on Ubuntu 7.10 server AMD64 editiion:

If I do an apt-get install webmin the error is:

webmin: depends: libnet-ssleay-perl but it is not available


I tied apt-get install libnet-ssleay-perl

but says libnet-ssleay-perl has no installation candidate?

Is it in some other installation?


Sorry in advance for the noobness - trying to wean myself off of Winblows server today

---

### Post by stalker145 on 2008-01-07
> **westsyde said:**
> Trying to install on Ubuntu 7.10 server AMD64 editiion:

If I do an apt-get install webmin the error is:

webmin: depends: libnet-ssleay-perl but it is not available


I tied apt-get install libnet-ssleay-perl

but says libnet-ssleay-perl has no installation candidate?

Is it in some other installation?


Sorry in advance for the noobness - trying to wean myself off of Winblows server today

I know it's not the best answer (since I, too prefer the repositories) but have you tried getting the install files (either deb or source) from the [WebMin site]("http://www.webmin.com/")?

---

### Post by westsyde on 2008-01-07
thats the other thing - if I try to do the command 'wget' and the [http://,](http://,) I get the error:

wget command not found

is there a way to install that command? or is there another command that I should be using to try to 'get'?

---

### Post by stalker145 on 2008-01-08
> **westsyde said:**
> thats the other thing - if I try to do the command 'wget' and the [http://,](http://,) I get the error:

wget command not found

is there a way to install that command? or is there another command that I should be using to try to 'get'?

How bizarre... OK, so for wget, you are using the format```
wget http://www.some-random-site.blah/file-I-want.whatever
```and it is erroring out with > wget command not found??

If so, try ```
sudo aptitude reinstall wget
```in the terminal and see if that fixes things.

---

