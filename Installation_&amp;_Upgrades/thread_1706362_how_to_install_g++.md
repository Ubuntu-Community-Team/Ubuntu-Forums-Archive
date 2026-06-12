---
title: "how to install g++"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by tirthpandya on 2011-03-13
Hi All,

I am trying to install Data Display Debugger and while doing that I get an error saying that c++ is not found in the system.

I tried re-installing g++ but it didnt help. 

To verify if g++ was installed in the system or not, I created a basic c++ program and tried to compile it. But the system doesnt even recognize iostream.h.

If I look into /usr/include/c++/4.4 I am able to locate iostream.h.

Please suggest how do I proceed. I downloaded gcc-g++4.5.2 tar.gz but am not sure how to install. I uncompressed the archive, what next should I do?

I also tried all of the following.
apt-get install g++  ------> says "you have the newest version of g++"
sudo apt-get install build-essential -----> 0 upgrades done
sudo aptitude install build-essential------> 0 upgrades done

Please advise,

Thanks,
Tirth

---

### Post by kagerato on 2011-03-13
Is there really something wrong with the C++ toolchain?  I'm not convinced.

```

#include <iostream>

using namespace std;

void main()
{
  cout << "Hello World!" << endl ;
}


```Copy and paste that text into a text editor.  Save it in your home directory as "hello.cpp".  Then open a terminal and run these:

```

cd
g++ hello.cpp -o hello

```What output do you get ?

The DDD error may have little to nothing to do with the actual compiler toolchain, and this will help determine it.

---

### Post by tirthpandya on 2011-03-13
You are correct, DDD seems to have nothing to do with the toolchain.

I found something interesting, If i run the code with #include<iostream.h> it doesnt compile. With <iostream> it does. On reading further about the differences, I learnt that <iostream.h> is deprecated.

But this leaves back a question that if we have iostream.h in our /usr/include/c++/ library, why does the code doesn't compile?

I tested the code you have given, it is working.

What do we deduce now?

Please advise.

Thanks,
Tirth

---

