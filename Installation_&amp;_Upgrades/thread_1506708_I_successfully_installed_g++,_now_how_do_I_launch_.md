---
title: "I successfully installed g++, now how do I launch it?"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by easyhustlin on 2010-06-10
The program is called the GNU C++ Compiler.  I tried typing it in the terminal and pressing tab, but got nothing.  How do I launch the program?

Thanks.

---

### Post by lisati on 2010-06-10
Use:
```
g++ source-file-name
```
Optionally use:
```
g++ source-file-name -o executable-file-name
```
If you use the first version, your program file will be called "a.out".

There are many more options.

Hope this helps getting you started.

---

### Post by easyhustlin on 2010-06-10
Ok I'm confused.  When I type 

g++ source-file-name 

into the terminal and press tab  I get nothing.  

Sorry but I'm completely new to this, and I don't even really understand how g++ works.

---

### Post by GregBrannon on 2010-06-10
Do you know that g++ is an open source C++ compiler?

What are you trying to do with it?  Why do you think you need it?  Why do you want to run it?

It's a tool that you should have a use for before using it.

---

### Post by lisati on 2010-06-10
> **easyhustlin said:**
> Ok I'm confused.  When I type 

g++ source-file-name 

into the terminal and press tab  I get nothing.  

Sorry but I'm completely new to this, and I don't even really understand how g++ works.

g++ is a compiler for C++ programs. Replace "source-file-name" with the name of the file you wish to compile. If you have navigate to the directory where your C++ file is stored, you can type in g++, the first few letters of the file name, then press tab.

---

### Post by easyhustlin on 2010-06-14
> **GregBrannon said:**
> Do you know that g++ is an open source C++ compiler?

What are you trying to do with it?  Why do you think you need it?  Why do you want to run it?

It's a tool that you should have a use for before using it.


I need to compile in c++ on ubuntu.  Meaning, I have code written in c++ on windows that i need to be able to compile on linux.  

I'll try 
```
g++ filename.cpp -o filename.exe
```

but I don't understand how I can compile a file from windows on linux.

---

### Post by easyhustlin on 2010-06-14
> **easyhustlin said:**
> I need to compile in c++ on ubuntu.  Meaning, I have code written in c++ on windows that i need to be able to compile on linux.  

I'll try 
```
g++ filename.cpp -o filename.exe
```but I don't understand how I can compile a file from windows on linux.
  
Nevermind, don't bother answering my last question, I'm an idiot and I (think) I figured it out.

---

