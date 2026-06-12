---
title: "autoconf 2.53?"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by katanabob on 2007-05-20
Hello!

 In following the example of [http://baghira.sourceforge.net/OS_Clone-en.php](http://baghira.sourceforge.net/OS_Clone-en.php) , I have encountered a problem when compiling/installing baghira. This is what I get:

```
cpearson@goose-laptop:~/baghira$ make -f Makefile.cvs
This Makefile is only for the CVS repository
This will be deleted before making the distribution

./admin/cvs.sh: line 33: --version: command not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
cpearson@goose-laptop:~/baghira$
```

I already installed autoconf with
```

cpearson@goose-laptop:~/baghira$ sudo apt-get install autoconf
```

but despite acquiring it, I still get the same error output when trying to make baghira. 

I thank you in advance for any suggestions. Thank you!

---

### Post by katanabob on 2007-05-20
Alright, I figured this one out shortly after posting. For those interested...

It wasn't actually autoconf that was missing. (despite the message...) it was automake. By acquiring the necessary automake... it all worked.

---

