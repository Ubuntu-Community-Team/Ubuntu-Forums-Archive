---
title: "Error installing SHA"
date: 2013-06-20
forum: Installation &amp; Upgrades
---

### Post by Nish123 on 2013-06-20
I'm trying to SHA using the following command
```

perl -MCPAN -e 'install Digest::SHA'
```

I also tried using:

```
sudo cpan

'install Digest::SHA'
```


But i'm getting a linker error:
```

/usr/local/bin/ld: this linker was not configured to use sysroots 
collect2: error: ld returned 1 exit status 
make: *** [blib/arch/auto/Digest/SHA/SHA.so] Error 1 
MSHELOR/Digest-SHA-5.84.tar.gz 
/usr/bin/make -- NOT OK 
Running make test 
Can't test without successful make 
Running make install 
Make had returned bad status, install seems impossible
```


Could someone please help me fix the error

---

### Post by dino99 on 2013-06-20
similar issue : [http://stackoverflow.com/questions/16432945/error-while-compiling-c-program-in-linux-mint](http://stackoverflow.com/questions/16432945/error-while-compiling-c-program-in-linux-mint)

---

