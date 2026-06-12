---
title: "Creating link to newly installed g++"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by ritikaSharma on 2010-12-08
I have installed gcc-3.3 & g++-3.3 in ubuntu 9.04. Now I want to  change the default compiler as gcc-3.3/g++-3.3.  After creating links to  newly installed gcc/g++,  gcc works fine but g++ doesn't work. 
When I give "$which gcc" or "$gcc --version" it works fine, but when I  give "$which g++" it gives nothing and also "$g++ --version" it gives an  error "the program 'g++' can be found in the following packages: *  g++..."
When I installed gcc I gave the command "$configure --perfix=/opt/gcc33 --program-suffix=33 --enable-languages=c,c++" . 
When I give "$which g++33" and "$g++33 --version", work fine. 
 
I tried following: 
$export CXX=g++33
$sudo ln -s g++-3.3 g++
Nothing happens. 
I am very new in Linux and I need to install ns2.1a9b in gcc-3.3. Please help me.

---

### Post by Aragant on 2010-12-08
What say about without version...??
Tried that..??

---

### Post by ritikaSharma on 2010-12-08
> **Aragant said:**
> What say about without version...??
Tried that..??
As I already remove the link from the existing g++ ($ rm g++-4.3). Now it gives following results:
**$ g++ --v**
[INDENT] The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Try: sudo apt-get install <selected package>
bash: g++: command not found
[/INDENT]**$ g++ --version**
[INDENT]The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Try: sudo apt-get install <selected package>
bash: g++: command not found
[/INDENT]**$ which g++**
*No result.*

But, g++33 (newly installed g++ works fine)
[B]
$ which g++33[/B]
/opt/gcc33/bin/g++33

---

