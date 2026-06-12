---
title: "GNU compiler cant load a new c++ header file"
date: 2013-04-19
forum: Installation &amp; Upgrades
---

### Post by gravit123 on 2013-04-19
hi there,

im trying to using a new header file [COLOR=#0000ff]*<random>*[/COLOR] from C++ Standard Library. I simply copy-paste the following example on [http://www.cplusplus.com/reference/random/bernoulli_distribution/](http://www.cplusplus.com/reference/random/bernoulli_distribution/)


```


// bernoulli_distribution 
#include <iostream> 
#include <random> 
 int main() {  
 const int nrolls=10000;   
 std::default_random_engine generator;   
std::bernoulli_distribution distribution(0.5);   
 int count=0;  // count number of trues   
 for (int i=0; i<nrolls; ++i) if (distribution(generator)) ++count;   
 std::cout << "bernoulli_distribution (0.5) x 10000:" << std::endl;   
std::cout << "true:  " << count << std::endl;  
 std::cout << "false: " << nrolls-count << std::endl;   
return 0; 
}

```

Then I got the following errors after execution of the file "test.cpp" containing the code above:
```

g++ test.cpp
In file included from /usr/include/c++/4.4/random:35,
                 from test.c:3:
/usr/include/c++/4.4/c++0x_warning.h:31:2: error: #error This file requires compiler and library support for the upcoming ISO C++ standard, C++0x. 
This support is currently experimental, and must be enabled with the -std=c++0x or -std=gnu++0x compiler options.
test.cpp: In function ‘int main()’:
test.cpp:9: error: ‘default_random_engine’ is not a member of ‘std’
test.cpp:9: error: expected ‘;’ before ‘generator’
test.cpp:10: error: ‘bernoulli_distribution’ is not a member of ‘std’
test.cpp:10: error: expected ‘;’ before ‘distribution’
test.cpp:14: error: ‘generator’ was not declared in this scope
test.cpp:14: error: ‘distribution’ was not declared in this scope
```

I think the message on line 4 *"...and must be enabled with the -std=c++0x or -std=gnu++0x compiler options."* is important. 

I´ve tried 
```
sudo apt-get install linux-headers-`uname -r`
```
But that doesnt help. Apart from this I have to admit at this point that I have no idea what else to do here.

Anyone can tell me how to deal with it? Some command codes would be very nice :D

thank you very much!

best regards

---

### Post by steeldriver on 2013-04-19
Have you tried doing exactly what it told you to do? i.e. changing your g++ command line to

```
g++ **-std=c++0x** test.cpp
```

---

### Post by Slim Odds on 2013-04-19
> **gravit123 said:**
> <cut>
I think the message on line 4 *"...and must be enabled with the -std=c++0x or -std=gnu++0x compiler options."* is important. 
<cut>
Indeed! Give it a try.

---

### Post by gravit123 on 2013-04-19
I now have a shorter error code:)

```
g++ -std=c++0x test.cpp
test.cpp: In function &#8216;int main()&#8217;:
test.cpp:9: error: &#8216;default_random_engine&#8217; is not a member of &#8216;std&#8217;
test.cpp:9: error: expected &#8216;;&#8217; before &#8216;generator&#8217;
test.cpp:14: error: &#8216;generator&#8217; was not declared in this scope
```

looks like gnu still dont recognize std::macros from [COLOR=#0000ff]<random>. [/COLOR]Using *-std=gnu++0x returns the same error*.

---

### Post by steeldriver on 2013-04-19
Well I copy-pasted exactly the fragment you posted above and it works for me on 12.04 / g++ 4.6.3

```
$ cat > test.cpp <<EOF
> // bernoulli_distribution
> #include <iostream>
> #include <random>
>  int main() {
>  const int nrolls=10000;
>  std::default_random_engine generator;
> std::bernoulli_distribution distribution(0.5);
>  int count=0;  // count number of trues
>  for (int i=0; i<nrolls; ++i) if (distribution(generator)) ++count;
>  std::cout << "bernoulli_distribution (0.5) x 10000:" << std::endl;
> std::cout << "true:  " << count << std::endl;
>  std::cout << "false: " << nrolls-count << std::endl;
> return 0;
> }
> EOF
$
$ g++ -std=c++0x test.cpp
$
$ ./a.out
bernoulli_distribution (0.5) x 10000:
true:  4994
false: 5006

```

What g++ version are you using?

---

### Post by matt_symes on 2013-04-19
Hi

Same as steeldriver. No errors.
```

matthew-S206:/home/matthew % cat > test.cpp <<"EOF"
heredoc> // bernoulli_distribution 
heredoc> #include <iostream> 
heredoc> #include <random> 
heredoc>  int main() {  
heredoc>  const int nrolls=10000;   
heredoc>  std::default_random_engine generator;   
heredoc> std::bernoulli_distribution distribution(0.5);   
heredoc>  int count=0;  // count number of trues   
heredoc>  for (int i=0; i<nrolls; ++i) if (distribution(generator)) ++count;   
heredoc>  std::cout << "bernoulli_distribution (0.5) x 10000:" << std::endl;   
heredoc> std::cout << "true:  " << count << std::endl;  
heredoc>  std::cout << "false: " << nrolls-count << std::endl;   
heredoc> return 0; 
heredoc> }
heredoc> EOF
matthew-S206:/home/matthew % g++ -std=c++0x test.cpp
matthew-S206:/home/matthew % ./a.out 
bernoulli_distribution (0.5) x 10000:
true:  4994
false: 5006
matthew-S206:/home/matthew % 
```

```
matthew-S206:/home/matthew % g++ --version
g++ (Ubuntu/Linaro 4.7.2-2ubuntu1) 4.7.2
```

Just thought i would pile in with this rather useless post :D

Kind regards

---

### Post by gravit123 on 2013-04-19
oh my! I have an old gcc on old ubuntu.I´ll update it:lolflag: 

```
g++ -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.3-4ubuntu5.1' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5.1) 
```

thank you for all your anwers

cheers

---

### Post by steeldriver on 2013-04-19
... a bit of googling suggests you could *try*

```
g++ -D__GXX_EXPERIMENTAL_CXX0X__ -std=c++0x test.cpp
```

if updating is difficult (which it sometimes is)

---

