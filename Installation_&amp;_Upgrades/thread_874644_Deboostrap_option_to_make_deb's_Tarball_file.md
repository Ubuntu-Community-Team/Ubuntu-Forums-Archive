---
title: "Deboostrap option to make deb's Tarball file"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by LuisPT on 2008-07-30
Hello,

Yesterday I was playing around with deboostrap and in the manpage I discover the following OPTION:

**[COLOR="Navy"]--make-tarball FILE[/COLOR] **
Instead of bootstrapping, make a tarball (_[COLOR="Blue"]written to FILE[/COLOR]_) of the downloaded packages. _The resulting tarball may be passed to a later --unpack-tarball_.

I think this is fantastic, since I could just download once the instalation deb's and then make several instalations on other computers (instead of make 10 downloads I would do just one).

The problem is that when I use the "--make-tarball:" option the debootstrap returns a error: saying that an argument is necessary to the "--make-tarball" option.

I think it should be something like this:

sudo debootstrap --arch=i386 --make-tarball:/home/user/backup.tar.gz hardy /home/user/my_debootstrap

I think that with this command, debootstrap will create a tarball file with name backup.tar.gz in /home/user.

but I've tried several times and always give the same error:
--unpack-tarball needs an argument.


Can anybody help me with this? I've searched entire web and I couldn't found any good or valid example with --make-tarball option.


Thanks in advance for your help.

---

