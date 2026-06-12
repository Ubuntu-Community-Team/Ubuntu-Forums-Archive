---
title: "Installing gfortran - issues...."
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by benji2412 on 2010-02-16
Hi folks,

Just wondering if I can get a bit of help? I'm new to Unix based OSs and am currently running Ubuntu 9.10

Currently I'm trying to download and install a piece of software called mobcal ([see link]("http://www.indiana.edu/%7Enano/Software.html")) that requires gfortran to run. I've spent all day reading up on what it is, what I need and how to use it but I'm still failing at the installation.

I've learnt quite a bit about the terminal and how to use it due to his escapade but I'm still not 100%. But I'm aware I need to install GNU and the apropriate libraries but when I've finished looking for something I find I need something else.

Does anyone know the list of what I need to get this to work and how I can install it based on the fact I'm a complete beginner with Linux. I am however very competent with hardware and Windoze, so I will hopefully understand most of what you may tell me.

Many thanks for anyone who can help,
Ben

---

### Post by Claus7 on 2010-02-16
Hello and welcome to the forums!

About your question, I have not dealt with the program you are mentioning, yet if it requires gfortran you can install it pretty easily:
Go to System -> Administration -> Synaptic package manager 

and type gfortran. Then you will see all the available versions for the ubuntu version you are using. Just click the one you want and install it.

You can install that way many other programs you might need.

Regards!

---

### Post by benji2412 on 2010-02-16
I did try that but it didn't work. I'm not at the machine that runs ubuntu at the moment but when I am I'll give it a try. Thanks for the response :)

---

### Post by benji2412 on 2010-02-17
Right I've managed to install it via the synaptic manager but how do I actually open the program so I can run these fortran files?

---

### Post by shirazbj on 2010-02-17
You could try to install g95 from here [http://www.g95.org/](http://www.g95.org/)

It has both windows & linux version.

For ubuntu, you only need to download the *.deb file and save it in your disk. Double click the file, ubuntu will install it automatically.

just type:

g95 mobcal.f

to complie. 

I got an error message saying I need to use the -freal-loops swith, so I type again as:

g95 -freal-loops mobcal.f

No error now and generat a file named a.exe

The txt file says it need a few hours to run the program. Good luck on that.

Cean

---

### Post by benji2412 on 2010-02-17
Thanks for that :)

I managed to download the g95 program and ran the terminal script as you said and got the same loop message. Ran it with the command you said but got the file 'a.out', tried double clicking this and nothing happened, tried ./a.out in the terminal and nothing happened, although a process was running (for quite some time). I'm not amazing with terminal commands but I thought thats what I needed to do to run the program. Anything I'm doing wrong?

---

### Post by Claus7 on 2010-02-17
Hello,

first of all sorry, yet I do not get exactly what are you trying to do. Hope the following points to help you out.

1) In general there are many fortran compilers that you can use in linux either by just clicking and installing them via synaptic or by installing them via command line after you have downloaded the source file.

All of these are doing in general the same thing: compiling fortran code.

2) You mentioned about a program that needed gfortran as dependency... Many programs that need to be run in ubuntu need the build essential package which has a lot of tools for aiding the compilation of other programs. I'm not so sure if this is what you need. 

3) If gfortran is what you wanted I told you how to install it, you can use also g95 compiler as well.

4) Now if you want to compile a program with a compiler then you have to do e.g.:
```
gfortran name_of_your_code.f90
./a.out
```

This is the simplest way to compile a program in linux. The a.out is the executable. In order to run it properly you have to do it via command line and not by just double clicking it, in the directory you compiled your source code.

Think this helped a little. There are also other ways to do things, yet I think that for the time being this is more than enough.

Regards!

---

### Post by benji2412 on 2010-02-17
Hi, thanks for the input.

I tried to mount the file 'mobcal.f' using the instructions above and got this error from the terminal:

ben@ben-laptop:~$ g95 mobcal.f./a.out
g95: mobcal.f./a.out: No such file or directory
ben@ben-laptop:~$ gfortran mobcal.f90./a.out
gfortran: mobcal.f90./a.out: No such file or directory
ben@ben-laptop:~$ gfortran mobcal.f./a.out
gfortran: mobcal.f./a.out: No such file or directory

As you can see I tried a few variations and then I finally tried this:

ben@ben-laptop:~/Desktop/mobcal$ gfortran mobcal.f
mobcal.f:970.18:

      do 301 id=1,npp                                                   
                  1
Warning: Deleted feature: End expression in DO loop at (1) must be integer
mobcal.f:983.18:

      do 300 id=1,npp                                                   
                  1
Warning: Deleted feature: End expression in DO loop at (1) must be integer
mobcal.f:1010.18:

      do 400 id=1,npp                                                   
                  1
Warning: Deleted feature: End expression in DO loop at (1) must be integer

I honestly don't know anything about the terminal and Linux and as much as I'd like to get this working and use it, there are no instructions anywhere and the ones that do exist presume a greater understanding of Linux. If anyone could just lay it out in black and white as if I was a child that'd be great as its very important I get this working. 

Thanks.
Ben

---

### Post by Claus7 on 2010-02-17
Hello,

let's take it step by step:

1) open terminal
Go to Applications -> Accessories -> Terminal
That way the terminal window will open.

2) Now go to the directory you have saved your source code, for example the example.f90 program
You have to navigate to the directory. Type in one line the command:
```
pwd
```
This will show you something like:
/home/*your_user_name*

With the command:
```
cd
``` 
you have to navigate to the folder you have your source code. For example if you have a folder named fortran_files in Desktop you have to do:
```
cd /home/*your_user_name*/Desktop/fortran_files
```

Type then ls to see the files in that directory.
You will see there the example.f90 file.

3) Compile the program
In order to compile the program you have to type:
```
name_of_fortran_compiler example.f90 
```
here that means
```
g95 example.f90
```

4) run the program
If you to not get any errors you have to type then:
./a.out

And you will see the results of your program. Now this will happen if in step 3 you do not face compilation errors, which mean that your program does not need debugging. For more about that you have to read how to create a fortran code from a manual. If it needs debugging then you have to change the code you have written. You can accomplish that by typing:
```
gedit example.f90
```
 
and do all the corrections you think are necessary. Then save the file and redo the compilation and the running of the code. If you do not get errors, probably you are ok, if not you have to repeat this process.

Hope this helped,
Regards!

---

### Post by shirazbj on 2010-02-18
Sorry,

I complied it under windows. So with 

g95 -freal-loops mobcal.f

I got an a.exe file. If you want to specify the name of the exe file, you should type like this,for example name the exe as mobcal.exe:

g95 -freal-loops mobcal.f mobcal.exe

then you will get the mobcal.exe.

Under linux, if you didn't specify the output file, you will get the a.out. To execute it, you need to type:

./a.out

I don't know what the program do. I read the txt file roughly, it says a10A1.out is the output file obtained by running mobcal.f with mobcal.run and a10A1.mfj. So save the exe file, mobcal.run and a10A1.mfj in another folder and run run it to see if it get the same a10A1.out.

The txt file also says "It will probably take a few hours to run, depending on the speed of your computer."

I don't want to try that.

---

### Post by aga5thi on 2011-04-07
Hello 

I am very new to ubuntu and what I need to do is to compile with gfortran a code which have separate modules, 

so I have a main.f90 file and also have four other  separated files (m1.f90, m2.f90, m3.f90 and m4.90) that are modules where I have a few subroutines and other stuff,

I dont know how to compile, if I type gfortran  main.f90  I get an error message saying that it cant open module file m1.f90 for reading at (1) : file or folder not found. I have changed the diretory to the right folder where my files are, and I can perfectly run this code in windows compiler. 

How can I run my program in ubuntu gfortran, can anyone give me a detailed tutorial for that? 


thanks

---

