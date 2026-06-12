---
title: "Which Package for Basic Development Apps?"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by VideoRoy on 2010-01-19
When I install Ubuntu 9.10, I missed the option to install the basic development tools.  Since I have switched from Fedora I actually cannot remember if the installer from 9.10 asked my or if I am remembering it from Fedora.

Can someone suggest the basic package to install the development tools until I figure out what dev apps I want to use?

Thanks.

---

### Post by darkod on 2010-01-19
Are you talking about development of ubuntu apps or development tools like java, c++, etc?

For java you only need JDK, and the package sun-java6-jdk is in synaptic. For c++ the compiler is g++.

If you after an IDE, check Netbeans [www.netbeans.com](www.netbeans.com)

---

### Post by VideoRoy on 2010-01-19
Thanks for the reply.

I am more of a C++ programmer but would like to get into some of the other languages / tools except for Java.  More and more we are trying to shy away from Java when possible.

---

### Post by darkod on 2010-01-19
Netbeans covers quite a few, and it's an IDE. Otherwise, as you are probably aware, you could write c++ code in a simple text editor like gedit (it has color marking for programming tools) and as long as you have g++, you can compile your .cpp file.

---

### Post by VideoRoy on 2010-01-19
Thanks.  Still kind of a linux noob when it comes to programming but have used linux / unix as a desktop on and off.

So I guess I need to make sure g++ is installed and will give Netbeans a shot!

One last question, if I want to compile some of the packages out there and assuming they are c++, is g++ all I need besides libraries?  One need I had recently was to recompile a kernel with a certain option but I was not sure what tools I would need.

I appreciate the help.

---

### Post by ibuclaw on 2010-01-19
If you don't like netbeans, you could give geany a try.

Regards
Iain

---

### Post by darkod on 2010-01-19
As far as I know, g++ is the actual compiler and you don't need anything else except of course any libraries that you are using.
Give it a shot with that simple Hello World code or something. :)

If any basic libraries are needed, installing g++ will also install them. As for your own libraries, you have to have them yourself.

There is also another option, you can install the package build-essential and that installs g++ too.

build-essential allows you to compile drivers if needed for any of your hardware, etc. But for just c++ all you need is g++.
[http://gcc.gnu.org/](http://gcc.gnu.org/)

PS. I included the above link just for information. You can find g++ in Synaptic or just do:
sudo apt-get install g++

No need for any complicated procedure to install.

---

### Post by VideoRoy on 2010-01-19
> **tinivole said:**
> If you don't like netbeans, you could give geany a try.

Regards
Iain
Thanks for the pointer!

> **darkod said:**
> As far as I know, g++ is the actual compiler and you don't need anything else except of course any libraries that you are using.
Give it a shot with that simple Hello World code or something. :)

If any basic libraries are needed, installing g++ will also install them. As for your own libraries, you have to have them yourself.

There is also another option, you can install the package build-essential and that installs g++ too.

build-essential allows you to compile drivers if needed for any of your hardware, etc. But for just c++ all you need is g++.
[http://gcc.gnu.org/](http://gcc.gnu.org/)

PS. I included the above link just for information. You can find g++ in Synaptic or just do:
sudo apt-get install g++

No need for any complicated procedure to install.

Thanks for all the help pointing me in the right direction guys!

I am trying to convert everything I have to linux and use as little of ms windows as possible.  With the current distros and available applications I think I can get really close.

Great forum here :D

---

