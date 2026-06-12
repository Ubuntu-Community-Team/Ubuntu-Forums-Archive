---
title: "Make error while installing MCScanX"
date: 2014-02-12
forum: Installation &amp; Upgrades
---

### Post by prasanth_tej_kumar on 2014-02-12
i am unable to install a software 

when i give command make

i am getting the following error message

" msa.cc: In function ‘void msa_main(const char*)’:
msa.cc:289:22: error: ‘chdir’ was not declared in this scope
     if (chdir(html_fn)<0)
                      ^
make: *** [mcscanx] Error 1" 

please tell me a solution

---

### Post by bc.haynes on 2014-02-12
Are you trying to install a program or are you trying to compile (make) one?

What are you trying to install?

What distro are you using (Ubuntu, Xubuntu, Lubuntu, etc.)?

---

### Post by prasanth_tej_kumar on 2014-02-13
i am trying to install a program and i am using ubuntu 

i am tring to install MCScanX

---

### Post by vasa1 on 2014-02-13
Did you see this: [https://github.com/wyp1125/MCScanx](https://github.com/wyp1125/MCScanx) ? What did you do **before** running "make"? You should really give people more information so that they can help you.

---

### Post by prasanth_tej_kumar on 2014-02-14
my comupter is sony E series intel core i3-2310M processor 2.10GHz
64-bit
8GB RAM 320GB HARD DISK
ROOT FILE IN 5GB
SWAP FILE IN 2GB
this is want i have done before doing make
$unzip MCscanx.zip
$cd MCScanx
$make

once i enter after make i get the following response

[B]prasanth@prasanth-VPCEH16EN:~/src/MCScanX$ make
g++ struct.cc mcscan.cc read_data.cc out_utils.cc dagchainer.cc msa.cc permutation.cc -o MCScanX
msa.cc: In function &#8216;void msa_main(const char*)&#8217;:
msa.cc:289:22: error: &#8216;chdir&#8217; was not declared in this scope
     if (chdir(html_fn)<0)
                      ^
make: *** [mcscanx] Error 1[/B]
prasanth@prasanth-VPCEH16EN:~/src/MCScanX$

---

### Post by steeldriver on 2014-02-14
If you are building on 64-bit you may need to add

```
#include <unistd.h>
```

to msa.h, dissect_multiple_alignment.h, and detect_collinear_tandem_arrays.h

---

### Post by prasanth_tej_kumar on 2014-02-14
thank you so much 

but where can i get the unistd.h file?

---

### Post by steeldriver on 2014-02-14
The unistd.h file is a system header file - it should have been installed as part of the libc6-dev package (which in turn is a dependency of the build-essential metapackage). All you need to do is add the include directive that I indicated in my previous post to each of the indicated header files e.g. in msa.h

```

#include <iostream>
#include <fstream>
#include <sys/stat.h>
[B]#include <unistd.h>
[/B]
#include "struct.h"

struct New_endpoint
{
    Gene_feat *n;

```

---

### Post by prasanth_tej_kumar on 2014-02-15
thank you so much now i have overcame error1

---

