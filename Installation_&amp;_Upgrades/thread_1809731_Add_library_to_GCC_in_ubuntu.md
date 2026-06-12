---
title: "Add library to GCC in ubuntu?"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by Worlds Tallest Engineer on 2011-07-22
Hi, one real green engineer here.  I am installing software on an Ubuntu 11.04 server.  

Some of the requirements are; "C/C++ compiler (preferably gcc/g++)","Boost Regex Library", and "PQXX Library".  

I think I have GCC and the Boost library, because I used :
[  sudo apt-get install gcc ]   and   [  sudo apt-get install libboost* ]
:P

How do I know if the boost library is "in" GCC?  Also what command would I use to get the Boost Regex Library?
:confused:

---

### Post by dirghrabadia on 2011-07-22
I had used the Lexical Cast library earlier. Here is an example I found:
```

#include <iostream>
#include <boost/lexical_cast.hpp>

int main()
{
  int value = boost::lexical_cast<int>("42");
  std::cout << value << '\n';
}

```

Basically, you include the header file, and then refer to the documentation for its use.

---

### Post by Worlds Tallest Engineer on 2011-07-22
Thanks.  I tried compiling that code.  

I got 
```
bryan@HonorsServer:~/Desktop$ gcc Testcode.c
In file included from HelloWorld.c:3:0:
/usr/include/boost/lexical_cast.hpp:17:19: fatal error: climits: No such file or directory
compilation terminated.
```and
```
bryan@HonorsServer:~/Desktop$ gcc Testcode.c
HelloWorld.c:4:20: fatal error: iostream: No such file or directory
compilation terminated.
```Douse this mean I have "/boost" but not "/boost/lexical_cast.hpp" or "iostream"?

---

### Post by Worlds Tallest Engineer on 2011-07-22
Also if anyone know the sudo code to get the **PQXX Library**, that would be grate :D

I tried this:
```
[*sudo apt-get install libpq++*]
```and it gave me a lot of text that ended with this:
```
[I]
libpq5 is already the newest version.
libpq5 set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
 libpqxx3-dev : Conflicts: libpqxx-dev but 2.6.9-9 is to be installed
 libpqxx3-doc : Conflicts: libpqxx-doc but 2.6.9-9 is to be installed
E: Broken packages[/I]
```I have no idea what to make of this:confused:

---

### Post by dino99 on 2011-07-22
[https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)

:) :) best wish for your dreaming registred name :) :)

---

