---
title: "CLN library installation"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by foxninja on 2008-04-11
I need to generate some statistics for my course assignments and I came across this C++ library:

[http://www.ginac.de/CLN/](http://www.ginac.de/CLN/)

After installation I can compile my source code but they don't run.  I get the error message

 "Error while loading shared libraries: libcln.so.5: cannot open shared object file: No such file or directory"

Any idea what I might have done wrong for the installation? I'm stumped, spent 2+ hours trying to see what's wrong...

---

### Post by WW on 2008-04-11
How did you install CLN?  With the Ubuntu package (it is in the repositories) or from source?

What command did you use to compile your program (or are you using an IDE that has a "compile" or "build" button)?

I installed CLN using the Ubuntu package.  Here's a sample program, along with how to compile and run it from the command line.

**clntest.cpp**
[php]
#include <iostream>
#include <cln/cln.h>

using namespace std;
using namespace cln;

int main(int argc, char *argv[])
    {
    cl_F e = "0.271828182845904523536028747135266249775724709369996e+1_40";
    cout << "e   = " << e << endl;
    cout << "e^2 = " << e*e << endl;
    return 0;
    }
[/php]

Compile and run:
> 
$ g++ clntest.cpp `pkg-config --cflags --libs cln` -o clntest
$ ./clntest
e   = 2.71828182845904523536028747135266249775724709369996L0
e^2 = 7.389056098930650227230427460575007813180315570551849634807L0
$ cat clntest.cpp

I used pkg-config to get the correct options to compile and link the program.

---

### Post by foxninja on 2008-04-11
I installed it through downloading the tar from the main site.  

I followed the steps of running: 
configure
make 
make check
make install

I tried to compile the program like the cmd line above.


no luck =(

---

### Post by WW on 2008-04-11
If the **configure** and **make** commands succeeded, then **make install** would have tried to install the library in **/usr/local**.  Unless you used **sudo make install**, or ran the command as root some other way, **make install** would have failed.

Assuming you actually did complete the installation, you can get the command that I gave to work by first doing this:
```

$ export PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig

```
This tells the pkg-config command to also look in /usr/local/lib/pkgconfig for library configuration files.

If **configure** or **make** failed, you'll have to figure out why.


Having said all that, I should ask why you don't just use the Ubuntu package.  Run this command
> 
$ sudo apt-get install libcln4 libcln-dev

(or use, say, Synaptic Package Manager to install libcln4 and libcln-dev) and you are good to go.

---

### Post by foxninja on 2008-04-11
WW:

Everything makes sense now, I installed one of the libraries, not both through the repository.  That's why I d/l the tar in the first place.  

Thank you for your help.

---

